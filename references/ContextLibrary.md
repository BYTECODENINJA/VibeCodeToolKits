# (Centralized Reference & Source Material)

## 1. Overview

A **Context Library** (also called a **Source Vault**, **Asset Repository**, or **Knowledge Base**) is a centralized collection of **external, static, or third-party reference materials** that inform and constrain the development of your project. It serves as the **input vault**—the raw source material that the AI agent consumes to understand the problem domain, brand identity, technical constraints, and external dependencies.

If the **PRD** defines *what* you're building, the **TDD** defines *how* you're building it, and the **Implementation Summary** documents *what was built*, the **Context Library** answers:

- *"What external references, assets, and source materials are we using to guide this project?"*

In **AI-assisted ("vibe") coding**, the Context Library is the **AI's reference shelf**—it provides all the external documentation, design references, brand assets, API specifications, and research materials the agent needs without requiring the AI to search the web or hallucinate details.

---

## 2. Why a Context Library Matters

| Benefit | Explanation |
| :--- | :--- |
| **Reduces Hallucinations** | When the AI has explicit reference materials (images, PDFs, API docs), it doesn't need to guess or invent details. |
| **Saves Tokens** | Instead of pasting long reference materials into every prompt, the agent reads them from the Context Library once. |
| **Single Source of Truth** | Ensures everyone (human and AI) is looking at the same reference image, API spec, or brand guideline. |
| **Accelerates Onboarding** | New AI agents (or new team members) can instantly access all relevant context without searching through emails or chat history. |
| **Decouples Source from Output** | Clearly separates *input material* (what you reference) from *output artifacts* (what you produce). |
| **Version Control** | Changes to the reference materials can be tracked over time, ensuring the AI always works with the latest version. |

**Key Insight**: The Context Library is **passive** (it exists before the project starts and changes infrequently), whereas documents like the PRD, TDD, and Implementation Summary are **active** (they evolve with the project).

---

## 3. Key Components of a Context Library

### 3.1. External Documentation
- **API Specifications**: OpenAPI/Swagger files, Postman collections, or raw API docs.
- **Third-Party SDKs**: Links to or snapshots of official SDK documentation.
- **Database Schemas**: Pre-existing database schemas you are integrating with.
- **External Services**: Docs for services you rely on (e.g., OTP providers, payment gateways, AI APIs).

### 3.2. Design & Brand Assets
- **Brand Guidelines**: Color palettes, typography, logo files, brand tone.
- **Design Mockups**: Figma exports, Sketch files, or static images of intended UI.
- **Reference Images**: Screenshots, mood boards, or competitor analyses (like your `image.png`).
- **Font Files**: Custom or licensed font assets.

### 3.3. Research & Discovery
- **User Research**: Interview transcripts, survey results, persona documents.
- **Competitor Analysis**: Screenshots, feature matrices, or written comparisons.
- **Industry Standards**: Regulatory requirements, compliance checklists, best-practice guides.

### 3.4. Domain-Specific Knowledge
- **Glossaries**: Definitions of domain-specific terminology.
- **Business Rules**: Any hardcoded business logic that isn't covered in the PRD.
- **Data Dictionaries**: Definitions for domain-specific data fields.

### 3.5. Code & Infrastructure References
- **Existing Codebases**: If the project extends an existing system, include relevant source files or documentation.
- **Infrastructure Diagrams**: Existing network architectures, cloud configurations, or deployment models.

---

## 4. Context Library vs. Other Documents

| Document | Purpose | Content Type | Lifecycle |
| :--- | :--- | :--- | :--- |
| **PRD** | *What* and *why* (requirements). | Active output | Evolves with project. |
| **TDD** | *How* the system works (architecture, APIs). | Active output | Evolves with project. |
| **Implementation Summary** | *What was built* (final report). | Active output | Completed at project end. |
| **Skills Reference** | *What tools are available* to the agent. | Active index | Updated when tools change. |
| **Context Library** | *The actual external source materials* themselves. | **Passive input** | Mostly static; updated when new source materials arrive. |

**Key Distinction**:
- The **Context Library** is the **vault**—it contains the actual images, PDFs, JSON files, and assets referenced by the project.

---

## 5. Recommended Folder Structure

For a vibe coding starter kit, the Context Library can be organized as follows:

