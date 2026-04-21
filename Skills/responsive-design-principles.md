---
name: responsive-design-principles
description: "Comprehensive technical and strategic framework for device-agnostic development. Covers fluid systems, adaptive media, container queries, mobile ergonomics, and modern CSS techniques."
---

# Responsive Design Principles

This skill provides comprehensive logic for creating interfaces that adapt fluidly to any viewport. It moves beyond "Mobile/Tablet/Desktop" silos toward a truly continuous, fluid web experience that works seamlessly across all devices and contexts.

---

## 1. The Mobile-First Paradigm

### 1.1 Progressive Enhancement Philosophy

**Core Principle:** Start with the simplest, most performant code for mobile devices, then progressively layer on complexity as capabilities and screen real estate increase.

**Why Mobile-First?**
- **Performance:** Mobile devices often have slower processors and network connections
- **Constraints Drive Focus:** Limited space forces you to prioritize essential content
- **Easier to Scale Up:** Adding features is easier than removing them
- **Better Accessibility:** Simpler base code is more accessible by default

**Implementation Strategy:**

```css
/* Base styles (Mobile-First) - No media query needed */
.navigation {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  background: var(--nav-bg);
}

.nav-item {
  padding: 0.75rem;
  font-size: 1rem;
}

/* Tablet Enhancement */
@media (min-width: 768px) {
  .navigation {
    flex-direction: row;
    justify-content: space-between;
    padding: 1.5rem 2rem;
  }
}

/* Desktop Enhancement */
@media (min-width: 1024px) {
  .navigation {
    padding: 2rem 4rem;
  }
  
  .nav-item {
    font-size: 1.125rem;
  }
  
  .nav-item:hover {
    background: var(--nav-hover);
  }
}
```

### 1.2 Core Content Prioritization

**The Critical Path:** Identify what users *must* see and do on mobile, then build around that.

**Content Hierarchy Techniques:**

1. **Visual Hierarchy:**
   ```css
   /* Mobile: Stack vertically, prioritize main content */
   .layout {
     display: grid;
     grid-template-areas:
       "header"
       "main"
       "sidebar"
       "footer";
   }
   
   /* Desktop: Traditional layout */
   @media (min-width: 1024px) {
     .layout {
       grid-template-areas:
         "header header header"
         "sidebar main main"
         "footer footer footer";
       grid-template-columns: 250px 1fr 1fr;
     }
   }
   ```

2. **Progressive Disclosure:**
   ```css
   /* Hide secondary content on mobile */
   .secondary-features {
     display: none;
   }
   
   @media (min-width: 768px) {
     .secondary-features {
       display: block;
     }
   }
   ```

3. **Conditional Loading:**
   ```html
   <!-- Load heavy components only on larger screens -->
   <picture>
     <source media="(min-width: 1024px)" srcset="hero-desktop.jpg">
     <source media="(min-width: 768px)" srcset="hero-tablet.jpg">
     <img src="hero-mobile.jpg" alt="Hero image">
   </picture>
   ```

### 1.3 Performance Budgeting

**Mobile Performance Targets:**
- **First Contentful Paint (FCP):** < 1.8s
- **Largest Contentful Paint (LCP):** < 2.5s
- **Time to Interactive (TTI):** < 3.8s
- **Total Page Weight:** < 500KB (initial load)

**Optimization Strategies:**

1. **System Fonts First:**
   ```css
   body {
     font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 
                  Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
   }
   
   /* Load custom fonts only on faster connections */
   @media (min-width: 1024px) {
     body {
       font-family: 'Inter', -apple-system, sans-serif;
     }
   }
   ```

2. **Lazy Loading:**
   ```html
   <img src="placeholder.jpg" 
        data-src="actual-image.jpg" 
        loading="lazy" 
        alt="Description">
   ```

3. **Critical CSS Inlining:**
   ```html
   <style>
     /* Inline critical above-the-fold CSS */
     .hero { display: flex; min-height: 100vh; }
   </style>
   <link rel="stylesheet" href="main.css" media="print" onload="this.media='all'">
   ```

---

## 2. Fluid Foundations (Units & Grids)

### 2.1 Fluid Typography

**The Problem with Fixed Sizes:** `font-size: 16px` looks different on a 320px phone vs. a 2560px monitor.

**Modern Solution: `clamp()` Function**

