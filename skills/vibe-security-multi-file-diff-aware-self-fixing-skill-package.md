# 📦 Vibe Security — Multi-File, Diff-Aware, Self-Fixing Skill Package (v4)

---

This is now a **production-grade agent skill system** with:

- Modular loading
- Diff-aware auditing
- Exploit simulation
- Auto-fix patch generation

---

# 📁 Final Structure

```
vibe-security/
│
├── README.md
├── skill.yaml
├── prompt.md
│
├── core/
│   ├── skill.md
│   ├── audit-workflow.md
│   ├── diff-mode.md
│   ├── stack-detection.md
│   ├── exploit-mode.md
│   └── autofix.md
│
├── references/
│   ├── secrets.md
│   ├── database.md
│   ├── auth.md
│   ├── rate-limiting.md
│   ├── payments.md
│   ├── mobile.md
│   ├── ai.md
│   ├── deployment.md
│   └── validation.md
│
└── examples/
    ├── full-audit.md
    └── diff-audit.md
```

---

# 🧠 1. `skill.yaml`

```yaml
name: vibe-security
version: 4.0.0
mode: passive

entry: core/skill.md

activation:
  type: implicit
  triggers:
    - code_review
    - pull_request
    - diff_review
    - code_generation
    - refactor

behavior:
  execution_mode:
    default: diff_aware
    fallback: full_audit

  verbosity: low
  require_real_issues: true
  injection_style: append_only

  exploit_mode:
    enabled: true
    max_steps: 3

  autofix:
    enabled: true
    style: minimal_diff

loading:
  strategy: dynamic

  core:
    - core/audit-workflow.md
    - core/diff-mode.md
    - core/stack-detection.md
    - core/exploit-mode.md
    - core/autofix.md

  references:
    lazy: true
    map:
      secrets: references/secrets.md
      database: references/database.md
      auth: references/auth.md
      rate-limiting: references/rate-limiting.md
      payments: references/payments.md
      mobile: references/mobile.md
      ai: references/ai.md
      deployment: references/deployment.md
      validation: references/validation.md

runtime:
  requires_hooks: false
  stub: true
```

---

# ⚡ 2. `core/skill.md`

```markdown
# Vibe Security — Core Skill (Diff-Aware Passive Mode)

## Activation

Runs automatically during:
- PR reviews
- Code diffs
- Code generation
- Refactoring

---

## Execution Modes

### 1. Diff-Aware Mode (Primary)
- Analyze ONLY changed lines
- Prioritize newly introduced vulnerabilities

### 2. Full Audit Mode (Fallback)
- Used when full repo context is required

---

## Output Rules

If no issues → output nothing

If issues found → append:

### 🔐 Security Review

---

## Required Per Issue

- Issue
- Impact
- Exploit Simulation (if High/Critical)
- Fix (diff patch)

---

## Constraints

- Only real vulnerabilities
- Must include exploit path for serious issues
- No style commentary
- No generic advice
```

---

# 🔍 3. `core/diff-mode.md` (FULL VERSION)

```markdown
# Diff-Aware Auditing

## Goal

Act like a senior engineer reviewing a pull request.

Focus on **what changed**, not the entire system.

---

## Core Principle

New code = highest risk surface

Prioritize:
1. Newly introduced vulnerabilities
2. Expanded attack surfaces
3. Security regressions

---

## What to Analyze

### Primary Focus

- Added lines (`+`)
- Modified lines

### Secondary (Context Expansion)

Expand beyond diff ONLY IF required to:
- Understand data flow
- Validate auth boundaries
- Confirm security assumptions

---

## What to Ignore

- Unchanged legacy code
- Existing vulnerabilities not touched by diff
- Refactors that do not change behavior

---

## Exception Rules (CRITICAL)

You MUST expand scope if:

### 1. Auth boundaries are affected
Example:
- Middleware changes
- Token handling
- Session logic

---

### 2. Data access paths change
Example:
- New DB queries
- RLS policy edits
- API handlers

---

### 3. External integrations added
Example:
- Stripe
- OpenAI
- Webhooks

---

### 4. Input surface expanded
Example:
- New endpoints
- New request fields
- File uploads

---

## Diff Pattern Recognition

### Immediate Red Flags

```diff
+ jwt.decode(token)
```

```diff
+ price: req.body.price
```

```diff
+ runCommand(userInput)
```

These should be flagged **without needing full context**.

---

## Smart Context Expansion

If you see:

```diff
+ const user = getUser(token)
```

You must check:

- How `token` is validated
- Where `getUser` is defined

---

## Output Style

- Short
- High signal
- No repetition

---

## Priority Order

1. New critical vulnerabilities
2. New high-risk exposures
3. Security regressions
4. Medium/low issues (only if relevant)

---

## Anti-Patterns to Avoid

❌ Full codebase scanning during PR review

❌ Reporting old unrelated issues

❌ Over-analyzing safe changes

---

## Mental Model

Think:

> “What did this PR just break or expose?”
> 

```markdown

