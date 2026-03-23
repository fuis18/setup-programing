# Architecture: [Project Name]

## 1. Context

<!-- Summary of concept.md: what it solves, for whom, with what constraints. -->
<!-- Do not repeat everything — only what impacts technical decisions. -->

## 1.5 Concept Assumptions That Changed

<!-- CRITICAL: Track what changed from concept.md to here. -->
<!-- This prevents stakeholders from discovering surprises later. -->
<!-- List only the assumptions that impacted technical decisions. -->

| Assumption from concept | What changed | Why | Impact on architecture |
| ----------------------- | ------------ | --- | ---------------------- |
|                         |              |     |                        |

If this section is empty: Either the concept was perfect, or you haven't validated assumptions yet. Neither happens often.

## 2. Technology Stack

<!-- At the beginning because everything else depends on this. -->
<!-- Reference the corresponding ADR if the choice is not obvious. -->

### Backend

<!-- If there is no frontend, delete this entire subsection -->

- Language:
- Framework:
- Runtime:

### Frontend

<!-- If there is no frontend, delete this entire subsection -->

- Framework:
- Key Libraries:

### Database

<!-- If there is no frontend, delete this entire subsection -->

- Type: (relational / document / key-value / graph)
- Engine:

### Infrastructure

- Hosting:
- Containers:
- CI/CD:

### Tools

- Testing:
- Linting / Formatter:
- Observability:

## 3. Technical Objectives

<!-- What the architecture must accomplish. Concrete and verifiable. -->

- [ ]
- [ ]

## 4. Design Principles

<!-- Those that actually apply to the project. Don't copy them all by default. -->
<!-- Examples: Simplicity, Maintainability, Scalability, Testability, Portability -->
-
-

## 5. Architectural Style

<!-- What pattern structures the code? Choose one (or a justified combination). -->
<!-- If the decision isn't obvious, generate an ADR for this. -->

**Pattern:**

<!-- Examples:
- Layered (N-Tier) → presentation / logic / data. Simple, well-known, good for CRUDs.
- Feature-based → each feature is a self-contained folder with its own internal layers.
- Clean Architecture → Entities → Use Cases → Interface Adapters → Frameworks. Useful when the business logic must be framework-independent.
- Hexagonal (Ports & Adapters) → the domain doesn't depend on anything external; everything enters/exits through ports.
- MVC → classic for web apps with server-side rendering.
- Event-Driven → modules communicate through events, not direct calls.
- Modular Monolith → a single deployable, but with modules that have well-defined boundaries.
- Microservices → independent services with their own deployment and database.
- Pipeline / Script → for CLIs or linear processing tools.
-->

**Brief Justification:**
<!-- Why this pattern is right for this project and this team. -->
<!-- If the answer is "it's the one we know," write it down—it's a valid reason. -->

**Layer/Folder Convention Enforced by This Pattern:**

<!-- How this pattern translates to the project's folder structure. -->
<!-- This should be consistent with the "Repository Structure" section. -->
<!-- Example for Feature-based Architecture:

each feature/
├── [feature].controller.ts
├── [feature].service.ts
├── [feature].repository.ts
├── [feature].schema.ts
└── [feature].test.ts
-->

<!-- Example for Clean Architecture:

domain/ → pure business entities and rules
use-cases/ → use cases, orchestrate the domain
adapters/ → controllers, presenters, gateways
infrastructure/ → frameworks, DB, HTTP, external services

-->

## 6. Components and Modules

<!-- List the modules or services. For each: name + responsibility on one line. -->
<!-- The granularity and organization must be consistent with the pattern in section 5. -->
<!-- Example:
- **AuthModule**: registration, login, token refresh, role guards
- **ChatModule**: chat creation, history, typing indicator
-->

## 7. Roles and Permissions

<!-- If the system has multiple actors with differentiated access, define them here. -->
<!-- If not applicable, delete this section. -->
<!--
**Role A** - action 1
- action 2

**Role B** - action 1
-->

## 8. Main Flow

<!-- How a typical request or action travels end-to-end. -->
<!-- An ASCII diagram or a numbered list of steps. Whichever is clearer. -->
<!--
Request → Auth → Router → Middleware → Handler → Response
-->

## 9. Data Model

<!-- Main entities and their relationships. Names of tables, collections, or structs. -->
<!-- It doesn't need to be the complete schema—just the structure that matters. -->

## 10. Contracts and Public Interfaces

<!-- API, CLI, events, WebSockets—what other systems or users consume. -->
<!-- Minimal example for unambiguous executables: -->
<!--
GET /ping → 200 { message: "pong" }
POST /users → 201 { id, email }
WS /chat/:id → events: message, typing, status
CLI arch-cli new [web|app]
-->

## 11. Repository Structure

<!-- Folder tree consistent with the architectural pattern in section 5. -->
<!-- Only the folders that matter, not individual files. -->
<!--
project-name/
  frontend/
  services/ || backend/ || apps/
  docs/
  infra/
-->

## 12. Error Handling

<!-- What happens when something fails. Standard error response format. -->
<!-- Example: { error: string, message: string, status: number } -->

## 13. Environment Variables and Configuration

<!-- List of variables that the system needs to run. -->
<!-- Don't put actual values ​​— only names and descriptions. -->
<!--
DATABASE_URL → string → Database connection URL
JWT_SECRET → string → Secret for signing tokens
PORT → number → Server port (default: 3000)
-->

## 14. Observability

<!-- Logs, metrics, traces. What you need to be able to see when something fails in production. -->

## 15. Security

<!-- Authentication, authorization, secrets, sensitive data, CORS, rate limiting. -->

## 16. Testing Strategy

<!-- What types of tests and where they reside. -->
<!-- The architectural pattern in section 5 determines where the unit tests reside. -->

- Unit tests:
- Integration tests:
- E2E:
- Contract tests (if applicable):

## 17. Related ADRs

<!-- Important decisions that deserve their own file. -->
<!-- The architectural style (section 5) almost always warrants an ADR if it's not obvious. -->

- ADR-0001: [Decision Title]
- ADR-0002: [Decision Title]

## 18. Technical Risks

<!-- What can break the architecture. Be specific. -->

- [ ]

## 19. Open Assumptions

<!-- Decisions not yet made. Mark them to avoid blocking progress. -->

- [ ]

## 20. Technical Acceptance Criteria

<!-- What must be met for the architecture to be considered correctly implemented. -->
<!-- They must be verifiable, not subjective. -->

- [ ]
