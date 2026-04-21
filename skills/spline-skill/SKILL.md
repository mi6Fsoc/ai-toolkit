---
name: spline-3d-integration
description: "Use when adding interactive 3D scenes from Spline.design to web projects. Covers embedding methods (React, Next.js, vanilla JS), the @splinetool/ runtime API for programmatic control (events, variables, animations, camera), performance optimization, mobile fallbacks, and common integration problems like scroll hijacking, layout shift, GPU fallbacks, and watermark removal."
---

# Spline 3D Integration Skill

Master guide for embedding interactive 3D scenes from [Spline.design](https://spline.design) into web projects.

---

## What Is Spline?

Spline is a browser-based 3D design tool — think Figma, but for 3D. Designers create interactive 3D scenes (objects, materials, animations, physics, events) in the Spline editor, then export them for the web via a hosted `.splinecode` file URL.

---

## STEP 1 — Identify the Stack

Before writing any code, check the existing project files to determine the framework.

| Stack | Method |
|---|---|
| Vanilla HTML/JS | `<spline-viewer>` web component OR `@splinetool/runtime` |
| React / Vite | `@splinetool/react-spline` |
| Next.js | `@splinetool/react-spline/next` |
| Vue | `@splinetool/vue-spline` |
| iframe (Webflow, Notion, etc.) | Public URL iframe |

---

## STEP 2 — Get the Scene URL

The user must go to their Spline editor → **Export** → **Code Export** → copy the `prod.spline.design` URL:

```
https://prod.spline.design/XXXXXXXXXXXXXXXX/scene.splinecode
```

**Before copying the URL, tell the user to check Play Settings:**
- ✅ Toggle **Hide Background** ON if the site has a dark or custom background
- ✅ Toggle **Hide Spline Logo** ON if they have a paid plan
- ✅ Set **Geometry Quality** to Performance for faster load
- ✅ Disable **Page Scroll**, **Zoom**, **Pan** if those aren't needed (reduces hijacking risk)
- ✅ Click **Generate Draft** or **Promote to Production** after any settings change — the URL does NOT auto-update

---

## STEP 3 — Integrate

Once you have the stack and the scene URL, follow the appropriate section below. Always read the **Common Problems** section before finishing integration — it contains critical gotchas that will otherwise only surface in production.

---
---

# Vanilla JS / HTML Integration

Two methods depending on how much control you need.

---

## Method A — Web Component (Recommended for most cases)

No npm required. Just add to HTML. Supports lazy loading, transparent backgrounds, and mouse interactivity.

```html
<!-- In <head> — loads the web component -->
<script type="module" src="https://unpkg.com/@splinetool/viewer/build/spline-viewer.js"></script>

<!-- Basic embed -->
<spline-viewer url="https://prod.spline.design/REPLACE_ME/scene.splinecode"></spline-viewer>

<!-- With mouse-following interactivity (e.g. cursor-tracking robots) -->
<spline-viewer
  url="https://prod.spline.design/REPLACE_ME/scene.splinecode"
  events-target="global">
</spline-viewer>

<!-- Transparent background -->
<spline-viewer
  url="https://prod.spline.design/REPLACE_ME/scene.splinecode"
  background="transparent">
</spline-viewer>
```

---

## Method B — Runtime API (When you need programmatic control)

Use when you need to manipulate objects, trigger animations, or respond to events from your own JS.

Install:
```bash
npm install @splinetool/runtime
```

Or via CDN (no install):
```html
<script type="module">
  import { Application } from 'https://unpkg.com/@splinetool/runtime@latest/build/runtime.module.js';
  // ... rest of your code
</script>
```

Basic usage:
```js
import { Application } from '@splinetool/runtime';

const canvas = document.getElementById('canvas3d');
const spline = new Application(canvas);

spline.load('https://prod.spline.design/REPLACE_ME/scene.splinecode').then(() => {
  console.log('Scene loaded');
});
```

With object interaction:
```js
spline.load(sceneUrl).then(() => {
  const obj = spline.findObjectByName('Cube');
  // or by ID: spline.findObjectById('uuid-here')

  obj.position.x += 50;
  obj.rotation.y += Math.PI / 4; // NOTE: radians, NOT degrees
  obj.scale.x = 2;
});
```

With event listeners:
```js
spline.load(sceneUrl).then(() => {
  spline.addEventListener('mouseDown', (e) => {
    console.log('Clicked:', e.target.name);
  });
});
```

Trigger animations programmatically:
```js
spline.load(sceneUrl).then(() => {
  const obj = spline.findObjectByName('MyObject');
  obj.emitEvent('mouseHover');       // forward
  obj.emitEventReverse('mouseHover'); // reverse
});
```

---

## Full-Page Background Setup (Vanilla)

The most common use case — Spline scene behind all content.

```html
<!DOCTYPE html>
<html>
<head>
  <script type="module" src="https://unpkg.com/@splinetool/viewer/build/spline-viewer.js"></script>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      /* DO NOT add overflow: hidden here — it will break page scroll */
      position: relative;
    }

    .spline-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      /* pointer-events: none — use this if scene is decorative only */
      /* pointer-events: all — use this if you want mouse interaction */
      pointer-events: all;
    }

    .content {
      position: relative;
      z-index: 1;
      /* Make sure content elements don't get blocked by the 3D scene */
    }

    /* Fallback shown while Spline loads or if it fails */
    .spline-fallback {
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      z-index: 0;
      background: #0a0a0a; /* match your site's base color */
      display: none; /* hidden by default, shown via JS if needed */
    }
  </style>
</head>
<body>
  <!-- Fallback (shown if Spline fails to load) -->
  <div class="spline-fallback" id="spline-fallback"></div>

  <!-- Spline background -->
  <div class="spline-bg">
    <spline-viewer
      url="https://prod.spline.design/REPLACE_ME/scene.splinecode"
      events-target="global"
      style="width:100%; height:100%;">
    </spline-viewer>
  </div>

  <!-- Your website content -->
  <div class="content">
    <h1>Your Content Here</h1>
  </div>

  <script>
    // Show fallback if Spline hasn't loaded after 8 seconds
    setTimeout(() => {
      const viewer = document.querySelector('spline-viewer');
      if (!viewer || !viewer.shadowRoot) {
        document.getElementById('spline-fallback').style.display = 'block';
      }
    }, 8000);

    // Skip Spline entirely on low-end mobile to save battery + performance
    if (window.innerWidth < 768 || navigator.hardwareConcurrency <= 2) {
      document.querySelector('.spline-bg').style.display = 'none';
      document.getElementById('spline-fallback').style.display = 'block';
    }
  </script>
</body>
</html>
```

---

## Available Event Types (Vanilla)

| Event | Use case |
|---|---|
| `mouseDown` | Click/tap on object |
| `mouseUp` | Release after click |
| `mouseHover` | Cursor enters object area |
| `mousePress` | Holding click down |
| `keyDown` | Key pressed |
| `keyUp` | Key released |
| `start` | Scene has loaded and started |
| `scroll` | Page scrolled |

---

## Preloading (Reduces Perceived Load Time)

Add to `<head>` to start fetching the scene file before scripts run:

```html
<link rel="preload" href="https://prod.spline.design/REPLACE_ME/scene.splinecode" as="fetch" crossorigin>
```

---
---

# React / Next.js / Vue Integration

---

## React / Vite

Install:
```bash
npm install @splinetool/react-spline
```

Basic:
```jsx
import Spline from '@splinetool/react-spline';

export default function App() {
  return (
    <div style={{ width: '100%', height: '100vh' }}>
      <Spline scene="https://prod.spline.design/REPLACE_ME/scene.splinecode" />
    </div>
  );
}
```

With object interaction + event listeners:
```jsx
import { useRef } from 'react';
import Spline from '@splinetool/react-spline';

export default function App() {
  const splineRef = useRef();

  function onLoad(splineApp) {
    splineRef.current = splineApp;
  }

  function triggerAnimation() {
    splineRef.current.emitEvent('mouseHover', 'Cube');
  }

  function onSplineEvent(e) {
    console.log('Object interacted:', e.target.name);
  }

  return (
    <div>
      <Spline
        scene="https://prod.spline.design/REPLACE_ME/scene.splinecode"
        onLoad={onLoad}
        onMouseDown={onSplineEvent}
      />
      <button onClick={triggerAnimation}>Trigger</button>
    </div>
  );
}
```

**Lazy loading (recommended for performance):**
```jsx
import { lazy, Suspense } from 'react';

const Spline = lazy(() => import('@splinetool/react-spline'));

export default function Hero() {
  return (
    <Suspense fallback={<div style={{ background: '#0a0a0a', width: '100%', height: '100vh' }} />}>
      <Spline scene="https://prod.spline.design/REPLACE_ME/scene.splinecode" />
    </Suspense>
  );
}
```

---

## Next.js

Install:
```bash
npm install @splinetool/react-spline
```

**Use the `/next` import** for SSR support + auto blurred placeholder:
```jsx
import Spline from '@splinetool/react-spline/next';

export default function Page() {
  return (
    <Spline scene="https://prod.spline.design/REPLACE_ME/scene.splinecode" />
  );
}
```

**With dynamic import (if you get hydration errors):**
```jsx
import dynamic from 'next/dynamic';

const Spline = dynamic(() => import('@splinetool/react-spline/next'), {
  ssr: false,
  loading: () => <div style={{ background: '#0a0a0a', width: '100%', height: '100vh' }} />
});

export default function Page() {
  return <Spline scene="https://prod.spline.design/REPLACE_ME/scene.splinecode" />;
}
```

---

## Vue

Install:
```bash
npm install @splinetool/vue-spline
```

```vue
<template>
  <Spline
    scene="https://prod.spline.design/REPLACE_ME/scene.splinecode"
    @spline-loaded="onLoaded"
    @mouseDown="onClick"
  />
</template>

<script>
import Spline from '@splinetool/vue-spline';

export default {
  components: { Spline },
  methods: {
    onLoaded(spline) {
      const obj = spline.findObjectByName('Cube');
      obj.position.x += 10; // NOTE: radians for rotation, not degrees
    },
    onClick(e) {
      console.log('Clicked:', e.target.name);
    }
  }
}
</script>
```

---

## Full-Page Background (React)

```jsx
import Spline from '@splinetool/react-spline';
import { useState } from 'react';

export default function HeroSection() {
  const [loaded, setLoaded] = useState(false);

  // Skip Spline on mobile / low-end devices
  const isMobile = typeof window !== 'undefined' && window.innerWidth < 768;
  const isLowEnd = typeof navigator !== 'undefined' && navigator.hardwareConcurrency <= 2;

  return (
    <div style={{ position: 'relative', width: '100vw', height: '100vh' }}>

      {/* Fallback background — always rendered, hidden once Spline loads */}
      <div style={{
        position: 'absolute', inset: 0,
        background: '#0a0a0a',
        zIndex: 0,
        opacity: loaded ? 0 : 1,
        transition: 'opacity 0.5s ease'
      }} />

      {/* Spline scene — only load on capable devices */}
      {!isMobile && !isLowEnd && (
        <Spline
          scene="https://prod.spline.design/REPLACE_ME/scene.splinecode"
          onLoad={() => setLoaded(true)}
          style={{
            position: 'absolute',
            top: 0, left: 0,
            width: '100%', height: '100%',
            zIndex: 0
          }}
        />
      )}

      {/* Content sits on top */}
      <div style={{ position: 'relative', zIndex: 1 }}>
        <h1>Your Content Here</h1>
      </div>

    </div>
  );
}
```

---

## React Prop Reference

| Prop | Type | Description |
|---|---|---|
| `scene` | string | Scene URL (required) |
| `onLoad` | function | Called with splineApp when loaded |
| `onMouseDown` | function | Mouse/touch down on object |
| `onMouseUp` | function | Mouse/touch up |
| `onMouseHover` | function | Hover over object |
| `onKeyDown` | function | Key pressed |
| `onKeyUp` | function | Key released |
| `onStart` | function | Scene started |
| `onScroll` | function | Scroll event |
| `style` | object | CSS styles for the canvas |
| `className` | string | CSS class |

---
---

# Performance & Mobile Optimization

Spline scenes are WebGL — they run on the GPU. A poorly optimized scene will tank your PageSpeed score, lag on mid-range devices, and drain mobile batteries. Treat them like video files, not images.

---

## Before You Even Integrate — Check Scene Size

**Tell the user to check their scene file size before giving you the URL.**

- Under ~3MB = generally fine
- 3–10MB = usable but optimize where possible
- Over 10MB = serious problem, needs optimization or a different approach
- Over 20MB = do not embed as live 3D — export as video instead

To check: in Spline editor → Export → Code Export → the file size is shown before generating the URL.

**If the scene is too heavy, tell the user to:**
1. In Export → Play Settings, set **Geometry Quality** to "Performance"
2. Reduce subdivision levels (1 is usually enough, max 2)
3. Delete objects that are hidden or never visible
4. Remove unused textures and images
5. Use fewer than 3 lights — prefer Matcap materials for reflective effects (fakes reflections without GPU cost)
6. Merge objects that share the same material

---

## Optimization Checklist (Pre-Integration)

Go through these before writing any embed code:

- [ ] Scene file size is under 10MB
- [ ] Geometry Quality set to "Performance" in Play Settings
- [ ] Background hidden if site has its own background color
- [ ] Disabled: Page Scroll, Zoom, Pan (in Play Settings) unless explicitly needed
- [ ] Max 1–2 Spline embeds on the page (never more than 3)
- [ ] Less than 3 lights in the scene
- [ ] No high-res textures unless essential

---

## Loading Strategy

### 1. Preload the scene file
Add to `<head>` to start fetching before scripts execute:
```html
<link rel="preload" href="https://prod.spline.design/REPLACE_ME/scene.splinecode" as="fetch" crossorigin>
```

### 2. Show a fallback while loading
Never leave users staring at a blank space. Always render a background color or static image as a placeholder:

```css
.spline-wrapper {
  background: #0a0a0a; /* your site's bg color — shows instantly */
  width: 100%;
  height: 100vh;
}
```

### 3. Lazy load (React)
Don't load Spline until it's needed:
```jsx
const Spline = lazy(() => import('@splinetool/react-spline'));
```

### 4. Intersection Observer (load only when visible)
For Spline scenes below the fold:
```js
const observer = new IntersectionObserver((entries) => {
  if (entries[0].isIntersecting) {
    loadSplineScene(); // only load when user scrolls to it
    observer.disconnect();
  }
});
observer.observe(document.getElementById('spline-section'));
```

---

## Mobile Strategy

Spline scenes are GPU-intensive. On mobile they:
- Drain battery quickly
- Lag on any device without a dedicated GPU
- Can cause the browser tab to crash on lower-end Android

**Always implement one of these strategies:**

### Option A — Skip entirely on mobile (recommended for hero backgrounds)
```js
if (window.innerWidth < 768) {
  // Don't load Spline — show static background instead
  document.querySelector('.spline-wrapper').style.background = 'url(fallback.jpg) center/cover';
}
```

### Option B — Hardware concurrency check
```js
// navigator.hardwareConcurrency = number of CPU cores
// Low core count = likely a low-end device
if (navigator.hardwareConcurrency <= 2 || window.innerWidth < 768) {
  // Skip Spline, use fallback
}
```

### Option C — Export as video for mobile
For decorative/non-interactive scenes: record the animation in Spline as MP4, serve that on mobile instead. Users get the visual, no GPU cost.

```js
const isMobile = window.innerWidth < 768;

if (isMobile) {
  // Show video
  document.getElementById('spline-video').style.display = 'block';
} else {
  // Load Spline
  loadSpline();
}
```

---

## Core Web Vitals (LCP / CLS)

Spline scenes are almost always the **Largest Contentful Paint** element, which means they directly affect your Google score.

### Preventing Layout Shift (CLS)
The canvas loads after HTML, causing the page to jump. Fix it by pre-allocating space:

```css
canvas#canvas3d {
  width: 100%;
  height: 100vh;
  /* This tells the browser to reserve this space before the scene loads */
  contain: strict;
}
```

Or for the web component:
```html
<spline-viewer
  url="..."
  style="width: 100%; height: 100vh; display: block;">
</spline-viewer>
```

### Lighthouse note
Lighthouse often cannot calculate a performance score at all when a Spline scene is the dominant above-the-fold element. This is a known Lighthouse limitation, not necessarily a site problem. Use WebPageTest or Chrome DevTools instead for real profiling.

---

## When NOT to Use a Live 3D Embed

Sometimes a Spline embed is the wrong tool. Use a video or GIF instead when:

- The animation doesn't respond to user input (no mouse tracking, no clicks)
- The scene file is over 15MB
- Your target audience is primarily mobile
- You need the page to score above 80 on PageSpeed

**How to export as video from Spline:**
In Spline editor → Export → Video → record your animation → compress with HandBrake → host on GitHub or a CDN → embed as `<video autoplay loop muted playsinline>`

---
---

# Common Problems & Debugging

These are the real-world issues that only surface after integration. Read this before finishing any Spline implementation.

---

## 🚨 Critical Gotchas (Will Break Your Site)

---

### 1. Scroll Hijacking — Page Won't Scroll

**What happens:** After adding Spline, the whole page stops scrolling. Users are stuck.

**Why:** Spline's auto-generated vanilla JS exports inject `overflow: hidden` into `<body>` CSS by default. This is baked into their generated code.

**Fix:**
```css
/* Add this to your CSS — overrides Spline's injection */
body {
  overflow: auto !important;
}
```

Or in Play Settings (Spline editor → Export → Play Settings), **disable "Page Scroll"** before generating the URL. This removes the overflow rule from the output.

**Also check:** If using the Runtime API and you embedded the generated `index.html` files, open them and manually remove the `overflow: hidden` line from the `<style>` block.

---

### 2. White Box Behind the 3D Scene

**What happens:** Your dark/transparent website has a white rectangle where the Spline scene is.

**Why:** The background color is set to white by default in Spline's export settings.

**Fix:**
1. In Spline editor → Export → Play Settings → toggle **Hide Background** ON
2. Click **Generate Draft** or **Promote to Production** — the URL does NOT auto-update with new settings
3. Copy the new URL

For the web component you can also override inline:
```html
<spline-viewer url="..." background="transparent"></spline-viewer>
```

---

### 3. Spline Scene Intermittently Fails to Load

**What happens:** Page loads fine sometimes, blank or broken other times. Feels random.

**Why:** The `prod.spline.design` CDN occasionally has latency or drops requests. There's no built-in retry or error handling.

**Fix — add a timeout fallback:**
```js
const TIMEOUT_MS = 8000;

const timeoutId = setTimeout(() => {
  // Spline didn't load in time — show fallback
  document.getElementById('spline-fallback').style.display = 'block';
  document.querySelector('.spline-wrapper').style.display = 'none';
}, TIMEOUT_MS);

// If using Runtime API, clear the timeout on successful load:
spline.load(sceneUrl).then(() => {
  clearTimeout(timeoutId);
});
```

**Long-term fix:** Download the `.splinecode` file and self-host it on your own CDN. This eliminates the third-party dependency entirely and also fixes CORS issues.

---

### 4. Scene Looks Fine on Mac, Lags on Everything Else

**What happens:** Buttery smooth on MacBook Pro or M-chip Mac. Completely broken — laggy, stuttering, sometimes crashing — on mid-range Windows laptops or Android phones.

**Why:** Spline uses WebGL which runs on the GPU. Apple Silicon Macs have exceptional GPU performance. Most Windows laptops and Android devices do not have dedicated GPUs.

**Fix — detect capability before loading:**
```js
function shouldLoadSpline() {
  const isMobile = window.innerWidth < 768;
  const isLowEnd = navigator.hardwareConcurrency <= 2;

  // Optional: test WebGL support
  const canvas = document.createElement('canvas');
  const gl = canvas.getContext('webgl2') || canvas.getContext('webgl');
  const noWebGL = !gl;

  return !isMobile && !isLowEnd && !noWebGL;
}

if (shouldLoadSpline()) {
  loadSplineScene();
} else {
  showFallback();
}
```

---

### 5. Layout Shift — Page Jumps When Scene Loads

**What happens:** User sees the page layout, then everything shifts/jumps when the 3D scene loads in.

**Why:** The canvas has no reserved height before loading, so the browser doesn't know how much space to allocate. HTML renders → space collapses → scene loads → everything jumps. This tanks your CLS (Cumulative Layout Shift) Core Web Vitals score.

**Fix — pre-allocate space:**
```css
spline-viewer, canvas.spline-canvas {
  display: block;
  width: 100%;
  height: 100vh; /* or whatever your target height is */
  contain: strict; /* tells browser to reserve this space */
}
```

For `position: fixed` backgrounds this is less of an issue, but for inline scenes it's critical.

---

### 6. Rotation Values Are Radians, Not Degrees

**What happens:** You try to rotate an object to 90 degrees. It barely moves or spins wildly.

**Why:** Spline's runtime API uses **radians**, not degrees. 90 degrees = `Math.PI / 2`. 180 degrees = `Math.PI`.

**Fix:**
```js
// WRONG
obj.rotation.y = 90;

// CORRECT
obj.rotation.y = Math.PI / 2; // 90 degrees
obj.rotation.y = Math.PI;     // 180 degrees
obj.rotation.y = Math.PI * 2; // 360 degrees (full rotation)

// Helper function to use if you prefer degrees:
const toRad = (deg) => deg * (Math.PI / 180);
obj.rotation.y = toRad(90);
```

---

### 7. 3D Scene Blocks Clicks on Buttons / Links

**What happens:** Buttons, CTAs, or nav links that overlap with the Spline scene don't respond to clicks.

**Why:** The Spline canvas sits on top and captures all pointer events.

**Fix:** Add `pointer-events: none` to the Spline wrapper if it's decorative (no interaction needed):
```css
.spline-wrapper {
  pointer-events: none; /* scene won't capture any clicks */
}
```

If you need BOTH mouse interaction on the scene AND clickable content on top:
```css
.spline-wrapper {
  pointer-events: all; /* scene gets mouse events */
}

.content-overlay {
  position: relative;
  z-index: 10;
  pointer-events: all; /* content also gets mouse events */
}
```

Note: When both have `pointer-events: all`, the topmost element (by z-index) wins. Make sure your content div has a higher z-index than the Spline wrapper.

---

### 8. Spline Watermark Visible (Free Plan)

**What happens:** A small "Built with Spline" logo appears in the corner.

**Options:**

**Option A — Upgrade to a Spline paid plan.** Then in Export → Play Settings → toggle "Hide Spline Logo" ON.

**Option B — CSS overlay (free plan workaround):**
```css
/* Hides the watermark via CSS — targets the shadow DOM */
spline-viewer::part(logo) {
  display: none;
}

/* Fallback if the above doesn't work */
spline-viewer {
  --spline-viewer-logo-display: none;
}
```

Note: CSS-based hiding may break with Spline updates. The paid plan is the reliable solution.

---

### 9. CORS Error When Loading Scene

**What happens:** Scene fails to load with a CORS error in the console.

**Why:** Browser security blocks cross-origin requests in some environments (especially localhost dev servers with certain configurations).

**Fix — self-host the scene file:**
1. In Spline → Export → Code Export → click the download icon next to the URL
2. Download the `.splinecode` file
3. Host it on your own server or CDN (same origin as your site)
4. Update the URL in your embed code to point to your hosted version

---

### 10. Next.js Hydration Error

**What happens:** React hydration mismatch error in Next.js when the Spline component is included.

**Why:** Spline renders on the client only (it needs the browser's WebGL), but Next.js tries to render on the server too.

**Fix:**
```jsx
import dynamic from 'next/dynamic';

// ssr: false tells Next.js not to render this on the server
const Spline = dynamic(() => import('@splinetool/react-spline/next'), {
  ssr: false,
  loading: () => <div style={{ background: '#0a0a0a', height: '100vh' }} />
});
```

---

### 11. Scene URL Not Reflecting Latest Changes

**What happens:** You updated the scene in the Spline editor, but the embed still shows the old version.

**Why:** The `prod.spline.design` URL is a snapshot. It does **not** auto-update when you make changes.

**Fix:** Every time you make changes in the Spline editor, you must:
1. Go to Export → Code Export
2. Click **"Promote to Production"** (or "Generate Draft" for a new draft URL)
3. The existing prod URL will now serve the updated scene — no need to change the URL in your code

---

## Quick Diagnostic Table

| Symptom | Most Likely Cause | Fix |
|---|---|---|
| Page won't scroll | `overflow: hidden` injected by Spline | Add `body { overflow: auto !important }` or disable Page Scroll in Play Settings |
| White box behind scene | Background not hidden | Play Settings → Hide Background → regenerate URL |
| Loads sometimes, blank others | CDN flakiness | Add timeout fallback; consider self-hosting |
| Smooth on Mac, laggy elsewhere | GPU performance gap | Add hardware detection, skip on low-end |
| Page jumps on load | No reserved space (CLS) | Set explicit height on canvas/viewer element |
| Rotations look wrong | Degrees vs radians | Use `Math.PI / 180 * degrees` |
| Buttons not clickable | Canvas capturing pointer events | Add `pointer-events: none` to Spline wrapper |
| Watermark visible | Free plan | Upgrade or use CSS override |
| CORS error | Cross-origin loading | Self-host the `.splinecode` file |
| Hydration error (Next.js) | SSR conflict | Use `dynamic(() => import(...), { ssr: false })` |
| Old scene still showing | Didn't promote to production | Click "Promote to Production" in Spline editor |

---
---

# Working Examples

## Example: Production-Ready Vanilla Embed

Minimal production-ready Spline embed — vanilla HTML/JS. Features: transparent background, mobile skip, GPU check, load timeout fallback, no scroll hijacking.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Spline Background</title>

  <!-- Preload scene for faster perceived load -->
  <link rel="preload" href="https://prod.spline.design/REPLACE_ME/scene.splinecode" as="fetch" crossorigin>

  <!-- Load Spline viewer web component -->
  <script type="module" src="https://unpkg.com/@splinetool/viewer/build/spline-viewer.js"></script>

  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      /* IMPORTANT: Do NOT set overflow: hidden here.
         Spline's generated code tries to add this — it will break page scroll.
         If it appears anywhere in your CSS, remove it. */
      overflow: auto;
      background: #0a0a0a;
    }

    /* Spline background wrapper */
    .spline-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;

      /* Reserve space to prevent layout shift */
      contain: strict;

      /* Fade in when loaded */
      opacity: 0;
      transition: opacity 0.6s ease;
    }

    .spline-bg.loaded {
      opacity: 1;
    }

    /* Fallback shown before load or on fallback devices */
    .spline-fallback {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      background: #0a0a0a;
      /* Optional: background image fallback
      background: url('fallback.jpg') center/cover no-repeat;
      */
    }

    /* Your actual page content */
    .content {
      position: relative;
      z-index: 1;
      /* Make sure buttons and links are always clickable */
      pointer-events: all;
    }

    spline-viewer {
      width: 100%;
      height: 100%;
      display: block;
    }
  </style>