```text
context/                         # Root of the Context Library
├── api-specs/                   # OpenAPI, Postman collections
│   ├── auth-api.json
│   ├── payment-gateway.yaml
│   └── external-api-docs.pdf
├── design-assets/               # Brand, UI, mockups
│   ├── brand-guidelines.pdf
│   ├── logo.png
│   ├── ui-mockups/              # Figma exports or images
│   │   ├── login-screen.png
│   │   ├── dashboard.png
│   │   └── reference-image.png  # (like your image.png)
│   └── fonts/
│       └── custom-font.ttf
├── research/                    # User research, competitor analysis
│   ├── user-personas.md
│   ├── competitor-analysis/
│   │   ├── competitor-a-screenshots/
│   │   └── feature-matrix.md
│   └── industry-standards/
│       └── compliance-checklist.md
├── business-rules/              # Domain logic, glossaries
│   ├── glossary.md
│   └── business-logic-rules.md
├── references/                  # Or just keep References.md here
│   └── References.md            # The index of all links and descriptions
└── README.md                    # Explain what's in the Context Library
```

---

## 6. Best Practices for Maintaining a Context Library

| Practice | Why |
| :--- | :--- |
| **Keep it organized** | Use clear folders and file names so agents (and humans) can find what they need quickly. |
| **Version large files** | For large PDFs or images, use version control (Git LFS or a separate asset store). |
| **Don't duplicate active docs** | The Context Library is for *passive input* only. Do not store PRDs, TDDs, or Summaries here—they belong elsewhere (e.g., `delivery/`). |
| **Use relative paths** | References in your prompts should point to the Context Library using relative paths (e.g., `context/design-assets/ui-mockups/login-screen.png`). |
| **Keep it accessible** | Place the Context Library at the root of your project or in a well-known location (e.g., `agentAssets/context/`). |

---

## 7. How AI Agents Use the Context Library

### 7.1. During Initialization
At the start of the project, the agent reads the Context Library to understand:
- What the UI should look like (from mockups).
- What external APIs are available (from API specs).
- What brand guidelines to follow (from design assets).

### 7.2. During Implementation
When the agent needs to reference an external service or design detail:
- It retrieves the relevant file from the Context Library.
- It uses the actual file (not a vague memory) to guide its code generation.

### 7.3. During Handoff
If a new agent joins the project:
1. It browses the Context Library folders to understand the full landscape of source materials.
2. It gains context without requiring the user to re-upload or re-explain every asset.

### 7.4. During Verification
When the agent writes the Implementation Summary:
- It references the Context Library to confirm that the implemented UI matches the mockups.
- It validates that the implemented APIs comply with the provided API specs.

---

## 8. Relationship to Your Starter Kit Documents

| Document | Purpose | Role in the Agent Workflow |
| :--- | :--- | :--- |
| **Context Library** | Provides **source materials** (images, PDFs, API specs, brand assets). | **Input** – What the agent consumes to understand the project. |
| **PRD** | Defines *what* to build. | **Plan** – Informs the agent's output. |
| **AppFlow** | Defines *where* users go. | **Plan** – Informs the agent's output. |
| **Design Brief** | Defines *how it looks*. | **Plan** – Informs the agent's output (often derived from the Context Library). |
| **Backend Schema** | Defines *data relationships*. | **Plan** – Informs the agent's output. |
| **TDD** | Defines *how the system works*. | **Plan** – Informs the agent's output. |
| **Skills Reference** | Defines *what tools are available*. | **Tooling** – Informs the agent's execution. |
| **Implementation Checklist** | Tracks *progress*. | **Tracking** – Guides the agent's daily work. |
| **Implementation Summary** | Documents *what was built*. | **Output** – The agent's final deliverable. |

---

## 9. Summary

| Aspect | Takeaway |
| :--- | :--- |
| **Core Purpose** | Centralize all external, static, and reference materials for the project. |
| **Key Audience** | AI Agents (primary), Developers, Designers. |
| **Content Type** | Passive input: images, PDFs, JSON/OpenAPI files, brand assets, research. |
| **Lifecycle** | Mostly static; updated when new source materials are added. |
| **Vibe-Coding Value** | Prevents AI hallucinations, reduces token waste, accelerates onboarding, and provides a single source of truth for external information. |

> A well-organized Context Library ensures that every AI agent working on your project—whether the original or a newcomer—has instant access to the exact same reference materials. This eliminates guesswork, enforces consistency, and dramatically improves the quality of AI-generated outputs.