```css
/* Syntax: clamp(MIN, PREFERRED, MAX) */
h1 {
  font-size: clamp(2rem, 5vw + 1rem, 4rem);
  /* Scales from 32px to 64px based on viewport */
}

h2 {
  font-size: clamp(1.5rem, 3vw + 0.5rem, 2.5rem);
}

p {
  font-size: clamp(1rem, 2vw, 1.25rem);
  line-height: 1.6;
}
```

**Type Scale System:**

```css
:root {
  /* Fluid type scale */
  --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
  --text-sm: clamp(0.875rem, 0.8rem + 0.375vw, 1rem);
  --text-base: clamp(1rem, 0.9rem + 0.5vw, 1.125rem);
  --text-lg: clamp(1.125rem, 1rem + 0.625vw, 1.25rem);
  --text-xl: clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem);
  --text-2xl: clamp(1.5rem, 1.3rem + 1vw, 2rem);
  --text-3xl: clamp(1.875rem, 1.6rem + 1.375vw, 2.5rem);
  --text-4xl: clamp(2.25rem, 2rem + 1.25vw, 3rem);
}

h1 { font-size: var(--text-4xl); }
h2 { font-size: var(--text-3xl); }
h3 { font-size: var(--text-2xl); }
```

### 2.2 Relative Units Deep Dive

**Unit Comparison Table:**

| Unit | Use Case | Example | Notes |
|------|----------|---------|-------|
| `rem` | Font sizes, spacing | `padding: 1.5rem` | Relative to root font-size (16px default) |
| `em` | Component-scoped sizing | `margin: 0.5em` | Relative to parent font-size |
| `%` | Layout widths, heights | `width: 100%` | Relative to parent dimension |
| `vw` | Full-width elements | `width: 100vw` | 1% of viewport width |
| `vh` | Full-height sections | `min-height: 100vh` | 1% of viewport height |
| `vmin` | Responsive squares | `width: 50vmin` | Smaller of vw or vh |
| `vmax` | Diagonal scaling | `font-size: 2vmax` | Larger of vw or vh |
| `ch` | Text-based widths | `max-width: 65ch` | Width of "0" character |
| `fr` | Grid columns | `grid-template-columns: 1fr 2fr` | Fraction of available space |

**Practical Examples:**

```css
/* Optimal reading width */
.article {
  max-width: 65ch; /* ~65 characters per line */
  margin-inline: auto;
  padding: 2rem;
}

/* Responsive container */
.container {
  width: min(90%, 1200px); /* Smaller of 90% or 1200px */
  margin-inline: auto;
}

/* Fluid spacing system */
:root {
  --space-xs: clamp(0.5rem, 1vw, 0.75rem);
  --space-sm: clamp(0.75rem, 1.5vw, 1rem);
  --space-md: clamp(1rem, 2vw, 1.5rem);
  --space-lg: clamp(1.5rem, 3vw, 2rem);
  --space-xl: clamp(2rem, 4vw, 3rem);
  --space-2xl: clamp(3rem, 6vw, 5rem);
}
```

### 2.3 Intrinsic Sizing

**Modern CSS Sizing Keywords:**

```css
/* min-content: Shrinks to smallest possible size */
.tag {
  width: min-content;
  white-space: nowrap;
}

/* max-content: Expands to fit all content */
.button {
  width: max-content;
  padding-inline: 2rem;
}

/* fit-content: Grows up to max-content, then wraps */
.card {
  width: fit-content;
  max-width: 100%;
}

/* Practical example: Auto-sizing grid */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(250px, 100%), 1fr));
  gap: 1.5rem;
}
```

---

## 3. Breakpoint & Adaptation Strategy

### 3.1 Standard Breakpoint Scale

**Tailwind/Bootstrap Standard (Recommended):**

```css
/* Mobile First - Base styles (0-639px) */
.element { /* mobile styles */ }

/* Small devices (640px+) - Large phones */
@media (min-width: 640px) {
  .element { /* sm styles */ }
}

/* Medium devices (768px+) - Tablets */
@media (min-width: 768px) {
  .element { /* md styles */ }
}

/* Large devices (1024px+) - Laptops */
@media (min-width: 1024px) {
  .element { /* lg styles */ }
}

/* Extra large (1280px+) - Desktops */
@media (min-width: 1280px) {
  .element { /* xl styles */ }
}

/* 2X large (1536px+) - Large monitors */
@media (min-width: 1536px) {
  .element { /* 2xl styles */ }
}
```

