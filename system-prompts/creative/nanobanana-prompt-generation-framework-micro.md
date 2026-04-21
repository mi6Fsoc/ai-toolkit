# Nano Banana Prompt Generation Framework

## Framework Overview

This framework provides a systematic approach to generating high-quality prompts for Google's Imagen models. It can be integrated into any AI tool, custom GPT, or Claude project to produce superior image generation results.

---

## Core Prompt Structure

### Base Template

```
[STYLE_PREFIX] [SUBJECT] [CONTEXT] [MODIFIERS] [QUALITY_ENHANCERS]

```

### Component Breakdown

### 1. **STYLE_PREFIX** (Required)

Choose ONE primary style indicator:

**Photography:**

- `A photo of`
- `A photograph of`
- `A studio photo of`
- `A portrait of`
- `An aerial photo of`

**Art/Illustration:**

- `A painting of`
- `A sketch of`
- `A digital art of`
- `An illustration of`
- `A drawing of`

**Specialized:**

- `A technical drawing of`
- `A 3D render of`
- `A concept art of`

### 2. **SUBJECT** (Required)

The primary focus of the image. Be specific and descriptive.

**Guidelines:**

- Use 3-15 words for subject description
- Include key attributes (color, size, age, material)
- For people: specify age range, gender, appearance details
- For objects: specify type, condition, distinctive features

**Examples:**

- `a woman in her 20s with curly brown hair`
- `a sleek electric sedan with angular design`
- `a Victorian-era mansion with ivy-covered walls`
- `a tabby cat wearing oversized sunglasses`

### 3. **CONTEXT** (Recommended)

Background, environment, and spatial relationships.

**Elements to Include:**

- **Location:** `in a studio`, `on a beach`, `in a forest`, `surrounded by skyscrapers`
- **Environment:** `with mountains in background`, `on a wooden surface`, `in a messy kitchen`
- **Atmosphere:** `at sunset`, `during golden hour`, `in foggy weather`, `under dramatic skies`

### 4. **MODIFIERS** (Essential for Control)

Layer multiple modifiers for precision.

**Photography Modifiers:**

**Camera Proximity:**

- `close-up`, `macro`, `extreme close-up`
- `medium shot`, `full body shot`
- `taken from far away`, `zoomed out`

**Camera Position:**

- `aerial view`, `bird's eye view`, `from above`
- `from below`, `low angle`, `worm's eye view`
- `eye level`, `over the shoulder`

**Lighting:**

- `natural lighting`, `dramatic lighting`, `soft lighting`
- `warm tones`, `cold tones`, `muted orange warm tones`
- `golden hour`, `blue hour`, `harsh midday sun`
- `backlit`, `rim lighting`, `studio lighting`

**Camera Settings:**

- `motion blur`, `soft focus`, `sharp focus`
- `bokeh`, `shallow depth of field`, `deep depth of field`
- `long exposure`, `fast shutter speed`

**Lens Types:**

- `35mm lens`, `50mm lens`, `85mm lens`
- `fisheye lens`, `wide angle lens`, `telephoto lens`
- `macro lens` (for 60-105mm equivalent)

**Film Types:**

- `black and white`, `black and white film`
- `polaroid`, `polaroid portrait`
- `film noir`, `vintage film`, `grainy film`

**Art Style Modifiers:**

**Artistic Techniques:**

- `technical pencil drawing`, `charcoal drawing`, `color pencil drawing`
- `pastel painting`, `oil painting`, `watercolor`
- `digital art`, `concept art`, `isometric 3D`

**Historical References:**

- `in the style of impressionist painting`
- `in the style of renaissance painting`
- `in the style of pop art`
- `art deco`, `art nouveau`, `baroque style`

**Material/Shape Transformations:**

- `made of [material]` (cheese, paper, glass, metal, neon tubes)
- `in the shape of [object]`
- `origami style`, `paper craft style`

### 5. **QUALITY_ENHANCERS** (Highly Recommended)

**General:**

- `high-quality`, `beautiful`, `stylized`, `detailed`
- `professional`, `masterpiece`, `award-winning`

**Photography-Specific:**

- `4K`, `8K`, `HDR`, `high resolution`
- `studio photo`, `professional photography`
- `taken by a professional photographer`
- `sharp details`, `crisp focus`

**Art-Specific:**

- `by a professional artist`, `highly detailed`
- `intricate details`, `fine art quality`

---

## Advanced Features

### Text Integration in Images

**Rules:**