</head>
<body>

  <!-- Fallback (always rendered — hidden by JS once Spline loads) -->
  <div class="spline-fallback" id="spline-fallback"></div>

  <!-- Spline background (hidden until loaded) -->
  <div class="spline-bg" id="spline-bg">
    <spline-viewer
      id="spline-viewer"
      url="https://prod.spline.design/REPLACE_ME/scene.splinecode"
      events-target="global">
      <!--
        events-target="global" = scene responds to mouse movements anywhere on page
        Remove it if you only want interaction when hovering directly on the scene
      -->
    </spline-viewer>
  </div>

  <!-- Your page content -->
  <div class="content">
    <h1 style="color: white; padding: 40px;">Your Content Here</h1>
  </div>

  <script>
    const splineBg = document.getElementById('spline-bg');
    const splineFallback = document.getElementById('spline-fallback');
    const splineViewer = document.getElementById('spline-viewer');

    // --- Device capability check ---
    function shouldLoadSpline() {
      const isMobile = window.innerWidth < 768;
      const isLowEnd = navigator.hardwareConcurrency <= 2;

      // Check WebGL support
      const testCanvas = document.createElement('canvas');
      const gl = testCanvas.getContext('webgl2') || testCanvas.getContext('webgl');
      const noWebGL = !gl;

      return !isMobile && !isLowEnd && !noWebGL;
    }

    if (!shouldLoadSpline()) {
      // Low-end or mobile — skip Spline entirely, keep fallback visible
      splineBg.remove();
    } else {
      // --- Load timeout fallback ---
      // If Spline hasn't loaded in 8 seconds, give up and show the fallback
      const timeout = setTimeout(() => {
        console.warn('Spline scene timed out — showing fallback');
        splineBg.remove();
        splineFallback.style.opacity = '1';
      }, 8000);

      // --- Detect successful load ---
      // spline-viewer fires a 'load' event when the scene is ready
      splineViewer.addEventListener('load', () => {
        clearTimeout(timeout);
        splineBg.classList.add('loaded');
        // Optionally fade out the fallback
        splineFallback.style.transition = 'opacity 0.6s ease';
        splineFallback.style.opacity = '0';
      });
    }
  </script>

