---
name: ux-ui-principles-pro-max
description: "Comprehensive cognitive, visual, and design intelligence for UX/UI. Includes: Laws of UX (cognitive psychology), visual design principles, accessibility (WCAG), interaction design, 100 industry-specific reasoning rules, 67 UI styles database, 96 color palettes, 57 typography pairings, 24 landing page patterns, 25 chart types, 13 tech stack guidelines, and 99 UX best practices. Use for: design system generation, layout auditing, usability improvement, accessibility compliance, and creating professional user-centered interfaces."
version: "3.0 - Pro Max Integration"
---

# UX/UI Principles + Pro Max Design Intelligence

**Complete cognitive, behavioral, and visual framework enhanced with AI-powered design intelligence**

This skill combines:
- ✅ **Foundational UX Principles** - Cognitive psychology, visual design, accessibility
- ✅ **Industry-Specific Design Systems** - 100 reasoning rules for automatic design system generation
- ✅ **Searchable Databases** - 67 UI styles, 96 color palettes, 57 font pairings, 25 chart types
- ✅ **Stack-Specific Guidelines** - 13 frameworks (React, Vue, SwiftUI, Flutter, etc.)
- ✅ **99 UX Best Practices** - Common anti-patterns and professional rules

---

## Quick Start Guide

### For Design System Generation

When starting a new UI/UX project, use the design system generator:

```bash
# Check Python is installed (required)
python3 --version

# Generate complete design system
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "beauty spa wellness" --design-system -p "Serenity Spa"
```

This generates:
- Landing page pattern with section structure
- UI style recommendation (from 67 options)
- Complete color palette (from 96 options)
- Typography pairing (from 57 options)
- Key effects and animations
- Anti-patterns to avoid
- Pre-delivery checklist

### For Quick Reference

Search specific domains:

```bash
# UI styles
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py "glassmorphism" --domain style

# Color palettes
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py "fintech" --domain color

# Typography
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py "elegant serif" --domain typography

# UX guidelines
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py "animation accessibility" --domain ux

# Stack-specific
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py "responsive" --stack react
```

---

## Table of Contents

**PART I: FOUNDATIONAL PRINCIPLES**
## 1. Laws of UX (Cognitive Psychology)

Apply these psychological principles to every design decision. These are not suggestions—they are scientifically-backed patterns of human behavior.

### 1.1 Hick's Law
**Principle:** The time it takes to make a decision increases logarithmically with the number and complexity of choices.

**Formula:** `RT = a + b log₂(n)` where RT is reaction time, n is number of choices, and a/b are constants.

**Application:**
- **Navigation:** Limit primary navigation to 5-7 items maximum
- **Forms:** Break long forms into multi-step wizards (progressive disclosure)
- **Menus:** Use categorization and nested menus rather than flat lists
- **CTAs:** Present one primary action per screen when possible

**Examples:**
- ❌ **Bad:** Homepage with 15 top-level navigation items
- ✅ **Good:** Homepage with 5 main categories, each containing sub-items
- ❌ **Bad:** Checkout page with 10 different payment options visible
- ✅ **Good:** Checkout with "Credit Card" selected by default, "More options" link for alternatives

**Code Pattern:**
```javascript
// Progressive disclosure pattern
const [showAdvanced, setShowAdvanced] = useState(false);

return (
  <form>
    {/* Basic fields always visible */}
    <input name="email" />
    <input name="password" />
    
    {/* Advanced options hidden by default */}
    <button onClick={() => setShowAdvanced(!showAdvanced)}>
      {showAdvanced ? 'Hide' : 'Show'} Advanced Options
    </button>
    
    {showAdvanced && (
      <>
        <input name="customDomain" />
        <input name="apiKey" />
      </>
    )}
  </form>
);
```

---

### 1.2 Fitts's Law
**Principle:** The time to acquire a target is a function of the distance to and size of the target.

**Formula:** `MT = a + b log₂(D/W + 1)` where MT is movement time, D is distance, W is width of target.

**Application:**
- **Button Sizing:** Primary CTAs should be 44×44px minimum (mobile), 32×32px minimum (desktop)
- **Proximity:** Place related actions close together (e.g., "Save" and "Cancel" buttons)
- **Corners & Edges:** Screen corners are infinitely large targets (cursor stops at edge)—use for critical actions
- **Touch Targets:** Increase padding around small interactive elements to create larger hit areas

**Examples:**
- ❌ **Bad:** 16×16px icon buttons with no padding on mobile
- ✅ **Good:** 16×16px icons wrapped in 48×48px touch targets
- ❌ **Bad:** "Delete Account" button same size as "Save Changes"
- ✅ **Good:** Primary action (Save) is large and prominent; destructive action (Delete) is smaller, secondary style

**CSS Pattern:**
```css
/* Increase hit area without changing visual size */
.icon-button {
  width: 20px;
  height: 20px;
  padding: 14px; /* Creates 48×48px touch target */
  margin: -14px; /* Prevents layout shift */
}

/* Primary CTA should dominate */
.btn-primary {
  min-height: 48px;
  min-width: 120px;
  font-size: 16px;
  font-weight: 600;
}

.btn-secondary {
  min-height: 36px;
  font-size: 14px;
}
```

---

### 1.3 Jakob's Law
**Principle:** Users spend most of their time on other sites. They prefer your site to work the same way as all the others they already know.

**Application:**
- **Conventions:** Use standard patterns for common UI elements
  - Logo in top-left links to homepage
  - Shopping cart icon in top-right
  - Hamburger menu (☰) for mobile navigation
  - Magnifying glass (🔍) for search
- **Behavior:** Links should be underlined or clearly differentiated; buttons should look clickable
- **Layout:** F-pattern for content-heavy pages, Z-pattern for landing pages
- **Innovation:** Only break conventions when your solution is 10× better AND you can teach it quickly

**Examples:**
- ✅ **Good:** E-commerce site with cart in top-right, search bar in header, filters on left sidebar
- ❌ **Bad:** E-commerce site with unconventional navigation that requires tutorial
- ✅ **Good:** Using standard date picker component
- ❌ **Bad:** Custom date input that requires users to type "YYYY-MM-DD" format

