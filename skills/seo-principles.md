# SEO Principles Skill

This skill ensures that web applications, content, and digital experiences are built to be discoverable, crawlable, indexable, and authoritative. It bridges the gap between clean code, user experience, and search engine visibility while maintaining modern web standards.

---

## 1. Technical SEO & Crawlability

Ensuring search engines can efficiently discover, crawl, render, and index your site structure.

### 1.1 URL Architecture & Structure

**Best Practices:**
* **Descriptive, Semantic URLs:** Use kebab-case with meaningful keywords
  * ✅ Good: `/services/web-design-london`, `/blog/seo-guide-2026`
  * ❌ Bad: `/s?id=123`, `/page.php?cat=5&item=99`
* **Flat Hierarchy:** Keep content within 3 clicks from homepage
  * Optimal: `domain.com/category/subcategory/page`
  * Maximum depth: 4 levels for most sites
* **URL Parameters:** Minimize or eliminate query strings where possible
  * Use clean paths for filtering: `/products/shoes/running` vs `/products?type=shoes&cat=running`
* **Trailing Slashes:** Be consistent (with or without) across the entire site
* **HTTPS Everywhere:** SSL/TLS is a confirmed ranking signal; no mixed content
* **Lowercase Convention:** URLs are case-sensitive; standardize on lowercase
* **Hyphens Over Underscores:** Google treats hyphens as word separators

**Implementation:**
```html
<!-- Bad URL Structure -->
<a href="/ProductDetail.aspx?ProductID=12345&Category=Electronics">

<!-- Good URL Structure -->
<a href="/electronics/wireless-headphones-noise-cancelling">
```

### 1.2 Robots.txt & Crawler Directives

**Purpose:** Control crawler access and crawl budget optimization.

**Essential Directives:**
```
User-agent: *
Disallow: /admin/
Disallow: /private/
Disallow: /api/
Disallow: /*?*sort=  # Block parameter-based duplicates
Allow: /api/public/

# Sitemap location
Sitemap: https://example.com/sitemap.xml
Sitemap: https://example.com/sitemap-images.xml

# Crawl delay (use sparingly)
Crawl-delay: 1
```

**Strategic Blocking:**
* Development/staging environments
* Thank-you pages (after conversions)
* Duplicate content variations (print versions, filtered results)
* Infinite scroll/pagination traps
* Admin panels and login pages
* Search result pages on your site

### 1.3 XML Sitemaps

**Types of Sitemaps:**
* **Primary Sitemap:** Main content pages
* **Image Sitemap:** Enhanced image discovery
* **Video Sitemap:** Video content with metadata
* **News Sitemap:** For news publishers (last 2 days)

**Optimal Structure:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:image="http://www.google.com/schemas/sitemap-image/1.1">
  <url>
    <loc>https://example.com/page</loc>
    <lastmod>2026-01-15</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
    <image:image>
      <image:loc>https://example.com/image.jpg</image:loc>
      <image:title>Descriptive Image Title</image:title>
      <image:caption>Image caption for context</image:caption>
    </image:image>
  </url>
</urlset>
```

**Best Practices:**
* Maximum 50,000 URLs per sitemap (50MB uncompressed)
* Use sitemap index files for larger sites
* Update `lastmod` only when content genuinely changes
* Prioritize pages realistically (0.0 to 1.0 scale)
* Submit to Google Search Console and Bing Webmaster Tools
* Include only canonical URLs (exclude duplicates)

### 1.4 Canonicalization Strategy

**Purpose:** Consolidate duplicate or similar content signals to a preferred URL.

**Implementation Methods:**

```html
<!-- 1. Canonical Link Element (Most Common) -->
<link rel="canonical" href="https://example.com/preferred-version" />

<!-- 2. HTTP Header Method (for PDFs, non-HTML) -->
Link: <https://example.com/preferred-version>; rel="canonical"

<!-- 3. Sitemap Specification -->
<!-- Only include canonical URLs in sitemap.xml -->
```

**Common Canonicalization Scenarios:**
* **Pagination:** Point all pages to View All or first page with `rel="canonical"`
* **Protocol Variants:** HTTPS canonical for HTTP versions
* **WWW vs Non-WWW:** Choose one and redirect the other
* **Sorting/Filtering:** `/products?sort=price` → canonical to `/products`
* **Tracking Parameters:** `/page?utm_source=email` → canonical to `/page`
* **AMP Pages:** AMP version points to canonical desktop/mobile version
* **Syndicated Content:** Point to original source if republishing

**Self-Referencing Canonical:**
```html
<!-- Always include, even if no duplicates exist -->
<link rel="canonical" href="https://example.com/current-page" />
```

### 1.5 HTTP Status Codes & Redirects

**Critical Status Codes:**

| Code | Name | SEO Impact | When to Use |
|------|------|------------|-------------|
| **200** | OK | Positive | Normal page serving |
| **301** | Permanent Redirect | Transfers ~90-99% link equity | URL changes, site migrations |
| **302** | Temporary Redirect | No link equity transfer | A/B testing, temporary moves |
| **307** | Temporary Redirect | Like 302 but preserves method | Same as 302, more modern |
| **404** | Not Found | Neutral if intentional | Deleted content, no replacement |
| **410** | Gone | Signals permanent removal | Discontinued products/content |
| **451** | Unavailable (Legal) | Neutral | Legal takedowns |
| **500** | Server Error | Negative if persistent | Server issues (fix immediately) |
| **503** | Service Unavailable | Temporary pass if short | Maintenance mode |

**Redirect Best Practices:**
* **Redirect Chains:** Avoid A→B→C; go directly A→C (max 2 hops)
* **Redirect Loops:** Prevent circular redirects (critical error)
* **Page Speed:** Each redirect adds ~200-500ms latency
* **Mobile Redirects:** Avoid separate mobile URLs if possible; use responsive design
* **JavaScript Redirects:** Avoid; use server-side 301s instead

**Soft 404s (False 200s):**
Avoid returning `200 OK` for pages that should be `404`. Search engines penalize this.

```html
❌ Bad: <h1>Page Not Found</h1> with 200 status
✅ Good: 404 status with helpful navigation and search
```

### 1.6 Pagination & Infinite Scroll

**Pagination Strategies:**

```html
<!-- Method 1: rel="next" and rel="prev" (Deprecated by Google but still useful) -->
<link rel="prev" href="https://example.com/page1" />
<link rel="next" href="https://example.com/page3" />

<!-- Method 2: Canonical to View All (if feasible) -->
<link rel="canonical" href="https://example.com/all-items" />

