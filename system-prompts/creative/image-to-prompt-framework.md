# Image to Prompt Framework

# 🔷 GPT:

Great idea. Give GPT a shopping list, not a vibe. Here’s a concise checklist of datapoints to include when you ask it to craft a production-grade, platform-ready image prompt.

What to specify

- Objective and deliverables
    - Purpose/use (poster, tattoo flash, print, concept art)
    - Deliverable sections you want: Core prompt, Optional negatives, Midjourney variant (+ negatives), SD/SDXL positive/negative/settings, DALL·E-style phrasing, Notes/tweaks
- Primary subject and focal hierarchy
    - Main subject(s), count, orientation (front-facing, 3/4, profile)
    - Focal priority (what must be the center of attention)
    - Scale/cropping (bust, head-only, full figure)
- Key actions and gestures
    - Exact poses/gestures and which limb/body part performs them
    - Interaction with props (who holds what, how)
- Props and iconography
    - List of props, materials, and condition (aged, frayed, polished)
    - Placement and symmetry (left/right/center; foreground/background)
    - Any “must include” micro-details
- Composition and framing
    - Layout (centered, symmetrical, rule-of-thirds, poster-like)
    - Aspect ratio and orientation (e.g., 2:3 portrait)
    - Negative space vs dense detail; vignette/framing elements
- Background and geometric structures
    - Backdrop motifs (halo, web, sigils, mandala, lattice)
    - Geometry style (radial, concentric, hex/diamond mesh)
    - How it fades or blends (vignette, fog, gradient)
- Style, medium, and technique
    - Visual medium (engraving, scratchboard, pen-and-ink, woodcut)
    - Line/shading methods (cross‑hatching, stippling, etching)
    - Era/influences (baroque, Victorian gothic, memento mori)
    - Level of stylization (photoreal, illustrative, raw/clean linework)
- Palette and lighting
    - Color policy (monochrome vs limited palette; list tones)
    - Contrast and lighting model (high-contrast chiaroscuro, rim light, backlight)
    - Value placement (bright halo, dark vignette, midtone subject)
- Atmospherics and surface details
    - Mist/fog/smoke, dust motes, drips/ichor, condensation, grime
    - Weathering: cracks, patina, texture emphasis
- Quality and sharpness
    - Line quality (razor‑sharp, ultra-detailed, fine micro-lines)
    - Detail target phrases (8k detail/ultra-detailed lines—if desired)
- Negatives and exclusions
    - Content bans (no text/typography/watermarks/signatures/logos)
    - Anatomy bans (no extra limbs/fingers; specify “five fingers per hand”)
    - Style bans (no anime, no 3D, no low-res, no blur, no gore, no neon)
    - Any safety/filters concerns (e.g., avoid explicit occult if needed)
- Engine targets and parameters
    - Midjourney: version, aspect ratio, --style raw, --stylize value, --chaos, --quality, seed (if needed); MJ negatives via --no
    - SD/SDXL: resolution, sampler (e.g., DPM++ 2M Karras), steps, CFG, Hires fix/upscale factor and method, denoise strength; positive and negative prompts separated
    - DALL·E-style: compact natural-language phrasing, no platform flags, reiterate “no text”
- Constraint strength and priority
    - Must-have vs nice-to-have elements
    - Hard constraints (e.g., “monochrome only,” “symmetrical, perfectly centered”)
- Variation knobs
    - Style dials you might want versions for (tattoo flash / occult poster/scratchboard print)
    - Randomness/creativity bounds (e.g., low chaos vs exploratory)
    - Number of variants to output
- Output formatting from GPT
    - Clear section headers; prompts in quotes; no commentary inside the quoted prompts
    - Bulleted negatives per engine
    - Short “Notes/tweaks” with troubleshooting tips

Optional mini-template you can paste for GPT