**When to Break Conventions:**
- Your innovation solves a major pain point (e.g., Tinder's swipe interface)
- You can teach the new pattern in < 5 seconds
- The pattern becomes intuitive after one use
- You have data showing it performs better

---

### 1.4 Miller's Law
**Principle:** The average person can only keep 7 (±2) items in their working memory.

**Application:**
- **Chunking:** Group related information into digestible chunks
- **Phone Numbers:** Format as (555) 123-4567 not 5551234567
- **Navigation:** Limit menu items to 5-7 per level
- **Forms:** Group fields into logical sections with clear labels
- **Lists:** Use pagination or infinite scroll for lists > 10 items

**Examples:**
- ❌ **Bad:** Single-page form with 25 fields
- ✅ **Good:** Multi-step form with 4 steps, each containing 4-6 related fields
- ❌ **Bad:** Dropdown with 50 unsorted countries
- ✅ **Good:** Searchable dropdown with common countries at top, rest alphabetized

**Form Chunking Pattern:**
```html
<!-- Step 1: Personal Information -->
<fieldset>
  <legend>Personal Information</legend>
  <input name="firstName" />
  <input name="lastName" />
  <input name="email" />
</fieldset>

<!-- Step 2: Address -->
<fieldset>
  <legend>Shipping Address</legend>
  <input name="street" />
  <input name="city" />
  <input name="zip" />
</fieldset>

<!-- Step 3: Payment -->
<fieldset>
  <legend>Payment Details</legend>
  <input name="cardNumber" />
  <input name="expiry" />
  <input name="cvv" />
</fieldset>
```

---

### 1.5 Gestalt Principles
**Principle:** Users perceive elements as unified wholes rather than individual parts.

#### Proximity
Elements close together are perceived as related.

**Application:**
- Group related form fields together
- Add more spacing between unrelated sections than within sections
- Place labels close to their inputs

**Example:**
```css
/* Related items close together */
.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px; /* Small gap within group */
  margin-bottom: 24px; /* Larger gap between groups */
}
```

#### Similarity
Elements with similar styling are perceived as having the same function.

**Application:**
- All primary CTAs should use the same color and style
- All destructive actions should use consistent warning colors
- Icons of the same category should share visual style

#### Continuity
Elements arranged in a line or curve are perceived as related.

**Application:**
- Use alignment to create visual flow
- Breadcrumbs should follow a clear left-to-right path
- Progress indicators should show clear linear progression

#### Closure
Users mentally complete incomplete shapes.

**Application:**
- Use subtle borders or backgrounds to define card boundaries
- Loading skeletons suggest content structure before it loads

#### Figure/Ground
Users distinguish objects from their background.

**Application:**
- Use contrast to make interactive elements stand out
- Modal overlays should dim background content
- Active/selected states should be clearly differentiated

**Visual Example:**
```css
/* Figure/Ground: Modal overlay */
.modal-backdrop {
  background: rgba(0, 0, 0, 0.6); /* Dims background */
  backdrop-filter: blur(4px); /* Further separates layers */
}

.modal-content {
  background: white;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3); /* Elevates foreground */
}
```

---

### 1.6 Law of Prägnanz (Simplicity)
**Principle:** People will perceive and interpret ambiguous or complex images as the simplest form possible.

**Application:**
- Use simple, recognizable icons
- Avoid unnecessary decorative elements
- Reduce visual noise and clutter
- Use whitespace to create breathing room

**Examples:**
- ✅ **Good:** Simple line icons that are instantly recognizable
- ❌ **Bad:** Overly detailed, photorealistic icons that are hard to parse at small sizes

---

### 1.7 Serial Position Effect
**Principle:** Users best remember the first and last items in a series.

**Application:**
- Place most important navigation items at the beginning and end of menus
- In forms, put critical fields first and confirmation last
- In lists, highlight priority items at top and bottom

---

### 1.8 Zeigarnik Effect
**Principle:** People remember uncompleted or interrupted tasks better than completed tasks.

**Application:**
- Show progress indicators in multi-step processes
- Use "Save Draft" functionality to allow users to return to incomplete tasks
- Display completion percentage to motivate users to finish

**Example:**
```html
<!-- Progress indicator -->
<div class="progress-bar">
  <div class="progress-fill" style="width: 60%"></div>
  <span>Step 3 of 5</span>
</div>
```

---

### 1.9 Peak-End Rule
**Principle:** People judge an experience largely based on how they felt at its peak and at its end.

**Application:**
- Create delightful micro-interactions at key moments
- End user flows with positive confirmation messages
- Celebrate user achievements (e.g., "Account created! 🎉")
- Make error recovery smooth and reassuring

**Examples:**
- ✅ **Good:** After completing checkout, show animated success state with order confirmation
- ✅ **Good:** After uploading files, show satisfying checkmark animation
- ❌ **Bad:** After successful action, just redirect to blank dashboard with no feedback

---

### 1.10 Doherty Threshold
**Principle:** Productivity soars when a computer and its users interact at a pace (<400ms) that ensures neither has to wait on the other.

**Application:**
- Aim for <100ms response to user input (perceived as instantaneous)
- <1s for common tasks (page transitions, form submissions)
- Use optimistic UI updates for perceived speed
- Show loading states for anything >1s

**Performance Budgets:**
- Button hover/active state: <16ms (1 frame at 60fps)
- Form validation feedback: <100ms
- Page navigation: <1s
- Search results: <1s
- Complex calculations: <3s (with progress indicator)

---

## 2. Information Architecture (IA) & Navigation

Information Architecture is the structural design of shared information environments. It's the "map" of your application.

### 2.1 Hierarchy Levels

Organize navigation into clear priority tiers:

#### Primary Navigation (Tier 1)
**Purpose:** Critical user paths that drive core value

**Characteristics:**
- Always visible or easily accessible
- 3-7 items maximum
- Represents main user jobs-to-be-done

**Examples:**
- E-commerce: Home, Shop, Cart, Account
- SaaS: Dashboard, Projects, Team, Settings
- Content: Home, Explore, Library, Profile

**Implementation:**
```html
<nav class="primary-nav">
  <a href="/" class="nav-item active">Dashboard</a>
  <a href="/projects" class="nav-item">Projects</a>
  <a href="/team" class="nav-item">Team</a>
  <a href="/settings" class="nav-item">Settings</a>
</nav>
```

#### Secondary Navigation (Tier 2)
**Purpose:** Utility tasks and supporting features

**Characteristics:**
- Accessible but not prominent
- Can be in dropdown menus or secondary nav bar
- 5-10 items typical

**Examples:**
- Help, Documentation, API, Integrations, Billing, History

**Implementation:**
```html
<nav class="secondary-nav">
  <a href="/help">Help</a>
  <a href="/docs">Docs</a>
  <a href="/api">API</a>
</nav>
```

#### Tertiary Navigation (Tier 3)
**Purpose:** Legal, compliance, and rarely-accessed information

**Characteristics:**
- Footer or hidden menu
- Low visual priority

**Examples:**
- Privacy Policy, Terms of Service, Cookie Policy, Accessibility Statement

---

### 2.2 Wayfinding

Users should always be able to answer three questions:

1. **"Where am I?"**
   - Clear page titles
   - Active states in navigation
   - Breadcrumbs for deep hierarchies

2. **"How did I get here?"**
   - Breadcrumbs showing path
   - Browser back button works correctly
   - Clear navigation trail

3. **"Where can I go next?"**
   - Related links and suggestions
   - Clear CTAs
   - Logical next steps

**Breadcrumb Implementation:**
```html
<nav aria-label="Breadcrumb">
  <ol class="breadcrumb">
    <li><a href="/">Home</a></li>
    <li><a href="/products">Products</a></li>
    <li><a href="/products/electronics">Electronics</a></li>
    <li aria-current="page">Laptops</li>
  </ol>
</nav>
```

```css
.breadcrumb {
  display: flex;
  gap: 8px;
  list-style: none;
}

.breadcrumb li:not(:last-child)::after {
  content: '/';
  margin-left: 8px;
  color: var(--text-muted);
}

.breadcrumb [aria-current="page"] {
  color: var(--text-primary);
  font-weight: 600;
}
```

---

### 2.3 Scanning Patterns

Design layouts that align with natural eye movement patterns.

#### F-Pattern (Content-Heavy Pages)
**When to use:** Articles, search results, lists, forms

**Pattern:**
1. Horizontal scan across top (header/title)
2. Vertical scan down left side (scanning headings)
3. Horizontal scan across middle (subheading or interesting content)
4. Vertical scan continues down left

**Design Implications:**
- Put most important information in top-left
- Use left-aligned headings
- Front-load paragraphs with key information
- Use bullet points and scannable formatting

#### Z-Pattern (Landing Pages)
**When to use:** Simple pages with clear hierarchy, landing pages, hero sections

**Pattern:**
1. Top-left to top-right (logo to CTA)
2. Diagonal to bottom-left (eye travels down)
3. Bottom-left to bottom-right (secondary CTA or footer)

**Design Implications:**
- Logo top-left, primary CTA top-right
- Hero content in center
- Secondary CTA or social proof bottom-right

#### Layer Cake Pattern (Modern Web)
**When to use:** Marketing sites, product pages

**Pattern:**
- Horizontal sections stacked vertically
- Each section is self-contained
- Alternating layouts create rhythm

---

### 2.4 Navigation Patterns

#### Hamburger Menu
**When to use:** Mobile, secondary navigation

**Pros:** Saves space, familiar pattern
**Cons:** Hides content, reduces discovery

**Best Practices:**
- Use only on mobile or for secondary nav
- Animate open/close for clarity
- Include close button (X) in open state

#### Tab Navigation
**When to use:** Related content sections, settings panels

**Best Practices:**
- 3-7 tabs maximum
- Active tab clearly indicated
- Content changes without page reload
- Use `role="tablist"` for accessibility

#### Mega Menu
**When to use:** Large sites with many categories (e-commerce, enterprise)

**Best Practices:**
- Show on hover or click
- Include visual hierarchy (headings, icons, images)
- Limit to 2-3 levels deep
- Include "View All" links

---

## 3. Visual Hierarchy & UI Design

Visual hierarchy guides users' attention to the most important elements first.

### 3.1 The 60-30-10 Rule

**Principle:** Use 60% dominant color, 30% secondary color, 10% accent color.

**Application:**
- **60% Dominant:** Backgrounds, large surfaces (usually neutral: white, light gray, dark gray)
- **30% Secondary:** Supporting elements, cards, sidebars (brand color or complementary neutral)
- **10% Accent:** CTAs, highlights, important UI elements (brand primary color)

**Example Palette:**
```css
:root {
  /* 60% - Dominant (Backgrounds) */
  --bg-primary: #FFFFFF;
  --bg-secondary: #F7F9FC;
  --bg-tertiary: #E8EDF5;
  
  /* 30% - Secondary (Surfaces) */
  --surface-primary: #2D3748;
  --surface-secondary: #4A5568;
  
  /* 10% - Accent (CTAs, highlights) */
  --accent-primary: #3B82F6;
  --accent-hover: #2563EB;
  --accent-active: #1D4ED8;
}
```

---

### 3.2 Scale & Contrast

Use size, weight, and color to create clear hierarchy.

#### Type Scale
Use a modular scale for consistent hierarchy:

```css
:root {
  --text-xs: 0.75rem;    /* 12px - Captions, labels */
  --text-sm: 0.875rem;   /* 14px - Body small, secondary text */
  --text-base: 1rem;     /* 16px - Body text */
  --text-lg: 1.125rem;   /* 18px - Emphasized body */
  --text-xl: 1.25rem;    /* 20px - H4 */
  --text-2xl: 1.5rem;    /* 24px - H3 */
  --text-3xl: 1.875rem;  /* 30px - H2 */
  --text-4xl: 2.25rem;   /* 36px - H1 */
  --text-5xl: 3rem;      /* 48px - Display */
}
```

#### Font Weight
```css
:root {
  --font-normal: 400;    /* Body text */
  --font-medium: 500;    /* Emphasized text */
  --font-semibold: 600;  /* Headings, buttons */
  --font-bold: 700;      /* Strong emphasis */
}
```

#### Color Contrast
Use contrast to differentiate importance:

```css
:root {
  /* Text hierarchy through opacity/color */
  --text-primary: rgba(0, 0, 0, 0.9);    /* Headlines, primary content */
  --text-secondary: rgba(0, 0, 0, 0.7);  /* Body text */
  --text-tertiary: rgba(0, 0, 0, 0.5);   /* Captions, labels */
  --text-disabled: rgba(0, 0, 0, 0.3);   /* Disabled states */
}
```

---

### 3.3 Negative Space (Whitespace)

Whitespace is not wasted space—it's a functional design tool.

**Benefits:**
- Reduces cognitive load
- Groups related elements
- Creates breathing room
- Improves readability
- Adds sophistication

**Spacing Scale:**
```css
:root {
  --space-1: 0.25rem;  /* 4px - Tight spacing */
  --space-2: 0.5rem;   /* 8px - Related elements */
  --space-3: 0.75rem;  /* 12px - Small gaps */
  --space-4: 1rem;     /* 16px - Standard spacing */
  --space-6: 1.5rem;   /* 24px - Section spacing */
  --space-8: 2rem;     /* 32px - Large gaps */
  --space-12: 3rem;    /* 48px - Major sections */
  --space-16: 4rem;    /* 64px - Page sections */
}
```

**Application Rules:**
- Use smaller spacing (4-8px) within components
- Use medium spacing (16-24px) between components
- Use large spacing (48-64px) between page sections
- Increase spacing as screen size increases

---

### 3.4 Grids & Alignment

#### Grid Systems
Use consistent grid systems for alignment:

**12-Column Grid (Standard):**
```css
.container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 24px;
  max-width: 1200px;
  margin: 0 auto;
}

/* Full width */
.col-12 { grid-column: span 12; }

/* Half width */
.col-6 { grid-column: span 6; }

/* Third width */
.col-4 { grid-column: span 4; }

/* Quarter width */
.col-3 { grid-column: span 3; }
```

#### Baseline Grid
Maintain vertical rhythm with a baseline grid:

```css
:root {
  --baseline: 8px; /* All spacing should be multiples of 8px */
}

h1 { 
  font-size: 36px; 
  line-height: 48px; /* 6 × 8px */
  margin-bottom: 24px; /* 3 × 8px */
}

p { 
  font-size: 16px; 
  line-height: 24px; /* 3 × 8px */
  margin-bottom: 16px; /* 2 × 8px */
}
```

#### Optical Alignment
Sometimes mathematical centering looks wrong. Use optical alignment:

**Example: Icon + Text Button**
```css
/* Icons often need slight vertical adjustment */
.button-icon {
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.button-icon svg {
  /* Optically center icon (may need -1px or -2px) */
  margin-top: -1px;
}
```

---

## 4. Interaction Design (IxD)

Interaction design defines how users engage with your interface.

### 4.1 Affordance & Signifiers

**Affordance:** What an object can do (a button can be clicked)
**Signifier:** Visual cue that communicates the affordance (button looks raised/clickable)

**Best Practices:**
- Buttons should look clickable (raised, shadowed, or outlined)
- Links should be underlined or colored differently
- Draggable items should have a grab cursor
- Disabled elements should look inactive (reduced opacity, no hover state)

**Button States:**
```css
.button {
  /* Default: Clearly looks clickable */
  background: var(--accent-primary);
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: all 0.2s ease;
}

.button:hover {
  /* Hover: Responds to interaction */
  background: var(--accent-hover);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
  transform: translateY(-1px);
}

.button:active {
  /* Active: Pressed down */
  transform: translateY(0);
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.button:disabled {
  /* Disabled: Clearly not interactive */
  background: var(--bg-tertiary);
  color: var(--text-disabled);
  cursor: not-allowed;
  box-shadow: none;
}
```

---

### 4.2 Feedback Loops

Every action must have a reaction. Users need to know their action was registered.

#### Immediate Feedback (<100ms)
Visual response to user input:
- Hover states
- Active/pressed states
- Focus rings
- Ripple effects

```css
.button:hover {
  background: var(--accent-hover);
}

.button:active {
  transform: scale(0.98);
}

input:focus {
  outline: 2px solid var(--accent-primary);
  outline-offset: 2px;
}
```

#### Intermediate Feedback (100ms - 3s)
Show progress for ongoing operations:
- Loading spinners
- Progress bars
- Skeleton screens
- Optimistic UI updates

**Loading States:**
```html
<!-- Skeleton screen while loading -->
<div class="skeleton-card">
  <div class="skeleton-image"></div>
  <div class="skeleton-text"></div>
  <div class="skeleton-text short"></div>
</div>
```

```css
.skeleton-image,
.skeleton-text {
  background: linear-gradient(
    90deg,
    #f0f0f0 25%,
    #e0e0e0 50%,
    #f0f0f0 75%
  );
  background-size: 200% 100%;
  animation: loading 1.5s infinite;
}

@keyframes loading {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}
```

#### Final Feedback (>3s or completion)
Confirm completion or error:
- Success messages
- Error messages
- Toast notifications
- Confirmation modals

**Toast Notification Pattern:**
```javascript
function showToast(message, type = 'success') {
  const toast = document.createElement('div');
  toast.className = `toast toast-${type}`;
  toast.textContent = message;
  
  document.body.appendChild(toast);
  
  // Animate in
  setTimeout(() => toast.classList.add('show'), 10);
  
  // Auto-dismiss after 3s
  setTimeout(() => {
    toast.classList.remove('show');
    setTimeout(() => toast.remove(), 300);
  }, 3000);
}
```

---

### 4.3 Error Prevention vs. Error Recovery

**Prevention is better than recovery, but both are necessary.**

#### Error Prevention Strategies

1. **Disable Invalid Actions**
```javascript
// Disable submit until form is valid
<button 
  type="submit" 
  disabled={!isFormValid}
>
  Submit
</button>
```

2. **Input Constraints**
```html
<!-- Prevent invalid input -->
<input 
  type="email" 
  required 
  pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$"
/>

<input 
  type="number" 
  min="0" 
  max="100" 
  step="1"
/>
```

3. **Input Masks**
```javascript
// Format phone number as user types
function formatPhone(value) {
  const cleaned = value.replace(/\D/g, '');
  const match = cleaned.match(/^(\d{3})(\d{3})(\d{4})$/);
  if (match) {
    return '(' + match[1] + ') ' + match[2] + '-' + match[3];
  }
  return value;
}
```

4. **Confirmation for Destructive Actions**
```javascript
// Confirm before deleting
function handleDelete() {
  if (confirm('Are you sure you want to delete this item? This cannot be undone.')) {
    deleteItem();
  }
}
```

#### Error Recovery Strategies

1. **Undo Functionality**
```javascript
// Allow undo after deletion
function deleteItem(id) {
  const item = getItem(id);
  removeItem(id);
  
  showToast(
    'Item deleted. Undo?',
    'warning',
    {
      action: 'Undo',
      onAction: () => restoreItem(item)
    }
  );
}
```

2. **Auto-Save / Draft Mode**
```javascript
// Auto-save form data
useEffect(() => {
  const timer = setTimeout(() => {
    localStorage.setItem('draft', JSON.stringify(formData));
  }, 1000);
  
  return () => clearTimeout(timer);
}, [formData]);
```

3. **Human-Readable Error Messages**
```javascript
// ❌ Bad
"Error 422: Unprocessable Entity"

// ✅ Good
"We couldn't process your request. Please check that your email address is valid and try again."
```

4. **Inline Validation**
```html
<input 
  type="email" 
  aria-invalid={!isValidEmail}
  aria-describedby="email-error"
/>
{!isValidEmail && (
  <span id="email-error" class="error-message">
    Please enter a valid email address
  </span>
)}
```

---

### 4.4 Micro-Interactions

Small, delightful animations that enhance UX:

**Examples:**
- Button hover effects
- Like button animation
- Pull-to-refresh
- Swipe gestures
- Toggle switches
- Loading animations

**Principles:**
- Duration: 200-400ms for most interactions
- Easing: Use ease-out for entrances, ease-in for exits
- Purpose: Every animation should serve a purpose (feedback, guidance, delight)

**Example: Like Button**
```css
.like-button {
  transition: transform 0.2s ease;
}

.like-button:active {
  transform: scale(1.2);
}

.like-button.liked {
  animation: heartbeat 0.3s ease;
}

@keyframes heartbeat {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.3); }
}
```

---

## 5. Accessibility (A11y) & Inclusivity

Accessibility is not optional—it's a legal requirement and moral imperative.

### 5.1 WCAG 2.1 Compliance Levels

- **Level A:** Minimum accessibility (must meet)
- **Level AA:** Recommended standard (should meet)
- **Level AAA:** Enhanced accessibility (nice to have)

**Target: WCAG 2.1 Level AA compliance minimum**

---

### 5.2 Color & Contrast

**WCAG AA Requirements:**
- Normal text (< 18px): 4.5:1 contrast ratio
- Large text (≥ 18px or ≥ 14px bold): 3:1 contrast ratio
- UI components and graphics: 3:1 contrast ratio

**Best Practices:**
- Never rely on color alone to convey meaning
- Add icons or text labels alongside color indicators
- Test with color blindness simulators

**Example:**
```html
<!-- ❌ Bad: Color only -->
<span style="color: red;">Error</span>

<!-- ✅ Good: Color + icon + text -->
<span class="error">
  <svg aria-hidden="true"><!-- X icon --></svg>
  Error: Invalid email address
</span>
```

**Color Blindness Considerations:**
- Avoid red/green as only differentiator
- Use patterns or textures in charts
- Provide text labels for data visualizations

---

### 5.3 Keyboard Navigation

**All interactive elements must be keyboard accessible.**

**Requirements:**
- `Tab` to navigate forward
- `Shift + Tab` to navigate backward
- `Enter` or `Space` to activate
- `Esc` to close modals/dropdowns
- Arrow keys for menus and sliders

**Focus Management:**
```css
/* Visible focus indicator */
:focus-visible {
  outline: 2px solid var(--accent-primary);
  outline-offset: 2px;
}

/* Remove default outline only when using custom */
:focus:not(:focus-visible) {
  outline: none;
}
```

**Focus Trap for Modals:**
```javascript
function trapFocus(element) {
  const focusableElements = element.querySelectorAll(
    'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])'
  );
  
  const firstElement = focusableElements[0];
  const lastElement = focusableElements[focusableElements.length - 1];
  
  element.addEventListener('keydown', (e) => {
    if (e.key === 'Tab') {
      if (e.shiftKey && document.activeElement === firstElement) {
        e.preventDefault();
        lastElement.focus();
      } else if (!e.shiftKey && document.activeElement === lastElement) {
        e.preventDefault();
        firstElement.focus();
      }
    }
  });
}
```

---

### 5.4 Touch Targets

**WCAG 2.1 Success Criterion 2.5.5:**
- Minimum touch target size: 44×44px
- Exception: Inline links in text can be smaller

**Implementation:**
```css
/* Ensure minimum touch target */
.button,
.icon-button,
a {
  min-height: 44px;
  min-width: 44px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

/* For smaller visual elements, increase padding */
.small-icon {
  width: 20px;
  height: 20px;
  padding: 12px; /* Creates 44×44px touch area */
}
```

---

### 5.5 Screen Reader Support

**Semantic HTML:**
Use proper HTML elements for their intended purpose:

```html
<!-- ✅ Good: Semantic HTML -->
<nav>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
  </ul>
</nav>

<main>
  <article>
    <h1>Page Title</h1>
    <p>Content...</p>
  </article>
</main>

<!-- ❌ Bad: Div soup -->
<div class="nav">
  <div class="link">Home</div>
  <div class="link">About</div>
</div>
```

**ARIA Labels:**
```html
<!-- Descriptive labels for screen readers -->
<button aria-label="Close dialog">
  <svg><!-- X icon --></svg>
</button>

<!-- Live regions for dynamic content -->
<div role="status" aria-live="polite">
  Item added to cart
</div>

<!-- Hidden content for screen readers -->
<span class="sr-only">
  Current page: Dashboard
</span>
```

**Screen Reader Only CSS:**
```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

---

### 5.6 Readability

**Line Length:**
- Optimal: 45-75 characters per line
- Maximum: 90 characters per line

```css
.content {
  max-width: 65ch; /* 65 characters */
}
```

**Line Height:**
- Body text: 1.5-1.8
- Headings: 1.2-1.4

```css
p {
  line-height: 1.6;
}

h1, h2, h3 {
  line-height: 1.3;
}
```

**Font Size:**
- Minimum body text: 16px
- Recommended: 16-18px for body, larger for older audiences

---

### 5.7 Motion & Animation

**Respect `prefers-reduced-motion`:**

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 6. Usage Workflow for AI

When analyzing or generating designs, follow this systematic checklist:

### Step 1: Goal Identification
**Question:** What is the *one* primary action the user should take on this screen?

**Actions:**
- Identify the primary CTA
- Ensure it's the most visually prominent element
- Remove or de-emphasize competing actions

---

### Step 2: Friction Audit
**Question:** How many clicks/decisions are required? Can this be reduced?

**Actions:**
- Count steps in user flow
- Apply Hick's Law: Reduce choices
- Use progressive disclosure for complex flows
- Provide smart defaults

**Example:**
- ❌ **High Friction:** 5-step form with all fields on one page
- ✅ **Low Friction:** 3-step wizard with 3-4 fields per step, smart defaults pre-filled

---

### Step 3: Visual Weight Check
**Question:** What is the most prominent element? Is it the right one?

**Actions:**
- Squint test: Blur your vision and see what stands out
- Ensure primary CTA has highest visual weight (size, color, contrast)
- Use hierarchy to guide eye flow

**Visual Weight Factors:**
1. Size (larger = more weight)
2. Color (bright/saturated = more weight)
3. Contrast (high contrast = more weight)
4. Position (top-left and center = more weight)
5. Whitespace (isolated elements = more weight)

---

### Step 4: Accessibility Pass
**Question:** Can everyone use this interface?

**Checklist:**
- [ ] Color contrast meets WCAG AA (4.5:1 for text)
- [ ] All interactive elements have focus states
- [ ] Touch targets are ≥ 44×44px
- [ ] Keyboard navigation works
- [ ] Screen reader tested (or semantic HTML used)
- [ ] Forms have proper labels and error messages
- [ ] Images have alt text
- [ ] Motion respects `prefers-reduced-motion`

---

### Step 5: Pattern Verification
**Question:** Does this follow established conventions?

**Actions:**
- Check against Jakob's Law: Does it work like users expect?
- Verify common patterns (logo top-left, cart top-right, etc.)
- Only break conventions if you have a 10× better solution
- Test with users unfamiliar with your product

---

### Step 6: Feedback & States
**Question:** Does every action have a reaction?

**Checklist:**
- [ ] Hover states for interactive elements
- [ ] Active/pressed states for buttons
- [ ] Loading states for async operations
- [ ] Success/error messages for form submissions
- [ ] Disabled states clearly differentiated
- [ ] Empty states with helpful guidance

---

### Step 7: Mobile Responsiveness
**Question:** Does this work on all screen sizes?

**Breakpoints:**
```css
/* Mobile first approach */
.container {
  padding: 16px;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: 24px;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    padding: 32px;
  }
}

