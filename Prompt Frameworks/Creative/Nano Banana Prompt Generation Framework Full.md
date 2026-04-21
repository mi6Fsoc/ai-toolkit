# Nano Banana Prompt Generation Framework — Complete Knowledge Base

> A comprehensive, production-ready framework for generating superior image prompts for Google's Nano Banana (Gemini native image generation) AI. This single document contains the entire framework: instructions, modifier libraries, configuration data, templates, TypeScript source code, and integration examples.

---

## Table of Contents

1. [Role & Workflow](#role--workflow)
2. [Prompt Structure](#prompt-structure)
3. [Configuration Options](#configuration-options)
4. [Photography Modifiers](#photography-modifiers)
5. [Art Style Modifiers](#art-style-modifiers)
6. [Quality Modifiers](#quality-modifiers)
7. [Material & Shape Modifiers](#material--shape-modifiers)
8. [Photorealism Specialization](#photorealism-specialization)
9. [Aspect Ratio Guide](#aspect-ratio-guide)
10. [Prompt Templates](#prompt-templates)
11. [Best Practices](#best-practices)
12. [Usage Examples](#usage-examples)
13. [TypeScript Source Code](#typescript-source-code)

---

## Role & Workflow

You are an expert Nano Banana prompt generator. Your role is to help users create superior prompts for Google's Nano Banana (Gemini native image generation) AI.

### When a user requests a Nano Banana prompt:

1. **Understand Requirements** — Ask about subject, style, intended use, mood. Clarify ambiguities. Determine if it's photography, art, or mixed.
2. **Construct the Prompt** — Follow the structure: `[Style] + [Subject] + [Context] + [Modifiers] + [Quality]`. Reference the appropriate modifier libraries. Use technical terms from photography/art modifiers.
3. **Optimize** — Keep under 480 tokens. Ensure clarity and specificity. Remove redundancy.
4. **Present Complete Solution** — Full prompt (ready to use), recommended configuration (aspect ratio, model, image size), brief explanation of key choices.

### Response Format

Always provide:
1. **Complete Prompt** (ready to copy/paste)
2. **Configuration Recommendations**
   - Model: [model name]
   - Aspect Ratio: [ratio]
   - Image Size: [1K or 2K]
   - Number of Images: [1-4]
3. **Key Choices Explanation** (2-3 sentences)

---

## Prompt Structure

### Formula

```
[Style/Medium] of [Subject], [Context], [Technical Modifiers], [Quality Enhancers]
```

### Required Elements

- **Subject** (Required): The main focus of the image. Be specific — "a luxury sports car" not "a car".
- **Context** (Recommended): Background, setting, or environment — "in an urban setting at night".
- **Style** (Recommended): Overall visual approach — "professional studio photo", "watercolor painting".

### Optional Elements

- **Modifiers**: Photography settings, art techniques, material specifications.
- **Quality Enhancers**: General quality terms, context-specific modifiers, professional indicators.
- **Text in Image**: Up to 3 phrases, 25 characters or less per phrase. Specify placement and style.

---

## Configuration Options

### Models (Nano Banana Family)

"Nano Banana" is Google's name for Gemini's native image generation capabilities. The family comprises three models:

| Model ID | Nano Banana Name | Description | Image Sizes |
|---|---|---|---|
| `gemini-3-pro-image-preview` | **Nano Banana Pro** | Professional asset production. Advanced reasoning ("Thinking") for complex instructions and high-fidelity text rendering. Best quality. | 1K, 2K, 4K |
| `gemini-3.1-flash-image-preview` | **Nano Banana 2** | High-efficiency model optimized for speed and high-volume use cases. Adds 512 resolution and extra aspect ratios. | 512, 1K, 2K, 4K |
| `gemini-2.5-flash-image` | **Nano Banana** | Legacy fast model for general speed and efficiency. Good for conversational editing and lightweight tasks. | 1K, 2K |

**When to use which:**
- **Nano Banana Pro** — When images must carry text, product UI, brand consistency, or complex multi-element compositions.
- **Nano Banana 2** — When you need many iterations, batch throughput, or fast turnaround.
- **Nano Banana (legacy)** — Fallback for lightweight jobs or when the newer models are unavailable.

### Key Capabilities

- **Conversational editing**: Multi-turn image editing using text prompts and reference images
- **Thinking mode**: The model reasons through complex prompts, generating interim "thought images" to refine composition before the final output
- **Up to 14 reference images**: Mix reference images per prompt (Pro: up to 6 objects + 5 characters; Flash: up to 10 objects + 4 characters)
- **Advanced text rendering**: Legible, stylized text for infographics, menus, diagrams, and marketing assets
- **Grounding with Google Search**: Generate imagery based on real-time data (weather maps, stock charts, recent events)
- **SynthID watermark**: All generated images include an invisible SynthID watermark

### Prompt Constraints

- **Language**: English only
- **Text in image**: Max 25 characters per phrase, max 3 phrases recommended
- **Number of images**: 1-4 (default: 4)

### Aspect Ratios

All models support: `1:1` · `3:4` · `4:3` · `9:16` · `16:9` · `2:3` · `3:2` · `4:5` · `5:4` · `21:9`

Nano Banana 2 additionally supports: `1:4` · `4:1` · `1:8` · `8:1`

### Image Sizes

| Size | Description | Availability |
|---|---|---|
| **512** (0.5K) | Smallest, fastest | Nano Banana 2 only |
| **1K** (default) | Standard quality, fast generation | All models |
| **2K** | High quality | All models |
| **4K** | Highest quality | Nano Banana Pro, Nano Banana 2 |

### Person Generation

| Setting | Description | Restrictions |
|---|---|---|
| `dont_allow` | Block generation of people | — |
| `allow_adult` (default) | Adults only, no children | — |
| `allow_all` | Adults and children | Not allowed in EU, UK, CH, MENA |

### Default Configuration

```json
{
  "model": "gemini-3-pro-image-preview",
  "numberOfImages": 4,
  "aspectRatio": "1:1",
  "imageSize": "1K",
  "personGeneration": "allow_adult"
}
```

---

## Photography Modifiers

### Camera Proximity

| Modifier | Description | Use Cases |
|---|---|---|
| `close-up` / `close up` | Very near to subject, showing detail | Portraits, product details, texture emphasis |
| `extreme close-up` | Extremely near, showing minute details | Macro details, emotion capture, texture focus |
| `medium shot` | Balanced framing | Portraits, product photography, general use |
| `full shot` / `wide shot` | Shows entire subject | Full body portraits, architecture, products in context |
| `zoomed out` / `taken from far away` | Far from subject, showing context | Landscapes, environmental context, establishing shots |

### Camera Position

| Modifier | Description | Use Cases | Example |
|---|---|---|---|
| `aerial` / `bird's eye view` | Looking down from above | Urban photography, landscapes, patterns | "aerial photo of urban city with skyscrapers" |
| `from below` / `low angle` | Looking up from below | Dramatic portraits, architecture, trees | "photo of a forest canopy from below" |
| `eye-level` | Same height as subject | Natural portraits, product photography | — |
| `high angle` | Camera above, looking down | Flatlay, food photography | — |
| `dutch angle` | Camera tilted on axis | Creative compositions, disorientation | — |
| `over the shoulder` | Behind one subject looking at another | Storytelling, interaction shots | — |

### Lighting

| Modifier | Description | Use Cases | Example |
|---|---|---|---|
| `natural lighting` | Natural light sources | Portraits, products, general | "studio photo of a modern arm chair, natural lighting" |
| `dramatic lighting` | High contrast, theatrical | Portraits, mood shots | "studio photo of a modern arm chair, dramatic lighting" |
| `warm lighting` | Orange/yellow temperature | Cozy atmospheres, sunset scenes | — |
| `cold lighting` / `cool lighting` | Blue temperature | Clinical settings, modern aesthetics, winter | — |
| `golden hour` | Warm, soft (sunrise/sunset) | Landscapes, portraits, romantic scenes | "the sun sets across the lake, golden hour" |
| `blue hour` | Cool, soft (pre-sunrise/post-sunset) | Cityscapes, architectural, moody scenes | — |
| `studio lighting` / `controlled lighting` | Professional controlled setup | Product photography, professional portraits | — |
| `soft lighting` / `diffused lighting` | Even, gentle, minimal shadows | Flattering portraits, beauty shots | — |
| `hard lighting` | Direct, strong shadows | Dramatic portraits, film noir, texture | — |
| `backlit` | Light behind subject | Silhouettes, rim lighting, ethereal effects | — |
| `rim lighting` | Light outlining subject edges | Separation from background, dramatic portraits | — |

### Camera Settings

| Modifier | Description | Use Cases | Example |
|---|---|---|---|
| `motion blur` | Blur from movement | Dynamic scenes, speed indication | "city from inside a car with motion blur" |
| `soft focus` | Dreamy, slightly out of focus | Romantic scenes, ethereal portraits | "soft focus photograph of a bridge at night" |
| `bokeh` | Aesthetic background blur | Portraits, subject isolation | — |
| `portrait mode` | Shallow depth of field effect | Portraits, subject isolation | — |
| `shallow depth of field` | Small area in focus | Portraits, product focus, macro | — |
| `deep focus` | Everything in focus | Landscapes, architecture, documentary | — |
| `tilt-shift` | Miniature effect | Creative cityscapes, miniature effect | — |
| `long exposure` | Extended shutter time | Waterfalls, star trails, smooth water | — |
| `fast shutter speed` | Freezes motion | Sports, wildlife, action | "a winning touchdown, fast shutter speed" |
| `movement tracking` / `action tracking` | Camera follows moving subject | Sports, wildlife, dynamic scenes | "deer running in forest, movement tracking" |

### Lens Types

#### Wide-Angle (10-24mm)

| Lens | Focal Length | Use Cases | Example |
|---|---|---|---|
| `wide angle` | 10-24mm | Landscapes, architecture, interiors | "mountain range, landscape wide angle 10mm" |
| `fisheye` | 8-15mm | Creative, skateboarding, action sports | "street photography, NYC, fisheye lens" |

#### Standard (24-70mm)

| Lens | Focal Length | Use Cases | Example |
|---|---|---|---|
| `35mm` | 35mm | Street photography, documentary, environmental portraits | "35mm portrait, blue and grey duotones" |
| `50mm` | 50mm | Portraits, street photography, general use | — |

#### Macro (60-105mm)

| Lens | Focal Length | Use Cases | Example |
|---|---|---|---|
| `macro` / `macro lens` | 60-105mm | Insects, plants, food, product details | "photo of a leaf, macro lens" |
| `60mm macro` | 60mm | Food, products, flowers | "leaf of prayer plant, macro lens, 60mm" |
| `100mm macro` | 100mm | Insects, shy subjects, food | "plate of pasta, 100mm Macro lens" |

#### Telephoto (85-400mm)

| Lens | Focal Length | Use Cases | Example |
|---|---|---|---|
| `85mm` | 85mm | Portraits, headshots, fashion | — |
| `telephoto zoom` | 100-400mm | Wildlife, sports, bird photography | — |

### Film Types

| Modifier | Description | Use Cases | Example |
|---|---|---|---|
| `black and white` | Monochrome | Classic portraits, artistic, documentary | "B&W photo of dog wearing sunglasses" |
| `polaroid` / `instant film` | Instant film look | Vintage aesthetic, casual portraits | "polaroid portrait of a dog" |
| `film noir` | High contrast B&W + dramatic lighting | Dramatic portraits, moody scenes | "A woman, 35mm portrait, film noir" |
| `vintage film` | Old film stock aesthetic | Nostalgic, retro photography | — |
| `35mm film` | Standard film format | General photography | — |
| `color film` | Traditional color photography | Vibrant scenes, realistic colors | — |

### Photography Specializations (Photorealism Quick Reference)

| Use Case | Lens Type | Focal Lengths | Key Modifiers |
|---|---|---|---|
| **Portraits** | Prime or zoom | 24-35mm, 50mm, 85mm | B&W film, film noir, depth of field, duotones, portrait mode, bokeh |
| **Objects/Still Life** (food, insects, plants) | Macro | 60-105mm | High detail, precise focusing, controlled lighting, shallow DOF |
| **Motion/Action** (sports, wildlife) | Telephoto zoom | 100-400mm | Fast shutter speed, action tracking, movement tracking |
| **Wide-Angle/Landscape** (astronomical, landscape) | Wide-angle | 10-24mm | Long exposure, sharp focus, smooth water, smooth clouds, deep focus |

---

## Art Style Modifiers

### Art Mediums

#### Drawing

| Medium | Description | Use Cases | Example |
|---|---|---|---|
| `sketch` | Quick, loose drawing | Concepts, informal art | "sketch of a modern apartment building" |
| `pencil drawing` | Traditional pencil | Realistic portraits, studies | — |
| `technical pencil drawing` | Precise, architectural | Architecture, product design | "technical pencil drawing of an electric sedan" |
| `charcoal drawing` | Bold, dramatic, rich blacks | Portraits, life drawing | "charcoal drawing of an electric sedan" |
| `color pencil drawing` | Vibrant colored pencil | Illustrations, botanical drawings | — |
| `ink drawing` / `pen and ink` | Bold line work | Comics, illustrations, technical | — |

#### Painting

| Medium | Description | Use Cases |
|---|---|---|
| `painting` | General painted artwork | Traditional art |
| `pastel painting` | Soft, chalk-like | Portraits, landscapes, still life |
| `watercolor` | Transparent, fluid | Landscapes, botanical art |
| `oil painting` | Rich, traditional | Portraits, fine art, classical |
| `acrylic painting` | Versatile, fast-drying | Modern art, abstract, murals |
| `gouache` | Opaque watercolor | Illustrations, graphic art |

#### Digital

| Medium | Description | Use Cases | Example |
|---|---|---|---|
| `digital art` | Computer-created | Concept art, illustrations | "digital art of an electric sedan" |
| `digital render` / `3D render` | 3D computer-generated | Product visualization, architecture | "digital render of a massive skyscraper" |
| `vector art` | Scalable graphics | Logos, icons, graphic design | — |
| `isometric 3D` | Geometric 3D perspective | Infographics, game art | — |
| `low poly` | Minimalist with visible polygons | Modern art, game art | — |

### General Art Styles

| Style | Description | Use Cases |
|---|---|---|
| `realistic` | True-to-life | Portraits, still life |
| `photorealistic` | Indistinguishable from photos | Hyperrealism, product visualization |
| `abstract` | Non-representational | Modern art, emotional expression |
| `minimalist` | Simple, essential elements | Modern design, logos |
| `modern` | Contemporary aesthetic | Design, architecture |
| `traditional` | Classical approach | Heritage brands, fine art |
| `stylized` | Distinctive artistic interpretation | Illustrations, character design |
| `cartoon` | Simplified, exaggerated | Children's content, humor |
| `anime` | Japanese animation style | Character art, manga |
| `comic book` | American comic aesthetic | Superhero art, action scenes |

### Historical Art Styles

| Style | Period | Description | Characteristics |
|---|---|---|---|
| `impressionism` | Late 19th century | Loose brushwork, light effects | Visible brushstrokes, emphasis on light |
| `renaissance` | 14th-17th century | Classical realism, balanced composition | Realistic proportions, chiaroscuro |
| `baroque` | 17th-18th century | Drama, movement, rich colors | Dramatic lighting, grandeur |
| `art nouveau` | 1890-1910 | Organic lines, natural forms | Flowing lines, natural motifs |
| `art deco` | 1920s-1930s | Geometric patterns, luxury | Geometric shapes, metallic colors |
| `pop art` | 1950s-1960s | Bold colors, commercial imagery | Bright colors, repetition |
| `surrealism` | 1920s onward | Dreamlike, irrational | Unexpected juxtapositions, symbolic |
| `cubism` | Early 20th century | Geometric forms, multiple perspectives | Fragmented, multiple viewpoints |
| `expressionism` | Early 20th century | Emotional intensity, distorted forms | Bold colors, distortion |
| `abstract expressionism` | 1940s-1950s | Spontaneous, non-representational | Gestural brushwork, large scale |
| `romanticism` | Late 18th-19th century | Emotion, nature, drama | Emotional intensity, dramatic lighting |
| `realism` | Mid-19th century | Accurate depiction of everyday life | Everyday subjects, social themes |

### Artistic Techniques

| Technique | Description | Use Cases |
|---|---|---|
| `stippling` | Using dots to create images | Detailed drawings, texture |
| `cross-hatching` | Overlapping parallel lines for shading | Pen drawings, engraving effect |
| `blending` | Smooth transitions between colors | Soft gradients, realistic shading |
| `glazing` | Transparent layers of paint | Depth in paintings, luminous effects |
| `impasto` | Thick, textured paint application | Textured paintings, 3D effects |
| `pointillism` | Small dots of pure color | Optical color mixing |

### Style Combination Suggestions

| Combination | Components | Example Prompt |
|---|---|---|
| Classic Fine Art | oil painting + renaissance + realistic | "oil painting in the style of renaissance, realistic portrait" |
| Modern Digital | digital art + minimalist + vector art | "minimalist digital art, vector style" |
| Vintage Illustration | watercolor + art nouveau + botanical | "art nouveau watercolor illustration of flowers" |
| Contemporary Abstract | acrylic + abstract expressionism + bold colors | "abstract expressionism acrylic painting with bold colors" |

---

## Quality Modifiers

### General Quality Terms

Use 1-3 general modifiers. Avoid overloading.

`high-quality` · `high quality` · `beautiful` · `stunning` · `gorgeous` · `elegant` · `stylized` · `detailed` · `highly detailed` · `intricate` · `intricate details` · `professional` · `premium` · `award-winning` · `masterful` · `exceptional`

### Photography-Specific Quality

| Modifier | Description | Use Cases |
|---|---|---|
| `4K` / `8K` | Ultra high resolution | Modern photography, digital displays |
| `HDR` / `4K HDR` | High dynamic range | Landscapes, dramatic scenes |
| `studio photo` | Professional studio quality | Products, portraits |
| `professional photograph` | Expert photography | Commercial, portfolio |
| `taken by a professional photographer` | Expert technique implied | Highest quality photography |
| `commercial photography` / `editorial photography` | Publication quality | Advertising, magazines |
| `magazine quality` | High-end publication standard | Fashion, lifestyle |
| `sharp focus` / `crystal clear` | Exceptional clarity | Detailed subjects, technical |
| `breathtaking` | Awe-inspiring | Spectacular scenes |

### Art-Specific Quality

| Modifier | Description |
|---|---|
| `by a professional` | Professional artist quality |
| `professional artwork` | Professional-level artistic quality |
| `masterpiece` | Exceptional, outstanding quality |
| `museum quality` / `gallery worthy` | Exhibition standard |
| `highly detailed artwork` | Exceptionally detailed |
| `intricate details` | Complex, detailed elements |
| `fine art` | Artistic merit |

### Context-Specific Modifiers

| Context | Modifiers |
|---|---|
| **Food** | "professional food photography", "in the style of a food magazine", "appetizing", "mouth-watering" |
| **Architecture** | "architectural photography", "architectural digest style", "grand", "epic" |
| **Product** | "product photography", "commercial product shot", "e-commerce ready" |
| **Portrait** | "professional portrait", "studio portrait", "editorial portrait" |
| **Fashion** | "fashion photography", "high fashion", "vogue style" |
| **Landscape** | "landscape photography", "national geographic style", "breathtaking", "majestic" |

### Quality Combination Strategies

| Strategy | Photography | Art |
|---|---|---|
| **Maximum** | "4K HDR", "taken by a professional photographer", "stunning", "sharp focus" | "masterpiece", "by a professional", "highly detailed", "intricate details" |
| **Balanced** | "high-quality", "professional photograph" | "professional artwork", "detailed" |
| **Minimal** | "professional" | "detailed" |

**Placement Tips:**
- Resolution specs work well at the beginning: "4K HDR"
- General descriptors fit naturally mid-prompt: "beautiful", "stunning"
- Professional qualifiers work at the end: "by a professional photographer"

---

## Material & Shape Modifiers

### Materials

#### Natural Materials

| Material | Textures | Use Cases | Example |
|---|---|---|---|
| `wood` / `wooden` | rough, smooth, polished, weathered | Furniture, crafts, natural aesthetics | — |
| `stone` | rough, smooth, polished, carved | Sculpture, architecture | — |
| `marble` | polished, smooth, veined | Luxury items, sculpture | — |
| `paper` | smooth, textured, folded, creased | Origami, crafts, minimalist | "armchair made of paper, origami style" |
| `fabric` / `cloth` | soft, woven, smooth, textured | Soft goods, clothing, draping | — |

#### Synthetic Materials

| Material | Textures | Use Cases |
|---|---|---|
| `plastic` | glossy, matte, smooth, textured | Modern products, toys |
| `glass` | transparent, translucent, frosted, clear | Elegant objects, modern design |
| `metal` | polished, brushed, rough, rusty, shiny | Industrial design, reflective surfaces |
| `ceramic` | glazed, matte, smooth, textured | Pottery, decorative objects |

#### Organic/Food Materials

| Material | Textures | Use Cases | Example |
|---|---|---|---|
| `cheese` | soft, aged, melted, solid | Surreal imagery, creative concepts | "duffle bag made of cheese" |
| `ice` | frozen, clear, frosted, crystalline | Cold themes, winter imagery | — |
| `crystal` | faceted, clear, colored, reflective | Magical themes, luxury items | — |

#### Special Materials

| Material | Description | Use Cases | Example |
|---|---|---|---|
| `neon tubes` | Glowing neon tubing | Signage, modern art, glowing effects | "neon tubes in the shape of a bird" |
| `wire` / `wireframe` | Wire structure | Technical designs, minimalist art | — |
| `concrete` | Industrial concrete | Industrial design, brutalist aesthetics | — |

### Textures

`rough` · `smooth` · `glossy` · `matte` · `shiny` · `brushed` · `polished` · `textured` · `soft` · `hard`

### Material Styles

| Style | Description | Best With |
|---|---|---|
| `origami style` | Paper folding aesthetic | paper, geometric forms |
| `wireframe` | Structural outline visible | wire, metal, technical subjects |
| `transparent` | See-through | glass, crystal, modern designs |
| `translucent` | Partially see-through | glass, fabric, special materials |
| `opaque` | Not see-through | most materials |
| `reflective` | Mirror-like surface | metal, glass, polished surfaces |

### Usage Patterns

- **Made of**: `"[subject] made of [material]"` — "a duffle bag made of cheese"
- **In shape of**: `"[material] in the shape of [object]"` — "neon tubes in the shape of a bird"
- **With texture**: `"[subject] with [texture] [material]"` — "chair with polished wood"

### Creative Applications

- **Logo Recreation**: Recreate logos in various materials — "company logo made of neon tubes"
- **Impossible Objects**: Objects from unexpected materials — "a laptop made of glass"
- **Material Studies**: Same object in different materials — "an armchair: wood, metal, paper variations"

---

## Photorealism Specialization

### Portrait Photography

- **Lens**: Prime or zoom, 24-35mm, 50mm, 85mm
- **Key Modifiers**: portrait, black and white film, film noir, depth of field, duotone (mention two colors), portrait mode, bokeh
- **Quality**: professional portrait, studio portrait, editorial portrait, magazine quality
- **Tips**: Specify facial details as focus. Use "portrait" in prompt. Consider duotones for artistic effect.

**Example prompts:**
- "A woman, 35mm portrait, blue and grey duotones"
- "A woman, 35mm portrait, film noir"
- "close-up photo of a woman in her 20s, street photography, movie still, muted orange warm tones"

### Objects & Still Life (Food, Insects, Plants)

- **Lens**: Macro, 60-105mm
- **Key Modifiers**: high detail, precise focusing, controlled lighting, studio lighting, macro lens, shallow depth of field
- **Quality**: professional food photography, in the style of a food magazine, studio photography, commercial quality

**Example prompts:**
- "leaf of a prayer plant, macro lens, 60mm"
- "a plate of pasta, 100mm Macro lens"
- "A professional studio photo of french fries for a high end restaurant, in the style of a food magazine" (4:3)

### Motion & Action (Sports, Wildlife)

- **Lens**: Telephoto zoom, 100-400mm
- **Key Modifiers**: fast shutter speed, action tracking, movement tracking, freeze motion, dynamic composition
- **Quality**: professional sports photography, wildlife photography, action photography

**Example prompts:**
- "a winning touchdown, fast shutter speed, movement tracking"
- "A deer running in the forest, fast shutter speed, movement tracking"

### Wide-Angle & Landscape

- **Lens**: Wide-angle, 10-24mm
- **Key Modifiers**: long exposure, sharp focus, smooth water, smooth clouds, deep focus, wide angle
- **Quality**: landscape photography, national geographic style, breathtaking, majestic, epic landscape

**Example prompts:**
- "an expansive mountain range, landscape wide angle 10mm"
- "a photo of the moon, astro photography, wide angle 10mm"

### Photorealism Construction Formula

```
[Subject] + [lens type and focal length] + [lighting/camera settings] + [quality modifiers]
```

---

## Aspect Ratio Guide

### Quick Reference

| Ratio | Name | Orientation | Best For | Platforms |
|---|---|---|---|---|
| **1:1** | Square | Square | Social media posts, products, logos, avatars | Instagram, Facebook, Twitter/X, LinkedIn |
| **4:3** | Fullscreen | Landscape | Photography, food, group portraits | Traditional media, editorial |
| **3:4** | Portrait | Portrait | Individual portraits, fashion, tall objects | Print (8x10), magazine covers |
| **16:9** | Widescreen | Landscape | Landscapes, cinematic, desktop wallpapers | YouTube, website banners |
| **9:16** | Vertical | Portrait | Mobile content, skyscrapers, waterfalls | TikTok, Instagram Stories/Reels, YouTube Shorts |

### Selection by Use Case

| Use Case | Recommended Ratio |
|---|---|
| Instagram Feed / Facebook Post | 1:1 |
| Instagram Stories / Reels / TikTok | 9:16 |
| YouTube Thumbnail | 16:9 |
| Portrait (headshot) | 3:4 |
| Portrait (full body) | 3:4 or 9:16 |
| Landscape | 16:9 or 4:3 |
| Product photo | 1:1 or 4:3 |
| Food photography | 4:3 or 1:1 |
| Architecture (wide) | 16:9 |
| Architecture (tall) | 9:16 or 3:4 |
| Desktop Wallpaper | 16:9 |
| Mobile Wallpaper | 9:16 |

### Selection by Subject

| Subject | Recommended |
|---|---|
| Headshot | 3:4 |
| Group of people | 4:3 or 16:9 |
| Single product | 1:1 or 3:4 |
| Mountains / beach / scenic | 16:9 |
| Waterfall | 3:4 or 9:16 |
| Skyline | 16:9 |
| Skyscraper | 9:16 or 3:4 |

### Decision Tree

1. **Is it for social media?**
   - Instagram Feed / Facebook → **1:1**
   - Stories / Reels / TikTok → **9:16**
   - YouTube → **16:9**
2. **What's the subject orientation?**
   - Tall / Vertical → **3:4** or **9:16**
   - Wide / Horizontal → **16:9** or **4:3**
   - Balanced / Square → **1:1**

### Technical Comparison

| Ratio | Width:Height | Common Resolutions |
|---|---|---|
| 9:16 | 0.5625 (very tall) | 1080×1920, 2160×3840 |
| 3:4 | 0.75 (moderately tall) | 768×1024, 1536×2048 |
| 1:1 | 1.0 (square) | 1024×1024, 2048×2048 |
| 4:3 | 1.333 (moderately wide) | 1024×768, 2048×1536 |
| 16:9 | 1.777 (very wide) | 1920×1080, 3840×2160 |

---

## Prompt Templates

### Portrait Photography

- **Template**: `"A portrait of {subject}, {focal_length}, {lighting}, {film_type}, {quality}"`
- **Config**: 3:4 aspect ratio
- **Examples**:
  - "A portrait of a woman in her 20s, 35mm, natural lighting, portrait mode"
  - "A portrait of an elderly man, 35mm, dramatic lighting, black and white film"

### Product Photography

- **Template**: `"A professional studio photo of {product} on {background}, {lighting}, {settings}, {quality}"`
- **Config**: 1:1 aspect ratio
- **Backgrounds**: white background, clean background, wooden surface, solid color background
- **Examples**:
  - "A professional studio photo of a smartwatch on a clean background, studio lighting, shallow depth of field"
  - "A professional studio photo of french fries on a wooden surface, 4K, studio photo"

### Logo Design

- **Template**: `"A {style} logo for a {industry} company on a solid color background, with the text '{name}', {quality}"`
- **Config**: 1:1 aspect ratio
- **Styles**: minimalist, modern, traditional, vintage, geometric, abstract
- **Examples**:
  - "A minimalist logo for a health care company on a solid color background. Include the text Journey."
  - "A modern logo for a software company on a solid color background. Include the text Silo."

### Landscape Photography

- **Template**: `"{scene_description}, wide angle {focal_length}, {lighting}, {settings}, {quality}"`
- **Config**: 16:9 aspect ratio
- **Examples**:
  - "A park in the spring next to a lake, the sun sets across the lake, golden hour, wide angle, stunning"
  - "An expansive mountain range, landscape wide angle 10mm, 4K HDR, breathtaking"

### Food Photography

- **Template**: `"A professional photo of {dish} for a {restaurant_type} restaurant, {lens}, {lighting}, {quality}"`
- **Config**: 4:3 aspect ratio
- **Examples**:
  - "A professional studio photo of french fries for a high end restaurant, in the style of a food magazine"
  - "A plate of pasta, 100mm Macro lens, professional food photography"

### Artistic Illustration

- **Template**: `"A {medium} of {subject} in the style of {art_style}, {quality}"`
- **Config**: 1:1 aspect ratio
- **Mediums**: watercolor, oil painting, digital art, pencil drawing, charcoal drawing, pastel painting
- **Styles**: impressionism, art deco, pop art, minimalist, modern, abstract
- **Examples**:
  - "A watercolor of a garden in the style of impressionism, professional artwork, beautiful"
  - "A digital art of a city skyline in the style of art deco, detailed"

### Social Media Post

- **Template**: `"{subject} for social media, {lighting}, {quality}"`
- **Config**: 1:1 aspect ratio
- **Examples**:
  - "A coffee cup on a desk with laptop for social media, natural lighting, vibrant, eye-catching"

### Concept Art

- **Template**: `"Concept art of {concept}, digital art, {quality}"`
- **Config**: 16:9 aspect ratio
- **Examples**:
  - "Concept art of a futuristic city, digital art, highly detailed, intricate details"

### Poster Design

- **Template**: `"A poster with the text \"{title}\" in bold font as a title, underneath this text is the slogan \"{slogan}\", {quality}"`
- **Config**: 3:4 aspect ratio
- **Examples**:
  - "A poster with the text \"Summerland\" in bold font as a title, underneath this text is the slogan \"Summer never felt so good\""

### Architectural Rendering

- **Template**: `"A {render_type} of {building}, {lighting}, {quality}"`
- **Config**: 9:16 aspect ratio
- **Render types**: digital render, architectural rendering, 3D visualization, photo
- **Examples**:
  - "A digital render of a massive skyscraper, modern, grand, epic with a beautiful sunset"

---

## Best Practices

### DO ✅

- **Start with a clear subject** — Be specific about what you want
- **Use appropriate technical terms** — Lens types, lighting, etc.
- **Include 2-3 quality modifiers** — Enhance without overwhelming
- **Match aspect ratio to use case** — Consider final platform
- **Iterate and refine** — Start simple, add details
- **Keep text short** — 25 characters or less per phrase
- **Specify style/medium** — Always include
- **Add context** — Background and setting matter

### DON'T ❌

- **Exceed 480 tokens** — Stay within limits
- **Be vague** — Specificity produces better results
- **Mix incompatible modifiers** — e.g., "aerial from below"
- **Overload with quality terms** — 2-3 is optimal
- **Forget style/medium** — Always specify
- **Use only subject** — Add context and modifiers

### Token Management

```
✅ Good — "A professional portrait, 35mm, natural lighting, high quality"
❌ Too long — "A very professional high-quality premium award-winning masterpiece portrait..."
```

### Text in Images

- Maximum 25 characters per phrase
- Maximum 3 phrases total
- Specify font style and size
- Guide placement
- Example: `with the text "Summerland" in bold font, large size, centered`

### Modifier Layering Strategy

- **Base**: Subject + context
- **Layer 1**: Technical specs (lens, lighting)
- **Layer 2**: Artistic touches (style, mood)
- **Layer 3**: Quality enhancement

### Use Case Optimization

| Use Case | Key Focus |
|---|---|
| **E-commerce** | Clean backgrounds, studio lighting, multiple angles |
| **Social Media** | Eye-catching, vibrant, platform-specific ratios |
| **Marketing** | Professional quality, brand-aligned, text integration |
| **Art** | Creative freedom, historical references, unique materials |

### Troubleshooting

| Problem | Solution |
|---|---|
| Prompt too long | Remove redundant modifiers; simplify context; use 2-3 quality terms max |
| Not photorealistic enough | Add specific lens types (35mm, 50mm); include technical terms; reference photorealism guide |
| Images not matching style | Be more specific with style/medium; add historical references; include technique descriptions |
| Text not appearing correctly | Shorten text (≤25 chars); specify font style clearly; limit to 2-3 phrases |

---

## Usage Examples

### Example 1: Basic Usage

```
Prompt: "a modern electric car, in an urban setting with skyscrapers, golden hour, 35mm, 4K HDR, professional photograph, stunning"
Config: 16:9, gemini-3-pro-image-preview, 1K
```

### Example 2: Product Photography

```
Prompt: "a luxury watch, clean white background, studio lighting, shallow depth of field, 4K HDR, studio photo, professional product photography"
Config: 1:1, gemini-3-pro-image-preview, 2K
```

### Example 3: Film Portrait

```
Prompt: "a woman in her 20s, dramatic lighting, film noir, 35mm, professional portrait"
Config: 3:4, gemini-3-pro-image-preview
```

### Example 4: Logo with Text

```
Prompt: "A modern logo for a software company, on a solid color background, with the text "Silo" in bold font, centered, professional, clean, high-quality"
Config: 1:1, gemini-3-pro-image-preview
```

### Example 5: Artistic Illustration

```
Prompt: "a serene forest scene, impressionist, watercolor, masterpiece, by a professional, highly detailed"
Config: 1:1, gemini-3-pro-image-preview
```

### Example 6: Creative Materials

```
Prompt: "an armchair, studio lighting, made of paper, origami style, studio photo, beautiful"
Config: 1:1, gemini-3-pro-image-preview
```

### Example 7: Photorealistic Landscape

```
Prompt: "an expansive mountain range with a pristine lake, wide-angle, 10-24mm, golden hour, long exposure, 4K HDR, landscape photography, breathtaking, stunning"
Config: 16:9, gemini-3-pro-image-preview, 2K
```

### Example 8: Food Photography

```
Prompt: "a gourmet pasta dish, 100mm macro, controlled lighting, shallow depth of field, professional food photography, in the style of a food magazine"
Config: 4:3, gemini-3-pro-image-preview
```

### Example 9: Social Media Content

```
Prompt: "a minimalist workspace with laptop and coffee, from above, natural lighting, vibrant, eye-catching, beautiful"
Config: 1:1, gemini-3-pro-image-preview
```

### Example 10: Architectural Rendering

```
Prompt: "digital render, a futuristic skyscraper, with a dramatic sunset in the background, from below, dramatic lighting, modern, grand, epic, architectural photography"
Config: 9:16, gemini-3-pro-image-preview
```

### Example 11: Complex Scene

```
Prompt: "a woman hiking through a mountain trail, reflection of her boots in a puddle, majestic mountains in background, close-up, from below, golden hour, wide angle, professional photograph, dramatic composition, stunning, cinematic"
Config: 3:4, gemini-3-pro-image-preview
```

---

## TypeScript Source Code

### Type Definitions (`prompt-components.ts`)

```typescript
/**
 * Nano Banana Prompt Framework - Type Definitions
 */

// Core Prompt Structure
export interface PromptStructure {
  subject: string;
  context?: string;
  style?: string;
  modifiers?: PromptModifiers;
  textInImage?: TextInImage[];
  parameters?: PromptParameters;
}

export interface PromptParameters {
  parameterName: string;
  allowedValues?: string[];
  defaultValue?: string;
  description?: string;
}

export interface TextInImage {
  text: string;
  placement?: string;
  fontStyle?: string;
  fontSize?: 'small' | 'medium' | 'large' | string;
}

// Modifier Categories
export interface PromptModifiers {
  photography?: PhotographyModifiers;
  art?: ArtModifiers;
  quality?: QualityModifiers;
  material?: MaterialModifiers;
  photorealism?: PhotorealismModifiers;
  custom?: string[];
}

// Photography Modifiers
export interface PhotographyModifiers {
  cameraProximity?: CameraProximity;
  cameraPosition?: CameraPosition;
  lighting?: Lighting;
  cameraSettings?: CameraSettings;
  lensType?: LensType;
  filmType?: FilmType;
  focalLength?: string;
}

export type CameraProximity =
  | 'close-up' | 'close up' | 'extreme close-up' | 'medium shot'
  | 'full shot' | 'zoomed out' | 'taken from far away' | 'wide shot';

export type CameraPosition =
  | 'aerial' | 'aerial photo' | "bird's eye view" | 'from below'
  | 'from above' | 'eye-level' | 'low angle' | 'high angle'
  | 'dutch angle' | 'over the shoulder';

export type Lighting =
  | 'natural lighting' | 'natural' | 'dramatic lighting' | 'dramatic'
  | 'warm lighting' | 'warm' | 'cold lighting' | 'cold'
  | 'golden hour' | 'blue hour' | 'studio lighting' | 'soft lighting'
  | 'hard lighting' | 'backlit' | 'rim lighting' | 'natural light'
  | 'controlled lighting';

export type CameraSettings =
  | 'motion blur' | 'soft focus' | 'bokeh' | 'portrait mode' | 'portrait'
  | 'shallow depth of field' | 'deep focus' | 'tilt-shift'
  | 'long exposure' | 'fast shutter speed' | 'action tracking'
  | 'movement tracking';

export type LensType =
  | '35mm' | '50mm' | '24mm' | '85mm' | '100mm'
  | 'fisheye' | 'fisheye lens' | 'wide angle' | 'wide-angle'
  | 'macro' | 'macro lens' | 'telephoto' | 'telephoto zoom'
  | 'prime lens' | 'zoom lens' | '10-24mm' | '60-105mm' | '100-400mm';

export type FilmType =
  | 'black and white' | 'black and white film' | 'polaroid'
  | 'polaroid photo' | 'polaroid portrait' | 'film noir'
  | 'vintage film' | '35mm film' | 'instant film' | 'color film';

// Art & Illustration Modifiers
export interface ArtModifiers {
  medium?: ArtMedium;
  style?: ArtStyle;
  historicalReference?: HistoricalArtStyle;
  technique?: ArtTechnique;
}

export type ArtMedium =
  | 'painting' | 'sketch' | 'drawing' | 'illustration' | 'digital art'
  | 'pencil drawing' | 'technical pencil drawing' | 'charcoal drawing'
  | 'color pencil drawing' | 'pastel painting' | 'watercolor'
  | 'oil painting' | 'acrylic painting' | '3D render' | 'digital render';

export type ArtStyle =
  | 'realistic' | 'photorealistic' | 'abstract' | 'minimalist' | 'modern'
  | 'traditional' | 'contemporary' | 'stylized' | 'cartoon' | 'anime'
  | 'comic book' | 'graphic novel' | 'vector art' | 'low poly'
  | 'isometric' | 'isometric 3D';

export type HistoricalArtStyle =
  | 'impressionism' | 'impressionist painting' | 'renaissance'
  | 'renaissance painting' | 'baroque' | 'art nouveau' | 'art deco'
  | 'pop art' | 'surrealism' | 'cubism' | 'expressionism'
  | 'abstract expressionism' | 'romanticism' | 'realism';

export type ArtTechnique =
  | 'stippling' | 'cross-hatching' | 'blending' | 'glazing'
  | 'impasto' | 'sgraffito' | 'pointillism' | 'collage' | 'mixed media';

// Quality Modifiers
export interface QualityModifiers {
  general?: GeneralQuality[];
  photoSpecific?: PhotoQuality[];
  artSpecific?: ArtQuality[];
}

export type GeneralQuality =
  | 'high-quality' | 'high quality' | 'beautiful' | 'stunning'
  | 'gorgeous' | 'elegant' | 'stylized' | 'detailed' | 'highly detailed'
  | 'intricate' | 'professional' | 'premium' | 'award-winning';

export type PhotoQuality =
  | '4K' | '8K' | 'HDR' | '4K HDR' | 'studio photo'
  | 'professional photograph' | 'professional photography'
  | 'professional product photography' | 'landscape photography'
  | 'taken by a professional photographer' | 'commercial photography'
  | 'editorial photography' | 'magazine quality' | 'sharp focus'
  | 'crystal clear' | 'breathtaking';

export type ArtQuality =
  | 'by a professional' | 'professional artwork' | 'masterpiece'
  | 'museum quality' | 'gallery worthy' | 'highly detailed artwork'
  | 'highly detailed' | 'detailed' | 'intricate details' | 'fine art';

// Material & Shape Modifiers
export interface MaterialModifiers {
  material?: Material;
  texture?: Texture;
  shape?: string;
  style?: MaterialStyle;
}

export type Material =
  | 'glass' | 'metal' | 'wood' | 'wooden' | 'paper' | 'fabric' | 'cloth'
  | 'plastic' | 'ceramic' | 'stone' | 'marble' | 'concrete'
  | 'cheese' | 'ice' | 'crystal' | 'neon tubes' | 'wire' | 'origami';

export type Texture =
  | 'rough' | 'smooth' | 'glossy' | 'matte' | 'shiny'
  | 'brushed' | 'polished' | 'textured' | 'soft' | 'hard';

export type MaterialStyle =
  | 'origami style' | 'wireframe' | 'transparent'
  | 'translucent' | 'opaque' | 'reflective';

// Photorealism
export interface PhotorealismModifiers {
  useCase?: PhotorealismUseCase;
  lensType?: PhotorealismLensType;
  focalLength?: string;
  additionalDetails?: string[];
}

export type PhotorealismUseCase =
  | 'portrait' | 'people' | 'object' | 'still-life' | 'food'
  | 'insects' | 'plants' | 'motion' | 'sports' | 'wildlife'
  | 'wide-angle' | 'landscape' | 'astronomical';

export type PhotorealismLensType =
  | 'prime' | 'zoom' | 'macro' | 'telephoto zoom' | 'wide-angle';

// Nano Banana Configuration
export interface NanoBananaConfig {
  model: NanoBananaModel;
  numberOfImages?: number;
  aspectRatio?: AspectRatio;
  imageSize?: ImageSize;
  personGeneration?: PersonGeneration;
}

export type NanoBananaModel =
  | 'gemini-3-pro-image-preview' | 'gemini-3.1-flash-image-preview'
  | 'gemini-2.5-flash-image';

export type AspectRatio = '1:1' | '3:4' | '4:3' | '9:16' | '16:9' | '2:3' | '3:2' | '4:5' | '5:4' | '21:9';
export type ImageSize = '512' | '1K' | '2K' | '4K';
export type PersonGeneration = 'dont_allow' | 'allow_adult' | 'allow_all';

// Aspect Ratio Guidance
export interface AspectRatioGuide {
  ratio: AspectRatio;
  name: string;
  description: string;
  useCases: string[];
  bestFor: string[];
}

// Prompt Template
export interface PromptTemplate {
  name: string;
  category: TemplateCategory;
  description: string;
  basePrompt: string;
  parameters?: PromptParameters[];
  suggestedModifiers?: PromptModifiers;
  suggestedConfig?: Partial<NanoBananaConfig>;
  examples?: string[];
}

export type TemplateCategory =
  | 'portrait' | 'product' | 'landscape' | 'logo' | 'artistic'
  | 'photorealistic' | 'marketing' | 'social-media' | 'concept-art'
  | 'brand-asset';

// Validation
export interface ValidationResult {
  valid: boolean;
  errors?: ValidationError[];
  warnings?: ValidationWarning[];
  suggestions?: string[];
}

export interface ValidationError {
  code: string;
  message: string;
  field?: string;
}

export interface ValidationWarning {
  code: string;
  message: string;
  suggestion?: string;
}

// Generated Prompt Output
export interface GeneratedPrompt {
  prompt: string;
  config: NanoBananaConfig;
  tokenCount: number;
  metadata: PromptMetadata;
}

export interface PromptMetadata {
  category?: TemplateCategory;
  modifiersUsed: string[];
  hasTextInImage: boolean;
  textCharacterCount?: number;
  complexity: 'simple' | 'moderate' | 'complex';
  generatedAt: string;
}
```

### Main Prompt Builder (`nano-banana-prompt-framework.ts`)

```typescript
/**
 * Nano Banana Prompt Framework - Main Prompt Builder
 */

import type {
  PromptStructure, NanoBananaConfig, GeneratedPrompt, AspectRatio,
  NanoBananaModel, PhotographyModifiers, ArtModifiers, QualityModifiers,
  MaterialModifiers, LensType, PhotoQuality, Lighting, FilmType,
  ArtStyle, ArtMedium
} from './prompt-components';

export class NanoBananaPromptBuilder {
  private structure: PromptStructure;
  private config: NanoBananaConfig;

  constructor(config?: Partial<NanoBananaConfig>) {
    this.structure = { subject: '', modifiers: {} };
    this.config = {
      model: config?.model || 'gemini-3-pro-image-preview',
      numberOfImages: config?.numberOfImages || 4,
      aspectRatio: config?.aspectRatio || '1:1',
      imageSize: config?.imageSize || '1K',
      personGeneration: config?.personGeneration || 'allow_adult'
    };
  }

  subject(subject: string): this { this.structure.subject = subject; return this; }
  context(context: string): this { this.structure.context = context; return this; }
  style(style: string): this { this.structure.style = style; return this; }

  photography(modifiers: PhotographyModifiers): this {
    if (!this.structure.modifiers) this.structure.modifiers = {};
    this.structure.modifiers.photography = modifiers;
    return this;
  }

  art(modifiers: ArtModifiers): this {
    if (!this.structure.modifiers) this.structure.modifiers = {};
    this.structure.modifiers.art = modifiers;
    return this;
  }

  quality(modifiers: QualityModifiers): this {
    if (!this.structure.modifiers) this.structure.modifiers = {};
    this.structure.modifiers.quality = modifiers;
    return this;
  }

  material(modifiers: MaterialModifiers): this {
    if (!this.structure.modifiers) this.structure.modifiers = {};
    this.structure.modifiers.material = modifiers;
    return this;
  }

  photorealistic(type: 'portrait' | 'objects' | 'motion' | 'wideAngle'): this {
    // Apply photorealism presets based on type
    return this;
  }

  addText(text: string, options?: {
    placement?: string; fontStyle?: string;
    fontSize?: 'small' | 'medium' | 'large' | string;
  }): this {
    if (!this.structure.textInImage) this.structure.textInImage = [];
    this.structure.textInImage.push({ text, ...options });
    return this;
  }

  aspectRatio(ratio: AspectRatio): this { this.config.aspectRatio = ratio; return this; }
  model(model: NanoBananaModel): this { this.config.model = model; return this; }
  numberOfImages(count: number): this { this.config.numberOfImages = Math.min(4, Math.max(1, count)); return this; }
  imageSize(size: '512' | '1K' | '2K' | '4K'): this { this.config.imageSize = size; return this; }
  personGeneration(setting: 'dont_allow' | 'allow_adult' | 'allow_all'): this { this.config.personGeneration = setting; return this; }

  private buildPromptString(): string {
    const parts: string[] = [];
    if (this.structure.style) parts.push(this.structure.style);
    if (this.structure.subject) parts.push(this.structure.subject);
    if (this.structure.context) parts.push(this.structure.context);

    if (this.structure.modifiers?.photography) {
      const p = this.structure.modifiers.photography;
      if (p.cameraProximity) parts.push(p.cameraProximity);
      if (p.cameraPosition) parts.push(p.cameraPosition);
      if (p.lighting) parts.push(p.lighting);
      if (p.cameraSettings) {
        Array.isArray(p.cameraSettings) ? parts.push(...p.cameraSettings) : parts.push(p.cameraSettings);
      }
      if (p.lensType) parts.push(p.lensType);
      if (p.focalLength) parts.push(p.focalLength);
      if (p.filmType) parts.push(p.filmType);
    }

    if (this.structure.modifiers?.art) {
      const a = this.structure.modifiers.art;
      if (a.medium) parts.push(a.medium);
      if (a.historicalReference) parts.push(`in the style of ${a.historicalReference}`);
      if (a.technique) parts.push(a.technique);
    }

    if (this.structure.modifiers?.material) {
      const m = this.structure.modifiers.material;
      if (m.material) parts.push(`made of ${m.material}`);
      if (m.texture) parts.push(m.texture);
      if (m.shape) parts.push(`in the shape of ${m.shape}`);
      if (m.style) parts.push(m.style);
    }

    if (this.structure.modifiers?.quality) {
      const q = this.structure.modifiers.quality;
      if (q.general) parts.push(...q.general);
      if (q.photoSpecific) parts.push(...q.photoSpecific);
      if (q.artSpecific) parts.push(...q.artSpecific);
    }

    if (this.structure.textInImage?.length) {
      this.structure.textInImage.forEach(t => {
        let textPart = `with the text "${t.text}"`;
        if (t.fontStyle) textPart += ` in ${t.fontStyle} font`;
        if (t.fontSize) textPart += `, ${t.fontSize} size`;
        if (t.placement) textPart += `, ${t.placement}`;
        parts.push(textPart);
      });
    }

    return parts.join(', ');
  }

  build(): GeneratedPrompt {
    const prompt = this.buildPromptString();
    const tokenCount = Math.ceil(prompt.length / 4);

    if (!this.structure.subject) throw new Error('Subject is required');
    if (tokenCount > 480) throw new Error(`Prompt exceeds 480 token limit (estimated ${tokenCount} tokens)`);

    return {
      prompt,
      config: this.config,
      tokenCount,
      metadata: {
        modifiersUsed: Object.keys(this.structure.modifiers || {}),
        hasTextInImage: !!this.structure.textInImage?.length,
        textCharacterCount: this.structure.textInImage?.reduce((s, t) => s + t.text.length, 0),
        complexity: tokenCount > 300 ? 'complex' : tokenCount > 150 ? 'moderate' : 'simple',
        generatedAt: new Date().toISOString()
      }
    };
  }

  toString(): string { return this.buildPromptString(); }
}

// Quick builders for common use cases
export const QuickBuild = {
  portrait(subject: string, options?: { lighting?: Lighting; filmType?: FilmType; quality?: 'standard' | 'high' | 'premium' }) {
    const b = new NanoBananaPromptBuilder();
    b.subject(subject).photography({ lensType: '35mm', lighting: options?.lighting || 'natural lighting' });
    if (options?.filmType) b.photography({ filmType: options.filmType });
    if (options?.quality === 'premium') b.quality({ photoSpecific: ['4K HDR', 'professional photograph'] });
    else if (options?.quality === 'high') b.quality({ photoSpecific: ['professional photograph'] });
    return b;
  },

  product(subject: string, options?: { background?: string; quality?: 'standard' | 'high' | 'premium' }) {
    const b = new NanoBananaPromptBuilder();
    b.subject(subject).photography({ lighting: 'studio lighting', cameraSettings: 'shallow depth of field' }).context(options?.background || 'clean background');
    if (options?.quality === 'premium') b.quality({ photoSpecific: ['4K HDR', 'studio photo', 'professional product photography'] });
    else if (options?.quality === 'high') b.quality({ photoSpecific: ['studio photo', 'professional product photography'] });
    return b;
  },

  illustration(subject: string, style: ArtStyle, options?: { medium?: ArtMedium; quality?: 'standard' | 'high' | 'premium' }) {
    const b = new NanoBananaPromptBuilder();
    b.subject(subject).art({ style, medium: options?.medium });
    if (options?.quality === 'premium') b.quality({ artSpecific: ['masterpiece', 'by a professional', 'highly detailed'] });
    else if (options?.quality === 'high') b.quality({ artSpecific: ['professional artwork', 'detailed'] });
    return b;
  },

  landscape(subject: string, options?: { lighting?: Lighting; quality?: 'standard' | 'high' | 'premium' }) {
    const b = new NanoBananaPromptBuilder();
    b.subject(subject).photography({ lensType: 'wide angle', focalLength: '10-24mm', lighting: options?.lighting || 'golden hour' }).aspectRatio('16:9');
    if (options?.quality === 'premium') b.quality({ photoSpecific: ['4K HDR', 'landscape photography', 'breathtaking'], general: ['stunning'] });
    else if (options?.quality === 'high') b.quality({ photoSpecific: ['landscape photography'], general: ['beautiful'] });
    return b;
  }
};
```

---

## Common Prompt Patterns (Quick Reference)

### Pattern Templates

| Type | Pattern |
|---|---|
| **Portrait** | `"A [style] portrait of [subject], [focal length], [lighting], [film type], [quality]"` |
| **Product** | `"A professional studio photo of [product] on [background], studio lighting, shallow depth of field, [quality]"` |
| **Landscape** | `"[Scene description], wide angle [focal length], [lighting], [camera settings], [quality]"` |
| **Logo** | `"A [style] logo for a [industry] company on a solid color background, with the text '[name]', [quality]"` |
| **Art** | `"A [medium] of [subject] in the style of [art style], [quality]"` |
| **Food** | `"A professional photo of [dish], macro lens [focal length], [lighting], in the style of a food magazine"` |
| **Architecture** | `"A digital render of [building], [camera position], [lighting], modern, grand, epic"` |
| **Social Media** | `"[Subject] for social media, [camera angle], [lighting], vibrant, eye-catching, [aspect ratio]"` |

---
