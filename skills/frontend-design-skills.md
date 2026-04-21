---
name: frontend-design-skills
description: "Comprehensive technical standards for implementing high-fidelity UIs. Covers component architecture, CSS methodologies, responsiveness, accessibility compliance, animation, performance optimization, and modern development patterns."
---

# Frontend Design Skills

This skill governs the bridge between visual design (Figma, Adobe XD) and code implementation. It ensures that interfaces are not only pixel-perfect but also accessible, performant, scalable, and maintainable across diverse devices and user contexts.

---

## 1. Structural Foundation (HTML & Semantics)

### 1.1 Semantic Hierarchy
Proper HTML semantics improve accessibility, SEO, and code maintainability.

**Core Principles:**
* **Landmark Elements:** Use `<main>`, `<article>`, `<section>`, `<nav>`, `<aside>`, `<header>`, `<footer>` to define page regions.
* **Avoid Div Soup:** Every `<div>` should have a clear purpose. If a semantic element exists, use it.
* **Heading Hierarchy:** Must reflect document structure, not visual size.
  * One `<h1>` per page (primary topic)
  * Headings should not skip levels (`h2` → `h4` is invalid)
  * Use CSS to adjust visual size, not heading level

**Example:**
```html
<!-- ❌ Bad: Non-semantic structure -->
<div class="header">
  <div class="nav">...</div>
</div>
<div class="content">
  <div class="post">
    <div class="title">Article Title</div>
  </div>
</div>

<!-- ✅ Good: Semantic structure -->
<header>
  <nav aria-label="Primary navigation">...</nav>
</header>
<main>
  <article>
    <h1>Article Title</h1>
  </article>
</main>
```

### 1.2 Interactive Elements

**Button vs. Link Decision Matrix:**

| Use Case | Element | Reason |
|:---------|:--------|:-------|
| Submit form | `<button type="submit">` | Triggers action |
| Open modal | `<button>` | Changes UI state |
| Navigate to page | `<a href="/page">` | Changes URL |
| Download file | `<a href="/file.pdf" download>` | Retrieves resource |
| Toggle accordion | `<button aria-expanded="false">` | Controls visibility |

**Form Accessibility:**
```html
<!-- ✅ Explicit label association -->
<label for="email">Email Address</label>
<input type="email" id="email" name="email" required>

<!-- ✅ Wrapping label (no 'for' needed) -->
<label>
  Email Address
  <input type="email" name="email" required>
</label>

<!-- ❌ Bad: No association -->
<span>Email</span>
<input type="email" name="email">
```

### 1.3 SEO & Meta Implementation

**Essential Meta Tags:**
```html
<head>
  <!-- Primary Meta Tags -->
  <title>Page Title - Brand Name (50-60 chars)</title>
  <meta name="description" content="Compelling description (150-160 chars)">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  
  <!-- Open Graph (Facebook, LinkedIn) -->
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://example.com/page">
  <meta property="og:title" content="Page Title">
  <meta property="og:description" content="Description for social sharing">
  <meta property="og:image" content="https://example.com/og-image.jpg">
  
  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:url" content="https://example.com/page">
  <meta name="twitter:title" content="Page Title">
  <meta name="twitter:description" content="Description for Twitter">
  <meta name="twitter:image" content="https://example.com/twitter-image.jpg">
  
  <!-- Favicon -->
  <link rel="icon" type="image/svg+xml" href="/favicon.svg">
  <link rel="apple-touch-icon" href="/apple-touch-icon.png">
</head>
```

**Semantic Keyword Placement:**
* Primary keyword in `<h1>` (once)
* Secondary keywords in `<h2>` tags
* Use `<strong>` for important terms (not just bold styling)
* Use `<em>` for emphasis (not just italic styling)

---

## 2. Modern Styling Strategies

### 2.1 CSS Layout Systems

#### Flexbox (1-Dimensional Layouts)

**Best Use Cases:**
* Navigation bars
* Card content alignment
* Centering elements
* Distributing space between items

**Common Patterns:**
```css
/* Horizontal centering */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Space-between navigation */
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

/* Vertical stack with gap */
.stack {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

/* Responsive wrapping */
.card-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
```

#### CSS Grid (2-Dimensional Layouts)

**Best Use Cases:**
* Page layouts
* Complex card designs
* Magazine-style layouts
* Dashboard grids

**Common Patterns:**
```css
/* Responsive grid with auto-fit */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

/* Named grid areas (page layout) */
.page-layout {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  grid-template-columns: 250px 1fr 300px;
  grid-template-rows: auto 1fr auto;
  gap: 1rem;
  min-height: 100vh;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.aside { grid-area: aside; }
.footer { grid-area: footer; }

/* Complex card layout */
.card {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: auto 1fr auto;
  gap: 1rem;
}
```

