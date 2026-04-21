# Prompts for Web Design: Animations, Interactions & Effects [Claude]

# Scroll-Based Animations

### *Scroll Animation Prompt*

> Build a full-screen hero section with a fixed background video (`position: fixed`, `object-cover`, `muted`, `playsInline`, `preload="auto"`). Tie video playback to scroll using Framer Motion's `useScroll` hook - map scroll progress (0-1) to `video.currentTime` via `targetTimeRef`, then smoothly interpolate with `requestAnimationFrame` loop using lerp (`currentTimeRef += diff * lerpFactor`). Add a dark overlay (`bg-background/50`) on the video. Create multiple text sections that fade in/out based on scroll position using `useTransform` for opacity, Y translation, and blur. Make the hero container `h-[300vh]` with a `sticky top-0 h-screen` inner wrapper so the content scrolls over the fixed video. Include a scroll indicator at the bottom that fades out on scroll (`useTransform(scrollYProgress, [0, 0.05], [1, 0])`).

### *Parallax Scroll Layers*

Build a multi-layer parallax section with foreground, midground, and background elements. Use Framer Motion's `useScroll` with `useTransform` to move layers at different speeds based on scroll position. Set `layoutId` for smooth transitions. Apply `translateY` transforms with different multipliers (background: 0.2x, midground: 0.5x, foreground: 1x). Wrap in a container with `relative overflow-hidden` and make it at least `h-[150vh]`. Add depth with `scale` transforms that grow slightly on background layers as you scroll. Include subtle blur effects using `useTransform` to map scroll progress to CSS backdrop blur values.

### *Horizontal Scroll Gallery*

Create a horizontal scrolling gallery using `useScroll` with `target` ref on a container. Make the container `h-screen flex items-center` with an inner wrapper that's `flex gap-8 px-8`. Use `useTransform` to map vertical scroll (`scrollYProgress`) to horizontal `translateX` on the gallery. Calculate total width dynamically based on number of items. Add momentum with spring physics (`type: "spring", stiffness: 100, damping: 30`). Include scroll snap points with `scroll-snap-type: x mandatory` and individual items with `scroll-snap-align: center`. Add scale and opacity transforms on individual cards based on their position relative to viewport center using `useTransform` with custom ranges.

### *Reveal on Scroll (Stagger)*

Build a grid of cards that reveal with staggered animation on scroll. Use `IntersectionObserver` API or Framer Motion's `whileInView` prop. Wrap cards in `motion.div` with `initial={{ opacity: 0, y: 50 }}` and `whileInView={{ opacity: 1, y: 0 }}`. Add `viewport={{ once: true, margin: "-100px" }}` to trigger before fully visible. Implement stagger with `transition={{ delay: index * 0.1, duration: 0.6, ease: "easeOut" }}`. For grids, calculate delay based on both row and column position. Add subtle rotation (`rotateX: -10`) that resolves to 0 on reveal for depth.

### *Scroll Progress Indicator*

Create a fixed scroll progress bar at the top of the page. Use `useScroll` to get `scrollYProgress` (0-1 value). Transform this into a width percentage with `useTransform(scrollYProgress, [0, 1], ["0%", "100%"])`. Style as `fixed top-0 left-0 h-1 bg-gradient-to-r from-blue-500 to-purple-500 z-50`. Add a glow effect with `shadow-[0_0_10px_rgba(59,130,246,0.5)]`. Include smooth spring animation with `transition={{ type: "spring", stiffness: 100, damping: 20 }}`. Optionally add circular progress indicator in corner using `motion.circle` SVG with `pathLength` animated from 0 to 1.

### *Sticky Section Transitions*

Build multiple sections that stick and transition as you scroll. Each section should be `h-screen sticky top-0` with increasing z-index values. Use `useScroll` with element `target` and `offset` props to track when each section enters/exits. Apply scale and opacity transforms: sections scale down from 1 to 0.9 and fade from 1 to 0 as next section arrives. Add border radius that increases on scroll out (`useTransform` from 0 to 24px). Include backdrop blur that intensifies as sections stack. Each section should have distinct gradient backgrounds that blend during transitions.

---

# Cursor & Hover Interactions

### *Custom Cursor with Follow Effect*

Create a custom cursor that follows mouse position with smooth lag. Use `useState` for cursor position and `useEffect` with `mousemove` listener. Implement position lerping in `requestAnimationFrame` loop (current position moves 10% toward target each frame). Style cursor as `fixed pointer-events-none z-50` with `mix-blend-mode: difference` for contrast. Include two elements: small inner dot (8px) and larger outer ring (40px). Add scale transforms on hover over interactive elements using `data-cursor-hover` attributes and global event delegation. Implement magnetic effect for buttons: cursor snaps partially toward button center when within range.

### *Magnetic Buttons*

