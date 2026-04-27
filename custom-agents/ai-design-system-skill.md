# AI Design System Skill
### Build a Production-Ready Design System with AI — From Inspiration to Code

> **Compatible with:** Claude · Claude Code · Gemini · ChatGPT · Codex · Figma Make · Cursor · Antigravity · Any LLM with file/project context
> **Use as:** Custom Agent Skill · Knowledge Base · Project Context · System Prompt module

---

## Purpose & Scope

This skill guides an AI agent (or a human working with AI tools) through a complete, end-to-end design system workflow — from gathering visual inspiration, generating UI pages, extracting a coherent design system, to refactoring production code with design tokens.

The output is a consistent, maintainable, and scalable UI system that can be handed off to any developer or AI coding tool.

---

## Prerequisites

Before executing this workflow, confirm the following are in place:

- [ ] A **Product Requirements Document (PRD)** exists with user stories defined
- [ ] The list of **pages** the UI will contain is known
- [ ] The **content and components** for each page are understood
- [ ] A preferred **tech stack** is identified (e.g., React + Tailwind CSS, Next.js, Vue, etc.)
- [ ] A **design reference company** (or visual style) is identified to use as inspiration anchor

---

## The 5-Step Process

```
Step 1: Collect Inspiration     → Gather UI references for every page and component
Step 2: Create a Mood Board     → Organise inspiration in Figma
Step 3: Generate UI Pages       → Use Figma Make (or equivalent) to create initial designs
Step 4: Extract Design System   → Generate a minimum viable design system
Step 5: Refactor for Production → Clean up code using design tokens
```

---

## Step 1 — Collect Inspiration

### What to Collect

Gather reference screenshots for every page and component type your product contains.

**Pages**
- Every unique page layout (dashboard, list view, detail view, settings, onboarding)
- Empty states (no data loaded)
- Populated states (with realistic data)
- Error states and fallback screens

**Components**
- Buttons: primary, secondary, ghost, destructive, icon-only
- Form inputs: default, focus, error, disabled
- Dropdowns/selects: closed and open states
- Modals and dialogs
- Cards (basic, interactive, with metadata)
- Tables (with sorting, row selection, bulk actions)
- Navigation: header, sidebar, tabs, breadcrumbs
- Badges and tags: all color/status variants
- Avatars: single and stacked
- Alerts and notifications (inline and toast)
- Dashboards: metric cards, charts, sparklines

**States**
- Hover states for all interactive elements
- Active / selected states
- Loading and skeleton states
- Disabled states

---

### Where to Find Inspiration

| Source | Best For |
|---|---|
| **mobbin.com** | Curated real-product UI screenshots, filterable by component or company |
| **dribbble.com** | Polished visual concepts and component explorations |
| **screenlane.com** | Mobile UI patterns |
| **uigarage.net** | Component-level inspiration |
| **Linear.app** | Reference for clean B2B SaaS aesthetics |
| **Notion / Deel / Vercel** | Reference for minimal, high-information-density UIs |

> **Pro Tip:** Identify 1–2 companies whose visual language you want to emulate. Use them as a consistent anchor throughout the process. This gives the AI a clear aesthetic target. **Don't mix styles from different companies** — conflicting references produce inconsistent output.

---

### Step 1 Action Items

- [ ] Identify 1–2 companies whose design style you want to emulate
- [ ] Collect screenshots for each unique page type in your app
- [ ] Collect screenshots for each component type you will need
- [ ] Note specific interactions and states (hover, selected, loading, error)
- [ ] Organise all screenshots in a local folder or Figma canvas before proceeding

---

## Step 2 — Create Your Mood Board

Organise all collected inspiration into a structured mood board in Figma (or a Figma-equivalent canvas). This document becomes the single source of truth for all AI design generation.

### Mood Board Structure

Create clearly labelled sections:

| Section | Contents |
|---|---|
| **Navigation** | Headers, sidebars, breadcrumbs |
| **Pages** | Full-page layouts for each screen type |
| **Components** | Buttons, inputs, cards, tables, modals |
| **States** | Hover, active, disabled, loading, empty |
| **Typography** | Font scale samples, heading hierarchy |
| **Color Palettes** | Brand colors, semantic status colors |

### Best Practices

