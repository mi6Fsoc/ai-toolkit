# Elite Web Design System Architect Prompt [Lovable, Cursor, Gemini, etc.]

# Elite Design System Architect Prompt

**Purpose**: Generate sophisticated, production-ready interfaces that transcend generic AI outputs through intentional design decisions, systematic thinking, and craft-level execution.

---

## I. Pre-Design Analysis Framework

### A. Design Discovery Process

Before writing any code, systematically determine:

1. **Primary Function**
    - Conversion/Marketing: Persuade → Action
    - Utility/Tool: Enable → Task Completion
    - Content/Editorial: Inform → Understanding
    - Entertainment/Brand: Engage → Memory
2. **User Context**
    - Device primary: Mobile-first vs Desktop-optimized
    - Attention span: Scanning vs Deep reading
    - Trust level: Established brand vs New visitor
    - Technical literacy: Consumer vs Developer audience
3. **Brand Positioning**
    - Established/Corporate: Trust, authority, consistency
    - Startup/Disruptor: Innovation, energy, differentiation
    - Luxury/Premium: Refinement, exclusivity, craft
    - Community/Open: Accessibility, transparency, warmth

---

## II. Design Archetype System

### Detailed Archetype Matrix

### **A. SaaS/Tech** (Trust-Building Efficiency)

**When to use**: B2B products, developer tools, productivity software

**Visual Language:**

- **Typography**: Space Grotesk, Plus Jakarta Sans, Geist Sans, Manrope, DM Sans
- **Font Scale**: Restrained (16/18/24/32/48px), high legibility priority
- **Color Strategy**:
    - Base: Cool neutrals (Slate/Gray/Zinc scales)
    - Primary: Single confident accent (Indigo 600, Emerald 600, Blue 600)
    - Semantic colors for status only
    - Background: `#FAFAFA` or `#F8FAFC`
- **Layout**: Systematic grid (12-column), generous padding (24-32px), clear hierarchy
- **Spacing**: Consistent 8px rhythm, breathing room between sections (80-128px)
- **Borders**: Subtle (`1px solid rgba(0,0,0,0.06)`), rounded corners (8-12px)
- **Shadows**: Layered elevation (`0 1px 3px rgba(0,0,0,0.1)`)

**Interaction Patterns:**

- Instant feedback (<100ms)
- Subtle hover states (color shift, mild lift)
- Loading states with skeleton screens
- Toast notifications, not modals

**Anti-patterns:** Overdesign, decorative elements without function, inconsistent spacing

---

### **B. Luxury/Editorial** (Considered Refinement)

**When to use**: Fashion, hospitality, high-end services, long-form content

**Visual Language:**

- **Typography**: Playfair Display, Cormorant Garamond, Fraunces, Crimson Pro, Lora + Montserrat
- **Font Scale**: Dramatic contrast (16/18/28/48/72/96px)
- **Color Strategy**:
    - Base: Warm neutrals (Stone, Warm Gray)
    - Palette: Muted earth (Terracotta, Sage, Ochre, Cream)
    - Accents: Deep burgundy, forest green, or classic black
    - Background: `#FBF9F7`, `#F5F3EF`, or rich black `#0A0A0A`
- **Layout**: Asymmetric, editorial grid (breaking traditional 12-col), ample whitespace (120-200px between sections)
- **Spacing**: Generous, luxurious breathing room
- **Borders**: Minimal or none, rely on spacing
- **Shadows**: Rare, prefer subtle texture/noise

**Interaction Patterns:**

- Slow, deliberate animations (400-600ms)
- Page transitions with elegance
- Parallax for depth, not gimmick
- Hover states: Underline animations, opacity shifts

**Anti-patterns:** Rushed interactions, cluttered layouts, competing focal points

---

### **C. Brutalist/Developer** (Intentional Rawness)

**When to use**: Dev tools, tech communities, experimental projects, crypto/web3

**Visual Language:**

- **Typography**: JetBrains Mono, IBM Plex Mono, Fira Code, Space Mono, Courier Prime
- **Font Scale**: Uniform or inverted hierarchy (16/16/18/20/24px)
- **Color Strategy**:
    - High contrast: Pure black (`#000000`) on white (`#FFFFFF`)
    - Primary colors used unapologetically (red, blue, yellow)
    - Terminal aesthetics: Green on black, amber on black
    - Background: Stark white or `#0D0D0D`
- **Layout**: Grid-resistant, intentional misalignment, borders as design elements
- **Spacing**: Variable, sometimes tight (16px), sometimes extreme (200px+)
- **Borders**: Heavy (2-4px solid black), tables, hard edges
- **Shadows**: None or hard drop shadows (`4px 4px 0 black`)

**Interaction Patterns:**

- No transitions or instant snaps
- System fonts, monospace everywhere
- Terminal-style inputs
- Brutalist buttons (thick borders, no rounding)

**Anti-patterns:** Softness, gradients, trying to be "friendly"

---

### **D. Playful/Consumer** (Approachable Joy)

**When to use**: Consumer apps, gaming, children's products, lifestyle brands

**Visual Language:**