Build buttons with magnetic hover effect that pulls cursor toward button center. Track mouse position with `onMouseMove` on button container. Calculate distance from cursor to button center, then apply `translateX` and `translateY` transforms proportional to distance (max 20px movement). Add `transition-transform duration-200 ease-out` for smoothness. Include scale transform on actual click (`whileTap={{ scale: 0.95 }}`). Add ripple effect on click: create expanding circle from click coordinates using absolute positioned element with scale animation from 0 to 2 and opacity from 0.3 to 0. Reset button position on mouse leave with `onMouseLeave`.

### *Hover Reveal Masks*

Create image or text elements that reveal on hover using clip-path or mask animations. For images: use two layers (grayscale and color), animate color layer's `clip-path: circle()` from `0% at 50% 50%` to `150% at 50% 50%` on hover. For text: implement gradient mask that follows cursor, using `background-clip: text` and animated `background-position` based on mouse coordinates. Add smooth transition with `transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1)`. Include slight zoom effect (`scale: 1.05`) and brightness increase. Can also use WebGL shader approach with Three.js for more complex reveals like liquid distortion.

### *Tilt on Hover (3D Perspective)*

Implement 3D tilt effect on cards based on mouse position. Wrap card in container with `perspective-1000`. Track mouse position relative to card bounds (use `getBoundingClientRect()`). Calculate rotation angles: `rotateX = (mouseY - centerY) / height * maxRotation` and `rotateY = (mouseX - centerX) / width * maxRotation` (typically maxRotation = 15deg). Apply transform with `transition: transform 0.1s ease-out`. Add inner shine/gloss layer that moves opposite to tilt using `background: radial-gradient` positioned based on mouse. Include subtle shadow that shifts with tilt. Reset to flat on mouse leave with smooth spring animation.

### *Hover Expand Cards*

Build a grid of cards where hovering one expands it while shrinking siblings. Use shared state to track which card is hovered. On hover, animate hovered card to `flex-grow: 2` or absolute scaled width, others shrink to `flex-grow: 0.8`. Add smooth layout transitions with Framer Motion's `layout` prop. Include z-index changes so hovered card appears above others. Add content that fades in on expand (additional text, buttons) with opacity and y-offset animations. Include blur effect on non-hovered cards (`filter: blur(4px)`). Add magnetic cursor effect that combines with expand for rich interaction.

---

# Page Transitions

### *Route Transition Fade & Slide*

Create page route transitions with exit and enter animations. Use Framer Motion's `AnimatePresence` with `mode="wait"`. Wrap page components in `motion.div` with `initial={{ opacity: 0, x: 20 }}`, `animate={{ opacity: 1, x: 0 }}`, `exit={{ opacity: 0, x: -20 }}`. Add different transitions per route direction (forward slides left, back slides right). Include fixed duration of 0.3s with `ease: [0.6, 0.01, 0.05, 0.95]` cubic bezier. Add scale effect on exit (slightly shrink to 0.98). Implement page loading skeleton that appears if transition exceeds 200ms using timeout.

### *Morphing Page Transitions*

Build smooth morphing transitions between pages sharing elements. Use Framer Motion's `layoutId` prop on shared elements (images, titles, containers). Elements with matching `layoutId` will animate position and size between routes. Add `transition={{ type: "spring", stiffness: 300, damping: 30 }}` for physics-based motion. Include background color transitions on page container with gradient interpolation. Add blur effect during mid-transition for depth. Implement custom path animations for non-shared elements (curtain wipe, circle expand). Consider using View Transitions API as progressive enhancement for browsers that support it.

### *Slide Panel Navigation*

Create slide-in navigation panel that overlays page content. Panel starts off-screen (`translateX: -100%`). On toggle, animate to `translateX: 0` with `transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1)`. Add backdrop overlay that fades in (`opacity: 0 to 0.5`) with `bg-black/50 backdrop-blur-sm`. Lock body scroll when panel open (add `overflow-hidden` to body). Animate navigation items in sequence with stagger delay (50ms per item) sliding from left with opacity fade. Include close gesture: detect drag with `useDrag` hook, allow swiping left to close with threshold. Add subtle shadow that intensifies during open animation.

---

# Component Micro-Interactions

### *Button States & Feedback*

Create button with comprehensive interaction states. Use Framer Motion's `whileHover={{ scale: 1.05 }}`, `whileTap={{ scale: 0.95 }}`. Add ripple effect on click from exact cursor position (create expanding circle, absolute positioned). Include loading state with spinner that fades in and button text that fades out, disable during loading. Add success state with checkmark icon and color change (green) that auto-reverts after 2s. Implement error shake animation (quick horizontal vibration using keyframes). Add haptic feedback on mobile with `navigator.vibrate(10)`. Include sound effect on click (optional, user-controlled). Style with gradient background that shifts on hover using `background-position` animation.

### *Toggle Switch*

Build animated toggle switch with smooth transitions. Create input checkbox with custom styled label. Use `peer` class pattern or state management. Toggle track should be `w-12 h-6 rounded-full` with background transition from gray to blue. Toggle thumb is absolutely positioned circle that translates from left to right (`translateX: 0` to `translateX: 24px`). Add spring physics to movement: `transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1)`. Include scale effect on click (`scale: 1.1` briefly). Add icon that fades in/out based on state (sun/moon, check/x). Implement hover state with slight scale increase and shadow. Add keyboard support (Space to toggle) and aria labels.

