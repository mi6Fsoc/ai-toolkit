---
name: brand-guidelines
description: "Comprehensive framework for visual identity, UI systems, voice, and technical implementation. Use for: generating design tokens, auditing UI, writing copy, and ensuring consistency across codebases."
---

# Brand Guidelines Skill

This skill provides a single source of truth for the brand's visual and verbal identity. It is designed to bridge the gap between design requirements and technical implementation, ensuring consistency across all touchpoints.

---

## 1. Visual Identity Core

### 1.1 Logo Usage

#### Primary Lockup
* **Default Logo:** The primary logo used on light backgrounds with full color.
* **Placement:** Prefer top-left for web interfaces, centered for marketing materials.
* **File Formats:**
  * Vector: `.svg` (web), `.eps` (print)
  * Raster: `.png` with transparent background (minimum 2x resolution)

#### Logo Variations
* **Inverted/Monochrome:**
  * White version for dark backgrounds (hex: `#FFFFFF`)
  * Black version for single-color print (hex: `#000000`)
* **Horizontal vs. Stacked:** Use horizontal lockup when width > 200px; stacked for square/vertical spaces.
* **Icon-Only:** Permitted only when brand recognition is established (e.g., app icons, favicons).

#### Clear Space & Sizing
* **Clear Space Rule:** Minimum safety margin is `x`, where `x` equals the height of the logomark or the cap-height of the wordmark.
  * Example: If logomark is 40px tall, maintain 40px clear space on all sides.
* **Minimum Sizes:**
  * Digital: 24px height (logomark), 120px width (full lockup)
  * Print: 10mm height (logomark), 50mm width (full lockup)
  * Favicon: 32x32px (icon only)

#### Prohibitions
* ❌ Do not rotate, skew, or distort proportions
* ❌ Do not add drop shadows, glows, or outlines
* ❌ Do not change opacity below 100%
* ❌ Do not place on busy backgrounds without a solid backdrop
* ❌ Do not recreate or modify the logo in any way
* ❌ Do not use outdated logo versions

---

### 1.2 Color Palette & Tokens

Define colors using multiple formats for cross-platform compatibility. All colors must pass WCAG AA contrast requirements.

#### Primary Colors (Brand Dominance)
* **`primary-500`** (Main Brand Color)
  * Hex: `#0066FF`
  * RGB: `rgb(0, 102, 255)`
  * HSL: `hsl(216, 100%, 50%)`
  * Usage: Primary CTAs, links, brand moments
* **`primary-600`** (Hover/Active State)
  * Hex: `#0052CC`
  * RGB: `rgb(0, 82, 204)`
  * HSL: `hsl(216, 100%, 40%)`
  * Usage: Hover states, active selections
* **`primary-400`** (Light Variant)
  * Hex: `#3385FF`
  * RGB: `rgb(51, 133, 255)`
  * HSL: `hsl(216, 100%, 60%)`
  * Usage: Backgrounds, disabled states with reduced opacity
* **`primary-700`** (Dark Variant)
  * Hex: `#003D99`
  * RGB: `rgb(0, 61, 153)`
  * HSL: `hsl(216, 100%, 30%)`
  * Usage: Dark mode primary, text on light backgrounds

#### Secondary Colors (Accents & Support)
* **`secondary-500`** (Accent Color)
  * Hex: `#FF6B35`
  * RGB: `rgb(255, 107, 53)`
  * HSL: `hsl(16, 100%, 60%)`
  * Usage: Secondary CTAs, highlights, visual interest
* **`secondary-600`** (Hover State)
  * Hex: `#E55A2B`
  * RGB: `rgb(229, 90, 43)`
  * HSL: `hsl(15, 79%, 53%)`

#### Neutrals (Text, Borders, Backgrounds)
* **`neutral-900`** (Primary Text)
  * Hex: `#1A1A1A`
  * RGB: `rgb(26, 26, 26)`
  * Usage: Headings, body text, high-emphasis content
* **`neutral-700`** (Secondary Text)
  * Hex: `#4A4A4A`
  * RGB: `rgb(74, 74, 74)`
  * Usage: Supporting text, labels, captions
