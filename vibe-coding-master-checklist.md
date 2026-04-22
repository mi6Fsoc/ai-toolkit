# Vibe Coding Master Checklist

> **How to use this document**
> Each section has two parts: a **Checklist** (things you do manually or verify) and an **AI Prompt** (paste into your AI tool to automate the work). Items marked 🔴 are P0 — do these before anything else. Items marked 🟡 are P1 — important but not blocking. Items marked 🟢 are P2 — polish and best practice.
>
> **Recommended sequence:** Security → Database → Testing → Performance → Accessibility → Observability → Cost & Usage → Deployment

---

## 1. Security

### Checklist

**Authentication & Access Control**
- 🔴 Test login/logout flow multiple times in sequence
- 🔴 Manually visit private URLs while logged out — confirm redirect
- 🔴 Confirm passwords are hashed (never stored in plaintext)
- 🔴 Enable Row Level Security (RLS) in Supabase *before* adding users
- 🔴 Verify users cannot access other users' data by spoofing IDs
- 🟡 Add session timeouts and idle logout
- 🟡 Test all OAuth / social login flows end-to-end
- 🟡 Implement role-based access (admin vs. user vs. guest)

**Input & API Security**
- 🔴 Review every form for validation and server-side sanitisation
- 🔴 Scan all frontend components for hardcoded API keys
- 🔴 Move all secrets to environment variables
- 🟡 Test rate limiting on all public-facing endpoints
- 🟡 Configure CORS — allow only your own domains
- 🟡 Add Content Security Policy (CSP) headers
- 🟢 Run `npm audit` and resolve high/critical vulnerabilities
- 🟢 Check for dependency vulnerabilities with a tool like Snyk

**Data & Infrastructure**
- 🔴 Confirm database connection strings are never exposed to the client
- 🔴 Error messages shown to users contain no stack traces or DB details
- 🟡 Ensure HTTPS is enforced everywhere (no mixed content)
- 🟡 Run secrets scanning in your CI/CD pipeline (e.g. GitHub secret scanning)
- 🟢 Review third-party packages — remove unused ones

### AI Prompt

```
Conduct a comprehensive security audit of my application and implement these measures:

Authentication & Access Control:
- Ensure secure password storage with proper hashing
- Add session timeouts and proper logout functionality
- Implement user role restrictions and data isolation
- Verify Supabase RLS policies are enabled and correctly scoped per user
- Test OAuth flows and confirm they handle failure states gracefully

Input & API Protection:
- Review all form inputs for server-side validation and sanitisation
- Scan every frontend file for hardcoded API keys and move them to environment variables
- Add rate limiting to all public endpoints to prevent abuse
- Configure CORS to only allow trusted origins
- Implement Content Security Policy (CSP) headers

Infrastructure:
- Ensure error handling never exposes stack traces or database details to users
- Verify HTTPS is enforced across all routes
- Run a dependency vulnerability check and flag high/critical issues

Provide a summary of every specific change made, grouped by category.
```

---

## 2. Database

### Checklist