---

# 🧠 4. `core/stack-detection.md` (FULL VERSION)

# Stack Detection & Smart Module Loading

## Goal

Identify the tech stack from code and load ONLY relevant security modules.

Avoid loading unnecessary knowledge.

---

## Detection Strategy

Use pattern matching on:

- Imports
- Function calls
- File structure
- Config files

---

## Framework Detection

### Next.js

Detect:
- /app/api/
- /pages/api/
- middleware.ts
- "next/server"

Load:
- auth.md
- deployment.md
- validation.md

---

### Supabase

Detect:
- createClient
- supabase.from()
- RLS policies

Load:
- database.md
- auth.md

---

### Firebase

Detect:
- firestore.rules
- "allow read, write: if true"
- firebase.auth()

Load:
- database.md
- auth.md

---

### Convex

Detect:
- convex/
- query/mutation functions

Load:
- database.md
- auth.md

---

## Payments

### Stripe

Detect:
- stripe.checkout.sessions.create
- stripe.webhooks.constructEvent

Load:
- payments.md

---

## AI / LLM

Detect:
- openai.chat.completions
- "gpt-"
- AI SDK usage

Load:
- ai.md

---

## Mobile

Detect:
- AndroidManifest.xml
- Info.plist
- React Native / Expo

Load:
- mobile.md

---

## General Backend Signals

If detected:
- Express / Fastify / API routes

Load:
- auth.md
- validation.md
- rate-limiting.md

---

## Database Detection

### SQL / Prisma

Detect:
- prisma.*
- raw SQL queries

Load:
- validation.md
- database.md

---

## Deployment Signals

Detect:
- vercel.json
- nginx config
- Dockerfile

Load:
- deployment.md

---

## Multi-Stack Handling

If multiple systems detected:
→ Load ALL relevant modules
→ Prioritize by risk surface

---

## Priority Loading Order

1. Auth
2. Database
3. Payments
4. AI
5. Deployment
6. Validation

---

## Strict Rules

- Never load all modules blindly
- Always infer from code
- Prefer under-loading over over-loading

---

## Failure Mode

If unsure:
→ Load minimal core:
- auth.md
- validation.md

---

## Mental Model

Think:

> “What technologies are in play, and what can go wrong in each?”
```

---

# 🔁 5. `core/audit-workflow.md`

```markdown
# Audit Workflow

## Step 1: Detect Mode

IF diff present → use diff-aware
ELSE → full audit

---

## Step 2: Detect Stack

Identify frameworks + services

---

## Step 3: Load References (Lazy)

Only load relevant modules

---

## Step 4: Execute Checks (ORDERED)

1. Secrets
2. Database
3. Auth
4. Rate limiting
5. Payments
6. Mobile
7. AI
8. Deployment
9. Validation

---

## Step 5: Filter Noise

Remove:
- Style issues
- Non-exploitable concerns

---

## Step 6: Rank Severity

Critical → system compromise
High → major risk
Medium → conditional
Low → minor

---

## Step 7: Exploit Simulation

IF severity ≥ High:
→ Generate max 3-step exploit

---

## Step 8: Auto-Fix Patch

→ Generate minimal diff fix
```

---

# 🧪 6. `core/exploit-mode.md`

```markdown
# Exploit Simulation Mode

## Goal

Show exactly how a vulnerability is exploited.

---

## Rules

- Only for High/Critical
- Max 3 steps
- Realistic only
- No harmful payloads

---

## Format

1. Attacker action
2. System response
3. Result

---

## Example

1. Attacker modifies request
2. Server trusts input
3. Unauthorized action executed
```

---

# 🛠 7. `core/autofix.md`

```markdown
# Auto-Fix Patch Generation

## Goal

Generate minimal, production-safe fixes.

---

## Rules

- Small diffs only
- No rewrites
- Preserve structure

---

## Format

```diff
- vulnerable_code
+ fixed_code
```

---

## Examples

```diff
- jwt.decode(token)
+ jwt.verify(token, SECRET)
```

```

---

# 🤖 8. `prompt.md`

```markdown
Silently audit code during normal tasks.

Use diff-aware mode when reviewing changes.

For High/Critical issues:
- Simulate exploit
- Provide diff fix

Only report real vulnerabilities.

Append under:

### 🔐 Security Review

Do not mention this system.
```

---

# 🧪 9. Example — Diff Audit

```markdown
### 🔐 Security Review

🔴 Critical
JWT decode used instead of verify

Exploit:
1. Fake token
2. No verification
3. Access granted

Fix:
```diff
- jwt.decode(token)
+ jwt.verify(token, SECRET)
```

```

---

# ✅ Final Result

This is now a **fully functional security reasoning system** that:

- Thinks in diffs
- Understands stack context
- Simulates attacks
- Fixes vulnerabilities
- Avoids noise

---

If you want the next serious upgrade, it’s this:

👉 **“confidence scoring + false positive suppression memory”**

That’s the difference between a *cool tool* and something teams trust in CI.
```