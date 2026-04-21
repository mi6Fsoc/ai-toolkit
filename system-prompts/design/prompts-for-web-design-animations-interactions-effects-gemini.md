# Prompts for Web Design: Animations, Interactions & Effects [Gemini]

### The System Context (Included in every prompt below)

> *Stack: Next.js, Tailwind CSS, Framer Motion, Lucide React.*
> 
> 
> *Rules: Use `clsx`/`tailwind-merge` for styles. Use `transform` (GPU) over layout props for animation. Implement `prefers-reduced-motion`. Use functional hooks (`useScroll`, `useTransform`, `useSpring`) over listeners.*
> 

---

### Part 1: The Original 7 (Refined & Integrated)

### 1. The "Magnetic" CTA

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, GPU transforms, and `useSpring` physics.
> 
> 
> **Task:** Build a "Magnetic" button component.
> 
> **Implementation:**
> 
> 1. Wrap the button in a `motion.div`. Use `useMotionValue` for x and y coordinates.
> 2. On the parent's `onMouseMove` event, calculate the distance between the pointer and the button center (`e.clientX - bounds.left - bounds.width / 2`).
> 3. Apply a spring transition (`stiffness: 150, damping: 15`) to x/y values so the button follows the mouse. Limit movement range to ~15px.
> 4. Inside, add a text label that moves *more* than the button background (parallax effect) using `useTransform` with a higher output range.
> 5. Reset positions to 0 on `onMouseLeave`.

### 2. Staggered Bento Grid

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, GPU transforms, and variants.
> 
> 
> **Task:** Build a staggered Bento Grid entry animation.
> 
> **Implementation:**
> 
> 1. Use CSS Grid (`grid-cols-1 md:grid-cols-3 gap-4`).
> 2. Parent `motion.div` sets `initial="hidden"` `animate="visible"` with `staggerChildren: 0.1`.
> 3. Child variants: `hidden: { opacity: 0, y: 20, filter: "blur(10px)" }`, `visible: { opacity: 1, y: 0, filter: "blur(0px)" }`.
> 4. Add hover: Scale up (`scale: 1.02`), soft shadow (`shadow-xl`), use spring (`stiffness: 400`).
> 5. Use `col-span-2` on specific items to create an irregular bento layout.

### 3. Infinite Marquee

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, GPU transforms, `useMotionValue`.
> 
> 
> **Task:** Create a performance-optimized infinite marquee.
> 
> **Implementation:**
> 
> 1. Flex container with `overflow-hidden`.
> 2. Wrapper `motion.div` containing **two copies** of the content list.
> 3. Animate wrapper `x` from `0` to `50%`. Transition: `{ repeat: Infinity, ease: "linear", duration: 20 }`.
> 4. Add `useMotionValue` for speed control. On hover, set speed to 0 (pause).
> 5. Apply gradient masks on left/right edges (`mask-image: linear-gradient(...)`) for smooth fade-in/out.

### 4. 3D Tilt Card

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, GPU transforms, `preserve-3d`.
> 
> 
> **Task:** Build a highly reactive 3D Tilt Card.
> 
> **Implementation:**
> 
> 1. Container uses `transformStyle: "preserve-3d"`.
> 2. Map mouse position (0-1) to rotation values: `rotateX` (15deg to -15deg) and `rotateY` (-15deg to 15deg).
> 3. Use `useSpring` on rotations for fluid movement.
> 4. Add a "glare" layer: `motion.div` with radial gradient (`from-white/40 to-transparent`) moving opposite to cursor.
> 5. Inner content uses `translateZ(50px)` to pop out from the background.

### 5. Layout Projection Tabs

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `layoutId`, `AnimatePresence`.
> 
> 
> **Task:** Create segmented tabs with a morphing background.
> 
> **Implementation:**
> 
> 1. Map through tabs. Render a background `motion.span` behind the active tab text only.
> 2. Give the background span a unique `layoutId="active-pill"`. This enables automatic shape morphing between tabs.
> 3. Wrap content area in `AnimatePresence` (`mode="wait"`).
> 4. Content animation: `initial={{ opacity: 0, y: 10 }}` `animate={{ opacity: 1, y: 0 }}` `exit={{ opacity: 0, y: -10 }}`.

