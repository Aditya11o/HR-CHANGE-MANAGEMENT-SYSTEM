# Deployment, Infrastructure & DevOps Guide
## University HR Change Management & Automation System

| Document Metadata | Specification Detail |
|---|---|
| **Document Identifier** | `DOC-10-DEP-CANONICAL` |
| **Project Name** | University HR Change Management & Automation System |
| **System Phase** | Phase 8 — Infrastructure, Deployment & Operations Specification |
| **Document Status** | Approved Canonical Deployment Baseline |
| **Date** | October 2026 |
| **Runtime Target** | Node.js 20 LTS, PostgreSQL 16, Redis 7, S3 / MinIO |
| **Orchestration** | Docker, Docker Compose, Kubernetes Ready |
| **Authoritative Sources** | `docs/04-system-architecture/`, `docs/05-database/`, `source-requirements/TECHNOLOGY_ARCHITECTURE_BASELINE.md` |

---

## 1. Container Topology & Infrastructure Architecture

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                PRODUCTION CONTAINER TOPOLOGY                                     │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘

                       [ University Ingress / Reverse Proxy (Nginx) ]
                                    │ TLS 1.3 Termination & WSS Proxy
                                    ▼
       ┌────────────────────────────┴────────────────────────────┐
       │                                                         │
       ▼                                                         ▼
 [ frontend-app ]                                          [ backend-api ]
 Next.js App Router (Port 3000)                           NestJS Modular Monolith (Port 4000)
 • Server-Side Rendering                                  • REST Controllers & Services
 • Vanilla CSS Design Tokens                              • Socket.IO WebSocket Gateway
 • Static Asset Caching                                   • BullMQ Worker Producers
                                                                 │
                                                                 ├──► [ database ] (PostgreSQL 16, Port 5432)
                                                                 ├──► [ cache-queue ] (Redis 7, Port 6379)
                                                                 └──► [ object-store ] (MinIO / S3, Port 9000)
```

---

## 2. Docker Compose Configuration (`docker-compose.yml`)

The following production-aligned compose configuration powers local development and staging:

```yaml
version: '3.8'

services:
  database:
    image: postgres:16-alpine
    container_name: hrms-postgres
    restart: always
    environment:
      POSTGRES_DB: university_hrms
      POSTGRES_USER: hrms_admin
      POSTGRES_PASSWORD: ${DB_PASSWORD:-StrongSecretDbPass123!}
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data
      - ./init-db.sql:/docker-entrypoint-initdb.d/init-db.sql
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U hrms_admin -d university_hrms"]
      interval: 10s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    container_name: hrms-redis
    restart: always
    command: redis-server --appendonly yes --requirepass ${REDIS_PASSWORD:-RedisStrongPass456!}
    ports:
      - "6379:6379"
    volumes:
      - redisdata:/data
    healthcheck:
      test: ["CMD", "redis-cli", "-a", "${REDIS_PASSWORD:-RedisStrongPass456!}", "ping"]
      interval: 10s
      timeout: 5s
      retries: 5

  object-store:
    image: minio/minio:RELEASE.2024-01-01T00-00-00Z
    container_name: hrms-minio
    restart: always
    command: server /data --console-address ":9001"
    environment:
      MINIO_ROOT_USER: ${MINIO_ROOT_USER:-hrms_storage_admin}
      MINIO_ROOT_PASSWORD: ${MINIO_ROOT_PASSWORD:-StorageSecretKey789!}
    ports:
      - "9000:9000"
      - "9001:9001"
    volumes:
      - miniodata:/data

  backend-api:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: hrms-backend
    restart: always
    environment:
      NODE_ENV: production
      PORT: 4000
      DATABASE_URL: postgresql://hrms_admin:${DB_PASSWORD:-StrongSecretDbPass123!}@database:5432/university_hrms
      REDIS_HOST: redis
      REDIS_PORT: 6379
      REDIS_PASSWORD: ${REDIS_PASSWORD:-RedisStrongPass456!}
      JWT_SECRET: ${JWT_SECRET:-EnterpriseJwtSecretKeyAtLeast32CharsLong!}
      OBJECT_STORAGE_ENDPOINT: http://object-store:9000
    ports:
      - "4000:4000"
    depends_on:
      database:
        condition: service_healthy
      redis:
        condition: service_healthy

  frontend-app:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    container_name: hrms-frontend
    restart: always
    environment:
      NODE_ENV: production
      PORT: 3000
      NEXT_PUBLIC_API_URL: http://localhost:4000/api/v1
      NEXT_PUBLIC_SOCKET_URL: http://localhost:4000
    ports:
      - "3000:3000"
    depends_on:
      - backend-api