1. Keep the board clean and scannable — add clear labels to every group
2. Include annotations about what you like about each reference (e.g., "tight spacing here", "love how the badge variants are handled")
3. Group related elements physically close together
4. Include both full-page layouts **and** close-up component details
5. Document different states for every interactive element
6. Avoid overloading the board — curate, don't dump
7. Keep it scannable — **Figma Make reads the mood board visually**, so spatial organisation and clear grouping directly affects generation quality

---

### Step 2 Action Items

- [ ] Create a new Figma file dedicated to this mood board
- [ ] Set up labelled sections for each category above
- [ ] Paste and organise all collected screenshots
- [ ] Add concise annotations and notes
- [ ] Review for completeness — every page and component type should be represented

---

## Step 3 — Generate UI Pages

### Tooling

Use **Figma Make** (`make.figma.com`) as the primary UI generation tool. It accepts image references and text prompts and produces functional prototypes directly in Figma.

Alternatives for non-Figma workflows:

| Tool | How to Use |
|---|---|
| **V0 by Vercel** (`v0.dev`) | Prompt-to-React component generation |
| **Lovable** (`lovable.dev`) | Full-app generation from prompts |
| **Google AI Studio** | Multimodal design exploration with Gemini |
| **Claude / ChatGPT + image** | Upload mood board screenshot + prompt |

---

### Which Pages to Generate First

Prioritise pages that expose the most design elements in one shot:

| Priority | Page | Why |
|---|---|---|
| 1 | Navigation / Header | Establishes overall visual structure |
| 2 | Table / List View | Surfaces avatars, badges, buttons, status indicators in one place |
| 3 | Dashboard | Exercises cards, charts, and metric displays |
| 4 | Form Page | Exposes inputs, dropdowns, and validation states |
| 5 | Detail / Profile Page | Complex component composition |

---

### Quick Prompt: Generate a Page in Figma Make

When working directly inside Figma Make with a reference screenshot already selected, use this minimal prompt to get started fast:

```
Generate this page matching the reference style.
```

Then iterate with follow-up prompts to refine layout, spacing, or component details.

---

### Prompt: Generate a UI Page (Detailed)

```
You are a senior product designer.

Using the attached reference image(s) as visual style inspiration — not to copy exactly —
generate a [PAGE NAME] UI for [PRODUCT DESCRIPTION].

Requirements:
- Tech stack: [React + Tailwind CSS / plain HTML+CSS / etc.]
- Visual style: reference the attached mood board
- Include realistic placeholder content (not Lorem Ipsum for labels or CTAs)
- Build for desktop (1280px wide) unless specified otherwise
- All interactive states should be represented (hover, active, disabled)
- Use a component-first structure: avoid inline one-off styles

Page-specific requirements:
[Describe the page content, data shown, and user actions here]
```

---

### Prompt: Generate a Specific Component

```
You are a senior UI engineer specialising in design systems.

Generate a [COMPONENT NAME] component in [React TSX / HTML+CSS] using Tailwind CSS.

Visual reference: [describe or attach image]
Variants needed: [primary, secondary, ghost, destructive / or list specific variants]
States needed: [default, hover, focus, active, disabled, loading]

Rules:
- Use design tokens / CSS variables — no hardcoded hex values
- Use semantic class names
- Export each variant clearly
- Include a usage example at the bottom
- Accessibility: correct ARIA roles, keyboard navigable, focus rings visible
```

---

### Step 3 Action Items

- [ ] Generate the navigation / header design first
- [ ] Generate 2–3 main page layouts
- [ ] Generate component-level explorations for complex components (tables, forms)
- [ ] Generate component states as needed (e.g., table in bulk-edit mode, form with errors)
- [ ] Review and adjust each design before proceeding
- [ ] Organise all generated designs in your Figma file

---

## Step 4 — Extract Your Design System

Once UI pages have been generated, use AI to derive a coherent, reusable design system from them. This is the step that ensures cross-page visual consistency.

---

### Prompt: Generate the Minimum Viable Design System

Use this prompt in Figma Make (with your generated pages selected), or paste into Claude / ChatGPT with screenshots attached:

