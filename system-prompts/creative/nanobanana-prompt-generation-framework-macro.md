# Nano Banana Prompt Generation Framework (Antigravity)

> A comprehensive framework for generating superior image prompts for Google Nano Banana
> 

---

## Table of Contents

1. [Overview](about:blank#overview)
2. [Core Concepts](about:blank#core-concepts)
3. [Prompt Structure](about:blank#prompt-structure)
4. [Configuration Options](about:blank#configuration-options)
5. [Photography Modifiers](about:blank#photography-modifiers)
6. [Art Style Modifiers](about:blank#art-style-modifiers)
7. [Quality Modifiers](about:blank#quality-modifiers)
8. [Material & Shape Modifiers](about:blank#material--shape-modifiers)
9. [Photorealism Specialization](about:blank#photorealism-specialization)
10. [Usage Examples](about:blank#usage-examples)
11. [Best Practices](about:blank#best-practices)
12. [Quick Reference](about:blank#quick-reference)

---

## Overview

The Nano Banana Prompt Framework provides a systematic approach to generating high-quality prompts for Google’s Nano Banana image generation models. It includes:

- **500+ Categorized Modifiers** for photography, art, quality, and materials
- **TypeScript Framework** with a strongly-typed, fluent API
- **Template System** with pre-built templates for common use cases
- **Validation & Optimization** with built-in token counting
- **Integration Ready** for Custom GPTs, Claude Projects, and APIs
- **Photorealism Specialization** with detailed guides

---

## Core Concepts

### What Makes a Great Nano Banana Prompt?

Every effective Nano Banana prompt follows this structure:

```
[Style/Medium] + [Subject] + [Context] + [Modifiers] + [Quality Enhancers]
```

**Example:**

```
A professional studio photo (style) of a luxury watch (subject) on a clean background (context), studio lighting, shallow depth of field (modifiers), 4K HDR, professional product photography (quality)
```

### Key Principles

1. **Be Specific**: Clear, detailed descriptions produce better results
2. **Use Technical Terms**: Photography and art terminology enhances quality
3. **Layer Modifiers**: Combine 2-3 categories for best results
4. **Stay Within Limits**: Maximum 480 tokens per prompt
5. **Match Context**: Choose modifiers appropriate to your subject

---

## Prompt Structure

### Required Elements

**Subject** (Required)
- The main focus of your image
- Be specific and descriptive
- Example: “a luxury sports car” not just “a car”

**Context** (Recommended)
- Background or environment
- Setting and atmosphere
- Example: “in an urban setting at night”

**Style** (Recommended)
- Overall visual approach
- Medium or artistic style
- Example: “professional studio photo”, “watercolor painting”

### Optional Elements

**Modifiers**
- Photography settings (lighting, lens, camera position)
- Art techniques (medium, historical style, technique)
- Material specifications (texture, material, shape)

**Quality Enhancers**
- General quality terms
- Context-specific modifiers
- Professional indicators

**Text in Image**
- Up to 3 text phrases recommended
- 25 characters or less per phrase
- Specify placement and style

---

## Configuration Options

### Models

**Nano Banana-4.0-ultra-generate-001**
- Highest quality output
- Supports 1K and 2K image sizes
- Best for professional work

**Nano Banana-4.0-generate-001** (Standard)
- Balanced quality and speed
- Supports 1K and 2K image sizes
- Recommended for most use cases

**Nano Banana-4.0-fast-generate-001**
- Fastest generation
- 1K image size only
- Good for rapid iteration

**Nano Banana-3.0-generate-002**
- Previous generation
- 1K image size only
- Legacy support

### Aspect Ratios

**1:1 - Square**
- Use for: Social media posts, product photography, profile images
- Platforms: Instagram, Facebook, avatars

**4:3 - Fullscreen**
- Use for: Photography, food photography, general content
- Traditional photo format

**3:4 - Portrait**
- Use for: Vertical subjects, portraits, tall objects
- Vertical orientation

**16:9 - Widescreen**
- Use for: Landscapes, cinematic shots, YouTube thumbnails
- Horizontal emphasis

**9:16 - Vertical**
- Use for: Mobile content, TikTok, Instagram Stories
- Tall buildings, full-body portraits

### Image Sizes

**1K** (Default)
- Faster generation
- Available on all models
- Suitable for most use cases

**2K** (Premium)
- Higher quality output
- Only available on Ultra and Standard models
- Best for professional work

### Person Generation

**dont_allow**
- Blocks generation of people entirely
- Use for non-human subjects only

**allow_adult** (Default)
- Generates adults only, no children
- Recommended setting for most use cases

**allow_all**
- Generates adults and children
- Not available in EU, UK, Switzerland, MENA regions

---

## Photography Modifiers

### Camera Proximity

Distance of the camera from the subject:

**close-up** / **close up**
- Very near to the subject, showing detail
- Use for: Portraits, product details, texture emphasis
- Example: “close-up of a luxury watch face”

**extreme close-up**
- Extremely near, showing minute details
- Use for: Macro details, emotion capture, texture focus
- Example: “extreme close-up of water droplets on a leaf”

**medium shot**
- Balanced framing of the subject
- Use for: Portraits, product photography, general use
- Example: “medium shot of a business professional”

**full shot** / **wide shot**
- Shows the entire subject
- Use for: Full body portraits, architecture, products in context
- Example: “full shot of a modern building”

**zoomed out** / **taken from far away**
- Far from the subject, showing context
- Use for: Landscapes, environmental context, establishing shots
- Example: “zoomed out view of mountain range”

### Camera Position

Angle and position relative to the subject:

**aerial** / **aerial photo** / **bird’s eye view**
- Looking down from above
- Use for: Urban photography, landscapes, patterns, architecture
- Example: “aerial photo of urban city with skyscrapers”

**from below** / **low angle**
- Looking up from below the subject
- Use for: Dramatic portraits, architecture, trees, power dynamics
- Example: “photo of a forest canopy with blue skies from below”

**eye-level** / **straight on**
- Camera at the same height as the subject
- Use for: Natural portraits, product photography, street photography
- Example: “eye-level portrait of a woman”

**high angle**
- Camera above the subject, looking down
- Use for: Flatlay, food photography, vulnerable subject portrayal
- Example: “high angle view of a coffee cup on a desk”

**dutch angle** / **canted angle**
- Camera tilted on its axis
- Use for: Creative compositions, disorientation, artistic shots
- Example: “dutch angle shot of city street”

**over the shoulder** / **OTS**
- From behind one subject looking at another
- Use for: Storytelling, interaction shots, perspective
- Example: “over the shoulder view of person working”

### Lighting Conditions

**natural lighting** / **natural light**
- Lighting from natural sources
- Use for: Portraits, products, general photography
- Example: “studio photo of a modern arm chair, natural lighting”

**dramatic lighting**
- High contrast, theatrical lighting
- Use for: Portraits, mood shots, artistic photography
- Example: “portrait with dramatic lighting”

**warm lighting** / **warm**
- Orange/yellow color temperature
- Use for: Cozy atmospheres, sunset scenes, portraits
- Example: “interior scene with warm lighting”

**cold lighting** / **cool lighting**
- Blue color temperature
- Use for: Clinical settings, modern aesthetics, winter scenes
- Example: “modern office with cold lighting”

**golden hour**
- Warm, soft light shortly after sunrise or before sunset
- Use for: Landscapes, portraits, romantic scenes
- Example: “the sun sets across the lake, golden hour”

**blue hour**
- Cool, soft light just before sunrise or after sunset
- Use for: Cityscapes, architectural photography, moody scenes
- Example: “city skyline during blue hour”

**studio lighting** / **controlled lighting**
- Professional controlled lighting setup
- Use for: Product photography, professional portraits, commercial work
- Example: “product shot with studio lighting”

**soft lighting** / **diffused lighting**
- Even, gentle lighting with minimal shadows
- Use for: Flattering portraits, product photography, beauty shots
- Example: “beauty portrait with soft lighting”

**hard lighting**
- Direct lighting creating strong shadows
- Use for: Dramatic portraits, film noir, texture emphasis
- Example: “portrait with hard lighting and strong shadows”

**backlit** / **backlighting**
- Light source behind the subject
- Use for: Silhouettes, rim lighting, ethereal effects
- Example: “backlit portrait at sunset”

**rim lighting**
- Light outlining the subject’s edges
- Use for: Separation from background, dramatic portraits, product shots
- Example: “product with rim lighting on dark background”

### Camera Settings

**motion blur**
- Blur created by movement during exposure
- Use for: Dynamic scenes, speed indication, artistic effect
- Example: “photo of a city with skyscrapers from the inside of a car with motion blur”

**soft focus**
- Slightly out of focus, dreamy look
- Use for: Romantic scenes, ethereal portraits, artistic photography
- Example: “soft focus photograph of a bridge in an urban city at night”

**bokeh**
- Aesthetic blur in out-of-focus areas
- Use for: Portraits, isolation of subject, artistic backgrounds
- Example: “portrait with bokeh background”

**portrait mode** / **portrait**
- Shallow depth of field effect
- Use for: Portraits, subject isolation, professional look
- Example: “smartphone portrait mode of a person”

**shallow depth of field**
- Small area in focus, blurred background
- Use for: Portraits, product focus, macro photography
- Example: “product photo with shallow depth of field”

**deep focus**
- Everything in focus from foreground to background
- Use for: Landscapes, architecture, documentary photography
- Example: “landscape with deep focus”

**tilt-shift**
- Miniature effect or selective focus
- Use for: Creative cityscapes, miniature effect, artistic photography
- Example: “tilt-shift view of city making it look miniature”

**long exposure**
- Extended shutter time for motion blur or light trails
- Use for: Waterfalls, star trails, light painting, smooth water
- Example: “waterfall with long exposure creating smooth water”

**fast shutter speed**
- Freezes motion, captures detail in movement
- Use for: Sports, wildlife, action shots
- Example: “a winning touchdown, fast shutter speed”

**movement tracking** / **action tracking**
- Camera follows moving subject
- Use for: Sports photography, wildlife, dynamic scenes
- Example: “a deer running in the forest, fast shutter speed, movement tracking”

### Lens Types

**Wide-Angle Lenses (10-24mm)**

**wide angle** / **wide-angle**
- Focal Length: 10-24mm
- Use for: Landscapes, architecture, interiors, astronomical photography
- Example: “an expansive mountain range, landscape wide angle 10mm”

**fisheye** / **fisheye lens**
- Focal Length: 8-15mm
- Ultra-wide with characteristic distortion
- Use for: Creative photography, skateboarding, action sports
- Example: “street photography, new york city, fisheye lens”

**Standard Lenses (24-70mm)**

**35mm**
- Focal Length: 35mm
- Versatile, natural perspective
- Use for: Street photography, documentary, environmental portraits
- Example: “35mm portrait, blue and grey duotones”

**50mm**
- Focal Length: 50mm
- Classic standard lens, natural perspective
- Use for: Portraits, street photography, general use
- Example: “50mm portrait in natural lighting”

**Macro Lenses (60-105mm)**

**macro** / **macro lens**
- Focal Length: 60-105mm
- Extreme close-up capability for small subjects
- Use for: Insects, plants, food photography, product details
- Example: “photo of a leaf, macro lens”
- Additional Details: high detail, precise focusing, controlled lighting

**60mm macro**
- Focal Length: 60mm
- Standard macro focal length
- Use for: Food, products, flowers
- Example: “leaf of a prayer plant, macro lens, 60mm”

**100mm macro**
- Focal Length: 100mm
- Telephoto macro for working distance
- Use for: Insects, shy subjects, food
- Example: “a plate of pasta, 100mm Macro lens”

**Telephoto Lenses (85-400mm)**

**85mm**
- Focal Length: 85mm
- Portrait lens with flattering compression
- Use for: Portraits, headshots, fashion
- Example: “85mm portrait headshot”

**telephoto zoom**
- Focal Length: 100-400mm
- Variable focal length for distant subjects
- Use for: Wildlife, sports, bird photography
- Additional Details: fast shutter speed, action tracking, movement tracking
- Example: “wildlife photo with telephoto zoom lens”

### Film Types

**black and white** / **black and white film** / **B&W**
- Monochrome photography
- Use for: Classic portraits, artistic photography, documentary
- Example: “black and white photo of a dog wearing sunglasses”
- Additional Details: film noir, depth of field, high contrast

**polaroid** / **polaroid photo** / **instant film**
- Instant film with characteristic look
- Use for: Vintage aesthetic, casual portraits, nostalgic scenes
- Example: “a polaroid portrait of a dog wearing sunglasses”

**film noir**
- High contrast black and white with dramatic lighting
- Use for: Dramatic portraits, moody scenes, crime aesthetics
- Example: “A woman, 35mm portrait, film noir”

**vintage film** / **retro film** / **analog film**
- Old film stock aesthetic
- Use for: Nostalgic scenes, retro photography, artistic work
- Example: “vintage film photograph of a classic car”

**35mm film**
- Standard film format
- Use for: General photography, professional work, artistic photography
- Example: “35mm film portrait”

**color film**
- Traditional color photography
- Use for: Vibrant scenes, realistic colors, general photography
- Example: “color film photograph of a landscape”

---

## Art Style Modifiers

### Art Mediums

**painting**
- General painting medium
- Use for: Traditional art styles, classic looks

**sketch** / **drawing**
- Line-based artwork
- Use for: Conceptual work, studies, illustrations

**illustration**
- General illustration style
- Use for: Editorial, children’s books, graphic work

**digital art**
- Computer-generated artwork
- Use for: Modern illustrations, concept art

**pencil drawing** / **technical pencil drawing**
- Graphite-based artwork
- Use for: Detailed studies, realistic drawings

**charcoal drawing**
- Charcoal medium
- Use for: Dramatic, high-contrast artwork

**color pencil drawing**
- Colored pencil artwork
- Use for: Vibrant, detailed illustrations

**pastel painting**
- Soft pastel medium
- Use for: Soft, dreamy artwork

**watercolor**
- Watercolor painting
- Use for: Soft, flowing artwork, landscapes

**oil painting**
- Oil paint medium
- Use for: Rich, textured artwork, classical paintings

**acrylic painting**
- Acrylic paint medium
- Use for: Vibrant, modern artwork

**3D render** / **digital render**
- Computer-generated 3D imagery
- Use for: Product visualization, architectural renders

### Art Styles

**realistic** / **photorealistic**
- Lifelike representation
- Use for: Detailed, accurate depictions

**abstract**
- Non-representational art
- Use for: Conceptual, emotional artwork

**minimalist**
- Simple, clean design
- Use for: Modern, uncluttered compositions

**modern** / **contemporary**
- Current artistic trends
- Use for: Fresh, current aesthetics

**traditional**
- Classic artistic approaches
- Use for: Timeless, conventional styles

**stylized**
- Distinctive artistic interpretation
- Use for: Unique, characteristic looks

**cartoon**
- Simplified, exaggerated style
- Use for: Playful, accessible imagery

**anime**
- Japanese animation style
- Use for: Manga-inspired artwork

**comic book** / **graphic novel**
- Sequential art style
- Use for: Dynamic, narrative imagery

**vector art**
- Clean, scalable graphics
- Use for: Logos, icons, flat design

**low poly**
- Geometric, faceted style
- Use for: Modern, geometric artwork

**isometric** / **isometric 3D**
- Angled, technical perspective
- Use for: Game art, technical illustrations

### Historical Art Styles

**impressionism** / **impressionist painting**
- Loose brushwork, light emphasis
- Artists: Monet, Renoir, Degas
- Use for: Soft, atmospheric scenes

**renaissance** / **renaissance painting**
- Classical European art (14th-17th century)
- Artists: Leonardo da Vinci, Michelangelo, Raphael
- Use for: Classical, detailed compositions

**baroque**
- Dramatic, ornate style (17th-18th century)
- Artists: Caravaggio, Rembrandt, Rubens
- Use for: Dramatic, rich compositions

**art nouveau**
- Organic, flowing lines (late 19th century)
- Artists: Mucha, Klimt
- Use for: Decorative, elegant designs

**art deco**
- Geometric, glamorous style (1920s-1930s)
- Use for: Elegant, streamlined designs

**pop art**
- Bold, commercial imagery (1950s-1960s)
- Artists: Warhol, Lichtenstein
- Use for: Vibrant, graphic compositions

**surrealism**
- Dream-like, bizarre imagery
- Artists: Dalí, Magritte
- Use for: Fantastical, imaginative scenes

**cubism**
- Geometric, fragmented forms
- Artists: Picasso, Braque
- Use for: Abstract, analytical compositions

**expressionism** / **abstract expressionism**
- Emotional, subjective art
- Artists: Kandinsky, Pollock
- Use for: Emotional, gestural artwork

**romanticism**
- Emotional, dramatic scenes (late 18th-19th century)
- Use for: Dramatic, emotional landscapes

**realism**
- Accurate, objective representation
- Use for: Truthful, unidealized depictions

### Artistic Techniques

**stippling**
- Dots creating tone and texture
- Use for: Detailed, textured artwork

**cross-hatching**
- Intersecting lines for shading
- Use for: Traditional drawing techniques

**blending**
- Smooth color transitions
- Use for: Soft, gradual effects

**glazing**
- Transparent layers of paint
- Use for: Luminous, deep colors

**impasto**
- Thick, textured paint application
- Use for: Sculptural, textured surfaces

**sgraffito**
- Scratching through layers
- Use for: Textural effects, revealing underlayers

**pointillism**
- Small dots of pure color
- Use for: Optical color mixing

**collage**
- Assembled mixed materials
- Use for: Layered, textural compositions

**mixed media**
- Multiple materials combined
- Use for: Experimental, varied textures

---

## Quality Modifiers

### General Quality Terms

Use 2-3 quality modifiers for best results. Avoid overloading.

**high-quality** / **high quality**
- General quality indicator
- Use for: Any subject requiring quality emphasis

**beautiful**
- Aesthetic appeal
- Use for: Pleasing, attractive subjects

**stunning**
- Impressive visual impact
- Use for: Eye-catching, remarkable imagery

**gorgeous**
- Exceptionally beautiful
- Use for: Highly attractive subjects

**elegant**
- Refined, graceful quality
- Use for: Sophisticated subjects

**stylized**
- Distinctive artistic treatment
- Use for: Unique visual approaches

**detailed** / **highly detailed**
- Rich in detail
- Use for: Complex, intricate subjects

**intricate**
- Complex, elaborate detail
- Use for: Detailed, complex compositions

**professional**
- Expert-level quality
- Use for: Commercial, high-standard work

**premium**
- Top-tier quality
- Use for: Luxury, high-end subjects

**award-winning**
- Exceptional, recognized quality
- Use for: Outstanding, exemplary work

### Photography-Specific Quality

**4K** / **8K**
- High resolution indicators
- Use for: Sharp, detailed photography

**HDR** / **4K HDR**
- High dynamic range
- Use for: Rich tonal range, vivid imagery

**studio photo**
- Professional studio quality
- Use for: Controlled, professional photography

**professional photograph** / **professional photography**
- Expert photography quality
- Use for: Commercial, high-quality photos

**professional product photography**
- Specialized product photography
- Use for: E-commerce, catalog imagery

**landscape photography**
- Specialized landscape quality
- Use for: Scenic, environmental photography

**taken by a professional photographer**
- Expert photographer indicator
- Use for: High-standard photography

**commercial photography** / **editorial photography**
- Professional commercial work
- Use for: Advertising, magazine quality

**magazine quality**
- Publication-standard photography
- Use for: Editorial, high-quality imagery

**sharp focus** / **crystal clear**
- Exceptional sharpness
- Use for: Detailed, crisp imagery

**breathtaking**
- Awe-inspiring quality
- Use for: Spectacular, impressive scenes

### Art-Specific Quality

**by a professional**
- Professional artist quality
- Use for: Expert-level artwork

**professional artwork**
- High-quality artistic work
- Use for: Commercial, professional art

**masterpiece**
- Exceptional artistic achievement
- Use for: Outstanding, exemplary artwork

**museum quality** / **gallery worthy**
- Exhibition-standard quality
- Use for: Fine art, collectible work

**highly detailed artwork** / **highly detailed**
- Rich artistic detail
- Use for: Complex, intricate artwork

**detailed**
- Good level of detail
- Use for: Careful, thorough artwork

**intricate details**
- Complex, elaborate detail
- Use for: Detailed, sophisticated artwork

**fine art**
- High artistic quality
- Use for: Serious, artistic work

### Context-Specific Modifiers

**Food Photography**
- “in the style of a food magazine”
- “appetizing”
- “mouth-watering”
- “gourmet presentation”

**Architecture**
- “architectural photography”
- “architectural digest style”
- “modern architecture”

**Fashion**
- “fashion photography”
- “vogue style”
- “haute couture”

**Product**
- “professional product photography”
- “e-commerce quality”
- “catalog photography”

---

## Material & Shape Modifiers

### Materials

**Natural Materials**
- **wood** / **wooden**: Organic, warm material
- **stone**: Solid, natural material
- **marble**: Elegant, veined stone
- **crystal**: Clear, faceted material
- **ice**: Frozen, translucent material

**Metals**
- **metal**: General metallic material
- **glass**: Transparent, reflective material
- **wire**: Thin, linear metal

**Synthetic Materials**
- **plastic**: Moldable, modern material
- **ceramic**: Fired clay material
- **concrete**: Industrial, textured material

**Fabric & Soft Materials**
- **fabric** / **cloth**: Textile materials
- **paper**: Flat, foldable material
- **origami**: Folded paper art

**Special Materials**
- **cheese**: Organic, textured material (creative use)
- **neon tubes**: Glowing, linear elements

### Textures & Finishes

**rough**
- Uneven, textured surface
- Use for: Natural, organic subjects

**smooth**
- Even, flat surface
- Use for: Polished, refined subjects

**glossy** / **shiny**
- Reflective, lustrous finish
- Use for: Polished, wet surfaces

**matte**
- Non-reflective finish
- Use for: Subtle, understated surfaces

**brushed**
- Directionally textured metal
- Use for: Modern, industrial subjects

**polished**
- Highly refined, smooth surface
- Use for: Luxury, refined subjects

**textured**
- Surface with tactile quality
- Use for: Interesting, varied surfaces

**soft** / **hard**
- Tactile quality indicators
- Use for: Material characteristic emphasis

### Material Styles

**origami style**
- Folded paper aesthetic
- Use for: Geometric, angular designs

**wireframe**
- Skeletal, outlined structure
- Use for: Technical, architectural subjects

**transparent**
- See-through quality
- Use for: Glass-like, ethereal subjects

**translucent**
- Partially see-through
- Use for: Soft, diffused light effects

**opaque**
- Non-transparent
- Use for: Solid, substantial subjects

**reflective**
- Mirror-like quality
- Use for: Shiny, polished surfaces

### Usage Patterns

**“made of [material]”**
- Example: “a coffee cup made of glass”
- Example: “a logo made of neon tubes”

**“in the shape of [object]”**
- Example: “a building in the shape of a pyramid”
- Example: “a cake in the shape of a castle”

**“[material] [subject]”**
- Example: “wooden sculpture”
- Example: “glass figurine”

**“[subject] with [texture] finish”**
- Example: “metal sphere with brushed finish”
- Example: “ceramic vase with glossy finish”

---

## Photorealism Specialization

### Portrait Photography

**Recommended Lenses**: Prime, Zoom
**Focal Lengths**: 24-35mm, 50mm, 85mm

**Additional Details**:
- black and white film
- film noir
- depth of field
- duotone (mention two colors)
- natural lighting
- dramatic lighting

**Tips**:
- Specify facial details as a focus
- Use the word “portrait” in the prompt
- Consider color grading (duotones)
- Mention film style for aesthetic

**Example**:

```
A woman in her 20s, 35mm portrait, film noir, dramatic lighting, depth of field
```

### Objects & Still Life

**Subjects**: Food, insects, plants
**Recommended Lenses**: Macro
**Focal Lengths**: 60-105mm

**Additional Details**:
- high detail
- precise focusing
- controlled lighting
- studio lighting
- professional photography

**Example**:

```
A plate of pasta, 100mm macro lens, studio lighting, high detail, professional food photography
```

### Motion & Action

**Subjects**: Sports, wildlife
**Recommended Lenses**: Telephoto zoom
**Focal Lengths**: 100-400mm

**Additional Details**:
- fast shutter speed
- action tracking
- movement tracking
- freeze motion

**Example**:

```
A deer running in the forest, telephoto zoom, fast shutter speed, movement tracking
```

### Wide-Angle & Landscape

**Subjects**: Astronomical, landscape
**Recommended Lenses**: Wide-angle
**Focal Lengths**: 10-24mm

**Additional Details**:
- long exposure times
- sharp focus
- long exposure
- smooth water
- smooth clouds
- deep focus

**Example**:

```
An expansive mountain range with a pristine lake, wide angle 10-24mm, golden hour, deep focus, landscape photography
```

---

## Usage Examples

### Example 1: Portrait Photography

**Objective**: Professional portrait with dramatic mood

**Prompt**:

```
A woman in her 20s, 35mm portrait, film noir, dramatic lighting, professional photograph
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 3:4
- Image Size: 1K

**Breakdown**:
- Subject: “A woman in her 20s”
- Photography: “35mm portrait”, “film noir”, “dramatic lighting”
- Quality: “professional photograph”

---

### Example 2: Product Photography

**Objective**: Premium product shot for e-commerce

**Prompt**:

```
A luxury smartwatch on a clean white background, studio lighting, shallow depth of field, 4K HDR, professional product photography
```

**Configuration**:
- Model: Nano Banana-4.0-ultra-generate-001
- Aspect Ratio: 1:1
- Image Size: 2K

**Breakdown**:
- Subject: “A luxury smartwatch”
- Context: “on a clean white background”
- Photography: “studio lighting”, “shallow depth of field”
- Quality: “4K HDR”, “professional product photography”

---

### Example 3: Landscape Photography

**Objective**: Breathtaking landscape at sunset

**Prompt**:

```
An expansive mountain range with a pristine lake, wide angle 10-24mm, golden hour, deep focus, landscape photography, stunning, breathtaking
```

**Configuration**:
- Model: Nano Banana-4.0-ultra-generate-001
- Aspect Ratio: 16:9
- Image Size: 2K

**Breakdown**:
- Subject: “An expansive mountain range with a pristine lake”
- Photography: “wide angle 10-24mm”, “golden hour”, “deep focus”
- Quality: “landscape photography”, “stunning”, “breathtaking”

---

### Example 4: Logo Design with Text

**Objective**: Modern logo for healthcare company

**Prompt**:

```
A minimalist logo for a health care company on a solid color background, with the text "Journey" in modern font, centered, professional, clean, high-quality
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 1:1
- Image Size: 1K

**Breakdown**:
- Subject: “A minimalist logo for a health care company”
- Context: “on a solid color background”
- Text: “Journey” (modern font, centered)
- Quality: “professional”, “clean”, “high-quality”

---

### Example 5: Artistic Illustration

**Objective**: Watercolor landscape in impressionist style

**Prompt**:

```
A serene forest scene, watercolor, in the style of impressionism, masterpiece, by a professional, highly detailed
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 4:3
- Image Size: 1K

**Breakdown**:
- Subject: “A serene forest scene”
- Art: “watercolor”, “in the style of impressionism”
- Quality: “masterpiece”, “by a professional”, “highly detailed”

---

### Example 6: Food Photography

**Objective**: Magazine-quality food shot

**Prompt**:

```
French fries on a wooden surface, 100mm macro lens, controlled lighting, 4:3 aspect ratio, in the style of a food magazine, professional food photography
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 4:3
- Image Size: 1K

**Breakdown**:
- Subject: “French fries”
- Context: “on a wooden surface”
- Photography: “100mm macro lens”, “controlled lighting”
- Quality: “in the style of a food magazine”, “professional food photography”

---

### Example 7: Creative Material Application

**Objective**: Unique neon tube logo

**Prompt**:

```
A coffee cup logo made of neon tubes on a dark background, glowing, professional, vibrant, eye-catching
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 1:1
- Image Size: 1K

**Breakdown**:
- Subject: “A coffee cup logo”
- Material: “made of neon tubes”
- Context: “on a dark background”
- Style: “glowing”
- Quality: “professional”, “vibrant”, “eye-catching”

---

### Example 8: Action Photography

**Objective**: Frozen sports moment

**Prompt**:

```
A winning touchdown, telephoto zoom 100-400mm, fast shutter speed, action tracking, professional sports photography, 4K HDR
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 16:9
- Image Size: 1K

**Breakdown**:
- Subject: “A winning touchdown”
- Photography: “telephoto zoom 100-400mm”, “fast shutter speed”, “action tracking”
- Quality: “professional sports photography”, “4K HDR”

---

### Example 9: Architectural Photography

**Objective**: Modern building exterior

**Prompt**:

```
A modern glass skyscraper, aerial photo, blue hour, wide angle 10-24mm, architectural photography, stunning, professional photograph
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 9:16
- Image Size: 1K

**Breakdown**:
- Subject: “A modern glass skyscraper”
- Photography: “aerial photo”, “blue hour”, “wide angle 10-24mm”
- Quality: “architectural photography”, “stunning”, “professional photograph”

---

### Example 10: Abstract Art

**Objective**: Modern abstract composition

**Prompt**:

```
Abstract geometric shapes, digital art, vibrant colors, minimalist, modern, professional artwork, high-quality
```

**Configuration**:
- Model: Nano Banana-4.0-generate-001
- Aspect Ratio: 1:1
- Image Size: 1K

**Breakdown**:
- Subject: “Abstract geometric shapes”
- Art: “digital art”, “minimalist”, “modern”
- Context: “vibrant colors”
- Quality: “professional artwork”, “high-quality”

---

## Best Practices

### DO ✅

**Start with a Clear Subject**
- Be specific about what you want
- Include relevant details
- Example: “a luxury sports car” not “a car”

**Use Appropriate Technical Terms**
- Photography: lens types, lighting, camera settings
- Art: mediums, styles, techniques
- Example: “35mm, natural lighting, bokeh”

**Include 2-3 Quality Modifiers**
- Enhance without overwhelming
- Choose context-appropriate terms
- Example: “professional photograph, 4K HDR, stunning”

**Match Aspect Ratio to Use Case**
- Social media: 1:1 or 9:16
- Landscapes: 16:9
- Portraits: 3:4
- Example: Use 16:9 for YouTube thumbnails

**Iterate and Refine**
- Start simple, add details
- Test different modifiers
- Build complexity gradually

**Keep Text Short**
- 25 characters or less per phrase
- Maximum 3 text phrases
- Example: “SALE” not “Big Summer Sale Event”

**Layer Modifiers**
- Combine 2-3 categories
- Photography + Quality
- Art + Material + Quality
- Example: “watercolor (art) on textured paper (material), masterpiece (quality)”

**Consider Context**
- Match modifiers to subject
- Use appropriate quality terms
- Example: “food magazine style” for food, not “architectural photography”

### DON’T ❌

**Exceed 480 Tokens**
- Stay within limits
- Framework estimates tokens automatically
- Remove redundant modifiers if needed

**Be Vague**
- Specificity produces better results
- Avoid generic descriptions
- Bad: “a nice picture”
- Good: “a professional portrait with natural lighting”

**Mix Incompatible Modifiers**
- Avoid contradictions
- Check logical consistency
- Bad: “aerial from below”
- Bad: “black and white, vibrant colors”

**Overload with Quality Terms**
- 2-3 is optimal
- More doesn’t mean better
- Bad: “professional premium high-quality award-winning masterpiece stunning gorgeous”
- Good: “professional, high-quality, stunning”

**Forget Style/Medium**
- Always specify visual approach
- Photography or art style
- Bad: “a person”
- Good: “a professional portrait” or “a watercolor illustration of a person”

**Use Only Subject**
- Add context and modifiers
- Build complete prompts
- Bad: “a car”
- Good: “a luxury sports car in an urban setting, dramatic lighting, professional photograph”

**Ignore Aspect Ratio**
- Match to final use
- Consider platform requirements
- Bad: 1:1 for landscape
- Good: 16:9 for landscape

**Use Long Text Phrases**
- Keep text concise
- Break into multiple phrases if needed
- Bad: “Welcome to our amazing summer sale event”
- Good: “Summer Sale” or split into “Summer” and “Sale”

### Token Management

**Good - Concise and Effective** (≈15 tokens)

```
A professional portrait, 35mm, natural lighting, high quality
```

**Too Long - Redundant Modifiers** (≈25 tokens)

```
A very professional high-quality premium award-winning masterpiece portrait with excellent lighting
```

**Optimal Balance** (≈30 tokens)

```
A woman in her 20s, 35mm portrait, natural lighting, bokeh, professional photograph, stunning
```

### Aspect Ratio Selection Guide

**Social Media**
- Instagram Post: 1:1
- Instagram Story: 9:16
- Facebook Post: 1:1 or 4:3
- Twitter Post: 16:9 or 1:1

**Video Platforms**
- YouTube Thumbnail: 16:9
- TikTok: 9:16
- YouTube Shorts: 9:16

**Photography**
- Portrait: 3:4
- Landscape: 16:9 or 4:3
- Square: 1:1

**Print**
- Standard Photo: 4:3
- Portrait: 3:4
- Poster: 16:9 or 9:16

### Quality Modifier Combinations

**Photography - Standard Quality**

```
professional photograph
```

**Photography - High Quality**

```
professional photograph, 4K HDR
```

**Photography - Premium Quality**

```
professional photograph, 4K HDR, stunning, sharp focus
```

**Art - Standard Quality**

```
professional artwork
```

**Art - High Quality**

```
professional artwork, detailed
```

**Art - Premium Quality**

```
masterpiece, by a professional, highly detailed
```

---

## Quick Reference

### Common Use Case Templates

**Portrait Photography**

```
[Subject description], [focal length] portrait, [lighting], [film type], professional photograph
```

**Product Photography**

```
[Product] on [background], studio lighting, shallow depth of field, professional product photography
```

**Landscape Photography**

```
[Landscape description], wide angle [focal length], [time of day], landscape photography, stunning
```

**Logo Design**

```
A [style] logo for [industry], on [background], professional, clean, high-quality
```

**Food Photography**

```
[Food item] on [surface], [lens] macro lens, controlled lighting, food magazine style
```

**Artistic Illustration**

```
[Subject], [medium], in the style of [historical style], masterpiece, highly detailed
```

**Action Photography**

```
[Action scene], telephoto zoom, fast shutter speed, action tracking, professional sports photography
```

**Architectural Photography**

```
[Building description], [camera position], [lighting], wide angle, architectural photography
```

### Modifier Quick List

**Photography Essentials**
- Proximity: close-up, medium shot, zoomed out
- Position: aerial, from below, eye-level
- Lighting: natural lighting, dramatic lighting, golden hour
- Settings: bokeh, shallow depth of field, motion blur
- Lens: 35mm, 50mm, 85mm, wide angle, macro, telephoto

**Art Essentials**
- Medium: watercolor, oil painting, digital art, sketch
- Style: realistic, abstract, minimalist, stylized
- Historical: impressionism, art deco, pop art, surrealism

**Quality Essentials**
- General: professional, high-quality, stunning, detailed
- Photo: 4K HDR, professional photograph, sharp focus
- Art: masterpiece, by a professional, highly detailed

**Material Essentials**
- Materials: glass, metal, wood, neon tubes, origami
- Textures: glossy, matte, rough, smooth
- Styles: transparent, wireframe, reflective

### Token Estimation

Rough estimation: ~1 token per 4 characters

**Short Prompt** (≈50 tokens)

```
A modern chair, studio lighting, professional photograph
```

**Medium Prompt** (≈100 tokens)

```
A luxury sports car in an urban setting at night, dramatic lighting, 35mm, bokeh, professional photograph, 4K HDR, stunning
```

**Long Prompt** (≈200 tokens)

```
A woman in her 20s wearing a business suit, 35mm portrait, film noir, dramatic lighting with strong shadows, shallow depth of field, professional photograph taken by a professional photographer, 4K HDR, stunning, elegant
```

**Maximum Recommended** (≈400 tokens)
Approach with caution - use only when necessary for complex scenes

### Model Selection Guide

**Nano Banana-4.0-ultra-generate-001**
- Use when: Maximum quality needed
- Best for: Professional work, client deliverables, portfolio pieces
- Supports: 1K and 2K sizes

**Nano Banana-4.0-generate-001**
- Use when: Balanced quality and speed needed
- Best for: Most use cases, general production work
- Supports: 1K and 2K sizes

**Nano Banana-4.0-fast-generate-001**
- Use when: Speed is priority
- Best for: Rapid iteration, testing, drafts
- Supports: 1K size only

**Nano Banana-3.0-generate-002**
- Use when: Legacy compatibility needed
- Best for: Specific legacy requirements
- Supports: 1K size only

### Troubleshooting

**Problem**: Images lack detail
**Solution**: Add quality modifiers like “highly detailed”, “4K HDR”, “sharp focus”

**Problem**: Wrong composition
**Solution**: Specify camera proximity and position more clearly

**Problem**: Poor lighting
**Solution**: Add specific lighting modifiers like “golden hour”, “studio lighting”, “dramatic lighting”

**Problem**: Wrong style
**Solution**: Specify art medium or photography style more explicitly

**Problem**: Text not appearing
**Solution**: Keep text under 25 characters, use clear placement instructions

**Problem**: Exceeding token limit
**Solution**: Remove redundant quality modifiers, simplify descriptions

**Problem**: Inconsistent results
**Solution**: Be more specific with technical terms, add more modifiers

**Problem**: Wrong aspect ratio
**Solution**: Explicitly set aspect ratio in configuration

---

## Framework Components

### TypeScript Framework Files

**Nano Banana-prompt-framework.ts**
- Main PromptBuilder class
- Fluent API for building prompts
- Validation and token counting
- QuickBuild helper functions

**prompt-components.ts**
- TypeScript type definitions
- Interface definitions for all components
- Type safety for modifiers

**integration-examples.ts**
- 15+ complete code examples
- Integration patterns
- Real-world use cases

### JSON Modifier Libraries

**photography-modifiers.json**
- Camera proximity values
- Camera positions
- Lighting conditions
- Camera settings
- Lens types and focal lengths
- Film types
- Photography specializations

**art-style-modifiers.json**
- Art mediums
- Art styles
- Historical art movements
- Artistic techniques
- Combination suggestions

**quality-modifiers.json**
- General quality terms
- Photography-specific modifiers
- Art-specific modifiers
- Context-specific modifiers
- Usage strategies

**material-shape-modifiers.json**
- Material types
- Textures and finishes
- Material styles
- Usage patterns
- Creative applications

**photorealism-guide.json**
- Portrait photography specs
- Object photography specs
- Motion photography specs
- Landscape photography specs
- Recommended settings

**Nano Banana-config.json**
- Model specifications
- Aspect ratio guidance
- Configuration options
- Best practices

**prompt-templates.json**
- Pre-built templates
- Common use cases
- Parameter definitions
- Example prompts

### Integration Guides

**gpt-instructions.md**
- Custom GPT setup instructions
- Knowledge file configuration
- Conversation starters
- Testing procedures

**claude-project-instructions.md**
- Claude Project setup
- Knowledge base configuration
- Custom instructions
- Usage examples

---

## Advanced Techniques

### Combining Multiple Modifiers

**Photography + Quality**

```
A luxury watch, 35mm, studio lighting, bokeh, professional product photography, 4K HDR
```

**Art + Material + Quality**

```
A coffee cup logo made of neon tubes, digital art, glowing, professional, vibrant
```

**Photography + Art + Quality**

```
A forest scene, 35mm, natural lighting, watercolor style, masterpiece, highly detailed
```

### Duotone Color Grading

Specify two colors for duotone effect:

```
35mm portrait, blue and grey duotones
```

```
Landscape photo, orange and teal duotones
```

### Layering Text

Multiple text elements (max 3):

```
A logo on white background, with the text "BRAND" in bold font, centered, and the text "Est. 2024" in small font, bottom
```

### Material Transformations

Creative material applications:

```
A lion made of origami paper, origami style, white background
```

```
A city skyline made of glass, transparent, reflective, modern
```

```
A tree in the shape of a human figure, wooden, natural
```

### Time-of-Day Lighting

Specific lighting for atmosphere:

```
golden hour - warm, soft, shortly after sunrise or before sunset
blue hour - cool, soft, just before sunrise or after sunset
midday - bright, harsh, overhead sun
dusk - fading light, transitional
dawn - early morning, soft light
```

### Seasonal Variations

Add seasonal context:

```
A park in autumn, golden hour, warm tones, falling leaves
```

```
A mountain landscape in winter, blue hour, cold lighting, snow-covered
```

### Emotional Tone

Convey mood through modifiers:

```
Dramatic lighting, film noir, high contrast - moody, intense
Soft lighting, warm tones, golden hour - peaceful, romantic
Hard lighting, cold tones, high angle - clinical, stark
Natural lighting, soft focus, pastel colors - dreamy, ethereal
```

---

## Integration Patterns

### Custom GPT Integration

**Setup**:
1. Create Custom GPT in ChatGPT
2. Upload JSON modifier files to knowledge
3. Add framework instructions
4. Configure conversation starters
5. Test with example prompts

**Usage**:
User describes desired image → GPT builds structured prompt → User refines → Final prompt generated

### Claude Project Integration

**Setup**:
1. Create new Claude Project
2. Upload JSON files to project knowledge
3. Add custom instructions from framework
4. Test with examples

**Usage**:
Conversational prompt building → Claude suggests modifiers → Iterative refinement → Complete prompt

### API Integration

**Pattern**:

```tsx
import { Nano BananaPromptBuilder } from './Nano Banana-prompt-framework';// Build promptconst result = new Nano BananaPromptBuilder()
  .subject('your subject')
  .photography({ lighting: 'natural lighting' })
  .quality({ photoSpecific: ['4K HDR'] })
  .build();// Use with Nano Banana APIconst response = await Nano BananaAPI.generateImages({
  model: result.config.model,  prompt: result.prompt,  config: result.config});
```

### Programmatic Usage

**Batch Generation**:

```tsx
const subjects = ['car', 'house', 'tree'];const prompts = subjects.map(subject =>
  new Nano BananaPromptBuilder()
    .subject(subject)
    .photography({ lighting: 'golden hour' })
    .quality({ general: ['stunning'] })
    .build()
);
```

**Template-Based**:

```tsx
const template = {
  basePrompt: 'A {subject} in {setting}',  parameters: [
    { parameterName: 'subject', defaultValue: 'car' },    { parameterName: 'setting', defaultValue: 'urban environment' }
  ]
};const prompt = fromTemplate(template, {
  subject: 'sports car',  setting: 'mountain road'});
```

---

## Validation & Optimization

### Token Counting

Framework automatically estimates tokens:
- ~1 token per 4 characters (English)
- Maximum: 480 tokens
- Warning at: 400 tokens
- Optimal: 100-300 tokens

### Validation Rules

**Required**:
- Subject must be provided
- Token count under 480

**Warnings**:
- More than 3 text phrases
- Text phrases over 25 characters
- Token count over 400
- 2K size with Nano Banana 3 model

**Errors**:
- Missing subject
- Token limit exceeded
- Invalid configuration combinations

### Optimization Tips

**Reduce Tokens**:
- Remove redundant quality modifiers
- Simplify subject description
- Use concise technical terms
- Combine similar modifiers

**Improve Quality**:
- Add specific technical terms
- Layer 2-3 modifier categories
- Include context
- Use appropriate quality modifiers

**Balance**:
- Aim for 100-300 tokens
- 2-3 quality modifiers
- 1-2 photography/art modifiers
- Clear subject and context

---

## Conclusion

This framework provides a comprehensive system for generating superior Nano Banana prompts. By understanding and applying these modifiers, configurations, and best practices, you can create highly effective prompts for any use case.

### Key Takeaways

1. **Structure is Essential**: Follow the [Style] + [Subject] + [Context] + [Modifiers] + [Quality] pattern
2. **Be Specific**: Technical terms and detailed descriptions produce better results
3. **Layer Modifiers**: Combine 2-3 categories for optimal results
4. **Stay Within Limits**: Maximum 480 tokens, optimal 100-300 tokens
5. **Match Context**: Choose appropriate modifiers for your subject
6. **Iterate**: Start simple, refine based on results
7. **Use Quality Wisely**: 2-3 quality modifiers, not more

### Next Steps

1. **Experiment**: Try different modifier combinations
2. **Build Templates**: Create reusable patterns for your use cases
3. **Integrate**: Set up Custom GPT or Claude Project
4. **Refine**: Iterate based on generated results
5. **Share**: Document successful patterns for reuse

---

**Framework Version**: 1.0
**Last Updated**: 2024
**Based on**: Google Nano Banana Official Documentation

**Resources**:
- [Google Nano Banana Documentation](https://ai.google.dev/gemini-api/docs/imagen)
- [Gemini API Documentation](https://ai.google.dev/gemini-api/docs)
- [Nano Banana Model Versions](https://ai.google.dev/gemini-api/docs/imagen#model-versions)

---

*Built for superior Nano Banana prompt generation*