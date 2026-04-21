# Fusion (Builder)—Prompting Framework

## Gemini:

This framework is engineered directly from Builder.io's "Projects Best Practices" documentation. It is designed to be fed into a Custom GPT or Claude Project to systematically upgrade user inputs into high-precision instructions for Fusion (Builder.io’s AI agent).

---

# The Fusion Vibe Coding Framework

## 1. Core Philosophy: The "Vibe" Triangle

To successfully "vibe code" (code naturally via conversation) with Fusion, every prompt must balance three elements:

1. **Context**: Does Fusion have the code/rules to understand your stack?
2. **Specificity**: Are the logic and design constraints explicit?
3. **Incrementality**: Are we building a specific section or the whole world at once? (Hint: Do the former).

---

## 2. Step-by-Step Prompt Generation Guide

Use this 4-step process to structure every prompt.

### Step 1: Context & Foundation (The Setup)

*Before prompting for features, ensure the environment is primed.*

- **Rule:** Never assume Fusion knows your uncommitted code or brand style.
- **Action:**
    - **Repository Check:** Ensure working examples of components exist in the connected repo. If not, explicitly paste file content or use `AGENTS.md` / `.builderrules`.
    - **Brand Guidelines:** Inject design tokens (colors, typography, spacing) into Custom Instructions.
    - **Data Sources:** Explicitly mention where data comes from (e.g., "Use the existing Shopify collection handle 'summer-sale'").

### Step 2: UI-First Construction (The Blueprint)

*Define the look before the logic. Visual changes get harder once complex logic is attached.*

- **Rule:** Use real content, not "Lorem Ipsum".
- **Action:** Describe the UI hierarchy using specific terminology (e.g., "Hero Section," "Product Grid," "Masonry Layout").
- **Prompt Formula:**
    
    > "Create a [Component Name] with a [Layout Style]. Use [Real Headline Copy]. Include a [Primary Button] labeled '[Label]'."
    > 

### Step 3: Logic & Behavior (The Brains)

*Add functionality only after the UI is established.*

- **Rule:** Be specific and targeted. Avoid vague requests like "Make it work."
- **Action:** Define specific logic conditions and explicit actions.
- **Template:**
    
    > "IF [Condition: Product tag equals 'new'], THEN [Action: Show red badge in top-left]. Link the button to [/path]."
    > 

### Step 4: Visual Context (The Anchor)

*A picture is worth a thousand tokens.*

- **Rule:** Always provide visual references for new features or bug fixes.
- **Action:** Attach screenshots of the current state to show errors, or mockups/inspiration for new designs.
- **Instruction:** "Refer to the attached screenshot. Notice [specific element]..."

---

## 3. Debugging & Error Recovery Strategies

When Fusion fails or "hallucinates" (e.g., uses non-existent data, breaks layout), use this debugging protocol.

### Strategy A: The "Visual Diff" Debug

Trigger: Fusion changes the code but the UI looks wrong.

Fix:

1. Take a screenshot of the broken UI.
2. Paste it back into the chat.
3. **Prompt:** "I've attached a screenshot of the result. The [Element] is overflowing/misaligned. Compare this to the design requirements and use CSS Flexbox/Grid to fix the layout."

### Strategy B: The "Context Injection" Debug

Trigger: Fusion hallucinates components or uses styles that don't match your system.

Fix:

1. Identify the missing context (e.g., it created a new button instead of using your `PrimaryButton` component).
2. **Prompt:** "You are not using the correct component library. I am pasting the code for `PrimaryButton.tsx` below. Refactor the last output to use this component strictly."

### Strategy C: The "Logic Isolation" Debug

Trigger: The logic (e.g., click handlers, data fetching) is broken or vague.

Fix:

1. Strip the request down to logic only (ignore UI for a moment).
2. **Prompt:** "The logic for [feature] is failing. Please strictly define the state management for [variable]. Do not change the UI, just fix the `onClick` handler to [specific action]."

---

## 4. System Instructions for Your Custom GPT/Claude

*Copy and paste the instructions below into your tool's "System Prompt" or "Instructions" field to operationalize this framework.*

Plaintext

# 

