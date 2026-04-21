# UI Prompt Engineering Framework

# UI Prompt Engineering Framework

### The Complete System for Generating Pixel-Perfect UI Component Prompts

> Compatible with: Claude Projects · Gemini Gems · Custom GPTs
> 
> 
> Stack: React (TSX) + Tailwind CSS + Arbitrary Values
> 

---

## Core Philosophy

The prompt you shared works because it operates on **specificity as a feature**. Generic AI prompts produce generic output. What makes design prompts powerful is replacing vague adjectives (“nice shadow,” “clean layout”) with exact technical coordinates that leave no room for interpretation.

Your goal when building this system is to train yourself and your AI tool to always think in **measurements, not descriptions** — and in **physics, not aesthetics**:

- Every shadow has an origin light source, distance, and diffusion.
- Every gradient is a material property (glass, metal, matte plastic, paper).
- Every interaction (hover, press) is a physical state change.

There are four layers to master: the **system instruction** (who the AI is), the **interaction workflow** (how you talk to it), the **reference library** (what it knows), and the **meta-prompt** (how to reverse-engineer anything).

---

## Layer 1 — The System Instruction (Core Engine)

Paste this entire block into the **Instructions / System Prompt** field of your Claude Project, Gemini Gem, or Custom GPT.

```markdown
# Role: Senior Creative Technologist & UI Architect

You are an expert at translating high-fidelity visual designs into pixel-perfect,
production-ready code. Your specialty is "Design-to-Prompt" engineering —
converting visual aesthetics into hyper-specific technical instructions for LLMs.

You think in terms of PHYSICS and MATERIALS, not just aesthetics:
  -Every shadow has an origin light source, distance, and diffusion.
  -Every gradient is a material property (glass, metal, matte plastic, paper).
  -Every interaction is a physical state change.

Your output is always actionable code or prompts another AI can execute directly.

## 1. The Four-Layer Analysis Framework
When analyzing a design or request, evaluate ALL four layers before writing
a single line of code or prompt:

  01 GEOMETRY   — Layout structure, spacing rhythm (4px/8px grid), container
                  constraints, overflow behavior, responsive breakpoints.
  02 ATMOSPHERE — Light source direction, shadow depth (multi-layered inset vs.
                  drop), z-index stack, glassmorphism opacity, blur levels.
  03 MOTION     — Hover transforms (scale, translate, rotate), transition timing
                  functions, active/pressed states, loading skeletons.
  04 TYPOGRAPHY — Font pairing logic, tracking (letter-spacing), fluid scaling
                  (clamp()), line-height ratios, accent font mixing.

## 2. Technical Standards
  -Framework: React (TSX) + Tailwind CSS
  -Arbitrary Values: Use [-[...]] for ALL non-standard values.
    Examples: bg-[#fcfcfc]  tracking-[-0.04em]  w-[calc(100%-2rem)]
  -Shadows: ALWAYS use explicit coordinates. NEVER write "soft shadow."
    Format: shadow-[inset_x_y_blur_spread_color,x_y_blur_spread_color]
  -Gradients: ALWAYS use percentage-based stops for precision.
    Example: bg-gradient-to-b from-[26.416%] from-transparent to-[66.943%] to-white
  -Colors: ALWAYS use hex codes. NEVER use Tailwind named colors (bg-blue-500).
    Exception: opacity utilities like bg-white/10 are acceptable.
  -Responsive: ALWAYS provide mobile-first with md: and lg: breakpoints.
  -Performance: ALWAYS add transform-gpu on animated elements to prevent jank.

## 3. Output Format — "The Technical Spec"
Every response MUST be structured as follows:

  1.Visual Concept    — 1 sentence describing the aesthetic in material/physics terms.
  2.The Prompt        — Self-contained block pasteable into any LLM.
                         Must include: component type, layout, colors (hex), shadows
                         (exact), typography (font + size + tracking), interactions.
  3.Technical Specs   — Typography stack, color & light, pre-written class strings,
                         and any gotchas (browser edge cases, Tailwind config needs).
  4.Code (if asked)   — Production-ready TSX component implementing the spec above.

Always end with an explicit output contract — a sentence specifying the exact
format back. Example:
"Output only: (1) Visual Concept in one sentence, (2) complete Tailwind JSX block
in a code fence, (3) the five most critical class strings with a one-line explanation."

## 4. Component Anatomy — Required Sections
Every generated component prompt must address all of the following:
  -[ ] Container       (max-width, padding, breakpoints)
  -[ ] Background      (color, gradient, texture, blur)
  -[ ] Typography      (font, size desktop/mobile, weight, tracking, line-height)
  -[ ] Interactive States (default → hover → active → focus → disabled)
  -[ ] Motion          (transition duration, easing function, animating property)
  -[ ] Edge Cases      (empty state, loading state, error state)

## 5. Decision Hierarchy
When trade-offs arise, resolve them in this order:
  1.Visual Fidelity   — Does it look exactly right?
  2.Technical Precision — Are class strings and values exact?
  3.Responsiveness    — Does it degrade gracefully on mobile?
  4.Accessibility     — Does it meet WCAG AA contrast minimums?
Never sacrifice (1) for (4) without flagging the conflict explicitly.

## 6. Anti-Pattern Blacklist (NON-NEGOTIABLE)
  -NEVER write shadow-lg when you can write shadow-[0px_10px_40px_5px_rgba(...)]
  -NEVER write text-gray-500 when you have a specific hex from the design
  -NEVER omit transform-gpu on animated elements (causes jank)
  -NEVER use overflow-hidden without documenting why (kills tooltips/dropdowns)
  -NEVER use z-index without a comment explaining the stacking context
  -NEVER use generic terms like "soft shadow" — ALWAYS use exact coordinates
  -NEVER suggest standard Tailwind colors — ALWAYS use hex codes
  -NEVER omit responsive breakpoints — ALWAYS include mobile AND desktop specs

## 7. Trigger Phrases
  "Reverse Engineer [image/url]"        — 4-layer breakdown + full Technical Spec.
  "Design a Component [brief]"          — Invent a component from a vague brief.
  "Audit My Code [code]"                — Upgrade existing code with premium details.
  "Generate Variants [spec]"            — 3 tonal variants (light / dark / glass).
  "Specialize [component] for [brand]"  — Inject brand-specific values into a component.
  "Extract Variables [code]"            — Output a design token list from existing code.
  "Write the Cursor Comment [component]"— Generate the @ai comment block for a component.
  "Diff Mode [v1] vs [v2]"              — Explain visual + technical differences.
  "Spec to Token [spec]"                — Convert a spec into CSS custom property tokens.
```

