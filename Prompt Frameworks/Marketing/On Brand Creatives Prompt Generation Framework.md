# AI Image Prompt Generation Framework
> A plug-and-play system prompt + structural guide for generating on-brand AI image prompts at scale. Compatible with Claude, ChatGPT, Gemini, and any instruction-following LLM.

---

## How to Use This Framework

1. Copy the **System Prompt** section into your custom AI (Claude Project, GPT, Gem, etc.)
2. Use the **User Message Template** when making requests
3. Reference the **Category Playbook** to tailor prompts for specific use cases
4. Apply the **Structural Formula** to review or manually craft prompts

---

## System Prompt
*Paste this as the system/instruction prompt in your custom AI.*

```
You are a professional AI image prompt engineer. You specialize in crafting detailed, highly effective image generation prompts for brand creatives — the kind used with Midjourney, DALL-E, Stable Diffusion, and Adobe Firefly.

Your prompts follow this structure:
Subject → Setting/Environment → Lighting → Style/Mood → Technical specs → Brand-specific details

Each prompt is a single rich paragraph, 50–100 words, written as a direct generation instruction (no preamble, no numbering, just the prompt text). Every prompt you write should be meaningfully distinct — vary the angle, mood, lighting approach, and compositional technique. Make them feel professional and production-ready.

When asked to generate multiple variations, ensure each one differs in at least three of the following dimensions:
- Camera angle or perspective (overhead, eye-level, close-up, wide establishing shot)
- Lighting setup (soft studio, natural golden hour, dramatic side lighting, backlit, etc.)
- Background / environment (minimal, contextual, abstract, textured)
- Mood / emotional register (energetic, serene, luxurious, raw, playful)
- Compositional style (centered symmetry, rule of thirds, negative space, editorial crop)

Respond ONLY with a JSON array of prompt strings unless the user asks for a different format.
No markdown, no keys, no explanation — just the array.
Example: ["prompt one here", "prompt two here"]
```

---

## User Message Template
*Use this structure every time you make a generation request.*

```
Generate [NUMBER] distinct AI image generation prompts for the following brief:

- Category: [see Category Playbook below]
- Subject / brand details: [product name, brand colors, key visual identity notes]
- Platform / use case: [e.g. Instagram post, LinkedIn banner, product packaging, website hero]
- Style direction: [e.g. editorial, high contrast, dark mood, pastel minimalist]
- Additional constraints: [aspect ratio, must-include elements, things to avoid]

Make each prompt meaningfully different in composition, lighting angle, and mood
while staying true to the brief.
```

### Example Filled Request

```
Generate 6 distinct AI image generation prompts for the following brief:

- Category: Product photography
- Subject / brand details: A premium skincare serum in a frosted glass bottle,
  brand colors are midnight blue and warm gold, minimalist identity
- Platform / use case: Instagram feed post
- Style direction: Editorial, luxury, high contrast
- Additional constraints: Portrait orientation (4:5), no human subjects,
  always include the full bottle

Make each prompt meaningfully different in composition, lighting angle, and mood
while staying true to the brief.
```

---

## Structural Formula
*The anatomy of a high-performing image generation prompt.*

```
[SUBJECT + KEY DETAILS]
+ [SETTING / ENVIRONMENT]
+ [LIGHTING STYLE]
+ [MOOD / EMOTIONAL TONE]
+ [COMPOSITIONAL APPROACH]
+ [TECHNICAL SPECS]
+ [BRAND-SPECIFIC DETAILS]
```

### Formula in Action

| Element | Weak version | Strong version |
|---|---|---|
| Subject | "a perfume bottle" | "a slender amber glass perfume bottle with a gold-leaf stopper" |
| Setting | "on a table" | "on a cracked white marble surface dusted with dried rose petals" |
| Lighting | "good lighting" | "raking side light from camera left, casting long soft shadows" |
| Mood | "luxury" | "intimate and sensorial, as if discovered on a dressing table at dusk" |
| Composition | "centered" | "rule of thirds, slight low angle, generous negative space above" |
| Technical | "high quality" | "medium-format editorial photography, f/2.8, shallow depth of field" |
| Brand | "brand colors" | "warm ivory background, accents in dusty rose and brushed brass" |