**CSS Custom Properties for Breakpoints:**

```css
:root {
  --breakpoint-sm: 640px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 1024px;
  --breakpoint-xl: 1280px;
  --breakpoint-2xl: 1536px;
}

/* Usage in media queries */
@media (min-width: 768px) { /* md */ }
```

### 3.2 Content-Driven Breakpoints

**Don't design for devices—design for content.**

**Example: Card Grid Breakpoint:**

```css
.card-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
}

/* Content looks cramped at 2 columns below 600px */
@media (min-width: 600px) {
  .card-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* 3 columns work well at 900px */
@media (min-width: 900px) {
  .card-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* 4 columns for very wide screens */
@media (min-width: 1400px) {
  .card-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}
```

**Auto-Responsive Grid (No Breakpoints Needed):**

```css
.auto-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(300px, 100%), 1fr));
  gap: 2rem;
}
/* Automatically adjusts columns based on available space */
```

### 3.3 Container Queries (`@container`)

**The Future of Responsive Design:** Components respond to their container size, not viewport size.

**Basic Setup:**

```css
/* Define container */
.sidebar {
  container-type: inline-size;
  container-name: sidebar;
}

/* Query the container */
.card {
  padding: 1rem;
}

@container sidebar (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 150px 1fr;
    padding: 1.5rem;
  }
}
```

**Advanced Example: Adaptive Card Component:**

```css
/* Card adapts based on its container, not viewport */
.card-container {
  container-type: inline-size;
}

.card {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding: 1rem;
  background: white;
  border-radius: 8px;
}

/* When container is 400px+, switch to horizontal layout */
@container (min-width: 400px) {
  .card {
    flex-direction: row;
    align-items: center;
  }
  
  .card-image {
    width: 150px;
    height: 150px;
  }
}

/* When container is 600px+, add more details */
@container (min-width: 600px) {
  .card {
    padding: 2rem;
  }
  
  .card-metadata {
    display: block;
  }
}
```

**Container Query Units:**

```css
.card-container {
  container-type: inline-size;
}

.card-title {
  /* cqw = container query width (1% of container width) */
  font-size: clamp(1rem, 3cqw, 2rem);
}

.card-image {
  /* cqh = container query height */
  height: 30cqh;
}
```

---

## 4. Adaptive Media & Assets

### 4.1 Responsive Images

**The `srcset` Attribute:**

```html
<!-- Density descriptors (for different pixel densities) -->
<img 
  src="image-1x.jpg"
  srcset="image-1x.jpg 1x,
          image-2x.jpg 2x,
          image-3x.jpg 3x"
  alt="Responsive image">

<!-- Width descriptors (for different viewport sizes) -->
<img 
  src="image-800.jpg"
  srcset="image-400.jpg 400w,
          image-800.jpg 800w,
          image-1200.jpg 1200w,
          image-1600.jpg 1600w"
  sizes="(max-width: 600px) 100vw,
         (max-width: 1200px) 50vw,
         800px"
  alt="Responsive image">
```

**Understanding `sizes` Attribute:**

```html
<img 
  srcset="small.jpg 400w, medium.jpg 800w, large.jpg 1200w"
  sizes="(max-width: 600px) 100vw,
         (max-width: 1200px) 50vw,
         33vw"
  alt="Example">
<!-- 
  Translation:
  - On screens ≤600px: image takes 100% viewport width
  - On screens 601-1200px: image takes 50% viewport width
  - On screens >1200px: image takes 33% viewport width
  Browser picks the best image from srcset based on this info
-->
```

### 4.2 Art Direction with `<picture>`

**Different crops/images for different viewports:**

```html
<picture>
  <!-- Mobile: Vertical crop, portrait orientation -->
  <source 
    media="(max-width: 767px)" 
    srcset="hero-mobile-400.jpg 400w,
            hero-mobile-800.jpg 800w"
    sizes="100vw">
  
  <!-- Tablet: Square crop -->
  <source 
    media="(max-width: 1023px)" 
    srcset="hero-tablet-800.jpg 800w,
            hero-tablet-1200.jpg 1200w"
    sizes="100vw">
  
  <!-- Desktop: Wide landscape crop -->
  <source 
    media="(min-width: 1024px)" 
    srcset="hero-desktop-1200.jpg 1200w,
            hero-desktop-1920.jpg 1920w,
            hero-desktop-2560.jpg 2560w"
    sizes="100vw">
  
  <!-- Fallback -->
  <img src="hero-fallback.jpg" alt="Hero image">
</picture>
```