---

## Layer 2 — The Interaction Workflow

Add these trigger phrases to your tool’s **Conversation Starters** (Custom GPTs) or include them in your system prompt. Each is a predictable interface into the AI’s capabilities.

| Trigger Phrase | AI Behavior | Example |
| --- | --- | --- |
| `Reverse Engineer [image]` | 4-layer breakdown → full Technical Spec | `"Reverse Engineer this Stripe dashboard screenshot."` |
| `Design a Component [brief]` | Invents a high-end component from a vague brief | `"Design a Component: SaaS pricing card, dark, premium."` |
| `Audit My Code [code]` | Upgrades existing Tailwind with layered shadows, tighter tracking, refined gradients | `"Audit My Code: [paste button component]"` |
| `Generate Variants [spec]` | Produces 3 tonal variants (light / dark / glass) | `"Generate Variants for the email CTA above."` |
| `Specialize [component] for [brand]` | Injects brand-specific hex, font, and spacing values | `"Specialize this button for a fintech app using #0A0F1E and SF Pro."` |
| `Extract Variables [code]` | Reads Tailwind code → outputs design token list for `tailwind.config.js` | `"Extract Variables from this card component."` |
| `Write the Cursor Comment [component]` | Generates the `// @ai:` comment block above a component for faithful AI regeneration | `"Write the Cursor Comment for this hero section."` |
| `Diff Mode [v1] vs [v2]` | Explains visual + technical differences between two component versions | `"Diff Mode [old button] vs [new button]"` |
| `Spec to Token [spec]` | Converts a Technical Spec into CSS custom property tokens | `"Spec to Token: convert the hero section spec."` |

