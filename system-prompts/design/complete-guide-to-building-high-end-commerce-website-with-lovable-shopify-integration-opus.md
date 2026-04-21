# Complete Guide to Building a High-End E-Commerce Website with Lovable + Shopify Integration [Opus]

## Executive Summary

This comprehensive guide walks you through building a luxury-grade, conversion-optimized e-commerce website using Lovable's AI-powered development platform with full Shopify integration. Following modern 2024-2025 design standards, this guide covers everything from initial planning through launch, ensuring your store meets the highest standards of design excellence, accessibility, performance, and user experience.

---

## Phase 1: Strategic Planning & Discovery

### Step 1.1: Define Your Brand Foundation

Before writing a single prompt, establish your design system fundamentals:

Brand Identity Checklist:

- [ ]  Primary brand colors (limit to 2-3 core colors)
- [ ]  Secondary/accent colors (1-2 complementary shades)
- [ ]  Typography hierarchy (heading font + body font pairing)
- [ ]  Logo variations (primary, secondary, favicon)
- [ ]  Photography style (lifestyle, product-focused, editorial)
- [ ]  Voice and tone (luxury, approachable, technical, playful)

Example Brand Configuration:

```
Primary: #1A1A1A (Rich Black)
Secondary: #B8860B (Antique Gold)
Accent: #F5F5DC (Cream)
Heading Font: "Playfair Display" (Serif)
Body Font: "Inter" (Sans-serif)
Button Style: Rounded corners (8px), subtle shadows

```

> Pro Tip: High-end brands typically use restrained color palettes, generous white space, and sophisticated typography pairings. Avoid more than 3 primary colors.
> 

### Step 1.2: Competitive Analysis & Wireframing

Research Checklist:

- [ ]  Analyze 5-10 competitor sites in your niche
- [ ]  Document navigation patterns that work
- [ ]  Screenshot UI elements you want to emulate
- [ ]  Note conversion tactics (urgency indicators, social proof placement)

Recommended Site Structure for E-Commerce:

```
├── Homepage
│   ├── Hero Section
│   ├── Featured Products
│   ├── Benefits/Value Proposition
│   ├── Product Categories
│   ├── Social Proof/Reviews
│   ├── Content/Blog Preview
│   ├── Newsletter Signup
│   └── Footer
├── Collection Pages
├── Product Detail Pages
├── Cart/Checkout
├── About Page
├── Contact Page
└── Policy Pages (Shipping, Returns, Privacy)

```

---

## Phase 2: Project Setup & Knowledge Configuration

### Step 2.1: Initialize Your Lovable Project

Action: Create a new Lovable project and configure it for optimal AI collaboration.

Navigate to: Project Settings → Manage Knowledge

Master Configuration Prompt:

```
Role: You are an expert world-class web designer and senior frontend developer specializing in luxury e-commerce experiences. Follow component-driven architecture and modern React best practices throughout this project.

Development Approach:
- We will build iteratively, one section at a time
- Each instruction will be specific and focused
- You will write clean, scalable, maintainable code

Design System Requirements:
- Color Mode: Light mode only
- Primary Color: [YOUR_PRIMARY_COLOR]
- Secondary Color: [YOUR_SECONDARY_COLOR]
- Accent Color: [YOUR_ACCENT_COLOR]
- Heading Font: [YOUR_HEADING_FONT]
- Body Font: [YOUR_BODY_FONT]
- Border Radius: 8px (buttons), 12px (cards), 16px (sections)
- Shadow Style: Subtle (0 2px 8px rgba(0,0,0,0.08))

Code Architecture Rules:
1. Create reusable components for all repeated elements (buttons, cards, badges, inputs)
2. Each page section must be its own component file
3. Use Tailwind CSS utility classes exclusively - no inline styles
4. Define global Tailwind configurations in tailwind.config.js for colors, fonts, and spacing
5. Implement proper TypeScript interfaces for all data structures
6. Follow mobile-first responsive design (sm: → md: → lg: → xl:)

Accessibility Requirements:
- All images must have descriptive alt text
- Interactive elements must be keyboard navigable
- Color contrast must meet WCAG 2.1 AA standards (4.5:1 minimum)
- Form inputs must have associated labels
- Focus states must be visible

Performance Requirements:
- Lazy load images below the fold
- Use proper image formats (WebP with fallbacks)
- Minimize component re-renders
- Implement loading states for async operations

Naming Conventions:
- Components: PascalCase (ProductCard.tsx)
- Functions: camelCase (handleAddToCart)
- CSS Classes: Tailwind utilities only
- Files: PascalCase for components, kebab-case for utilities

```

