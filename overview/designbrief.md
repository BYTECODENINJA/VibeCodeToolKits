# (Visual Identity & UI Design System)

## 1. Overview

A **Design Brief** (also called a **Visual Design Specification**, **Style Guide**, or **Brand Guidelines**) is a document that defines the **look, feel, and aesthetic personality** of your application. It answers the question:

- *"What should the app look and feel like?"*

If the **PRD** defines *what* you're building, the **AppFlow** defines *where* users go, and the **TDD** defines *how* it's coded technically, the **Design Brief** defines the *visual language*—colors, typography, spacing, component styles, motion, and brand tone.

In **AI-assisted ("vibe") coding**, the Design Brief is the instruction manual that tells the AI which CSS classes, hex codes, and component libraries to use, preventing it from generating random or inconsistent UI.

---

## 2. Why a Design Brief Matters

| Benefit | Explanation |
| :--- | :--- |
| **Brand Consistency** | Ensures every screen looks like it belongs to the same product, building user trust. |
| **Developer Speed** | Engineers and AI agents can quickly build new screens without guessing colors or spacing. |
| **Accessibility** | Forces you to define contrast ratios, focus states, and inclusive design upfront. |
| **Reduced CSS Sprawl** | Prevents one-off styling; encourages reusable design tokens. |
| **AI Agent Accuracy** | An AI with a Design Brief knows exactly which `tailwind` classes, `shadcn` themes, or `styled-components` to use, rather than inventing its own. |

---

## 3. Key Components of a Design Brief

### 3.1. Brand Personality & Tone
- **Define the mood**: Minimalist, corporate, playful, edgy, trustworthy, friendly, technical.
- **Describe the vibe**: "Clean and airy with bold accents" or "Dark, moody, and technical."
- **Visual references**: Links to Pinterest boards, Dribbble shots, or existing competitor sites that match the desired aesthetic.

### 3.2. Color Palette
Define explicit colors with **hex values** and their intended usage.

| Category | Purpose | Example Hex Values |
| :--- | :--- | :--- |
| **Primary** | Main brand color (buttons, links, headers). | `#2563EB` (blue) |
| **Secondary** | Supporting accent (badges, highlights). | `#8B5CF6` (purple) |
| **Neutral / Grayscale** | Backgrounds, text, borders, dividers. | `#FFFFFF`, `#F3F4F6`, `#1F2937` |
| **Success** | Positive feedback, completed states. | `#22C55E` |
| **Warning** | Caution, pending states. | `#EAB308` |
| **Error / Danger** | Errors, destructive actions. | `#EF4444` |
| **Info** | General information, informational banners. | `#3B82F6` |

### 3.3. Typography
Define the font hierarchy and styling rules.

| Element | Font / Weight | Size | Usage |
| :--- | :--- | :--- | :--- |
| **Headings** | Inter Bold, `600`/`700` | 24–36px | Page titles, section headers |
| **Body Text** | Inter Regular, `400` | 16px | Paragraphs, descriptions |
| **Small Text** | Inter Regular, `400` | 12–14px | Helper text, timestamps, metadata |
| **Monospace** | JetBrains Mono | 14px | Code blocks, technical data |

- **Font Import**: Include Google Fonts or system font stack.
- **Line-height**: 1.5 for body, 1.2 for headings.
- **Letter-spacing**: Optional for special headings.

### 3.4. Spacing & Layout Grid
Define a consistent spacing scale (based on a factor, typically 4px or 8px).

| Token | Value | Usage |
| :--- | :--- | :--- |
| `space-1` | 4px | Icon margins, tight spacing |
| `space-2` | 8px | Padding inside compact components |
| `space-3` | 12px | Between related elements |
| `space-4` | 16px | Standard padding, card margins |
| `space-6` | 24px | Section spacing |
| `space-8` | 32px | Major layout breaks |

- **Container width**: Max-width (e.g., 1280px) for centered layouts.
- **Grid system**: 12-column grid (or 8/16) with defined gutters.

### 3.5. UI Component Styles
Define how common UI elements look:

| Component | Style Rules |
| :--- | :--- |
| **Buttons** | Border-radius: 6–8px. Padding: `space-2` `space-4`. Primary (solid), Secondary (outline). Hover/active states. |
| **Inputs** | Border color: neutral-300. Focus ring: primary-500 with `box-shadow` or `ring`. |
| **Cards** | Background: white. Border: 1px solid neutral-200. Border-radius: 8px. Optional shadow. |
| **Badges** | Small pill shapes for status (success, warning, error). |
| **Modals** | Centered overlay. Max-width: 500px. Padding: `space-6`. |