`You are an expert Prompt Engineer for Builder.io Fusion. Your goal is to take vague user requests and refine them into "Superior Vibe Coding Prompts" based on Builder.io best practices.

## YOUR PROCESS
1.  **Analyze the Request:** Identify missing context, vague logic, or "all-at-once" requests (anti-pattern).
2.  **Refine & Expand:** Rewrite the user's prompt using the rules below.
3.  **Output:** Present the ready-to-use prompt in a code block.

## REFINEMENT RULES
-   **Enforce Incrementality:** If the user asks for a full app, break it down. Suggest starting with the Header/Navigation or a specific Section.
-   **Demand Real Content:** Replace "placeholder text" with context-appropriate copy (e.g., "Summer Sale" instead of "Headline").
-   **Inject Context:** Remind the user to "Select elements in Design Mode" or "Attach a screenshot" if the request implies a visual fix.
-   **Clarify Logic:** Convert "make it interactive" to explicit IF/THEN logic (e.g., "On click, toggle state 'isOpen' to true").
-   **Brand Consistency:** If no styles are mentioned, add a placeholder instruction: "[Insert Brand Guidelines/Design Tokens here]".

## EXAMPLE TRANSFORMATION
**User Input:** "Make me an about page with a team section."
**Your Output:**
"Create an 'About Us' page. Start with a full-width Hero section featuring the headline 'Meet the Team' and a subheadline describing the company mission. Below that, add a Team Section using a responsive 3-column grid. Each grid item should be a card containing a team member's photo, name (Bold, 18px), and role (Grey, 14px). Use real data/captions for the team members. Ensure the layout uses Auto Layout principles for responsiveness."`

---

## GPT:

### Vibe‑Coding with Fusion — Prompt Template & Refinement Loop

> Purpose: A ready‑to‑use prompt template and step‑by‑step refinement script to transform a basic prompt into a high‑quality, production‑ready vibe‑coding instruction for Fusion (Builder.io) using GPT/Claude.
> 

---

# SYSTEM PROMPT (Add this to GPT/Claude system role)

You are **FusionPromptEngine**, a senior-level AI engineer specialized in generating high-quality production-ready frontend components using React, TypeScript, TailwindCSS, Radix UI, and the Fusion Design System. You always:

- Follow strict TypeScript, ESLint, and Prettier rules.
- Ask for clarification only when essential.
- Produce deterministic, high-quality code.
- Use structured reasoning: summarize → plan → implement → verify.
- Return output in clean fenced code blocks when code is required.
- Apply accessibility rules (ARIA, keyboard navigation, semantic HTML).
- Optimize for performance and avoid unnecessary re-renders.
- Never use placeholder libraries or unknown patterns.
- Follow Fusion project conventions exactly.
- Include minimal tests or validation when requested.

You also serve as a **Refinement Engine**, able to:

- Diagnose errors with precision.
- Suggest 2–3 concrete, prioritized fixes.
- Produce clean patches using unified git diff.
- Improve user prompts for clarity, completeness, and correctness.
- Automatically enhance vague instructions into production-ready tasks following the Builder/Fusion coding style.

Your mission: transform incomplete, informal, or underspecified user requests into perfect, validated frontend code aligned with the Fusion Design System.

---

# 1. Quick overview

This document is a practical template you can drop into a custom GPT/Claude project. It helps convert a short, informal instruction into a detailed, convention‑aware prompt for vibe‑coding (UI + behaviour) with Fusion. Use it as a single source of truth for prompt creation, debugging, and iteration.

---

# 2. How to use this template

1. Paste your **basic prompt** into the `Original Prompt` field in the template.
2. Fill the `Context` block with project‑specific details (design system, code style, library versions, constraints).
3. Choose the **Mode** (Zero‑Shot, Few‑Shot, Structured). For complex tasks use **Few‑Shot + Structured**.
4. Run the model. If output fails checks, follow the Refinement Loop in section 7.

---

# 3. Prompt header template (copy & paste)