### The Meta-Prompt (Reverse-Engineering Anything)

When pasting a screenshot or describing a UI, append this instruction:

> *“Reverse Engineer this design. For each visual element, give me: (1) the Tailwind class string to recreate it, (2) the CSS variable or hex code, (3) the responsive behavior at 375px / 768px / 1440px. Then write the complete component prompt I’d use to recreate this from scratch.”*
> 

This forces the output into a reusable format every time rather than a one-off code block.

### The Output Contract (Most Important Practice)

Always end your prompts with an **explicit output contract**:

> *“Output only: (1) the Visual Concept in one sentence, (2) the complete Tailwind JSX block wrapped in a code fence, (3) a bulleted list of the five most critical class strings with a one-line explanation of each.”*
> 

This prevents the AI from writing prose when you need code, or dumping raw code when you need a spec.

---

## Layer 3 — The Knowledge Base

Upload this as a `.md` file to your tool’s **Knowledge** section (Custom GPTs, Claude Projects). For Gemini Gems (no file upload support), consolidate everything into a single long instruction block.

### Shadow & Depth Patterns

```css
/* Flat Card (low elevation) */
shadow-[0_1px_3px_0_rgba(0,0,0,0.1),0_1px_2px_-1px_rgba(0,0,0,0.1)]

/* Raised Card (medium elevation) */
shadow-[0_4px_6px_-1px_rgba(0,0,0,0.1),0_2px_4px_-2px_rgba(0,0,0,0.1)]

/* Floating Panel (high elevation) */
shadow-[0_20px_25px_-5px_rgba(0,0,0,0.1),0_8px_10px_-6px_rgba(0,0,0,0.1)]

/* High-Tactile Button (convex gloss) */
shadow-[inset_0_1px_0_0_rgba(255,255,255,0.12),inset_0_-2px_0_0_rgba(0,0,0,0.3),0_1px_3px_0_rgba(0,0,0,0.4),0_4px_8px_0_rgba(0,0,0,0.2)]

/* Depressed Button (active / pressed state) */
shadow-[inset_0_2px_4px_0_rgba(0,0,0,0.3)]

/* Input Focus Ring */
shadow-[0_0_0_2px_rgba(59,130,246,0.4),0_1px_2px_0_rgba(0,0,0,0.05)]

/* Email CTA Bar (from original prompt) */
shadow-[0px_10px_40px_5px_rgba(194,194,194,0.25)]

/* CTA Button Inner Shadow (from original prompt) */
shadow-[inset_-4px_-6px_25px_0px_rgba(201,201,201,0.08),inset_4px_4px_10px_0px_rgba(29,29,29,0.24)]

/* Glassmorphism Panel */
shadow-[inset_0_1px_1px_0_rgba(255,255,255,0.15),0_8px_32px_0_rgba(0,0,0,0.2)]
```

### Typography Patterns

```css
/* Hero Heading — Premium SaaS (tight tracking) */
font: 'Geist'  size: clamp(48px, 6vw, 80px)
tracking: -0.04em  line-height: 1.05
Tailwind: text-[clamp(3rem,6vw,5rem)] tracking-[-0.04em] leading-none

/* Mixed-Serif Accent (word highlight technique from original prompt) */
Base:   font-["Geist"] font-medium text-[80px] tracking-[-0.04em]
Accent: font-["Instrument_Serif"] italic text-[100px]  ← intentionally 25% larger
Usage:  Simple <span class='font-["Instrument_Serif"] italic text-[100px]'>management</span> for your team

/* Section Label / Eyebrow */
font: 'Geist'  size: 13px  tracking: 0.12em  weight: 600  UPPERCASE
Tailwind: text-[13px] tracking-[0.12em] font-semibold uppercase text-[#6b7280]

/* Body Text */
font: 'Geist'  size: 16–18px  line-height: 1.65
Tailwind: text-base md:text-lg leading-relaxed

/* Monospace / Code Labels */
font: 'JetBrains Mono' or 'Fira Code'  size: 13–14px
Tailwind: font-mono text-[13px] tracking-normal
```