- Purpose/use:
- Target engines and sections to produce:
- Main subject(s) and count:
- Orientation/pose/gestures (who does what):
- Props (with materials/condition/placement):
- Composition/framing (centered/symmetry/aspect ratio):
- Background geometry/motifs:
- Style/medium/technique keywords:
- Palette and lighting:
- Atmospherics/surface details:
- Quality/linework targets:
- Must-have elements (hard constraints):
- Exclusions/negatives:
- Midjourney params (—ar, —style, —s, —chaos, —q, seed):
- SDXL settings (resolution, sampler, steps, CFG, upscaler/Hires fix, denoise):
- DALL·E phrasing preferences:
- Variation dials to include:
- Output formatting requirements:

Pro tip: Be explicit about counts, sides, and actions (e.g., “left hand offers a corked vial with faint vapor; right hand holds a twine-tied scroll; central hand makes a ‘shh’ gesture”). That one habit alone prevents many models from freelancing.

———

## 🔷 CLAUDE:

Based on the superior GPT prompt, here's a comprehensive list of datapoints to include when prompting GPT to generate high-quality image generation prompts:

## Core Content Requirements

### 1. Element Inventory

- Main focal point (specific identification)
- All visible objects with precise descriptions
- Positioning relationships ("below," "behind," "central")
- Specific gestures or actions
- Small details (drips, vapor, textures)

### 2. Technical Art Specifications

- Exact artistic techniques (cross-hatching, stippling, etc.)
- Style references (baroque etching, scratchboard, pen-and-ink)
- Lighting approach (chiaroscuro, rim light, etc.)
- Texture descriptions (linework quality, shading methods)
- Color palette (specific: "monochrome: black, bone, pewter")

### 3. Composition Details

- Layout (symmetrical, centered, rule of thirds)
- Framing (portrait, landscape, poster-like)
- Depth elements (foreground, background, vignetting)
- Visual hierarchy (focal point emphasis)

### 4. Mood & Atmosphere

- Emotional descriptors (haunting, serene, unsettling)
- Thematic keywords (memento mori, gothic, ritual)
- Atmospheric effects (mist, dust motes, fog)

## Platform-Specific Elements

### 5. Multi-Platform Variants

- Core all-purpose prompt
- Midjourney syntax with parameters (--ar, --v, --s, --chaos)
- Stable Diffusion format with settings
- DALL-E condensed phrasing
- Platform-specific terminology adjustments

### 6. Technical Parameters

- Resolution specifications (8k, 1024x1536)
- Aspect ratios
- Sampler recommendations
- CFG/guidance scale values
- Steps count
- Upscaling suggestions

### 7. Negative Prompts

- Common unwanted elements (extra limbs, blur)
- Style exclusions (no cartoon, no 3D)
- Quality issues (low-res, watermark)
- Platform-specific negatives

## Structural Format

### 8. Organization

- Clear section headers
- Core prompt first
- Platform variants separated
- Technical settings grouped
- Optional elements marked

### 9. Language Precision

- Active, specific verbs
- Precise adjectives (not just "detailed" but "razor-sharp")
- Technical terminology where appropriate
- Consistent punctuation and formatting

### 10. Practical Additions

- "No text" specification if needed
- Output quality markers (detail level)
- Alternative style suggestions
- Customization notes for users

## Sample Instruction Template

- "Create a comprehensive image generation prompt with:
- Detailed description of [subject], including all visible elements
- Multiple platform variants (Midjourney v6, SDXL, DALL-E)
- Technical art style specifications using terms like [specific techniques]
- Negative prompts to avoid common issues
- Recommended settings for each platform
- Mood descriptors emphasizing [desired atmosphere]
- Composition details (symmetry, framing, layout)
- Resolution and quality specifications
- Optional style variations (tattoo flash, poster art, etc.)"*

This structured approach ensures GPT generates prompts that are immediately usable, technically precise, and adaptable across different AI art platforms.

———

## 🔷 GEMINI:

Of course. Based on the analysis of what made the "GPT Prompt" superior, here is a list of datapoints and instructions you should include in your request to have me generate similar high-quality, actionable image prompts.

Think of this as building a "prompt for a prompt generator." The more of these datapoints you provide, the more tailored and effective the final output will be.

---

### Datapoints for Generating Superior Image Prompts

### 1. Define the Core Subject and Scene

This is the foundational idea. Be as clear as possible about the "what."