#### Container Queries (Component-Level Responsiveness)

**Why Container Queries > Media Queries:**
* Components adapt to their container, not viewport
* True component reusability
* Better for design systems

```css
/* Define container */
.card-container {
  container-type: inline-size;
  container-name: card;
}

/* Query the container, not viewport */
.card {
  display: flex;
  flex-direction: column;
}

@container card (min-width: 400px) {
  .card {
    flex-direction: row;
  }
}

@container card (min-width: 600px) {
  .card {
    grid-template-columns: 1fr 2fr;
  }
}
```

#### Logical Properties (Internationalization)

**Physical vs. Logical Properties:**

| Physical (Avoid) | Logical (Use) | Benefit |
|:-----------------|:--------------|:--------|
| `margin-left` | `margin-inline-start` | RTL support |
| `margin-right` | `margin-inline-end` | RTL support |
| `margin-top` | `margin-block-start` | Vertical writing modes |
| `padding-bottom` | `padding-block-end` | Vertical writing modes |
| `border-left` | `border-inline-start` | RTL support |
| `width` | `inline-size` | Writing mode agnostic |
| `height` | `block-size` | Writing mode agnostic |

```css
/* ❌ Physical properties (breaks in RTL) */
.element {
  margin-left: 1rem;
  padding-right: 2rem;
  border-left: 2px solid blue;
}

/* ✅ Logical properties (works in RTL) */
.element {
  margin-inline-start: 1rem;
  padding-inline-end: 2rem;
  border-inline-start: 2px solid blue;
}
```

### 2.2 Styling Architectures

#### Tailwind CSS (Utility-First)

**Class Organization Order:**
1. **Layout:** `flex`, `grid`, `block`, `inline-block`
2. **Positioning:** `relative`, `absolute`, `fixed`, `sticky`
3. **Box Model:** `w-*`, `h-*`, `p-*`, `m-*`
4. **Typography:** `text-*`, `font-*`, `leading-*`
5. **Visual:** `bg-*`, `border-*`, `shadow-*`, `rounded-*`
6. **Interactive:** `hover:*`, `focus:*`, `active:*`, `transition-*`

**Example:**
```html
<!-- ✅ Well-organized classes -->
<button class="
  flex items-center justify-center
  w-full px-6 py-3
  text-base font-semibold text-white
  bg-blue-600 rounded-lg shadow-md
  hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2
  transition-colors duration-200
">
  Submit
</button>
```

**Component Variants with CVA:**
```typescript
// Using class-variance-authority
import { cva, type VariantProps } from "class-variance-authority";

const buttonVariants = cva(
  // Base classes
  "inline-flex items-center justify-center rounded-lg font-semibold transition-colors focus:outline-none focus:ring-2 focus:ring-offset-2",
  {
    variants: {
      variant: {
        primary: "bg-blue-600 text-white hover:bg-blue-700 focus:ring-blue-500",
        secondary: "bg-gray-200 text-gray-900 hover:bg-gray-300 focus:ring-gray-500",
        destructive: "bg-red-600 text-white hover:bg-red-700 focus:ring-red-500",
        ghost: "hover:bg-gray-100 focus:ring-gray-500",
      },
      size: {
        sm: "px-3 py-1.5 text-sm",
        md: "px-4 py-2 text-base",
        lg: "px-6 py-3 text-lg",
      },
    },
    defaultVariants: {
      variant: "primary",
      size: "md",
    },
  }
);

// Usage
<button className={buttonVariants({ variant: "primary", size: "lg" })}>
  Click me
</button>
```

**Tailwind Rules:**
* ❌ Avoid arbitrary values: `w-[13px]`, `text-[#ff0000]`
* ✅ Extend theme in `tailwind.config.js` instead
* ✅ Use `@apply` sparingly (only for repeated patterns)

#### CSS Modules / Scoped CSS

**Naming Convention (BEM-inspired):**
```css
/* Component_element--modifier */
.Card_container { }
.Card_header { }
.Card_title--large { }
.Card_body { }
.Card_footer--sticky { }
```

**Local CSS Variables:**
```css
.Card_container {
  --card-padding: 1.5rem;
  --card-radius: 0.5rem;
  --card-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  
  padding: var(--card-padding);
  border-radius: var(--card-radius);
  box-shadow: var(--card-shadow);
}

.Card_container--compact {
  --card-padding: 1rem;
}
```

#### CSS-in-JS (Styled-Components/Emotion)