- **Typography**: Outfit, Nunito, Quicksand, Poppins, Fredoka, Lexend
- **Font Scale**: Friendly (16/18/22/32/48px), rounded terminals
- **Color Strategy**:
    - Saturated, multi-color palettes (3-5 distinct hues)
    - Backgrounds with subtle gradients or color tints
    - Playful combinations (pink + yellow, teal + coral)
    - Background: `#FEFEFE`, `#F0F9FF`, or colored (`#FFF7ED`)
- **Layout**: Organic, card-based, generous rounded corners (16-24px)
- **Spacing**: Comfortable, 16px rhythm
- **Borders**: Often gradient borders or thick colored outlines
- **Shadows**: Softer, more diffused (`0 4px 12px rgba(0,0,0,0.08)`)

**Interaction Patterns:**

- Bouncy animations (spring physics)
- Scale transforms on hover (1.05-1.1x)
- Confetti, success animations
- Emoji integration encouraged

**Anti-patterns:** Flat corporate feel, muted colors, rigid grids

---

### **E. Corporate/Enterprise** (Authoritative Stability)

**When to use**: Fortune 500, government, healthcare, financial services

**Visual Language:**

- **Typography**: Source Sans 3, Noto Sans, Open Sans (yes, really—trust signals), IBM Plex Sans
- **Font Scale**: Conservative (14/16/18/24/32px)
- **Color Strategy**:
    - Anchored by navy, forest green, burgundy, or charcoal
    - Muted secondary colors (lighter tints)
    - High accessibility priority (WCAG AAA where possible)
    - Background: Pure `#FFFFFF` or very light gray `#F7F7F7`
- **Layout**: Strict 12-column grid, predictable, hierarchical
- **Spacing**: Formal, consistent 8px grid
- **Borders**: 1px, neutral gray
- **Shadows**: Minimal, professional (`0 2px 4px rgba(0,0,0,0.1)`)

**Interaction Patterns:**

- Conservative transitions (200ms linear)
- Focus on accessibility (keyboard nav, screen readers)
- Clear states for all elements
- Print-friendly considerations

**Anti-patterns:** Trendy effects, experimental layouts, playful language

---

### **F. Creative/Portfolio** (Memorable Individuality)

**When to use**: Personal brands, agencies, artists, experimental projects

**Visual Language:**

- **Typography**: Syne, Clash Display, Cabinet Grotesk, Archivo Black, Unbounded
- **Font Scale**: Experimental (12/14/64/80/120px), headline-focused
- **Color Strategy**:
    - Bold statements: Monochrome + one shock color
    - Or: Full spectrum experimentation
    - Dark mode often preferred
    - Background: Rich blacks (`#0C0C0C`) or unexpected colors
- **Layout**: Grid-breaking, asymmetric, scroll-jacking allowed
- **Spacing**: Intentionally uneven, creates tension
- **Borders**: Used as graphic elements
- **Shadows**: Creative (colored shadows, multiple layers)

**Interaction Patterns:**

- Scroll-driven animations (GSAP ScrollTrigger)
- Cursor effects, trailing animations
- Page transitions, scene changes
- WebGL, Three.js for 3D

**Anti-patterns:** Playing it safe, conventional layouts, explaining too much

---

## III. Advanced Color Theory

### A. Palette Construction Strategy

**Never use these combinations** (instant "AI slop" detection):

- `#FFFFFF` + `#3B82F6` (generic blue)
- `#FFFFFF` + `#8B5CF6` (generic purple)
- Any pure white background with Tailwind default colors unchanged
- Rainbow gradients without purpose

**Instead, build intentional palettes:**

### **1. Monochromatic + Accent** (Safest, most professional)

`Base: 8-10 shades of one neutral (Slate, Stone, Zinc, Gray)
- 50: Near white (backgrounds)
- 100-200: Subtle borders, disabled states
- 300-400: Secondary text, placeholders
- 500-600: Primary text
- 700-800: Headings, emphasis
- 900-950: Near black

Accent: Single color, 500-700 weight
- Used for: CTAs, links, active states, brand moments
- Examples: Emerald 600, Rose 600, Amber 600`

### **2. Duotone** (Editorial, sophisticated)

`Primary: Warm or cool neutral (full scale)
Secondary: Contrasting temperature
- Warm base (Stone) + Cool accent (Cyan)
- Cool base (Slate) + Warm accent (Amber)

Use secondary sparingly: 10-15% of the interface`

### **3. Triadic** (Playful, vibrant)

`Three equidistant hues from color wheel
- Teal + Coral + Amber
- Violet + Lime + Rose

Balance: 60% primary, 30% secondary, 10% tertiary
Reduce saturation for backgrounds (200-300 weights)`

### B. Background Sophistication

**Off-White Palette** (warm to cool):

`Cream: #FBF9F7, #F5F3EF (pairs with earth tones)
Neutral: #FAFAFA, #F5F5F5 (pairs with anything)
Cool: #F8FAFC, #F1F5F9 (pairs with blues/grays)
Paper: #FFFEF9 (pairs with dark greens, reds)`

**Off-Black Palette** (rich to pure):

`Charcoal: #1C1917, #292524 (warm undertone)
Graphite: #18181B, #27272A (neutral)
Slate: #0F172A, #1E293B (cool undertone)
Pure: #0A0A0A, #000000 (maximum contrast)`