### *Input Focus Animations*

Create text input with smooth focus animations. Add border that expands from center on focus using `transform: scaleX(0)` to `scaleX(1)` with `transform-origin: center`. Include floating label that moves up and shrinks on focus or when input has value. Add subtle glow effect with animated box shadow. Implement character count that appears with slide-in animation. Include validation feedback: shake on error, checkmark on success. Add autofill detection (use `:-webkit-autofill` pseudo-class) with color transition. Include password strength meter that grows and changes color. Style placeholder with gentle fade-in animation.

### *Toast Notifications*

Build toast notification system with stacked positioning. Toasts slide in from top-right with `initial={{ opacity: 0, y: -50, scale: 0.3 }}` to `animate={{ opacity: 1, y: 0, scale: 1 }}`. Use `AnimatePresence` for exit animations. Auto-dismiss after 5s with progress bar that depletes (`width: 100%` to `0%`). Allow manual dismiss with close button that has hover/tap feedback. When multiple toasts exist, stack them with 8px gap and slight scale/opacity reduction on lower items. Implement swipe-to-dismiss gesture (drag right to remove). Add pause on hover (stop auto-dismiss timer). Include accessibility: announce with `role="status"` and `aria-live="polite"`. Different variants (success, error, info) with icon and color coding.

### *Dropdown Menu*

Create dropdown with smooth open/close animations. Use `AnimatePresence` for mount/unmount. Menu animates with `initial={{ opacity: 0, scale: 0.95, y: -10 }}` to `animate={{ opacity: 1, scale: 1, y: 0 }}` with transform origin at top. Add backdrop blur on menu container. Implement arrow that points to trigger. Individual menu items slide in with stagger (20ms delay each). Add hover states on items with background color fill from left to right using pseudo-element with `width: 0` to `width: 100%` transition. Include keyboard navigation (arrow keys, Enter, Escape). Auto-close on outside click (use `useClickOutside` hook). Add dividers between sections with fade-in. Support nested submenus with slide-out animation.

### *Modal Overlay*

Build modal with backdrop and content animations. Backdrop fades in from `opacity: 0` to `opacity: 1` with `bg-black/60 backdrop-blur-md`. Modal content combines fade and scale: `initial={{ opacity: 0, scale: 0.8 }}` to `animate={{ opacity: 1, scale: 1 }}`. Add spring physics for bounce effect. Lock body scroll when open. Implement close on backdrop click and Escape key. Add close button with hover states. Content can slide up from bottom on mobile (`y: 100%` to `y: 0`). Include header with gradient border that animates in. Support different sizes (sm, md, lg, full). Add entrance animation variation based on context (success modal bounces, error modal shakes slightly). Implement focus trap (Tab cycles through modal elements only).

### *Accordion / Collapse*

Create accordion with smooth height animations. Use Framer Motion's `AnimatePresence` and `motion.div` with `initial={{ height: 0, opacity: 0 }}` to `animate={{ height: "auto", opacity: 1 }}`. Add `overflow: hidden` during animation. Rotate chevron icon 180deg on expand with smooth transition. Include option for single-open (closing others) or multi-open. Add hover state on headers with background color transition. Implement border animations where borders slide in/out. Include nested accordions with slight indentation. Add aria-expanded and aria-controls attributes. Style active item with accent color and bold text. Support default open state. Add subtle content fade-in with delay after height animation starts.

### *Tabs Navigation*

Build tab navigation with animated active indicator. Create underline that slides between tabs matching active tab's position and width. Use `layoutId` with Framer Motion for smooth morphing or manually calculate with `useEffect` tracking active index. Add click animation on tab buttons (`whileTap={{ scale: 0.95 }}`). Include hover state with background color fade-in. Tab content animates in with direction-aware slide (left to right or right to left based on which direction tab changed). Use `AnimatePresence` with `mode="wait"` for clean transitions. Add keyboard navigation (arrow keys, Home, End). Include disabled state styling. Support vertical tab orientation. Add badge counts on tabs that pulse when updating. Implement lazy loading of tab content.

---

# Loading & Progress States

### *Skeleton Loaders*

Create skeleton loading states that match final content structure. Use div placeholders with `bg-gray-200 dark:bg-gray-800 rounded` and animated shimmer effect. Shimmer uses gradient that moves across: `background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent)` with `background-size: 200%` animated from `background-position: -200% 0` to `200% 0` using keyframes over 1.5s infinite. Build skeleton variants for cards, lists, text blocks. Include pulse animation as alternative (opacity 0.5 to 1). Ensure skeletons match exact dimensions of loaded content to prevent layout shift. Add rounded corners and spacing matching actual design.

### *Progress Bars*