---

## Category Playbook

### 1. Product Photography
**Best for:** E-commerce, D2C brands, packaging, hero shots
**Prompt focus:** Texture, material quality, surface interaction, lighting drama

**Template:**
```
A high-resolution [adjective] product shot of [product description] placed on [surface].
[Lighting description]. The background is [background style], with [shadow/reflection detail]
to highlight the product's [key quality]. [Mood]. Shot in the style of [reference aesthetic,
e.g. "MSCHF editorial" or "Apple product photography"].
```

**Example:**
```
A high-resolution product shot of a matte black ceramic candle vessel placed on a polished
obsidian surface. Directional backlight creates a soft halo effect, while a secondary fill
light from camera right reveals the vessel's subtle texture. The background is deep charcoal
with an almost imperceptible gradient. Mood is meditative and premium. Shot in the style of
luxury fragrance editorial photography, medium format, shallow depth of field.
```

---

### 2. Brand Portrait
**Best for:** Team pages, spokesperson content, ambassador campaigns
**Prompt focus:** Consistent facial structure, brand-coded clothing, professional expression

**Template:**
```
A professional portrait of a [gender, approximate age] individual with [hair description],
wearing [brand-coded clothing colors and style]. The background is [backdrop description
using brand palette]. [Lighting setup]. The expression is [emotional tone]. The image should
feel [overall aesthetic — e.g. "approachable and modern"].
```

**Example:**
```
A professional portrait of a woman in her early thirties with sleek dark hair pulled back,
wearing a structured blazer in deep forest green and ivory. Background is a soft gradient
from warm cream to sage. Studio lighting with a large octabox overhead and a subtle hair
light. Expression is confident and direct. The image should feel polished, editorial,
and quietly authoritative.
```

---

### 3. Social Media Post
**Best for:** Instagram, LinkedIn, Twitter/X, Pinterest
**Prompt focus:** Platform aspect ratio, typographic space, strong visual hook

**Template:**
```
A [platform]-optimized image ([aspect ratio]) for [brand/campaign name]. [Visual description
of the hero element]. [Background description]. The composition leaves [top/bottom/side]
space for [overlay text / CTA / logo]. [Color palette]. [Mood and energy]. Design aesthetic
is [style reference].
```

**Example:**
```
An Instagram-optimized image (4:5 ratio) for a wellness supplement brand. A glass of sparkling
water with a dissolved effervescent tablet, shot from slightly above at a 45-degree angle.
Background is a clean white tile surface with scattered citrus slices and mint sprigs. The
composition leaves the upper third clear for headline text overlay. Color palette is mint
green, citrus yellow, and white. Mood is fresh, energetic, and clean. Design aesthetic is
modern apothecary meets food editorial.
```

---

### 4. Brand Background / Texture
**Best for:** Website headers, presentation decks, digital stationery, packaging fills
**Prompt focus:** Seamlessness, color accuracy, scalability, non-distracting

**Template:**
```
A seamless [style: abstract / geometric / organic / gradient] background pattern featuring
[shape or texture description] in [brand primary color] and [brand secondary color].
The design is [adjective trio, e.g. "modern, fluid, and minimal"], with [technical detail,
e.g. "soft gradients and no hard edges"]. Optimized for [use case]. High-resolution,
tileable output.
```

**Example:**
```
A seamless abstract wave pattern featuring flowing, organic shapes in deep navy (#0A1628)
and warm sand (#E8D5B0). The design is modern, fluid, and minimal, with soft gradients and
no hard edges or repeating artifacts. Subtle depth created through layered opacity. Optimized
for website header backgrounds and slide decks. High-resolution, tileable, landscape
orientation.
```

---

### 5. Lifestyle Shot
**Best for:** Brand storytelling, email campaigns, lookbooks, ads
**Prompt focus:** Authentic context, human interaction, aspirational environment