- Keep text to **25 characters or less**
- Use 2-3 distinct phrases maximum
- Specify font style generally (don't expect exact replication)

**Template:**

```
[STYLE] with the text "[TEXT_1]" in [font_style] font [size_descriptor], [optional: underneath/above] this text is "[TEXT_2]"

```

**Example:**

```
A poster with the text "Summerland" in bold font as a title, underneath this text is the slogan "Summer never felt so good"

```

**Font Styles:** `bold`, `serif`, `sans-serif`, `handwritten`, `script`, `modern`, `vintage`

**Size Descriptors:** `small`, `medium`, `large`, `extra large`

---

## Parameterization System

For creating templated prompt systems (logos, products, etc.):

### Template Structure

```
A {parameter1} [fixed_content] for a {parameter2} [fixed_content]. {parameter3}.

```

### Example: Logo Generator

```
A {logo_style} logo for a {company_area} company on a solid color background. Include the text {company_name}.

```

**Parameter Options:**

- `logo_style`: minimalist, modern, traditional, vintage, playful, corporate
- `company_area`: technology, healthcare, baking, finance, education
- `company_name`: user input (keep under 25 characters)

---

## Aspect Ratio Guidelines

### Selection Criteria

**1:1 (Square) - Default**

- Social media posts
- Profile pictures
- Balanced compositions

**4:3 (Fullscreen)**

- Photography projects
- Traditional media
- Horizontal emphasis

**3:4 (Portrait Fullscreen)**

- Vertical subjects
- Portrait photography
- Magazine layouts

**16:9 (Widescreen)**

- Scenic landscapes
- Cinematic shots
- Desktop wallpapers
- Horizontal panoramas

**9:16 (Portrait)**

- Mobile content
- Tall buildings
- Vertical landscapes (waterfalls, trees)
- Social media stories

---

## Specialized Use Case Templates

### 1. Portrait Photography

```
A [proximity] portrait of a [age/description] person [action/pose], [lens]mm lens, [lighting], [film_type], [quality_modifiers]

```

**Example:**

```
A close-up portrait of a woman in her 30s with natural smile, 85mm lens, natural lighting, soft focus, black and white film, 4K, professional photography

```

### 2. Product Photography

```
A studio photo of [product] [material/color], [surface/background], [lighting], [camera_settings], [quality_modifiers]

```

**Example:**

```
A studio photo of a modern armchair made of leather, on white background, dramatic lighting, sharp focus, 4K HDR, taken by a professional photographer

```

### 3. Food Photography

```
A [proximity] photo of [food_item] [presentation_details], [lighting], [lens], professional food photography, [quality_modifiers]

```

**Example:**

```
A close-up photo of french fries arranged artistically, warm lighting, macro lens, professional food photography, 4K, in the style of a food magazine

```

### 4. Landscape Photography

```
[Camera_position] photo of [landscape] [weather/time], [lens], [camera_settings], [quality_modifiers]

```

**Example:**

```
Aerial photo of a river flowing through a mystical valley during golden hour, wide angle lens, long exposure, smooth water, 8K, professional landscape photography

```

### 5. Architectural Photography

```
A photo of [building_type] with [distinctive_features], [camera_position], [lighting], [lens], [quality_modifiers]

```

**Example:**

```
A photo of a modern skyscraper with glass facade, from below, dramatic sunset lighting, wide angle lens, 4K HDR, architectural photography

```

### 6. Wildlife/Action Photography

```
A photo of [animal/subject] [action], [camera_settings], [lens], [lighting], [quality_modifiers]

```

**Example:**

```
A photo of a bird in flight catching prey, fast shutter speed, telephoto lens, natural lighting, 4K, wildlife photography

```

### 7. Artistic Illustration

```
A [art_technique] of [subject] [context], [art_style_reference], [color_palette], [quality_modifiers]

```

**Example:**

```
A watercolor painting of a coastal village at sunset, in the style of impressionist painting, warm color palette, highly detailed, by a professional artist

```

### 8. Abstract/Conceptual

```
[Art_medium] in the shape of [form] made of [material], [style], [quality_modifiers]

```

**Example:**

```
Neon tubes in the shape of a phoenix made of light, cyberpunk style, vibrant colors, highly detailed, digital art

```

---

## Optimization Strategies

### Iteration Protocol

**Stage 1: Core Prompt (Minimal)**

```
[STYLE] [SUBJECT] [BASIC_CONTEXT]

```

**Stage 2: Enhanced Prompt (Recommended)**

```
[STYLE] [DETAILED_SUBJECT] [RICH_CONTEXT] [2-3_MODIFIERS] [QUALITY]

```

**Stage 3: Maximum Detail (Complex)**

```
[STYLE] [DETAILED_SUBJECT] [RICH_CONTEXT] [CAMERA/ART_MODIFIERS] [LIGHTING] [LENS/TECHNIQUE] [QUALITY_STACK]

```

### Prompt Length Guidelines

- **Minimum effective:** 10-15 words
- **Optimal range:** 20-50 words
- **Maximum:** 480 tokens (~360-400 words)

---

## Configuration Parameters

### API Configuration Template

```jsx
config: {
  numberOfImages: [1-4],           // Default: 4
  aspectRatio: "[ratio]",          // "1:1", "3:4", "4:3", "9:16", "16:9"
  imageSize: "[size]",             // "1K" or "2K" (Standard/Ultra only)
  personGeneration: "[setting]"    // "dont_allow", "allow_adult", "allow_all"
}

```

### Configuration Decision Tree

**numberOfImages:**

- 1: Quick test, single concept
- 2-3: Compare variations
- 4: Maximum variety, best result selection

**aspectRatio:**

- Subject is vertical → 3:4 or 9:16
- Subject is horizontal → 4:3 or 16:9
- Subject is balanced → 1:1

**imageSize:**

- Draft/preview → 1K
- Final output/print → 2K

**personGeneration:**

- No people needed → "dont_allow"
- Adults only → "allow_adult"
- Include children → "allow_all" (not available in EU/UK/CH/MENA)

---

## Quality Assurance Checklist

### Pre-Generation Review

- [ ]  Style prefix is clear and appropriate
- [ ]  Subject is specifically described (3-15 words)
- [ ]  Context provides meaningful background
- [ ]  At least 2-3 relevant modifiers included
- [ ]  Quality enhancers added for final output
- [ ]  Prompt length is under 480 tokens
- [ ]  Text requests are under 25 characters
- [ ]  Aspect ratio matches subject orientation
- [ ]  Person generation settings are appropriate
- [ ]  No conflicting style directives

### Post-Generation Refinement

**If results are unsatisfactory:**

1. **Too generic** → Add specific modifiers (lighting, lens, style)
2. **Wrong composition** → Adjust camera position/proximity
3. **Poor quality** → Add quality enhancers (4K, HDR, professional)
4. **Wrong mood** → Modify lighting and color descriptors
5. **Incorrect text** → Simplify text, reduce character count, regenerate
6. **Wrong aspect** → Change aspect ratio parameter

---

## Common Pitfall Avoidance

### DON'T:

- ❌ Use vague subjects ("a person", "a building")
- ❌ Mix incompatible styles ("photorealistic sketch")
- ❌ Request text over 25 characters
- ❌ Use more than 3 text phrases
- ❌ Expect exact font replication
- ❌ Over-specify beyond 480 tokens
- ❌ Use technical jargon without style context

### DO:

- ✅ Be descriptive but concise
- ✅ Layer compatible modifiers
- ✅ Keep text minimal and clear
- ✅ Iterate from simple to complex
- ✅ Specify general font styles
- ✅ Balance detail with token limits
- ✅ Use photography/art terminology appropriately

---

## Integration Guide

### For Custom GPTs/Claude Projects

**System Prompt Addition:**

```
When generating image prompts for Imagen, follow this structure:
1. Start with style prefix (photo/painting/illustration)
2. Describe subject in detail (3-15 words)
3. Add context and environment
4. Layer 2-4 relevant modifiers
5. Include quality enhancers
6. Keep total under 480 tokens
7. For text in images: max 25 characters, 2-3 phrases
8. Select appropriate aspect ratio based on subject

```

**User Interaction Template:**

```
To generate your image prompt, I need:
1. What's the main subject?
2. What style (photo/art/illustration)?
3. What's the setting/context?
4. Any specific details (lighting, angle, mood)?
5. Aspect ratio preference?

[Generate optimized prompt based on framework]

```

---

## Example Prompt Library

### Photorealistic Examples

**Simple:**

```
A photo of coffee beans on a wooden kitchen surface

```

**Enhanced:**

```
A close-up photo of roasted coffee beans on a rustic wooden kitchen surface, natural lighting, shallow depth of field, 4K, professional photography

```

**Maximum:**

```
A macro close-up photo of freshly roasted arabica coffee beans scattered on a weathered wooden kitchen surface, warm natural lighting from window, shallow depth of field with soft bokeh, 50mm lens, 4K HDR, taken by a professional photographer, rich brown tones

```

### Artistic Examples

**Simple:**

```
A painting of a wind farm

```

**Enhanced:**

```
A painting of a wind farm at sunset, in the style of impressionist painting, warm color palette, beautiful

```

**Maximum:**

```
An impressionist oil painting of a modern wind farm during golden hour, vibrant sunset colors bleeding into the sky, loose brushstrokes, in the style of Claude Monet, warm orange and purple tones, highly detailed, by a professional artist, masterpiece quality

```

### Product Examples

**Simple:**

```
A photo of a modern armchair

```

**Enhanced:**

```
A studio photo of a modern leather armchair, white background, dramatic lighting, sharp focus

```

**Maximum:**

```
A professional studio photo of a contemporary mid-century modern armchair in cognac leather, seamless white background, dramatic three-point lighting with soft shadows, sharp focus throughout, 85mm lens, 4K HDR, product photography, taken by a professional photographer

```

---

## Quick Reference Card

```
FORMULA: [STYLE] + [SUBJECT] + [CONTEXT] + [MODIFIERS] + [QUALITY]

STYLES: photo, painting, sketch, digital art, illustration
MODIFIERS: camera (position, proximity, settings, lens), lighting, art technique
QUALITY: 4K, HDR, professional, detailed, high-quality
TEXT: Max 25 chars, 2-3 phrases, specify font style/size
ASPECT: 1:1 (square), 4:3 (landscape), 3:4 (portrait), 16:9 (wide), 9:16 (tall)
LENGTH: 20-50 words optimal, 480 tokens maximum

ITERATE: Simple → Enhanced → Maximum Detail

```

---

This framework provides a comprehensive, systematic approach to generating high-quality Imagen prompts. By following the structured component system and leveraging the specialized templates, you can consistently produce superior image generation results across any use case.