Build linear progress bar with smooth fill animation. Container is `h-2 bg-gray-200 rounded-full overflow-hidden`. Inner bar is `h-full bg-blue-500` with width animated based on progress value. Use `transition: width 0.3s ease-out` for smooth updates. Add shimmer effect that travels across filled portion. Include percentage text that counts up using spring animation. For indeterminate state, animate bar sliding left to right repeatedly with `translateX` from `-100%` to `200%`. Add glow effect with box shadow. Support color variants based on progress (0-30% red, 30-70% yellow, 70-100% green). Include circular variant using SVG circle with `stroke-dasharray` and `stroke-dashoffset` animated.

### *Spinner Animations*

Create various loading spinner styles. Classic spinning circle: use SVG circle with rotating container (`animate: { rotate: 360 }` with infinite loop and linear easing). Add multiple circles with staggered animations for orbital loader. Build dot loader with three dots bouncing in sequence (stagger `scale` and `y` animations). Create pulse ring that expands and fades (scale 1 to 1.5, opacity 1 to 0). Include bars loader with multiple vertical bars that scale up/down in sequence. Style with currentColor so it inherits text color. Add size variants (sm, md, lg). Implement smooth fade-in on appearance. Include accessibility with `role="status"` and `aria-label="Loading"`.

### *Upload Progress*

Build file upload component with progress visualization. Show file card with thumbnail preview. Add circular progress ring (SVG circle animating `stroke-dashoffset` from full circumference to 0). Include percentage text in center that counts up. Show file size and name. Add speed indicator (KB/s or MB/s) that updates in real-time. Include cancel button with confirm dialog. Show different states: queued (gray), uploading (blue with animation), complete (green checkmark), error (red with retry). For multiple files, stack cards with individual progress. Add overall progress bar for batch uploads. Include drag reorder capability on queued files. Show estimated time remaining that updates based on speed.

---

# Data Visualization Animations

### *Animated Charts*

Create chart components that animate on mount and data updates. For bar charts: bars grow from height 0 to final value with stagger delay (50ms per bar). Use spring animation for bouncy effect. For line charts: animate path drawing using `stroke-dasharray` and `stroke-dashoffset` (starting with offset equal to path length, animating to 0). Add dot markers that pop in after line completes. For pie charts: animate each segment's arc angle from 0 to final value in sequence. Include tooltips that appear on hover with fade and slight scale. Add legend items that highlight corresponding chart elements on hover. Implement crosshair on line charts that follows cursor. Support responsive scaling with smooth transitions when container resizes.

### *Number Counters*

Build animated number counter that counts up to target value. Use `useSpring` from Framer Motion or custom `useEffect` with `requestAnimationFrame`. Interpolate from 0 (or previous value) to target value over duration (1-2s). Apply easing function (ease-out quad). Format numbers with locale string (commas, decimals). Add currency symbols, percentage signs. Include prefix/suffix with fade-in. For large number changes, add color flash effect (green for increase, red for decrease). Support decimal precision. Include abbreviated format for large numbers (1.2K, 3.4M). Add hover state showing full unformatted number in tooltip. Implement odometer-style rolling digits as variant.

### *Data Table Sorting*

Create data table with animated sorting transitions. When column header clicked, add loading skeleton for affected rows. Animate row reordering using `layoutId` on each row's wrapper with Framer Motion. Rows smoothly swap positions with spring physics. Include sort direction indicator (arrow icon) that rotates 180deg when switching ascending/descending. Add hover state on headers showing they're clickable. Highlight sorted column with background tint. Implement multi-column sorting with numbered badges. Add filter animations: rows slide out with opacity fade when filtered, new matching rows slide in. Include pagination with page transitions (fade and slide). Add row expansion for details with height animation.

---

# Scroll Snap & Navigation

### *Full-Page Snap Sections*

Build full-height sections with scroll snap. Each section is `h-screen` with container having `scroll-snap-type: y mandatory`. Individual sections have `scroll-snap-align: start`. Add smooth scroll behavior. Include navigation dots sidebar that shows current section (active dot scales up, others fade). Clicking dot scrolls to section with `scrollIntoView({ behavior: 'smooth' })`. Add scroll direction indicator (arrow that fades in/out based on scroll position). Implement keyboard navigation (Space, arrow keys). Include progress bar showing position in overall page. Add content animations that trigger when section becomes active using `IntersectionObserver` (title slides up, content fades in). Support automatic progression (auto-advance every 5s, optional).

### *Infinite Scroll Loader*

Create infinite scroll list with smooth loading experience. Use `IntersectionObserver` on sentinel element at bottom of list. When sentinel visible, trigger loading state and fetch next page. Animate new items sliding up with stagger (50ms delay per item). Add spinner at bottom during loading. Implement "scroll to top" button that fades in after scrolling past first viewport. Button has elastic bounce on click and smooth scroll animation. Include empty state when no items exist. Add error state with retry button if loading fails. Support pull-to-refresh on mobile (drag down with threshold, show spinner, release to trigger). Track scroll position on unmount and restore on remount.

### *Scroll Spy Navigation*