> Critical: This knowledge base is referenced in every AI interaction. Invest time making it comprehensive—it's the foundation of your entire build quality.
> 

### Step 2.2: Configure Global Tailwind Styles

Initial Prompt:

```
Set up the Tailwind configuration with our brand's design tokens:

Colors:
- primary: [YOUR_PRIMARY_HEX]
- secondary: [YOUR_SECONDARY_HEX]
- accent: [YOUR_ACCENT_HEX]
- background: #FFFFFF
- foreground: #1A1A1A
- muted: #F5F5F5
- muted-foreground: #6B7280

Typography:
- Font family for headings: [YOUR_HEADING_FONT]
- Font family for body: [YOUR_BODY_FONT]
- Heading sizes: h1 (48px/56px), h2 (36px/44px), h3 (24px/32px), h4 (20px/28px)
- Body sizes: lg (18px), base (16px), sm (14px)
- Line heights: tight (1.2), normal (1.5), relaxed (1.75)

Spacing scale extensions:
- 18: 4.5rem
- 22: 5.5rem
- 26: 6.5rem

Create utility classes for:
- .container-main (max-w-7xl mx-auto px-4 sm:px-6 lg:px-8)
- .section-padding (py-16 md:py-24 lg:py-32)
- .heading-primary (font-heading text-4xl md:text-5xl lg:text-6xl font-bold tracking-tight)
- .heading-secondary (font-heading text-3xl md:text-4xl font-semibold)
- .body-large (font-body text-lg leading-relaxed text-muted-foreground)

```

---

## Phase 3: Building the Design System Components

### Step 3.1: Create Core UI Components

Before building pages, establish your reusable component library:

Prompt for Button Component:

```
Create a Button component with the following variants:

Variants:
1. Primary: Solid background with primary color, white text, hover darkens 10%
2. Secondary: Outlined with primary color border, transparent background, hover fills
3. Ghost: No border, transparent background, hover shows subtle background
4. Link: Text only, underline on hover

Sizes:
- sm: px-4 py-2 text-sm
- md: px-6 py-3 text-base (default)
- lg: px-8 py-4 text-lg

Features:
- Loading state with spinner animation
- Disabled state with reduced opacity
- Icon support (left or right position)
- Full width option
- Proper focus ring for accessibility
- Smooth transition animations (150ms)

Export as: components/ui/Button.tsx

```

Prompt for Product Card Component:

```
Create a ProductCard component for displaying products in grids:

Structure:
1. Image container (aspect-square, overflow-hidden, rounded-lg)
2. Quick view overlay on hover (desktop only)
3. Product title (truncate after 2 lines)
4. Price display (current price, compare-at price with strikethrough)
5. Color swatches (if variants exist, max 4 visible)
6. Add to Cart button (appears on hover for desktop, always visible on mobile)

Features:
- Skeleton loading state for images
- Wishlist heart icon in top-right corner
- "Sale" or "New" badge support
- Hover zoom effect on image (scale 1.05)
- Link wrapper for product detail page
- Proper image lazy loading

Responsive behavior:
- Mobile: Full width card, touch-friendly tap areas (min 44px)
- Tablet: 2-column grid
- Desktop: 3-4 column grid

Export as: components/products/ProductCard.tsx

```

Prompt for Section Wrapper:

```
Create a Section component that standardizes all page sections:

Props:
- id: string (for anchor navigation)
- className: string (additional classes)
- background: 'white' | 'muted' | 'primary' | 'gradient'
- spacing: 'sm' | 'md' | 'lg' (controls vertical padding)
- container: boolean (whether to wrap in max-width container)

Default styling:
- Consistent vertical padding based on spacing prop
- Proper container width with horizontal padding
- Background color options
- Semantic HTML section tag

Export as: components/ui/Section.tsx

```

### Step 3.2: Create Additional UI Components

Component Checklist:

- [ ]  Badge (variant: default, success, warning, error)
- [ ]  Card (with header, body, footer slots)
- [ ]  Input (with label, error state, helper text)
- [ ]  Select dropdown
- [ ]  Modal/Dialog
- [ ]  Accordion
- [ ]  Tabs
- [ ]  Rating stars display
- [ ]  Price display (handles sale prices, currency formatting)
- [ ]  Quantity selector
- [ ]  Image gallery/carousel

---

## Phase 4: Building Core Page Sections

### Step 4.1: Hero Section (Above the Fold)

The hero section is critical for first impressions and conversion. It must:

