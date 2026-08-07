# (User Journey & Screen Flow Specification)

## 1. Overview

An **AppFlow** (also called a **User Journey Map**, **Screen Flow**, or **UX Flow**) is a visual or textual specification that defines **every screen, interaction, and state transition** a user experiences while using your application.

If the **PRD** answers *"What are we building and why?"* and the **TDD** answers *"How will we build it technically?"*, the **AppFlow** answers:
- *"Where will the user go?"*
- *"What will they see at each step?"*
- *"What happens when they click, type, or swipe?"*

It bridges the gap between product requirements and UI/UX design, ensuring that every possible user action—from onboarding to error recovery—is accounted for before a single line of UI code is written.

---

## 2. Why an AppFlow Matters

| Benefit | Explanation |
| :--- | :--- |
| **UX Completeness** | Forces you to think through every screen, state, and edge case (loading, empty, error). |
| **Developer Clarity** | Engineers (and AI agents) know exactly which screens to build and what triggers each transition. |
| **Consistency** | Prevents disjointed navigation; every back button, modal, and deep link behaves predictably. |
| **Early Edge-Case Discovery** | Reveals gaps like "What happens if the user presses back during OTP verification?" before coding starts. |
| **AI Agent Accuracy** | An AI with a detailed AppFlow generates the exact screen hierarchy and navigation logic you intend, rather than guessing or inventing routes. |

---

## 3. Key Components of an AppFlow

### 3.1. User Personas (Context)
- Briefly restate who is navigating the app (e.g., "Logged-out visitor," "Logged-in power user," "Admin").
- Different personas may have different flows.

### 3.2. Onboarding Flow
- **First-time launch**: Splash screen, permissions request (e.g., notifications), app introduction.
- **Account creation**: Sign-up screens, verification steps (email/phone), profile completion.
- **Post-onboarding**: What the user sees immediately after finishing onboarding (e.g., empty state with a call-to-action).

### 3.3. Authentication Flow
- **Login**: Screens for email/password, social OAuth (Google, GitHub), phone OTP.
- **Password reset**: "Forgot password" → email link → reset form → success.
- **Session management**: Auto-logout, session expiry, "Remember me" behavior.

### 3.4. Main Navigation & Core Screens
- **Dashboard / Home**: Primary landing screen, key metrics, quick actions.
- **List / Index views**: Browsing, filtering, searching, sorting.
- **Detail views**: Deep-dive into a single entity (e.g., a message, a task, a user profile).
- **Create / Edit screens**: Forms, validation feedback, save/cancel behavior.

### 3.5. Primary User Journeys (Goal-Oriented)
- Describe the **happiest path** for the core feature(s).
- Example (generic): *"Search for an item → Select it → View details → Take action."*
- Include **alternate paths** (e.g., "No search results found" → show empty state with suggestions).

### 3.6. State-Based UI Transitions
| State | UI Behavior |
| :--- | :--- |
| **Loading** | Show a skeleton screen, spinner, or progress bar. |
| **Empty** | Show a friendly message with a call-to-action (e.g., "No items yet. Create one!"). |
| **Success** | Show a confirmation toast, redirect to the next screen, or update UI in place. |
| **Error** | Show a user-friendly error message with a retry or "go back" option. |
| **Partially Loaded** | Show cached data while fetching fresh data in the background. |

### 3.7. Error & Boundary Flows
- **Network errors**: Offline detection, retry logic, queued actions.
- **Validation errors**: Inline field validation (red text below input, error summaries).
- **Permission errors**: What happens if the user tries an action they aren't allowed to do (e.g., redirect to login, show an access-denied modal).

### 3.8. Account & Settings Flow
- Profile editing, password change, notification preferences, connected apps/integrations.
- Deletion or deactivation flows (with confirmation dialogs).

### 3.9. Logout & Exit Flows
- Single logout, global session termination, cleanup (local storage clearing).

---

## 4. How to Document the AppFlow (Format)

An effective AppFlow document is a mix of **visual diagrams** and **structured text**.

