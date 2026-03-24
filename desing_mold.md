# Design: [Project Name]

<!-- This document answers HOW the system is built internally. -->
<!-- It is generated from architecture.md and is the direct input for task.md. -->
<!-- Update it when modules, flows, data model, or contracts change. -->

---

## 1. Layer / Folder Convention

<!-- How the architectural pattern (defined in architecture.md) translates into folders. -->
<!-- This is the convention that every module must follow consistently. -->

<!--
Example for Feature-based Architecture:
each feature/
├── [feature].controller.ts   → HTTP layer, input validation
├── [feature].service.ts      → business logic
├── [feature].repository.ts   → data access
├── [feature].schema.ts       → data model / DTOs
└── [feature].test.ts         → unit tests

Example for Clean Architecture:
domain/           → pure entities and business rules (no external dependencies)
use-cases/        → orchestrate the domain, one file per use case
adapters/         → controllers, presenters, gateways (translate between layers)
infrastructure/   → frameworks, DB, HTTP, external services
-->

**Convention enforced:**

```
[paste the folder/file structure your pattern produces]
```

---

## 2. Components and Modules

<!-- One module = one clear responsibility. -->
<!-- Name must match the folder structure above and task.md sections. -->
<!-- Format: **ModuleName**: what it does, what it does NOT do. -->

<!--
- **AuthModule**: registration, login, token refresh, role guards. Does NOT handle authorization beyond JWT validation.
- **ChatModule**: message creation, history retrieval, typing indicator. Does NOT handle notifications.
- **UserModule**: profile CRUD, preferences. Does NOT handle authentication.
-->

| Module | Responsibility | Does NOT handle |
| ------ | -------------- | --------------- |
|        |                |                 |
|        |                |                 |
|        |                |                 |

---

## 3. Pages and Screens

<!-- Only for projects with a UI (web app, mobile, desktop). -->
<!-- Delete this section if the project is a pure API, CLI, or library. -->
<!-- One row per page. If a page has variants by role, add a row per variant. -->

| Page | Route / Path | Who can access | Components |
| ---- | ------------ | -------------- | ---------- |
|      |              |                |            |

<!--
Example:
| Login        | /login        | Public        | LoginForm, Alert                     |
| Dashboard    | /dashboard    | Admin, Editor | StatCard, RecentActivity, SidebarNav |
| User Detail  | /users/:id    | Admin         | UserProfile, PermissionsPanel        |
| Edit Profile | /profile/edit | Any logged-in | ProfileForm, AvatarUpload            |
| 404          | *             | Public        | NotFoundIllustration                 |
-->

---

## 4. Roles and Permissions

<!-- Only if the system has multiple actors with differentiated access. -->
<!-- Delete this section if there is a single actor. -->

<!--
**Admin**
- Create, update, delete users
- View audit logs
- Manage system configuration

**Editor**
- Create and update own content
- View published content from others

**Viewer**
- Read-only access to published content
-->

---

## 5. Main Flows

<!-- How a typical request or action travels end-to-end. -->
<!-- One subsection per critical flow. Minimum: the happy path. -->
<!-- Use ASCII diagrams or numbered steps — whichever is clearer. -->
<!-- If a flow involves authorization, show where it's checked. -->

### 4.1 [Primary Flow Name]

```
[Example]
Client → Auth Middleware → Router → Handler → Service → Repository → DB
                                                        ↓
                                                   Response ← DTO mapping
```

### 4.2 [Secondary Flow Name]

```
[Example]
User action → Validate input → Publish event → Consumer → Side effect
```

---

## 6. Data Model

<!-- Main entities and their relationships. -->
<!-- Not the full schema — only the structure that matters for understanding the system. -->
<!-- Include: entity name, key fields, and relationships (1:N, N:M, etc.). -->
<!-- If using a relational DB, an ER-style list is enough. -->
<!-- If using a document DB, show the main document shape. -->

<!--
**User**
- id, email, passwordHash, role, createdAt
- has many → Message

**Conversation**
- id, createdBy (User), participants (User[]), createdAt
- has many → Message

**Message**
- id, conversationId (Conversation), authorId (User), content, sentAt
-->

---

## 7. Contracts and Public Interfaces

<!-- What external systems or users consume: REST, CLI, WebSockets, events, etc. -->
<!-- Each entry must be executable / testable as written. -->
<!-- Format: METHOD /path → STATUS { response shape } -->

<!--
REST:
GET  /ping              → 200 { message: "pong" }
POST /auth/login        → 200 { token, expiresAt } | 401 { error }
POST /auth/register     → 201 { id, email }        | 409 { error }
GET  /users/:id         → 200 { id, email, role }  | 404 { error }
DELETE /users/:id       → 204                       | 403 { error }

WebSocket:
WS /chat/:conversationId → events: message_created, user_typing, user_joined

CLI:
mycli init [project-name]   → creates folder structure
mycli generate module [name] → scaffolds module files
-->

---

## 8. Repository Structure

<!-- Folder tree consistent with the convention in section 1. -->
<!-- Only folders that matter — no need to list every file. -->
<!-- Annotate folders with a short comment where the purpose isn't obvious. -->

```
project-name/
├── src/
│   ├── [module-a]/
│   ├── [module-b]/
│   └── shared/           # shared utilities, types, constants
├── docs/
│   ├── architecture.md
│   ├── design.md         # this file
│   ├── task.md
│   └── adr/
│       └── ADR-0001.md
├── tests/
│   ├── integration/
│   └── e2e/
├── .env.example
└── README.md
```

---

## 9. Error Handling

<!-- What happens when something fails. -->
<!-- Define the standard error response format used across all modules. -->
<!-- Document any module-specific error behavior that deviates from the standard. -->

<!--
Standard error response:
{
  "error": "ERROR_CODE",        // machine-readable constant
  "message": "Human readable.", // for developers / logs
  "status": 400                 // mirrors HTTP status
}

HTTP status conventions used in this project:
- 400 Bad Request   → validation errors
- 401 Unauthorized  → missing or invalid token
- 403 Forbidden     → valid token, insufficient permissions
- 404 Not Found     → resource doesn't exist
- 409 Conflict      → duplicate resource
- 500 Internal      → unexpected server error (never expose internals)
-->

---

## Notes

<!-- Anything that doesn't fit above but a developer needs to know before touching the code. -->
<!-- Examples: known shortcuts taken, planned refactors, tricky integrations. -->