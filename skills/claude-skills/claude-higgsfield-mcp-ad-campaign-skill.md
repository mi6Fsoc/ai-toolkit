# Instagram Ad Campaign Generator

> End-to-end automation skill for creating 50-ad Instagram campaigns from a single product image. Combines web research, creative strategy, Higgsfield MCP generation (Nano Banana 2 + Soul 2), and delivery — all from one conversation.

---

## When to Use This Skill

- User uploads a product image and wants Instagram ads
- User asks you to "create an ad campaign", "generate Instagram ads", or "build creatives"
- User wants product photography variations at scale
- User mentions Higgsfield, Nano Banana, or Soul for ad generation
- User says "build me ads", "create a campaign", or "generate social media creatives"

---

## Prerequisites

### Required Tools

Verify these are available before starting:

| Tool | Purpose | Check |
|------|---------|-------|
| **Playwright / Web Search** | Research current IG ad trends and competitor creative | Run `list_tools` to confirm browser/search tools |
| **Higgsfield MCP** | Image generation via Nano Banana 2 and Soul 2 | Confirm `mcp.higgsfield.ai/mcp` is connected |
| **Product Image** | User-uploaded reference image | Must be provided before Step 1 |

### If Higgsfield MCP is NOT connected

Instruct the user:

```
1. Open your AI agent settings
2. Add a custom MCP connector named "Higgsfield"
3. Paste the URL: https://mcp.higgsfield.ai/mcp
4. Click Add → Connect and sign in with your Higgsfield account
```

> ⚠️ **Do NOT proceed until the Higgsfield MCP is connected and you can access `generate_image` and related tools.**

---

## Workflow Checklist

```
- [ ] Step 0: Intake — collect product image + brand context
- [ ] Step 1: Research — IG trends, competitor analysis, creative angles
- [ ] Step 2: Strategy — build 50-ad matrix for approval
- [ ] Step 3: Generation — produce all 50 ads via Higgsfield MCP
- [ ] Step 4: Delivery — organize, recommend, and suggest copy
```

---

## Pre-Flight: Intake Questionnaire

Before beginning any research, ask the user these clarifying questions. **Do NOT skip this step.** Gathering this context dramatically improves research quality and prompt accuracy.

### Required Information

| Question | Why It Matters |
|----------|---------------|
| **What is the product?** (name, category, key features) | Determines research direction and prompt language |
| **Who is the target audience?** (age, gender, interests, pain points) | Shapes creative angles and visual tone |
| **What is the brand voice?** (luxury, playful, minimal, bold, clinical, etc.) | Controls mood, typography cues, and color grading |
| **Brand colors?** (hex codes or descriptions) | Ensures visual consistency across all 50 ads |
| **What platforms/placements?** (feed, stories, reels, explore) | Confirms aspect ratio requirements |
| **Any existing brand assets or style references?** | Anchors the aesthetic to established identity |
| **What is the campaign goal?** (awareness, conversion, engagement, retargeting) | Influences creative angle prioritization |
| **Competitors or brands to reference?** | Directs competitive research |
| **Anything to avoid?** (colors, styles, messaging, imagery) | Prevents wasted generations |

### Optional but Valuable