/* Large desktop */
@media (min-width: 1440px) {
  .container {
    padding: 48px;
  }
}
```

---

## 7. Evaluation Matrix

Use this matrix to evaluate any design:

| Principle | Pass Criteria | How to Test |
| :--- | :--- | :--- |
| **Clarity** | Can a first-time user understand the purpose of the page in 5 seconds? | 5-second test with new users |
| **Efficiency** | Is the most frequent task accessible within 1-2 clicks? | User flow analysis, click counting |
| **Consistency** | Do similar actions use the same icons, colors, and patterns throughout? | Visual audit across all screens |
| **Feedback** | Does every action have immediate, intermediate, or final feedback? | Interaction testing |
| **Accessibility** | Does it meet WCAG 2.1 Level AA? | Automated tools (axe, Lighthouse) + manual testing |
| **Hierarchy** | Is the visual hierarchy clear and does it guide users to primary actions? | Squint test, heat map analysis |
| **Recovery** | Is there an obvious way to go back, undo, or cancel an action? | Error scenario testing |
| **Performance** | Do interactions feel instantaneous (<100ms) or provide loading feedback? | Performance monitoring, Lighthouse |
| **Mobile-First** | Does the design work on the smallest supported screen size? | Responsive testing, real device testing |
| **Delight** | Are there thoughtful micro-interactions that enhance the experience? | User satisfaction surveys, qualitative feedback |

---

## 8. Common UI Patterns & When to Use Them

### 8.1 Modals
**When to use:**
- Require user decision before proceeding
- Display critical information
- Capture focused input (e.g., login form)

**When NOT to use:**
- For non-critical information (use toast instead)
- For complex multi-step processes (use dedicated page)
- On mobile (consider bottom sheet instead)

**Best Practices:**
- Include close button (X) in top-right
- Allow `Esc` key to close
- Dim background with overlay
- Trap focus within modal
- Return focus to trigger element on close

---

### 8.2 Tooltips
**When to use:**
- Provide additional context for icons
- Explain unfamiliar terminology
- Show keyboard shortcuts

**When NOT to use:**
- For critical information (should be visible by default)
- On mobile (no hover state)
- For long text (use popover instead)

**Best Practices:**
- Appear on hover after 500ms delay
- Disappear on mouse leave
- Position intelligently (don't cover content)
- Keep text concise (< 10 words)

---

### 8.3 Dropdowns
**When to use:**
- 5-15 options
- Options are familiar to users
- Space is limited

**When NOT to use:**
- < 5 options (use radio buttons)
- > 15 options (use searchable select)
- Options need explanation (use radio with descriptions)

**Best Practices:**
- Show 5-7 options before scrolling
- Highlight selected option
- Support keyboard navigation
- Consider autocomplete for long lists

---

### 8.4 Tabs
**When to use:**
- Related content sections
- Settings panels
- Dashboard views

**When NOT to use:**
- Sequential processes (use stepper instead)
- Unrelated content
- > 7 tabs (consider different pattern)

**Best Practices:**
- Active tab clearly indicated
- Content loads without page refresh
- Use `role="tablist"` for accessibility
- Support arrow key navigation

---

### 8.5 Cards
**When to use:**
- Displaying collections of items
- Grouping related information
- Scannable content

**Best Practices:**
- Consistent sizing within a collection
- Clear visual hierarchy within card
- Hover state for interactive cards
- Adequate padding and whitespace

---

## 9. Performance & Perceived Performance

Users perceive speed differently than actual speed. Optimize for perception.

### 9.1 Performance Budgets

| Metric | Target | Critical Threshold |
|--------|--------|-------------------|
| First Contentful Paint (FCP) | < 1.8s | < 3s |
| Largest Contentful Paint (LCP) | < 2.5s | < 4s |
| Time to Interactive (TTI) | < 3.8s | < 7.3s |
| Cumulative Layout Shift (CLS) | < 0.1 | < 0.25 |
| First Input Delay (FID) | < 100ms | < 300ms |

### 9.2 Perceived Performance Techniques

**1. Skeleton Screens**
Show layout structure while content loads

**2. Optimistic UI**
Update UI immediately, rollback if server rejects

**3. Progressive Loading**
Load critical content first, defer non-critical

**4. Lazy Loading**
Load images/components as they enter viewport

**5. Prefetching**
Preload likely next pages on hover

---

## 10. Dark Mode Considerations

**Color Adjustments:**
- Don't just invert colors
- Use true black (#000) sparingly (causes eye strain)
- Prefer dark grays (#121212, #1E1E1E)
- Reduce saturation of bright colors
- Increase contrast for text

**Example:**
```css
:root {
  --bg-primary: #FFFFFF;
  --text-primary: rgba(0, 0, 0, 0.9);
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg-primary: #1E1E1E;
    --text-primary: rgba(255, 255, 255, 0.9);
  }
}
```

---

## 11. Final Checklist

Before shipping any UI, verify:

- [ ] Primary action is obvious and prominent
- [ ] All interactive elements have hover/focus/active states
- [ ] Loading states for all async operations
- [ ] Error states with helpful messages
- [ ] Empty states with guidance
- [ ] Success confirmations for important actions
- [ ] Keyboard navigation works
- [ ] Screen reader accessible (semantic HTML + ARIA)
- [ ] Color contrast meets WCAG AA
- [ ] Touch targets ≥ 44×44px
- [ ] Responsive on all breakpoints
- [ ] Fast loading (< 3s LCP)
- [ ] No layout shift (CLS < 0.1)
- [ ] Respects `prefers-reduced-motion`
- [ ] Works in dark mode (if supported)
- [ ] Tested in target browsers
- [ ] Consistent with design system

---

## Resources & Tools

**Accessibility:**
- [WAVE](https://wave.webaim.org/) - Accessibility checker
- [axe DevTools](https://www.deque.com/axe/devtools/) - Browser extension
- [Contrast Checker](https://webaim.org/resources/contrastchecker/)

**Performance:**
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) - Performance audit
- [WebPageTest](https://www.webpagetest.org/) - Detailed performance analysis

**Design:**
- [Laws of UX](https://lawsofux.com/) - Interactive reference
- [Refactoring UI](https://www.refactoringui.com/) - Practical design tips
- [Material Design](https://material.io/) - Comprehensive design system

**Color:**
- [Coolors](https://coolors.co/) - Color palette generator
- [Color Blindness Simulator](https://www.color-blindness.com/coblis-color-blindness-simulator/)

---

**Remember:** Great UX is invisible. Users should accomplish their goals effortlessly, without thinking about the interface itself.


---
---

# PART II: PRO MAX DESIGN INTELLIGENCE

This section provides AI-powered design intelligence with searchable databases and industry-specific reasoning rules.

---

## 11. Design System Generation

### How It Works

The Pro Max skill uses a multi-domain search engine with 100 industry-specific reasoning rules to automatically generate complete design systems.

```
┌─────────────────────────────────────────────────────────────────┐
│  1. USER REQUEST                                                │
│     "Build a landing page for my beauty spa"                    │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  2. MULTI-DOMAIN SEARCH (5 parallel searches)                   │
│     • Product type matching (100 categories)                    │
│     • Style recommendations (67 styles)                         │
│     • Color palette selection (96 palettes)                     │
│     • Landing page patterns (24 patterns)                       │
│     • Typography pairing (57 font combinations)                 │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  3. REASONING ENGINE                                            │
│     • Match product → UI category rules                         │
│     • Apply style priorities (BM25 ranking)                     │
│     • Filter anti-patterns for industry                         │
│     • Process decision rules (JSON conditions)                  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│  4. COMPLETE DESIGN SYSTEM OUTPUT                               │
│     Pattern + Style + Colors + Typography + Effects             │
│     + Anti-patterns to avoid + Pre-delivery checklist           │
└─────────────────────────────────────────────────────────────────┘
```

### Example Output

```
+----------------------------------------------------------------------------------------+
|  TARGET: Serenity Spa - RECOMMENDED DESIGN SYSTEM                                      |
+----------------------------------------------------------------------------------------+
|                                                                                        |
|  PATTERN: Hero-Centric + Social Proof                                                  |
|     Conversion: Emotion-driven with trust elements                                     |
|     CTA: Above fold, repeated after testimonials                                       |
|     Sections:                                                                          |
|       1. Hero                                                                          |
|       2. Services                                                                      |
|       3. Testimonials                                                                  |
|       4. Booking                                                                       |
|       5. Contact                                                                       |
|                                                                                        |
|  STYLE: Soft UI Evolution                                                              |
|     Keywords: Soft shadows, subtle depth, calming, premium feel, organic shapes        |
|     Best For: Wellness, beauty, lifestyle brands, premium services                     |
|     Performance: Excellent | Accessibility: WCAG AA                                    |
|                                                                                        |
|  COLORS:                                                                               |
|     Primary:    #E8B4B8 (Soft Pink)                                                    |
|     Secondary:  #A8D5BA (Sage Green)                                                   |
|     CTA:        #D4AF37 (Gold)                                                         |
|     Background: #FFF5F5 (Warm White)                                                   |
|     Text:       #2D3436 (Charcoal)                                                     |
|     Notes: Calming palette with gold accents for luxury feel                           |
|                                                                                        |
|  TYPOGRAPHY: Cormorant Garamond / Montserrat                                           |
|     Mood: Elegant, calming, sophisticated                                              |
|     Best For: Luxury brands, wellness, beauty, editorial                               |
|     Google Fonts: https://fonts.google.com/share?selection.family=...                  |
|                                                                                        |
|  KEY EFFECTS:                                                                          |
|     Soft shadows + Smooth transitions (200-300ms) + Gentle hover states                |
|                                                                                        |
|  AVOID (Anti-patterns):                                                                |
|     Bright neon colors + Harsh animations + Dark mode + AI purple/pink gradients       |
|                                                                                        |
|  PRE-DELIVERY CHECKLIST:                                                               |
|     [ ] No emojis as icons (use SVG: Heroicons/Lucide)                                 |
|     [ ] cursor-pointer on all clickable elements                                       |
|     [ ] Hover states with smooth transitions (150-300ms)                               |
|     [ ] Light mode: text contrast 4.5:1 minimum                                        |
|     [ ] Focus states visible for keyboard nav                                          |
|     [ ] prefers-reduced-motion respected                                               |
|     [ ] Responsive: 375px, 768px, 1024px, 1440px                                       |
|                                                                                        |
+----------------------------------------------------------------------------------------+
```

### Usage Commands

```bash
# Basic design system generation
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "product-type keywords" --design-system