* **`neutral-500`** (Tertiary Text/Icons)
  * Hex: `#8A8A8A`
  * RGB: `rgb(138, 138, 138)`
  * Usage: Placeholder text, disabled states, subtle icons
* **`neutral-300`** (Borders)
  * Hex: `#D1D1D1`
  * RGB: `rgb(209, 209, 209)`
  * Usage: Dividers, input borders, card outlines
* **`neutral-100`** (Background Light)
  * Hex: `#F5F5F5`
  * RGB: `rgb(245, 245, 245)`
  * Usage: Page backgrounds, subtle containers
* **`neutral-50`** (Background Lightest)
  * Hex: `#FAFAFA`
  * RGB: `rgb(250, 250, 250)`
  * Usage: Alternate row backgrounds, hover states

#### Semantic State Colors
* **`success`** (Positive Actions/States)
  * Hex: `#00C853`
  * RGB: `rgb(0, 200, 83)`
  * Usage: Success messages, confirmations, positive metrics
* **`warning`** (Caution/Attention)
  * Hex: `#FFB300`
  * RGB: `rgb(255, 179, 0)`
  * Usage: Warnings, pending states, important notices
* **`error`** (Errors/Destructive Actions)
  * Hex: `#E53935`
  * RGB: `rgb(229, 57, 53)`
  * Usage: Error messages, validation failures, delete actions
* **`info`** (Informational)
  * Hex: `#1E88E5`
  * RGB: `rgb(30, 136, 229)`
  * Usage: Info messages, tips, neutral notifications

#### Background Variants (Tints)
For subtle backgrounds, use primary/secondary colors at 10% opacity:
* **`primary-tint`**: `rgba(0, 102, 255, 0.1)` - Light blue background
* **`secondary-tint`**: `rgba(255, 107, 53, 0.1)` - Light orange background
* **`success-tint`**: `rgba(0, 200, 83, 0.1)` - Light green background
* **`warning-tint`**: `rgba(255, 179, 0, 0.1)` - Light yellow background
* **`error-tint`**: `rgba(229, 57, 53, 0.1)` - Light red background

---

### 1.3 Typography System

#### Font Families
* **Headings:** `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
  * Weights Available: 400 (Regular), 500 (Medium), 600 (Semibold), 700 (Bold)
  * CDN: `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap`
* **Body Text:** `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
  * Weights Available: 400 (Regular), 500 (Medium)
* **Code/Monospace:** `'JetBrains Mono', 'Fira Code', 'Courier New', monospace`
  * Weight: 400 (Regular)
  * CDN: `https://fonts.googleapis.com/css2?family=JetBrains+Mono&display=swap`

#### Type Scale (Responsive)
Format: `Mobile Size / Desktop Size (Weight, Line-height, Letter-spacing)`

* **`H1` (Page Titles):**
  * Mobile: `32px` / Desktop: `48px`
  * Weight: `700`, Line-height: `1.2`, Letter-spacing: `-0.02em`
  * Use: Page headers, hero titles
* **`H2` (Section Headings):**
  * Mobile: `28px` / Desktop: `36px`
  * Weight: `600`, Line-height: `1.3`, Letter-spacing: `-0.01em`
  * Use: Major section headers
* **`H3` (Subsection Headings):**
  * Mobile: `24px` / Desktop: `28px`
  * Weight: `600`, Line-height: `1.4`, Letter-spacing: `0`
  * Use: Card titles, subsection headers
* **`H4` (Component Headings):**
  * Mobile: `20px` / Desktop: `24px`
  * Weight: `600`, Line-height: `1.4`, Letter-spacing: `0`
  * Use: Component titles, list headers
* **`H5` (Small Headings):**
  * Mobile: `18px` / Desktop: `20px`
  * Weight: `500`, Line-height: `1.5`, Letter-spacing: `0`
* **`Body Large`:**
  * Size: `18px`
  * Weight: `400`, Line-height: `1.6`, Letter-spacing: `0`
  * Use: Intro paragraphs, important body text