```
Based on the generated UI pages provided, create a Minimum Viable Design System.
Output should be a single structured reference page.

COLORS
- 3–4 Background colors (page background, card, subtle/muted, overlay)
- 3 Text colors (primary, secondary, muted/disabled)
- 2 Border colors (default, strong/emphasis)
- 1–2 Action colors (primary button, hyperlink)
- 4 Status color sets — each with background, border, and text values:
  success | info | warning | error

TYPOGRAPHY
- Heading 1: font-size, font-weight, line-height
- Heading 2: font-size, font-weight, line-height
- Heading 3: font-size, font-weight, line-height
- Body: font-size, font-weight, line-height
- Small / Caption: font-size, font-weight, line-height
- Specify font family choices with fallback stack

SPACING & LAYOUT
- Base spacing unit (e.g., 4px)
- Spacing scale: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96
- Border radius values: tags/badges, inputs, cards, modals, pills
- Standard gap values for flex/grid layouts

SHADOWS
- shadow-sm (subtle elevation, inputs and cards)
- shadow-md (dropdowns, popovers)
- shadow-lg (modals, dialogs)

ICONS
- Specify icon library (e.g., Lucide React, Heroicons, Phosphor)
- Size scale: 14px (small), 16px (default), 20px (large), 24px (x-large)

COMPONENTS — provide 1 example each, showing all variants:
- Button (primary, secondary, ghost, destructive — all with disabled state)
- Input (default, focus, error, disabled)
- Card (basic structure with header, body, footer slots)
- Badge / Tag (success, info, warning, error, neutral)
- Avatar (with initials fallback and color palette)
- Table (header row + 1 data row, with sort indicator)
- Dropdown / Select (closed and open states)
- Modal / Dialog (header, body, footer with actions)

OUTPUT FORMAT:
Return this as a structured CSS/Tailwind token file AND a visual reference layout.
If generating code, output a tokens.css file with CSS custom properties.
```

---

### Prompt: Generate the CSS Design Token File

Use this in Claude Code, Cursor, or Codex after the design system has been visually defined:

```
Based on the design system defined above, generate a complete design token file.

Output: /styles/tokens.css (or /styles/globals.css if using Next.js/Tailwind)

Format: CSS custom properties under :root {}

Include tokens for:
- Color: --color-bg-page, --color-bg-card, --color-bg-muted, --color-bg-overlay
- Color: --color-text-primary, --color-text-secondary, --color-text-muted, --color-text-disabled
- Color: --color-border-default, --color-border-strong
- Color: --color-action-primary, --color-action-link
- Color status sets (bg/border/text) for: success, info, warning, error, destructive
- Typography: --font-family-heading, --font-family-body
- Typography: --font-size-h1 through --font-size-caption
- Typography: --font-weight-heading, --font-weight-body
- Typography: --line-height-heading, --line-height-body
- Spacing: --spacing-1 through --spacing-24 (multiples of 4px)
- Radius: --radius-sm, --radius-md, --radius-lg, --radius-full
- Shadow: --shadow-sm, --shadow-md, --shadow-lg
- Z-index: --z-dropdown, --z-modal, --z-toast

Also generate the corresponding Tailwind extend block for tailwind.config.ts.

Rules:
- All values must reference CSS custom properties — no hardcoded literals in component classes
- Add a clear comment block at the top documenting the design system name, version, and date
```

---

### Important Notes on Design System Scope

> The first time you generate a design system with AI, it may produce something very comprehensive — including loading states, empty states, modals, and edge-case components. While thorough, this can be too large for AI coding tools like Cursor to process as a single context.

**Recommended approach:**

1. Start with the **Minimum Viable Design System** prompt above
2. Verify visual consistency across generated pages
3. If more detail is needed, **split the design system into multiple context files** and feed them to Cursor / Claude Code one at a time via MCP or file attachments
4. Maintain a single `tokens.css` as the source of truth — never hardcode values in components

---

### Step 4 Action Items

- [ ] Select all generated UI pages
- [ ] Run the design system extraction prompt
- [ ] Review the generated design system — is it consistent with the mood board?
- [ ] Simplify if it is too detailed — start minimal
- [ ] Generate the CSS token file
- [ ] Copy the final design system to your main Figma file and your codebase

---

## Step 5 — Refactor for Production

Figma Make and AI-generated code often contains hardcoded values (hex codes, arbitrary spacing, pixel values). Before this code enters production, it must be refactored to use design tokens. This prevents the **spaghetti code** problem where styles are inconsistent, unthemeable, and impossible to maintain.

---

### Two Paths to Production