### 4.1. Recommended Formats

| Format | When to Use | Example |
| :--- | :--- | :--- |
| **Flowchart (Mermaid/ASCII)** | For branching logic and decision points. | `Login → OTP Sent → [Valid OTP] → Dashboard` |
| **Screen List (Textual)** | For enumerating screens and their layout. | `Screen: Login` → Fields: Email, Password, Submit Button. |
| **State-Transition Table** | For mapping interactions to outcomes. | `Click "Submit" → If valid → Redirect to Dashboard` |
| **User Story Mapping** | To tie journeys back to PRD user stories. | Links `PRD-3.1` to the `Checkout` flow. |

---

## 5. AppFlow vs. Other Documents

| Document | Focus | Audience |
| :--- | :--- | :--- |
| **PRD** | *What* and *why* (features, business logic). | PMs, Designers, Devs, QA |
| **AppFlow** | *Where* and *when* (screens, navigation, state transitions). | Designers, Frontend Devs, QA, AI Agents |
| **TDD** | *How* (architecture, DB, APIs). | Backend/Fullstack Devs, Architects |
| **UI Design Spec** | *How it looks* (colors, spacing, typography). | Designers, Frontend Devs |

---

## 6. Best Practices for Writing an AppFlow

| Practice | Why |
| :--- | :--- |
| **Start with the happy path** | Map the optimal user journey first, then add edge cases. |
| **Use consistent naming** | Screen names in the AppFlow should match the actual file names (e.g., `LoginScreen`, `DashboardScreen`). |
| **Explicitly state triggers** | Define what triggers each transition (e.g., "On button click," "On API success," "On timer expiry"). |
| **Document modals and overlays** | Don't ignore dialogs, popups, and toasts—they are part of the flow. |
| **Show both logged-in and logged-out states** | Clearly differentiate what changes when the user is authenticated. |
| **Link to the PRD** | Reference the user story or requirement number (e.g., `PRD-2.3`) for traceability. |

---

## 7. Sample AppFlow Skeleton (For Your Starter Kit)

You can include this template in your vibe-coding starter kit:

```markdown
# AppFlow: [Feature/Product Name]

## 1. User Personas
- **[Persona A]** : [Goals, typical entry point]
- **[Persona B]** : [Goals, typical entry point]

## 2. Onboarding Flow
- **Splash Screen** → [Description]
- **Permissions Request** → [Description]
- **Sign-Up Screen** → [Fields, validation rules]
- **Verification Screen** → [Resend logic, expiry]
- **Profile Completion** → [Optional/Required fields]

## 3. Authentication Flow
- **Login Screen** → [Fields: Email/Password, Phone, Social buttons]
- **Forgot Password** → [Flow steps]
- **Session Expiry** → [What happens? Redirect to login with a toast?]

## 4. Main Navigation
- **Bottom Tab / Sidebar Structure** → [List of sections]
- **Section A: Dashboard** → [KPI cards, quick actions]
- **Section B: List View** → [Filters, search bar, pagination]

## 5. Core Journey: [Journey Name]
### Happy Path
1. Screen A (List) → User clicks "Create".
2. Screen B (Form) → User fills in fields and clicks "Submit".
3. API returns success → Show toast → Redirect to Screen C (Detail).
### Edge Paths
- **Scenario**: Form validation fails → Show inline errors; user stays on Screen B.
- **Scenario**: Network timeout → Show error overlay with "Retry" button.

## 6. State Handling Summary
| State | UI Reaction |
| :--- | :--- |
| Loading | [Skeleton / Spinner] |
| Empty | [Illustration + CTA] |
| Error | [Error message + Retry button] |
| Success | [Toast / Redirect] |

## 7. Account & Settings
- **Profile Screen** → Editable fields, avatar upload.
- **Notification Preferences** → Toggles for push/email.
- **Danger Zone** → Deactivate account (requires confirmation modal).

## 8. Logout Flow
- Click logout → Confirmation dialog → Clear session → Redirect to Login.