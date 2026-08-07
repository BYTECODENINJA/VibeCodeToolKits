# What Is an Implementation Checklist? (Task Tracking & Validation)

## 1. Overview

An **Implementation Checklist** (also called a **Task Manifest**, **Development Checklist**, or **Build Log**) is a structured document that tracks the **completion of individual tasks, features, and sub-components** during the development process. It serves as the **project manager's scorecard** for what has been built and what remains.

If the **PRD** defines *what* you're building, the **TDD** defines *how* you're building it, and the **Definition of Done** defines the final acceptance criteria, the **Implementation Checklist** tracks the **day-to-day progress** toward that goal.

In **AI-assisted ("vibe") coding**, the Implementation Checklist is the agent's **task list**—it tells the AI what to build next, in what order, and provides a clear mechanism to mark items complete.

---

## 2. Why an Implementation Checklist Matters

| Benefit | Explanation |
| :--- | :--- |
| **Progress Visibility** | Instantly see what's done, what's in progress, and what's not started. |
| **Task Prioritization** | Helps the AI (and the team) focus on the most critical items first. |
| **Reduces Overwhelm** | Breaks a large project into manageable, bite-sized chunks. |
| **Accountability** | Each completed task is a small win; the checklist is the record of delivery. |
| **AI Agent Focus** | An AI with an Implementation Checklist works step-by-step rather than trying to build everything at once. |
| **Communication** | Provides a shared understanding of progress across team members (including AI agents). |

---

## 3. Key Components of an Implementation Checklist

### 3.1. Task Definition
Each task in the checklist should include:

| Component | Description | Example |
| :--- | :--- | :--- |
| **Task ID** | A unique identifier (e.g., `TASK-001`). | `TASK-004` |
| **Task Title** | A short, descriptive name. | `"Create Login Screen"` |
| **Description** | Details of what the task entails. | `"Build the login page with email/password fields, OTP option, and social login buttons."` |
| **Status** | Current state of the task. | `Not Started`, `In Progress`, `Blocked`, `Done` |

### 3.2. Task Grouping
Tasks should be organized logically:

| Group | Purpose | Example |
| :--- | :--- | :--- |
| **By Feature** | Group all tasks for a specific feature together. | `"Feature: Authentication"` → Login, Signup, Password Reset |
| **By Layer** | Group by technical layer. | `"Database Setup"`, `"API Development"`, `"Frontend UI"` |
| **By Phase** | Group by development phase. | `"Phase 1: MVP"`, `"Phase 2: Enhancements"` |

### 3.3. Task Dependencies
Document which tasks must be completed before others can begin:

| Dependency | Example |
| :--- | :--- |
| **Blocked By** | "TASK-002 must be completed before TASK-003 can start." |
| **Blocks** | "TASK-001 blocks TASK-004 and TASK-005." |

### 3.4. Acceptance Criteria (Per Task)
Each task should define its own **mini-Definition of Done**:

| Criteria | Example |
| :--- | :--- |
| **Pass/Fail** | "Login form validates email format." |
| **Testable** | "User receives OTP within 5 seconds." |

### 3.5. Status Tracking
Common statuses used in implementation checklists:

| Status | Meaning | Visual Indicator |
| :--- | :--- | :--- |
| `[ ]` | Not Started | Empty checkbox |
| `[-]` | In Progress | Half-filled checkbox (or in-flight marker) |
| `[?]` | Blocked | Question mark (needs input or dependency) |
| `[x]` | Completed | Filled checkbox |
| `[!]` | Critical | Priority marker (must be completed early) |

### 3.6. Timestamps & Assignment
Track **who** is working on what and **when**:

| Field | Purpose |
| :--- | :--- |
| **Assigned To** | Team member or AI agent responsible. |
| **Start Date** | When work began. |
| **Completion Date** | When the task was marked complete. |

---

## 4. Implementation Checklist vs. Other Documents

| Document | Focus | When to Use | Key Output |
| :--- | :--- | :--- | :--- |
| **PRD** | *What* and *why* (business requirements). | At project start | Feature list, user stories |
| **AppFlow** | *Where* users go (screens, navigation). | After PRD | Screen maps, user journeys |
| **TDD** | *How* the system works (architecture, APIs). | Alongside development | System diagrams, API specs |
| **Definition of Done** | The *final* acceptance criteria. | At project or feature completion | Pass/fail checklist |
| **Implementation Checklist** | *Progress tracking* of tasks. | Throughout development | In-progress/complete task list |

**Key distinction**:
- The **Definition of Done** is a **contract**: "Here are the conditions that must be met for this feature to be considered complete."
- The **Implementation Checklist** is a **work plan**: "Here are all the individual steps we need to take to get there."

---

## 5. Best Practices for Writing an Implementation Checklist