- Communicate value proposition in under 3 seconds
- Include a clear call-to-action
- Feature high-quality imagery
- Load quickly (LCP target: under 2.5 seconds)

Comprehensive Hero Prompt:

```
Create a hero section for our e-commerce homepage with these specifications:

Layout (Desktop - lg:):
- Two-column layout (content left 45%, visual right 55%)
- Content column contains text stack and CTAs
- Visual column contains product imagery showcase

Content Elements (Left Column):
1. Trust badge: Star rating (4.8/5) with review count (2,847 reviews) - small, subtle
2. Eyebrow text: Category or brand identifier
3. Main headline: "[YOUR_HEADLINE]" - use heading-primary class
4. Subheadline: "[YOUR_SUBHEADLINE]" - use body-large class, max 2 lines
5. Feature highlights: 3 bullet points with check icons (e.g., "Free shipping over $100")
6. CTA group:
   - Primary button: "Shop Collection" → links to /collections/all
   - Secondary button: "Learn More" → smooth scroll to benefits section
7. Social proof micro-element: "Join 50,000+ happy customers"

Visual Elements (Right Column):
1. Hero product image (large, high-quality)
2. Floating accent images (2-3 smaller product shots positioned absolutely)
3. Subtle background decoration (gradient orb or pattern)

Responsive Behavior:
- Mobile: Single column, image above text, stacked CTAs (full width)
- Tablet: Single column with larger text
- Desktop: Two-column as described

Performance:
- Hero image uses priority loading (no lazy load)
- Implement proper image sizing with srcSet
- Add subtle entrance animations (fade-in, slide-up) using CSS

Create as: components/sections/HeroSection.tsx

```

> Design Best Practice: Hero images should be minimum 1920px wide for desktop, with optimized versions at 1200px, 800px, and 400px for responsive delivery.
> 

### Step 4.2: Enable Shopify Integration

Critical Integration Prompt:

```
Enable Shopify Storefront API integration for this project with the following configuration:

API Configuration:
- Use Shopify Storefront API version 2024-10 (or latest stable)
- Configure for headless commerce architecture
- Set up proper environment variables for API credentials
- Implement GraphQL client for Storefront API queries

Required Functionality:
1. Fetch all products with pagination support
2. Fetch single product by handle
3. Fetch collections and products within collections
4. Create cart (checkout) session
5. Add/remove/update cart items
6. Fetch cart contents
7. Generate checkout URL

Data Types to Create:
- Product interface (id, title, handle, description, images, variants, price)
- ProductVariant interface (id, title, price, compareAtPrice, available, selectedOptions)
- Collection interface (id, title, handle, description, products)
- Cart interface (id, lines, totalAmount, checkoutUrl)
- CartLine interface (id, quantity, variant, product)

State Management:
- Use Zustand for cart state
- Persist cart ID in localStorage
- Implement optimistic updates for cart operations

Error Handling:
- Graceful error states for API failures
- Retry logic for transient failures
- User-friendly error messages

Create necessary files:
- lib/shopify/client.ts (API client configuration)
- lib/shopify/queries.ts (GraphQL queries)
- lib/shopify/types.ts (TypeScript interfaces)
- hooks/useProducts.ts (React Query hook)
- hooks/useCart.ts (cart operations hook)
- stores/cartStore.ts (Zustand store)

```

Post-Integration Verification:

- [ ]  Products display correctly from Shopify
- [ ]  Cart operations work (add, remove, update quantity)
- [ ]  Checkout URL redirects to Shopify checkout
- [ ]  Variant selection updates price correctly

### Step 4.3: Product Grid Section

```
Create a featured products section that fetches from Shopify:

Section Structure:
1. Section header:
   - Eyebrow text: "Our Collection"
   - Heading: "Best Sellers" (or dynamic collection title)
   - Subheading: Brief description
   - View all link (aligned right on desktop)

2. Product grid:
   - Use the ProductCard component created earlier
   - 4-column grid on desktop (lg:grid-cols-4)
   - 2-column on tablet (md:grid-cols-2)
   - 1-column on mobile with horizontal scroll option
   - Display first 8 products

3. States:
   - Loading: Show 8 skeleton cards
   - Empty: Friendly message with CTA to browse collections
   - Error: Retry button with error message

4. Optional filtering tabs:
   - "All", "New Arrivals", "Sale" (filter client-side or refetch)

Fetch products using the useProducts hook with:
- first: 8
- sortKey: BEST_SELLING

Create as: components/sections/FeaturedProducts.tsx

```

### Step 4.4: Value Proposition / Benefits Section