### 3.6. Motion & Interaction
- **Transition speeds**: Fast (150ms) for hover states; Medium (300ms) for modal entries.
- **Easing curves**: `ease-in-out` for toggles, `ease-out` for reveals.
- **Micro-interactions**: Button press feedback (scale 0.98), skeleton loading shimmer.

### 3.7. Accessibility Requirements
- **Contrast ratios**: Text must be AA compliant (4.5:1 for normal text, 3:1 for large text).
- **Focus states**: Clear visible focus rings (e.g., `ring-2 ring-primary-500`) for keyboard navigation.
- **ARIA labels**: Guidance for screen readers (e.g., icon-only buttons must have `aria-label`).

---

## 4. Design Brief vs. Other Documents

| Document | Focus | Audience |
| :--- | :--- | :--- |
| **PRD** | *What* and *why* (business logic, features). | PMs, Devs, QA |
| **AppFlow** | *Where* and *when* (screens, navigation, states). | Designers, Frontend Devs, QA, AI |
| **Design Brief** | *How it looks and feels* (visual identity, brand). | Designers, Frontend Devs, AI |
| **TDD** | *How it works* (architecture, API, DB). | Backend/Fullstack Devs, Architects |

---

## 5. Best Practices for Writing a Design Brief

| Practice | Why |
| :--- | :--- |
| **Be specific with hex codes and pixel values** | "Primary blue" is too vague; `#2563EB` is exact and machine-readable. |
| **Provide visual examples** | Include screenshots, mockups, or UI pattern links for clarity. |
| **Document only what's necessary** | Don't over-engineer it; focus on colors, fonts, spacing, and core components. |
| **Map styles to a framework** | If using Tailwind CSS, map the color names to Tailwind config (e.g., `primary-500: #2563EB`). |
| **Set responsive breakpoints** | Define how the UI scales (mobile, tablet, desktop) with explicit breakpoints. |
| **Keep it living** | Update the Design Brief when the brand evolves. |

---

## 6. Sample Design Brief Skeleton (For Your Starter Kit)

You can include this template in your vibe-coding starter kit:

```markdown
# Design Brief: [Product/App Name]

## 1. Brand Personality
- **Mood**: [e.g., Minimalist, Modern, Friendly, Trustworthy]
- **Vibe**: [e.g., "Clean, spacious, with bold accent colors to guide focus."]
- **Visual References**: [Links to Dribbble, Pinterest, or competitor analyses]

## 2. Color Palette
| Role | Hex | Tailwind Class (if applicable) | Usage |
| :--- | :--- | :--- | :--- |
| Primary | `#2563EB` | `blue-600` | Buttons, links, headers |
| Secondary | `#8B5CF6` | `purple-500` | Badges, highlights |
| Background | `#F9FAFB` | `gray-50` | Main page background |
| Text Primary | `#111827` | `gray-900` | Headings, body text |

## 3. Typography
- **Font**: Inter (Google Fonts)
- **Hierarchy**:
  - `H1`: Inter Bold, 32px, 1.2 line-height.
  - `H2`: Inter Semi-Bold, 24px, 1.3 line-height.
  - `Body`: Inter Regular, 16px, 1.5 line-height.
  - `Small`: Inter Regular, 14px, 1.4 line-height.

## 4. Spacing Scale
- Base unit: `4px` (`1` = 4px, `2` = 8px, `4` = 16px, `6` = 24px, `8` = 32px)

## 5. Component Styles
- **Buttons**: Border-radius 8px. Padding 10px 20px.
  - Primary: Background primary, white text. Hover: darker shade.
  - Secondary: Background transparent, primary border.
- **Cards**: White background, 1px solid border, border-radius 12px, padding 24px.
- **Inputs**: 1px solid border, focus ring primary-500, padding 10px 14px.

## 6. Motion & Animation
- **Transitions**: 200ms ease-in-out for hover states.
- **Modals**: Slide-up from bottom on mobile; fade-in on desktop.

## 7. Accessibility
- Minimum contrast: 4.5:1 for body text.
- Focus rings: 2px solid primary-500 on all interactive elements.

## 8. Responsive Breakpoints
- **Mobile**: `max-width: 640px`
- **Tablet**: `641px – 1024px`
- **Desktop**: `1025px+`