volumes:
  pgdata:
  redisdata:
  miniodata:
```

---

## 3. Environment Variables Specification (`.env.example`)

### Backend Environment Configuration
```ini
# Application
NODE_ENV=production
PORT=4000
APP_NAME="University HR Change Management System"
API_PREFIX="/api/v1"

# Database Configuration (PostgreSQL 16)
DATABASE_URL=postgresql://hrms_admin:StrongPassword@localhost:5432/university_hrms?sslmode=prefer
DB_POOL_MIN=5
DB_POOL_MAX=25

# Cache & Queues (Redis 7)
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=RedisStrongPassword
REDIS_DB=0

# Security & JWT Tokens
JWT_PRIVATE_KEY_PATH=/etc/hrms/secrets/jwt_rs256_private.pem
JWT_PUBLIC_KEY_PATH=/etc/hrms/secrets/jwt_rs256_public.pem
JWT_ACCESS_EXPIRATION=15m
JWT_REFRESH_EXPIRATION=7d
COOKIE_DOMAIN=.university.edu

# Binary Object Storage (S3 / MinIO)
S3_ENDPOINT=https://storage.university.edu
S3_REGION=ap-south-1
S3_BUCKET_NAME=hrms-documents
S3_ACCESS_KEY=StorageAccessKey
S3_SECRET_KEY=StorageSecretKey
MAX_FILE_SIZE_MB=10

# Outbound Mail (SMTP Gateway)
SMTP_HOST=smtp.office365.com
SMTP_PORT=587
SMTP_USER=hrms-noreply@university.edu
SMTP_PASSWORD=SmtpSecretPassword
SMTP_FROM_NAME="University HR Automation Engine"

# ERP Integration Gateway
ERP_ENDPOINT_URL=https://erp.university.edu/api/v2/integration/hrms-feed
ERP_API_KEY=ErpIntegrationBearerTokenSecret
```

---

## 4. Database Migration & Initialization Runbook

### Step 1: Initialize Database Schemas
Run the initialization script against PostgreSQL to create the logical domain schemas:
```sql
CREATE DATABASE university_hrms;
\c university_hrms;

CREATE SCHEMA IF NOT EXISTS mod1_core;
CREATE SCHEMA IF NOT EXISTS mod2_recruitment;
CREATE SCHEMA IF NOT EXISTS mod3_performance;
CREATE SCHEMA IF NOT EXISTS shared_platform;

-- Revoke raw destructive permissions on audit tables
REVOKE DELETE, TRUNCATE ON ALL TABLES IN SCHEMA shared_platform FROM PUBLIC;
```

### Step 2: Execute Relational Migrations
```bash
# Execute schema migration tool (NestJS / TypeORM / Prisma)
npm run migration:run
```

### Step 3: Seed Institutional Foundation Data
```bash
# Seed 16 RBAC Roles, System Administrator account, and School/Department hierarchy nodes
npm run seed:institutional-baseline
```

---

## 5. High Availability, Backups & Disaster Recovery

| Component | Backup Frequency | Retention Period | Recovery Objective |
|---|---|---|---|
| **PostgreSQL Database** | Continuous WAL archiving + Daily Full Snapshot at 02:00 IST | 90 Days | RPO $< 5$ minutes; RTO $< 30$ minutes via Point-in-Time Recovery (PITR). |
| **Object Storage (Documents)**| Multi-region bucket replication (S3 Versioning enabled) | Indefinite (Per `REQ-TBD-11`) | RPO $= 0$; RTO $< 10$ minutes. |
| **Redis In-Memory State** | AOF (Append-Only File) every second + RDB snapshot hourly | 7 Days | Cache can rebuild from PostgreSQL; BullMQ persistent jobs recovered. |

---

## 6. Healthchecks & Operational Monitoring

The backend exposes standard Kubernetes-compatible health endpoints:
- `GET /api/v1/health/liveness`: Verifies process responsiveness; returns HTTP 200 `{ "status": "UP" }`.
- `GET /api/v1/health/readiness`: Verifies active connection to PostgreSQL, Redis, and Object Storage; returns HTTP 200 if all dependencies are healthy.
- `GET /api/v1/metrics`: Prometheus metrics scraper exporting HTTP latency, active WebSocket connections, and BullMQ queue depth.