### C. Semantic Color Systems

Build consistent semantic layers:

css

`:root {
  */* Base layers */*
  --color-background: ...;
  --color-foreground: ...;
  --color-muted: ...;
  --color-border: ...;
  
  */* Semantic states */*
  --color-success: #10B981; */* Emerald 500 */*
  --color-warning: #F59E0B; */* Amber 500 */*
  --color-error: #EF4444; */* Red 500 */*
  --color-info: #3B82F6; */* Blue 500 */*
  
  */* Interactive */*
  --color-primary: ...;
  --color-primary-hover: ...;
  --color-primary-active: ...;
}
```

---

## IV. Typography System

### A. Font Selection Philosophy

**Forbidden fonts** (overused, trigger "generic" detection):
- Inter, Roboto, Open Sans, Lato, Montserrat (as primary), Arial, Helvetica, system-ui

**Exception**: Inter/Roboto acceptable in dashboards where reading efficiency > brand, or in body text when paired with distinctive display font.

### B. Pairing Strategy

**Rule**: Contrast in personality, harmony in proportion.

#### **Proven Pairings:**

| Display (Headers) | Body (Text) | Archetype | Mood |
|-------------------|-------------|-----------|------|
| Space Grotesk | Plus Jakarta Sans | SaaS | Modern, technical |
| Fraunces | Source Serif 4 | Editorial | Sophisticated, literary |
| Syne | Inter | Creative | Bold, contemporary |
| Playfair Display | Lato | Luxury | Classic, refined |
| JetBrains Mono | JetBrains Mono | Brutalist | Monospace, systematic |
| Cabinet Grotesk | Synonym | Portfolio | Unique, artistic |
| Outfit | Nunito | Playful | Friendly, rounded |
| Crimson Pro | Crimson Pro | Editorial | Serif-only, elegant |

### C. Type Scale Architecture

**Modular Scale** (1.250 - Major Third):
```
xs:   12px / 0.75rem  (captions, labels)
sm:   14px / 0.875rem (secondary text)
base: 16px / 1rem     (body text)
lg:   20px / 1.25rem  (lead paragraphs)
xl:   24px / 1.5rem   (subheadings)
2xl:  32px / 2rem     (section titles)
3xl:  40px / 2.5rem   (page titles)
4xl:  48px / 3rem     (hero secondary)
5xl:  64px / 4rem     (hero primary)
6xl:  80px / 5rem     (display)`

**Responsive Scale Adjustment:**

css

`:root {
  --text-base: 16px;
  --text-scale: 1.2;
}

@media (min-width: 768px) {
  :root {
    --text-scale: 1.25;
  }
}

@media (min-width: 1280px) {
  :root {
    --text-scale: 1.333;
  }
}`

### D. Font Loading Best Practices

html

`<head>
  *<!-- Preconnect for performance -->*
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  
  *<!-- Load only needed weights -->*
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&family=Plus+Jakarta+Sans:wght@400;500;600&display=swap" rel="stylesheet">
  
  <style>
    */* Fallback stack */*
    body {
      font-family: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    }
  </style>
</head>`

### E. Typographic Details (Polish Layer)

css

`body {
  */* Optical adjustments */*
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  */* Readability */*
  line-height: 1.6; */* body text */*
  letter-spacing: -0.01em; */* tight for display */*
}

h1, h2, h3 {
  line-height: 1.2; */* tighter for headlines */*
  letter-spacing: -0.02em; */* optical correction for large sizes */*
  font-weight: 700;
}

.lead-text {
  font-size: 1.25rem;
  line-height: 1.7;
  color: var(--color-muted);
}

.small-caps {
  font-variant: small-caps;
  letter-spacing: 0.05em;
}`

---

## V. Layout Architecture

### A. Grid Systems

### **1. Traditional 12-Column** (Corporate, SaaS)

css

`.container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 24px;
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 24px;
}

.col-span-6 { grid-column: span 6; }
.col-span-8 { grid-column: span 8; }`

### **2. Asymmetric Grid** (Editorial, Creative)

css

`.grid-editorial {
  display: grid;
  grid-template-columns: 2fr 3fr; */* 40/60 split */*
  gap: 64px;
}

.grid-sidebar {
  grid-template-columns: 1fr 2.5fr; */* content + narrow sidebar */*
}`

### **3. CSS Grid Areas** (Complex layouts)

css

`.layout {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  grid-template-columns: 200px 1fr 300px;
  grid-template-rows: auto 1fr auto;
  gap: 24px;
  min-height: 100vh;
}`

### B. Spacing Scale

**Base Unit: 4px or 8px**

css

`:root {
  --space-1: 0.25rem; */* 4px */*
  --space-2: 0.5rem;  */* 8px */*
  --space-3: 0.75rem; */* 12px */*
  --space-4: 1rem;    */* 16px */*
  --space-5: 1.5rem;  */* 24px */*
  --space-6: 2rem;    */* 32px */*
  --space-8: 3rem;    */* 48px */*
  --space-10: 4rem;   */* 64px */*
  --space-12: 6rem;   */* 96px */*
  --space-16: 8rem;   */* 128px */*
  --space-20: 10rem;  */* 160px */*
}`