**Best Practices:**
```typescript
import styled from 'styled-components';

// ✅ Separate static and dynamic styles
const Button = styled.button<{ variant: 'primary' | 'secondary' }>`
  /* Static styles */
  display: inline-flex;
  align-items: center;
  padding: 0.75rem 1.5rem;
  border-radius: 0.5rem;
  font-weight: 600;
  transition: background-color 0.2s;
  
  /* Dynamic styles based on props */
  background-color: ${props => 
    props.variant === 'primary' 
      ? props.theme.colors.primary 
      : props.theme.colors.secondary
  };
  
  &:hover {
    background-color: ${props => 
      props.variant === 'primary' 
        ? props.theme.colors.primaryHover 
        : props.theme.colors.secondaryHover
    };
  }
`;

// ✅ Theme provider integration
const theme = {
  colors: {
    primary: '#007AFF',
    primaryHover: '#0051D5',
    secondary: '#E5E5EA',
    secondaryHover: '#D1D1D6',
  },
  spacing: {
    sm: '0.5rem',
    md: '1rem',
    lg: '1.5rem',
  },
};
```

---

## 3. Component Architecture & Design Systems

### 3.1 Design Tokens (Single Source of Truth)

**Token Hierarchy:**

```css
/* 1. Global Tokens (Raw Values) */
:root {
  /* Colors - Primitives */
  --color-blue-50: #E3F2FD;
  --color-blue-100: #BBDEFB;
  --color-blue-500: #2196F3;
  --color-blue-700: #1976D2;
  --color-blue-900: #0D47A1;
  
  --color-gray-50: #FAFAFA;
  --color-gray-100: #F5F5F5;
  --color-gray-500: #9E9E9E;
  --color-gray-900: #212121;
  
  /* Spacing Scale */
  --space-1: 0.25rem;  /* 4px */
  --space-2: 0.5rem;   /* 8px */
  --space-3: 0.75rem;  /* 12px */
  --space-4: 1rem;     /* 16px */
  --space-6: 1.5rem;   /* 24px */
  --space-8: 2rem;     /* 32px */
  --space-12: 3rem;    /* 48px */
  
  /* Typography Scale */
  --font-size-xs: 0.75rem;   /* 12px */
  --font-size-sm: 0.875rem;  /* 14px */
  --font-size-base: 1rem;    /* 16px */
  --font-size-lg: 1.125rem;  /* 18px */
  --font-size-xl: 1.25rem;   /* 20px */
  --font-size-2xl: 1.5rem;   /* 24px */
  --font-size-3xl: 1.875rem; /* 30px */
  
  /* Font Weights */
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  
  /* Border Radius */
  --radius-sm: 0.25rem;  /* 4px */
  --radius-md: 0.5rem;   /* 8px */
  --radius-lg: 0.75rem;  /* 12px */
  --radius-xl: 1rem;     /* 16px */
  --radius-full: 9999px;
  
  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
}

/* 2. Semantic Tokens (Contextual Usage) */
:root {
  /* Brand Colors */
  --color-primary: var(--color-blue-500);
  --color-primary-hover: var(--color-blue-700);
  --color-primary-light: var(--color-blue-50);
  
  /* UI Colors */
  --color-background: white;
  --color-surface: var(--color-gray-50);
  --color-border: var(--color-gray-100);
  
  /* Text Colors */
  --color-text-primary: var(--color-gray-900);
  --color-text-secondary: var(--color-gray-500);
  --color-text-on-primary: white;
  
  /* State Colors */
  --color-success: #10B981;
  --color-warning: #F59E0B;
  --color-error: #EF4444;
  --color-info: var(--color-blue-500);
}

/* 3. Component Tokens (Specific Overrides) */
:root {
  /* Button */
  --btn-padding-x: var(--space-4);
  --btn-padding-y: var(--space-2);
  --btn-font-size: var(--font-size-base);
  --btn-font-weight: var(--font-weight-semibold);
  --btn-radius: var(--radius-md);
  
  --btn-primary-bg: var(--color-primary);
  --btn-primary-text: var(--color-text-on-primary);
  --btn-primary-hover-bg: var(--color-primary-hover);
  
  /* Input */
  --input-padding-x: var(--space-3);
  --input-padding-y: var(--space-2);
  --input-border-color: var(--color-border);
  --input-border-radius: var(--radius-md);
  --input-focus-ring: 0 0 0 3px var(--color-primary-light);
  
  /* Card */
  --card-padding: var(--space-6);
  --card-radius: var(--radius-lg);
  --card-shadow: var(--shadow-md);
  --card-border: 1px solid var(--color-border);
}

/* Dark Mode Overrides */
[data-theme="dark"] {
  --color-background: var(--color-gray-900);
  --color-surface: #1A1A1A;
  --color-border: #2A2A2A;
  --color-text-primary: var(--color-gray-50);
  --color-text-secondary: var(--color-gray-500);
}
```