Build navigation that highlights based on scroll position. Monitor section visibility with `IntersectionObserver` with `threshold: 0.5`. Update active nav item when section becomes most visible. Active item has background pill that morphs between items (use `layoutId` with Framer Motion). Add automatic smooth scroll when nav item clicked. Include underline that slides between items as alternative indicator. Nav sticky at top with backdrop blur (`sticky top-0 backdrop-blur-md bg-white/80`). Hide nav on scroll down, show on scroll up (track scroll direction with `useScroll`). Support nested navigation for subsections. Add keyboard accessibility (Tab, Enter). Include mobile hamburger menu that transforms to full-screen overlay.

---

# Gestures & Touch

### *Swipe Gestures*

Implement swipeable card stack (like Tinder). Use Framer Motion's `useDrag` hook with `dragConstraints`. Track drag distance and velocity. On release, if velocity or distance exceeds threshold, animate card off-screen in swipe direction (`x: 1000` or `x: -1000`, `rotate: 20` or `rotate: -20`, opacity to 0). Otherwise, snap back to center with spring physics. Add subtle rotation while dragging based on horizontal position. Next card in stack scales up slightly (0.95 to 1) as top card swipes. Include "like" and "nope" indicators that fade in based on swipe direction and distance. Add undo button that animates previous card back onto stack. Support keyboard controls (Arrow keys to swipe, Escape to undo).

### *Pull to Refresh*

Create pull-to-refresh interaction for mobile. Detect touch drag on scroll container when already at top (`scrollTop === 0`). Track drag distance with `useDrag` or touch events. Show pull indicator (circle with arrow) that grows and rotates based on drag distance. Apply resistance function (diminishing returns as drag increases). When released past threshold (80px), lock indicator in place, show spinner, trigger refresh callback. After refresh completes, animate indicator out with scale and fade. Add haptic feedback at threshold point. Support mouse drag for desktop testing. Include pull distance text ("Pull to refresh", "Release to refresh"). Style with branded colors and smooth cubic-bezier easing.

### *Long Press Actions*

Implement long press context menu. Use `onPointerDown` and `setTimeout` to detect press duration (500ms threshold). Show subtle scale effect during press (`scale: 0.98`). Display circular progress indicator around touch point that fills during hold. On complete, vibrate device (`navigator.vibrate`) and show context menu with animation (fade and scale from touch position). Menu options slide in with stagger. Add ripple effect from touch point. Cancel if pointer moves beyond threshold (20px) or on pointer up before completion. Include visual feedback during hold (pulse animation on target). Support keyboard activation (hold key down). Add accessibility announcement when menu appears.

### *Drag and Drop Reordering*

Create drag-and-drop list reordering. Use Framer Motion's drag functionality with `layout` prop. Dragged item lifts up with scale and shadow increase. Other items smoothly reposition using layout animations. Add drop zones with highlight effect when dragging over. Include auto-scroll when dragging near container edges. Show ghost placeholder in potential drop position (dashed outline). On drop, animate item to final position with spring physics. Add undo snackbar after reordering. Implement touch support with long press to initiate drag. Support multi-select for batch operations (Shift+click or Ctrl+click). Add constraints to prevent invalid drops. Include keyboard reordering (Alt+Arrow keys).

---

# Background Effects

### *Animated Gradients*

Create morphing background gradients. Use multiple gradient layers with keyframe animations rotating hue, saturation, and position. Base gradient: `bg-gradient-to-br from-purple-500 via-pink-500 to-orange-500` with `background-size: 400% 400%` animated with `background-position` changing over 15s. Add mesh gradient overlay with blur for depth. Include option for animated grain texture that subtly shifts. Implement dark mode variant with deeper, less saturated colors. Add parallax effect where gradient position shifts slightly based on cursor position. Include reduced motion support (static gradient for users who prefer less motion). Style with subtle noise texture for organic feel.

### *Particle Systems*

Build canvas-based particle system background. Use HTML5 Canvas or WebGL for performance. Generate particles with random positions, sizes, velocities. Update particle positions in `requestAnimationFrame` loop. Implement mouse interaction: particles attracted to cursor position within radius. Add connection lines between nearby particles that fade based on distance. Include color gradients on particles. Implement boundary collision (particles bounce off edges). Add depth with varying particle sizes and opacity based on z-index. Include flow field option (particles follow Perlin noise vector field). Optimize with spatial hashing for collision detection. Support dark/light theme colors. Add performance monitoring to adjust particle count based on frame rate.

### *Grid Animations*

Create animated background grid with perspective. Use CSS Grid or SVG. Apply 3D perspective transform (`perspective: 1000px`). Grid tiles have subtle pulse animation with staggered delays creating wave pattern. Add hover effect: tiles near cursor elevate and brighten. Implement glow effect on active tiles with box-shadow or SVG filters. Include option for flowing highlight that travels across grid using gradient mask animated with background-position. Add distortion effect on scroll using CSS transforms. Grid lines can fade in/out or shift position. Support theme integration (grid color matches brand). Add reduced motion version with static grid.

### *Blob Animations*