**Modern Image Formats:**

```html
<picture>
  <!-- Serve AVIF to supporting browsers (best compression) -->
  <source type="image/avif" srcset="image.avif">
  
  <!-- Serve WebP to supporting browsers (good compression) -->
  <source type="image/webp" srcset="image.webp">
  
  <!-- Fallback to JPEG (universal support) -->
  <img src="image.jpg" alt="Description">
</picture>
```

### 4.3 Responsive Video

**Adaptive Video Loading:**

```html
<!-- Disable autoplay on mobile to save data -->
<video 
  poster="video-poster.jpg"
  controls
  preload="metadata">
  
  <!-- Serve smaller video on mobile -->
  <source 
    src="video-mobile.mp4" 
    type="video/mp4"
    media="(max-width: 767px)">
  
  <!-- HD video for desktop -->
  <source 
    src="video-desktop.mp4" 
    type="video/mp4"
    media="(min-width: 768px)">
</video>
```

**CSS for Responsive Video Embeds:**

```css
/* Maintain 16:9 aspect ratio */
.video-container {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* 16:9 ratio */
  height: 0;
  overflow: hidden;
}

.video-container iframe,
.video-container video {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

### 4.4 Background Images

```css
.hero {
  background-image: url('hero-mobile.jpg');
  background-size: cover;
  background-position: center;
  min-height: 400px;
}

@media (min-width: 768px) {
  .hero {
    background-image: url('hero-tablet.jpg');
    min-height: 500px;
  }
}

@media (min-width: 1024px) {
  .hero {
    background-image: url('hero-desktop.jpg');
    min-height: 600px;
  }
}

/* High DPI screens */
@media (min-width: 1024px) and (-webkit-min-device-pixel-ratio: 2) {
  .hero {
    background-image: url('hero-desktop-2x.jpg');
  }
}
```

---

## 5. Mobile Ergonomics & Touch

### 5.1 The Thumb Zone

**Mobile Interaction Heatmap:**

```
┌─────────────────┐
│  Hard to Reach  │ ← Top of screen
├─────────────────┤
│                 │
│   Easy Reach    │ ← Middle (natural thumb arc)
│                 │
├─────────────────┤
│  Primary Zone   │ ← Bottom third (optimal)
└─────────────────┘
```

**Practical Implementation:**

```css
/* Mobile navigation at bottom */
.mobile-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-around;
  padding: 1rem;
  background: white;
  box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
}

@media (min-width: 768px) {
  .mobile-nav {
    position: static;
    box-shadow: none;
  }
}
```

### 5.2 Touch Target Sizing

**Minimum Sizes (WCAG 2.5.5):**
- **Apple:** 44×44 points
- **Android:** 48×48 dp
- **Web Standard:** 44×44 CSS pixels minimum

**Implementation:**

```css
/* Ensure all interactive elements meet minimum size */
button,
a,
input,
.interactive {
  min-height: 44px;
  min-width: 44px;
  padding: 0.75rem 1.5rem;
}

/* Add visual padding without affecting layout */
.touch-target {
  position: relative;
}

.touch-target::before {
  content: '';
  position: absolute;
  top: -8px;
  right: -8px;
  bottom: -8px;
  left: -8px;
  /* Expands touch area without visual change */
}
```

**Spacing Between Targets:**

```css
/* Minimum 8px gutter between touch targets */
.button-group {
  display: flex;
  gap: 0.5rem; /* 8px minimum */
}

.nav-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem; /* 12px for better UX */
}
```

### 5.3 Mobile Input Optimization

**HTML5 Input Types:**

```html
<!-- Triggers numeric keyboard -->
<input type="tel" inputmode="numeric" pattern="[0-9]*">

<!-- Triggers email keyboard with @ -->
<input type="email" autocomplete="email">

<!-- Triggers URL keyboard with .com -->
<input type="url" autocomplete="url">

<!-- Triggers date picker -->
<input type="date">