| Path | When to Use |
|---|---|
| **Option A: Push code directly** | Figma Make's generated code matches your stack. Push to GitHub → open in Cursor → run refactoring prompt. |
| **Option B: Figma MCP** | Keep designs in Figma. Use Figma MCP integration in Cursor to rebuild components from scratch in your preferred stack, referencing the Figma design tokens. |

---

### Prompt: Refactor Codebase for Design Tokens

Use this in Cursor, Claude Code, or Codex as a full-codebase audit prompt:

```
Audit the entire codebase and refactor all hardcoded design values to use design tokens,
following senior UI engineer best practices.

AUDIT SCOPE:
- All component files (UI components, page components, shared/layout components)
- Check for hardcoded: colors, spacing, typography, borders, shadows, radii, breakpoints

REFACTOR CATEGORIES:

1. COLORS
   - Background colors       → bg-* tokens       (bg-card, bg-primary, bg-muted, bg-accent)
   - Text colors             → text-* tokens     (text-foreground, text-muted-foreground, text-primary)
   - Border colors           → border-* tokens   (border-border, border-input)
   - State/semantic colors   → semantic variants (success, info, warning, error, destructive)
   - Arbitrary hex values    → CSS variable refs (bg-[var(--color-bg-card)])

2. SPACING
   - Arbitrary values like p-[24px]  → spacing scale tokens (p-6)
   - Gap values                      → consistent gap-* tokens
   - Margin / padding                → standardise to spacing scale

3. TYPOGRAPHY
   - Hardcoded font-size classes     → typography scale tokens
   - Hardcoded font-weight           → design system weight tokens
   - Hardcoded line-height           → standardise or defer to CSS

4. BORDERS
   - border-gray-200       → border-border
   - Arbitrary widths      → standard border-* classes
   - Border radius         → radius tokens (rounded-sm, rounded-md, rounded-lg, rounded-full)

5. SHADOWS
   - Arbitrary shadow-[...] → shadow-sm / shadow-md / shadow-lg
   - Custom shadows          → define in CSS variables

6. OPACITY & TRANSPARENCY
   - Arbitrary opacity values → Tailwind opacity scale (/90, /80, /70, /60)
   - Hover state opacity      → consistent patterns across components

SYSTEMATIC APPROACH:
1. Start with the design system foundation (/styles/globals.css or tokens.css)
2. Refactor UI primitive components first (Button, Input, Badge, Card)
3. Then refactor composite / page-level components
4. Then refactor shared and layout components
5. Verify visual design is pixel-perfect identical after each major section

OUTPUT RULES:
- Work file-by-file, systematically
- Group related changes within each file
- Use fast_apply_tool for all edits (Cursor-specific)
- Document any intentional exceptions with inline comments

VALIDATION CHECKLIST:
□ All components use design tokens from CSS variables
□ No hardcoded hex codes remain (except documented exceptions)
□ Consistent spacing scale used throughout
□ Typography follows the system scale
□ All borders use standard tokens
□ Visual design is pixel-perfect identical to pre-refactor
□ Code is maintainable, themeable, and ready for dark mode
```

---

### Prompt: Dark Mode Extension

After the refactor is complete, use this prompt to extend the design system with dark mode support:

```
The codebase has been fully refactored to use CSS design tokens in /styles/tokens.css.

Extend the design system to support dark mode using the following approach:
- Use a [data-theme="dark"] attribute on the root <html> element (preferred)
  OR the @media (prefers-color-scheme: dark) query if system-preference-only
- Override all --color-* tokens with dark-mode-appropriate values
- Do NOT use separate dark: utility classes on individual components
  (the token-based approach handles theming at the root level)

Dark mode color mapping guidelines:
- Page background → very dark neutral (e.g., #0a0a0a or #111113)
- Card background → one step lighter than page (e.g., #18181b)
- Muted background → another step lighter (e.g., #27272a)
- Primary text → near-white (e.g., #fafafa)
- Secondary text → mid-gray (e.g., #a1a1aa)
- Borders → subtle (e.g., #27272a for default, #3f3f46 for strong)
- Status colors → desaturate slightly and reduce brightness for dark surfaces
- Shadows → reduce opacity significantly (dark UIs need lighter, more subtle shadows)

Deliverables:
1. Updated tokens.css with a [data-theme="dark"] {} block
2. A ThemeToggle component that sets the data-theme attribute and persists to localStorage
3. Verify no component needs per-class dark: overrides — if any do, fix the token instead
```