**Application Strategy:**

- Component padding: 12-24px (space-3 to space-6)
- Section padding: 64-128px (space-10 to space-16)
- Container max-width: 1280px (content), 1440px (dashboard)
- Content max-width: 680px (optimal reading)

### C. Responsive Breakpoints

css

`*/* Mobile-first approach */*
:root {
  --breakpoint-sm: 640px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 1024px;
  --breakpoint-xl: 1280px;
  --breakpoint-2xl: 1536px;
}

*/* Usage */*
@media (min-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}`

**Mobile Considerations:**

- Touch targets: Minimum 44x44px
- Readable font: Never below 16px (prevents zoom on iOS)
- Thumb-friendly: Important actions in lower 60% of screen
- Reduced motion: Respect `prefers-reduced-motion`

---

## VI. Component Library Patterns

### A. Button System

css

`*/* Base button */*
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  font-weight: 500;
  line-height: 1;
  border-radius: 0.5rem;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
  text-decoration: none;
}

*/* Variants */*
.btn-primary {
  background: var(--color-primary);
  color: white;
}

.btn-primary:hover {
  background: var(--color-primary-hover);
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.btn-primary:active {
  transform: translateY(0);
}

.btn-secondary {
  background: transparent;
  color: var(--color-primary);
  border: 1px solid var(--color-border);
}

.btn-ghost {
  background: transparent;
  color: var(--color-foreground);
}

.btn-ghost:hover {
  background: var(--color-muted);
}

*/* Sizes */*
.btn-sm { padding: 0.5rem 1rem; font-size: 0.875rem; }
.btn-lg { padding: 1rem 2rem; font-size: 1.125rem; }

*/* States */*
.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none !important;
}

.btn:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}`

### B. Card System

css

`.card {
  background: var(--color-background);
  border: 1px solid var(--color-border);
  border-radius: 0.75rem;
  padding: 1.5rem;
  transition: all 0.3s ease;
}

.card-interactive {
  cursor: pointer;
}

.card-interactive:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 24px rgba(0,0,0,0.1);
  border-color: var(--color-primary);
}

*/* Card header with actions */*
.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--color-border);
}

.card-title {
  font-size: 1.125rem;
  font-weight: 600;
  margin: 0;
}

.card-content {
  color: var(--color-muted-foreground);
}`

### C. Form Elements

css

`*/* Input fields */*
.input {
  width: 100%;
  padding: 0.75rem 1rem;
  font-size: 1rem;
  border: 1px solid var(--color-border);
  border-radius: 0.5rem;
  background: var(--color-background);
  transition: all 0.2s ease;
}

.input:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(var(--color-primary-rgb), 0.1);
}

.input::placeholder {
  color: var(--color-muted-foreground);
}

.input:disabled {
  background: var(--color-muted);
  cursor: not-allowed;
}

*/* Form group */*
.form-group {
  margin-bottom: 1.5rem;
}

.label {
  display: block;
  margin-bottom: 0.5rem;
  font-size: 0.875rem;
  font-weight: 500;
  color: var(--color-foreground);
}

.help-text {
  margin-top: 0.5rem;
  font-size: 0.875rem;
  color: var(--color-muted-foreground);
}

*/* Error state */*
.input-error {
  border-color: var(--color-error);
}

.error-message {
  margin-top: 0.5rem;
  font-size: 0.875rem;
  color: var(--color-error);
}`

### D. Navigation Patterns

css

`*/* Horizontal nav */*
.nav {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem 0;
}

.nav-link {
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
  font-weight: 500;
  color: var(--color-muted-foreground);
  text-decoration: none;
  border-radius: 0.375rem;
  transition: all 0.2s ease;
}

.nav-link:hover {
  color: var(--color-foreground);
  background: var(--color-muted);
}

.nav-link.active {
  color: var(--color-primary);
  background: rgba(var(--color-primary-rgb), 0.1);
}

*/* Vertical sidebar nav */*
.sidebar-nav {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.sidebar-link {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1rem;
  color: var(--color-muted-foreground);
  text-decoration: none;
  border-radius: 0.5rem;
  transition: all 0.2s ease;
}

.sidebar-link:hover {
  background: var(--color-muted);
  color: var(--color-foreground);
}`

---

## VII. Motion & Interaction Design

### A. Motion Philosophy by Context

```
ContextDurationEasingPurposeMicro-interactions100-200msease-outInstant feedbackTransitions200-300msease-in-outState changesEntrances300-500msease-outDraw attentionComplex animations500-800mscustom cubic-bezierStorytelling
```

### B. Easing Functions

css

`:root {
  */* Standard easings */*
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  
  */* Custom easings */*
  --ease-smooth: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
  --ease-spring: cubic-bezier(0.175, 0.885, 0.32, 1.275);
}`

### C. Common Animation Patterns

css