<!-- Triggers time picker -->
<input type="time">

<!-- Search with optimized keyboard -->
<input type="search" inputmode="search">
```

**Autocomplete Attributes:**

```html
<form>
  <input type="text" autocomplete="name">
  <input type="email" autocomplete="email">
  <input type="tel" autocomplete="tel">
  <input type="text" autocomplete="address-line1">
  <input type="text" autocomplete="postal-code">
  <input type="text" autocomplete="cc-number">
</form>
```

### 5.4 Form Usability

**Mobile-Optimized Forms:**

```html
<form class="mobile-form">
  <!-- Top-aligned labels for better vertical space -->
  <div class="form-field">
    <label for="name">Full Name</label>
    <input 
      type="text" 
      id="name" 
      autocomplete="name"
      required>
  </div>
  
  <div class="form-field">
    <label for="email">Email</label>
    <input 
      type="email" 
      id="email" 
      autocomplete="email"
      required>
  </div>
  
  <button type="submit">Submit</button>
</form>
```

```css
.mobile-form {
  max-width: 100%;
}

.form-field {
  display: flex;
  flex-direction: column;
  margin-bottom: 1.5rem;
}

.form-field label {
  margin-bottom: 0.5rem;
  font-weight: 600;
}

.form-field input,
.form-field textarea,
.form-field select {
  min-height: 44px;
  padding: 0.75rem;
  font-size: 16px; /* Prevents zoom on iOS */
  border: 1px solid #ccc;
  border-radius: 4px;
}

/* Prevent iOS zoom on focus */
@media (max-width: 767px) {
  input, textarea, select {
    font-size: 16px !important;
  }
}
```

---

## 6. Advanced Responsive Techniques

### 6.1 Responsive Typography Scale

**Modular Scale with Fluid Sizing:**

```css
:root {
  /* Base size */
  --text-base-size: clamp(1rem, 0.9rem + 0.5vw, 1.125rem);
  
  /* Scale ratio: 1.25 (Major Third) on mobile, 1.333 (Perfect Fourth) on desktop */
  --text-scale-ratio: clamp(1.25, 1.2vw, 1.333);
  
  /* Calculated sizes */
  --text-xs: calc(var(--text-base-size) / var(--text-scale-ratio) / var(--text-scale-ratio));
  --text-sm: calc(var(--text-base-size) / var(--text-scale-ratio));
  --text-md: var(--text-base-size);
  --text-lg: calc(var(--text-base-size) * var(--text-scale-ratio));
  --text-xl: calc(var(--text-base-size) * var(--text-scale-ratio) * var(--text-scale-ratio));
  --text-2xl: calc(var(--text-base-size) * var(--text-scale-ratio) * var(--text-scale-ratio) * var(--text-scale-ratio));
}
```

### 6.2 Responsive Spacing System

```css
:root {
  /* Fluid spacing scale */
  --space-3xs: clamp(0.25rem, 0.23rem + 0.11vw, 0.31rem);
  --space-2xs: clamp(0.5rem, 0.46rem + 0.22vw, 0.63rem);
  --space-xs: clamp(0.75rem, 0.68rem + 0.33vw, 0.94rem);
  --space-sm: clamp(1rem, 0.91rem + 0.43vw, 1.25rem);
  --space-md: clamp(1.5rem, 1.37rem + 0.65vw, 1.88rem);
  --space-lg: clamp(2rem, 1.83rem + 0.87vw, 2.5rem);
  --space-xl: clamp(3rem, 2.74rem + 1.3vw, 3.75rem);
  --space-2xl: clamp(4rem, 3.65rem + 1.74vw, 5rem);
  --space-3xl: clamp(6rem, 5.48rem + 2.61vw, 7.5rem);
}
```

### 6.3 Responsive Grid Systems

**Auto-Fit Grid:**

```css
.grid-auto-fit {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(250px, 100%), 1fr));
  gap: var(--space-md);
}
```

**Auto-Fill Grid:**

```css
.grid-auto-fill {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: var(--space-md);
}
```

**Named Grid Areas:**

```css
.page-layout {
  display: grid;
  gap: var(--space-md);
  grid-template-areas:
    "header"
    "main"
    "sidebar"
    "footer";
}