<!-- Method 3: Self-Referencing Canonical (Most Common Now) -->
<link rel="canonical" href="https://example.com/page2" />
```

**Infinite Scroll SEO:**
* Implement "Load More" pagination fallback
* Use History API to create unique URLs for each state
* Ensure crawlers can access paginated versions
* Include pagination in sitemap

### 1.7 International SEO & Hreflang

**Hreflang Implementation:**

```html
<!-- Indicate language/region variants -->
<link rel="alternate" hreflang="en-us" href="https://example.com/en-us/" />
<link rel="alternate" hreflang="en-gb" href="https://example.com/en-gb/" />
<link rel="alternate" hreflang="es-es" href="https://example.com/es/" />
<link rel="alternate" hreflang="x-default" href="https://example.com/" />
```

**URL Structure Options:**
* **ccTLDs:** `example.co.uk`, `example.de` (strongest geo-signal)
* **Subdirectories:** `example.com/uk/`, `example.com/de/` (easiest to manage)
* **Subdomains:** `uk.example.com`, `de.example.com` (separate properties)

**Requirements:**
* Bidirectional linking (all pages must reference each other)
* Include `x-default` for global/language selector pages
* Use correct language-region codes (ISO 639-1 + ISO 3166-1)

---

## 2. On-Page Semantic Optimization

Using HTML5 semantic elements and structured markup to provide context and hierarchy.

### 2.1 Heading Hierarchy (H1-H6)

**The Golden Rules:**
* **One H1 per page** containing the primary target keyword
* **Logical descending order:** Never skip levels (H1→H3 without H2)
* **Keyword distribution:** Natural placement of semantic variations
* **Accessibility alignment:** Screen readers use headings for navigation

**Example Structure:**
```html
<h1>Complete Guide to Technical SEO in 2026</h1>

  <h2>What is Technical SEO?</h2>
    <h3>Core Components</h3>
    <h3>Why It Matters</h3>
  
  <h2>Technical SEO Checklist</h2>
    <h3>Crawlability Optimization</h3>
      <h4>Robots.txt Configuration</h4>
      <h4>XML Sitemap Best Practices</h4>
    <h3>Site Speed Optimization</h3>
      <h4>Core Web Vitals</h4>
      <h4>Resource Optimization</h4>
```

**Common Mistakes:**
* Multiple H1s (confuses topic hierarchy)
* Using headings for styling (use CSS instead)
* Skipping levels for visual design
* Empty headings or generic text ("Introduction")

### 2.2 Title Tags (The Most Critical Element)

**Specifications:**
* **Length:** 50-60 characters (512-600px width)
* **Structure:** `Primary Keyword - Secondary Keyword | Brand Name`
* **Uniqueness:** Every page must have a unique title
* **Keyword Placement:** Front-load important keywords
* **Emotional Triggers:** Numbers, power words, year

**Title Tag Formulas:**

```html
<!-- Product Pages -->
<title>Product Name - Key Benefit | Brand Name</title>
<title>iPhone 15 Pro - 5x Optical Zoom Camera | Apple</title>

<!-- Blog Posts -->
<title>How to [Achieve Goal]: [Number] Tips for [Year]</title>
<title>How to Rank #1 on Google: 15 SEO Tips for 2026</title>

<!-- Category Pages -->
<title>Category Name - Subcategory | Brand</title>
<title>Running Shoes - Trail Running | Nike</title>

<!-- Local Pages -->
<title>Service + Location | Business Name</title>
<title>Emergency Plumber in Brooklyn 24/7 | Joe's Plumbing</title>

<!-- Homepage -->
<title>Brand Name - What You Do | Unique Value Proposition</title>
<title>Airbnb - Vacation Rentals & Experiences | Book Unique Stays</title>
```

**Dynamic Title Tag Optimization:**
```javascript
// React/Next.js Example
<Head>
  <title>{`${product.name} - ${product.category} | ${siteName}`}</title>
</Head>
```

### 2.3 Meta Descriptions (The Pitch)

**Specifications:**
* **Length:** 150-160 characters for desktop, ~120 for mobile
* **Purpose:** Improve click-through rate (CTR), not a ranking factor
* **Include:** Primary keyword, benefit, call-to-action (CTA)
* **Uniqueness:** Different for every page

**Meta Description Formulas:**

```html
<!-- Information/How-To -->
<meta name="description" content="Learn [how to achieve X] with our [comprehensive/step-by-step] guide. Discover [benefit 1], [benefit 2], and [bonus benefit]. [CTA]">

<!-- Product -->
<meta name="description" content="[Product Name] offers [key benefit]. Features include [feature 1], [feature 2], and [feature 3]. [Price/Offer]. [CTA like 'Shop now' or 'Free shipping']">

<!-- Local Service -->
<meta name="description" content="[Service] in [Location]. [Years] of experience. [Benefit/USP]. [Availability]. Call [phone] or book online. [Social proof like 'Rated 4.9/5']">
```

**Power Words for Higher CTR:**
* Time-sensitive: Today, Now, 2026, Limited
* Value: Free, Discount, Save, Exclusive
* Credibility: Proven, Certified, Expert, Official
* Emotional: Discover, Transform, Master, Ultimate

**Example:**
```html
<meta name="description" content="Master technical SEO in 2026 with our complete guide. Learn crawlability, Core Web Vitals, and schema markup. Trusted by 50K+ marketers. Start optimizing today.">
```

### 2.4 Open Graph & Social Meta Tags

**Purpose:** Control how content appears when shared on social platforms.

```html
<!-- Open Graph (Facebook, LinkedIn, Pinterest) -->
<meta property="og:title" content="Your Compelling Title for Social">
<meta property="og:description" content="Engaging description for social shares">
<meta property="og:image" content="https://example.com/share-image.jpg">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:url" content="https://example.com/page">
<meta property="og:type" content="article">
<meta property="og:site_name" content="Your Brand Name">
<meta property="og:locale" content="en_US">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@yourbrand">
<meta name="twitter:creator" content="@authorhandle">
<meta name="twitter:title" content="Twitter-Specific Title">
<meta name="twitter:description" content="Twitter-specific description">
<meta name="twitter:image" content="https://example.com/twitter-image.jpg">