---

### Prompt: Accessibility Audit

Run this after the design system is in place to validate WCAG compliance:

```
Perform an accessibility audit of the design system and all UI components.

Scope:
1. COLOR CONTRAST
   - Check all text/background color token combinations against WCAG AA (4.5:1 for body, 3:1 for large text)
   - Flag any failing combinations and suggest token adjustments

2. INTERACTIVE ELEMENTS
   - All buttons, links, and inputs must have visible :focus-visible ring styles
   - Focus ring must use --color-action-primary or a dedicated --color-ring token
   - Ensure focus ring is not suppressed with outline: none without a replacement

3. COMPONENT SEMANTICS
   - Buttons: correct type attribute (type="button" vs type="submit")
   - Inputs: every input has an associated <label> or aria-label
   - Icons: decorative icons use aria-hidden="true"; informational icons have aria-label
   - Modals: use role="dialog", aria-modal="true", aria-labelledby pointing to heading
   - Tables: use <th scope="col"> for column headers

4. KEYBOARD NAVIGATION
   - All interactive elements reachable via Tab
   - Modal/dialog traps focus correctly and returns focus on close
   - Dropdown menus navigable with arrow keys

Output:
- List of issues found with severity (Critical / Major / Minor)
- Suggested fixes for each issue
- Updated token values where contrast fails
```

---

## Quick-Fire Prompts

These shorter prompts are optimised for fast iteration inside Cursor, Claude Code, or Figma Make when you don't need the full structured versions above.

---

### Quick Prompt: Token Extraction from Figma

Use after the design system page has been generated in Figma. Run in Cursor via Figma MCP, or paste with a screenshot attached in Claude / ChatGPT:

```
From the Figma design system page, extract and generate CSS design tokens.
Output format: CSS custom properties under :root {}.
Include all colors, spacing (e.g., --spacing-4: 16px), typography, radius, and shadows.
Make output Tailwind-compatible (also provide the tailwind.config.ts extend block).
```

---

### Quick Prompt: Build a Component from the Design System

Use in Cursor or Claude Code when building a new component against an already-defined design system:

```
Build [Component Name] exactly matching the design system defined in tokens.css.
Use only design tokens — no hardcoded values.
Include all states: default, hover, focus, disabled.
Framework: [React + Tailwind CSS].
Reference: [attach Figma screenshot or describe the component].
```

---

### Quick Prompt: Visual Validation Check

Use after generating or refactoring code to verify it matches the Figma design system:

```
Compare the generated component code to the Figma design system reference.
List:
1. Any pixel-level differences from the reference
2. Missing states or variants
3. Any remaining hardcoded values or token violations
Suggest specific fixes for each issue found.
```

---

## Best Practices Reference

A quick-scan table of the most important principles for working through this workflow:

| Concern | Guidance |
|---|---|
| **Consistency** | Always reference the mood board and design system file in every AI prompt |
| **Iteration cycle** | Follow the loop: Generate → Refactor → Validate for every component |
| **Scope control** | Start with a minimum viable system; expand component states incrementally |
| **Tool selection** | Figma Make for design exploration; Cursor or Claude Code for implementation |
| **Context limits** | If Cursor or Claude struggles with a large design system file, split into pages and feed one at a time via MCP |
| **No mixed styles** | Pick 1–2 reference companies and stay consistent — mixed style references produce inconsistent AI output |
| **Token discipline** | Never hardcode a value that exists in `tokens.css` — one source of truth, always |
| **State coverage** | Always generate all interactive states (hover, focus, disabled, loading, error) — not just the default |
| **Dark mode** | Define dark mode token overrides from the start, even if not initially shipped |
| **Accessibility** | Run the accessibility audit prompt before marking any component as production-ready |

---

## Quick Reference — Prompt Index

| # | Prompt Name | Where to Use |
|---|---|---|
| 1 | Quick: Generate a Page | Figma Make |
| 2 | Generate a UI Page (Detailed) | Figma Make · Claude · ChatGPT · V0 |
| 3 | Generate a Specific Component | Claude · Cursor · Codex · V0 |
| 4 | Generate Minimum Viable Design System | Figma Make · Claude · ChatGPT |
| 5 | Generate CSS Design Token File | Claude Code · Cursor · Codex |
| 6 | Refactor Codebase for Design Tokens | Cursor · Claude Code · Codex |
| 7 | Dark Mode Extension | Claude Code · Cursor |
| 8 | Accessibility Audit | Claude · Claude Code · Cursor |
| 9 | Quick: Token Extraction from Figma | Cursor (Figma MCP) · Claude · ChatGPT |
| 10 | Quick: Build a Component | Cursor · Claude Code |
| 11 | Quick: Visual Validation Check | Claude · Cursor · Claude Code |