Create organic blob shapes that morph and float. Use SVG with multiple path elements. Animate path `d` attribute between different blob shapes using Framer Motion or CSS animations. Add floating animation with `translateX`, `translateY`, and `rotate` using different duration and delay for each axis (creates figure-8 patterns). Layer multiple blobs with different colors and blend modes (`mix-blend-mode: multiply` or `screen`). Add blur filters for soft edges. Implement mouse-following behavior: closest blob gravitates toward cursor. Include scale pulsing (1 to 1.1) with eased timing. Apply gradients within blobs that rotate. Use backdrop-filter on overlapping areas for frosted glass effect.

---

# Text Animations

### *Typewriter Effect*

Create realistic typewriter text animation. Split text into individual characters. Animate characters appearing sequentially with slight delay between each (50ms). Add blinking cursor at end of visible text (`animation: blink 1s step-end infinite`). Include randomized typing speed for organic feel (vary delay ±20ms). Add occasional pauses at punctuation (longer delay after periods, commas). Implement backspace effect for corrections: some characters delete and retype with different text. Add typing sound effect (optional, subtle click). Support multiple lines with return key pause. Include start delay and callback on completion. Make cursor animate away on finish or option to keep blinking.

### *Text Scramble Reveal*

Build text reveal with scramble effect. Show random characters that gradually resolve to actual text. Use array of random chars (letters, numbers, symbols). On mount, start with all random chars. Each character resolves to correct char at staggered intervals (50ms apart). Use `requestAnimationFrame` for smooth updates. Before resolving, each char cycles through 3-5 random chars. Add green/cyan color during scramble that fades to normal color on resolve. Include cursor effect that sweeps across during reveal. Works well for headers and tech-themed content. Support revealing on scroll into view using `IntersectionObserver`. Add optional glitch effect during reveal (brief horizontal offset).

### *Split Text Animations*

Create word or character-level animations on text. Split text into spans for each character or word. Animate with various effects: fade up (characters slide from `y: 20` to `y: 0` with opacity fade, staggered), rotate in (characters rotate from `rotateY: 90deg` to `0deg`), scale in (characters scale from `0` to `1`). Use Framer Motion with `staggerChildren: 0.03` on container. Add hover effect on words where characters wave up and down in sequence. Implement color gradient that sweeps across text animating each character's color. Include perspective transforms for 3D flip effects. Add blur to opacity animation for depth. Ensure accessibility: use `aria-label` with full text on container while individual characters are decorative.

### *Text Gradient Animation*

Create animated gradient text effect. Use `background-clip: text` with `-webkit-background-clip: text` and `color: transparent`. Animate gradient with keyframes adjusting `background-position` from `0% 0%` to `200% 200%` over 3s infinite. Use multi-stop gradient: `linear-gradient(90deg, #ff00ff, #00ffff, #ff00ff, #00ffff)` with `background-size: 200% 200%`. Add text shadow that matches gradient colors for glow effect. Include hover state that speeds up animation. Support dark mode with adjusted gradient colors. Add shimmer effect: white gradient overlay that sweeps across periodically. Combine with subtle scale pulse on hover. Implement smooth color transitions between theme changes.

---

# Form Animations

### *Multi-Step Form*

Build multi-step form with progress indicator and transitions. Show progress bar at top that fills based on current step. Each step slides in from right, previous step slides out to left with `AnimatePresence` and direction-aware animations. Add step numbers with checkmarks for completed steps. Include back button with slide-right animation. Implement validation per step: errors shake relevant fields and show messages with fade-in. Add "Save & Continue Later" option that stores form state in localStorage. Show summary slide at end before submission. Include loading state on submit with spinner replacing submit button. Add success animation: checkmark scales in with bounce, confetti particles burst. Support keyboard navigation (Tab between fields, Enter to advance).

### *Floating Labels*

Create input fields with floating label animation. Label starts inside input field as placeholder. On focus or when input has value, label animates upward and scales down (move from `y: 0` to `y: -24px`, scale from `1` to `0.85`). Add color change on focus (gray to blue). Include smooth transition with cubic-bezier easing. Add bottom border that expands from center on focus using pseudo-element scaling from `scaleX(0)` to `scaleX(1)`. Implement character counter that fades in on focus. Add validation state: success (green), error (red with shake). Support disabled state with reduced opacity. Include autofill detection with color transition. Make label background match field background to avoid text overlap.

### *Checkbox & Radio Animations*

Create custom animated checkboxes and radios. Hide default input, style label as button. Checkbox: animate checkmark SVG path drawing using `stroke-dasharray` and `stroke-dashoffset`. Add scale and rotation on check. Include background color fill animation with elastic ease. Radio: animate inner circle scaling from 0 to 1 on selection with spring physics. Add outer ring pulse effect on click. Implement hover states with border color transition and subtle scale. Include focus visible styles with animated ring. Support disabled state with reduced opacity and grayscale filter. Add group animations where selecting one option deselects others with smooth transitions. Include haptic feedback on mobile. Make labels animate (text color, background) on state change.

---

# Mobile-Specific Interactions

### *Bottom Sheet*