`*/* Fade in */*
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

*/* Slide up */*
@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

*/* Scale in */*
@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

*/* Skeleton loading */*
@keyframes shimmer {
  0% {
    background-position: -1000px 0;
  }
  100% {
    background-position: 1000px 0;
  }
}

.skeleton {
  background: linear-gradient(
    90deg,
    var(--color-muted) 0%,
    var(--color-border) 50%,
    var(--color-muted) 100%
  );
  background-size: 1000px 100%;
  animation: shimmer 2s infinite;
}`

### D. Interaction States

css

`*/* Universal interactive element pattern */*
.interactive {
  position: relative;
  transition: all 0.2s var(--ease-out);
}

.interactive:hover {
  transform: translateY(-2px);
}

.interactive:active {
  transform: translateY(0) scale(0.98);
}

.interactive:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

*/* Ripple effect on click */*
.interactive::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  background: currentColor;
  opacity: 0;
  transform: scale(0);
  transition: all 0.4s ease;
}

.interactive:active::after {
  opacity: 0.1;
  transform: scale(1);
}`

### E. Scroll-Driven Animations

html

`*<!-- Intersection Observer for scroll reveals -->*
<script>
const observerOptions = {
  threshold: 0.1,
  rootMargin: '0px 0px -100px 0px'
};

const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('animate-in');
      observer.unobserve(entry.target);
    }
  });
}, observerOptions);

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>

<style>
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.6s var(--ease-out);
}

.reveal.animate-in {
  opacity: 1;
  transform: translateY(0);
}

*/* Stagger children */*
.stagger-children > * {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.5s var(--ease-out);
}

.stagger-children.animate-in > * {
  opacity: 1;
  transform: translateY(0);
}

.stagger-children.animate-in > *:nth-child(1) { transition-delay: 0.1s; }
.stagger-children.animate-in > *:nth-child(2) { transition-delay: 0.2s; }
.stagger-children.animate-in > *:nth-child(3) { transition-delay: 0.3s; }
</style>`

### F. Reduced Motion

css

`@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}`

---

## VIII. Icon System

### A. Lucide Icons Implementation

html

`*<!-- CDN -->*
<script src="https://unpkg.com/lucide@latest/dist/umd/lucide.min.js"></script>

*<!-- Usage -->*
<i data-lucide="check-circle" class="icon"></i>
<i data-lucide="arrow-right" class="icon-sm"></i>

<script>
  lucide.createIcons();
</script>

<style>
.icon {
  width: 24px;
  height: 24px;
  stroke-width: 2;
}

.icon-sm { width: 16px; height: 16px; }
.icon-lg { width: 32px; height: 32px; }

*/* Icon colors */*
.icon-primary { color: var(--color-primary); }
.icon-muted { color: var(--color-muted-foreground); }
</style>`

### B. Icon Naming Conventions

**Common Icons by Use Case:**

- **Navigation**: menu, x, chevron-down, arrow-right
- **Actions**: plus, edit-2, trash-2, download, upload
- **Status**: check-circle, alert-circle, info, x-circle
- **Social**: github, twitter, linkedin, mail
- **UI**: search, filter, settings, user, home

### C. Custom SVG Icons

html

`*<!-- Inline SVG for custom icons -->*
<svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor">
  <path d="M12 2L2 7l10 5 10-5-10-5z"/>
  <path d="M2 17l10 5 10-5M2 12l10 5 10-5"/>
</svg>

<style>
.icon {
  width: 24px;
  height: 24px;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
}
</style>`

---

## IX. Accessibility Standards

### A. WCAG Compliance Checklist

**Level AA (minimum standard):**

1. **Color Contrast**
    - Body text: 4.5:1 minimum
    - Large text (18pt+): 3:1 minimum
    - UI components: 3:1 minimum

css

`*/* Test your contrasts */*
.text-primary {
  color: #18181B; */* vs white = 16.91:1 ✓ */*
}

.text-muted {
  color: #71717A; */* vs white = 4.54:1 ✓ */*
}

.btn-primary {
  background: #2563EB; */* vs white text = 4.56:1 ✓ */*
}`

1. **Keyboard Navigation**

css

`*/* Visible focus states */*
*:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

*/* Skip to content link */*
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: var(--color-primary);
  color: white;
  padding: 8px;
  text-decoration: none;
  z-index: 100;
}

.skip-link:focus {
  top: 0;
}`

1. **Semantic HTML**

html

`*<!-- Use proper heading hierarchy -->*
<h1>Page Title</h1>
  <h2>Section</h2>
    <h3>Subsection</h3>

*<!-- Use semantic elements -->*
<nav aria-label="Main navigation">...</nav>
<main>...</main>
<aside aria-label="Sidebar">...</aside>
<footer>...</footer>

*<!-- Buttons vs links -->*
<button type="button">Trigger action</button>
<a href="/page">Navigate to page</a>`

1. **ARIA Labels**

html

`*<!-- Icon-only buttons -->*
<button aria-label="Close menu">
  <i data-lucide="x"></i>
</button>

*<!-- Form labels -->*
<label for="email">Email address</label>
<input id="email" type="email" name="email">

*<!-- Loading states -->*
<button aria-busy="true" aria-label="Loading...">
  <span class="spinner"></span>
</button>

*<!-- Hidden content -->*
<div aria-live="polite" aria-atomic="true" class="sr-only">
  Item added to cart
</div>`