| Practice | Why |
| :--- | :--- |
| **Break tasks into small chunks** | A single coding task should not take more than a day (or an AI session). If it does, break it down further. |
| **Order tasks by dependency** | Always list tasks in the order they must be completed. |
| **Make tasks specific and testable** | Avoid vague tasks like "Fix the UI." Instead: "Add proper validation to the login form." |
| **Keep it up to date** | Update the checklist daily or after each coding session. |
| **Use consistent formatting** | Checkboxes (`[ ]`, `[x]`) are universal and parseable by AI agents. |
| **Prioritize visibly** | Label P0 (must-have), P1 (should-have), P2 (nice-to-have) tasks so the AI knows what to build first. |
| **Link to other docs** | Reference PRD IDs, TDD sections, or AppFlow screens for context (e.g., "TASK-003 implements PRD-2.4"). |

---

## 6. Sample Implementation Checklist Skeleton (For Your Starter Kit)

You can include this template in your vibe-coding starter kit as `docs/ImplementationChecklist_Template.md`:

```markdown
# Implementation Checklist: [Project Name]

## Legend
- `[ ]` = Not Started
- `[-]` = In Progress
- `[?]` = Blocked
- `[x]` = Completed
- `[!]` = Priority (must be done early)

---

## 1. Setup & Configuration

- [ ] TASK-001: Initialize project repository
- [ ] TASK-002: Install and configure dependencies (framework, ORM, auth)
- [ ] TASK-003: Set up environment variables and `.env` file
- [ ] TASK-004: Configure linting and formatting (ESLint, Prettier)

---

## 2. Database & Backend Setup

- [ ] TASK-005: Define and apply database schema (migrations)
- [ ] TASK-006: Implement database client/ORM connection
- [ ] TASK-007: Create base repository/DAO classes
- [ ] TASK-008: Seed initial data (if required)

---

## 3. Authentication Module

### 3.1. Email/Password Auth
- [ ] TASK-009: Create sign-up API endpoint
- [ ] TASK-010: Create sign-in API endpoint
- [ ] TASK-011: Implement password hashing (bcrypt/Argon2)
- [ ] TASK-012: Create session management (JWT/cookies)

### 3.2. OAuth Integration
- [ ] TASK-013: Implement Google OAuth 2.0
- [ ] TASK-014: Implement GitHub OAuth 2.0 (if applicable)

### 3.3. Phone OTP Auth
- [ ] TASK-015: Integrate third-party OTP provider (e.g., Twilio/Sent.dm)
- [ ] TASK-016: Implement send OTP endpoint
- [ ] TASK-017: Implement verify OTP endpoint
- [ ] TASK-018: Add rate limiting for OTP requests

---

## 4. Core Feature: [Feature Name]

### 4.1. Data Layer
- [ ] TASK-019: Create database tables for feature
- [ ] TASK-020: Implement repository methods

### 4.2. API Layer
- [ ] TASK-021: Implement GET /api/feature endpoint
- [ ] TASK-022: Implement POST /api/feature endpoint
- [ ] TASK-023: Implement PUT /api/feature/:id endpoint
- [ ] TASK-024: Implement DELETE /api/feature/:id endpoint

### 4.3. Frontend
- [ ] TASK-025: Create feature list view
- [ ] TASK-026: Create feature detail view
- [ ] TASK-027: Create feature create/edit form
- [ ] TASK-028: Implement form validation

---

## 5. Real-Time Features

- [ ] TASK-029: Set up WebSocket/SSE server
- [ ] TASK-030: Implement client-side listener
- [ ] TASK-031: Connect real-time updates to UI

---

## 6. AI Features

- [ ] TASK-032: Integrate AI service (OpenAI, Anthropic, etc.)
- [ ] TASK-033: Implement "Generate Summary" feature
- [ ] TASK-034: Implement "Suggest Next Action" feature
- [ ] TASK-035: Implement "Draft Reply" feature

---

## 7. Testing

- [ ] TASK-036: Write unit tests for auth module
- [ ] TASK-037: Write unit tests for core feature
- [ ] TASK-038: Write integration tests for API endpoints
- [ ] TASK-039: Run accessibility tests on UI components

---

## 8. Documentation

- [ ] TASK-040: Update PRD with final decisions
- [ ] TASK-041: Update TDD with implemented architecture
- [ ] TASK-042: Write README with setup instructions
- [ ] TASK-043: Write API documentation

---

## 9. Deployment

- [ ] TASK-044: Configure production environment
- [ ] TASK-045: Set up CI/CD pipeline
- [ ] TASK-046: Deploy to staging
- [ ] TASK-047: Run final smoke tests
- [ ] TASK-048: Deploy to production

---

## 10. Change Log

| Date | Task ID | Change |
| :--- | :--- | :--- |
| 2026-08-07 | TASK-010 | Completed |
| 2026-08-07 | TASK-011 | In progress |