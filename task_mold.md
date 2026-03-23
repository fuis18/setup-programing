# Tasks: [Project Name]

<!-- INSTRUCTION FOR AI: Tasks should be small, organized, and testable. -->
<!-- Each task should be completeable in a reasonable work session (1-4 hours). -->
<!-- If a task is larger, break it down. -->
<!-- Mark dependencies with: (depends on: #N) -->
<!-- Mark priority with tags: 🔴 CRITICAL | 🟡 IMPORTANT | 🟢 NICE-TO-HAVE -->

---

## 0. Minimum Deliverable

<!-- Define the minimum scenario that must work without errors at the end. -->
<!-- This is the "done" criterion for the entire project. -->
<!-- All tasks marked 🔴 CRITICAL must be completed for this to pass. -->
<!-- Example:
GET /ping → 200 { message: "pong" }
POST /login → 200 { token }
GET /invalid-resource → 404
-->

---

## Priority Legend

- 🔴 **CRITICAL**: Must be done. Without it, the project doesn't work.
- 🟡 **IMPORTANT**: Should be done. The project works without it, but is incomplete.
- 🟢 **NICE-TO-HAVE**: Can be done later. Nice to have but not essential for MVP.

---

## 1. Project Preparation

- [ ] 🔴 Create the basic repository structure
- [ ] 🔴 Configure development tools (linting, formatter)
- [ ] 🔴 Configure testing
- [ ] 🔴 Create `.env.example` with all required variables
- [ ] 🔴 Initial database setup / migrations (if applicable)
- [ ] 🟡 Configure pre-commit hooks
- [ ] 🟡 Set up CI/CD pipeline skeleton
- [ ] 🟢 Configure code coverage reporting

---

## 2. [Module or Feature 1]

<!-- Repeat this block for each module in the system. -->
<!-- Name the block the same as the module in architecture.md -->
<!-- Organize tasks within each module by priority. -->

**Module Deliverable:** <!-- What works when this module is complete -->

### Critical Path

- [ ] 🔴 Specific and testable task (depends on: 1.1)
- [ ] 🔴 Specific and testable task
- [ ] 🔴 Module unit tests covering critical paths

### Important Features

- [ ] 🟡 Specific and testable task
- [ ] 🟡 Module edge cases
- [ ] 🟡 Error handling tests

### Polish

- [ ] 🟢 Performance optimization (if applicable)
- [ ] 🟢 Code comments / documentation
- [ ] 🟢 Logging statements

---

## 3. [Module or Feature 2]

**Module Deliverable:**

### Critical Path

- [ ] 🔴 Specific and testable task
- [ ] 🔴 Specific and testable task
- [ ] 🔴 Module unit tests

### Important Features

- [ ] 🟡 Specific and testable task
- [ ] 🟡 Module edge cases

### Polish

- [ ] 🟢 Optimization or documentation

---

## 4. Integration

### Critical Path

- [ ] 🔴 Integration tests between key modules (critical path only)
- [ ] 🔴 End-to-end smoke test of the main flow
- [ ] 🔴 Global error handling and edge cases

### Important Features

- [ ] 🟡 Integration tests for secondary flows
- [ ] 🟡 Performance testing under load (if applicable)

### Polish

- [ ] 🟢 Cross-module logging and observability

---

## 5. Documentation

### Critical

- [ ] 🔴 Update README.md with "How to Run" commands
- [ ] 🔴 Document all environment variables in `.env.example`

### Important

- [ ] 🟡 Create or update ADRs for decisions taken during development
- [ ] 🟡 Document any deviations from architecture.md

### Nice-to-Have

- [ ] 🟢 API documentation (Swagger, OpenAPI, etc.)
- [ ] 🟢 Architecture diagrams (if applicable)
- [ ] 🟢 Runbook for common operations

---

## 6. Final Validation

### Critical

- [ ] 🔴 Verify minimum deliverable (section 0) — all 🔴 tasks complete
- [ ] 🔴 Review technical acceptance criteria in architecture.md
- [ ] 🔴 Manual demo or smoke test

### Important

- [ ] 🟡 Code review of all modules
- [ ] 🟡 Test coverage report meets minimum threshold

### Nice-to-Have

- [ ] 🟢 Performance profiling
- [ ] 🟢 Security audit (if applicable)

---

## Quick Reference: What's MVP?

**To ship the Minimum Viable Product**, you only need to complete all tasks marked 🔴.

**To ship a solid 1.0**, add all 🟡 tasks.

**To ship a polished product**, complete all tasks including 🟢.

---

<!-- NOTE FOR AI: If the project has N modules, generate N blocks in section 2-3. -->
<!-- Each block must have its own deliverable and tests. -->
<!-- Organize each module by priority. -->