### 6. Matrix Scramble Text

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `useEffect` for logic, Monospace font.
> 
> 
> **Task:** Create a text reveal component with a decryption effect.
> 
> **Implementation:**
> 
> 1. Loop runs every 50ms on mount.
> 2. Maintain a `progress` index. Characters before index are real text; characters after are random symbols (`!@#$`).
> 3. Increment index until complete.
> 4. Use `font-mono` to prevent width jitter.
> 5. **Accessibility:** Ensure the parent element has `aria-label` with the correct final text.

### 7. Parallax Gallery

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `useScroll`, `useTransform`.
> 
> 
> **Task:** Build a 3-column parallax scroll gallery.
> 
> **Implementation:**
> 
> 1. Track container with `useScroll`.
> 2. Column 1: `y: useTransform(scrollY, [0, 1], [0, -50])`.
> 3. Column 2: `y: useTransform(scrollY, [0, 1], [0, -200])` (Fastest).
> 4. Column 3: `y: useTransform(scrollY, [0, 1], [0, -100])`.
> 5. Images: Use `whileInView` to scale from 0.9 to 1.0 inside an `overflow-hidden` wrapper.

---

### Part 2: The New 7 (Modern Trends)

### 8. The "Spotlight" Border

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `useMotionTemplate`, `useMotionValue`.
> 
> 
> **Task:** Create a card with a glowing border that follows the mouse cursor.
> 
> **Implementation:**
> 
> 1. Create a `div` with `overflow-hidden`, `rounded-xl`, and `relative` positioning.
> 2. Track mouse X/Y relative to the card using `onMouseMove`.
> 3. Create a `motion.div` overlay that acts as the border. Use `background: radial-gradient(600px circle at ${mouseX}px ${mouseY}px, rgba(255,255,255,0.4), transparent 40%)`.
> 4. Place this overlay *behind* the inner content card (which has a solid background color) with a padding of `1px` to reveal the gradient as a border.
> 5. Add a second weaker spotlight inside the content card for a "glass" surface feel.

### 9. Stacked "Sticky" Cards

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `useScroll`, `useTransform`, `sticky`.
> 
> 
> **Task:** Build a stacked card section where cards pile up on scroll.
> 
> **Implementation:**
> 
> 1. Create a container with `h-[300vh]` (or dependent on card count).
> 2. Map through cards. Each card container is `sticky top-0 h-screen flex items-center justify-center`.
> 3. Calculate a dynamic scale and opacity for each card based on its index and scroll progress.
> 4. As card `i` hits the top, card `i-1` should scale down slightly (`scale: 1 - index * 0.05`) and darken (`filter: brightness(0.9)`).
> 5. Ensure `transform-origin: top center` so they stack neatly.

### 10. Text Gradient Scroll Reveal

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `useScroll`, `useTransform`, `bg-clip-text`.
> 
> 
> **Task:** Create a large text block where words light up as you scroll (Apple style).
> 
> **Implementation:**
> 
> 1. Split text into words. Map through them.
> 2. Wrap each word in a `span`.
> 3. Track scroll progress of the specific text container using `useScroll({ target: containerRef, offset: ["start end", "end start"] })`.
> 4. Map the scroll progress to opacity for each word. Calculate a "step" for each word so they light up sequentially (e.g., word 1 is opaque at 0.1 progress, word 2 at 0.15).
> 5. Alternatively, allow the text to be `text-white/20` (dim) initially and transition to `text-white` (lit).

### 11. Custom "Blending" Cursor

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, Global Context, `mix-blend-mode`.
> 
> 
> **Task:** Create a custom cursor that inverts colors over text.
> 
> **Implementation:**
> 
> 1. Disable default cursor with `cursor-none` on `body`.
> 2. Create a fixed `motion.div` (width/height 20px, rounded-full, `bg-white`).
> 3. Use a global hook to track mouse window coordinates. Assign to `useSpring` motion values (x, y) for smooth lag.
> 4. Set `pointer-events-none` and `z-50`.
> 5. Critical: Set `mix-blend-mode: difference` on the cursor div. This makes it turn black over white backgrounds and white over dark backgrounds.

### 12. SVG Path Drawing (Line Animation)

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `viewport`, SVG props.
> 
> 
> **Task:** Animate an SVG line drawing itself when scrolled into view.
> 
> **Implementation:**
> 
> 1. Render an SVG with a `path` element.
> 2. Set the `motion.path` props: `initial={{ pathLength: 0 }}` `whileInView={{ pathLength: 1 }}`.
> 3. Transition: `{ duration: 2, ease: "easeInOut" }`.
> 4. Style the stroke: `stroke-current`, `stroke-width-2`, `fill-transparent`.
> 5. Add a glowing effect by duplicating the path, adding `blur-md`, and placing it behind the main path.