```
Create a benefits section that communicates our unique value:

Layout:
- Two-column on desktop (content left, image right)
- Single column on mobile (image first, then content)

Content Column:
1. Eyebrow: "Why Choose Us"
2. Heading: "[YOUR_VALUE_PROP_HEADLINE]"
3. Body paragraph: 2-3 sentences expanding on the headline
4. Benefits list (4-6 items):
   Each item has:
   - Icon (use Lucide icons)
   - Title (bold, one line)
   - Description (1-2 sentences, muted color)
5. CTA button: "Explore Our Process" or similar

Image Column:
- Large lifestyle image showing product in use
- Subtle floating stats card overlay (e.g., "10,000+ Orders Shipped")

Design Notes:
- Use alternating background (muted) to break up page flow
- Add subtle animation on scroll (elements fade in)
- Icons should be consistent in style (outlined or filled, not mixed)

Create as: components/sections/BenefitsSection.tsx

```

### Step 4.5: Social Proof Section

```
Create a social proof section with customer testimonials:

Layout Options (implement as prop):
Option A - Carousel:
- Auto-playing carousel with manual navigation
- 3 testimonials visible on desktop, 1 on mobile
- Dots pagination below

Option B - Grid:
- 3-column grid on desktop
- Stacked on mobile

Testimonial Card Structure:
1. Quote text (italic, larger font)
2. Star rating (5 stars visual)
3. Customer name
4. Customer title/location (optional)
5. Customer photo (circular, 48px)
6. Verified purchase badge (optional)

Section Header:
- Centered alignment
- Eyebrow: "Customer Love"
- Heading: "What Our Customers Say"
- Optional: Integration callout (e.g., "4.9/5 on Trustpilot")

Additional Elements:
- Logos of press mentions or trust badges below testimonials
- "Read More Reviews" link to dedicated reviews page

Create as: components/sections/TestimonialsSection.tsx

```

### Step 4.6: Collection/Category Navigation

```
Create a category showcase section for browsing collections:

Layout:
- 3-column grid on desktop
- 2-column on tablet
- Vertical stack on mobile

Category Card Structure:
- Full-bleed background image with overlay gradient
- Category name (white text, centered)
- Product count badge
- Hover effect: Image zoom + overlay lightens
- Click links to /collections/[handle]

Categories to Display:
1. [CATEGORY_1_NAME] - Image: [provide or describe]
2. [CATEGORY_2_NAME] - Image: [provide or describe]
3. [CATEGORY_3_NAME] - Image: [provide or describe]

Variations:
- One large featured card + 2 smaller (masonry style)
- Or equal-sized cards

Section Header:
- "Shop by Category"

Create as: components/sections/CategoryShowcase.tsx

```

### Step 4.7: Newsletter Signup Section

```
Create a newsletter signup section:

Layout:
- Full-width with brand accent background color
- Centered content with max-width constraint
- Padding generous (section-padding class)

Content:
1. Heading: "Join Our Community"
2. Subheading: "Get exclusive offers, early access to new products, and style inspiration delivered to your inbox."
3. Form:
   - Email input (large, white background)
   - Submit button (contrasting color)
   - Inline layout on desktop, stacked on mobile
4. Privacy note: "We respect your privacy. Unsubscribe anytime."
5. Optional: Social media links row

Functionality:
- Form validation (valid email required)
- Loading state on submit
- Success state (thank you message replaces form)
- Error state (inline error message)

Integration Note:
- For now, implement as UI only with console log on submit
- Add comment for future integration with Klaviyo/Mailchimp

Create as: components/sections/NewsletterSection.tsx

```

### Step 4.8: Footer

```
Create a comprehensive footer:

Structure (4-column on desktop):

Column 1 - Brand:
- Logo
- Brief tagline (1-2 sentences)
- Social media icons (Instagram, Facebook, Twitter, Pinterest, TikTok)

Column 2 - Shop:
- All Products
- New Arrivals
- Best Sellers
- Sale
- Gift Cards

Column 3 - Help:
- FAQ
- Shipping & Returns
- Size Guide
- Contact Us
- Track Order

Column 4 - Company:
- Our Story
- Sustainability
- Careers
- Press
- Affiliate Program

Bottom Bar:
- Copyright: "© 2025 [Brand Name]. All rights reserved."
- Legal links: Privacy Policy | Terms of Service | Accessibility
- Payment icons (Visa, Mastercard, Amex, PayPal, Apple Pay, Shop Pay)
- Country/currency selector (optional)

Responsive:
- Desktop: 4-column grid
- Tablet: 2x2 grid
- Mobile: Accordion-style (tap to expand each column)

Design:
- Background: Primary dark color or muted
- Text: Light color for contrast
- Links: Subtle hover underline effect

Create as: components/sections/Footer.tsx

```