@media (min-width: 768px) {
  .page-layout {
    grid-template-areas:
      "header header"
      "main sidebar"
      "footer footer";
    grid-template-columns: 2fr 1fr;
  }
}

@media (min-width: 1024px) {
  .page-layout {
    grid-template-areas:
      "header header header"
      "sidebar main main"
      "footer footer footer";
    grid-template-columns: 250px 1fr 1fr;
  }
}

.header { grid-area: header; }
.main { grid-area: main; }
.sidebar { grid-area: sidebar; }
.footer { grid-area: footer; }
```

### 6.4 Responsive Navigation Patterns

**Mobile Menu (Hamburger):**

```html
<nav class="main-nav">
  <button class="menu-toggle" aria-label="Toggle menu">
    <span></span>
    <span></span>
    <span></span>
  </button>
  
  <ul class="nav-list">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```

```css
.main-nav {
  position: relative;
}

.menu-toggle {
  display: flex;
  flex-direction: column;
  gap: 4px;
  background: none;
  border: none;
  padding: 0.5rem;
  cursor: pointer;
}

.menu-toggle span {
  display: block;
  width: 24px;
  height: 3px;
  background: currentColor;
  transition: transform 0.3s;
}

.nav-list {
  position: fixed;
  top: 0;
  right: -100%;
  width: 80%;
  max-width: 300px;
  height: 100vh;
  background: white;
  padding: 2rem;
  transition: right 0.3s;
  z-index: 1000;
}

.nav-list.active {
  right: 0;
}

@media (min-width: 768px) {
  .menu-toggle {
    display: none;
  }
  
  .nav-list {
    position: static;
    display: flex;
    width: auto;
    height: auto;
    padding: 0;
    gap: 2rem;
  }
}
```

---

## 7. Testing & Debugging

### 7.1 Responsive Testing Checklist

**Viewport Sizes to Test:**
- 320px (iPhone SE)
- 375px (iPhone 12/13)
- 390px (iPhone 14)
- 414px (iPhone Plus)
- 768px (iPad Portrait)
- 1024px (iPad Landscape)
- 1280px (Laptop)
- 1920px (Desktop)

**Browser DevTools:**

```css
/* Debug helper: Show breakpoint in corner */
body::before {
  content: 'XS';
  position: fixed;
  bottom: 0;
  right: 0;
  padding: 0.5rem;
  background: red;
  color: white;
  font-size: 12px;
  z-index: 9999;
}

@media (min-width: 640px) {
  body::before { content: 'SM'; background: orange; }
}

@media (min-width: 768px) {
  body::before { content: 'MD'; background: yellow; color: black; }
}

@media (min-width: 1024px) {
  body::before { content: 'LG'; background: green; }
}

@media (min-width: 1280px) {
  body::before { content: 'XL'; background: blue; }
}

@media (min-width: 1536px) {
  body::before { content: '2XL'; background: purple; }
}
```

### 7.2 Common Responsive Issues

**Horizontal Scroll Prevention:**

```css
/* Prevent horizontal overflow */
html, body {
  overflow-x: hidden;
  max-width: 100vw;
}

/* Better alternative: Use overflow-wrap */
* {
  overflow-wrap: break-word;
}

/* Ensure images don't overflow */
img {
  max-width: 100%;
  height: auto;
}
```

**Fixed Width Elements:**

```css
/* ❌ Bad: Fixed width */
.container {
  width: 1200px;
}

/* ✅ Good: Max width with fluid fallback */
.container {
  width: min(90%, 1200px);
  margin-inline: auto;
}
```

---

## 8. AI Usage Workflow

When generating or refactoring code for responsiveness, follow this systematic checklist:

### Step 1: Start Mobile-First
```css
/* Write base styles without media queries */
.component {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  gap: 1rem;
}
```

### Step 2: Apply Fluidity
```css
/* Replace fixed values with fluid alternatives */
.component {
  display: flex;
  flex-direction: column;
  padding: clamp(1rem, 2vw, 2rem);
  gap: var(--space-md);
  max-width: 100%;
}
```

### Step 3: Define Breakpoints
```css
/* Add progressive enhancements */
@media (min-width: 768px) {
  .component {
    flex-direction: row;
    padding: clamp(1.5rem, 3vw, 3rem);
  }
}
```

### Step 4: Componentize with Container Queries
```css
/* Make component container-aware */
.component-wrapper {
  container-type: inline-size;
}