### 3.2 Component Composition (Atomic Design)

**Hierarchy:**

```
Atoms (Smallest Units)
├── Button
├── Input
├── Label
├── Icon
├── Badge
└── Avatar

Molecules (Groups of Atoms)
├── SearchBar (Input + Button + Icon)
├── FormField (Label + Input + ErrorMessage)
├── UserCard (Avatar + Text + Badge)
└── Dropdown (Button + Menu + Items)

Organisms (Complex Components)
├── Navbar (Logo + Navigation + SearchBar + UserCard)
├── Sidebar (Navigation + UserCard + Settings)
├── ProductCard (Image + Title + Price + Button)
└── CommentSection (UserCard + Input + CommentList)

Templates (Page Layouts)
├── DashboardLayout (Navbar + Sidebar + Main)
├── AuthLayout (Logo + Form + Footer)
└── LandingLayout (Hero + Features + CTA)

Pages (Specific Instances)
├── HomePage
├── LoginPage
└── ProductDetailPage
```

**Example Implementation:**

```typescript
// Atom: Button
interface ButtonProps {
  children: React.ReactNode;
  variant?: 'primary' | 'secondary' | 'ghost';
  size?: 'sm' | 'md' | 'lg';
  onClick?: () => void;
  disabled?: boolean;
}

const Button: React.FC<ButtonProps> = ({ 
  children, 
  variant = 'primary', 
  size = 'md',
  ...props 
}) => {
  return (
    <button 
      className={`btn btn--${variant} btn--${size}`}
      {...props}
    >
      {children}
    </button>
  );
};

// Molecule: SearchBar
interface SearchBarProps {
  placeholder?: string;
  onSearch: (query: string) => void;
}

const SearchBar: React.FC<SearchBarProps> = ({ placeholder, onSearch }) => {
  const [query, setQuery] = useState('');
  
  return (
    <div className="search-bar">
      <Icon name="search" />
      <Input 
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder={placeholder}
      />
      <Button onClick={() => onSearch(query)}>Search</Button>
    </div>
  );
};

// Organism: Navbar
const Navbar: React.FC = () => {
  return (
    <nav className="navbar">
      <Logo />
      <Navigation items={navItems} />
      <SearchBar onSearch={handleSearch} />
      <UserCard user={currentUser} />
    </nav>
  );
};
```

### 3.3 Props & Interfaces (TypeScript)

**Strict Type Definitions:**

```typescript
// ✅ Comprehensive interface
interface CardProps {
  // Required props
  title: string;
  
  // Optional props with defaults
  variant?: 'default' | 'outlined' | 'elevated';
  size?: 'sm' | 'md' | 'lg';
  
  // Content slots (use ReactNode, not string)
  children: React.ReactNode;
  header?: React.ReactNode;
  footer?: React.ReactNode;
  
  // Event handlers
  onClick?: (event: React.MouseEvent<HTMLDivElement>) => void;
  onHover?: () => void;
  
  // Style overrides
  className?: string;
  style?: React.CSSProperties;
  
  // Accessibility
  ariaLabel?: string;
  role?: string;
  
  // State
  isLoading?: boolean;
  isDisabled?: boolean;
}

// ✅ Default props
const Card: React.FC<CardProps> = ({
  title,
  variant = 'default',
  size = 'md',
  children,
  header,
  footer,
  className = '',
  isLoading = false,
  ...props
}) => {
  return (
    <div 
      className={`card card--${variant} card--${size} ${className}`}
      {...props}
    >
      {header && <div className="card__header">{header}</div>}
      <div className="card__body">
        <h3 className="card__title">{title}</h3>
        {isLoading ? <Spinner /> : children}
      </div>
      {footer && <div className="card__footer">{footer}</div>}
    </div>
  );
};
```

**Headless UI Pattern (Separation of Logic & Presentation):**

```typescript
// Logic Hook (Headless)
function useDropdown() {
  const [isOpen, setIsOpen] = useState(false);
  const [selectedIndex, setSelectedIndex] = useState(0);
  
  const toggle = () => setIsOpen(!isOpen);
  const close = () => setIsOpen(false);
  const select = (index: number) => {
    setSelectedIndex(index);
    close();
  };
  
  return {
    isOpen,
    selectedIndex,
    toggle,
    close,
    select,
  };
}

// Presentation Component
const Dropdown: React.FC<DropdownProps> = ({ items, onSelect }) => {
  const { isOpen, selectedIndex, toggle, select } = useDropdown();
  
  return (
    <div className="dropdown">
      <button onClick={toggle} aria-expanded={isOpen}>
        {items[selectedIndex].label}
      </button>
      {isOpen && (
        <ul className="dropdown__menu">
          {items.map((item, index) => (
            <li 
              key={item.id}
              onClick={() => {
                select(index);
                onSelect(item);
              }}
            >
              {item.label}
            </li>
          ))}
        </ul>
      )}
    </div>
  );
};
```