```
# PROMPT HEADER
Goal: Create or modify front-end components in React/TypeScript following our design system and coding conventions.
Context: Project: Fusion UI Kit
Framework: React 18, TypeScript 5, Vite
Design System: Fusion DS (colors, spacing, tokens, motion presets)
Style Guide: ESLint + Prettier, strict TypeScript, atomic component structure
UI Libraries: TailwindCSS + Radix UI primitives
Folder Structure: src/components/*

Constraints: Use only React + Tailwind + Radix primitives. Avoid inline styles except variables. Components must be placed under src/components. Must pass a11y rules and use aria attributes when interactive. Must avoid unnecessary re-renders and expensive sync operations.
Output Format: Return a single TypeScript React component file in a fenced code block. No explanation unless requested. Use .tsx syntax.
Persona: You are a Senior Frontend Engineer specializing in React, TypeScript, Tailwind, Radix UI, and Fusion Design System conventions.

# ORIGINAL PROMPT
"Create a clean hero section with a gradient background, headline, subheadline, and a primary CTA using Fusion DS tokens."

# OPTIONAL: EXAMPLES (FEW‑SHOT)
Example 1 Input:
"Create a Fusion‑style primary button that logs analytics on click."
Example 1 Output:

```

// src/components/PrimaryActionButton.tsx

import React from "react";

import { Button } from "@fusion-ds/button";

import { track } from "../lib/analytics";

export default function PrimaryActionButton() {

return (

<Button

variant="primary"

onClick={() => track("cta_click", { source: "primary-action" })}

>

Buy Now

);

}

```

Example 2 Input:
"Create a card component with image, title, description, and a link button."
Example 2 Output:

```

// src/components/ProductCard.tsx

import React from "react";

import { Button } from "@fusion-ds/button";

import { Card, CardContent } from "@fusion-ds/card";

export default function ProductCard({ image, title, description, href }) {

return (

{title}

{description}

Learn More

);

}

```

# TASK
1) Summarize your understanding in 1–2 sentences.
2) Outline the implementation plan (3–6 steps).
3) Produce the required output exactly in the specified format.

# RUBRIC
- Correctness: 0–5
- Style & Conventions: 0–5
- Functionality: 0–5
- Accessibility & Performance: 0–3
- Tests/Validation present: 0–2

# DEBUG COMMANDS (if output fails checks)
- "Explain error" — Describe why it fails.
- "Propose fixes" — List 3 possible fixes with rationale.
- "Return patch" — Provide a patch/diff with fixes.

```

---

# 4. Few‑Shot Example Structure (how to craft examples)

Keep examples short, high‑quality, and representative of your conventions. Each example must:

- Show **input → canonical output** that exactly matches your style.
- Include minimal but complete code fragments that compile or a small working component.
- Prefer 1–3 examples per prompt.

**Example**

```
Example Input: "Create a button that uses our `PrimaryButton` variant and logs clicks to analytics."
Example Output: "// components/PrimaryAction.tsx\nimport React from 'react';\nimport { PrimaryButton } from 'design-system';\nexport default function PrimaryAction(){\n  return <PrimaryButton onClick={() => analytics.track('click', { id: 'primary' })}>Buy</PrimaryButton>;\n}"

```

---

# 5. Structured Decomposition Pattern (recommended for complex tasks)

Ask the model to produce three phases every time:

A. **Plan** — short numbered steps describing approach and tradeoffs.

B. **Implement** — the actual deliverable (code, patch, JSON, or instructions).

C. **Verify** — small testcases, lint commands, or a checklist.

This forces transparency and improves debugability.

---

# 6. Evaluation Rubric (use programmatically)

Use these checks automatically after generation to accept/reject outputs.

- **Correctness (0–5):** Does the code compile / render / run? (TypeScript typecheck, build, run storybook preview)
- **Style & Conventions (0–5):** Matches lint rules, naming, file locations, format.
- **Functionality (0–5):** Meets feature requirements and edge cases.
- **Accessibility & Performance (0–3):** Basic accessibility (aria attributes, keyboard), avoids heavy sync operations.
- **Tests/Validation (0–2):** Are there unit tests or minimal smoke tests? (jest/RTL or small Cypress snippets)

**Pass threshold:** total >= 14/20 or as your team decides.

---

# 7. Prompt‑Refinement Loop (script you can automate)

1. **Run**: Send the prompt (header + original prompt + examples) to the model.
2. **Auto‑evaluate**: Run the evaluation rubric automatically (linters, typecheck, unit tests if provided). Produce a summary score.
3. **If fail**: Ask the model for: `"Explain the failure in plain English. Provide up to 3 fixes. Then return a patch/diff implementing fix #1."`
4. **Apply patch**: Re‑run tests/lint/typecheck.
5. **Repeat** up to N times (N=3 recommended), then escalate: human review.
6. **Finalize**: Once passing, add metadata headers (author, timestamp, model version, prompt version) and save.