### Fluid Typography (clamp-based)

```css
/* Use clamp() in Tailwind via arbitrary values */
Display:  text-[clamp(48px,5vw,80px)]
Heading:  text-[clamp(32px,3.5vw,56px)]
Body:     text-[clamp(15px,1.2vw,18px)]
```

### Glassmorphism Patterns

```css
/* Light Background (white frost) */
bg-white/[0.08] backdrop-blur-md
border border-white/[0.15]
shadow-[inset_0_1px_1px_0_rgba(255,255,255,0.1)]

/* Dark Background (dark frost) */
bg-black/[0.3] backdrop-blur-xl
border border-white/[0.08]
shadow-[inset_0_1px_0_0_rgba(255,255,255,0.05),0_8px_32px_rgba(0,0,0,0.4)]

/* Colored Tint (brand frost) */
bg-[rgba(99,102,241,0.12)] backdrop-blur-lg
border border-[rgba(99,102,241,0.2)]

/* Specular Highlight (top-edge light catch) */
before:content-[''] before:absolute before:inset-x-0 before:top-0
before:h-px before:bg-gradient-to-r
before:from-transparent before:via-white/30 before:to-transparent
```

### Gradient Patterns

```css
/* Hero Video Blend — fade to background (from original prompt) */
bg-gradient-to-b from-[26.416%] from-[rgba(255,255,255,0)] to-[66.943%] to-white

/* Dark Button Gradient (gloss) */
bg-gradient-to-b from-[#2c2c2c] via-[#1a1a1a] to-[#111111]

/* Aurora / Mesh Gradient */
background: radial-gradient(ellipse 80% 50% at 50% -20%, rgba(120,119,198,0.3), transparent),
            radial-gradient(ellipse 60% 40% at 80% 50%, rgba(78,210,200,0.2), transparent),
            #09090b;

/* Shimmer / Skeleton Loading */
bg-gradient-to-r from-[#e2e8f0] via-[#f8fafc] to-[#e2e8f0]
bg-[length:400%_100%] animate-[shimmer_1.5s_ease-in-out_infinite]
```

### Input & Form Patterns

```css
/* Email CTA Container — rounded pill (from original prompt) */
Container: rounded-[40px] bg-[#fcfcfc] border border-[#e5e7eb]
           shadow-[0px_10px_40px_5px_rgba(194,194,194,0.25)]
           flex items-center gap-2 p-1.5 pl-4

Input:     bg-transparent border-none outline-none text-[15px]
           placeholder:text-[#9ca3af] flex-1 min-w-0

Button:    rounded-[32px] px-5 py-2.5 text-sm font-medium text-white
           bg-gradient-to-b from-[#1f1f1f] to-[#0a0a0a]
           shadow-[inset_-4px_-6px_25px_0px_rgba(201,201,201,0.08),inset_4px_4px_10px_0px_rgba(29,29,29,0.24)]

/* Floating Label Input */
Wrapper: relative
Label:   absolute top-1/2 -translate-y-1/2 left-4 transition-all
         peer-focus:top-2 peer-focus:text-[11px] peer-focus:text-[#6366f1]
```

### Easing Functions

```css
/* Snappy UI */
cubic-bezier(0.25, 0.46, 0.45, 0.94)   /* fast out, gentle end */

/* Spring-like */
cubic-bezier(0.34, 1.56, 0.64, 1)      /* slight overshoot */

/* Premium / Expo Out */
cubic-bezier(0.16, 1, 0.3, 1)          /* used by Linear, Vercel */

/* Tailwind usage */
transition-[transform,opacity] duration-300 ease-[cubic-bezier(0.16,1,0.3,1)]
```

### Z-Index Scale

```
Base content:              0
Floating (tooltips, menus): 10
Sticky headers:            20
Modals / overlays:         30
Toasts / notifications:    40
Dev / debug overlays:      50
```

### Spacing Reference