* **`Body` (Default):**
  * Size: `16px`
  * Weight: `400`, Line-height: `1.5`, Letter-spacing: `0`
  * Use: Standard body text, descriptions
* **`Body Small`:**
  * Size: `14px`
  * Weight: `400`, Line-height: `1.5`, Letter-spacing: `0`
  * Use: Secondary information, metadata
* **`Caption`:**
  * Size: `12px`
  * Weight: `500`, Line-height: `1.4`, Letter-spacing: `0.05em`, Transform: `uppercase`
  * Use: Labels, tags, timestamps
* **`Code`:**
  * Size: `14px`
  * Weight: `400`, Line-height: `1.6`, Font-family: Monospace
  * Use: Inline code, code blocks

#### Typography Best Practices
* **Hierarchy:** Maintain clear visual hierarchy using size, weight, and color.
* **Line Length:** Optimal reading width is 60-75 characters (approximately 600-700px).
* **Paragraph Spacing:** Use `1em` (16px) between paragraphs.
* **Link Styling:** Underline links in body text; use color only for navigation.

---

## 2. UI & Interaction System

### 2.1 Spacing & Grid

#### Base Unit System
The system uses a **4px base unit**. All spacing must be multiples of 4 (or 8 for larger gaps).

#### Spacing Tokens
* **`xs`**: `4px` - Tight spacing (icon padding, compact lists)
* **`sm`**: `8px` - Small gaps (button padding, form field spacing)
* **`md`**: `16px` - Standard spacing (card padding, section gaps)
* **`lg`**: `24px` - Large spacing (component margins, section padding)
* **`xl`**: `32px` - Extra large (page margins, major sections)
* **`2xl`**: `48px` - Section dividers
* **`3xl`**: `64px` - Major page sections
* **`4xl`**: `96px` - Hero sections, landing page spacing

#### Layout Grid System
* **Desktop (≥1200px):**
  * Columns: 12
  * Max-width: `1200px`
  * Gutter: `24px`
  * Margin: `32px`
* **Tablet (768px - 1199px):**
  * Columns: 8
  * Gutter: `16px`
  * Margin: `24px`
* **Mobile (<768px):**
  * Columns: 4
  * Gutter: `16px`
  * Margin: `16px`

#### Breakpoints
```css
/* Mobile First Approach */
--breakpoint-sm: 640px;   /* Small tablets */
--breakpoint-md: 768px;   /* Tablets */
--breakpoint-lg: 1024px;  /* Small desktops */
--breakpoint-xl: 1280px;  /* Large desktops */
--breakpoint-2xl: 1536px; /* Extra large screens */
```

---

### 2.2 Component Properties

#### Border Radius
* **`none`**: `0px` - Tables, alerts
* **`sm`**: `4px` - Checkboxes, tags, badges
* **`md`**: `8px` - Buttons, inputs, cards
* **`lg`**: `12px` - Modals, large cards
* **`xl`**: `16px` - Feature cards, images
* **`2xl`**: `24px` - Hero images, special containers
* **`full`**: `9999px` - Pills, avatars, circular buttons

#### Shadows (Elevation Levels)
```css
/* Level 0 - Flat */
--shadow-none: none;

/* Level 1 - Subtle (Cards, Inputs) */
--shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);

/* Level 2 - Standard (Buttons, Dropdowns) */
--shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);

/* Level 3 - Elevated (Hover States) */
--shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);

/* Level 4 - Floating (Modals, Popovers) */
--shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.15);

/* Level 5 - Maximum (Dialogs, Overlays) */
--shadow-2xl: 0 25px 50px rgba(0, 0, 0, 0.25);
```

#### Border Widths
* **`thin`**: `1px` - Default borders, dividers
* **`medium`**: `2px` - Focus rings, emphasized borders
* **`thick`**: `4px` - Strong emphasis, loading indicators

#### Opacity Levels
* **`disabled`**: `0.4` - Disabled elements
* **`muted`**: `0.6` - Secondary elements
* **`hover`**: `0.8` - Hover states for images/overlays
* **`full`**: `1.0` - Default state

---

### 2.3 Iconography

