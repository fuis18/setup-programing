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

<!-- The folder/file convention that this pattern produces lives in design.md → Section 1. -->
<!-- Reference it here so readers know where to look. -->

> See [`docs/design.md`](./design.md) → **Section 1** for the folder/file convention this pattern enforces.

---

<!-- Sections 6–11 (Modules, Roles, Flows, Data Model, Contracts, Repository Structure) -->
<!-- have been moved to design.md, which covers HOW the system is built internally.     -->
<!-- architecture.md stays focused on WHY and WHAT: decisions, principles, constraints. -->

> See [`docs/design.md`](./design.md) for modules, roles, flows, data model, contracts, and repository structure.

---

## 6. Error Handling

<!-- What happens when something fails. Standard error response format. -->
<!-- Example: { error: string, message: string, status: number } -->

## 7. Environment Variables and Configuration

<!-- List of variables that the system needs to run. -->
<!-- Don't put actual values ​​— only names and descriptions. -->
<!--
DATABASE_URL → string → Database connection URL
JWT_SECRET → string → Secret for signing tokens
PORT → number → Server port (default: 3000)
-->

## 8. Observability

<!-- Logs, metrics, traces. What you need to be able to see when something fails in production. -->

## 9. Security

<!-- Authentication, authorization, secrets, sensitive data, CORS, rate limiting. -->

## 10. Testing Strategy

<!-- What types of tests and where they reside. -->
<!-- The architectural pattern in section 5 determines where the unit tests reside. -->

- Unit tests:
- Integration tests:
- E2E:
- Contract tests (if applicable):

## 11. Related ADRs

<!-- Important decisions that deserve their own file. -->
<!-- The architectural style (section 5) almost always warrants an ADR if it's not obvious. -->

- ADR-001: [Decision Title]
- ADR-002: [Decision Title]

## 12. Technical Risks

<!-- What can break the architecture. Be specific. -->

- [ ]

## 13. Open Assumptions

<!-- Decisions not yet made. Mark them to avoid blocking progress. -->

- [ ]

## 14. Technical Acceptance Criteria

<!-- What must be met for the architecture to be considered correctly implemented. -->
<!-- They must be verifiable, not subjective. -->

- [ ]