# With project name
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "fintech banking app" --design-system -p "BankApp"

# Markdown format output
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "ecommerce fashion" --design-system -f markdown

# Persist to design-system/ folder
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "saas dashboard" --design-system --persist -p "MyApp"

# With page-specific overrides
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "saas dashboard" --design-system --persist -p "MyApp" --page "analytics"
```

---

## 12. Industry-Specific Reasoning Rules (100 Categories)

The skill includes 100 industry-specific rules that automatically determine the best design system based on product type.

### Categories by Industry

#### Tech & SaaS (25 rules)
- SaaS (generic)
- Micro SaaS
- B2B Enterprise SaaS
- Developer Tools
- AI/Chatbot Platform
- API Documentation
- Monitoring/Analytics Dashboard
- Project Management
- CRM
- HR/Recruiting SaaS
- And 15 more...

#### Finance (15 rules)
- Fintech (generic)
- Banking
- Crypto/Blockchain
- Insurance
- Trading Dashboard
- Payment Processing
- Personal Finance
- Investment Platform
- Lending Platform
- And 6 more...

#### Healthcare (12 rules)
- Medical Clinic
- Pharmacy
- Dental
- Veterinary
- Mental Health
- Telemedicine
- Health Records
- Fitness Tracker
- And 4 more...

#### E-commerce (15 rules)
- E-commerce (generic)
- Luxury E-commerce
- Marketplace
- Subscription Box
- Dropshipping
- B2B E-commerce
- Fashion
- Electronics
- Food Delivery
- And 6 more...

#### Services (18 rules)
- Beauty/Spa
- Restaurant
- Hotel/Hospitality
- Real Estate
- Legal
- Consulting
- Agency
- Photography
- Event Planning
- And 9 more...

#### Creative & Media (10 rules)
- Portfolio (Designer/Developer)
- Creative Agency
- Photography
- Music Streaming
- Video Platform
- Gaming
- Podcast
- And 3 more...

#### Emerging Tech (5 rules)
- Web3/NFT
- Spatial Computing (AR/VR)
- Quantum Computing UI
- Autonomous Systems
- Robotics Interface

### Rule Structure

Each reasoning rule defines:

```json
{
  "product_type": "Beauty/Spa Service",
  "recommended_pattern": "Hero-Centric + Social Proof",
  "style_priority": ["Soft UI Evolution", "Claymorphism", "Minimalism"],
  "color_mood": "calming, elegant, natural",
  "typography_mood": "elegant, calming, sophisticated",
  "key_effects": "Soft shadows, smooth transitions, gentle hovers",
  "anti_patterns": "Bright neon, harsh animations, dark mode",
  "conversion_notes": "Emotion-driven, trust elements, booking focus"
}
```

---

## 13. UI Style Database (67 Styles)

### General Styles (49)

#### Modern & Clean

**1. Minimalism & Swiss Style**
- Keywords: Clean, simple, white space, geometric, grid-based
- Colors: Monochromatic, Black/White, neutral accents
- Best For: Enterprise apps, dashboards, documentation, SaaS
- Performance: ⚡ Excellent | Accessibility: ✓ WCAG AAA
- Framework: Tailwind 10/10, Bootstrap 9/10

**2. Flat Design**
- Keywords: 2D, bold colors, no shadows, clean lines
- Colors: 4-6 solid bright colors, high saturation
- Best For: Web apps, mobile apps, MVPs, dashboards
- Performance: ⚡ Excellent | Accessibility: ✓ WCAG AAA

**3. Soft UI Evolution**
- Keywords: Evolved soft UI, better contrast, subtle depth
- Colors: Improved contrast pastels, modern accents
- Best For: Modern enterprise, SaaS, business tools
- Performance: ⚡ Excellent | Accessibility: ✓ WCAG AA+

#### Premium & Luxury

**4. Glassmorphism**
- Keywords: Frosted glass, transparent, blurred background
- Colors: Translucent white (10-30% opacity), vibrant backgrounds
- Effects: Backdrop blur (10-20px), subtle borders
- Best For: Modern SaaS, financial dashboards, overlays
- Performance: ⚠ Good | Accessibility: ⚠ Ensure 4.5:1 contrast

**5. Liquid Glass**
- Keywords: Flowing glass, morphing, chromatic aberration
- Colors: Vibrant iridescent, translucent base
- Effects: SVG morphing (400-600ms), dynamic blur
- Best For: Premium SaaS, high-end e-commerce, luxury
- Performance: ⚠ Moderate-Poor | Accessibility: ⚠ Text contrast

#### Playful & Creative

**6. Claymorphism**
- Keywords: Soft 3D, chunky, toy-like, bubbly
- Colors: Pastels (peach, baby blue, mint, lilac)
- Effects: Double shadows, soft press (200ms), rounded (16-24px)
- Best For: Educational apps, children's apps, creative tools
- Performance: ⚡ Good | Accessibility: ⚠ Ensure 4.5:1

**7. Neumorphism**
- Keywords: Soft UI, embossed, convex/concave, subtle depth
- Colors: Light pastels, monochromatic
- Effects: Soft box-shadow (multiple layers), inner shadows
- Best For: Health/wellness, meditation, minimal UIs
- Performance: ⚡ Good | Accessibility: ⚠ Low contrast

**8. Vibrant & Block-based**
- Keywords: Bold, energetic, geometric, high contrast
- Colors: Neon green, electric purple, vivid pink, bright cyan
- Effects: Large gaps (48px+), animated patterns, scroll-snap
- Best For: Startups, creative agencies, gaming, youth brands
- Performance: ⚡ Good | Accessibility: ◐ Ensure WCAG

#### Artistic & Experimental

**9. Brutalism**
- Keywords: Raw, stark, anti-design, asymmetric
- Colors: Primary only (red, blue, yellow, black, white)
- Effects: No transitions (instant), sharp corners (0px)
- Best For: Design portfolios, artistic projects, tech blogs
- Performance: ⚡ Excellent | Accessibility: ✓ WCAG AAA

**10. Retro-Futurism**
- Keywords: 80s aesthetic, neon glow, cyberpunk, synthwave
- Colors: Neon blue, hot pink, cyan, deep black, purple
- Effects: CRT scanlines, neon glow, glitch effects
- Best For: Gaming, entertainment, music platforms
- Performance: ⚠ Moderate | Accessibility: ⚠ High contrast

**11. Vaporwave**
- Keywords: Pink/purple gradients, Roman busts, retro 90s
- Colors: Pink #FF71CE, purple #01CDFE, #B967FF
- Effects: VHS distortion, pastel gradients, geometric shapes
- Best For: Music platforms, gaming, creative portfolios
- Performance: ⚠ Moderate

#### Immersive & 3D

**12. 3D & Hyperrealism**
- Keywords: Depth, realistic textures, 3D models, spatial
- Colors: Deep navy, forest green, burgundy, gold, silver
- Effects: WebGL/Three.js, realistic shadows, parallax (3-5 layers)
- Best For: Gaming, product showcase, VR/AR
- Performance: ❌ Poor | Accessibility: ⚠ Not accessible

**13. Spatial UI (VisionOS)**
- Keywords: Depth layers, spatial computing, 3D cards
- Colors: Translucent panels, depth-aware
- Effects: Z-axis depth, spatial shadows, hand tracking
- Best For: Spatial computing apps, VR/AR
- Performance: ⚠ Moderate

#### Dark & Night Modes

**14. Dark Mode (OLED)**
- Keywords: Dark theme, deep black, eye-friendly, power efficient
- Colors: Deep black #000000, dark grey #121212, neon accents
- Effects: Minimal glow, dark-to-light transitions
- Best For: Night-mode apps, coding platforms, entertainment
- Performance: ⚡ Excellent | Accessibility: ✓ WCAG AAA

#### Modern Trends

**15. Aurora UI**
- Keywords: Vibrant gradients, mesh gradients, Northern Lights
- Colors: Complementary pairs (blue-orange, purple-yellow)
- Effects: Flowing gradients (8-12s loops), iridescent
- Best For: Modern SaaS, creative agencies, hero sections
- Performance: ⚠ Good | Accessibility: ⚠ Text contrast

**16. Bento Box Grid**
- Keywords: Grid-based cards, varied sizes, iOS-like
- Colors: Clean with accent colors
- Effects: Grid layouts, card-based
- Best For: Dashboards, product pages, portfolios
- Performance: ⚡ Excellent

**17. Neubrutalism**
- Keywords: Harsh shadows, bold borders, vibrant colors
- Colors: Black borders, vibrant fills, high contrast
- Effects: Heavy shadows, sharp corners
- Best For: Gen Z brands, startups, design tools
- Performance: ⚡ Excellent

**18. AI-Native UI**
- Keywords: Chat interfaces, streaming text, AI patterns
- Colors: Neutral with smart accent colors
- Effects: Typing animations, streaming content
- Best For: AI products, chatbots, copilots
- Performance: ⚡ Good

**19. Y2K Aesthetic**
- Keywords: Chrome effects, butterfly clips, gel text
- Colors: Silver, blue, pink, holographic
- Effects: Metallic gradients, glossy surfaces
- Best For: Fashion brands, music, Gen Z targeting
- Performance: ⚠ Moderate

**20. Organic Biophilic**
- Keywords: Nature-inspired, flowing shapes, earth tones
- Colors: Forest green, terracotta, sand, sage
- Effects: Organic shapes, nature textures
- Best For: Wellness apps, sustainability brands
- Performance: ⚡ Good

### Landing Page Styles (8)

**1. Hero-Centric Design**
- Best For: Products with strong visual identity
- Structure: Large hero, single CTA, minimal content
- Conversion: Visual impact first

**2. Conversion-Optimized**
- Best For: Lead generation, sales pages
- Structure: Clear value prop, multiple CTAs, trust signals
- Conversion: Maximize form submissions

**3. Feature-Rich Showcase**
- Best For: SaaS, complex products
- Structure: Feature grid, benefits, demos, pricing
- Conversion: Education + conversion

**4. Social Proof-Focused**
- Best For: Services, B2C products
- Structure: Testimonials, case studies, reviews
- Conversion: Trust-based

**5. Interactive Product Demo**
- Best For: Software, tools
- Structure: Live demo, interactive elements
- Conversion: Try before buy

**6. Storytelling-Driven**
- Best For: Brands, agencies, nonprofits
- Structure: Narrative flow, emotional journey
- Conversion: Emotional connection

**7. Minimal & Direct**
- Best For: Simple products, apps
- Structure: One message, one CTA, minimal sections
- Conversion: Clarity over features

**8. Trust & Authority**
- Best For: B2B, enterprise, consulting
- Structure: Credentials, case studies, expertise
- Conversion: Professional credibility

### BI/Analytics Dashboard Styles (10)

**1. Data-Dense Dashboard**
- Best For: Complex data analysis
- Layout: Multi-panel, high information density
- Charts: Multiple types, interconnected

**2. Executive Dashboard**
- Best For: C-suite summaries
- Layout: KPI cards, trend indicators, clean
- Charts: Simplified, high-level

**3. Real-Time Monitoring**
- Best For: Operations, DevOps
- Layout: Live updates, alerts, status
- Charts: Time series, gauges

**4. Drill-Down Analytics**
- Best For: Detailed exploration
- Layout: Hierarchical, progressive disclosure
- Charts: Interactive, filterable

[... And 6 more dashboard styles]

---

## 14. Color Palette Database (96 Palettes)

### By Industry

#### SaaS & Tech (15 palettes)
- SaaS Generic: Blue #0066FF, Grey #64748B
- Developer Tools: Dark #1E293B, Green #10B981
- API Platform: Purple #7C3AED, Cyan #06B6D4
- And 12 more...

#### E-commerce (12 palettes)
- E-commerce Generic: Orange #FF6B35, Navy #2C3E50
- Luxury: Black #000000, Gold #D4AF37
- Fashion: Pink #FF1493, Black #1A1A1A
- And 9 more...

#### Healthcare (10 palettes)
- Medical: Blue #0052CC, Green #00875A
- Wellness: Sage #A8D5BA, Soft Pink #E8B4B8
- Pharmacy: Green #22C55E, White #FFFFFF
- And 7 more...

#### Finance (12 palettes)
- Fintech: Blue #1E40AF, Green #059669
- Banking: Navy #1E3A8A, Gold #F59E0B
- Crypto: Purple #8B5CF6, Cyan #06B6D4
- And 9 more...

#### Services (20 palettes)
- Beauty/Spa: Soft Pink #E8B4B8, Sage #A8D5BA
- Restaurant: Red #DC2626, Warm #78350F
- Real Estate: Blue #1E40AF, Gold #D97706
- And 17 more...

[... Full database with hex codes, use cases, and mood descriptors]

---

## 15. Typography Database (57 Font Pairings)

### Elegant & Sophisticated

**1. Playfair Display + Inter**
- Heading: Playfair Display (serif)
- Body: Inter (sans-serif)
- Mood: Elegant, editorial, premium
- Best For: Luxury brands, editorial, beauty
- Google Fonts: https://fonts.google.com/share?selection.family=...

**2. Cormorant Garamond + Montserrat**
- Heading: Cormorant Garamond (serif)
- Body: Montserrat (sans-serif)
- Mood: Elegant, calming, sophisticated
- Best For: Wellness, beauty, lifestyle

[... 55 more typography pairings with complete details]

---

## 16. Landing Page Patterns (24 Patterns)

### Pattern Structure

Each pattern defines:
- Section order
- CTA placement strategy
- Conversion optimization approach
- Best use cases

**Example: Hero-Centric + Social Proof**

```
Sections:
1. Hero (Full viewport)
   - Value proposition
   - Single primary CTA above fold
   - Supporting visual/video