- Central Focal Point: What is the main subject? (e.g., "a cybernetic wolf," "an ancient tree," "a floating crystal.")
- Secondary Elements: What other objects are in the scene? (e.g., "glowing runes on its fur," "moss and lanterns hanging from its branches," "smaller shards orbiting it.")
- Actions & Poses: What is the subject doing? (e.g., "howling at a binary moon," "its roots are pulling up cobblestones," "it's pulsing with a soft light.")
- Background & Environment: Where is the subject? (e.g., "on a rain-slicked neon street," "in a misty, forgotten forest," "in the void of space.")

### 2. Specify the Desired Prompt Structure and Format

This is the most critical step to get a truly actionable prompt. You must explicitly ask for the components you need.

- Request a "Core Prompt": Ask for a primary, all-purpose descriptive prompt. Specify if you want it as a dense, single paragraph for model efficiency.
- Request "Platform-Specific Variants": This is key. Ask for versions tailored for popular models. (e.g., "Provide variants for Midjourney v6, Stable Diffusion (SDXL), and DALL-E 3.")
- Request "Technical Parameters": Ask for suggested settings for each platform. (e.g., "Include suggested Midjourney parameters like --ar, --s, --style raw and Stable Diffusion settings like Resolution, Sampler, CFG Scale.")
- Request a "Negative Prompt": Explicitly ask for a list of negative keywords to exclude common issues. (e.g., "Generate a comprehensive negative prompt to avoid blur, low resolution, text, watermarks, extra limbs, etc.")

### 3. Detail the Artistic and Stylistic Direction

Provide keywords that guide the aesthetic. The more specific, the better.

- Art Medium/Technique: (e.g., "baroque etching," "giclee print," "airbrushed concept art," "digital painting," "tintype photograph," "scratchboard illustration.")
- Linework & Texture: (e.g., "razor-sharp ink lines," "soft, blended brushstrokes," "cross-hatching and stippling," "heavy grain," "subtle textures.")
- Lighting & Atmosphere: (e.g., "high-contrast chiaroscuro," "soft volumetric lighting," "dramatic rim light," "eerie morning mist," "golden hour glow.")
- Color Palette: (e.g., "monochrome (black and white)," "sepia tone," "vibrant triadic color scheme," "desaturated pastels," "iridescent highlights.")
- Mood & Genre: (e.g., "gothic," "biopunk," "hopeful solarpunk," "Lovecraftian horror," "memento mori," "serene and tranquil.")

### 4. Dictate the Composition and Framing

Control how the scene is presented to the viewer.

- Shot Type: (e.g., "extreme close-up," "full body portrait," "wide landscape shot," "macro detail shot.")
- Compositional Rules: (e.g., "perfectly centered and symmetrical," "dynamic asymmetrical composition," "rule of thirds," "leading lines.")
- Framing: (e.g., "poster-like framing," "vignette," "framed by architectural elements.")
- Camera Angle: (e.g., "low-angle shot looking up," "high-angle shot looking down," "dutch angle.")

---

### Example Request Template

You can use this template to structure your request.

Please generate a polished, high-fidelity, multi-platform image prompt based on the following details.

1.  **Core Subject:** A lone astronaut discovering a giant, crystalline flower inside a dark, cavernous asteroid. The flower emits a soft, blue bioluminescent light.

2.  **Prompt Structure:**

*   Create a main "Core Prompt" in a single, dense paragraph.

*   Create platform-ready variants for Midjourney v6 and Stable Diffusion XL.

*   Include recommended technical parameters for both platforms (aspect ratio 3:4, samplers, etc.).

*   Provide a detailed negative prompt to avoid common errors.

3.  **Artistic Style:**

*   **Medium:** Digital painting with the feel of cinematic concept art.

*   **Lighting:** High-contrast, with the flower as the primary light source, casting long shadows. Add subtle dust motes visible in the light beams.

*   **Color Palette:** Deep blacks and blues, with a brilliant sapphire for the flower and silver highlights on the astronaut's suit.

*   **Mood:** Awe, discovery, silence, and cosmic wonder.

