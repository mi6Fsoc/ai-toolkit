# Extract Brand DNA

Tool: Claude

1. Extracting Brand DNA
    1. Upload 10-30 images from the brand’s past campaigns.
    2. **Prompt:**
    `Analyze these images and extract the brand’s visual DNA:
2. Color grading patterns (palette, shadows, highlights, saturation)
3. Pose language (body positioning, hand placement, eye lines, energy)
4. Texture treatment (fabric, skin, background, detail emphasis)
5. Lighting setups (direction, quality, shadow density)
6. Composition rules (framing, negative space, depth of field)
7. Environmental patterns (settings, architecture, seasonal elements)

Output as a technical style guide.`

1. Generate Scene Concepts
    1. **Prompt:**
    `Based on this brand DNA: [paste DNA]

Create 10 scene concepts for [campaign theme/product].

For each scene, include:

- Setting, time of day, atmospheric conditions
- Model direction: pose, expression, wardrobe
- Camera setup: focal length, angle, framing
- Technical specs: color grading, lighting, texture emphasis

Make each concept detailed enough to execute without additional decisions.`

1. Execute in Weavy
Copy scene concept. Paste into Weavy. Generate
Quality check:
Color grading matches brand palette?
Pose language consistent?
Lighting aligned?
Composition follows brand rules?
2. Character (if needed)
    1. Generate character sheet from the same model
    2. Lock facial identity
    3. Apply to scenes