- Price point (premium vs. mass market changes the visual register)
- USP / key differentiator
- Existing ad performance data (what's worked before?)
- Seasonal or promotional context

> **Store all intake answers in a `BRIEF.md` mental model.** Reference this throughout every step.

---

## Step 1: Research Phase

### Objective
Build a data-backed creative brief by researching current Instagram ad trends, competitor creative, and high-performing patterns.

### 1a: Research Current IG Ad Trends (2026)

Use Playwright or web search to investigate:

```
Search queries:
- "Instagram ad trends 2026 top performing creative formats"
- "best Instagram ad creative formats hooks 2026"
- "Instagram Reels ad best practices 2026"
- "high performing Instagram ad visual styles 2026"
- "Instagram ad hooks that convert 2026"
```

**Extract and document:**

| Dimension | What to Find |
|-----------|-------------|
| **Formats** | Which creative formats are driving highest engagement (carousels, static, Reels, etc.) |
| **Hooks** | First-frame patterns that stop the scroll (text overlays, bold visuals, pattern interrupts) |
| **Visual styles** | Dominant aesthetics (UGC-raw, studio-polished, AI-native, mixed media, etc.) |
| **Color trends** | Palettes trending in paid social (earth tones, neon, muted pastels, high contrast) |
| **Copy patterns** | CTA styles, headline structures, caption formulas that drive action |
| **Platform updates** | Any new IG ad features, algorithm changes, or placement specs |

### 1b: Research Product Category & Competitors

```
Search queries (customize to the product):
- "[product category] Instagram ads examples 2026"
- "[product category] best performing social ads"
- "[competitor brand] Instagram ad strategy"
- "top [product category] DTC brands Instagram creative"
```

**Extract and document:**

- Top 5 competitors and their creative approaches
- Common visual patterns in this product category
- Price point positioning reflected in creative style
- What's working vs. what's saturated

### 1c: Research Top Creative Angles

```
Search queries:
- "Instagram ad creative angles that convert 2026"
- "UGC vs lifestyle vs studio ads performance comparison"
- "problem solution ads Instagram performance"
- "social proof ads vs aspirational ads conversion rates"
```

**Document the top 5 proven creative angles:**

| Angle | Description | Best For |
|-------|-------------|----------|
| **Lifestyle** | Product in aspirational real-world context | Awareness, brand building |
| **UGC-Style** | Raw, authentic, phone-shot aesthetic | Trust, conversion, retargeting |
| **Studio Hero** | Clean, polished product-forward photography | Catalog, consideration, e-commerce |
| **Problem/Solution** | Before/after or pain-point-driven narrative | Conversion, direct response |
| **Aspirational** | Premium, mood-driven, editorial aesthetic | Luxury positioning, brand equity |

### 1d: Compile Creative Brief

Synthesize all research into a **Creative Brief** of 8-10 bullet points:

```markdown
## Creative Brief — [Product Name] Instagram Campaign

1. **Category insight:** [What's working in this product category right now]
2. **Top trend #1:** [Most relevant IG ad trend for this product]
3. **Top trend #2:** [Second most relevant trend]
4. **Visual style direction:** [Recommended dominant aesthetic]
5. **Color strategy:** [Brand colors + trend-informed accents]
6. **Hook pattern:** [First-frame strategy based on research]
7. **Competitive gap:** [What competitors aren't doing that we should]
8. **Primary angle:** [Which creative angle to lead with]
9. **Secondary angles:** [Supporting angles for variety]
10. **Platform specs:** [Aspect ratios, safe zones, format notes]
```

> **Present the Creative Brief to the user for review before proceeding to Step 2.**

---

## Step 2: Strategy Phase

### Objective
Design a structured 50-ad matrix that covers 5 creative angles × 5 settings × 2 aspect ratios, with mood variation throughout.

### 2a: Define the 5 Creative Angles

Based on the research, define 5 angles. Customize these based on the product — the defaults below are starting points:

| # | Angle | Visual Treatment | Higgsfield Model |
|---|-------|-----------------|-----------------|
| 1 | **Lifestyle** | Product in real-world aspirational setting | Nano Banana 2 (scene compositing) |
| 2 | **UGC-Style** | Raw, authentic, natural-light aesthetic | Soul 2 (photorealistic human models) |
| 3 | **Studio Hero** | Clean backdrop, dramatic lighting, product focus | Nano Banana 2 (product preservation) |
| 4 | **Problem/Solution** | Split or sequential showing pain → relief | Nano Banana 2 (scene compositing) |
| 5 | **Aspirational** | Premium, editorial, mood-driven | Soul 2 (aesthetic depth) or Nano Banana 2 |

### 2b: Define 5 Settings Per Angle

For each angle, design 5 distinct backgrounds/environments:

**Example (customize per product):**

| Angle | Setting 1 | Setting 2 | Setting 3 | Setting 4 | Setting 5 |
|-------|-----------|-----------|-----------|-----------|-----------|
| Lifestyle | Morning kitchen | Urban café | Beach sunset | Home office | Garden terrace |
| UGC-Style | Bathroom mirror selfie | Car dashboard | Gym locker | Bed flat-lay | Walking outdoors |
| Studio Hero | White seamless | Dark marble | Gradient backdrop | Textured concrete | Color-matched brand BG |
| Problem/Solution | Cluttered "before" | Clean "after" | Side-by-side split | Close-up texture | Infographic-style |
| Aspirational | Luxury hotel suite | Rooftop skyline | Gallery/museum | First class cabin | Designer workspace |

### 2c: Define Mood Distribution

Distribute moods across the 50 ads for maximum variety:

| Mood | Count | Characteristics |
|------|-------|----------------|
| **Bright/Airy** | ~12 ads | High-key lighting, soft shadows, pastel or white-dominant palette |
| **Moody/Premium** | ~12 ads | Low-key lighting, deep shadows, rich tones, editorial feel |
| **Vibrant/Playful** | ~10 ads | Saturated colors, dynamic compositions, energetic |
| **Minimal/Clean** | ~8 ads | Negative space, simple compositions, restrained palette |
| **Bold/Contrasty** | ~8 ads | High contrast, dramatic lighting, punchy colors |

### 2d: Build the 50-Ad Matrix

Present as a table with this structure:

```markdown
## 50-Ad Campaign Matrix — [Product Name]

| Ad # | Angle | Setting | Mood | Aspect Ratio | Model | Prompt Summary |
|------|-------|---------|------|-------------|-------|----------------|
| 01 | Lifestyle | Morning kitchen | Bright/Airy | 1:1 | Nano Banana 2 | Product on marble counter, morning light streaming through window... |
| 02 | Lifestyle | Morning kitchen | Bright/Airy | 9:16 | Nano Banana 2 | Same scene, vertical crop for Stories/Reels... |
| 03 | Lifestyle | Urban café | Moody/Premium | 1:1 | Nano Banana 2 | Product on café table, warm ambient lighting... |
| 04 | Lifestyle | Urban café | Moody/Premium | 9:16 | Nano Banana 2 | Same scene, vertical crop... |
| ... | ... | ... | ... | ... | ... | ... |
| 49 | Aspirational | Designer workspace | Minimal/Clean | 1:1 | Nano Banana 2 | Product on designer desk, neutral tones... |
| 50 | Aspirational | Designer workspace | Minimal/Clean | 9:16 | Nano Banana 2 | Same scene, vertical crop... |
```

### Matrix Structure Logic

```
5 angles × 5 settings = 25 unique scenes
25 scenes × 2 aspect ratios (1:1 + 9:16) = 50 total ads
```

> **Present the complete 50-ad matrix to the user for approval before proceeding to Step 3.**
>
> Wait for explicit approval. If the user wants changes, iterate the matrix. **Do NOT generate images until approved.**

---

## Step 3: Generation Phase

### Objective
Generate all 50 ads using Higgsfield MCP, processing in batches of 10 with user visibility at each checkpoint.

### 3a: Model Selection Rules

| Use Case | Model | Why |
|----------|-------|-----|
| Product compositing into scenes | **Nano Banana 2** | Best for preserving product details, adding text/scenes, maintaining fidelity |
| Ads featuring human models | **Soul 2** | Photorealistic humans holding/using the product, fashion-grade aesthetics |
| Product-only hero shots | **Nano Banana 2** | Clean product preservation with background generation |
| Character-consistent campaigns | **Soul 2 + Soul ID** | Same model/person across multiple ads |

### 3b: Prompt Engineering Template

For each ad, construct the Higgsfield prompt using this formula:

```
[Product description from uploaded image] + [Setting/Environment] + [Lighting/Mood keywords] +
[Composition direction] + [Aspect ratio context] + [Quality modifiers]
```

**Prompt template for Nano Banana 2:**
```
Professional [mood] product photography of [product description] placed in [setting].
[Lighting description]. [Composition — e.g., "centered with negative space for text overlay"].
The product is the clear hero of the image. [Color/brand direction].
[Quality: "commercial quality, high-resolution, Instagram-optimized"].
```

**Prompt template for Soul 2 (with human models):**
```
A [age/gender description] person [action with product] in [setting].
[Lighting description]. [Mood/aesthetic direction].
The product is clearly visible and prominent. [Styling direction].
[Quality: "editorial photography, natural skin tones, authentic"].
```

### 3c: Batch Generation Protocol

Process ads in **5 batches of 10**:

```
Batch 1: Ads 01-10 (Lifestyle angle, all 5 settings × 2 ratios)
Batch 2: Ads 11-20 (UGC-Style angle)
Batch 3: Ads 21-30 (Studio Hero angle)
Batch 4: Ads 31-40 (Problem/Solution angle)
Batch 5: Ads 41-50 (Aspirational angle)
```

**For each batch:**

1. **Generate** — Call Higgsfield `generate_image` with:
   - `prompt`: The crafted prompt from the template above
   - The user's uploaded product image as the reference image
   - Model: `nano_banana_2` or `soul_2` as specified in the matrix
   - Aspect ratio: `1:1` or `9:16` as specified

2. **Poll** — Higgsfield runs asynchronously. Poll for completion status.

3. **Present** — Show the user each completed batch with:

```markdown
### Batch [X] Complete — [Angle Name]

| Ad # | Setting | Mood | Ratio | Image | Caption | Hashtags |
|------|---------|------|-------|-------|---------|----------|
| 01 | Morning kitchen | Bright/Airy | 1:1 | [image] | "Start your morning right ☀️" | #MorningRoutine #ProductName #SelfCare |
| 02 | Morning kitchen | Bright/Airy | 9:16 | [image] | "This changed everything 🌿" | #DailyEssentials #Wellness #NewFavorite |
| ... | ... | ... | ... | ... | ... | ... |
```

4. **Checkpoint** — Ask: "Batch [X] complete. Any adjustments before I continue to Batch [X+1]?"

### 3d: Caption & Hashtag Generation

For each ad, generate:

- **Caption** (1-2 sentences): Hook + value prop, aligned with the creative angle
- **3 Hashtags**: Mix of broad reach, niche, and branded

**Caption formulas by angle:**

| Angle | Caption Formula | Example |
|-------|----------------|---------|
| Lifestyle | [Aspiration] + [Product as enabler] | "Your calm morning ritual, elevated. ☀️" |
| UGC-Style | [Authentic reaction] + [Social proof cue] | "OK I'm obsessed 😍 this is the one" |
| Studio Hero | [Feature highlight] + [CTA] | "Precision-crafted for perfection. Shop now →" |
| Problem/Solution | [Pain point?] + [Solution] | "Tired of [problem]? Meet your solution." |
| Aspirational | [Mood/feeling] + [Brand statement] | "Some things are simply worth it. ✨" |

### 3e: Error Handling

| Error | Cause | Fix |
|-------|-------|-----|
| Generation fails / timeout | API overload or complex prompt | Retry with simplified prompt; reduce scene complexity |
| Product not preserved accurately | Prompt too vague on product details | Add more specific product descriptors; emphasize "preserve the exact product" |
| Wrong aspect ratio | Parameter mismatch | Double-check ratio parameter before generation |
| Human model looks artificial | Soul 2 prompt too generic | Add "natural skin tones, authentic expression, candid pose" |
| Brand colors not reflected | Colors not specified in prompt | Add explicit hex codes or color descriptions to prompt |
| Credits insufficient | Higgsfield plan limit reached | Alert user; suggest upgrading plan or reducing batch size |

---

## Step 4: Delivery Phase

### Objective
Organize all 50 ads, recommend top performers for A/B testing, and suggest copy variations.

### 4a: Organize by Creative Angle

Present a summary organized by angle:

```markdown
## Campaign Summary — [Product Name]

### Total: 50 Ads Generated
- 10 × Lifestyle
- 10 × UGC-Style
- 10 × Studio Hero
- 10 × Problem/Solution
- 10 × Aspirational

---

### 🏡 Lifestyle (Ads 01-10)
| Ad # | Setting | Mood | Ratio | Caption Preview |
|------|---------|------|-------|----------------|
| 01 | Morning kitchen | Bright/Airy | 1:1 | "Start your morning right ☀️" |
| ... | ... | ... | ... | ... |

### 📱 UGC-Style (Ads 11-20)
[same table format]

### 🎯 Studio Hero (Ads 21-30)
[same table format]

### 💡 Problem/Solution (Ads 31-40)
[same table format]

### ✨ Aspirational (Ads 41-50)
[same table format]
```

### 4b: Top 5 A/B Test Recommendations

Based on the research from Step 1, recommend the top 5 ads to test first:

```markdown
## Recommended A/B Test — First 5 Ads

| Priority | Ad # | Why This One | Test Against |
|----------|------|-------------|-------------|
| 1 | [#] | [Research-backed reasoning — e.g., "UGC-style outperforms studio by 2.3x in this category"] | [Complementary ad #] |
| 2 | [#] | [Reasoning] | [Complementary ad #] |
| 3 | [#] | [Reasoning] | [Complementary ad #] |
| 4 | [#] | [Reasoning] | [Complementary ad #] |
| 5 | [#] | [Reasoning] | [Complementary ad #] |

### Testing Strategy
- **Budget allocation:** 70% to top 2, 30% split across remaining 3
- **Test duration:** 3-5 days minimum per variant
- **Primary metric:** [Based on campaign goal — CTR for awareness, CPA for conversion]
- **Kill criteria:** Drop any ad below [X]% CTR after 1,000 impressions
```

### 4c: Copy Variations for Winners

For each of the top 5 recommended ads, provide 3 caption variations:

```markdown
## Copy Variations — Top 5 Ads

### Ad #[X] — [Angle] / [Setting]

| Variation | Caption | CTA |
|-----------|---------|-----|
| A (Original) | "[original caption]" | Shop Now |
| B (Question hook) | "[rewritten as question]" | Learn More |
| C (Social proof) | "[rewritten with social proof element]" | Try It Free |

### Ad #[Y] — [Angle] / [Setting]
[same format]
```

### 4d: Final Deliverable Checklist

```
- [ ] All 50 ads generated and organized
- [ ] Each ad has caption + 3 hashtags
- [ ] Ads organized by creative angle
- [ ] Top 5 A/B test recommendations with reasoning
- [ ] Copy variations for top 5 winners
- [ ] Testing strategy with budget allocation and metrics
```

---

## Quick Reference: Full Campaign in 4 Steps

```
Step 0: Intake → Gather product image + brand context + audience info
Step 1: Research → IG trends + competitor audit + creative angles → Creative Brief
Step 2: Strategy → 50-ad matrix (5 angles × 5 settings × 2 ratios) → User approval
Step 3: Generate → Higgsfield MCP in 5 batches of 10, with captions + hashtags
Step 4: Deliver → Organized summary + Top 5 recommendations + copy variations
```

---

## Model Quick Reference

### Nano Banana 2 — Use for:
- Product compositing into any scene or background
- Preserving exact product details and textures
- Adding text overlays or graphic elements
- Product-only hero shots with generated environments
- Problem/solution and before/after compositions

### Soul 2 — Use for:
- Ads featuring human models holding/using the product
- Fashion-grade, photorealistic people
- Character-consistent campaigns (same model across multiple ads via Soul ID)
- Lifestyle scenes requiring authentic human interaction
- Aspirational/editorial aesthetic with people

### Higgsfield MCP Connection

```
Server URL: https://mcp.higgsfield.ai/mcp
Key tools: generate_image, generate_video (if video ads needed)
Auth: Higgsfield account (no API key management)
Processing: Asynchronous — poll for results
Credits: Based on your Higgsfield plan
```

---

## Prompt Engineering Best Practices for Ad Creative

### DO ✅

- **Lead with the product** — Always describe the product clearly and early in the prompt
- **Specify the mood explicitly** — "bright, airy, soft morning light" not just "nice lighting"
- **Include composition direction** — "product centered with upper third clear for text overlay"
- **Reference the platform** — "Instagram feed optimized" or "vertical Stories format"
- **Use commercial photography language** — "commercial product photography", "editorial lifestyle shot"
- **Preserve brand consistency** — Reference brand colors and visual identity in every prompt
- **Add negative guidance when needed** — "no text, no watermarks, no busy backgrounds"

### DON'T ❌

- **Don't be vague** — "nice product photo" produces generic results
- **Don't overload the prompt** — Keep it focused, 50-100 words
- **Don't forget the reference image** — Always include the user's uploaded product image
- **Don't mix incompatible moods** — "moody and bright and playful" cancels out
- **Don't generate without approval** — Always get matrix sign-off first
- **Don't skip the research** — Data-backed creative outperforms guesswork every time

---

## Variation Techniques for Batch Diversity

Use these modifiers to ensure genuine visual diversity across the 50 ads:

| Dimension | Variation A | Variation B | Variation C | Variation D | Variation E |
|-----------|-------------|-------------|-------------|-------------|-------------|
| **Perspective** | Eye-level straight-on | Overhead flat-lay | 45° three-quarter | Low angle looking up | Close-up detail |
| **Lighting** | Soft diffused natural | Golden hour warm | Dramatic hard side | Backlit rim light | Studio controlled |
| **Background** | Pure white/minimal | Contextual environment | Color gradient | Textured surface | Depth-blurred scene |
| **Color grading** | True to life | Warm-toned | Cool-toned | Muted/desaturated | High contrast |
| **Composition** | Centered symmetry | Rule of thirds | Negative space heavy | Tight editorial crop | Environmental wide |

---

*Skill version 1.0 — Designed for Claude + Higgsfield MCP (Nano Banana 2 + Soul 2). Compatible with any MCP-enabled AI agent.*