---

## Phase 5: Product Detail Page (PDP)

### Step 5.1: Product Page Structure

```
Create a product detail page at route /product/:handle with these sections:

Page Structure:
1. Breadcrumb navigation
2. Product hero (image gallery + product info)
3. Product description tabs
4. Related products section
5. Recently viewed products

Product Hero Layout (Desktop):
- Left side (55%): Image gallery
- Right side (45%): Product information

Image Gallery Requirements:
- Main large image (aspect-square or 4:5)
- Thumbnail strip below or beside main image
- Click thumbnail to change main image
- Zoom on hover (desktop) or pinch-to-zoom (mobile)
- Support for multiple product images
- Video thumbnail support if product has video

Product Information Stack:
1. Breadcrumb: Home > Collection > Product Name
2. Product title (heading-secondary)
3. Price display:
   - Current price (large, bold)
   - Compare-at price (strikethrough, muted) if on sale
   - "Save X%" badge if on sale
4. Rating stars with review count link
5. Short description (2-3 lines max)
6. Variant selectors:
   - Color swatches (visual circles with color)
   - Size dropdown or button group
   - Show "Only X left" if inventory low
7. Quantity selector (- / number / +)
8. Add to Cart button (full width, primary)
9. Buy Now button (secondary, skips cart) - optional
10. Trust badges row (Free shipping, Easy returns, Secure checkout)
11. Accordion sections:
    - Description (expanded by default)
    - Size Guide
    - Shipping & Returns
    - Care Instructions

Data Fetching:
- Fetch product by handle using Shopify Storefront API
- Handle loading state with skeleton
- Handle product not found (404 page)
- Update URL with selected variant (e.g., ?variant=123)

Create as: pages/ProductPage.tsx
With components:
- components/product/ImageGallery.tsx
- components/product/ProductInfo.tsx
- components/product/VariantSelector.tsx
- components/product/ProductTabs.tsx

```

### Step 5.2: Add to Cart Functionality

```
Implement the Add to Cart functionality on the product page:

Flow:
1. User selects variant (color, size)
2. User adjusts quantity
3. User clicks "Add to Cart"
4. Button shows loading state
5. Item added to cart (Shopify Storefront API)
6. Success feedback:
   - Button briefly shows checkmark + "Added!"
   - Cart icon in header updates count
   - Cart drawer slides in from right (optional)
7. If error: Show inline error message, button returns to normal

Cart Drawer (slide-in panel):
- Header: "Your Cart (X items)"
- Cart items list:
  - Product image (small)
  - Product title
  - Variant info (Color: Black, Size: M)
  - Quantity selector
  - Item price
  - Remove button (trash icon)
- Subtotal
- Shipping note: "Free shipping on orders over $100"
- Checkout button (primary, full width)
- Continue Shopping link
- Empty state: "Your cart is empty" with shop link

Technical Requirements:
- Use Zustand cart store
- Optimistic UI updates (update UI before API confirms)
- Rollback on error
- Persist cart across sessions (localStorage cart ID)

Create/update:
- components/cart/CartDrawer.tsx
- components/cart/CartItem.tsx
- hooks/useCart.ts (add addToCart, removeFromCart, updateQuantity)

```

---

## Phase 6: Responsive Design & Mobile Optimization

### Step 6.1: Mobile-First Audit

After building sections, conduct a systematic mobile review:

Responsive Testing Checklist:

- [ ]  Hero section readable and CTAs accessible
- [ ]  Product grid scrolls or stacks properly
- [ ]  All buttons meet 44px minimum tap target
- [ ]  Images don't overflow container
- [ ]  Text doesn't break awkwardly
- [ ]  Forms are usable on mobile keyboard
- [ ]  Navigation is accessible (hamburger menu)
- [ ]  Cart drawer doesn't cause horizontal scroll

Common Fix Prompts:

Overflow Issues:

```
The product carousel is causing horizontal scroll on mobile. Fix this by:
1. Adding overflow-hidden to the container
2. Ensuring carousel items are properly contained
3. Testing on 375px width viewport
Do not affect the desktop layout.

```

Spacing Adjustments:

```
On mobile (below md breakpoint):
- Reduce section padding from py-24 to py-12
- Reduce heading sizes by one step
- Stack the two-column layouts vertically
- Add more vertical spacing between stacked elements
Keep desktop layouts unchanged.

```