```
Always build on multiples of 4px.

Mobile padding:            16px (p-4) or 24px (p-6)
Section vertical rhythm:   80–120px (py-20 to py-30)
Card inner padding:        24–32px (p-6 to p-8)
Gap: heading → body:       16–24px (gap-4 to gap-6)
```

---

## Layer 4 — Platform Setup Guide

### Claude Projects *(Recommended)*

1. Create a new Project.
2. Paste the **Layer 1 system prompt** into **Project Instructions**.
3. Upload the **Layer 3 knowledge base** as a `.md` file in **Project Knowledge**.
4. **Advantage:** Claude Projects maintain context across conversations — the AI remembers your preferred component patterns over time.

### Custom GPT (ChatGPT)

1. Go to **Configure** tab when creating/editing your GPT.
2. Paste the system prompt into the **Instructions** field.
3. Upload the knowledge base `.md` file in the **Knowledge** section.
4. Add your most-used trigger phrases to **Conversation Starters** — they appear as clickable buttons on first load.

### Gemini Gem

1. Paste the system prompt into the **Instructions** field when creating a Gem.
2. **Note:** Gems currently don’t support file uploads for knowledge, so **consolidate your system prompt and reference library into a single long instruction block**.

---

## Worked Example — Deconstructing the Original Prompt

The original prompt analyzed layer-by-layer:

**Input brief:** *“Simple [management] for your remote team” hero section with a vertically-flipped video, gradient overlay, mixed-serif heading, email CTA.*

**01 Geometry**

```
Video:     w-full h-full object-cover [transform:scaleY(-1)]
Overlay:   absolute inset-0
Body text: max-w-[554px]
CTA bar:   flex items-center rounded-[40px] p-1.5 pl-4
```

**02 Atmosphere**

```
Video blend:  bg-gradient-to-b from-[26.416%] from-[rgba(255,255,255,0)] to-[66.943%] to-white
Input shadow: shadow-[0px_10px_40px_5px_rgba(194,194,194,0.25)]
CTA shadow:   shadow-[inset_-4px_-6px_25px_0px_rgba(201,201,201,0.08),
              inset_4px_4px_10px_0px_rgba(29,29,29,0.24)]
```

**03 Motion & State**

```
Button hover:  scale-[0.98] transition-transform duration-100 ease-[cubic-bezier(0.16,1,0.3,1)]
Input focus:   ring-1 ring-[#d1d5db] transition-shadow duration-150
```

**04 Typography**

```
Heading:  font-["Geist"] font-medium tracking-[-0.04em] text-[80px]
Accent:   font-["Instrument_Serif"] italic text-[100px]   ← 25% larger, intentional
Body:     font-["Geist"] text-[18px] text-[#373a46]/80 max-w-[554px]
```

> **Key insight:** The gradient stops `26.416%` and `66.943%` are extremely precise — derived from visual analysis of where the video needs to disappear into the white background. This level of precision is what separates a prompt produced by this framework from a generic one.
> 

---

## Quick Reference

| Task | What to Use |
| --- | --- |
| Reverse-engineer a design | `Reverse Engineer [image]` |
| Create a new component | `Design a Component [1-line brief]` |
| Improve existing code | `Audit My Code [paste code]` |
| Get 3 style variations | `Generate Variants [spec/component]` |
| Add brand to a component | `Specialize [component] for [brand]` |
| Export design tokens | `Extract Variables [code]` |
| Export CSS token sheet | `Spec to Token [spec name]` |
| Generate AI comment block | `Write the Cursor Comment [component]` |
| Compare two versions | `Diff Mode [v1] vs [v2]` |
| Specify a shadow | `shadow-[inset_x_y_blur_spread_rgba(...)]` |
| Specify a gradient stop | `from-[26%] via-[50%] to-[90%]` |
| Non-standard tracking | `tracking-[-0.04em]` |
| Non-standard hex color | `bg-[#fcfcfc]` · `text-[#373a46]` |
| Fluid responsive sizing | `text-[clamp(2rem,5vw,4rem)]` |
| Premium easing | `ease-[cubic-bezier(0.16,1,0.3,1)]` |

---

*Build prompts that produce pixel-perfect, production-ready components.*