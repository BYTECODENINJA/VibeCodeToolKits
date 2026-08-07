#  (AI Skills & Tool Integration Guide)

## 1. Overview

A **Skills Reference** (also called an **AI Skills Manifest**, **Tool Integration Guide**, or **Agent Capabilities Document**) is a centralized catalog that defines and references **all AI skills, tools, and external capabilities** that your development agent can leverage during the project.

If the **PRD** defines *what* you're building, the **AppFlow** defines *where* users go, the **Design Brief** defines *how it looks*, the **Backend Schema** defines *what data is stored*, and the **TDD** defines *how the system works*, the **Skills Reference** defines **what tools and skills are available to the AI agent** to get the job done.

In **AI-assisted ("vibe") coding**, the Skills Reference is the **toolbelt**—it tells the AI which specialized skills it can invoke, where to find them, how to configure them, and when to use them.

---

## 2. Why a Skills Reference Matters

| Benefit | Explanation |
| :--- | :--- |
| **Discoverability** | AI agents can see all available skills in one place, rather than guessing or hallucinating capabilities. |
| **Consistency** | Ensures the same skill is used for the same task across the project (e.g., always use `ui-ux-pro-max` for design system generation). |
| **Onboarding Speed** | New developers (or new AI sessions) can quickly understand what tools are available. |
| **Traceability** | Links each skill to the specific project artifact it produces (e.g., "This skill generates the Design Brief"). |
| **Configuration Centralization** | Stores all API keys, environment variables, and invocation commands in one place. |
| **AI Agent Accuracy** | An AI with a Skills Reference knows exactly which skill to invoke for which task, reducing errors and improving output quality. |

---

## 3. Key Components of a Skills Reference

### 3.1. Skill Definition
For each skill, define:

| Component | Description | Example |
| :--- | :--- | :--- |
| **Skill Name** | The official name of the skill. | `ui-ux-pro-max` |
| **Description** | What the skill does in plain English. | "Generates a complete design system with colors, typography, and components." |
| **Source / Repository** | Where to find the skill (GitHub, internal repo, npm package). | `https://github.com/nextlevelbuilder/ui-ux-pro-max-skill` |
| **Version** | Which version to use (or `latest`). | `v2.1.0` |
| **Category** | What domain the skill belongs to. | `UI/UX`, `Code Generation`, `Testing`, `Documentation` |

### 3.2. When to Use (Trigger Conditions)
Define the explicit conditions under which the AI should invoke this skill:

| Trigger | Example |
| :--- | :--- |
| **Specific task** | "When generating the design system, use `ui-ux-pro-max`." |
| **File type** | "When creating a new database migration, use `prisma-migrate` skill." |
| **User request** | "When the user asks for a new feature, invoke `feature-generator`." |

### 3.3. Usage Instructions
Provide the exact command, prompt, or configuration to invoke the skill:

| Component | Example |
| :--- | :--- |
| **Command** | `npx ui-ux-pro-max --style=minimal --output=DesignBrief.md` |
| **Prompt Template** | "Generate a design system using UI/UX Pro Max with the following parameters: [params]." |
| **API Call** | `POST /api/skills/design-system` with payload `{ style: "minimal", colors: ["#2563EB"] }` |

### 3.4. Inputs & Outputs
Document what the skill expects and what it produces:

| Aspect | Example |
| :--- | :--- |
| **Inputs** | Reference image, style preferences, brand guidelines. |
| **Outputs** | `DesignBrief.md` with color tokens, typography, component styles. |
| **Artifacts** | Generated files (e.g., `theme.css`, `tailwind.config.js`, `design-system.json`). |

### 3.5. Dependencies & Prerequisites
List any required setup before the skill can run:

| Item | Example |
| :--- | :--- |
| **Environment Variables** | `UI_UX_API_KEY=xyz` |
| **Packages** | `npm install -g ui-ux-pro-max` |
| **Permissions** | Write access to the `agentAssets/` folder. |
| **Network Access** | Internet connection to fetch font files. |

### 3.6. Example Invocation
Provide a concrete example of how the AI would call the skill in practice:

```markdown
### Example: Generating a Design Brief

**User Request**: "Generate the design system for my dashboard app."

**Agent Action**:
1. Invoke `ui-ux-pro-max` skill.
2. Pass parameters: `{ style: "modern", colorPalette: "blue", output: "agentAssets/DesignBrief.md" }`.
3. Receive `DesignBrief.md` and `tailwind.config.js`.
4. Place outputs in the project root.

```
---

## 4. For AI-Assisted ("Vibe") Coding

When using a Skills Reference in a vibe-coding workflow, it becomes the **agent's playbook**. Here's how to optimize it:

1.  **Position it prominently**: Tell the AI to read the Skills Reference *before* starting any task. Include it in your initial prompt.
2.  **Use consistent naming**: The skill names in the Skills Reference should match the exact commands the AI will run.
3.  **Provide fallback instructions**: If a skill fails, what should the AI do? (e.g., "If the UI skill fails, generate a minimal manual design using CSS variables.").
4.  **Link to the PRD**: Map skills to PRD sections (e.g., "To fulfill PRD-3.2, use the `doc-generator` skill to create the User Stories.").
5.  **Keep it up to date**: If you add a new skill during the project, update the Skills Reference immediately so the AI knows it's available.

---

## 5. Relationship to Your Starter Kit Documents

Here is how the Skills Reference fits into your complete documentation suite:

| Document | Purpose |
| :--- | :--- |
| **PRD** | *What* and *why* (requirements, business logic). |
| **AppFlow** | *Where* and *when* (screens, navigation, user journeys). |
| **Design Brief** | *How it looks and feels* (visual identity, brand, UI tokens). |
| **Backend Schema** | *What data is stored and how it relates* (tables, fields, relationships). |
| **TDD (Technical Design)** | *How the system works* (architecture, APIs, infrastructure). |
| **Skills Reference** | *What tools and skills are available* to the AI agent. |
| **Context Library** | External context (API docs, ORM docs, book references). |
| **Definition of Done** | The final checklist for verifying everything works. |

---

## 6. Summary

| Aspect | Takeaway |
| :--- | :--- |
| **Core Purpose** | Catalog and define all AI skills, tools, and capabilities available for the project. |
| **Key Audience** | AI Agents, Developers setting up the environment. |
| **Essential Sections** | Skill definitions, trigger conditions, usage instructions, inputs/outputs, dependencies, examples. |
| **Vibe-Coding Value** | Gives the AI a clear toolbelt, ensuring it uses the right skill for the right task. |
| **Living Document** | Must be updated whenever new skills are added or existing skills are updated/removed. |

> A well-maintained Skills Reference transforms your AI agent from a generic code generator into a specialized craftsman with a curated toolkit—knowing exactly which tool to reach for at each step of the project.