Touch Target Compliance:

```
Audit all interactive elements for WCAG touch target compliance:
- Minimum 44x44px tap area for all buttons and links
- Add padding if needed to increase tap area
- Ensure spacing between targets prevents mis-taps
Apply fixes to mobile breakpoints only where needed.

```

### Step 6.2: Navigation Implementation

```
Create a responsive navigation header:

Desktop Header (lg: and up):
- Logo (left)
- Main navigation links (center):
  - Shop (dropdown with collections)
  - New Arrivals
  - Best Sellers
  - About
  - Contact
- Utility icons (right):
  - Search icon (opens search modal)
  - Account icon (links to account or login)
  - Wishlist icon with count badge
  - Cart icon with item count badge

Mobile Header (below lg:):
- Hamburger menu icon (left)
- Logo (center)
- Cart icon (right)

Mobile Menu (slide-in from left):
- Full-height overlay
- Logo at top
- Main navigation (stacked, large touch targets)
- Nested dropdowns for collections
- Account and wishlist links
- Close button (X)

Dropdown Menus (Desktop):
- Open on hover with slight delay
- Mega menu style for "Shop" with collection images
- Smooth animation (fade + slide)

Header Behavior:
- Sticky on scroll (remains fixed at top)
- Background blur effect when scrolling (backdrop-blur)
- Hide on scroll down, show on scroll up (optional, advanced)

Create as:
- components/layout/Header.tsx
- components/layout/MobileMenu.tsx
- components/layout/DesktopNav.tsx
- components/layout/MegaMenu.tsx

```

---

## Phase 7: Performance Optimization

### Step 7.1: Image Optimization

```
Implement image optimization across the site:

1. Create an OptimizedImage component that:
   - Uses Shopify's image CDN URL transformations
   - Generates srcSet for responsive images (400w, 800w, 1200w, 1600w)
   - Sets appropriate sizes attribute based on layout context
   - Lazy loads images below the fold
   - Shows skeleton placeholder while loading
   - Handles error state with fallback image
   - Supports WebP format with JPEG fallback

2. Apply to:
   - Product card images
   - Product detail gallery images
   - Hero images (except main hero which should be priority)
   - Category card images
   - Testimonial avatars

3. Add loading="lazy" to all images except:
   - Hero section main image
   - First 2 products visible on initial load

Example usage:
<OptimizedImage
  src={product.images[0].url}
  alt={product.title}
  width={400}
  height={400}
  sizes="(max-width: 768px) 100vw, (max-width: 1024px) 50vw, 25vw"
  priority={false}
/>

Create as: components/ui/OptimizedImage.tsx

```

### Step 7.2: Code Splitting & Loading States

```
Implement performance optimizations:

1. Code Splitting:
   - Lazy load route components using React.lazy()
   - Create loading fallback component (spinner + logo)
   - Split cart drawer into separate chunk (not needed on initial load)

2. Loading States:
   - Create Skeleton components for:
     - ProductCard skeleton
     - ProductPage skeleton
     - TextBlock skeleton
     - ImagePlaceholder skeleton
   - Use for all async data fetching

3. React Query Optimization:
   - Configure stale time appropriately (5 minutes for products)
   - Enable refetch on window focus for cart
   - Prefetch product data on card hover

4. Bundle Analysis:
   - Ensure no duplicate dependencies
   - Tree-shake unused icon imports

Create as:
- components/ui/Skeleton.tsx (variants for different shapes)
- components/ui/LoadingSpinner.tsx
- Update router configuration for lazy loading

```

---

## Phase 8: Accessibility Compliance

### Step 8.1: Accessibility Audit & Fixes

```
Conduct an accessibility audit and implement fixes:

1. Semantic HTML:
   - Use proper heading hierarchy (only one h1 per page)
   - Use nav, main, section, article, aside appropriately
   - Use button for actions, a for navigation

2. ARIA Labels:
   - Add aria-label to icon-only buttons
   - Add aria-expanded to accordion triggers
   - Add aria-hidden to decorative images
   - Add role="img" with aria-label to icon components

3. Focus Management:
   - Visible focus rings on all interactive elements
   - Focus trap in modals and drawers
   - Return focus to trigger when modal closes
   - Skip-to-content link at top of page

4. Color Contrast:
   - Verify all text meets 4.5:1 contrast ratio
   - Ensure form error states are not color-only
   - Add underlines to links within body text

5. Form Accessibility:
   - All inputs have associated labels
   - Error messages linked with aria-describedby
   - Required fields indicated with aria-required

6. Screen Reader Optimization:
   - Add visually-hidden text for context where needed
   - Price display: "Current price: $99" not just "$99"
   - Cart count: "Cart, 3 items" not just "3"

Create utility:
- components/ui/VisuallyHidden.tsx (for screen-reader-only text)

```