Create mobile bottom sheet drawer. Sheet slides up from bottom with `translateY: 100%` to `0%` animation. Add drag handle at top that hints at draggability. Implement drag gesture with `useDrag`: user can drag sheet down to close or up to expand. Add snap points (half, full height) with spring physics. Include backdrop that fades in with sheet, dismisses sheet on tap. Sheet content scrolls independently when fully expanded. Add header that becomes sticky on scroll. Implement swipe-down-to-close when content scrolled to top. Include haptic feedback at snap points. Support nested scrolling: prevent body scroll when sheet open. Add keyboard push animation (sheet moves up when keyboard appears). Style with rounded top corners and shadow.

### *Touch Feedback Ripples*

Create material design ripple effect for touch interactions. On touch/click, create circular expanding element from exact touch coordinates. Use absolute positioning with touch coords as center. Animate scale from 0 to 2.5 and opacity from 0.3 to 0 over 600ms. Use cubic-bezier easing for material motion. Clip ripple to parent bounds with `overflow: hidden` on parent. Add multiple ripples if user taps rapidly (queue animations). Include color variant based on element type (buttons, cards, list items). Support dark mode with adjusted ripple color. Implement on all interactive elements globally using event delegation. Add accessibility: keyboard interactions (Enter, Space) trigger ripple from element center instead of undefined coordinates.

### *Pull-Out Side Menu*

Build slide-out side navigation drawer for mobile. Menu starts off-screen left (`translateX: -100%`). Add hamburger button that animates to X icon: top and bottom lines rotate 45deg and -45deg, middle line fades out. On open, menu slides in with `transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1)`. Add backdrop overlay that fades in and dismisses menu on tap. Menu items slide in from left with stagger after menu opens. Include current page indicator with animated background pill. Implement swipe-from-edge gesture to open (detect touch within 20px of left edge). Support close on swipe left. Add nested menu items that expand/collapse with height animation. Include header with user profile that blurs out when scrolling menu content.

---

# Advanced Effects

### *Glassmorphism*

Create frosted glass effect components. Use `backdrop-filter: blur(10px)` with semi-transparent background (`bg-white/20`). Add subtle border with gradient: `border: 1px solid rgba(255, 255, 255, 0.2)`. Include box shadow with spread for depth. Layer multiple blur elements for depth perception. Add subtle gradient overlay that shifts on hover. Implement on cards, navigation bars, modals. Include fallback for browsers without backdrop-filter support (solid background with higher opacity). Add noise texture for organic feel. Support dark mode with adjusted colors. Include hover state with increased blur and brightness. Combine with other effects: slight scale, glow, shadow changes.

### *Parallax Mouse Tracking*

Create elements that move based on mouse position for depth. Track mouse coordinates with `mousemove` listener. Calculate distance from element center to cursor. Apply transform based on distance: closer elements move more (multiply by depth factor). Use `translateX` and `translateY` with values proportional to mouse offset from center. Add smooth following with lerp (current position += (target position - current position) * 0.1) in `requestAnimationFrame` loop. Layer multiple elements with different depth values (foreground moves more than background). Include 3D rotation: elements tilt toward cursor. Add magnetic effect: elements lean toward cursor within threshold. Reset to center on mouse leave with smooth transition. Support touch devices with gyroscope tilting alternative.

### *Text Masks & Clip Paths*

Create text with video or image visible through it. Use large heading text with `background-clip: text` and `-webkit-background-clip: text`. Set `color: transparent` so background shows through. Background can be video, animated gradient, or image. For video: use `<video>` element with `object-fit: cover` and play inline. Add scroll parallax where background moves at different speed than text. Include hover effect: background scales up slightly. Implement animated gradient that shifts colors continuously. Add stroke around text with `-webkit-text-stroke: 1px white`. Ensure fallback color for unsupported browsers. Combine with scroll-triggered animations: text and background reveal together. Support dark mode with filter adjustments.

### *Lottie Animations*

Integrate Lottie JSON animations. Use `lottie-web` or `@lottiefiles/react-lottie-player`. Load animation JSON with `fetch` or import. Control playback programmatically: play, pause, stop, seek to specific frame. Trigger animation on scroll: map scroll progress to animation frame using `useScroll` and `useTransform`. Implement hover states that play animation forward, reverse on mouse leave. Add click interaction that plays animation once. Include loading state while JSON fetches. Support reduced motion: show static final frame. Add speed controls. Implement loop with custom iteration count. Use for icons, illustrations, loading states, success/error feedback. Optimize JSON size (remove unused assets, simplify paths). Include accessibility: provide alternative text or description.

---

# Performance Patterns

### *Virtual Scroll Lists*

Build performant list that renders only visible items. Calculate visible range based on scroll position and container height. Render items in visible range plus buffer (5 items above/below). Use absolute positioning with dynamic `top` values based on item heights. Track scroll position with `onScroll` handler throttled to 16ms (60fps). Implement smooth scrolling by translating container. Add scroll-to-index function that calculates offset. Handle variable height items by storing measured heights. Include placeholder skeleton for items while measuring. Add scroll restoration on navigation back. Implement infinite scroll by checking if scrolled to bottom and loading more. Support horizontal virtual scrolling. Ensure accessibility: all items remain in DOM for screen readers (use `aria-hidden` on non-visible items).