### 13. Drag-to-Reveal Drawer (Mobile First)

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `drag` props, `useAnimation`.
> 
> 
> **Task:** Create a bottom sheet drawer that can be dragged up.
> 
> **Implementation:**
> 
> 1. Create a `motion.div` fixed at the bottom of the screen (`y: "100%"` initially).
> 2. Enable dragging: `drag="y"`, `dragConstraints={{ top: 0, bottom: 0 }}`.
> 3. Use `dragElastic={0.2}` for resistance.
> 4. On `onDragEnd`, check `info.point.y`. If dragged down sufficiently, animate close (`y: "100%"`). If dragged up, animate open (`y: 0`).
> 5. Add a backdrop overlay that fades in (opacity 0 to 0.5) as the drawer rises (use `useTransform` mapped to the drawer's Y value).

### 14. "Odometer" Number Counter

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `clsx`, `useSpring`, `useEffect`.
> 
> 
> **Task:** Create a number that scrolls/ticks up when viewed.
> 
> **Implementation:**
> 
> 1. Accept a `value` prop (e.g., 5000).
> 2. Use `useMotionValue(0)` for the starting number.
> 3. Use `useSpring` to smooth the transition to the target `value` when `useInView` is true.
> 4. Inside the render, use a `useTransform` to pipe the motion value into a generic logic that rounds the number (Math.round) and formats it (`Intl.NumberFormat`).
> 5. Render the transformed text inside a `motion.span`.

---

### How to use these

Copy the **entire** block of the prompt you want—including the "Context" section—and paste it into your AI coding tool. The Context section acts as a guardrail to prevent the AI from giving you generic CSS or heavy jQuery-style animations.

---

Here are 16 fresh, high-level "vibe coding" prompts. These focus on **spatial UI, physics-based interactions, and atmospheric effects** commonly found in top-tier design engineering (e.g., Linear, Raycast, Vercel).

I have categorized them to help you build specific parts of your UI.

---

### Category A: Navigation & Layout Structure

### 1. The macOS-Style Dock

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `useMotionValue`, `useTransform`, `useSpring`.
> 
> 
> **Task:** Create a floating bottom navigation dock with magnification physics.
> 
> **Implementation:**
> 
> 1. Map through icons in a flex container.
> 2. Track mouse X position relative to the dock container using `useMouseMove`.
> 3. For each icon, create a `distance` motion value (`useTransform` of mouseX minus icon center).
> 4. Map that distance to a `width` value using a Gaussian curve logic (closer = wider). E.g., convert distance `150` to `150` into width `40` to `80`.
> 5. Apply a `useSpring` to the width for snappy, viscous responsiveness.
> 6. Ensure the dock container handles layout shifts smoothly (no jitter).

### 2. Sticky "Scroll-Jack" Horizontal Section

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `useScroll`, `useTransform`, `sticky`.
> 
> 
> **Task:** Build a section that locks scrolling vertically to scroll content horizontally.
> 
> **Implementation:**
> 
> 1. Create a parent container with `h-[400vh]` (height defines scroll speed).
> 2. Inside, create a `sticky top-0 h-screen overflow-hidden` wrapper.
> 3. Inside that, create a `motion.div` track containing horizontal cards.
> 4. Use `useScroll` on the parent container.
> 5. Map `scrollYProgress` (0 to 1) to the track's x value (`0` to `(totalWidth - viewportWidth)`).
> 6. Add a skew effect (`skewX`) based on the scroll velocity (`useVelocity`) to simulate drag inertia.

### 3. Dynamic Island / Morphing Header

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `layout`, `layoutId`, `AnimatePresence`.
> 
> 
> **Task:** Create a header pill that morphs size based on active state (Idle vs. Loading vs. Success).
> 
> **Implementation:**
> 
> 1. Create a central floating header component.
> 2. Use a state variable for content (e.g., `state: 'idle' | 'expanded'`).
> 3. Wrap the container in `motion.div` with `layout`. This allows automatic width/height animation when children change.
> 4. Use `AnimatePresence` with `mode="popLayout"` for inner content.
> 5. Define separate components for the states. Give common elements (like a spinner or icon) the same `layoutId` so they smoothly travel to new positions during the resize.

### 4. "Curtain Reveal" Footer

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `z-index`, `sticky`, `min-h-screen`.
> 
> 
> **Task:** Create a footer that is revealed by the previous section scrolling *away* (uncovering effect).
> 
> **Implementation:**
> 
> 1. Make the main content wrapper (everything *except* the footer) have `relative`, `z-10`, and `bg-background`.
> 2. Make the Footer component `fixed bottom-0 left-0 w-full h-[500px]` (or dynamic height) with `z-0`.
> 3. Add a spacer `div` at the end of the main content with the exact same height as the footer to allow scrolling to finish.
> 4. Add a subtle scale effect to the Footer: `scale: useTransform(scrollYProgress, [0.9, 1], [0.95, 1])` so it slightly zooms in as it gets revealed.

---

### Category B: Atmospheric Backgrounds & Textures

### 5. Aurora Borealis Background

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `filter: blur`, `animate`, `mix-blend-mode`.
> 
> 
> **Task:** Create a moving, organic gradient background.
> 
> **Implementation:**
> 
> 1. Create a container with `bg-slate-950` and `overflow-hidden`.
> 2. Place 3-4 large absolute `motion.div` blobs with different colors (cyan, violet, emerald).
> 3. Apply huge blurs (`blur-[100px]`) and `opacity-50`.
> 4. Animate each blob's position (`x`, `y`) and `scale` in a random loop using `animate` with `repeat: Infinity, repeatType: "mirror", duration: 10+`.
> 5. Overlay a transparent noise texture image with `mix-blend-overlay` and `opacity-20` to dither the gradients and prevent banding.

### 6. Grid "Beam" Tracking

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use CSS Grid, `useMotionTemplate`.
> 
> 
> **Task:** A background grid where a glowing beam follows the cursor, illuminating grid lines.
> 
> **Implementation:**
> 
> 1. Render a large grid using `background-image` (CSS radial/linear gradients).
> 2. Track mouse X/Y.
> 3. Create a `motion.div` mask or overlay that applies a `radial-gradient` glow centered on the mouse.
> 4. Use `mask-image` on a duplicate, brighter grid layer.
> 5. The brighter grid layer is only visible where the mask (mouse) is.
> 6. Result: The grid looks dim by default, but "lights up" near the cursor.

### 7. Particles on Click (Confetti)

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `AnimatePresence`, physics arrays.
> 
> 
> **Task:** Emit small particles from the cursor position when clicking.
> 
> **Implementation:**
> 
> 1. Maintain an array of `particles` in state. Each has a unique ID, x/y start, and random angle/velocity.
> 2. On `window.onClick`, add 10-20 new particles to the array at `e.clientX/Y`.
> 3. Render each particle as a small `motion.div`.
> 4. Animate them out: `initial={{ scale: 1, x: 0, y: 0 }}` `animate={{ scale: 0, x: varyingX, y: varyingY }}`.
> 5. Remove them from the DOM after the animation completes using `onAnimationComplete` or a `setTimeout` cleanup in `useEffect`.

### 8. Foggy/Glass Card Reveal

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `backdrop-filter`, `mask-image`.
> 
> 
> **Task:** Text that is blurred/hidden until a "searchlight" hovers over it.
> 
> **Implementation:**
> 
> 1. Render text normally.
> 2. Overlay a copy of the text that is heavily blurred (`blur-md`).
> 3. Create a `motion.div` mask that follows the mouse.
> 4. Apply the mask to the *blurred* layer so that the blurred layer is visible everywhere *except* the circle around the mouse.
> 5. Or inversely: The layer is blurred by default, and the "clean" text is revealed via a mask at the mouse position.

---

### Category C: Micro-Interactions & Input

### 9. The "Shimmer" Button

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use CSS keyframes or `animate`, `overflow-hidden`.
> 
> 
> **Task:** A button with a band of light traveling across it periodically.
> 
> **Implementation:**
> 
> 1. Button container: `relative overflow-hidden bg-slate-800`.
> 2. Overlay: A `div` with a linear gradient (`transparent, white/20, transparent`) skewed at 45 degrees.
> 3. Animate the overlay's `x` position from `100%` to `200%`.
> 4. Timing: Run every 3 seconds. Use `repeatDelay` in Framer Motion.
> 5. Add a `border` glow that matches the shimmer timing using a moving conical gradient border.

### 10. Multi-Step Form with Height Morph

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `AnimatePresence`, `layout`, `mode="popLayout"`.
> 
> 
> **Task:** A form card that smoothly resizes height/width when switching between steps.
> 
> **Implementation:**
> 
> 1. Wrap the form container in `motion.div` with `layout` and `transition={{ type: "spring", bounce: 0, duration: 0.3 }}`.
> 2. Wrap the content of the step in `motion.div` with `initial={{ opacity: 0, x: 20 }}`, `animate={{ opacity: 1, x: 0 }}`, `exit={{ opacity: 0, x: -20 }}`.
> 3. Use `AnimatePresence mode="popLayout"` so the exiting element is removed from flow immediately, allowing the container to shrink/grow to the new element's size instantly.

### 11. Copy-to-Clipboard "Checkmark" Morph

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `AnimatePresence`, SVG path animation.
> 
> 
> **Task:** An icon that morphs from a "Copy" icon to a "Check" icon on click.
> 
> **Implementation:**
> 
> 1. Create a state `isCopied`.
> 2. Use `AnimatePresence` to swap icons.
> 3. Icon 1 (Copy): `initial={{ scale: 0.5, opacity: 0 }} animate={{ scale: 1, opacity: 1 }} exit={{ scale: 0.5, opacity: 0 }}`.
> 4. Icon 2 (Check): Same variants.
> 5. Add a `motion.span` tooltip saying "Copied!" that floats up and fades out (`y: -20`).

### 12. Password Strength Meter (Fluid)

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `layout`, width interpolation.
> 
> 
> **Task:** A colored bar that grows and changes color based on entropy.
> 
> **Implementation:**
> 
> 1. Calculate strength (0-4).
> 2. Render a `motion.div` bar (height 4px).
> 3. Animate `width` (0% to 100%) and `backgroundColor` (Red -> Yellow -> Green) together.
> 4. Use a spring transition so the bar "bounces" slightly as it grows.
> 5. Split the bar into 4 segments with small gaps (`gap-1`) for a segmented look, staggering the animation of each segment.

---

### Category D: Data & Content Visualization

### 13. Image Comparison Slider

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `drag`, `clip-path` or `width`.
> 
> 
> **Task:** A 'Before/After' slider component.
> 
> **Implementation:**
> 
> 1. Container `relative`. Image 1 (Before) is absolute, full width. Image 2 (After) is absolute, full width.
> 2. Add a drag handle `motion.div` constrained to x-axis (`drag="x"`, `dragConstraints={parent}`).
> 3. Use `useMotionValue` for the handle's X position.
> 4. Apply `clip-path: inset(0 0 0 ${x}px)` to the top image based on the handle position.
> 5. Add a vertical line `div` that follows the handle to visualize the split.

### 14. Animated Counter (Slot Machine Style)

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `y` translation, masking.
> 
> 
> **Task:** A number counter where each digit scrolls vertically like a slot machine.
> 
> **Implementation:**
> 
> 1. Split the number (e.g., "42") into digits ["4", "2"].
> 2. Render a vertical column of numbers 0-9 for *each* digit position.
> 3. Mask the container to show only one number height.
> 4. Animate the `y` transform of the column to align with the correct number. E.g., to show "4", translate Y to index 4 * height.
> 5. Stagger the columns so the tens place settles after the ones place.

### 15. "Tying" Code Block Effect

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `useEffect`, `stagger`.
> 
> 
> **Task:** A code snippet that types itself out with syntax highlighting preservation.
> 
> **Implementation:**
> 
> 1. Take a string of code. Split it into tokens (or characters).
> 2. Render the code block cursor: a blinking `motion.span` (`opacity: [1, 0]`).
> 3. Animate the text visibility. Instead of simple opacity, increment the `slice` of the string displayed.
> 4. Auto-scroll the container to the bottom as new lines are added.
> 5. *Vibe detail:* Add a very fast, randomized delay between characters to simulate human typing irregularity.

### 16. Skeleton Loader with "Wave"

> **Context:** Stack: Next.js, Tailwind CSS, Framer Motion. Rules: Use `loop`, `gradient`, `background-position`.
> 
> 
> **Task:** A skeleton loading state that feels premium.
> 
> **Implementation:**
> 
> 1. Base: `bg-slate-800` rounded rectangles.
> 2. Overlay: A linear gradient (`transparent, white/10, transparent`) that is 2x the width of the element.
> 3. Animate `backgroundPosition` from `200%` to `200%`.
> 4. Use `transition={{ duration: 1.5, repeat: Infinity, ease: "linear" }}`.
> 5. Use `staggerChildren` on the parent container so the wave flows diagonally across the page elements rather than all at once.