---

## 4. Interaction & Motion Design

### 4.1 Micro-interactions (State Feedback)

**Essential States:**

```css
/* Base state */
.button {
  background-color: var(--btn-primary-bg);
  transform: scale(1);
  transition: all 0.2s ease;
}

/* Hover state */
.button:hover {
  background-color: var(--btn-primary-hover-bg);
  transform: scale(1.02);
  box-shadow: var(--shadow-md);
}

/* Active state (click) */
.button:active {
  transform: scale(0.98);
  box-shadow: var(--shadow-sm);
}

/* Focus state (keyboard navigation) */
.button:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

/* Disabled state */
.button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

/* Loading state */
.button--loading {
  position: relative;
  color: transparent;
}

.button--loading::after {
  content: '';
  position: absolute;
  width: 16px;
  height: 16px;
  border: 2px solid white;
  border-top-color: transparent;
  border-radius: 50%;
  animation: spin 0.6s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
```

### 4.2 Transitions & Animations

**Performance-Optimized Properties:**

Only animate properties that don't trigger layout/paint:
* ✅ `transform` (translate, scale, rotate)
* ✅ `opacity`
* ❌ `width`, `height`, `top`, `left` (causes reflow)
* ❌ `background-color` (use `opacity` on pseudo-element instead)

**Standard Duration Scale:**

```css
:root {
  --duration-instant: 100ms;  /* Instant feedback (hover) */
  --duration-fast: 200ms;     /* Quick transitions */
  --duration-normal: 300ms;   /* Standard animations */
  --duration-slow: 500ms;     /* Emphasis animations */
}

/* Usage */
.card {
  transition: transform var(--duration-fast) ease-out;
}

.modal {
  animation: fadeIn var(--duration-normal) ease-out;
}
```

**Common Animation Patterns:**

```css
/* Fade In */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Slide In */
@keyframes slideIn {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

/* Scale In */
@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

/* Skeleton Loading */
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
    #f0f0f0 25%,
    #e0e0e0 50%,
    #f0f0f0 75%
  );
  background-size: 1000px 100%;
  animation: shimmer 2s infinite;
}
```

### 4.3 Accessibility in Motion

**Respect User Preferences:**

```css
/* Disable animations for users who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* Alternative: Provide simpler animations */
@media (prefers-reduced-motion: reduce) {
  .modal {
    animation: fadeIn 0.1s ease-out; /* Faster, simpler */
  }
}

@media (prefers-reduced-motion: no-preference) {
  .modal {
    animation: slideIn 0.3s ease-out; /* Full animation */
  }
}
```

---

## 5. Accessibility (A11y) Compliance

### 5.1 Keyboard Navigation

**Tab Order & Focus Management:**

```html
<!-- ✅ Logical tab order -->
<form>
  <input type="text" tabindex="0"> <!-- Default order -->
  <input type="email" tabindex="0">
  <button type="submit" tabindex="0">Submit</button>
</form>

<!-- ❌ Never use positive tabindex -->
<button tabindex="1">Bad</button> <!-- Breaks natural order -->

<!-- ✅ Skip to main content link -->
<a href="#main-content" class="skip-link">Skip to main content</a>
<nav>...</nav>
<main id="main-content">...</main>
```

**Focus Styles:**

```css
/* ❌ Never do this */
*:focus {
  outline: none; /* Removes accessibility indicator */
}

/* ✅ Custom focus styles */
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
  border-radius: 4px;
}

/* Different styles for different elements */
button:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

input:focus-visible {
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px var(--color-primary-light);
}
```

### 5.2 Screen Reader Support

**ARIA Attributes (Use Sparingly):**

```html
<!-- ✅ Button with dynamic state -->
<button 
  aria-expanded="false" 
  aria-controls="menu"
  aria-label="Open navigation menu"
>
  Menu
</button>

<!-- ✅ Loading state -->
<div aria-live="polite" aria-busy="true">
  Loading content...
</div>

<!-- ✅ Hidden decorative elements -->
<svg aria-hidden="true" focusable="false">
  <use href="#icon-decorative"></use>
</svg>

<!-- ✅ Accessible form validation -->
<input 
  type="email" 
  aria-invalid="true" 
  aria-describedby="email-error"
>
<span id="email-error" role="alert">
  Please enter a valid email address
</span>

<!-- ✅ Progress indicator -->
<div 
  role="progressbar" 
  aria-valuenow="75" 
  aria-valuemin="0" 
  aria-valuemax="100"
  aria-label="Upload progress"
>
  75% complete
</div>
```