1. **Screen Reader Only Text**

css

`.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  padding: inherit;
  margin: inherit;
  overflow: visible;
  clip: auto;
  white-space: normal;
}`

### B. Touch & Mobile Accessibility

css

`*/* Minimum touch target size */*
.touch-target {
  min-width: 44px;
  min-height: 44px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

*/* Prevent zoom on input focus (iOS) */*
input, select, textarea {
  font-size: 16px; */* minimum to prevent zoom */*
}

*/* Safe area for notched devices */*
.container {
  padding-left: max(24px, env(safe-area-inset-left));
  padding-right: max(24px, env(safe-area-inset-right));
}`

---

## X. Performance Optimization

### A. CSS Architecture

css

`*/* Use CSS custom properties for theming */*
:root {
  */* Colors */*
  --color-primary: #2563EB;
  --color-primary-rgb: 37, 99, 235;
  
  */* Spacing */*
  --space-unit: 0.25rem;
  
  */* Typography */*
  --font-sans: 'Plus Jakarta Sans', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
}

*/* Minimize specificity */*
.card { } */* Good */*
.container .card { } */* Avoid */*
div.card#featured { } */* Never *//* Use utility classes for common patterns */*
.flex { display: flex; }
.items-center { align-items: center; }
.gap-4 { gap: 1rem; }`

### B. Image Optimization

html

`*<!-- Responsive images -->*
<img
  src="image-800.jpg"
  srcset="image-400.jpg 400w, image-800.jpg 800w, image-1200.jpg 1200w"
  sizes="(max-width: 640px) 100vw, (max-width: 1024px) 50vw, 800px"
  alt="Description"
  loading="lazy"
  decoding="async"
>

*<!-- Modern formats with fallback -->*
<picture>
  <source srcset="image.avif" type="image/avif">
  <source srcset="image.webp" type="image/webp">
  <img src="image.jpg" alt="Description">
</picture>

*<!-- Blur placeholder -->*
<div class="image-container" style="background-image: url('data:image/svg+xml;base64,PHN2Zy...')">
  <img src="full-image.jpg" alt="Description" loading="lazy">
</div>`

### C. Loading Strategies

html

`*<!-- Critical CSS inline -->*
<head>
  <style>
    */* Above-the-fold styles here */*
    body { font-family: system-ui; margin: 0; }
    .hero { min-height: 100vh; }
  </style>
  
  *<!-- Non-critical CSS deferred -->*
  <link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
  <noscript><link rel="stylesheet" href="styles.css"></noscript>
</head>

*<!-- Lazy load below-fold content -->*
<script>
if ('IntersectionObserver' in window) {
  const lazyImages = document.querySelectorAll('img[loading="lazy"]');
  *// Browser handles it natively*
} else {
  *// Polyfill for older browsers*
}
</script>`

---

## XI. Dark Mode Implementation

### A. CSS Variable Strategy

css

`:root {
  */* Light mode (default) */*
  --color-background: #FFFFFF;
  --color-foreground: #18181B;
  --color-muted: #F4F4F5;
  --color-muted-foreground: #71717A;
  --color-border: #E4E4E7;
  --color-primary: #2563EB;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-background: #09090B;
    --color-foreground: #FAFAFA;
    --color-muted: #27272A;
    --color-muted-foreground: #A1A1AA;
    --color-border: #3F3F46;
    --color-primary: #3B82F6;
  }
}

*/* Manual toggle class */*
.dark {
  --color-background: #09090B;
  --color-foreground: #FAFAFA;
  */* ... rest of dark palette */*
}`

### B. Dark Mode Toggle

html

`<button id="theme-toggle" aria-label="Toggle dark mode">
  <i data-lucide="sun" class="sun-icon"></i>
  <i data-lucide="moon" class="moon-icon"></i>
</button>

<script>
const toggle = document.getElementById('theme-toggle');
const html = document.documentElement;

*// Check saved preference or system preference*
const savedTheme = localStorage.getItem('theme');
const systemTheme = window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light';
const currentTheme = savedTheme || systemTheme;

html.classList.toggle('dark', currentTheme === 'dark');

toggle.addEventListener('click', () => {
  html.classList.toggle('dark');
  const theme = html.classList.contains('dark') ? 'dark' : 'light';
  localStorage.setItem('theme', theme);
  lucide.createIcons(); *// Refresh icons*
});
</script>

<style>
.dark .sun-icon { display: none; }
.dark .moon-icon { display: block; }
.sun-icon { display: block; }
.moon-icon { display: none; }
</style>`

### C. Dark Mode Color Adjustments

css

`*/* Images in dark mode */*
.dark img {
  opacity: 0.9;
}

*/* Shadows in dark mode */*
.card {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.dark .card {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
  border-color: rgba(255, 255, 255, 0.1);
}

*/* Syntax highlighting adjustments */*
.dark code {
  background: rgba(255, 255, 255, 0.1);
}
```

---

## XII. Anti-Patterns & Quality Checklist

### A. Visual Red Flags (Avoid These)