</body>
</html>
```

---

## Example: Production-Ready React Wrapper

Production-ready Spline wrapper for React / Next.js. Features: lazy loading, mobile detection, GPU check, fallback, fade-in on load.

Usage:
```jsx
<SplineBackground sceneUrl="https://prod.spline.design/XXXXX/scene.splinecode" />
```

```tsx
// react-spline-wrapper.tsx
import { lazy, Suspense, useState, useEffect, useRef } from 'react';

const Spline = lazy(() => import('@splinetool/react-spline'));

interface SplineBackgroundProps {
  sceneUrl: string;
  fallbackColor?: string;
  fallbackImageUrl?: string;
  mobileBreakpoint?: number;
  className?: string;
  children?: React.ReactNode;
}

function shouldLoadSpline(mobileBreakpoint: number): boolean {
  if (typeof window === 'undefined') return false; // SSR guard

  const isMobile = window.innerWidth < mobileBreakpoint;
  const isLowEnd = navigator.hardwareConcurrency <= 2;

  // Check WebGL support
  const canvas = document.createElement('canvas');
  const gl = canvas.getContext('webgl2') || canvas.getContext('webgl');
  const noWebGL = !gl;

  return !isMobile && !isLowEnd && !noWebGL;
}

export default function SplineBackground({
  sceneUrl,
  fallbackColor = '#0a0a0a',
  fallbackImageUrl,
  mobileBreakpoint = 768,
  className = '',
  children,
}: SplineBackgroundProps) {
  const [splineLoaded, setSplineLoaded] = useState(false);
  const [splineFailed, setSplineFailed] = useState(false);
  const [canLoad, setCanLoad] = useState(false);
  const timeoutRef = useRef<ReturnType<typeof setTimeout>>();

  useEffect(() => {
    setCanLoad(shouldLoadSpline(mobileBreakpoint));
  }, [mobileBreakpoint]);

  useEffect(() => {
    if (!canLoad) return;

    // If Spline hasn't loaded after 8 seconds, show fallback
    timeoutRef.current = setTimeout(() => {
      if (!splineLoaded) {
        setSplineFailed(true);
      }
    }, 8000);

    return () => clearTimeout(timeoutRef.current);
  }, [canLoad, splineLoaded]);

  function onLoad() {
    clearTimeout(timeoutRef.current);
    setSplineLoaded(true);
  }

  const showFallback = !canLoad || splineFailed;

  return (
    <div
      className={className}
      style={{ position: 'relative', width: '100%', height: '100vh', overflow: 'hidden' }}
    >
      {/* Fallback layer — always rendered underneath */}
      <div
        style={{
          position: 'absolute',
          inset: 0,
          zIndex: 0,
          background: fallbackImageUrl
            ? `url(${fallbackImageUrl}) center/cover no-repeat`
            : fallbackColor,
          // Fade out once Spline loads
          opacity: splineLoaded && !showFallback ? 0 : 1,
          transition: 'opacity 0.6s ease',
        }}
      />

      {/* Spline scene — only on capable devices */}
      {canLoad && !splineFailed && (
        <Suspense fallback={null}>
          <Spline
            scene={sceneUrl}
            onLoad={onLoad}
            style={{
              position: 'absolute',
              top: 0,
              left: 0,
              width: '100%',
              height: '100%',
              zIndex: 0,
              // Fade in when ready
              opacity: splineLoaded ? 1 : 0,
              transition: 'opacity 0.6s ease',
              // Don't block clicks on content above
              // Change to 'all' if you want mouse interaction with the scene
              pointerEvents: 'none',
            }}
          />
        </Suspense>
      )}

      {/* Content sits on top of everything */}
      {children && (
        <div style={{ position: 'relative', zIndex: 1 }}>
          {children}
        </div>
      )}
    </div>
  );
}
```

---

## Example: Full Interactive Scene (React)

Full interactive Spline example — React. Demonstrates: events, object manipulation, animation triggers, variable access.

```tsx
// interactive-scene.tsx
import { useRef, useState, useCallback } from 'react';
import Spline from '@splinetool/react-spline';
import type { Application } from '@splinetool/runtime';