2. Benefits/Features (3-5 cards)
   - Icon + Title + Description
   - Scannable layout

3. Social Proof
   - Customer testimonials (3-5)
   - Logo wall if B2B
   - Repeat CTA

4. How It Works (3-4 steps)
   - Process visualization
   - Build confidence

5. Pricing/CTA
   - Clear pricing or final CTA
   - FAQ if needed

6. Footer
   - Links, legal, social
```

[... 23 more landing page patterns with full structural details]

---

## 17. Chart & Visualization Types (25 Types)

### By Use Case

#### Comparison Charts
1. **Bar Chart** - Compare categories
2. **Column Chart** - Time-based comparison
3. **Grouped Bar** - Multi-series comparison
4. **Radar/Spider Chart** - Multi-dimensional comparison

#### Trend Analysis
5. **Line Chart** - Show trends over time
6. **Area Chart** - Cumulative trends
7. **Sparklines** - Inline mini-trends

#### Part-to-Whole
8. **Pie Chart** - Simple proportions (max 5 slices)
9. **Donut Chart** - Proportions with center label
10. **Treemap** - Hierarchical proportions
11. **Stacked Bar** - Categorical proportions over time

#### Distribution
12. **Histogram** - Frequency distribution
13. **Box Plot** - Statistical distribution
14. **Scatter Plot** - Correlation and patterns

#### Flow & Process
15. **Sankey Diagram** - Flow between states
16. **Funnel Chart** - Process drop-off
17. **Gantt Chart** - Project timelines

[... Full database with recommendations and library suggestions]

---

## 18. Stack-Specific Guidelines (13 Stacks)

### Web Frameworks

**HTML + Tailwind (DEFAULT)**
- Focus: Tailwind utilities, responsive design, accessibility
- Key Guidelines:
  - Use semantic HTML5 elements
  - Responsive classes: `sm:`, `md:`, `lg:`, `xl:`, `2xl:`
  - Accessibility: ARIA labels, focus states
  - Performance: Purge unused CSS

**React**
- Focus: State management, hooks, performance patterns
- Key Guidelines:
  - Use functional components and hooks
  - Memoization: `React.memo`, `useMemo`, `useCallback`
  - Avoid prop drilling (use Context or state management)
  - Code splitting with `React.lazy`

**Next.js**
- Focus: SSR, routing, images, API routes
- Key Guidelines:
  - Use Image component for optimization
  - Implement ISR for static generation
  - API routes for backend logic
  - App Router patterns (Next.js 13+)

**Vue 3**
- Focus: Composition API, Pinia, Vue Router
- Key Guidelines:
  - Use Composition API for complex components
  - Reactive state with `ref` and `reactive`
  - Pinia for state management
  - Teleport for portals

**Svelte/SvelteKit**
- Focus: Runes, stores, reactive declarations
- Key Guidelines:
  - Use Svelte 5 runes ($state, $derived, $effect)
  - Stores for shared state
  - SvelteKit for full-stack apps

### Mobile Frameworks

**SwiftUI**
- Focus: Declarative UI, state, navigation
- Key Guidelines:
  - @State for local state, @Binding for two-way binding
  - NavigationStack for navigation
  - SF Symbols for icons
  - AsyncImage for remote images

**React Native**
- Focus: Components, navigation, performance
- Key Guidelines:
  - FlatList for long lists (virtualized)
  - React Navigation for routing
  - Fast Refresh for development
  - Hermes engine for performance

**Flutter**
- Focus: Widgets, state, Material/Cupertino
- Key Guidelines:
  - StatelessWidget vs StatefulWidget
  - Provider/Riverpod for state
  - Material Design widgets
  - CustomPainter for custom graphics

**Jetpack Compose**
- Focus: Composables, state hoisting, Material 3
- Key Guidelines:
  - remember for state, rememberSaveable for persistence
  - State hoisting pattern
  - Material 3 components
  - LazyColumn for lists

### UI Libraries

**shadcn/ui**
- Focus: Radix primitives, Tailwind, theming
- Key Guidelines:
  - Copy components, don't npm install
  - Customize via Tailwind classes
  - Accessible by default (Radix)

---

## 19. UX Guidelines & Anti-Patterns (99 Rules)

### Critical Accessibility Rules (15)

1. **color-contrast** - Minimum 4.5:1 for normal text, 3:1 for large text
2. **focus-states** - Visible focus rings on all interactive elements
3. **alt-text** - Descriptive alt text for all meaningful images
4. **aria-labels** - aria-label or aria-labelledby for icon-only buttons
5. **keyboard-nav** - Full keyboard navigation, Tab order matches visual
6. **form-labels** - Always use <label> with for attribute
7. **semantic-html** - Use semantic elements (<nav>, <main>, <article>)
8. **heading-hierarchy** - Logical heading structure (h1 → h2 → h3)
9. **skip-links** - "Skip to main content" link for keyboard users
10. **screen-reader** - Test with screen readers (NVDA, JAWS, VoiceOver)
11. **color-only** - Don't use color as the only visual indicator
12. **reduced-motion** - Respect prefers-reduced-motion
13. **lang-attribute** - Set lang attribute on <html>
14. **landmarks** - Use ARIA landmarks for page regions
15. **link-purpose** - Link text describes destination

### Touch & Interaction Rules (12)

16. **touch-target-size** - Minimum 44×44px for touch targets (WCAG 2.1)
17. **cursor-pointer** - cursor: pointer on all clickable elements
18. **hover-vs-tap** - Don't rely on hover for mobile interactions
19. **loading-states** - Show loading indicators for async operations
20. **button-disabled** - Disable buttons during async operations
21. **error-feedback** - Show errors inline near the problem field
22. **success-feedback** - Confirm successful actions
23. **debounce-input** - Debounce search/filter inputs (300-500ms)
24. **optimistic-ui** - Update UI immediately, rollback if fails
25. **gesture-feedback** - Visual feedback for touch gestures
26. **press-animation** - Subtle press animation (transform: scale(0.98))
27. **double-tap-zoom** - Prevent accidental double-tap zoom

### Performance Rules (10)

28. **image-optimization** - Use WebP, srcset, lazy loading
29. **font-loading** - Optimize font loading (font-display: swap)
30. **code-splitting** - Split large bundles
31. **lazy-load** - Lazy load below-the-fold content
32. **content-jumping** - Reserve space for async content (CLS)
33. **cdn-usage** - Serve static assets from CDN
34. **compression** - Enable gzip/brotli compression
35. **caching** - Set appropriate cache headers
36. **prefetch** - Prefetch likely next pages
37. **web-vitals** - Monitor Core Web Vitals (LCP, FID, CLS)

### Layout & Responsive Rules (15)

38. **viewport-meta** - width=device-width, initial-scale=1
39. **readable-font-size** - Minimum 16px body text on mobile
40. **horizontal-scroll** - Prevent horizontal scroll
41. **z-index-management** - Define z-index scale (10, 20, 30, 50, 100)
42. **max-width** - Limit content width (65-75ch for reading)
43. **spacing-scale** - Use 8px base spacing scale
44. **responsive-images** - srcset for different screen densities
45. **mobile-first** - Write mobile CSS first, desktop via min-width
46. **grid-fallbacks** - Fallbacks for older browsers
47. **portrait-landscape** - Test both orientations
48. **safe-area** - Respect safe areas (notches, home indicator)
49. **sticky-headers** - Account for fixed header height
50. **overflow-handling** - Handle long text (word-wrap, ellipsis)
51. **table-responsive** - Horizontal scroll or card layout on mobile
52. **form-mobile** - Large inputs, proper keyboard types

### Animation Rules (8)

53. **duration-timing** - 150-300ms for micro-interactions
54. **transform-performance** - Use transform/opacity (GPU-accelerated)
55. **avoid-layout-thrashing** - Batch DOM reads/writes
56. **reduced-motion** - @media (prefers-reduced-motion: reduce)
57. **animation-purpose** - Animations should communicate, not decorate
58. **loading-animations** - Skeleton screens > spinners
59. **page-transitions** - Smooth page transitions (150-300ms)
60. **scroll-animations** - Intersection Observer for scroll effects

### Typography & Content Rules (10)

61. **line-height** - 1.5-1.75 for body text
62. **line-length** - 50-75 characters per line (desktop)
63. **font-pairing** - Max 2-3 font families
64. **type-scale** - Consistent font size scale (1.25 or 1.33 ratio)
65. **text-hierarchy** - Clear visual hierarchy via size/weight
66. **link-styling** - Links clearly differentiated (underline or color)
67. **paragraph-spacing** - Space between paragraphs (1em)
68. **orphans-widows** - Prevent single words on last line
69. **text-contrast** - Sufficient contrast on all backgrounds
70. **copy-clarity** - Clear, concise microcopy

### Icon & Visual Rules (8)

71. **no-emoji-icons** - Use SVG icons (Heroicons, Lucide, Simple Icons)
72. **icon-consistency** - Consistent icon set (not mixed styles)
73. **icon-size** - 24×24px standard, 16×16px small, 32×32px large
74. **icon-labels** - Always label icons (visible or aria-label)
75. **logo-correct** - Verify brand logos from official sources
76. **icon-alignment** - Align icons with text baseline
77. **decorative-icons** - aria-hidden="true" for decorative icons
78. **svg-optimization** - Optimize SVGs (SVGO)

### Form Rules (12)

79. **label-required** - Always use <label> elements
80. **field-validation** - Inline validation on blur
81. **error-messages** - Specific, helpful error messages
82. **required-indicator** - Mark required fields (*, aria-required)
83. **input-types** - Correct input types (email, tel, number, date)
84. **autocomplete** - Enable autocomplete attributes
85. **password-visibility** - Toggle password visibility
86. **field-grouping** - Group related fields (fieldset/legend)
87. **focus-first-error** - Focus first error field on submit
88. **multi-step-progress** - Show progress in multi-step forms
89. **save-progress** - Allow saving incomplete forms
90. **confirmation** - Confirm before destructive actions

### Navigation & Information Architecture (9)

91. **breadcrumbs** - Show breadcrumbs for deep hierarchies
92. **active-state** - Clearly indicate current page in navigation
93. **burger-menu** - Reserve hamburger menu for mobile/secondary nav
94. **footer-links** - Logical footer organization
95. **404-helpful** - Helpful 404 pages with navigation
96. **search-prominent** - Make search discoverable
97. **back-button** - Browser back button works correctly
98. **external-links** - Indicate external links (icon or text)
99. **sitemap** - Provide sitemap for large sites

---

## 20. Search Command Reference

### Prerequisites

```bash
# Check Python version (3.x required)
python3 --version