@container (min-width: 600px) {
  .component {
    flex-direction: row;
  }
}
```

### Step 5: Audit Interactions
```css
/* Ensure hover states don't break touch */
@media (hover: hover) and (pointer: fine) {
  .button:hover {
    background: var(--hover-bg);
  }
}

/* Touch-friendly active states */
.button:active {
  transform: scale(0.98);
}
```

### Step 6: Verify Layout
- Check for horizontal overflow
- Test at all standard breakpoints
- Verify touch target sizes (44×44px minimum)
- Test with browser zoom at 200%
- Validate with screen readers

---

## 9. Best Practices Summary

### ✅ DO

| Practice | Example |
|----------|---------|
| **Use Mobile-First** | Start with base styles, add `@media (min-width)` |
| **Fluid Typography** | `font-size: clamp(1rem, 2vw, 1.5rem)` |
| **Relative Units** | `padding: 1.5rem` instead of `padding: 24px` |
| **Container Queries** | Use for component-level responsiveness |
| **Semantic HTML** | `<nav>`, `<article>`, `<section>` |
| **Accessible Touch Targets** | Minimum 44×44px |
| **Responsive Images** | Use `srcset` and `sizes` |
| **System Fonts** | Load custom fonts progressively |
| **Vertical Scrolling** | Natural, expected behavior |
| **Test Real Devices** | Emulators don't catch everything |

### ❌ DON'T

| Anti-Pattern | Why It's Bad |
|--------------|--------------|
| **Fixed Pixel Widths** | Breaks on different screen sizes |
| **Desktop-First** | Harder to scale down, worse performance |
| **Magic Numbers** | `width: 347px` - unclear intent |
| **Viewport Units for Text** | Can become unreadable (too small/large) |
| **Horizontal Scrolling** | Terrible UX on mobile |
| **`user-scalable=no`** | Breaks accessibility |
| **Tiny Touch Targets** | Frustrating on mobile |
| **Hover-Only Interactions** | Doesn't work on touch devices |
| **Ignoring Landscape** | Mobile landscape is a real use case |
| **Fixed Positioning Overuse** | Can cover content on small screens |

---

## 10. Quick Reference

### Media Query Syntax

```css
/* Viewport width */
@media (min-width: 768px) { }
@media (max-width: 767px) { }

/* Viewport height */
@media (min-height: 600px) { }

/* Orientation */
@media (orientation: landscape) { }
@media (orientation: portrait) { }

/* Pixel density */
@media (-webkit-min-device-pixel-ratio: 2) { }
@media (min-resolution: 192dpi) { }

/* Hover capability */
@media (hover: hover) { }
@media (hover: none) { }

/* Pointer precision */
@media (pointer: fine) { } /* Mouse */
@media (pointer: coarse) { } /* Touch */

/* Prefers reduced motion */
@media (prefers-reduced-motion: reduce) { }

/* Dark mode */
@media (prefers-color-scheme: dark) { }

/* Combined queries */
@media (min-width: 768px) and (orientation: landscape) { }
```

### Container Query Syntax

```css
/* Define container */
.container {
  container-type: inline-size; /* or 'size' or 'normal' */
  container-name: sidebar; /* optional */
}

/* Query container */
@container (min-width: 400px) { }
@container sidebar (min-width: 400px) { }

/* Container query units */
.element {
  width: 50cqw;  /* 50% of container width */
  height: 30cqh; /* 30% of container height */
  font-size: 5cqi; /* 5% of container inline size */
  padding: 2cqb; /* 2% of container block size */
}
```

---

## 11. Resources & Tools

### Testing Tools
- **Chrome DevTools:** Device emulation, responsive mode
- **Firefox Responsive Design Mode:** Advanced viewport testing
- **BrowserStack:** Real device testing
- **Responsively App:** Test multiple viewports simultaneously

### Validation
- **WAVE:** Accessibility checker
- **Lighthouse:** Performance and accessibility audit
- **Can I Use:** Browser support checker

### Generators
- **Utopia:** Fluid type and space calculators
- **Modern Fluid Typography:** CSS clamp() generator
- **CSS Grid Generator:** Visual grid builder

---

This comprehensive guide provides everything needed to build truly responsive, device-agnostic interfaces that work beautifully across all screen sizes and contexts.
