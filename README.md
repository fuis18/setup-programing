# Programming Project Creation Guide

## Document List

| Document          | Answer                   | Who wrote it                                |
| ----------------- | ------------------------ | ------------------------------------------- |
| `concept.md`      | What and why             | Human (with AI assistance)                  |
| `architecture.md` | How                      | AI based on concept.md                      |
| `task.md`         | What to do next          | AI based on architecture.md                 |
| `ADR-XXX.md`      | Why this decision        | AI or human when a major decision arises    |
| `README.md`       | How to enter the project | AI at the end, when everything above exists |

## Workflow

```
1. idea rough → concept.md (human completes the template)
2. concept.md → architecture.md (AI generates)
3. architecture.md → task.md (AI generates)
4. architecture.md → ADR-XXXX.md (AI generates one per important decision)
5. all of the above → README.md (AI generates last)
```

**Key rule:** Do not proceed to the next step if the previous one has important empty sections.

Specifically: Do not generate `architecture.md` without a clear understanding of the system stack and actors.

---

## Prompt: concept.md

**What you need before using this prompt:**

- Project type (CLI, web app, API, framework, etc.)
- Main objective in one sentence
- Main features (even if it's a draft)

```
Take this idea and turn it into a clear, concise, and actionable concept.md using the provided template.

Rules:
- Keep the focus on the problem, objective, stakeholders, and success criteria
- DO NOT include architecture, technology stack, or implementation details
- If the idea isn't clear in any section, ask a question instead of making things up
- The "Out of Scope" section is mandatory—it helps define the scope of work
- Be concise: one line per point where possible

[paste idea here]
```

---

## Prompt: architecture.md

**What you need before using this prompt:**

- A complete `concept.md` file (especially actors, roles, and constraints)
- A defined (or at least preferred) technology stack

`````
Using this concept.md file and the specified stack, generate an architecture.md file using the provided template.

```` Rules:
- Start with the Technology Stack (section 2) — everything else depends on this
- Include all modules/components with their responsibilities on one line each
- If the system has multiple roles, complete the "Roles and Permissions" section
- In "Contracts and Public Interfaces," include at least the critical endpoints or commands with their expected response
- Include the repository structure as a folder tree
- If there is a non-obvious decision (e.g., why that framework, that database), mark it as a candidate for ADR (Analysis, Diligence, and Reduction)
- If information is missing to make a decision, write it in "Open Assumptions" instead of guessing

[paste concept.md here]
`````

---

## Prompt: task.md

**What you need before using this prompt:**

- A complete `architecture.md` file

```
From this architecture.md file, generate a task.md file using the provided template.

Rules:
- Each task must be implementable in one work session (1-4 hours)
- If a task is larger, divide it into subtasks
- Organize tasks by module, as defined in architecture.md
- Each module must have its own "module deliverable" — what works when that module is complete
- Include testing tasks within each module, not just at the end
- Mark dependencies between tasks where they exist
- Section 0 "Minimum Deliverable" must describe the complete smoke test scenario for the system

[paste architecture.md here]
```

---

## Prompt: ADR

**When to write an ADR:**
When a technical decision changes the stack, repository structure, data model, or how modules communicate. If you're wondering whether it warrants an ADR, it probably does.

```
Generate an ADR using the provided template for the following decision:

Decision: [name of what was chosen]
Context: [why a decision had to be made]
Alternatives considered: [list]

Rules:
- The ADR title should state what was decided, not what was evaluated.
- In "Negative Consequences," be honest—everything has trade-offs.
- In "Impact on Architecture," indicate which sections of architecture.md are affected.
```

---

## Prompt: README.md

**What you need before using this prompt:**

- `concept.md`, `architecture.md`, `task.md`, and at least one ADR

````
From these documents, generate a README.md for the repository using the provided template.

``` Rules:
- The initial description must be understandable to someone outside the project.
- Prerequisites must include minimum versions.
- "How to Run" commands must be executable as written.
- List only the ADRs that someone new needs to read to understand the important decisions.
- Don't repeat architecture.md—link to it.

[paste concept.md + architecture.md here]
````

---

## Signs that the document is not ready to move to the next step

**concept.md is not ready if:**

- It doesn't have defined actors.
- The main functions are more than 10 or are vague.
- "Out of scope" is empty.
- The goal is not verifiable.

**architecture.md is not ready if:**

- The technology stack is not defined.
- The modules don't have clear responsibilities.
- There are no defined minimum contracts/interfaces.
- The repository structure is empty.
- There are important decisions without a candidate ADR.

**task.md is not It's ready if:**

- Tasks don't have a "module deliverable"
- There are tasks that last more than one day without being split
- There are no testing tasks per module
- The "Minimum Deliverable" (section 0) is empty