<!-- Article-Specific -->
<meta property="article:published_time" content="2026-01-15T08:00:00+00:00">
<meta property="article:modified_time" content="2026-01-20T14:30:00+00:00">
<meta property="article:author" content="https://example.com/author/john-smith">
<meta property="article:section" content="Technology">
<meta property="article:tag" content="SEO">
<meta property="article:tag" content="Technical SEO">
```

**Image Specifications:**
* **Facebook/OG:** 1200×630px (1.91:1 ratio)
* **Twitter Summary Large:** 1200×600px (2:1 ratio)
* **LinkedIn:** 1200×627px
* **Pinterest:** 1000×1500px (2:3 ratio)
* **Format:** JPG or PNG, <1MB, high quality

### 2.5 Image SEO

**Critical Elements:**

```html
<img 
  src="/images/red-running-shoes-nike-2026.webp"
  alt="Red Nike running shoes with white swoosh logo on wooden floor"
  title="Nike Air Zoom Pegasus 40 - Running Shoes"
  width="800"
  height="600"
  loading="lazy"
  decoding="async"
/>
```

**Alt Text Best Practices:**
* **Descriptive and specific:** Describe what's in the image
* **Include keywords naturally:** Don't stuff, but include relevant terms
* **Context matters:** Describe in relation to surrounding content
* **Length:** 125 characters or fewer
* **Decorative images:** Use empty alt (`alt=""`) for purely decorative images
* **Functional images:** Describe the function, not the image

**Alt Text Examples:**
```html
❌ Bad: <img alt="image1.jpg">
❌ Bad: <img alt="product">
❌ Bad: <img alt="buy red shoes cheap online best price">
✅ Good: <img alt="Red leather running shoes with mesh upper">
✅ Good: <img alt="Graph showing 40% increase in organic traffic">
```

**File Naming:**
* Use descriptive, hyphen-separated names
* Include relevant keywords
* ✅ `blue-wireless-headphones-2026.webp`
* ❌ `IMG_8472.jpg`, `image1.png`

**Image Optimization Checklist:**
* **Format:** WebP > AVIF > JPEG > PNG
* **Compression:** Use tools like ImageOptim, Squoosh, or TinyPNG
* **Responsive Images:** Use `srcset` for different screen sizes
* **Lazy Loading:** `loading="lazy"` for below-fold images
* **CDN Delivery:** Use image CDNs (Cloudflare, Imgix, Cloudinary)
* **Dimensions:** Always specify width/height to prevent CLS

**Responsive Images:**
```html
<img 
  srcset="image-400.webp 400w,
          image-800.webp 800w,
          image-1200.webp 1200w"
  sizes="(max-width: 600px) 400px,
         (max-width: 1000px) 800px,
         1200px"
  src="image-800.webp"
  alt="Descriptive alt text"
  width="1200"
  height="800"
  loading="lazy"
/>
```

### 2.6 Semantic HTML5 Elements

**Purpose:** Provide machine-readable structure and meaning.

```html
<!-- Proper Semantic Structure -->
<body>
  <header>
    <nav aria-label="Primary navigation">
      <!-- Main site navigation -->
    </nav>
  </header>

  <main>
    <article>
      <header>
        <h1>Article Title</h1>
        <p>
          <time datetime="2026-01-15">January 15, 2026</time>
          by <span itemprop="author">John Doe</span>
        </p>
      </header>

      <section>
        <h2>Section Heading</h2>
        <p>Content...</p>
      </section>

      <aside>
        <!-- Related content, definitions, notes -->
      </aside>

      <footer>
        <!-- Article metadata, share buttons -->
      </footer>
    </article>
  </main>

  <aside>
    <!-- Sidebar, related articles -->
  </aside>

  <footer>
    <!-- Site footer, copyright, links -->
  </footer>
</body>
```

**Key Semantic Elements:**
* `<article>`: Self-contained, independently distributable content
* `<section>`: Thematic grouping of content with heading
* `<nav>`: Navigation links
* `<aside>`: Tangentially related content
* `<header>` / `<footer>`: Introductory/concluding content for section
* `<main>`: Dominant content (one per page)
* `<figure>` / `<figcaption>`: Images, diagrams, code with captions

---

## 3. Structured Data & Rich Results

Help search engines understand content context and earn enhanced SERP features.

### 3.1 JSON-LD Format (Preferred)

**Why JSON-LD:**
* Separated from HTML markup (easier to manage)
* Doesn't affect page rendering
* Recommended by Google
* Can be dynamically generated

**Basic Implementation:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "SchemaType",
  "property": "value"
}
</script>
```

### 3.2 Essential Schema Types

#### Organization Schema
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Your Company Name",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "description": "Company description",
  "sameAs": [
    "https://www.facebook.com/yourcompany",
    "https://www.twitter.com/yourcompany",
    "https://www.linkedin.com/company/yourcompany",
    "https://www.instagram.com/yourcompany"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "+1-555-123-4567",
    "contactType": "Customer Service",
    "areaServed": "US",
    "availableLanguage": ["English", "Spanish"]
  },
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main Street",
    "addressLocality": "New York",
    "addressRegion": "NY",
    "postalCode": "10001",
    "addressCountry": "US"
  }
}
```

#### LocalBusiness Schema
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Joe's Pizza",
  "image": "https://example.com/restaurant.jpg",
  "@id": "https://example.com",
  "url": "https://example.com",
  "telephone": "+1-555-987-6543",
  "priceRange": "$$",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "456 Broadway",
    "addressLocality": "Brooklyn",
    "addressRegion": "NY",
    "postalCode": "11211",
    "addressCountry": "US"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 40.7128,
    "longitude": -74.0060
  },
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "11:00",
      "closes": "22:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Saturday", "Sunday"],
      "opens": "12:00",
      "closes": "23:00"
    }
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.5",
    "reviewCount": "328"
  }
}
```

#### Product Schema
```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Wireless Noise-Cancelling Headphones",
  "image": [
    "https://example.com/product-image1.jpg",
    "https://example.com/product-image2.jpg"
  ],
  "description": "Premium wireless headphones with active noise cancellation",
  "sku": "WH-1000XM5",
  "mpn": "925872",
  "brand": {
    "@type": "Brand",
    "name": "Sony"
  },
  "offers": {
    "@type": "Offer",
    "url": "https://example.com/product/headphones",
    "priceCurrency": "USD",
    "price": "399.99",
    "priceValidUntil": "2026-12-31",
    "availability": "https://schema.org/InStock",
    "itemCondition": "https://schema.org/NewCondition",
    "seller": {
      "@type": "Organization",
      "name": "Example Electronics"
    }
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "1247",
    "bestRating": "5",
    "worstRating": "1"
  },
  "review": [
    {
      "@type": "Review",
      "reviewRating": {
        "@type": "Rating",
        "ratingValue": "5",
        "bestRating": "5"
      },
      "author": {
        "@type": "Person",
        "name": "Sarah Johnson"
      },
      "reviewBody": "Best headphones I've ever owned. Noise cancellation is incredible.",
      "datePublished": "2026-01-10"
    }
  ]
}
```