**Template:**
```
A premium lifestyle image of [product] in [realistic, aspirational setting]. [Environmental
description with sensory details]. A [person description] is [action — naturally interacting
with the product]. [Lighting description]. The image conveys [lifestyle aspiration, e.g.
"slow living and intentional self-care"]. Shot in the aesthetic of [editorial/photography
reference].
```

**Example:**
```
A premium lifestyle image of a leather-bound notebook on a sunlit oak writing desk in a
minimalist home studio. Warm morning light streams through a linen curtain, casting long
soft shadows across scattered pencils and a small potted eucalyptus. A person's hand —
rings on two fingers — rests on the open notebook mid-sentence. The image conveys creative
focus and slow, intentional work. Shot in the aesthetic of Kinfolk magazine editorial
photography, natural color grade.
```

---

### 6. Campaign Banner
**Best for:** Black Friday, seasonal campaigns, launches, event promos
**Prompt focus:** Bold contrast, clear hierarchy, high visual impact, CTA space

**Template:**
```
A high-impact [campaign name] banner ([dimensions]) for [brand/product]. The design features
[hero visual description] against [background]. Bold [color] typography with [font energy,
e.g. "condensed, all-caps impact style"]. [Dynamic element — glow, motion blur, texture].
A clear [left/right/bottom] zone for [CTA / offer text]. Overall energy is [campaign mood].
```

**Example:**
```
A high-impact Black Friday banner (1920×1080px) for a premium sneaker brand. The design
features a dramatic side-lit sneaker floating at a slight angle against a deep matte black
background. Bold electric blue typography in a condensed, high-energy style. Subtle motion
blur trails extend from the sole, implying speed. A clear lower-third zone reserved for
sale percentage and CTA text. Overall energy is dark, powerful, and aspirational.
```

---

## Variation Techniques
*Use these modifiers to force genuine diversity across a batch of prompts.*

| Dimension | Option A | Option B | Option C | Option D |
|---|---|---|---|---|
| **Perspective** | Overhead flat-lay | Eye-level straight-on | Low angle looking up | 45° three-quarter |
| **Lighting** | Soft diffused studio | Natural golden hour | Dramatic hard side light | Backlit silhouette |
| **Background** | Pure white/minimal | Contextual environment | Abstract texture | Brand-color gradient |
| **Mood** | Energetic / bold | Serene / minimal | Warm / intimate | Cold / editorial |
| **Composition** | Centered symmetry | Rule of thirds | Negative space dominant | Tight editorial crop |
| **Color grading** | True to life | Muted / desaturated | Warm-toned | High contrast B&W |

---

## Tips for Prompt Engineering

**1. Be specific over generic**
Replace vague descriptors ("good lighting", "professional look") with concrete technical or visual language ("octabox overhead, soft fill from camera right, catchlight visible in subject's eyes").

**2. Name your reference aesthetic**
Adding "in the style of [Kinfolk magazine / Apple product photography / Bottega Veneta campaign]" anchors the model to a recognizable visual register without copyright issues.

**3. Specify what NOT to include**
Negative prompts prevent common failure modes: "no text overlays", "no human subjects", "avoid busy backgrounds", "no lens flare".

**4. Stack technical specs at the end**
End every prompt with: `[camera/format], [focal length or depth of field], [aspect ratio], [resolution note]`. Example: `medium-format digital, 85mm equivalent, f/2.8, 4:5, ultra-high resolution`.

**5. Iterate in batches, not individually**
Generate 8–12 at a time, select the 2–3 strongest directions, then run targeted follow-up batches for those angles. Faster than refining one prompt at a time.

---

## Quick-Reference Cheatsheet

```
FORMULA:   Subject → Setting → Lighting → Mood → Composition → Specs → Brand
BATCH SIZE: 8–12 for exploration / 3–5 for refinement
VARY BY:   Angle + Lighting + Mood (minimum 3 dimensions per batch)
END WITH:  Camera format, focal length, aspect ratio, resolution
AVOID:     Vague descriptors, no specs, same composition repeated
```

---

*Framework version 1.0 — compatible with Midjourney, DALL-E 3, Stable Diffusion, Adobe Firefly, Ideogram, and any instruction-following LLM (Claude, ChatGPT, Gemini).*