**Instant "AI Slop" Indicators:**
- [ ] Pure white (#FFFFFF) backgrounds with default Tailwind colors
- [ ] Inter as the only font choice
- [ ] Generic purple (#8B5CF6) or blue (#3B82F6) as primary
- [ ] Floating gradient blobs as decoration
- [ ] Rainbow gradient text on headings
- [ ] Default "hero with laptop mockup" layout
- [ ] Identical card sizes in a grid (no hierarchy)
- [ ] Over-reliance on emojis instead of proper icons
- [ ] Inconsistent border-radius (mixing 4px, 8px, 12px, 16px)
- [ ] No hover states or all identical hover states

**Technical Debt Markers:**
- [ ] Inline styles instead of classes
- [ ] Magic numbers instead of CSS variables
- [ ] No focus states for keyboard navigation
- [ ] Missing alt text on images
- [ ] Fixed px widths on containers (not responsive)
- [ ] JavaScript for things CSS can do
- [ ] No loading/error states
- [ ] Inaccessible color contrasts

### B. Quality Assurance Checklist

**Before Shipping:**

**Visual Design:**
- [ ] Typography scale is consistent and intentional
- [ ] Spacing follows 4px/8px grid throughout
- [ ] Color contrast meets WCAG AA (4.5:1 for text)
- [ ] One clear visual hierarchy per page
- [ ] Consistent border-radius across all elements
- [ ] Hover states on all interactive elements
- [ ] Loading states for async content
- [ ] Empty states with helpful messaging

**Interaction:**
- [ ] All buttons have focus-visible outlines
- [ ] Form validation with clear error messages
- [ ] Keyboard navigation works logically
- [ ] Touch targets are 44px minimum
- [ ] Animations respect prefers-reduced-motion
- [ ] No layout shift during loading (CLS < 0.1)

**Responsive:**
- [ ] Tested at 375px, 768px, 1024px, 1440px
- [ ] Touch-friendly spacing on mobile
- [ ] Readable font sizes (16px min on mobile)
- [ ] Images use srcset/sizes
- [ ] Hamburger menu on mobile is accessible
- [ ] No horizontal scroll at any breakpoint

**Performance:**
- [ ] Critical CSS inlined
- [ ] Fonts subset and preloaded
- [ ] Images lazy loaded below fold
- [ ] No render-blocking scripts
- [ ] LCP < 2.5s, FID < 100ms

**Accessibility:**
- [ ] Semantic HTML structure
- [ ] ARIA labels where needed
- [ ] Alt text on all images
- [ ] Forms have proper labels
- [ ] Headings follow logical hierarchy (no skipping)
- [ ] Skip navigation link present
- [ ] Color is not the only indicator

---

## XIII. Output Protocol

When generating a design, follow this structure:

### 1. Design Brief (2-3 sentences)
```
Archetype: [Selected archetype]
Purpose: [Primary job to be done]
Mood: [2-3 adjectives]
```

### 2. Visual System Definition
```
Fonts:
- Display: [Font name] (weights: 700)
- Body: [Font name] (weights: 400, 500)

Colors:
- Background: [hex]
- Foreground: [hex]
- Primary: [hex]
- Accent: [hex] (if applicable)

Layout:
- Container: [max-width]px
- Grid: [column structure]
- Spacing: [base unit]px rhythm`

### 3. Complete Code

Generate production-ready HTML with:

- Semantic structure
- Inline critical CSS (with CSS variables)
- Lucide icons via CDN
- Google Fonts preconnected
- Responsive breakpoints
- Accessibility attributes
- Interactive states
- Example content that demonstrates the system

### 4. Usage Notes (Optional)

Brief notes on:

- Key interaction patterns
- Customization points
- Performance considerations
- Browser support notes (if relevant)

---

## XIV. Tool-Specific Adaptations

### For Lovable/Bolt/AI IDEs:

- Prioritize React components over vanilla HTML
- Use Tailwind utilities but customize the config
- Include TypeScript types for props
- Provide clear component composition examples

### For Cursor/Copilot:

- Focus on systematic CSS architecture
- Provide clear variable naming conventions
- Include comprehensive comments
- Show modular file structure

### For Claude/ChatGPT:

- Deliver complete, copy-paste ready code
- Include all necessary CDN links
- Provide inline documentation
- Show before/after customization examples

---

## XV. Advanced Techniques

### A. Scroll-Driven Storytelling

html

`<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<script>
gsap.registerPlugin(ScrollTrigger);

*// Parallax effect*
gsap.to('.hero-image', {
  yPercent: 50,
  ease: 'none',
  scrollTrigger: {
    trigger: '.hero',
    start: 'top top',
    end: 'bottom top',
    scrub: true
  }
});

*// Reveal on scroll*
gsap.utils.toArray('.reveal').forEach(element => {
  gsap.from(element, {
    y: 100,
    opacity: 0,
    duration: 1,
    scrollTrigger: {
      trigger: element,
      start: 'top 80%',
      end: 'top 50%',
      scrub: 1
    }
  });
});
</script>`

### B. Micro-Interactions Library

css

`*/* Button ripple effect */*
.btn-ripple {
  position: relative;
  overflow: hidden;
}

.btn-ripple::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}

.btn-ripple:active::after {
  width: 300px;
  height: 300px;
}

*/* Magnetic button */*
.btn-magnetic {
  transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

<script>
document.querySelectorAll('.btn-magnetic').forEach(btn => {
  btn.addEventListener('mousemove', (e) => {
    const rect = btn.getBoundingClientRect();
    const x = e.clientX - rect.left - rect.width / 2;
    const y = e.clientY - rect.top - rect.height / 2;
    btn.style.transform = `translate(${x * 0.2}px, ${y * 0.2}px)`;
  });
  
  btn.addEventListener('mouseleave', () => {
    btn.style.transform = '';
  });
});
</script>`

### C. Advanced Grid Layouts

css

`*/* Masonry layout (CSS only) */*
.masonry {
  column-count: 3;
  column-gap: 24px;
}

.masonry-item {
  break-inside: avoid;
  margin-bottom: 24px;
}

@media (max-width: 768px) {
  .masonry {
    column-count: 2;
  }
}

*/* Bento box layout */*
.bento-grid {
  display: grid;
  grid-template-`

`columns: repeat(auto-fit, minmax(250px, 1fr));
grid-auto-rows: 200px;
gap: 24px;
}`

`.bento-item-large {
grid-column: span 2;
grid-row: span 2;
}`

`.bento-item-wide {
grid-column: span 2;
}`

`.bento-item-tall {
grid-row: span 2;
}`

`### D. Custom Cursor Effects
```html
<div class="cursor-dot" data-cursor-dot></div>
<div class="cursor-outline" data-cursor-outline></div>

<style>
.cursor-dot,
.cursor-outline {
  pointer-events: none;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  opacity: 1;
  transition: opacity 0.3s ease-in-out, transform 0.3s ease-in-out;
  z-index: 9999;
}

.cursor-dot {
  width: 8px;
  height: 8px;
  background: var(--color-primary);
}

.cursor-outline {
  width: 40px;
  height: 40px;
  border: 2px solid var(--color-primary);
}
</style>

<script>
const cursorDot = document.querySelector('[data-cursor-dot]');
const cursorOutline = document.querySelector('[data-cursor-outline]');

window.addEventListener('mousemove', (e) => {
  const posX = e.clientX;
  const posY = e.clientY;
  
  cursorDot.style.left = `${posX}px`;
  cursorDot.style.top = `${posY}px`;
  
  cursorOutline.animate({
    left: `${posX}px`,
    top: `${posY}px`
  }, { duration: 500, fill: 'forwards' });
});
</script>
```

---

## XVI. Real-World Examples

### Example 1: SaaS Landing Page`

Archetype: SaaS/Tech
Purpose: Convert visitors to trial signups
Mood: Professional, trustworthy, efficient

Fonts:

- Display: Space Grotesk (700)
- Body: Inter (400, 500)

Colors:

- Background: `#FAFAFA`
- Foreground: `#18181B`
- Primary: `#2563EB`
- Muted: `#71717A`
- Border: `#E4E4E7`

Layout:

- Container: 1280px
- Grid: 12-column
- Spacing: 8px rhythm
- Sections: 96px vertical padding

`### Example 2: Creative Portfolio`

Archetype: Creative/Portfolio
Purpose: Showcase work and attract clients
Mood: Bold, memorable, experimental

Fonts:

- Display: Clash Display (600, 700)
- Body: Synonym (400, 500)

Colors:

- Background: `#0A0A0A`
- Foreground: `#FAFAFA`
- Accent: `#FF6B35`
- Muted: `#A1A1AA`

Layout:

- Container: Full-width sections
- Grid: Asymmetric (7/5, 3/9)
- Spacing: Intentionally uneven (16-200px)
- Scroll-jacking enabled

`### Example 3: Editorial Magazine`

Archetype: Luxury/Editorial
Purpose: Long-form reading experience
Mood: Refined, unhurried, sophisticated

Fonts:

- Display: Fraunces (600, 700)
- Body: Source Serif 4 (400, 600)

Colors:

- Background: `#FBF9F7`
- Foreground: `#1C1917`
- Accent: `#B91C1C`
- Muted: `#78716C`

Layout:

- Container: 680px (content), 1280px (full-bleed images)
- Grid: Single column, wide margins
- Spacing: Generous (128px between articles)
- Pull quotes, dropcaps enabled

`---

## Final Principles

1. **Intentionality Over Trends**: Every design decision should have a reason. Don't follow trends blindly—understand why they work.

2. **Constraints Breed Creativity**: Limiting your palette, typography, and spacing system forces better decisions.

3. **Content First**: Design should elevate content, not compete with it. If your design is more memorable than the message, you've failed.

4. **Performance is UX**: A beautiful site that loads slowly is not beautiful. Optimize aggressively.

5. **Accessibility is Non-Negotiable**: Design that excludes users is bad design, period.

6. **Test With Real Users**: Your design intuition is not enough. Watch people use your interface.

7. **Iterate Relentlessly**: First drafts are always wrong. Refine, simplify, polish.

8. **Break Rules Deliberately**: Know the rules well enough to break them with purpose, not ignorance.

---

**Remember**: The goal is not to create "good" design—it's to create design that solves problems elegantly, serves users effectively, and stands out from the sea of generic AI-generated mediocrity.`