**ARIA Label Decision Matrix:**

| Scenario | Solution | Example |
|:---------|:---------|:--------|
| Visible text exists | No ARIA needed | `<button>Submit</button>` |
| Icon-only button | Use `aria-label` | `<button aria-label="Close"><Icon /></button>` |
| Additional context needed | Use `aria-describedby` | `<input aria-describedby="hint">` |
| Dynamic content | Use `aria-live` | `<div aria-live="polite">New message</div>` |
| Decorative image | Use `alt=""` | `<img src="bg.jpg" alt="">` |
| Informative image | Use descriptive `alt` | `<img src="chart.png" alt="Sales increased 25%">` |

### 5.3 Color Contrast

**WCAG 2.1 AA Requirements:**

* **Normal text (< 18px):** 4.5:1 contrast ratio
* **Large text (≥ 18px or ≥ 14px bold):** 3:1 contrast ratio
* **UI components & graphics:** 3:1 contrast ratio

**Testing & Implementation:**

```css
/* ✅ Sufficient contrast examples */
.text-on-white {
  color: #333333; /* 12.6:1 ratio */
  background: #FFFFFF;
}

.text-on-primary {
  color: #FFFFFF; /* 4.5:1 ratio */
  background: #0066CC;
}

/* ❌ Insufficient contrast */
.bad-contrast {
  color: #999999; /* 2.8:1 ratio - FAILS */
  background: #FFFFFF;
}

/* ✅ Fix with darker color */
.good-contrast {
  color: #666666; /* 5.7:1 ratio - PASSES */
  background: #FFFFFF;
}
```

**Tools for Testing:**
* Chrome DevTools: Lighthouse audit
* Browser extensions: axe DevTools, WAVE
* Online: WebAIM Contrast Checker

---

## 6. Performance & Core Web Vitals

### 6.1 Cumulative Layout Shift (CLS)

**Problem:** Elements shifting during page load

**Solutions:**

```html
<!-- ✅ Reserve space for images -->
<img 
  src="hero.jpg" 
  alt="Hero image"
  width="1200" 
  height="600"
  style="aspect-ratio: 2 / 1;"
>

<!-- ✅ Use aspect-ratio for responsive images -->
<style>
.image-container {
  aspect-ratio: 16 / 9;
  width: 100%;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>

<!-- ✅ Reserve space for dynamic content -->
<div class="skeleton" style="min-height: 200px;">
  <!-- Content loads here -->
</div>

<!-- ✅ Preload fonts to prevent FOUT -->
<link 
  rel="preload" 
  href="/fonts/inter.woff2" 
  as="font" 
  type="font/woff2" 
  crossorigin
>
```

### 6.2 Largest Contentful Paint (LCP)

**Target:** < 2.5 seconds

**Optimization Strategies:**

```html
<!-- ✅ Preload critical images -->
<link rel="preload" as="image" href="/hero.jpg">

<!-- ✅ Use responsive images -->
<img 
  src="hero-800.jpg"
  srcset="
    hero-400.jpg 400w,
    hero-800.jpg 800w,
    hero-1200.jpg 1200w
  "
  sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1200px"
  alt="Hero"
>

<!-- ✅ Use modern image formats -->
<picture>
  <source srcset="hero.avif" type="image/avif">
  <source srcset="hero.webp" type="image/webp">
  <img src="hero.jpg" alt="Hero">
</picture>

<!-- ✅ Inline critical CSS -->
<style>
  /* Critical above-the-fold styles */
  .hero { /* ... */ }
</style>

<!-- ✅ Defer non-critical CSS -->
<link 
  rel="preload" 
  href="/styles/non-critical.css" 
  as="style" 
  onload="this.onload=null;this.rel='stylesheet'"
>
```

### 6.3 First Input Delay (FID) / Interaction to Next Paint (INP)

**Target:** < 100ms (FID), < 200ms (INP)

**Optimization:**

```javascript
// ✅ Code splitting (lazy load non-critical components)
const HeavyComponent = React.lazy(() => import('./HeavyComponent'));

function App() {
  return (
    <Suspense fallback={<Spinner />}>
      <HeavyComponent />
    </Suspense>
  );
}

// ✅ Debounce expensive operations
import { debounce } from 'lodash';

const handleSearch = debounce((query) => {
  // Expensive search operation
}, 300);

// ✅ Use Web Workers for heavy computation
const worker = new Worker('heavy-task.js');
worker.postMessage({ data: largeDataset });
worker.onmessage = (e) => {
  console.log('Result:', e.data);
};
```