### *Debounced Search Input*

Create search input with optimized query handling. Use `useState` for input value, update on every keystroke for responsive UI. Implement `useDebounce` hook that delays value change (300ms typical). Only trigger search when debounced value changes. Show loading state during debounce period and while searching. Include clear button that fades in when input has value. Add search icon with loading spinner that replaces it during search. Implement instant results preview dropdown. Cache results to avoid redundant queries. Add keyboard navigation in results (arrow keys, Enter to select). Include recent searches that appear on focus. Support cancel ongoing request when new search starts. Add analytics tracking on successful searches (debounced to avoid spam).

### *Optimized Image Loading*

Implement progressive image loading pattern. Show low-quality image placeholder (LQIP) or blur hash immediately. Load full resolution image in background. When loaded, crossfade from placeholder to full image with `opacity: 0` to `1` transition. Use `onLoad` callback on image element. Include loading skeleton while initial placeholder loads. Add error state with retry button if image fails. Implement lazy loading with `IntersectionObserver`: only load images when near viewport. Use native `loading="lazy"` as fallback. Include zoom on hover with scale transform and cursor change. Add srcset for responsive images. Implement lightbox modal on click with animated expansion from thumbnail position. Ensure alt text for accessibility.

---

# Accessibility Considerations

### *Focus Management*

Implement visible focus indicators on all interactive elements. Use `:focus-visible` to show outline only for keyboard navigation. Style focus ring with brand colors, sufficient contrast (3:1 minimum against background). Add animated focus ring that scales in with spring physics. Implement focus trap in modals: Tab cycles only through modal elements, Escape closes modal and returns focus to trigger element. Include skip links at page top for keyboard users to bypass navigation. Use `focus()` method to move focus appropriately on route changes or dynamic content loads. Add focus restoration when dismissing UI elements. Implement roving tabindex for component groups (radio groups, tabs). Include ARIA labels and descriptions for screen reader context.

### *Reduced Motion*

Respect user's motion preferences. Use `@media (prefers-reduced-motion: reduce)` media query. For reduced motion users, disable or simplify animations: use instant transitions instead of animated ones, remove parallax effects, disable auto-playing animations. Implement with CSS variables or JavaScript feature detection. Provide all animations with reduced-motion alternatives: crossfades instead of slides, simple opacity changes instead of complex transforms. Include toggle in settings for users to control animation intensity regardless of system preference. Ensure critical functionality works without animations. Test all interactions with reduced motion enabled. Document accessibility considerations in component docs.

### *Screen Reader Announcements*

Implement proper ARIA live regions for dynamic content. Use `aria-live="polite"` for non-critical updates, `aria-live="assertive"` for important alerts. Add `role="status"` for status messages. Include `aria-atomic="true"` when entire region should be announced. Implement loading announcements for async operations. Add success/error announcements for form submissions. Use `aria-label` for icon-only buttons. Include `aria-describedby` for additional context. Add `aria-expanded`, `aria-controls`, `aria-owns` for collapsible sections. Implement keyboard shortcuts with visual indicators and announcements. Provide text alternatives for non-text content. Ensure animations don't interfere with screen reader operation. Test with actual screen readers (NVDA, JAWS, VoiceOver).

---

# Implementation Tips

- Always use `transform` and `opacity` for animations when possible (GPU accelerated)
- Avoid animating `width`, `height`, `top`, `left` (causes layout recalc)
- Use `will-change` sparingly and only for elements actively animating
- Implement intersection observers with appropriate thresholds and margins
- Debounce/throttle scroll and resize handlers
- Use CSS containment (`contain: layout style paint`) for isolated components
- Prefer CSS transitions for simple state changes, JavaScript for complex choreography
- Use `requestAnimationFrame` for JavaScript animations
- Implement loading states for all async operations
- Test all animations at 6x slowdown in Chrome DevTools
- Ensure all interactive elements have minimum 44x44px touch targets
- Provide visual feedback within 100ms of user interaction
- Use spring physics for natural motion (Framer Motion: `type: "spring"`)
- Implement proper easing curves (cubic-bezier) for brand-appropriate motion
- Test across devices: desktop, tablet, mobile
- Validate accessibility with automated tools and manual testing
- Consider data usage for auto-playing videos and heavy animations
- Document animation intent and behavior for team members

---

# Quick Reference - Common Animation Values

**Durations:**

- Micro-interactions: 100-200ms
- Small UI changes: 200-300ms
- Medium transitions: 300-500ms
- Large transitions: 500-700ms
- Page transitions: 300-400ms

**Easing:**

- Ease-out: entering UI, `cubic-bezier(0.0, 0, 0.2, 1)`
- Ease-in: exiting UI, `cubic-bezier(0.4, 0, 1, 1)`
- Ease-in-out: moving through, `cubic-bezier(0.4, 0, 0.2, 1)`
- Spring: natural motion, `type: "spring", stiffness: 300, damping: 30`

**Common Transform Origins:**

- Dropdown: `top center`
- Tooltip: varies by position
- Modal: `center`
- Sidebar: `left center` or `right center`