Accessibility Testing Checklist:

- [ ]  Navigate entire site using only keyboard
- [ ]  Test with screen reader (VoiceOver or NVDA)
- [ ]  Check color contrast with browser dev tools
- [ ]  Verify zoom to 200% doesn't break layout
- [ ]  Test with reduced motion preference

---

## Phase 9: Quality Assurance & Testing

### Step 9.1: Cross-Browser Testing

Test on:

- [ ]  Chrome (latest)
- [ ]  Firefox (latest)
- [ ]  Safari (latest)
- [ ]  Edge (latest)
- [ ]  Safari iOS (mobile)
- [ ]  Chrome Android (mobile)

### Step 9.2: Functional Testing Checklist

Homepage:

- [ ]  All sections render correctly
- [ ]  Products load from Shopify
- [ ]  All links navigate correctly
- [ ]  CTAs function as expected

Product Listing:

- [ ]  Products display with correct data
- [ ]  Pagination/load more works
- [ ]  Filtering works (if implemented)
- [ ]  Sorting works (if implemented)

Product Detail:

- [ ]  Product data displays correctly
- [ ]  Variant selection updates price and availability
- [ ]  Image gallery functions properly
- [ ]  Add to cart works
- [ ]  Cart updates correctly

Cart & Checkout:

- [ ]  Cart displays correct items
- [ ]  Quantity updates work
- [ ]  Remove items works
- [ ]  Cart persists across page refreshes
- [ ]  Checkout redirects to Shopify correctly
- [ ]  Checkout URL includes correct cart items

### Step 9.3: Performance Testing

Target Metrics (Core Web Vitals):

| Metric | Target | Tool |
| --- | --- | --- |
| LCP (Largest Contentful Paint) | < 2.5s | Lighthouse |
| FID (First Input Delay) | < 100ms | Lighthouse |
| CLS (Cumulative Layout Shift) | < 0.1 | Lighthouse |
| Performance Score | > 90 | Lighthouse |

Testing Prompt:

```
Analyze the site for performance issues and implement fixes:

1. Run Lighthouse audit and address any scores below 90
2. Identify and fix any layout shift issues (CLS)
3. Optimize largest contentful paint (LCP) element
4. Ensure all JavaScript is deferred or async where appropriate
5. Implement resource hints (preconnect, prefetch) for critical resources

Report findings and implement fixes.

```

---

## Phase 10: Launch Preparation

### Step 10.1: Pre-Launch Checklist

Content:

- [ ]  All placeholder text replaced
- [ ]  All images are final (no stock placeholders)
- [ ]  Legal pages complete (Privacy, Terms, Returns)
- [ ]  Contact information accurate
- [ ]  Social links work

Technical:

- [ ]  Shopify products created and published
- [ ]  Shopify checkout customized (colors, logo)
- [ ]  404 page designed
- [ ]  Favicon and app icons added
- [ ]  Meta tags and Open Graph images set
- [ ]  Analytics configured (Google Analytics, Shopify analytics)

SEO:

- [ ]  Page titles unique and descriptive
- [ ]  Meta descriptions written
- [ ]  Image alt text complete
- [ ]  Sitemap generated
- [ ]  Robots.txt configured

### Step 10.2: Shopify Store Activation

When ready to sell:

1. Claim your Shopify store through Lovable dashboard
2. Add products in Shopify admin (or import via CSV)
3. Configure payments (Shopify Payments, PayPal, etc.)
4. Set shipping rates and zones
5. Configure taxes for your regions
6. Test checkout with Shopify's test mode
7. Activate your Shopify plan (after 30-day trial or when ready)

### Step 10.3: Deploy & Domain Setup

```
Prepare the site for deployment:

1. Run production build and verify no errors
2. Test production build locally
3. Configure environment variables for production
4. Set up custom domain in Lovable
5. Configure SSL certificate
6. Set up domain redirects (www to non-www or vice versa)
7. Verify all Shopify API connections work in production

Checklist:
- [ ] Environment variables set for production
- [ ] No console errors in production build
- [ ] All API endpoints working
- [ ] Images loading correctly
- [ ] Checkout flow complete

```

---

## Common Pitfalls & How to Avoid Them

### ❌ Pitfall 1: Vague Prompts