### 6.4 Asset Optimization

**Image Optimization:**

```bash
# Convert to WebP
cwebp input.jpg -q 80 -o output.webp

# Convert to AVIF
avif --input input.jpg --output output.avif --quality 80
```

**CSS Optimization:**

```css
/* ✅ Use CSS containment for performance */
.card {
  contain: layout style paint;
}

/* ✅ Use will-change sparingly */
.animated-element:hover {
  will-change: transform;
}

.animated-element {
  will-change: auto; /* Reset after animation */
}

/* ✅ Optimize font loading */
@font-face {
  font-family: 'Inter';
  src: url('/fonts/inter.woff2') format('woff2');
  font-display: swap; /* Show fallback font immediately */
  font-weight: 400;
}
```

---

## 7. Responsive Design Patterns

### 7.1 Mobile-First Approach

```css
/* ✅ Mobile-first (base styles for mobile) */
.container {
  padding: 1rem;
  font-size: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: 2rem;
    font-size: 1.125rem;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    padding: 3rem;
    max-width: 1200px;
    margin: 0 auto;
  }
}

/* ❌ Desktop-first (avoid) */
.container {
  padding: 3rem; /* Desktop styles */
}

@media (max-width: 1024px) {
  .container {
    padding: 2rem; /* Override for smaller screens */
  }
}
```

### 7.2 Breakpoint System

```css
:root {
  --breakpoint-sm: 640px;   /* Mobile landscape */
  --breakpoint-md: 768px;   /* Tablet portrait */
  --breakpoint-lg: 1024px;  /* Tablet landscape / Small desktop */
  --breakpoint-xl: 1280px;  /* Desktop */
  --breakpoint-2xl: 1536px; /* Large desktop */
}

/* Usage with custom media queries (PostCSS) */
@custom-media --sm (min-width: 640px);
@custom-media --md (min-width: 768px);
@custom-media --lg (min-width: 1024px);
```

### 7.3 Fluid Typography

```css
/* ✅ Clamp for responsive font sizes */
.heading {
  font-size: clamp(1.5rem, 4vw, 3rem);
  /* Min: 24px, Preferred: 4% of viewport, Max: 48px */
}

.body {
  font-size: clamp(1rem, 2vw, 1.125rem);
  /* Min: 16px, Preferred: 2% of viewport, Max: 18px */
}

/* ✅ Fluid spacing */
.section {
  padding-block: clamp(2rem, 5vw, 6rem);
  /* Min: 32px, Preferred: 5% of viewport, Max: 96px */
}
```

---

## 8. Usage Workflow for AI Generation

When generating frontend code, follow this systematic sequence:

### Step 1: Analyze Requirements
* **Component Type:** Is this a reusable Atom, Molecule, Organism, or a one-off Page?
* **Responsive Needs:** What are the mobile vs. tablet vs. desktop constraints?
* **Accessibility Level:** Does this need WCAG AA or AAA compliance?
* **Performance Budget:** Are there specific LCP/CLS targets?
* **Browser Support:** Modern browsers only, or legacy support needed?

### Step 2: Define Structure (HTML)
1. Draft semantic HTML skeleton first
2. Add ARIA attributes immediately (if needed)
3. Ensure logical heading hierarchy
4. Add landmark regions (`<main>`, `<nav>`, etc.)
5. Include skip links for keyboard users

### Step 3: Apply Tokens (CSS)
1. Map design values (colors, spacing, typography) to existing design tokens
2. Use CSS variables for theming
3. **Never hardcode magic numbers** (e.g., `margin: 13px`)
4. Follow the spacing scale (`--space-*`)
5. Use logical properties for RTL support

### Step 4: Implement Responsiveness
1. Start with mobile-first base styles
2. Add breakpoints progressively
3. Use container queries for component-level responsiveness
4. Test with browser DevTools device emulation

### Step 5: Add Interactivity (JS/TS)
1. Define Props Interface with TypeScript
2. Handle all states: loading, error, empty, success
3. Implement keyboard navigation
4. Add focus management
5. Use appropriate ARIA attributes for dynamic content

### Step 6: Optimize Performance
1. Lazy load non-critical components
2. Optimize images (WebP/AVIF, responsive srcset)
3. Reserve space for dynamic content (prevent CLS)
4. Minimize JavaScript bundle size
5. Use CSS containment where applicable

### Step 7: Audit & Test
1. **Contrast:** Use browser DevTools or WebAIM checker
2. **Responsive:** Test across breakpoints
3. **Keyboard:** Tab through entire interface
4. **Screen Reader:** Test with VoiceOver (Mac) or NVDA (Windows)
5. **Performance:** Run Lighthouse audit
6. **States:** Verify hover, focus, active, disabled states

