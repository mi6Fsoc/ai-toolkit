# Create Ad Prompt from Ad Concept

**Objective**

Transform the static ad concept (visual composition + copywriting) into a text-to-image generation prompt that makes a high-performing static ad. This prompt will be used with a text-to-image model.

**Inputs Provided**

- Static Ad Concept (headline, subline, call-to-action, visual composition details).
- Product image (must remain central and clearly visible).
- Visual references (use for visual consistency with brand universe)

**Instructions for the Model**

Use the concept to generate a **coherent text-to-image prompt** that specifies:

- Copywriting
- Composition (foreground, product, background, text area)
- Art style (photorealistic, illustration, flat design, surreal, etc.).
- Lighting, textures, atmosphere.
- Color scheme consistent with the concept.

The image model will also receive the visual references to improve its adherence to brand guidelines. Include instruction to take these visual references into account in the prompt.

Output should be a **ready-to-use text-to-image prompt** in natural language.