4.  **Composition:**

*   **Shot Type:** Wide shot to show the scale difference between the tiny astronaut and the massive flower.

*   **Compositional Rules:** Use the rule of thirds, placing the astronaut off-center, looking towards the flower.

*   **Framing:** The scene should be framed by the jagged rock of the cavern entrance.

———

## 🔷 DEEPSEEK:

Based on the analysis of the superior GPT prompt, here is a list of key datapoints you should include in your prompt when instructing GPT to generate high-quality image prompts. These datapoints will guide GPT to produce prompts that are specific, technically precise, actionable, and faithful to the desired concept. Incorporate these into your prompt as guidelines or requirements.

### Datapoints to Include in Your Prompt to GPT:

1. Request a Core All-Purpose Prompt:
    - Specify that the response should start with a detailed, stand-alone prompt that is model-agnostic but highly descriptive. This core prompt should be polished and high-fidelity, using dense language without fluff.
2. Emphasize Extreme Specificity and Concrete Details:
    - Instruct GPT to include unique, narrative-driven elements (e.g., specific gestures like "shh" finger to teeth, objects like "corked apothecary vial with vapor", materials like "dried oak leaves", and artistic techniques like "cross-hatching and stippling").
    - Avoid vague terms; instead, use precise descriptors for textures, colors (e.g., "monochrome with black, bone, pewter"), and actions.
3. Require Platform-Specific Variants:
    - Ask for adapted prompts for major AI models like Midjourney, Stable Diffusion/SDXL, and DALL·E. Each variant should include:
        - Model-Specific Syntax: For example, Midjourney parameters like --style raw --ar 2:3 --v 6.0, or SDXL settings like sampler and CFG scale.
        - Negative Prompts: Include a separate negative prompt section for each variant, listing what to avoid (e.g., "no color, no extra limbs").
        - Technical Settings: Suggest resolutions, steps, and other configurable options where applicable (e.g., "Resolution: 1024x1536, Sampler: DPM++ 2M Karras").
4. Prioritize Clarity and Concise:
    - Encourage a logical structure that flows from the central focal point outward (e.g., start with the main subject, then surroundings, then background).
    - Use bullet points or clear sections for different parts (like core prompt, variants, negatives) to enhance readability.
5. Ensure Actionability and Usability:
    - The prompt should be copy-paste ready for users of any skill level. Avoid assumptions; include all necessary parameters and explanations in a straightforward manner.
    - If possible, offer optional tweaks or tailoring suggestions (e.g., for "tattoo flash" or "occult poster" vibes).
6. Maintain Fidelity to the Source Concept:
    - Explicitly name the style, mood, and medium (e.g., "memento mori, gothic, ritual, baroque etching").
    - Include compositional cues like "symmetrical, perfectly centered portrait" to guide the AI's output.
7. Incorporate Negative Prompts as a Standard Element:
    - Always include a dedicated negative prompt section that lists common issues to avoid (e.g., "no color, no neon, no deformed hands"). This should be tailored to each platform variant.
8. Suggest Scaling or Upscaling Instructions:
    - For models that benefit from it, add notes on upscaling or hires fix (e.g., "Hires fix or 1.5x–2x upscaler after").
9. Use Descriptive Keywords for AI Optimization:
    - Include terms that AI models recognize well, such as "hyper-detailed," "high-contrast chiaroscuro," "8k detail," or "ultra-sharp ink lines."
10. Request a Summary or Tailoring Offer:
    - End with a note that GPT can further customize the prompt for specific needs, encouraging interaction and flexibility.

### Example of How to Frame Your Prompt to GPT:

You could prompt GPT with something like:

"Generate a superior image prompt for a gothic memento mori illustration. Follow these guidelines:

- Provide a core all-purpose prompt with extreme specificity, including details like [...]
- Create variants for Midjourney, Stable Diffusion/SDXL, and DALL·E with model-specific parameters and negative prompts.
- Ensure the prompt is actionable, concise, and faithful to the Gothic style.
- [...]"

By including these datapoints, you'll steer GPT toward producing prompts that are comprehensive and effective, similar to the example analyzed.