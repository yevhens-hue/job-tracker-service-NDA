# 🔄 Status Tracking & Lifecycle Management Microservice

[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://docker.com)

An enterprise-grade, deterministic status tracking and case lifecycle management service. Designed for strict state machine enforcement, immutable audit logging, and high-frequency frontend synchronization across distributed dashboard systems.

---

## 🏛️ Architecture & State Lifecycle

```mermaid
stateDiagram-v2
    [*] --> SUBMITTED: Ingestion & Schema Validation
    SUBMITTED --> IN_TRIAGE: Automated Worker Pick
    IN_TRIAGE --> UNDER_REVIEW: Compliance & Data Check
    UNDER_REVIEW --> ACTION_REQUIRED: Missing Documentation
    ACTION_REQUIRED --> UNDER_REVIEW: Re-Submission
    UNDER_REVIEW --> APPROVED: Final Verification
    UNDER_REVIEW --> REJECTED: Validation Failure
    APPROVED --> [*]: Immutable Event Logged
    REJECTED --> [*]: Immutable Event Logged
```

```mermaid
flowchart LR
    Client["Frontend Dashboard\n(Next.js / React)"] <-->|REST API / Webhooks| API["API Gateway\n(Express / Fastify)"]
    API <--> Controller["Lifecycle Controller\n(State Validation)"]
    Controller <--> DB[(PostgreSQL / Audit Ledger)]
    Controller --> Queue["Event Dispatcher\n(Redis / Webhook Notifications)"]
```

---

## ✨ Key Capabilities

1. **Finite State Machine (FSM) Enforcement:** Guarantees that records only progress through mathematically valid, compliant state transitions.
2. **Immutable Audit Ledger:** Every state change records an append-only audit trail with actor ID, timestamp, transition metadata, and cryptographic hash verification.
3. **High-Performance Database Sync:** Connection pooling and indexed historical queries optimized for low-latency dashboard polling and webhook dispatches.
4. **Strict TypeScript & Schema Validation:** Zero runtime type errors with end-to-end Pydantic/Zod input validation.

---

## 🛠️ Tech Stack

- **Runtime & Language:** Node.js, TypeScript (Strict Mode), Express / Fastify
- **Data Persistence:** PostgreSQL, Prisma ORM, Redis
- **Security & Validation:** Zod schema validation, JWT auth, HMAC webhook signatures
- **DevOps:** Docker, Docker Compose, GitHub Actions CI/CD

---

## ⚡ Quick Start

```bash
# Clone the repository
git clone git@github.com:yevhens-hue/job-tracker-service-NDA.git
cd job-tracker-service-NDA

# Install dependencies
npm install

# Run in development mode
npm run dev

# Production build
npm run build && npm start
```

---

## 👨‍💻 Author & Engineering
- **Author:** [Yevhen Shaforostov](https://github.com/yevhens-hue)
- **Role:** AI Product Manager & Full-Stack AI Engineer at [Adsy.com](https://adsy.com)


<!-- activity-sync: 2026-08-28 -->


<!-- activity-sync: 2026-08-28 -->


<!-- activity-sync: 2026-08-29 -->
