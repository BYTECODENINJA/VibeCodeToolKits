# (Product Requirements Document)

## 1. Overview

A **PRD (Product Requirements Document)** is the foundational document that defines **what** you are building, **why** you are building it, and **for whom**. It serves as the single source of truth for the entire product team (product managers, designers, engineers, and QA).

In the context of **AI-assisted ("vibe") coding**, the PRD is your primary prompt artifact. It translates your product vision into a structured, machine-readable format that an AI agent can execute against.

---

## 2. Why a PRD Matters

| Benefit | Explanation |
| :--- | :--- |
| **Clarity** | Forces you to think through features, edge cases, and user flows before a single line of code is written. |
| **Alignment** | Ensures everyone (including the AI) is working toward the same goal. |
| **Scope Control** | Explicitly defines what is **in scope** and what is **out of scope**, preventing feature creep. |
| **Traceability** | Provides a clear audit trail: you can trace every line of code back to a specific requirement. |
| **AI Performance** | A well-structured PRD dramatically improves AI agent output quality by reducing ambiguity. |

---

## 3. Key Components of a PRD

### 3.1. Executive Summary
- **One-paragraph overview** of the product/feature.
- States the **business problem** being solved and the **proposed solution**.

### 3.2. User Personas
- Defines the target users.
- Example: *"Busy professionals who need to quickly triage notifications."*

### 3.3. User Stories
- Describes functionality from the user's perspective.
- Format: `As a [role], I want to [action] so that [benefit].`
- Example: *"As a user, I want to log in with my phone number so I don't need to remember another password."*

### 3.4. Functional Requirements
- **Specific, actionable features** the system must deliver.
- Use a numbered or bulleted list.
- Example: *"The system shall send a 6-digit OTP via SMS within 5 seconds."*

### 3.5. Non-Functional Requirements
- **Quality attributes** – how well the system must perform.
- Includes: performance, security, scalability, accessibility, compliance.
- Example: *"The API must respond within 500ms at p95 percentile."*

### 3.6. User Flows
- Step-by-step sequences of user actions and system responses.
- Often accompanied by wireframes, mockups, or flow diagrams.

### 3.7. Success Metrics (KPIs)
- Measurable outcomes that define success.
- Example: *"OTP verification success rate ≥ 95%."* / *"Reduction in support tickets by 30%."*

### 3.8. Scope & Out of Scope
- **In Scope**: What is being delivered in this release.
- **Out of Scope**: What is explicitly deferred to a future release.

### 3.9. Acceptance Criteria
- A checklist of conditions that must be met for the feature to be considered "complete."
- Each criterion should be **testable** (pass/fail).

---

## 4. Who Creates and Uses a PRD?

| Role | Responsibility |
| :--- | :--- |
| **Product Manager (PM)** | Primary author. Defines the vision, priorities, and success metrics. |
| **Designers** | Use the PRD to create user interfaces that align with requirements. |
| **Engineers** | Use the PRD as a blueprint for implementation. |
| **QA Engineers** | Derive test cases and test plans from the acceptance criteria. |
| **AI Agents** | In a vibe-coding workflow, the PRD serves as the master prompt that guides generation. |

---

## 5. PRD vs. Other Documentation

| Document | Focus | Audience |
| :--- | :--- | :--- |
| **PRD** | *What* to build and *why* (business logic, user value). | PMs, Design, Engineering, QA |
| **Design Spec** | *How it looks* (UI, colors, layout, interactions). | Designers, Frontend Engineers |
| **Technical Design Doc (TDD)** | *How it works* (system architecture, DB schema, APIs). | Engineers, Architects |
| **QA Test Plan** | *How to test it* (test cases, automation, edge cases). | QA Engineers |

---

## 6. Best Practices for Writing a PRD

| Practice | Why |
| :--- | :--- |
| **Keep it concise** | Overly long PRDs lose focus. Aim for clarity over volume. |
| **Write for the implementer** | If an AI agent will read it, use clear, unambiguous language. |
| **Use bullet points** | Scan-friendly formatting helps everyone (including AI) parse requirements quickly. |
| **Prioritize features** | Use labels like `P0` (must-have), `P1` (nice-to-have), `P2` (future). |
| **Include edge cases** | Explicitly state what happens when things go wrong (e.g., network failure, invalid input). |
| **Version control it** | Store it alongside your code (e.g., `/docs/PRD_FeatureName.md`). |

---

## 7. Sample PRD Skeleton (For Your Starter Kit)

You can include this as a template in your vibe-coding starter kit:

```markdown
# PRD: [Feature/Product Name]

## 1. Executive Summary
[Brief overview of the product and the problem it solves.]

## 2. User Personas
- **[Persona 1]**: [Description, goals, pain points]
- **[Persona 2]**: [Description, goals, pain points]

## 3. User Stories
- As a [role], I want to [action] so that [benefit].
- As a [role], I want to [action] so that [benefit].

## 4. Functional Requirements
- [FR-001] The system shall [specific behavior].
- [FR-002] The system shall [specific behavior].

## 5. Non-Functional Requirements
- **Performance**: [e.g., Load time < 2s]
- **Security**: [e.g., All data encrypted in transit]
- **Compliance**: [e.g., GDPR compliant]

## 6. User Flows
[Describe the primary user journey, step-by-step. Include diagrams if possible.]

## 7. Success Metrics
- Metric 1: [target]
- Metric 2: [target]

## 8. Scope
**In Scope**: [List features being shipped]
**Out of Scope**: [List deferred features]

## 9. Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3