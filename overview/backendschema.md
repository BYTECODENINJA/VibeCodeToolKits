# What Is a Backend Schema? (Data Model & Database Design)

## 1. Overview

A **Backend Schema** (also called a **Data Model**, **Database Schema**, or **Entity-Relationship Diagram (ERD)**) is a structural definition of how your application stores, organizes, and relates data. It answers the question:

- *"What data does the app store, and how are those pieces connected?"*

If the **PRD** defines *what* you're building, the **AppFlow** defines *where* users go, the **Design Brief** defines *how it looks*, and the **TDD** defines *how it's built technically*, the **Backend Schema** defines the **foundation of your data layer**—tables, fields, relationships, indexes, and constraints.

In **AI-assisted ("vibe") coding**, the Backend Schema is the blueprint that tells the AI exactly which database models, Prisma/SQLAlchemy schemas, or Mongoose models to generate, preventing it from inventing incorrect relationships or duplicating data.

---

## 2. Why a Backend Schema Matters

| Benefit | Explanation |
| :--- | :--- |
| **Data Integrity** | Enforces constraints (foreign keys, uniqueness, required fields) to prevent bad data. |
| **Performance** | Proper indexing and normalization ensure fast queries as the app scales. |
| **Clarity** | Provides a single source of truth for all data relationships (who owns what). |
| **Developer Speed** | Engineers and AI agents can quickly understand the data layer and build queries/APIs confidently. |
| **Security** | Defines access boundaries (e.g., "User data is scoped to `userId`"). |
| **AI Agent Accuracy** | An AI with a complete schema will generate correct database queries, migrations, and ORM models without guesswork. |

---

## 3. Key Components of a Backend Schema

### 3.1. Entity Definitions (Tables / Collections)
Each entity represents a core object in your system. For each entity, define:

- **Entity Name**: Singular, descriptive (e.g., `User`, `Message`, `Alert`).
- **Description**: What this entity represents in plain English.
- **Primary Key**: The unique identifier (usually `id` with `UUID` or auto-incrementing integer).

### 3.2. Fields (Columns / Attributes)
For each entity, define:

| Field Property | Explanation |
| :--- | :--- |
| **Field Name** | camelCase or snake_case (following project conventions). |
| **Data Type** | `string`, `integer`, `float`, `boolean`, `timestamp`, `JSON`, `UUID`, etc. |
| **Constraints** | `required` / `optional`, `unique`, `default` value. |
| **Description** | What this field stores (e.g., "User's full display name"). |
| **Example Value** | A concrete example (e.g., `"John Doe"`, `"+1234567890"`). |

### 3.3. Relationships
Define how entities relate to each other:

| Relationship | Notation | Example |
| :--- | :--- | :--- |
| **One-to-One** | `1:1` | `User` ↔ `Profile` |
| **One-to-Many** | `1:N` | `User` → `Alert` (one user has many alerts) |
| **Many-to-Many** | `M:N` | `User` ↔ `App` (many users can connect to many apps, through a junction table like `UserApp`) |

For each relationship, specify:
- **Foreign Key**: Which field references another table's primary key.
- **Cascade Behavior**: What happens on delete (`CASCADE`, `SET NULL`, `RESTRICT`).

### 3.4. Indexes
Define which fields need indexes for fast queries:

- **Single-column indexes**: For frequently filtered fields (e.g., `email`, `phoneNumber`).
- **Composite indexes**: For combined filters (e.g., `(userId, createdAt)`).
- **Unique indexes**: For enforcing uniqueness (e.g., `email` must be unique).

### 3.5. Enums
Define shared value sets (e.g., `Status = ['PENDING', 'ACTIVE', 'ARCHIVED']`, `Priority = ['LOW', 'MEDIUM', 'HIGH', 'CRITICAL']`).

### 3.6. Audit Fields
Standard timestamps that every table should include:

| Field | Purpose |
| :--- | :--- |
| `createdAt` | When the record was created. |
| `updatedAt` | When the record was last modified. |
| `deletedAt` | Soft-delete marker (optional, if using soft deletes). |

---

## 4. Backend Schema Documentation Format

### 4.1. Recommended Structure

For each entity, use the following format:

### Entity: User

**Description**: Represents an authenticated user in the system.

| Field | Type | Constraints | Description | Example |
| :--- | :--- | :--- | :--- | :--- |
| `id` | `UUID` | PK, required | Unique identifier | `'550e8400-e29b-41d4-a716-446655440000'` |
| `email` | `string` | unique, optional | User's email address | `'alice@example.com'` |
| `phoneNumber` | `string` | unique, optional | E.164 formatted phone | `'+1234567890'` |
| `name` | `string` | optional | Display name | `'Alice Johnson'` |
| `authProvider` | `enum` | required | `'EMAIL_PASSWORD'` | `'GOOGLE'` |
| `lastLoginAt` | `timestamp` | optional | Last successful login | `'2026-08-07T10:30:00Z'` |
| `createdAt` | `timestamp` | default: `now()` | Record creation time | `'2026-08-07T10:00:00Z'` |
| `updatedAt` | `timestamp` | auto-update | Record modification time | `'2026-08-07T10:30:00Z'` |

**Relationships**:
- `1:N` → `Alert` (one user has many alerts, via `userId` foreign key)
- `M:N` → `App` (through `UserApp` junction table)

**Indexes**:
- `email` (unique)
- `phoneNumber` (unique)
- `authProvider`

### 4.2. Visual Diagrams (ERD) — Detailed Explanation
Visual diagrams are essential for communicating complex relationships at a glance. They are far more efficient than reading pages of text.

### A. Why Use Visual Diagrams?

Instant comprehension: A picture of your schema is worth a thousand lines of code.

AI-friendly: AI agents parse Mermaid/ASCII diagrams effectively.

Team alignment: Non-technical stakeholders can understand relationships without reading SQL.

### B. Recommended Tools

| Tool | Best For | Output Format |
| :--- | :--- | :--- |
| **Mermaid** | Inline diagrams in markdown files (native to GitHub/GitLab). | Live-rendered in most markdown viewers. |
| **[dbdiagram.io](https://dbdiagram.io)** | Quick, browser-based design and export. | PDF, PNG, SQL scripts. |
| **[Draw.io / diagrams.net](https://diagrams.net)** | Drag-and-drop for complex diagrams. | PNG, SVG, XML. |
| **ASCII Art** | Simple, text-only diagrams for docs without rendering support. | Plain text. |
| **[PlantUML](https://plantuml.com)** | Text-to-diagram styling for UML and workflow charts. | PNG, SVG, LaTeX. |

### C. Mermaid ERD Syntax Example

erDiagram
USER ||--o{ ALERT : creates
USER ||--o{ USER_APP : connects
APP ||--o{ USER_APP : connects
ALERT {
UUID id PK
UUID userId FK
string title
string description
enum priority
enum status
timestamp createdAt
}
USER {
UUID id PK
string email
string phoneNumber
string name
enum authProvider
timestamp lastLoginAt
}
APP {
UUID id PK
string name
string iconUrl
boolean isConnected
}
USER_APP {
UUID id PK
UUID userId FK
UUID appId FK
string accessToken
timestamp connectedAt
}