**Schema & Relationships**
- 🔴 All tables have a primary key
- 🔴 Foreign keys are defined and enforce referential integrity
- 🔴 Junction tables exist for all many-to-many relationships
- 🟡 Schema is normalised — no duplicated data across tables
- 🟡 Unique constraints on emails, usernames, and phone numbers
- 🟡 NOT NULL constraints applied where data is always required
- 🟡 Correct data types used throughout (don't store numbers as strings)

**Performance**
- 🟡 Indexes added to all frequently queried columns
- 🟡 Indexes added to all foreign key columns
- 🟢 Slow query log reviewed and problematic queries optimised
- 🟢 Connection pooling configured (e.g. PgBouncer for Supabase)

**Data Integrity & Compliance**
- 🔴 Soft delete pattern chosen and implemented (or hard delete justified)
- 🟡 Data retention policy defined — how long is user data kept?
- 🟡 Right-to-erasure flow implemented (GDPR compliance)
- 🟡 Automatic database backups enabled and tested
- 🟢 Migration strategy documented for future schema changes

### AI Prompt

```
Review my database schema and ensure it covers the following:

Structure & Relationships:
- Proper primary and foreign keys with referential integrity
- Normalised structure avoiding data duplication
- Junction tables for any many-to-many relationships
- Unique constraints on emails, usernames, and phone numbers
- NOT NULL constraints where appropriate
- Correct data types throughout

Performance:
- Indexes on frequently queried and all foreign key columns
- Connection pooling configuration advice for my platform
- Identification of any N+1 query patterns

Compliance & Maintenance:
- Soft delete vs. hard delete recommendation for my use case
- GDPR right-to-erasure implementation
- Backup and recovery configuration
- A migration plan for future schema changes

Explain every architectural decision and flag anything that could cause problems at scale.
```

---

## 3. Testing

### Checklist

**Unit & Integration Tests**
- 🟡 Core business logic functions have unit tests
- 🟡 API utility functions are tested with mocked responses
- 🟡 Auth helper functions tested (token validation, role checks)

**End-to-End (E2E) Tests**
- 🔴 Critical happy path tested: sign up → core action → sign out
- 🔴 Auth edge cases tested: wrong password, expired session, locked account
- 🟡 Key user flows automated with Playwright or Cypress
- 🟡 Mobile viewport tested in E2E suite

**Manual QA**
- 🔴 Full manual walkthrough on desktop Chrome before every deploy
- 🔴 Full manual walkthrough on mobile Safari before every deploy
- 🟡 Test all empty states (new user, no results, empty list)
- 🟡 Test all error states (failed API call, no internet, timeout)
- 🟢 Cross-browser check: Chrome, Firefox, Safari, Edge

**CI Integration**
- 🟡 Tests run automatically on every pull request
- 🟡 Deploy is blocked if tests fail
- 🟢 Test coverage report generated and tracked over time

### AI Prompt

```
Set up a testing strategy for my application. Implement the following:

Unit Tests:
- Identify and test all core business logic functions
- Mock external dependencies (API calls, database) appropriately
- Test authentication helpers: token validation, role checks, session handling

E2E Tests (Playwright preferred):
- Write a smoke test for the primary happy path: [describe your main user journey]
- Write tests for key auth edge cases: failed login, expired session, unauthorised access
- Test the most critical user action in the application: [describe it]
- Include a mobile viewport configuration

Test Configuration:
- Set up the test runner and config file
- Add a test script to package.json
- Provide a GitHub Actions workflow that runs tests on every PR and blocks merge on failure

Output all test files, config, and CI workflow. Explain the coverage strategy.
```

---

## 4. Performance

### Checklist

**Measurement First**
- 🔴 Run PageSpeed Insights on your production URL
- 🔴 Run Lighthouse audit (Performance, Accessibility, SEO, Best Practices)
- 🟡 Identify your three slowest pages using Chrome DevTools Network tab
- 🟡 Check Core Web Vitals: LCP, CLS, INP

**Assets**
- 🔴 All images compressed (target ≤100KB where possible)
- 🔴 Images served in modern formats (WebP, AVIF)
- 🟡 Lazy loading implemented for all off-screen images
- 🟡 SVGs used for icons instead of PNG/JPG

**Code & Bundles**
- 🟡 Unused JavaScript and CSS identified and removed
- 🟡 Large bundles split into smaller chunks (code splitting)
- 🟡 Tree-shaking verified in build output
- 🟢 Fonts loaded with `font-display: swap`

**Caching & Delivery**
- 🟡 CDN configured for static assets
- 🟡 Cache-Control headers set appropriately
- 🟡 Stale-while-revalidate strategy in place for dynamic data
- 🟢 SSR vs. CSR decision reviewed — are you rendering in the right place?

**UX Performance**
- 🟡 Loading skeletons or spinners on all async operations
- 🟡 Pagination or infinite scroll for large data sets
- 🟢 Optimistic UI updates for common actions

### AI Prompt

```
My application needs performance optimisation. Here is my PageSpeed data:

[Paste your PageSpeed / Lighthouse results here]

Implement optimizations in this order:

1. Asset Optimization
   - Compress and convert images to WebP/AVIF (target ≤100KB)
   - Add lazy loading to all off-screen images
   - Replace image-based icons with SVGs

2. Bundle Optimization
   - Remove unused JavaScript and CSS
   - Implement code splitting for large bundles
   - Verify tree-shaking is working in the build

3. Caching & Delivery
   - Configure CDN for static assets
   - Set correct Cache-Control headers
   - Implement stale-while-revalidate for dynamic data

4. UX Performance
   - Add loading states and skeleton screens for all async operations
   - Implement pagination for large data sets
   - Identify any layout shifts (CLS) and resolve them with explicit sizing

For each optimization:
1. Identify the specific issue in my code
2. Show the updated implementation
3. Explain the performance benefit
4. Estimate the PageSpeed score improvement

Work through these systematically and confirm each stage before proceeding.
```

---

## 5. Accessibility (a11y)

### Checklist

**Structure & Semantics**
- 🔴 Correct HTML elements used (buttons are `<button>`, not `<div>`)
- 🔴 Page has exactly one `<h1>` and logical heading hierarchy
- 🟡 All images have descriptive `alt` text (or `alt=""` for decorative images)
- 🟡 All form inputs have associated `<label>` elements
- 🟡 ARIA roles and attributes used where native HTML is insufficient

**Keyboard & Focus**
- 🔴 Every interactive element is reachable via Tab key
- 🔴 Focus indicator is visible (never `outline: none` without replacement)
- 🟡 Modals and drawers trap focus correctly
- 🟡 Escape key closes modals and dropdowns

**Visual**
- 🔴 Text contrast ratio meets WCAG AA: 4.5:1 for normal text, 3:1 for large text
- 🟡 UI does not rely on colour alone to convey meaning
- 🟡 Text is readable at 200% browser zoom
- 🟢 Motion respects `prefers-reduced-motion`

**Screen Reader**
- 🟡 Test with VoiceOver (Mac/iOS) or NVDA (Windows) on critical flows
- 🟡 Dynamic content updates announced via ARIA live regions
- 🟢 Run automated check with axe DevTools browser extension

### AI Prompt

```
Audit my application for accessibility and implement fixes to meet WCAG 2.1 AA standard:

Semantics & Structure:
- Replace any non-semantic elements used as buttons or links
- Ensure heading hierarchy is logical (h1 → h2 → h3)
- Add appropriate alt text to all images
- Associate all form inputs with labels

Keyboard Navigation:
- Verify every interactive element is keyboard accessible
- Implement visible focus indicators where missing
- Add focus trapping for modals and overlays
- Ensure Escape key dismisses all modals and dropdowns

Visual Accessibility:
- Check and fix all text contrast ratios to meet 4.5:1 (AA)
- Remove any colour-only indicators and add text or icon alternatives
- Add prefers-reduced-motion support for animations

ARIA:
- Add ARIA labels to icon-only buttons
- Implement aria-live regions for dynamic content updates
- Review ARIA role usage for correctness

For each fix, show the before and after code and explain the accessibility benefit.
```

---

## 6. Observability & Error Monitoring

### Checklist

**Error Tracking**
- 🔴 Error tracking tool integrated (Sentry recommended)
- 🔴 Frontend errors captured and routed to a dashboard
- 🟡 Backend / API errors captured separately
- 🟡 Source maps uploaded so stack traces are readable
- 🟡 Error alerts configured (email or Slack notification on new issues)

**Logging**
- 🟡 Structured logging in place (JSON format, not raw `console.log`)
- 🟡 Log levels used correctly: error, warn, info, debug
- 🟡 All `console.log` statements removed from production builds
- 🟢 Centralised log aggregation configured (e.g. Logtail, Datadog)

**Performance Monitoring**
- 🟡 Core Web Vitals tracked in production (not just locally)
- 🟡 Slow API calls flagged with performance traces
- 🟢 Uptime monitoring in place (e.g. Better Uptime, UptimeRobot)
- 🟢 Alerting thresholds set for error rate spikes and latency

### AI Prompt

```
Set up observability for my application:

Error Tracking (Sentry):
- Install and configure Sentry for both frontend and backend
- Set up source map uploads so stack traces are readable in production
- Configure alert rules: notify me when a new error occurs or error rate spikes
- Add a global error boundary component that reports to Sentry and shows a user-friendly fallback UI

Logging:
- Replace all console.log calls with a structured logger (JSON format)
- Implement log levels: error, warn, info, debug
- Strip debug/info logs from production builds
- Suggest a log aggregation solution appropriate for my stack

Performance Monitoring:
- Set up Core Web Vitals tracking in production
- Add performance traces for slow API calls (flag anything over 1s)
- Configure uptime monitoring with alerting

For each step, provide the installation instructions, configuration code, and test to verify it's working.
```

---

## 7. Cost & Usage Monitoring

### Checklist

**AI API Costs**
- 🔴 Spend alerts configured in your AI provider dashboard (OpenAI, Anthropic, etc.)
- 🔴 Hard monthly spend cap set
- 🟡 Token usage logged per request so you can identify expensive calls
- 🟡 Prompts reviewed for unnecessary verbosity
- 🟡 Model tier reviewed — are you using a larger model than needed?
- 🟢 Caching in place for repeated identical prompts

**Infrastructure Costs**
- 🟡 Supabase usage tracked: row counts, storage, bandwidth, function invocations
- 🟡 Vercel/Netlify usage tracked: build minutes, function invocations, bandwidth
- 🟡 Alerts set for when you approach free tier limits
- 🟢 Cost forecast reviewed monthly

**Rate Limits & Abuse Prevention**
- 🔴 Rate limiting on all AI-powered endpoints (these are expensive to abuse)
- 🟡 User-level usage quotas implemented if applicable
- 🟡 Bot detection or CAPTCHA on public AI entry points
- 🟢 Anomaly detection: alert if a single user consumes disproportionate resources

### AI Prompt

```
Implement cost and usage monitoring for my application:

AI API Spend:
- Add token usage logging to every AI API call (log model, tokens in, tokens out, cost estimate)
- Implement a per-user or per-session token budget with enforcement
- Add caching for repeated identical prompts to reduce redundant API calls
- Review my current prompts and suggest condensed versions that reduce token usage without sacrificing quality

Rate Limiting for AI Endpoints:
- Implement strict rate limiting on all AI-powered routes (suggest appropriate limits)
- Add user-level quotas if my application has authenticated users
- Return a clear, user-friendly error when limits are hit

Infrastructure Usage:
- Add monitoring for Supabase usage: rows read/written, storage, edge function calls
- Set up alerts when usage approaches [my plan limits]
- Suggest the cheapest architecture change that would reduce my biggest cost driver

Provide all implementation code and a dashboard or logging approach I can review weekly.
```

---

## 8. Deployment

### Checklist

**Environment Configuration**
- 🔴 All secrets in environment variables — nothing hardcoded
- 🔴 Separate `.env.development` and `.env.production` configs
- 🔴 Production environment variables set in your hosting platform
- 🟡 CI/CD pipeline connected to your main branch
- 🟡 Preview deployments enabled for pull requests
- 🟡 Branch protection rules: require PR review + passing tests before merge
- 🟢 Rollback strategy documented (how do you revert a bad deploy?)

**Error Handling & UX**
- 🔴 Global error boundary implemented — app never shows a white screen
- 🔴 Custom 404 page exists and is branded
- 🟡 Custom 500 / error page exists with a user-friendly message
- 🟡 Network error state handled gracefully
- 🟡 All async operations have loading states

**SEO & Meta**
- 🟡 Meta title and description set on every page
- 🟡 Open Graph tags for social sharing (og:title, og:description, og:image)
- 🟡 `robots.txt` and `sitemap.xml` generated
- 🟢 Canonical URLs set to prevent duplicate content

**Pre-Launch Checklist**
- 🔴 All `console.log` and debug code removed
- 🔴 Custom domain configured and SSL verified (HTTPS active)
- 🔴 Production smoke test: walk through the full critical user journey
- 🟡 Performance baseline recorded (PageSpeed score at launch)
- 🟡 Favicon and app icons set
- 🟢 Cookie consent / privacy policy in place if collecting user data

### AI Prompt

```
Prepare my application for production deployment:

Current Setup:
- Built with [your AI tool / framework]
- Backend: Supabase
- Hosting: [Vercel / Netlify / other]
- Custom domain: [yourdomain.com]

Step 1 — Environment Configuration:
- Audit all files for hardcoded secrets and move them to environment variables
- Create .env.example with all required variables (no real values)
- Set up production vs. development environment configs

Step 2 — Error Handling:
- Implement a global error boundary that catches crashes and shows a friendly fallback
- Create a custom 404 page
- Create a custom error page for server errors
- Add loading states to every async operation that's missing one

Step 3 — SEO & Meta:
- Add meta title, description, and Open Graph tags to every page
- Generate robots.txt and sitemap.xml
- Set canonical URLs

Step 4 — CI/CD Pipeline:
- Provide a GitHub Actions workflow that: runs tests, checks for secrets, builds, and deploys to [platform]
- Configure branch protection: block merges if tests fail
- Enable preview deployments for PRs

Step 5 — Pre-Launch:
- Strip all console.log and debug code
- Verify custom domain and SSL setup
- Provide a final production smoke test checklist

For each step: exact code changes, platform configuration, a simple test to verify, and troubleshooting guidance.
```

---

## Master Sequence: Putting It All Together

Use this order to avoid doing work twice:

| Stage | Why this order |
|---|---|
| 1. Security | Fixing auth and RLS first prevents building features on top of broken access control |
| 2. Database | Schema changes are painful later — get the foundation right now |
| 3. Testing | Write tests before optimising so you can refactor safely |
| 4. Performance | Optimise after structure is stable |
| 5. Accessibility | Easier to audit a complete UI than a moving one |
| 6. Observability | You need monitoring before you go live |
| 7. Cost & Usage | Caps and alerts in place before real traffic hits |
| 8. Deployment | Launch only after everything above is done |

---

## Quick Reference: Priority Legend

| Symbol | Priority | Meaning |
|---|---|---|
| 🔴 P0 | Critical | Do before launch. A missing P0 is a bug, a security hole, or a broken experience. |
| 🟡 P1 | Important | Do in your first week post-launch if not before. Skipping these creates technical debt. |
| 🟢 P2 | Polish | Good practice. Do when you have breathing room. |