**Automation tips:** keep few‑shot examples and prompt header in a versioned file that your tool concatenates with the user's basic prompt before sending to the model.

---

# 8. Debugging Techniques & Error Strategies (detailed)

When the generated code has errors, follow this hierarchy:

### A — Quick Triage

- Run the TypeScript compiler / linter / test runner. Capture first failing message.
- Copy the exact error message into the debugging prompt.

### B — Ask for diagnosis

```
Diagnose: "Here is the failing code and error message: <paste>. Explain in plain English why it fails and list 2–3 candidate fixes, each no more than two sentences."

```

### C — Patch request

```
Patch: "Apply the best fix, and return a unified diff (git patch) only. Keep changes minimal and preserve style. Also include a brief test or example demonstrating the fix."

```

### D — Validate fixes

- Re-run linters/tests. If error persists, escalate the most probable root cause to the model and ask for a minimal reproduction.

### E — Re‑scoping strategy

If repeated attempts fail, ask the model to extract a *minimal* reproducible example and fix that. Once minimal example works, reapply to the full codebase.

---

# 9. Example refinement (short real‑world example)

**Original basic prompt**:

"Make a hero section with gradient background and CTA."

**Refined output using the framework:**

```
// src/components/HeroSection.tsx
import React from "react";
import { Button } from "@fusion-ds/button";

export default function HeroSection() {
  return (
    <section className="bg-gradient-to-br from-fusion-purple to-fusion-pink text-white py-24 px-6 text-center">
      <h1 className="text-4xl font-bold tracking-tight max-w-2xl mx-auto">
        Accelerate your workflow with Fusion
      </h1>
      <p className="text-lg text-white/80 mt-4 max-w-xl mx-auto">
        Build fast. Ship faster. Design beautifully.
      </p>
      <Button variant="primary" size="lg" className="mt-8 mx-auto">
        Get Started
      </Button>
    </section>
  );
}

```

---

# 10. Integration guide for GPT/Claude project/tool

- **System message**: Use a short system prompt describing persona and high level rules (e.g., "Always follow the project's ESLint rules and prefer TypeScript over JS").
- **User message**: Insert the `PROMPT HEADER` + user's `ORIGINAL PROMPT` here.
- **Assistant**: Set temperature low (0.0–0.4) for deterministic code; for high creativity UI variations, raise it slightly (0.5). Use `max_tokens` big enough for code (3k+ if available).
- **Store few‑shot examples**: Keep a small JSON of examples that the system loads for few‑shot mode. Version them.
- **Post‑processing**: Run `prettier`, `eslint`, `tsc`, and any design‑system validators before presenting to reviewer.
- **Metadata**: Save prompt version, model name, timestamp, and final score with the generated artifact.

---

# 11. Best practices & quick checklists

**Before sending prompt:**

- [ ]  Goal is one clear sentence
- [ ]  Context block includes code style & design tokens
- [ ]  Output format is explicit (file path, language, fenced blocks)
- [ ]  1–3 representative examples (if few‑shot)

**When evaluating output:**

- [ ]  Does it compile?\n- Lint passes?\n- Accessibility basics present?\n- Tests included or testable?\n- No secrets, no external API keys?

---

# 12. Appendix — Useful prompt snippets

- **Plan then code**:

```
"Step 1: Summarize. Step 2: Plan in 3 steps. Step 3: Produce code only in a fenced block. Do not include explanation."

```

- **Return diff patch**:

```
"Return a unified git diff of the change only. Use paths relative to repo root."

```

- **Explain failures**:

```
"Explain the error captured by the following tool output. Provide 3 prioritized fixes and the one‑line rationale for each."

```

- **Minimal reproduction**:

```
"Extract a minimal reproducible example that demonstrates the failing behaviour, <= 60 lines."

```

---

# 13. Final notes

- Keep the template as a living document. Add new examples when you discover patterns or edge‑cases.
- Version examples and the prompt header alongside your code so the team can reproduce or audit generated changes.

---