# If not installed:
# macOS: brew install python3
# Ubuntu: sudo apt update && sudo apt install python3
# Windows: winget install Python.Python.3.12
```

### Design System Generation (Primary Use Case)

```bash
# Basic syntax
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "<keywords>" --design-system [options]

# Common options
-p "Project Name"    # Set project name for output
-f markdown          # Output format (default: ascii box)
--persist            # Save to design-system/MASTER.md
--page "page-name"   # Create page-specific override

# Examples
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "fintech banking app" --design-system -p "BankApp"

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "beauty spa wellness" --design-system --persist -p "Serenity"

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "ecommerce fashion" --design-system --persist --page "checkout"
```

### Domain-Specific Searches

```bash
# Syntax
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "<keywords>" --domain <domain> [-n <max_results>]

# Available domains:
# product, style, typography, color, landing, chart, ux, react, web, prompt

# Examples
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "glassmorphism modern" --domain style -n 5

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "elegant luxury serif" --domain typography

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "fintech banking" --domain color

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "animation accessibility" --domain ux
```

### Stack-Specific Searches

```bash
# Syntax
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "<keywords>" --stack <stack>

# Available stacks:
# html-tailwind, react, nextjs, vue, nuxtjs, svelte, astro,
# swiftui, react-native, flutter, shadcn, jetpack-compose