const SCENE_URL = 'https://prod.spline.design/REPLACE_ME/scene.splinecode';

export default function InteractiveScene() {
  const splineApp = useRef<Application>();
  const [isLoaded, setIsLoaded] = useState(false);
  const [lastEvent, setLastEvent] = useState<string>('');

  // --- Called when scene finishes loading ---
  function onLoad(app: Application) {
    splineApp.current = app;
    setIsLoaded(true);
    console.log('Scene loaded');
  }

  // --- Listen to events from inside the Spline scene ---
  function onMouseDown(e: any) {
    setLastEvent(`mouseDown on: ${e.target?.name}`);
    console.log('mouseDown event:', e.target);
  }

  function onMouseHover(e: any) {
    setLastEvent(`mouseHover on: ${e.target?.name}`);
  }

  // --- Programmatically move an object ---
  const moveObject = useCallback(() => {
    if (!splineApp.current) return;

    const obj = splineApp.current.findObjectByName('Cube');
    if (!obj) return console.warn('Object "Cube" not found — check the name in Spline editor');

    obj.position.x += 50; // move right
  }, []);

  // --- Trigger an animation event ---
  const triggerAnimation = useCallback(() => {
    if (!splineApp.current) return;
    splineApp.current.emitEvent('mouseHover', 'Cube'); // triggers the mouseHover event on 'Cube'
  }, []);

  // --- Trigger animation in reverse (useful for toggle effects) ---
  const reverseAnimation = useCallback(() => {
    if (!splineApp.current) return;
    splineApp.current.emitEventReverse('mouseHover', 'Cube');
  }, []);

  // --- Rotate object (RADIANS not degrees!) ---
  const rotateObject = useCallback(() => {
    if (!splineApp.current) return;

    const obj = splineApp.current.findObjectByName('Cube');
    if (!obj) return;

    // 90 degrees = Math.PI / 2
    obj.rotation.y += Math.PI / 2;
  }, []);

  // --- Change object scale ---
  const scaleObject = useCallback((factor: number) => {
    if (!splineApp.current) return;

    const obj = splineApp.current.findObjectByName('Cube');
    if (!obj) return;

    obj.scale.x = factor;
    obj.scale.y = factor;
    obj.scale.z = factor;
  }, []);

  // --- Read/write Spline variables ---
  const updateVariable = useCallback(() => {
    if (!splineApp.current) return;

    // Get a variable defined in the Spline editor
    const score = splineApp.current.getVariable('score');
    console.log('Current score variable:', score);

    // Set a variable
    splineApp.current.setVariable('score', (score as number) + 1);
  }, []);

  return (
    <div style={{ position: 'relative', width: '100vw', height: '100vh' }}>

      {/* Spline scene */}
      <Spline
        scene={SCENE_URL}
        onLoad={onLoad}
        onMouseDown={onMouseDown}
        onMouseHover={onMouseHover}
        style={{
          position: 'absolute',
          inset: 0,
          width: '100%',
          height: '100%',
          zIndex: 0,
        }}
      />

      {/* Control panel — sits on top of the scene */}
      {isLoaded && (
        <div style={{
          position: 'absolute',
          bottom: 40,
          left: '50%',
          transform: 'translateX(-50%)',
          zIndex: 10,
          display: 'flex',
          gap: 12,
          flexWrap: 'wrap',
          justifyContent: 'center',
          background: 'rgba(0,0,0,0.6)',
          padding: '16px 24px',
          borderRadius: 12,
          backdropFilter: 'blur(8px)',
        }}>
          <button onClick={moveObject}>Move Right</button>
          <button onClick={rotateObject}>Rotate 90°</button>
          <button onClick={() => scaleObject(2)}>Scale Up</button>
          <button onClick={() => scaleObject(1)}>Reset Scale</button>
          <button onClick={triggerAnimation}>Trigger Hover</button>
          <button onClick={reverseAnimation}>Reverse Hover</button>
          <button onClick={updateVariable}>Increment Variable</button>
        </div>
      )}

      {/* Event log */}
      {lastEvent && (
        <div style={{
          position: 'absolute',
          top: 20,
          left: '50%',
          transform: 'translateX(-50%)',
          zIndex: 10,
          color: 'white',
          background: 'rgba(0,0,0,0.5)',
          padding: '8px 16px',
          borderRadius: 8,
          fontSize: 14,
          fontFamily: 'monospace',
        }}>
          {lastEvent}
        </div>
      )}

      {/* Loading state */}
      {!isLoaded && (
        <div style={{
          position: 'absolute',
          inset: 0,
          display: 'flex',
          alignItems: 'center',
          justifyContent: 'center',
          color: 'white',
          fontSize: 18,
          zIndex: 10,
          background: '#0a0a0a',
        }}>
          Loading scene...
        </div>
      )}
    </div>
  );
}

/*
NOTES FOR AGENT:

1. Replace 'Cube' with the actual object name from the Spline editor
   (right-click object in editor → "Copy Development Object ID" for the UUID,
   or just use the display name shown in the Objects panel)

2. Rotation uses RADIANS:
   90°  = Math.PI / 2
   180° = Math.PI
   360° = Math.PI * 2
   Convert: const toRad = (deg) => deg * (Math.PI / 180)

3. Variables must be defined in the Spline editor first
   (right sidebar → Variables panel → add variable)

4. All available event types for onXxx props:
   onMouseDown, onMouseUp, onMouseHover, onMousePress,
   onKeyDown, onKeyUp, onStart, onScroll

5. If getting hydration errors in Next.js, wrap with:
   const Spline = dynamic(() => import('@splinetool/react-spline/next'), { ssr: false })
*/
```
