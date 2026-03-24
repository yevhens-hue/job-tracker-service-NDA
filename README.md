# Status Tracking & Lifecycle Management Service

A modern tracking architecture and API demonstrating robust state management workflows. Built to accurately track the lifecycle, history, and current status of individual records or cases synchronized with external frontend interfaces.

## Project Structure

```text
status-tracking-service/
├── src/
│   ├── controllers/
│   │   └── recordController.ts   ← Main logic for lifecycle updates
│   ├── models/
│   │   └── statusSchema.ts       ← Strict typing for structured tracking logs
│   ├── services/
│   │   └── syncService.ts        ← Synchronizes state changes with the DB
│   ├── utils/
│   │   └── logger.ts             ← Audit trail generation
│   ├── index.ts                  ← Application entry point
│   └── routes.ts                 ← Express/Fastify API routes
├── .env.example
├── package.json
└── tsconfig.json
```

## Highlights & Capabilities

- **Strict State Management:** Ensures a record can only transition through valid, approved statuses (e.g., Pending -> Under Review -> Completed).
- **Audit Trails:** Every status change writes an immutable log, creating a complete historical timeline of the case/record.
- **Frontend Synchronization:** Built with RESTful best practices, making it highly compatible with modern React/Next.js dashboards using polling or WebSockets.
- **TypeScript Strictness:** Prevents runtime errors by strictly defining input payloads and state transitions.

## Quick Start

**1. Install Node Dependencies**
```bash
npm install
```

**2. Database & Environment**
Create your local `.env` file using the provided example. Make sure your PostgreSQL or MongoDB connection string is correctly configured.
```bash
cp .env.example .env
```

**3. Development Run**
Run the server in hot-reload mode for local development and testing:
```bash
npm run dev
```

**4. Production Build**
Compile the TypeScript code into production-ready JavaScript:
```bash
npm run build
npm start
```

## Interacting with the API

**Example Request: Update Record Status**
```bash
curl -X PATCH http://localhost:3000/api/records/1054
-H "Content-Type: application/json"
-d '{
  "status": "UNDER_REVIEW",
  "updated_by": "system_worker",
  "notes": "Automated pipeline transitioned record to review phase."
}'
```

**Example Response:**
```json
{
  "success": true,
  "data": {
    "record_id": "1054",
    "previous_status": "PENDING",
    "current_status": "UNDER_REVIEW",
    "timestamp": "2026-03-24T12:00:00Z"
  }
}
```