#### Icon Style Guidelines
* **Style:** Outline icons with 2px stroke weight
* **Caps:** Rounded line caps and joins
* **Size Standard:** 24x24px bounding box (16px, 20px, 24px, 32px variants)
* **Alignment:** Center-aligned within bounding box
* **Color:** Inherit from parent text color or use `neutral-700`

#### Icon Sizes
* **`xs`**: `16px` - Inline with small text, tight spaces
* **`sm`**: `20px` - Inline with body text, buttons
* **`md`**: `24px` - Default size, navigation, standalone icons
* **`lg`**: `32px` - Feature highlights, empty states
* **`xl`**: `48px` - Hero sections, large empty states

#### Recommended Icon Library
* **Primary:** [Lucide Icons](https://lucide.dev) - Consistent 24x24px grid, outline style
* **Alternative:** [Heroicons](https://heroicons.com) - Tailwind-compatible
* **Installation:**
  ```bash
  npm install lucide-react
  # or
  npm install @heroicons/react
  ```

#### Icon Usage Rules
* Use icons to **support** text, not replace it (except for universally recognized actions)
* Maintain consistent stroke weight across all icons
* Ensure icons have proper ARIA labels when used without text
* Use semantic color for status icons (success=green, error=red, etc.)

---

### 2.4 Motion & Animation

#### Duration Tokens
* **`instant`**: `100ms` - Micro-interactions (checkbox, toggle)
* **`fast`**: `150ms` - Hover states, tooltips
* **`normal`**: `300ms` - Standard transitions (dropdowns, modals)
* **`slow`**: `500ms` - Page transitions, complex animations
* **`slower`**: `700ms` - Dramatic reveals, hero animations

#### Easing Functions
```css
/* Entering elements (start slow, end fast) */
--ease-out: cubic-bezier(0, 0, 0.2, 1);

/* Exiting elements (start fast, end slow) */
--ease-in: cubic-bezier(0.4, 0, 1, 1);

/* Bi-directional (smooth both ways) */
--ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);

/* Bouncy (playful interactions) */
--ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
```

#### Animation Patterns
* **Fade In:** Opacity 0 → 1, duration `fast`, easing `ease-out`
* **Slide In:** Transform `translateY(10px)` → `translateY(0)`, duration `normal`, easing `ease-out`
* **Scale In:** Transform `scale(0.95)` → `scale(1)`, duration `fast`, easing `ease-out`
* **Hover Lift:** Transform `translateY(0)` → `translateY(-2px)`, shadow increase, duration `fast`

#### Accessibility Considerations
* Respect `prefers-reduced-motion` media query
* Disable animations for users who prefer reduced motion:
  ```css
  @media (prefers-reduced-motion: reduce) {
    * {
      animation-duration: 0.01ms !important;
      transition-duration: 0.01ms !important;
    }
  }
  ```

---

## 3. Voice & Tone (Verbal Identity)

### 3.1 Brand Personality

#### Core Traits
* **Helpful:** Anticipate user needs, provide clear guidance
* **Innovative:** Forward-thinking, modern language
* **Concise:** Respect user time, get to the point
* **Approachable:** Friendly but professional
* **Trustworthy:** Honest, transparent, reliable

#### Personality Spectrum
* **Professional vs. Casual:** 70% Professional / 30% Casual
  * Use professional language for legal, financial, or critical actions
  * Use casual tone for onboarding, tips, and community features
* **Technical vs. Simple:** Accessible but precise
  * Avoid jargon unless writing for technical audiences
  * Define technical terms on first use
* **Serious vs. Playful:** 80% Serious / 20% Playful
  * Maintain professionalism in core features
  * Allow personality in empty states, success messages, and easter eggs

---

### 3.2 Writing Mechanics

#### Capitalization Rules
* **Headlines/Buttons:** Sentence case
  * ✅ "Sign up now" | ❌ "Sign Up Now"
  * ✅ "Create new project" | ❌ "Create New Project"
* **Navigation Links:** Title case
  * ✅ "About Us" | ✅ "Contact Support"
* **Form Labels:** Sentence case
  * ✅ "Email address" | ❌ "Email Address"
* **Error Messages:** Sentence case with period
  * ✅ "Please enter a valid email address."

#### Punctuation
* **Buttons/CTAs:** No periods
  * ✅ "Get started" | ❌ "Get started."
* **Sentences:** Always use periods
* **Lists:** Use periods if items are complete sentences
* **Exclamation Points:** Use sparingly (success messages only)
  * ✅ "Welcome aboard!" | ❌ "Error! Something went wrong!"

#### Date & Time Formatting
* **Date Format (US):** `Jan 1, 2024` or `January 1, 2024`
* **Date Format (EU):** `1 Jan 2024` or `1 January 2024`
* **Time Format:** `3:45 PM` (12-hour) or `15:45` (24-hour based on locale)
* **Relative Time:** "2 minutes ago", "Yesterday", "Last week"

#### Number Formatting
* **Spell out:** One through nine
  * ✅ "You have three new messages"
* **Use digits:** 10 and above
  * ✅ "You have 15 new messages"
* **Large numbers:** Use commas or abbreviations
  * ✅ "1,234 users" or "1.2K users"
* **Percentages:** Always use digits
  * ✅ "5% complete"

---

### 3.3 Terminology (Dos and Don'ts)

#### Preferred Terms
| ✅ Use This | ❌ Not This | Context |
|------------|------------|---------|
| Log in / Log out | Sign in / Sign on | Authentication |
| Username | Handle / User ID | Account identification |
| Email address | Email / E-mail | Contact information |
| Delete | Remove / Trash / Erase | Destructive actions |
| Cancel | Abort / Quit | Reversible actions |
| Save | Submit / Apply | Preserving changes |
| Settings | Preferences / Options | Configuration |
| Dashboard | Home / Overview | Main interface |
| Notification | Alert / Message | System messages |
| Error | Failure / Problem | Error states |

#### Voice Examples

**❌ Avoid:**
> "Oops! Something went wrong. Please try again later."

**✅ Prefer:**
> "We couldn't complete your request. Please try again or contact support if the issue persists."

**❌ Avoid:**
> "You must enter a valid email address!"

**✅ Prefer:**
> "Please enter a valid email address."

**❌ Avoid:**
> "Click here to proceed to the next step of the process."

**✅ Prefer:**
> "Continue to next step"

---

### 3.4 Microcopy Guidelines

#### Empty States
* Be encouraging and actionable
* ✅ "No projects yet. Create your first project to get started."
* ❌ "No data available."

#### Error Messages
* Explain what happened and how to fix it
* ✅ "This email is already registered. Try logging in or use a different email."
* ❌ "Error 409: Conflict."

#### Success Messages
* Confirm the action and next steps
* ✅ "Project created! Start adding team members to collaborate."
* ❌ "Success."

#### Loading States
* Set expectations for wait time
* ✅ "Loading your dashboard... This may take a few seconds."
* ❌ "Loading..."

---

## 4. Technical Implementation & Accessibility

### 4.1 Accessibility Standards (WCAG 2.1 AA)

#### Contrast Requirements
* **Normal Text (< 24px):** Minimum 4.5:1 contrast ratio
* **Large Text (≥ 24px or ≥ 19px bold):** Minimum 3:1 contrast ratio
* **UI Components:** Minimum 3:1 contrast ratio for borders, icons, and interactive elements
* **Testing Tools:**
  * [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
  * [Stark Plugin](https://www.getstark.co/) for Figma/Sketch

#### Verified Color Combinations
| Background | Text Color | Contrast Ratio | Pass |
|-----------|-----------|----------------|------|
| `#FFFFFF` | `neutral-900` (#1A1A1A) | 15.8:1 | ✅ AAA |
| `#FFFFFF` | `neutral-700` (#4A4A4A) | 9.1:1 | ✅ AAA |
| `#FFFFFF` | `primary-500` (#0066FF) | 4.6:1 | ✅ AA |
| `primary-500` | `#FFFFFF` | 4.6:1 | ✅ AA |
| `neutral-100` | `neutral-900` | 14.2:1 | ✅ AAA |

#### Focus States
* **All interactive elements** must have a visible `:focus-visible` ring
* **Default Focus Ring:**
  ```css
  :focus-visible {
    outline: 2px solid var(--primary-500);
    outline-offset: 2px;
  }
  ```
* **Alternative (for dark backgrounds):**
  ```css
  :focus-visible {
    outline: 2px solid #FFFFFF;
    outline-offset: 2px;
  }
  ```

#### Keyboard Navigation
* All interactive elements must be keyboard accessible
* Tab order must follow logical reading order
* Provide skip links for repetitive navigation
* Trap focus within modals and dialogs

#### Screen Reader Support
* Use semantic HTML (`<nav>`, `<main>`, `<article>`, etc.)
* Provide `alt` text for all images (empty `alt=""` for decorative images)
* Use ARIA labels for icon-only buttons
  ```html
  <button aria-label="Close dialog">
    <IconX />
  </button>
  ```
* Announce dynamic content changes with ARIA live regions

#### Motion & Animation
* Respect `prefers-reduced-motion` for users with vestibular disorders
* Provide alternatives to auto-playing videos
* Avoid flashing content (no more than 3 flashes per second)

---

### 4.2 Code Implementation

#### CSS Variables (Design Tokens)
```css
:root {
  /* Colors - Primary */
  --color-primary-400: #3385FF;
  --color-primary-500: #0066FF;
  --color-primary-600: #0052CC;
  --color-primary-700: #003D99;
  
  /* Colors - Secondary */
  --color-secondary-500: #FF6B35;
  --color-secondary-600: #E55A2B;
  
  /* Colors - Neutrals */
  --color-neutral-50: #FAFAFA;
  --color-neutral-100: #F5F5F5;
  --color-neutral-300: #D1D1D1;
  --color-neutral-500: #8A8A8A;
  --color-neutral-700: #4A4A4A;
  --color-neutral-900: #1A1A1A;
  
  /* Colors - Semantic */
  --color-success: #00C853;
  --color-warning: #FFB300;
  --color-error: #E53935;
  --color-info: #1E88E5;
  
  /* Spacing */
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 24px;
  --spacing-xl: 32px;
  --spacing-2xl: 48px;
  --spacing-3xl: 64px;
  --spacing-4xl: 96px;
  
  /* Typography */
  --font-family-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-family-mono: 'JetBrains Mono', 'Fira Code', 'Courier New', monospace;
  
  --font-size-h1: 48px;
  --font-size-h2: 36px;
  --font-size-h3: 28px;
  --font-size-h4: 24px;
  --font-size-body: 16px;
  --font-size-small: 14px;
  --font-size-caption: 12px;
  
  /* Border Radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-full: 9999px;
  
  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.15);
  
  /* Animation */
  --duration-fast: 150ms;
  --duration-normal: 300ms;
  --duration-slow: 500ms;
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
}
```

#### Tailwind CSS Configuration
```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: {
          400: '#3385FF',
          500: '#0066FF',
          600: '#0052CC',
          700: '#003D99',
        },
        secondary: {
          500: '#FF6B35',
          600: '#E55A2B',
        },
        neutral: {
          50: '#FAFAFA',
          100: '#F5F5F5',
          300: '#D1D1D1',
          500: '#8A8A8A',
          700: '#4A4A4A',
          900: '#1A1A1A',
        },
        success: '#00C853',
        warning: '#FFB300',
        error: '#E53935',
        info: '#1E88E5',
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        mono: ['JetBrains Mono', 'Courier New', 'monospace'],
      },
      fontSize: {
        'h1': '48px',
        'h2': '36px',
        'h3': '28px',
        'h4': '24px',
      },
      spacing: {
        'xs': '4px',
        'sm': '8px',
        'md': '16px',
        'lg': '24px',
        'xl': '32px',
        '2xl': '48px',
        '3xl': '64px',
        '4xl': '96px',
      },
      borderRadius: {
        'sm': '4px',
        'md': '8px',
        'lg': '12px',
        'xl': '16px',
      },
      boxShadow: {
        'sm': '0 1px 2px rgba(0, 0, 0, 0.05)',
        'md': '0 4px 6px rgba(0, 0, 0, 0.1)',
        'lg': '0 10px 15px rgba(0, 0, 0, 0.1)',
        'xl': '0 20px 25px rgba(0, 0, 0, 0.15)',
      },
      transitionDuration: {
        'fast': '150ms',
        'normal': '300ms',
        'slow': '500ms',
      },
    },
  },
};
```

#### React Component Pattern
```jsx
// Button.jsx - Example component following design system
import React from 'react';
import './Button.css';

const Button = ({ 
  variant = 'primary', 
  size = 'md', 
  children, 
  disabled = false,
  ...props 
}) => {
  return (
    <button
      className={`btn btn--${variant} btn--${size}`}
      disabled={disabled}
      {...props}
    >
      {children}
    </button>
  );
};

export default Button;
```

```css
/* Button.css */
.btn {
  font-family: var(--font-family-sans);
  font-weight: 500;
  border-radius: var(--radius-md);
  transition: all var(--duration-fast) var(--ease-out);
  cursor: pointer;
  border: none;
}

.btn--primary {
  background-color: var(--color-primary-500);
  color: #FFFFFF;
}

.btn--primary:hover:not(:disabled) {
  background-color: var(--color-primary-600);
  transform: translateY(-1px);
  box-shadow: var(--shadow-md);
}

.btn--primary:focus-visible {
  outline: 2px solid var(--color-primary-500);
  outline-offset: 2px;
}

.btn--md {
  padding: var(--spacing-sm) var(--spacing-md);
  font-size: var(--font-size-body);
}

.btn:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}
```

#### Vue Component Pattern
```vue
<!-- Button.vue -->
<template>
  <button
    :class="['btn', `btn--${variant}`, `btn--${size}`]"
    :disabled="disabled"
    v-bind="$attrs"
  >
    <slot />
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    variant: {
      type: String,
      default: 'primary',
      validator: (value) => ['primary', 'secondary', 'outline'].includes(value)
    },
    size: {
      type: String,
      default: 'md',
      validator: (value) => ['sm', 'md', 'lg'].includes(value)
    },
    disabled: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style scoped>
/* Same CSS as React example */
</style>
```

---

## 5. Usage Workflow for AI

When asked to generate code or content, follow this systematic process:

### Step 1: Context Analysis
* **Identify the request type:**
  * UI Component? → Reference Section 2 (UI System)
  * Color/Visual? → Reference Section 1.2 (Color Palette)
  * Copy/Text? → Reference Section 3 (Voice & Tone)
  * Animation? → Reference Section 2.4 (Motion)

### Step 2: Token Retrieval
* **Look up exact values** from this document:
  * Color: Use hex codes from Section 1.2
  * Spacing: Use tokens from Section 2.1
  * Typography: Use scale from Section 1.3
  * Shadows: Use elevation levels from Section 2.2

### Step 3: Implementation
* **For Coding Tasks:**
  * Use CSS variables pattern: `var(--color-primary-500)`
  * Use Tailwind classes: `bg-primary-500 text-white`
  * Follow component patterns from Section 4.2
  * Ensure semantic HTML structure
* **For Writing Tasks:**
  * Apply sentence case for buttons/headlines
  * Use preferred terminology from Section 3.3
  * Match brand personality (70% professional, 30% casual)
  * Keep microcopy concise and actionable

### Step 4: Accessibility Audit
* **Before outputting code, verify:**
  * ✅ Contrast ratios meet WCAG AA (4.5:1 for text)
  * ✅ Focus states are visible on interactive elements
  * ✅ Spacing uses 4px multiples
  * ✅ ARIA labels exist for icon-only buttons
  * ✅ Motion respects `prefers-reduced-motion`

### Step 5: Quality Checklist
* **Visual Consistency:**
  * [ ] Colors match exact hex codes
  * [ ] Spacing uses defined tokens
  * [ ] Typography follows type scale
  * [ ] Border radius matches component type
* **Verbal Consistency:**
  * [ ] Tone matches brand personality
  * [ ] Terminology follows dos/don'ts
  * [ ] Capitalization follows rules
  * [ ] Microcopy is concise and helpful
* **Technical Compliance:**
  * [ ] Semantic HTML used
  * [ ] Accessibility requirements met
  * [ ] CSS variables/Tailwind classes used
  * [ ] Component props map to design tokens

---

## 6. Common Use Cases & Examples

### Use Case 1: Creating a Primary Button
**Request:** "Create a primary button component"

**AI Response:**
```jsx
<button className="bg-primary-500 hover:bg-primary-600 text-white font-medium py-sm px-md rounded-md transition-all duration-fast ease-out focus-visible:outline-2 focus-visible:outline-primary-500 focus-visible:outline-offset-2 disabled:opacity-40 disabled:cursor-not-allowed">
  Get started
</button>
```

**Rationale:**
* Color: `primary-500` (#0066FF) for background
* Hover: `primary-600` (#0052CC)
* Spacing: `py-sm` (8px), `px-md` (16px)
* Border radius: `rounded-md` (8px)
* Text: Sentence case "Get started"
* Accessibility: Focus ring, disabled state

---

### Use Case 2: Writing an Error Message
**Request:** "Write an error message for invalid email"

**AI Response:**
```
Please enter a valid email address.
```

**Rationale:**
* Sentence case with period
* Concise and actionable
* No exclamation point (professional tone)
* Uses preferred term "email address"

---

### Use Case 3: Designing a Card Component
**Request:** "Create a card with shadow and rounded corners"

**AI Response:**
```jsx
<div className="bg-white rounded-lg shadow-md p-lg border border-neutral-300">
  <h3 className="text-h4 font-semibold text-neutral-900 mb-sm">
    Card title
  </h3>
  <p className="text-body text-neutral-700">
    Card description goes here.
  </p>
</div>
```

**Rationale:**
* Border radius: `rounded-lg` (12px) for cards
* Shadow: `shadow-md` (Level 2 elevation)
* Spacing: `p-lg` (24px) padding, `mb-sm` (8px) margin
* Typography: `text-h4` (24px) for title, `text-body` (16px) for description
* Colors: `neutral-900` for heading, `neutral-700` for body text

---

## 7. Maintenance & Updates

### Version Control
* **Current Version:** 2.0
* **Last Updated:** 2026-01-31
* **Change Log:**
  * v2.0 - Comprehensive expansion with implementation examples
  * v1.0 - Initial brand guidelines

### Review Cycle
* **Quarterly Review:** Assess color accessibility, typography trends
* **Annual Audit:** Full brand refresh evaluation
* **Ad-hoc Updates:** As needed for new components or features

### Feedback Loop
* Collect feedback from designers, developers, and content creators
* Document edge cases and exceptions
* Update examples based on real-world usage

---

## 8. Resources & Tools

### Design Tools
* **Figma Plugin:** [Stark](https://www.getstark.co/) - Accessibility checker
* **Color Contrast:** [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
* **Icon Library:** [Lucide Icons](https://lucide.dev)

### Development Tools
* **CSS Variables Generator:** Use Section 4.2 as template
* **Tailwind Config:** Copy configuration from Section 4.2
* **Component Library:** Build from patterns in Section 4.2

### Documentation
* **WCAG Guidelines:** [W3C WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* **Typography Best Practices:** [Practical Typography](https://practicaltypography.com/)
* **Motion Design:** [Material Design Motion](https://m3.material.io/styles/motion)

---

## Quick Reference Card

### Most Common Tokens
```
Primary Color:    #0066FF (primary-500)
Text Color:       #1A1A1A (neutral-900)
Background:       #FFFFFF
Border:           #D1D1D1 (neutral-300)

Spacing:          8px (sm), 16px (md), 24px (lg)
Border Radius:    8px (md) for buttons/cards
Shadow:           0 4px 6px rgba(0,0,0,0.1) (md)

Font:             Inter, 16px, 400 weight
Heading:          Inter, 24px, 600 weight

Button Text:      Sentence case, no period
Error Message:    Sentence case, with period
```

---

**End of Brand Guidelines**