#### Article Schema
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Complete Guide to Technical SEO in 2026",
  "image": "https://example.com/article-image.jpg",
  "author": {
    "@type": "Person",
    "name": "Jane Smith",
    "url": "https://example.com/author/jane-smith"
  },
  "publisher": {
    "@type": "Organization",
    "name": "SEO Experts",
    "logo": {
      "@type": "ImageObject",
      "url": "https://example.com/logo.png",
      "width": 600,
      "height": 60
    }
  },
  "datePublished": "2026-01-15T08:00:00+00:00",
  "dateModified": "2026-01-20T14:30:00+00:00",
  "description": "Learn everything about technical SEO including crawlability, site speed, and schema markup.",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://example.com/blog/technical-seo-guide"
  }
}
```

#### FAQ Schema
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is technical SEO?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Technical SEO refers to optimizing your website's technical infrastructure to help search engines crawl, index, and rank your pages more effectively."
      }
    },
    {
      "@type": "Question",
      "name": "How long does SEO take to work?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "SEO typically takes 3-6 months to show significant results, though competitive industries may require 6-12 months of consistent optimization."
      }
    }
  ]
}
```

#### Breadcrumb Schema
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://example.com"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Electronics",
      "item": "https://example.com/electronics"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "Headphones",
      "item": "https://example.com/electronics/headphones"
    }
  ]
}
```

#### Video Schema
```json
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "How to Optimize Your Website for SEO",
  "description": "Step-by-step tutorial on optimizing your website for search engines",
  "thumbnailUrl": "https://example.com/video-thumbnail.jpg",
  "uploadDate": "2026-01-15T08:00:00+00:00",
  "duration": "PT10M30S",
  "contentUrl": "https://example.com/video.mp4",
  "embedUrl": "https://example.com/embed/video",
  "interactionStatistic": {
    "@type": "InteractionCounter",
    "interactionType": { "@type": "WatchAction" },
    "userInteractionCount": 5647
  }
}
```

### 3.3 Rich Results Testing

**Validation Tools:**
* Google Rich Results Test: https://search.google.com/test/rich-results
* Schema Markup Validator: https://validator.schema.org/
* Google Search Console Rich Results Report

**Common Errors to Avoid:**
* Missing required properties
* Invalid date formats (use ISO 8601: `2026-01-15T08:00:00+00:00`)
* Mismatched schema types
* Hidden or invisible content in schema
* Price/availability mismatches with actual page content

---

## 4. Performance & Core Web Vitals (CWV)

Google's page experience signals directly impact rankings.

### 4.1 Core Web Vitals Metrics

#### Largest Contentful Paint (LCP)
**What it measures:** Loading performance - time until largest content element renders

**Target:** <2.5 seconds (Good), 2.5-4.0s (Needs Improvement), >4.0s (Poor)

**Optimization Strategies:**
* **Optimize images:** Use WebP/AVIF, compress, lazy load below-fold
* **Preload critical resources:**
  ```html
  <link rel="preload" as="image" href="/hero-image.webp">
  <link rel="preload" as="font" href="/font.woff2" crossorigin>
  ```
* **Eliminate render-blocking resources:**
  ```html
  <!-- Defer non-critical CSS -->
  <link rel="stylesheet" href="non-critical.css" media="print" onload="this.media='all'">
  
  <!-- Defer JavaScript -->
  <script src="script.js" defer></script>
  ```
* **Use a CDN** for faster content delivery
* **Optimize server response time:** <200ms TTFB (Time to First Byte)
* **Implement text compression** (Gzip, Brotli)

#### First Input Delay (FID) / Interaction to Next Paint (INP)
**What it measures:** Interactivity - responsiveness to user input

**FID Target:** <100ms (Good), 100-300ms (Needs Improvement), >300ms (Poor)
**INP Target:** <200ms (Good), 200-500ms (Needs Improvement), >500ms (Poor)

**Optimization Strategies:**
* **Minimize JavaScript execution:**
  * Code splitting and lazy loading
  * Remove unused JavaScript
  * Defer third-party scripts
* **Break up long tasks** (>50ms)
* **Use web workers** for heavy computations
* **Reduce JavaScript bundle size:**
  * Tree shaking
  * Dynamic imports
  * Remove polyfills for modern browsers
* **Optimize event handlers**

#### Cumulative Layout Shift (CLS)
**What it measures:** Visual stability - unexpected layout shifts

**Target:** <0.1 (Good), 0.1-0.25 (Needs Improvement), >0.25 (Poor)

**Optimization Strategies:**
* **Set dimensions for images and videos:**
  ```html
  <img src="image.jpg" width="800" height="600" alt="...">
  ```
* **Reserve space for ads:**
  ```css
  .ad-slot {
    min-height: 250px;
  }
  ```
* **Avoid inserting content above existing content**
* **Use `aspect-ratio` CSS:**
  ```css
  .video-container {
    aspect-ratio: 16 / 9;
  }
  ```
* **Preload fonts to prevent FOIT/FOUT:**
  ```html
  <link rel="preload" as="font" href="/font.woff2" crossorigin>
  ```
  ```css
  @font-face {
    font-family: 'CustomFont';
    src: url('/font.woff2') format('woff2');
    font-display: swap; /* or optional */
  }
  ```

### 4.2 Additional Performance Optimizations

#### Critical Rendering Path
```html
<!-- 1. Inline critical CSS -->
<style>
  /* Above-the-fold styles */
  body { margin: 0; font-family: sans-serif; }
  .hero { height: 100vh; background: #000; }
</style>

<!-- 2. Preconnect to required origins -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://cdn.example.com">

<!-- 3. Defer non-critical CSS -->
<link rel="preload" as="style" href="/styles.css" onload="this.rel='stylesheet'">
```

#### Resource Hints
```html
<!-- DNS Prefetch: Resolve DNS early -->
<link rel="dns-prefetch" href="https://analytics.google.com">

<!-- Preconnect: Establish connection early -->
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Prefetch: Load resources for next navigation -->
<link rel="prefetch" href="/next-page.html">

<!-- Prerender: Render entire page in background -->
<link rel="prerender" href="/likely-next-page.html">
```

#### JavaScript Optimization
```html
<!-- Defer: Download in parallel, execute after parsing -->
<script src="script.js" defer></script>

<!-- Async: Download and execute asap, don't block parsing -->
<script src="analytics.js" async></script>

<!-- Module: Modern browsers, deferred by default -->
<script type="module" src="app.js"></script>
```

#### Image Optimization Techniques
```html
<!-- 1. Modern formats with fallbacks -->
<picture>
  <source srcset="image.avif" type="image/avif">
  <source srcset="image.webp" type="image/webp">
  <img src="image.jpg" alt="Description">
</picture>

<!-- 2. Responsive images -->
<img srcset="small.jpg 400w, medium.jpg 800w, large.jpg 1200w"
     sizes="(max-width: 600px) 400px, (max-width: 1000px) 800px, 1200px"
     src="medium.jpg" alt="Description">

<!-- 3. Lazy loading -->
<img src="image.jpg" loading="lazy" alt="Description">

<!-- 4. Blur-up technique -->
<img src="tiny-placeholder.jpg" 
     data-src="full-image.jpg" 
     class="lazy-load blur" 
     alt="Description">
```

#### Caching Strategy
```
# .htaccess for Apache
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/webp "access plus 1 year"
  ExpiresByType text/css "access plus 1 month"
  ExpiresByType application/javascript "access plus 1 month"
  ExpiresByType application/font-woff2 "access plus 1 year"
</IfModule>

<IfModule mod_headers.c>
  <FilesMatch "\.(jpg|jpeg|png|gif|webp|svg)$">
    Header set Cache-Control "max-age=31536000, public"
  </FilesMatch>
</IfModule>
```

### 4.3 Mobile Optimization

**Mobile-First Indexing:**
* Google predominantly uses mobile version for indexing
* Ensure mobile and desktop content parity
* Test with mobile-friendly test tool

**Responsive Design Best Practices:**
```css
/* Fluid typography */
html {
  font-size: clamp(16px, 2vw, 20px);
}

/* Responsive containers */
.container {
  width: min(90%, 1200px);
  margin-inline: auto;
}

/* Media queries */
@media (max-width: 768px) {
  .nav { flex-direction: column; }
}
```

**Viewport Configuration:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

**Touch Targets:**
* Minimum 48×48 CSS pixels
* Adequate spacing between interactive elements

---

## 5. Content Strategy & E-E-A-T

Experience, Expertise, Authoritativeness, and Trustworthiness.

### 5.1 Understanding Search Intent

**Four Primary Intent Types:**

| Intent Type | User Goal | Keywords | Content Type |
|-------------|-----------|----------|--------------|
| **Informational** | Learn/understand | how to, what is, guide, tutorial | Blog posts, guides, definitions |
| **Navigational** | Find specific site | brand name, login, site name | Homepage, login pages |
| **Commercial** | Research before buying | best, top, review, vs, comparison | Reviews, comparisons, listicles |
| **Transactional** | Complete action | buy, order, download, subscribe | Product pages, checkout, signup |

**Intent Optimization:**
```
Informational: "how to fix a leaky faucet"
→ Step-by-step guide with images/video

Commercial: "best espresso machines under $500"
→ Comparison article with pros/cons, buying guide

Transactional: "buy dyson v15 vacuum"
→ Product page with price, reviews, add-to-cart
```

### 5.2 E-E-A-T Framework

#### Experience
* **First-hand experience** with product/service/topic
* User-generated content (reviews, testimonials)
* Case studies with real results
* Before/after examples
* Personal anecdotes and insights

**Implementation:**
```html
<p>I've been using this camera for 18 months, shooting over 50,000 photos across various conditions...</p>

<!-- Author bio with credentials -->
<div class="author-bio">
  <p>John Smith is a professional photographer with 15 years of experience, specializing in wildlife photography.</p>
</div>
```

#### Expertise
* Author credentials and qualifications
* Industry certifications
* Years of experience
* Published works and citations
* Educational background

**Author Markup:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Dr. Sarah Johnson",
  "jobTitle": "Board-Certified Dermatologist",
  "affiliation": {
    "@type": "Organization",
    "name": "American Academy of Dermatology"
  },
  "alumniOf": {
    "@type": "Organization",
    "name": "Harvard Medical School"
  }
}
</script>
```

#### Authoritativeness
* Backlinks from authoritative sites
* Brand mentions and citations
* Industry recognition and awards
* Speaking engagements
* Original research and data

**Building Authority:**
* Create original research/surveys
* Get cited by authoritative sources
* Build brand presence across platforms
* Earn industry awards/recognition
* Publish in reputable publications

#### Trustworthiness
* **Security:** HTTPS, secure payment processing
* **Transparency:** Clear about-us, contact info, privacy policy
* **Accuracy:** Fact-checked, cited sources, regular updates
* **User Reviews:** Authentic testimonials and ratings
* **Professional Design:** Modern, functional, error-free

**Trust Signals:**
```html
<!-- Contact Information -->
<address>
  <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
  <p>Phone: +1-555-123-4567</p>
  <p>Address: 123 Main St, New York, NY 10001</p>
</address>

<!-- Trust Badges -->
<img src="bbb-accredited.png" alt="BBB A+ Rating">
<img src="ssl-secure.png" alt="SSL Secured">

<!-- Last Updated -->
<p>Last updated: <time datetime="2026-01-20">January 20, 2026</time></p>
```

### 5.3 Keyword Research & Targeting

**Keyword Research Process:**
1. **Brainstorm seed keywords:** Core topics related to your business
2. **Use keyword tools:** Google Keyword Planner, Ahrefs, SEMrush, Moz
3. **Analyze search volume & difficulty:** Balance opportunity vs competition
4. **Identify long-tail variations:** 3-5+ word phrases, lower competition
5. **Group by intent:** Organize by user goal
6. **Map to content:** Assign keywords to existing/planned pages

**Keyword Metrics:**
* **Search Volume:** Monthly searches (target mix of high/medium/low)
* **Keyword Difficulty:** Competitiveness score
* **Cost Per Click (CPC):** Indicates commercial value
* **SERP Features:** Featured snippets, People Also Ask, etc.

**Primary vs. Secondary Keywords:**
```
Page: "Best Running Shoes for Beginners"

Primary Keyword: "best running shoes for beginners" (1-2 per page)
Secondary Keywords:
- "beginner running shoes"
- "running shoes for new runners"
- "comfortable running shoes"
- "affordable running shoes"

LSI Keywords (Latent Semantic Indexing):
- cushioning, support, durability
- pronation, arch support
- breathable, lightweight
```

### 5.4 Content Optimization

**Content Length:**
* No magic number, but comprehensive coverage wins
* Industry average: 1,500-2,500 words for blog posts
* Match or exceed top-ranking content depth
* Quality > quantity (avoid fluff)

**Keyword Density:**
* Natural usage (1-2% density as rough guide)
* Primary keyword in:
  * H1 heading
  * First 100 words
  * At least one H2 subheading
  * Conclusion
  * URL slug
  * Title tag
  * Meta description

**Content Freshness:**
* Update evergreen content regularly
* Add new information and examples
* Update statistics and dates
* Refresh screenshots and images
* Expand sections with new insights

**Readability:**
* Short paragraphs (2-4 sentences)
* Bullet points and numbered lists
* Subheadings every 300 words
* White space and visual breaks
* Simple language (8th-grade reading level for general audience)
* Active voice over passive

**Visual Content:**
* Custom images and graphics
* Infographics (highly shareable)
* Screenshots with annotations
* Charts and data visualizations
* Videos (increase time on page)

### 5.5 Internal Linking Strategy

**Purpose:**
* Distribute page authority (link equity)
* Help search engines discover content
* Improve crawl efficiency
* Enhance user navigation
* Establish content hierarchy

**Best Practices:**
* **Descriptive anchor text:** Use relevant keywords, avoid "click here"
* **Link to deep pages:** Don't just link to homepage
* **Contextual relevance:** Link to related, valuable content
* **Reasonable number:** 3-10 internal links per 1,000 words
* **Avoid over-optimization:** Vary anchor text naturally

**Examples:**
```html
❌ Bad: <a href="/services">Click here</a> for our services.
❌ Bad: <a href="/blog">Read more</a> about this topic.
✅ Good: Our <a href="/services/web-design">web design services</a> include responsive layouts.
✅ Good: Learn more about <a href="/blog/technical-seo-guide">technical SEO optimization</a>.
```

**Internal Linking Structure:**
```
Homepage
├── Service Pages (high priority)
│   ├── Individual service details
│   └── Related blog posts
├── Product Category Pages
│   ├── Product subcategories
│   └── Individual products
└── Blog Categories
    ├── Individual blog posts
    └── Related articles
```

### 5.6 Topic Clusters & Pillar Pages

**Concept:**
* **Pillar Page:** Comprehensive guide on broad topic (2,000-5,000+ words)
* **Cluster Content:** Detailed articles on specific subtopics
* **Internal Links:** Clusters link to pillar, pillar links to all clusters

**Example Structure:**
```
Pillar Page: "Complete Guide to SEO"
├── Cluster: "Technical SEO Checklist"
├── Cluster: "On-Page SEO Best Practices"
├── Cluster: "Link Building Strategies"
├── Cluster: "Local SEO Guide"
└── Cluster: "SEO Tools Comparison"
```

**Benefits:**
* Signals topical authority to search engines
* Better user experience
* Improved internal linking
* Higher rankings for competitive keywords
* More organic traffic

---

## 6. Link Building & Off-Page SEO

### 6.1 Backlink Quality Factors

**What Makes a Quality Backlink:**
* **Authority:** From high Domain Authority (DA) sites
* **Relevance:** From topically related sites
* **Placement:** Editorial links in content (vs. footer/sidebar)
* **Anchor Text:** Descriptive, relevant (not exact match spam)
* **DoFollow:** Passes link equity (nofollow doesn't)
* **Traffic:** From sites that generate actual visitors
* **Diversity:** From variety of domains

**Link Attributes:**
```html
<!-- DoFollow (default, passes equity) -->
<a href="https://example.com">Link</a>

<!-- NoFollow (doesn't pass equity) -->
<a href="https://example.com" rel="nofollow">Link</a>

<!-- Sponsored (paid links) -->
<a href="https://example.com" rel="sponsored">Link</a>

<!-- UGC (user-generated content) -->
<a href="https://example.com" rel="ugc">Link</a>
```

### 6.2 Link Building Strategies

**White Hat Techniques:**
* **Create linkable assets:** Original research, tools, calculators, infographics
* **Guest posting:** Write for authoritative industry blogs
* **Digital PR:** Get media coverage and journalists' links
* **Broken link building:** Find broken links, offer your content as replacement
* **Resource page links:** Get listed on "best resources" pages
* **Competitor backlink analysis:** Replicate competitors' quality links
* **Unlinked mentions:** Find brand mentions without links, request addition
* **Testimonials:** Provide testimonials with link to client/vendor sites

**Content Types That Earn Links:**
* Original research and surveys
* Comprehensive guides (10,000+ words)
* Interactive tools and calculators
* Infographics with embeddable code
* Industry reports and whitepapers
* Expert roundups and interviews

### 6.3 Avoiding Penalties

**Black Hat Techniques to Avoid:**
* Buying links
* Link farms and PBNs (Private Blog Networks)
* Excessive exact-match anchor text
* Comment spam
* Directory spam
* Hidden links
* Link exchanges at scale

**Google Penalties:**
* **Manual Actions:** Human reviewer penalty (check Search Console)
* **Algorithmic Penalties:** Automatic (Penguin, Panda updates)
* **Recovery:** Remove bad links, disavow toxic backlinks, reconsideration request

### 6.4 Local SEO & NAP Consistency

**NAP = Name, Address, Phone**
*   **Consistency is King:** Maintain identical NAP formatting across all platforms (Google Business Profile, Website, Yelp, Social Media).
*   **Formatting Matters:** Don't mix "St." and "Street" or "(555) 123-4567" and "555-123-4567". Stick to one format.
*   **Update Protocols:** Update all listings immediately if business information changes.
*   **Local Schema:** Ensure your LocalBusiness schema matches your visible NAP exactly.

---

## 7. Technical Implementation Checklist

### 7.1 Pre-Launch SEO Audit

**Critical Elements:**
- [ ] SSL certificate installed (HTTPS)
- [ ] XML sitemap generated and submitted
- [ ] Robots.txt configured correctly
- [ ] Google Search Console verified
- [ ] Google Analytics / GA4 installed
- [ ] All pages have unique title tags
- [ ] All pages have unique meta descriptions
- [ ] All images have alt text
- [ ] No broken links (404 errors)
- [ ] 301 redirects for old URLs (if migration)
- [ ] Canonical tags implemented
- [ ] Structured data added and validated
- [ ] Mobile responsive design
- [ ] Page speed optimized (Core Web Vitals)
- [ ] Internal linking structure
- [ ] Breadcrumb navigation
- [ ] Hreflang tags (if international)
- [ ] Social meta tags (OG, Twitter)

### 7.2 Ongoing Maintenance

**Weekly:**
* Monitor Search Console for errors
* Check Core Web Vitals
* Review new backlinks

**Monthly:**
* Content updates (refresh old posts)
* Keyword ranking tracking
* Competitor analysis
* Technical crawl (Screaming Frog, Sitebulb)

**Quarterly:**
* Comprehensive SEO audit
* Content gap analysis
* Backlink profile review
* Strategy adjustment based on data

---

## 8. AI-Specific Usage Guidelines

When generating code or content using this skill, follow this workflow:

### 8.1 Simplified Development Workflow (Pre-During-Post)

**Pre-Development Checklist:**
1.  **Requirement Analysis:**
    -   [ ] Is this a landing page (high priority) or functional component?
    -   [ ] What is the primary keyword? Target audience? Search intent?
2.  **Schema Selection:**
    -   [ ] Identify applicable schema types (Article, Product, FAQ, etc.)
    -   [ ] Plan the schema hierarchy.
3.  **Content Planning:**
    -   [ ] Define the single H1.
    -   [ ] Outline H2-H6 structure.

**During Development Checklist:**
4.  **HTML & Structure:**
    -   [ ] Validate single `<h1>` presence.
    -   [ ] Check heading hierarchy (no skipped levels).
    -   [ ] Ensure `alt` attributes on all images.
    -   [ ] Set explicit image dimensions (`width` and `height`).
5.  **Meta Implementation:**
    -   [ ] Title tag (50-60 chars, keyword-first).
    -   [ ] Meta description (150-160 chars, CTA included).
    -   [ ] Canonical URL specified.
    -   [ ] Open Graph tags added.

**Post-Development Checklist:**
6.  **Validation:**
    -   [ ] Test with Google Rich Results Test (for schema).
    -   [ ] Verify mobile-friendliness.
    -   [ ] Measure Core Web Vitals (Lighthouse/PageSpeed Insights).
    -   [ ] Check for broken links.

### 8.2 Initial Assessment
1. **Identify page type:**
    * Landing page (high SEO priority)
    * Web app component (medium SEO priority)
    * Admin/internal page (low SEO priority)

2. **Determine target keywords:**
    * Primary keyword (1 per page)
    * Secondary keywords (3-5)
    * Intent type (informational/commercial/transactional)

### 8.2 HTML Structure Generation

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
  <!-- Title (50-60 chars) -->
  <title>Primary Keyword - Secondary Keyword | Brand</title>
  
  <!-- Meta Description (150-160 chars) -->
  <meta name="description" content="Compelling description with primary keyword and CTA">
  
  <!-- Canonical URL -->
  <link rel="canonical" href="https://example.com/page">
  
  <!-- Open Graph -->
  <meta property="og:title" content="Social-optimized title">
  <meta property="og:description" content="Social description">
  <meta property="og:image" content="https://example.com/image.jpg">
  <meta property="og:url" content="https://example.com/page">
  <meta property="og:type" content="website">
  
  <!-- Structured Data -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "WebPage",
    "name": "Page Name",
    "description": "Page description"
  }
  </script>
  
  <!-- Preconnect to external domains -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  
  <!-- Critical CSS inline -->
  <style>
    /* Critical above-fold styles */
  </style>
  
  <!-- Deferred CSS -->
  <link rel="preload" as="style" href="styles.css" onload="this.rel='stylesheet'">
</head>
<body>
  <header>
    <nav aria-label="Primary navigation">
      <!-- Navigation -->
    </nav>
  </header>
  
  <main>
    <article>
      <h1>Primary Keyword in H1</h1>
      
      <section>
        <h2>Descriptive Subheading</h2>
        <p>Content with natural keyword usage...</p>
        
        <img src="image.webp" 
             alt="Descriptive alt text with keywords" 
             width="800" 
             height="600" 
             loading="lazy">
      </section>
    </article>
  </main>
  
  <footer>
    <!-- Footer content -->
  </footer>
  
  <!-- Deferred JavaScript -->
  <script src="script.js" defer></script>
</body>
</html>
```

### 8.3 React/Next.js SEO Implementation

```jsx
// pages/example.jsx
import Head from 'next/head';

export default function ExamplePage({ data }) {
  const structuredData = {
    "@context": "https://schema.org",
    "@type": "Product",
    "name": data.name,
    "description": data.description,
    // ... more schema properties
  };

  return (
    <>
      <Head>
        {/* Title */}
        <title>{`${data.name} - ${data.category} | Brand Name`}</title>
        
        {/* Meta Tags */}
        <meta name="description" content={data.metaDescription} />
        <link rel="canonical" href={`https://example.com${data.slug}`} />
        
        {/* Open Graph */}
        <meta property="og:title" content={data.name} />
        <meta property="og:description" content={data.metaDescription} />
        <meta property="og:image" content={data.image} />
        <meta property="og:url" content={`https://example.com${data.slug}`} />
        
        {/* Structured Data */}
        <script
          type="application/ld+json"
          dangerouslySetInnerHTML={{ __html: JSON.stringify(structuredData) }}
        />
      </Head>
      
      <main>
        <h1>{data.name}</h1>
        {/* Page content */}
      </main>
    </>
  );
}

// Server-side rendering for SEO
export async function getServerSideProps(context) {
  const data = await fetchData(context.params.slug);
  return { props: { data } };
}
```

### 8.4 Validation Checklist

Before delivering code/content, verify:

**Technical:**
- [ ] Valid HTML5 (no unclosed tags, proper nesting)
- [ ] One H1 per page with primary keyword
- [ ] Heading hierarchy (no skipped levels)
- [ ] All images have width, height, alt text
- [ ] Lazy loading on below-fold images
- [ ] Canonical tag present
- [ ] Meta title 50-60 characters
- [ ] Meta description 150-160 characters

**Structured Data:**
- [ ] Appropriate schema type selected
- [ ] All required properties included
- [ ] Valid JSON-LD syntax
- [ ] Validated with Google Rich Results Test

**Performance:**
- [ ] CSS/JS deferred or async where possible
- [ ] Critical CSS inlined
- [ ] Image formats optimized (WebP)
- [ ] Resource hints added (preconnect, dns-prefetch)

**Content:**
- [ ] Primary keyword in H1, first paragraph, conclusion
- [ ] Natural keyword distribution (avoid stuffing)
- [ ] Internal links with descriptive anchor text
- [ ] Content matches search intent
- [ ] Readability optimized (short paragraphs, bullets)

---

## 9. SEO Health Matrix (Expanded)

| Element | Optimized State | Warning Signs | Critical Issues |
|---------|----------------|---------------|-----------------|
| **Title Tag** | `Primary KW - Secondary KW \| Brand` (50-60 chars) | 61-70 chars, missing brand | Generic ("Home"), >70 chars, duplicate |
| **Meta Description** | Unique, compelling, 150-160 chars with CTA | 120-149 or 161-200 chars | Missing, duplicate, >200 chars |
| **URL Structure** | `/category/descriptive-keyword-slug` | 4+ levels deep, some parameters | `?id=123`, uppercase, underscores |
| **H1 Heading** | One per page, primary keyword included | Multiple H1s, no keyword | Missing, identical to title |
| **Images** | WebP/AVIF, alt text, dimensions set, lazy load | JPEG/PNG, missing dimensions | No alt text, huge file sizes |
| **Canonical Tag** | Self-referencing or specified canonical | Missing on paginated pages | Points to wrong URL, missing |
| **Robots.txt** | Strategic blocks, sitemap referenced | Blocks CSS/JS, overly permissive | Blocks important pages |
| **Sitemap** | Updated regularly, <50K URLs, submitted | Not updated monthly, 40-50K URLs | Missing, not submitted, errors |
| **Mobile Friendly** | Responsive, touch targets 48px+, readable | Small text, close buttons | Not mobile responsive |
| **Page Speed** | LCP <2.5s, FID <100ms, CLS <0.1 | LCP 2.5-4s, FID 100-300ms | LCP >4s, FID >300ms, CLS >0.25 |
| **HTTPS** | Valid SSL, no mixed content | Certificate expiring <30 days | HTTP only, expired cert, mixed content |
| **Structured Data** | Appropriate schema, valid JSON-LD | Minor validation warnings | Invalid syntax, wrong schema type |
| **Internal Links** | 3-10 per page, descriptive anchors | 1-2 links, some generic anchors | No links, all "click here" anchors |
| **Content Length** | 1,500-2,500 words for blog, comprehensive | 500-1,000 words, thin content | <300 words, duplicate content |
| **Duplicate Content** | All unique, proper canonicalization | Similar pages without canonical | Exact duplicates, scraped content |
| **Backlink Profile** | Diverse, high DA, relevant sites | Mostly low DA, some irrelevant | Spammy links, penalties detected |
| **JavaScript Rendering** | SSR/SSG, hydration, progressive enhancement | Client-side only with prerendering | Pure SPA, no SSR, crawl issues |

---

## 10. Common SEO Mistakes to Avoid

### Technical Mistakes
* **Blocking resources in robots.txt:** CSS, JS, or images needed for rendering
* **Noindexing important pages:** Accidentally blocking pages from search
* **Redirect chains:** A→B→C instead of A→C
* **Mixed content:** HTTP resources on HTTPS pages
* **Slow server response:** TTFB >600ms
* **JavaScript-only content:** Content not in HTML source
* **Missing mobile optimization:** Not responsive or separate mobile URLs without proper configuration

### Content Mistakes
* **Keyword stuffing:** Unnatural keyword repetition
* **Thin content:** Pages with <300 words, little value
* **Duplicate content:** Same content on multiple URLs
* **Generic meta descriptions:** Same description across pages
* **Hidden text:** White text on white background
* **Over-optimization:** Too many exact-match anchors

### Structural Mistakes
* **Poor internal linking:** Orphan pages with no internal links
* **Deep page hierarchy:** Important content >3 clicks deep
* **Inconsistent URL structure:** Mixed conventions
* **Missing breadcrumbs:** Especially on e-commerce sites
* **Broken internal links:** 404 errors from own site

---

## 11. Resources & Tools

### SEO Analysis Tools
* **Google Search Console:** Performance tracking, indexing issues, Core Web Vitals
* **Google Analytics / GA4:** Traffic analysis, user behavior, conversions
* **Google PageSpeed Insights:** Performance and Core Web Vitals testing
* **Screaming Frog:** Technical SEO crawler (free up to 500 URLs)
* **Ahrefs:** Backlink analysis, keyword research, competitor research
* **SEMrush:** All-in-one SEO platform
* **Moz Pro:** Domain authority, keyword tracking

### Validation & Testing
* **Google Rich Results Test:** Schema markup validation
* **Schema.org Validator:** JSON-LD validation
* **W3C Markup Validator:** HTML validation
* **Mobile-Friendly Test:** Mobile optimization check
* **SSL Labs:** SSL certificate testing

### Performance Tools
* **WebPageTest:** Detailed performance analysis
* **GTmetrix:** Page speed and optimization recommendations
* **Lighthouse:** Chrome DevTools performance audit
* **ImageOptim / Squoosh:** Image compression

### Research Tools
* **Google Keyword Planner:** Keyword research and search volume
* **Answer the Public:** Question-based keyword ideas
* **Also Asked:** People Also Ask questions
* **Google Trends:** Search trend analysis
* **Keywords Everywhere:** Keyword metrics browser extension

### 11.5 Quick Validation Commands (Terminal)

Use these `curl` commands for instant feedback during development:

```bash
# Check if robots.txt exists and is accessible
curl -I https://example.com/robots.txt

# Check sitemap availability
curl -I https://example.com/sitemap.xml

# Check response headers (Verify 200 OK, see server info)
curl -I https://example.com

# Test mobile rendering response (Spoofing iPhone User-Agent)
curl -A "Mozilla/5.0 (iPhone; CPU iPhone OS 14_0 like Mac OS X)" https://example.com
```

---

## 12. Conclusion

SEO is an ongoing process requiring technical precision, strategic content creation, and continuous monitoring. By following these principles, you ensure that:

* Search engines can efficiently crawl and index your content
* Users find relevant, high-quality information that matches their intent
* Pages load quickly and provide excellent user experience
* Content demonstrates expertise and trustworthiness
* Technical implementation follows modern best practices

**Remember:**
* SEO takes time (3-6+ months for results)
* Focus on user value first, optimization second
* Stay updated with algorithm changes
* Test, measure, and iterate based on data
* Quality always beats manipulation

**Priority Order for New Projects:**
1. Technical foundation (HTTPS, mobile-friendly, fast)
2. On-page optimization (titles, headings, content)
3. Structured data implementation
4. Content quality and comprehensiveness
5. Internal linking and site architecture
6. Off-page SEO and link building

This skill should be applied thoughtfully, balancing SEO best practices with user experience and business goals.