# Examples
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "responsive layout" --stack html-tailwind

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "state management" --stack react

python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "navigation" --stack swiftui
```

### Workflow Example

```bash
# Step 1: Generate design system
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "saas analytics dashboard" --design-system -p "Analytics Pro"

# Step 2: Get additional typography options (if needed)
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "professional modern" --domain typography -n 3

# Step 3: Get UX guidelines for specific features
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "animation chart accessibility" --domain ux

# Step 4: Get stack-specific guidance
python3 ~/.claude/skills/ux-ui-principles-pro-max/search.py \
  "chart performance state" --stack react
```

---

## 21. Professional UI Checklist

### Before Delivery

#### Icons & Visual Elements
- [ ] No emojis used as icons (use SVG: Heroicons, Lucide, Simple Icons)
- [ ] All icons from consistent set (same style)
- [ ] Brand logos verified from official sources (Simple Icons)
- [ ] Icon size consistent (24×24px standard)
- [ ] Decorative icons have aria-hidden="true"
- [ ] Functional icons have text labels or aria-label

#### Interaction & Cursor
- [ ] All clickable elements have cursor-pointer
- [ ] Hover states provide clear visual feedback
- [ ] Transitions are smooth (150-300ms)
- [ ] Focus states visible for keyboard navigation
- [ ] Active/pressed states for buttons
- [ ] Disabled states clearly differentiated

#### Light/Dark Mode Contrast
- [ ] Light mode text contrast ≥ 4.5:1
- [ ] Dark mode text contrast ≥ 4.5:1
- [ ] Glass/transparent elements visible in light mode
- [ ] Borders visible in both modes
- [ ] Test both modes before delivery
- [ ] prefers-color-scheme respected

#### Layout & Spacing
- [ ] Floating elements have proper spacing from edges
- [ ] No content hidden behind fixed navbars/headers
- [ ] Consistent max-width for content containers
- [ ] 8px base spacing scale used consistently
- [ ] Whitespace creates clear visual hierarchy

#### Responsive Design
- [ ] Works at 375px (mobile)
- [ ] Works at 768px (tablet)
- [ ] Works at 1024px (laptop)
- [ ] Works at 1440px+ (desktop)
- [ ] No horizontal scroll on any breakpoint
- [ ] Touch targets ≥ 44×44px on mobile

#### Accessibility (WCAG 2.1 Level AA)
- [ ] All images have alt text
- [ ] Form inputs have associated labels
- [ ] Color is not the only indicator
- [ ] Keyboard navigation works (Tab, Enter, Esc)
- [ ] Focus visible on all interactive elements
- [ ] Screen reader tested (NVDA/JAWS/VoiceOver)
- [ ] Semantic HTML used (<nav>, <main>, <article>)
- [ ] Heading hierarchy logical (h1 → h2 → h3)

#### Performance
- [ ] Images optimized (WebP, srcset, lazy loading)
- [ ] Fonts optimized (font-display: swap)
- [ ] No layout shift (CLS < 0.1)
- [ ] Fast loading (LCP < 2.5s)
- [ ] Animations respect prefers-reduced-motion

#### Code Quality
- [ ] No console errors or warnings
- [ ] Valid HTML (no unclosed tags)
- [ ] Consistent naming conventions
- [ ] Comments for complex logic
- [ ] No unused CSS or JavaScript

---

## 22. Additional Resources

### Design Tools
- **Figma** - UI design and prototyping
- **Adobe XD** - UI/UX design
- **Sketch** - Mac-only UI design tool

### Accessibility Testing
- **WAVE** - https://wave.webaim.org/
- **axe DevTools** - Browser extension
- **Lighthouse** - Built into Chrome DevTools
- **Contrast Checker** - https://webaim.org/resources/contrastchecker/

### Performance Testing
- **Lighthouse** - https://developers.google.com/web/tools/lighthouse
- **WebPageTest** - https://www.webpagetest.org/
- **GTmetrix** - https://gtmetrix.com/

### Icon Libraries
- **Heroicons** - https://heroicons.com/
- **Lucide** - https://lucide.dev/
- **Simple Icons** - https://simpleicons.org/ (brand logos)
- **Phosphor Icons** - https://phosphoricons.com/
- **Feather Icons** - https://feathericons.com/

### Color Tools
- **Coolors** - https://coolors.co/ (palette generator)
- **Adobe Color** - https://color.adobe.com/
- **Paletton** - https://paletton.com/
- **Color Blindness Simulator** - https://www.color-blindness.com/coblis-color-blindness-simulator/

### Typography Tools
- **Google Fonts** - https://fonts.google.com/
- **Font Pair** - https://fontpair.co/
- **Type Scale** - https://type-scale.com/

### Learning Resources
- **Laws of UX** - https://lawsofux.com/
- **Refactoring UI** - https://www.refactoringui.com/
- **Material Design** - https://material.io/
- **Human Interface Guidelines** - https://developer.apple.com/design/human-interface-guidelines/
- **Web Content Accessibility Guidelines (WCAG)** - https://www.w3.org/WAI/WCAG21/quickref/

---

## Version History

- **v3.0 (Pro Max Integration)** - Added 100 reasoning rules, 67 UI styles, 96 color palettes, 57 typography pairings, design system generator, stack-specific guidelines
- **v2.0** - Added interaction design, evaluation matrix, common UI patterns
- **v1.0** - Initial release with Laws of UX, visual design, accessibility basics

---

**Remember:** Great UX is invisible. Users should accomplish their goals effortlessly, without thinking about the interface itself.

**This skill now combines foundational principles with AI-powered design intelligence to help you build professional, accessible, and user-centered interfaces faster.**