Bad: "Make the homepage look better"
Good: "Increase the hero section heading size to text-5xl on desktop, add more vertical padding (py-24), and make the CTA button larger (px-8 py-4)"

### ❌ Pitfall 2: Building Too Much at Once

Bad: "Build the entire homepage with all 10 sections"
Good: "Build the hero section with these specific requirements..." (then move to next section)

### ❌ Pitfall 3: Skipping the Knowledge Base

Bad: Starting prompts without project context
Good: Configuring comprehensive knowledge base first, then referencing it implicitly in every prompt

### ❌ Pitfall 4: Ignoring Mobile Until the End

Bad: Building desktop-first, then "make it responsive"
Good: Testing mobile after each section, fixing immediately

### ❌ Pitfall 5: Not Testing Shopify Integration Early

Bad: Building entire UI before connecting Shopify
Good: Connecting Shopify after hero section, verifying products display, then continuing build

### ❌ Pitfall 6: Using Mock Data in Production

Bad: Hardcoding product data instead of fetching from Shopify
Good: All product data fetched dynamically from Storefront API

### ❌ Pitfall 7: Neglecting Loading States

Bad: Components that just show nothing while loading
Good: Skeleton states, spinners, and graceful error handling throughout

---

## Pro Tips for Luxury-Level Design

### Typography Excellence

- Limit font families to 2 (one for headings, one for body)
- Use generous line-height (1.5-1.75 for body text)
- Implement proper hierarchy with consistent size scales
- Add letter-spacing to uppercase text (-0.02em) and headings

### Whitespace Mastery

- Don't fear empty space — it communicates luxury
- Consistent vertical rhythm — use multiples of 8px
- Generous padding on sections (min 80px vertical on desktop)
- Card padding should be substantial (24-32px)

### Color Sophistication

- Restrained palette — 2-3 colors maximum
- Use neutrals extensively — whites, off-whites, grays
- Accent sparingly — accent color for CTAs and highlights only
- Avoid pure black (#000) — use rich black (#1A1A1A) or charcoal

### Micro-Interactions

- Subtle hover states — opacity change, slight scale, soft shadows
- Smooth transitions — 150-300ms duration
- Button feedback — slight movement or color change on press
- Loading states — elegant spinners, skeleton shimmer

### Photography Standards

- Consistent style — same lighting, background, composition
- High resolution — minimum 2x for retina displays
- Optimized file size — compress without visible quality loss
- Consistent aspect ratios — squares or 4:5 for product grids

---

## Summary: Your Build Roadmap

```
{
  "tooltip": {
    "trigger": "item",
    "formatter": "{b}: {c} hours"
  },
  "legend": {
    "orient": "vertical",
    "left": "left",
    "top": "center"
  },
  "series": [
    {
      "name": "Build Time",
      "type": "pie",
      "radius": ["40%", "70%"],
      "avoidLabelOverlap": true,
      "itemStyle": {
        "borderRadius": 10,
        "borderColor": "#fff",
        "borderWidth": 2
      },
      "label": {
        "show": true,
        "formatter": "{b}: {c}h"
      },
      "data": [
        { "value": 1, "name": "Planning & Setup", "itemStyle": { "color": "#6366f1" } },
        { "value": 1, "name": "Design System", "itemStyle": { "color": "#8b5cf6" } },
        { "value": 3, "name": "Homepage Sections", "itemStyle": { "color": "#a855f7" } },
        { "value": 2, "name": "Product Pages", "itemStyle": { "color": "#d946ef" } },
        { "value": 1, "name": "Cart & Checkout", "itemStyle": { "color": "#ec4899" } },
        { "value": 1, "name": "Responsive Polish", "itemStyle": { "color": "#f43f5e" } },
        { "value": 1, "name": "Testing & Launch", "itemStyle": { "color": "#f97316" } }
      ]
    }
  ]
}

```

Total Estimated Time: 8-12 hours for a complete, production-ready e-commerce store

---

## Final Deliverables Checklist

After following this guide, you will have:

- ✅ Professional homepage with 8+ conversion-optimized sections
- ✅ Real Shopify integration with live product data
- ✅ Working cart and checkout via Storefront API
- ✅ Product detail pages with variants and image galleries
- ✅ Fully responsive design optimized for all devices
- ✅ Accessible interface meeting WCAG 2.1 AA standards
- ✅ Performance-optimized code (90+ Lighthouse score)
- ✅ Reusable component library for future updates
- ✅ TypeScript-powered codebase with proper typing
- ✅ Production-ready architecture that scales

---

You're now equipped to build world-class e-commerce experiences.

Happy building! 🚀