---

## 9. Dos and Don'ts

| Category | ✅ Do | ❌ Don't |
|:---------|:------|:---------|
| **Sizing** | Use `rem` for font-size and spacing | Use `px` for font-size (inaccessible to users who change browser font size) |
| **Images** | Use semantic `<img>` with `alt`, `width`, `height` | Use `<div>` with `background-image` for content images |
| **CSS Variables** | Use CSS Custom Properties (`var(--color)`) for theming | Use Sass variables for runtime theming (compiled away) |
| **State Management** | Use CSS for hover/active/focus states | Use JavaScript `onMouseEnter` for simple style changes |
| **Grid Spacing** | Use `gap` property for grid/flex spacing | Use margins on children to create gutters (breaks with wrapping) |
| **Focus Styles** | Provide visible `:focus-visible` outlines | Set `outline: none` without replacement |
| **Animations** | Animate `transform` and `opacity` only | Animate `width`, `height`, `top`, `left` (causes reflow) |
| **ARIA** | Use ARIA only when semantic HTML isn't enough | Add ARIA to every element "just in case" |
| **Breakpoints** | Use mobile-first `min-width` media queries | Use desktop-first `max-width` media queries |
| **Typography** | Use system font stack or preload custom fonts | Load multiple font weights/styles unnecessarily |
| **Colors** | Use design tokens from theme | Hardcode hex values directly in components |
| **Semantic HTML** | Use `<button>` for actions, `<a>` for navigation | Use `<div onClick>` for interactive elements |
| **Accessibility** | Test with keyboard and screen readers | Assume visual testing is sufficient |
| **Performance** | Lazy load below-the-fold content | Load all JavaScript upfront |
| **Component Props** | Use `React.ReactNode` for content slots | Pass large HTML strings as props |

---

## 10. Tools & Resources

### Development Tools
* **Browser DevTools:** Chrome/Firefox/Safari for debugging, Lighthouse audits
* **VS Code Extensions:** 
  * Prettier (code formatting)
  * ESLint (linting)
  * Tailwind CSS IntelliSense
  * axe Accessibility Linter

### Accessibility Testing
* **Screen Readers:** VoiceOver (Mac), NVDA (Windows), JAWS
* **Browser Extensions:** axe DevTools, WAVE, Lighthouse
* **Contrast Checkers:** WebAIM Contrast Checker, Stark

### Performance Testing
* **Lighthouse:** Built into Chrome DevTools
* **WebPageTest:** Detailed performance analysis
* **Chrome User Experience Report:** Real-world performance data

### Design Systems Reference
* **Material Design:** Google's design system
* **Ant Design:** Enterprise-level UI design
* **Chakra UI:** Accessible component library
* **Radix UI:** Unstyled, accessible components

---

## 11. Quick Reference Checklist

Before shipping any UI component, verify:

- [ ] **Semantic HTML:** Correct element usage (`<button>`, `<a>`, `<nav>`, etc.)
- [ ] **Heading Hierarchy:** Logical `h1` → `h6` structure
- [ ] **Keyboard Navigation:** All interactive elements are keyboard accessible
- [ ] **Focus Styles:** Visible `:focus-visible` indicators
- [ ] **ARIA Attributes:** Only where necessary, correctly implemented
- [ ] **Color Contrast:** Meets WCAG AA (4.5:1 for text, 3:1 for UI)
- [ ] **Responsive Design:** Works on mobile, tablet, desktop
- [ ] **Touch Targets:** Minimum 44x44px for interactive elements
- [ ] **Loading States:** Skeleton screens or spinners for async content
- [ ] **Error States:** Clear error messages with recovery options
- [ ] **Empty States:** Helpful messaging when no content exists
- [ ] **Image Optimization:** WebP/AVIF formats, responsive `srcset`
- [ ] **Performance:** LCP < 2.5s, CLS < 0.1, FID/INP < 100ms
- [ ] **Motion Preferences:** Respects `prefers-reduced-motion`
- [ ] **Design Tokens:** No hardcoded values, uses CSS variables
- [ ] **Code Splitting:** Non-critical components are lazy loaded

---

## Conclusion

This skill document serves as the comprehensive technical foundation for implementing production-ready, accessible, performant, and maintainable user interfaces. Always prioritize user experience, accessibility, and performance over visual complexity. When in doubt, refer to WCAG guidelines and Web Vitals benchmarks.

**Remember:** Great frontend development is not just about making things look good—it's about making them work well for everyone, everywhere, on every device.