---

## Design Token Reference Schema

When generating or documenting design tokens, follow this naming convention:

```
--[category]-[subcategory]-[variant]-[state]

Examples:
--color-bg-page
--color-bg-card
--color-text-primary
--color-text-muted
--color-border-default
--color-action-primary
--color-status-success-bg
--color-status-success-text
--color-status-success-border
--spacing-4          (= 16px if base unit is 4px)
--radius-md
--shadow-lg
--font-size-h1
--font-weight-heading
```

---

## Minimum Viable Design System Checklist

Use this as an acceptance test before moving to production:

**Colors**
- [ ] 3–4 background color tokens defined
- [ ] 3 text color tokens defined
- [ ] 2 border color tokens defined
- [ ] 1–2 action color tokens defined
- [ ] 4 status color sets (bg + border + text for success, info, warning, error)

**Typography**
- [ ] Font family tokens for heading and body defined
- [ ] Font size scale for H1–H3, body, small/caption
- [ ] Font weight and line-height tokens defined

**Spacing & Layout**
- [ ] Base unit (4px) established
- [ ] Spacing scale documented (4–96px)
- [ ] Border radius tokens defined
- [ ] Gap/layout tokens defined

**Elevation & Depth**
- [ ] 3 shadow levels defined (sm, md, lg)
- [ ] Z-index tokens defined for layering

**Components — Minimum Set**
- [ ] Button (all variants + disabled state)
- [ ] Input (default, focus, error, disabled)
- [ ] Card (basic structure)
- [ ] Badge/Tag (all status variants)
- [ ] Avatar
- [ ] Table (header + data row)

**Code Quality**
- [ ] All values use CSS custom properties — no hardcoded literals in components
- [ ] Tokens defined in a single source-of-truth file
- [ ] Dark mode token overrides defined (even if not initially shipped)
- [ ] All interactive components keyboard navigable
- [ ] Contrast ratios pass WCAG AA

---

## Tools Reference

| Tool | Role | URL |
|---|---|---|
| **Mobbin** | UI inspiration library | mobbin.com |
| **Figma** | Mood board and design file | figma.com |
| **Figma Make** | AI UI generation inside Figma | make.figma.com |
| **V0 by Vercel** | Prompt-to-React component generation | v0.dev |
| **Lovable** | Full-app generation | lovable.dev |
| **Cursor** | AI-powered IDE for refactoring and building | cursor.com |
| **Claude Code** | Agentic code generation and refactoring | Terminal / VS Code extension |
| **Lucide React** | Recommended icon library | lucide.dev |
| **Heroicons** | Alternative icon library | heroicons.com |
| **Realtime Colors** | Live palette contrast testing | realtimecolors.com |
| **Coolors** | Color palette generation | coolors.co |

---

## Usage Instructions for Agents

**To use this file as a Skill or Knowledge Base:**

1. **Claude Projects / Custom GPT / Gemini Gem:** Upload this `.md` file as a knowledge document. The agent will reference it when design system tasks are requested.

2. **Cursor / Claude Code:** Place this file in your project root as `DESIGN_SYSTEM_SKILL.md`. Reference it in your `.cursorrules` or system prompt: *"When working on UI or design system tasks, follow the process and use the prompts defined in DESIGN_SYSTEM_SKILL.md."*

3. **Figma Make:** Copy individual prompt blocks (Steps 3–4) directly into the Figma Make prompt field. Attach relevant mood board screenshots as context.

4. **Codex / API:** Pass this file as a system message or assistant context at the start of a session focused on UI/design system work.

5. **Antigravity or similar orchestration:** Register this file as a skill module triggered by intent labels: `design_system`, `ui_generation`, `design_tokens`, `component_refactor`.

---

*Based on the AI Builder Space methodology by Joanna Stoffregen. Extended with additional prompts for token generation, dark mode, accessibility auditing, and multi-tool compatibility.*
