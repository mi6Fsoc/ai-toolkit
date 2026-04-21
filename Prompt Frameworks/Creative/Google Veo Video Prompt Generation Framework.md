# Google Veo Video Prompt Generation Framework

---

## Core Prompt Architecture

### Essential Elements (Always Include)

1. **Subject** - The primary focus
    - Objects, people, animals, or scenery
    - Be specific: "calico kitten" not just "cat"
    - Examples: cityscape, nature scene, vintage car, golden retriever puppy
2. **Action** - What's happening
    - Active verbs describing movement or behavior
    - Examples: walking, running, turning head, melting, gliding, prancing
    - For static subjects: "resting," "standing still," "slowly rotating"
3. **Context/Environment** - The setting
    - Where the action takes place
    - Environmental details that ground the scene
    - Examples: misty forest, sunlit beach, bustling city street, frozen rock wall

### Enhancement Elements (Add for Better Results)

1. **Style** - Creative direction
    - Film styles: cinematic, film noir, sci-fi, horror
    - Animation styles: 3D cartoon, paper cut-out, stop-motion
    - Artistic styles: photorealistic, surreal, vintage, futuristic
    - Examples: "cinematic shot," "3D cartoon style render," "film noir aesthetic"
2. **Camera Positioning** - Where the camera is
    - Aerial view, eye-level, top-down, worm's eye view
    - POV (point of view) shot, over-the-shoulder
    - Examples: "aerial drone view," "close-up eye-level shot"
3. **Camera Motion** - How the camera moves
    - Dolly shot (moving toward/away)
    - Tracking shot (following subject)
    - Pan (horizontal rotation)
    - Static (no movement)
    - Examples: "camera slowly dollies in," "tracking drone view," "static wide shot"
4. **Composition** - Shot framing
    - Wide shot, medium shot, close-up, extreme close-up
    - Single-shot, two-shot (number of subjects)
    - Rule of thirds positioning
    - Examples: "wide establishing shot," "extreme close-up of eyes"
5. **Focus & Lens Effects** - Visual techniques
    - Shallow focus, deep focus, soft focus
    - Macro lens, wide-angle lens, telephoto
    - Depth of field specifications
    - Examples: "shallow depth of field," "macro lens detail"
6. **Ambiance** - Mood through light and color
    - Color palettes: warm tones, cool blue tones, muted oranges
    - Lighting: natural light, sunrise, sunset, neon glow, candlelight
    - Time of day: dawn, midday, dusk, night
    - Weather: foggy, rainy, sunny, overcast
    - Examples: "bathed in warm golden hour light," "cool blue tones with misty atmosphere"

---

## Advanced Features

### Audio Generation

**Dialogue**

- Use quotation marks for speech
- Include speaker identification
- Format: `Character: "Exact dialogue here"`
- Example: `Man: (whispering urgently) "We need to leave now."`

**Sound Effects (SFX)**

- Explicitly describe sounds you want
- Use onomatopoeia when appropriate
- Examples: "tires screeching loudly," "engine roaring," "glass shattering"

**Ambient Noise**

- Describe environmental soundscape
- Background audio elements
- Examples: "gentle waves lapping," "city traffic humming," "wind rustling through leaves"

**Audio Prompt Template:**

```
[Visual description]. [Character name]: [Action description] "[Dialogue]" [SFX description]. [Ambient sound description].

```

### Reference Images

**When to Use:**

- Preserve specific character/person appearance
- Maintain product consistency across videos
- Reference specific visual elements or assets

**Best Practices:**

- Use up to 3 reference images
- Specify `reference_type="asset"` in API
- Generate reference images with high quality (Nano Banana recommended)
- Include detailed descriptions of how references should appear

**Prompt Structure with References:**

```
The video [action description]. [Subject with reference 1 description] [interaction with reference 2 description] [reference 3 integration]. [Camera, style, ambiance details].

```

### First & Last Frame (Interpolation)

**Use Cases:**

- Precise control over start and end compositions
- Creating specific transitions
- Ensuring exact beginning and ending frames

**Prompt Strategy:**

- Describe the transition between frames
- Include camera movement during interpolation
- Specify subject transformation or motion

### Video Extension

**Guidelines:**

- Use for continuing action from previous generation
- Finalizes from last 24 frames (1 second) of input
- Voice extension only works if present in final second
- Can extend up to 20 times (7 seconds each)

**Extension Prompt Template:**

```
Extend this video with [specific continuation action]. [Additional details about how scene evolves]. [Maintain/change camera position as needed].

```

---

## Prompt Quality Levels

### Basic (Minimum Viable)

Subject + Action + Context

```
A calico kitten sleeping in the sunshine on a windowsill.

```

### Intermediate (Good Results)

Subject + Action + Context + Style + Camera + Ambiance

```
A cinematic close-up shot of a calico kitten sleeping peacefully in the warm sunshine streaming through a cottage windowsill, with soft focus and golden afternoon light creating a dreamy atmosphere.

```

### Advanced (Exceptional Results)

All elements + Audio + Specific details + Negative prompts

```
A cinematic, intimate close-up shot slowly dollies toward a calico kitten with distinctive orange, black, and white patches sleeping peacefully in a pool of warm sunshine streaming through a rustic cottage windowsill. Shallow depth of field keeps focus on the kitten's gently rising and falling chest while the background wooden frame softly blurs. Golden afternoon light creates a dreamy, cozy atmosphere with warm honey tones throughout. Soft ambient sounds of distant birdsong and a gentle breeze rustling curtains. The camera movement is smooth and reverent, capturing the pure serenity of the moment.

Negative prompt: harsh lighting, cold tones, cluttered background, urban setting, artificial elements

```

---

## Prompt Templates by Use Case

### 1. Product Showcase

```
[Composition] shot of [product name and key features] [positioned where] in [environment]. [Camera movement] to reveal [specific product details]. [Lighting description] highlights [material/texture]. [Style] aesthetic. [Optional: product interaction or demonstration].

Example: A slow rotating 360-degree shot of a sleek silver smartwatch with a vibrant blue display positioned on a minimalist white pedestal. Camera orbits smoothly while maintaining focus on the watch face. Studio lighting with soft shadows highlights the metallic finish and curved glass. Modern, premium aesthetic with clean backgrounds.

```

### 2. Narrative/Storytelling

```
[Setting establishment]. [Character introduction with appearance]. [Character action and emotional state]. [Camera follows/reveals]. [Dialogue if applicable]. [Ambient sounds and mood]. [Plot progression or tension element].

Example: A misty Victorian London street at dusk. A woman in a dark velvet coat with auburn hair walks briskly, glancing over her shoulder nervously. The camera tracks alongside her as fog swirls around gas lamps. Woman: (voice tight with urgency) "He's following me." Distant footsteps echo on cobblestones. The camera slowly pulls back to reveal a shadowy figure emerging from the fog behind her.

```

### 3. Nature/Wildlife

```
[Camera angle and movement] of [specific animal/natural element] [action] in [detailed habitat description]. [Time of day and lighting]. [Weather conditions if relevant]. [Specific behaviors or details to capture]. [Ambient natural sounds]. [Mood/tone].

Example: A slow-motion aerial drone shot descends toward a majestic bald eagle soaring over a pristine alpine lake at sunrise. The eagle's wings catch the golden light as it glides effortlessly above mirror-like water reflecting snow-capped peaks. Crystal clear morning air, gentle mountain breeze. The camera follows the eagle's graceful descent as it skims the water surface. Serene, awe-inspiring atmosphere capturing raw natural beauty.

```

### 4. Abstract/Artistic

```
[Artistic style] video featuring [abstract subject/concept]. [Visual elements and their movements]. [Color palette]. [Composition and framing]. [Texture and material qualities]. [Rhythm or pacing]. [Emotional tone].

Example: A surreal, dream-like sequence featuring flowing ribbons of iridescent liquid gold morphing through space. The ribbons twist and spiral in slow motion against a deep indigo void, splitting and rejoining in hypnotic patterns. Vibrant metallic sheens with prismatic reflections. Centered composition with symmetrical movements. Smooth, glossy textures catching and bending light. Meditative pacing with ethereal, otherworldly atmosphere.

```

### 5. Action/Dynamic

```
[Dynamic camera movement] capturing [subject] [high-energy action] through [environment]. [Fast-paced movement description]. [Lighting and time]. [Environmental interaction/destruction]. [Sound effects]. [Intensity and mood].

Example: A high-speed tracking shot follows a parkour athlete sprinting and vaulting across urban rooftops at sunset. The camera chases inches behind as she leaps between buildings, slides under obstacles, and wall-runs with explosive momentum. Golden hour lighting creates dramatic lens flares. Her feet strike rooftop gravel with each landing, breath heavy, city traffic humming far below. Heart-pounding, adrenaline-fueled energy with cinematic action movie aesthetics.

```

### 6. Educational/Demonstration

```
[Clear camera angle] showing [subject/process] [step-by-step action]. [Lighting for visibility]. [Zoom or focus on critical details]. [Clean composition]. [Optional: text callouts or highlighting]. [Professional tone].

Example: A clean, well-lit overhead shot demonstrates the process of folding an origami crane. Hands with manicured nails carefully crease and fold crisp white paper on a wooden work surface. Camera slowly zooms in to show each precise fold. Bright, even natural lighting eliminates shadows. Each major step pauses briefly for clarity. Professional, instructional atmosphere with minimalist aesthetic.

```

### 7. Emotional/Dramatic

```
[Intimate camera work] on [character with detailed appearance] experiencing [specific emotion]. [Micro-expressions and body language]. [Environmental reflection of mood]. [Lighting supporting emotion]. [Optional dialogue expressing feeling]. [Ambient sound reinforcing mood].

Example: A slow push-in close-up captures an elderly man with weathered features and gray stubble sitting alone at a rain-streaked window. His watery blue eyes reflect the passing storm outside as a single tear rolls down his weathered cheek. Soft, diffused overcast light creates muted, melancholic tones. Distant thunder rumbles softly. Man: (barely audible whisper) "I should have said goodbye." Heavy, sorrowful atmosphere thick with regret and longing.

```

---

## Negative Prompting Strategy

### What NOT to Do

❌ Don't use instructive language: "no walls," "don't include cars"
❌ Don't use negations: "without," "excluding," "none"

### What TO Do

✅ Describe what you don't want as concrete elements
✅ List unwanted styles, objects, or qualities directly

**Effective Negative Prompt Structure:**

```
Negative prompt: [unwanted style], [unwanted objects], [unwanted lighting], [unwanted mood], [unwanted quality descriptors]

```

**Examples:**

- Good: `cartoon style, animated, low resolution, artificial lighting, cluttered background`
- Bad: `not realistic, no cartoons, don't make it look fake`

**Common Negative Prompt Categories:**

**Style Issues:**

- cartoon, drawing, animated, illustrated, sketch, painting
- low quality, blurry, pixelated, grainy, compressed
- amateur, unprofessional, poorly lit

**Aesthetic Issues:**

- cluttered, busy, chaotic, messy
- oversaturated, washed out, flat colors
- artificial, fake, synthetic

**Content Issues:**

- unwanted objects (list specifically)
- unwanted people/crowds
- unwanted weather/time of day
- man-made structures (for nature scenes)
- modern elements (for historical scenes)

**Mood Issues:**

- dark, gloomy, threatening, ominous (if wanting bright)
- cheerful, happy, bright (if wanting moody)

---

## Technical Specifications Checklist

### Model Selection

- **Veo 3.1**: Best quality, audio, reference images, interpolation, extension (Preview)
- **Veo 3.1 Fast**: Fast generation with audio, optimized for business use (Preview)
- **Veo 3**: High quality with audio (Stable)
- **Veo 3 Fast**: Fast with audio (Stable)

### Parameters to Specify

**Aspect Ratio:**

- 16:9 (widescreen) - Best for: landscapes, cinematic content, widescreen displays
- 9:16 (portrait) - Best for: mobile content, social media, vertical displays

**Resolution:**

- 720p - Standard quality, faster generation, all models
- 1080p - High quality, longer generation time (Veo 3.1 & 3 only, 8s duration only)

**Duration:**

- Veo 3.1/3: 4s, 6s, or 8s (8s required for extension/interpolation)
- Veo 2: 5s, 6s, or 8s

**Person Generation (Regional Restrictions):**

- EU/UK/CH/MENA: `allow_adult` only for Veo 3.1/3; `dont_allow` or `allow_adult` for Veo 2
- Other regions: `allow_all` for text-to-video; `allow_adult` for image-to-video

---

## Quality Optimization Strategies

### Specificity Over Generality

❌ Generic: "A person walks down a street"
✅ Specific: "A woman in her 30s with long auburn hair wearing a navy peacoat walks purposefully down a rain-slicked cobblestone street"

### Active Language

❌ Passive: "There is a sunset behind mountains"
✅ Active: "The sun descends behind jagged mountain peaks, casting long purple shadows"

### Sensory Details

- Visual: colors, textures, materials, light quality
- Audio: sounds, volume, rhythm, pitch
- Motion: speed, direction, fluidity, rhythm
- Spatial: distances, scale, positioning, depth

### Cinematic Language

Use film industry terminology:

- Shot types: establishing shot, insert shot, cutaway
- Camera moves: crane shot, steadicam, handheld
- Lighting: three-point lighting, practical lights, motivated lighting
- Editing: match cut, jump cut, dissolve (for context, not actual editing)

---

## Common Pitfalls & Solutions

### Problem: Inconsistent Results

**Solution:** Be more specific about all elements, especially subject details and camera work

### Problem: Unwanted Elements Appear

**Solution:** Use negative prompts listing specific unwanted items (not negation words)

### Problem: Audio Doesn't Match

**Solution:**

- Place audio cues in proper context within prompt
- Use quotation marks for dialogue
- Explicitly describe sound effects
- Don't rely on implicit audio generation

### Problem: Action Unclear or Wrong

**Solution:**

- Use stronger, more specific action verbs
- Describe the motion's quality (smooth, jerky, rapid, gradual)
- Include beginning and end states of motion

### Problem: Wrong Mood/Atmosphere

**Solution:**

- Be explicit about emotional tone
- Use ambiance keywords (lighting + color + weather)
- Include atmospheric sound descriptions

### Problem: Extension Doesn't Continue Well

**Solution:**

- Ensure original video ends with action that can continue
- Describe continuation that logically follows
- Consider that last 1 second determines extension starting point

---

## Prompt Construction Workflow

### Step 1: Define Core Concept (30 seconds)

- What is the main subject?
- What is happening?
- Where is this taking place?

### Step 2: Choose Style & Mood (30 seconds)

- What aesthetic are you going for?
- What emotion should it evoke?
- What time period or genre?

### Step 3: Plan Camera Work (30 seconds)

- Where should the camera be?
- Should it move? How?
- What should be in/out of focus?

### Step 4: Add Audio (if Veo 3+) (30 seconds)

- What should we hear?
- Any dialogue?
- Ambient sounds?

### Step 5: Enhance with Details (60 seconds)

- Add specific descriptors for subject
- Include lighting/color palette
- Specify composition choices
- Add texture and material details

### Step 6: Negative Prompting (30 seconds)

- List unwanted styles
- List unwanted objects
- List unwanted qualities

### Step 7: Technical Setup (30 seconds)

- Choose aspect ratio
- Set resolution
- Set duration
- Configure person generation

---

## Example Transformations

### From Basic to Advanced

**User Request:** "A dog playing in a park"

**Basic Prompt:**

```
A golden retriever playing fetch in a park.

```

**Enhanced Prompt:**

```
A wide establishing shot of an energetic golden retriever with a flowing golden coat bounding joyfully across a sun-drenched meadow in a sprawling city park. The dog leaps athletically to catch a bright orange frisbee mid-air, ears flapping in the breeze. Camera tracks smoothly alongside the dog's movement. Late afternoon golden hour light creates long shadows on lush green grass dotted with wildflowers. Soft ambient sounds of distant children playing, birds chirping, and the dog's excited panting. Joyful, carefree summer atmosphere with warm honey tones throughout. Shallow depth of field keeps focus on the dog while bokeh highlights sparkle in the background.

Negative prompt: urban clutter, harsh shadows, overcast, artificial elements, crowds of people

```

---

## Integration Instructions for AI Tools

### For Custom GPTs:

```
When user requests a video prompt, follow this sequence:
1. Ask clarifying questions about subject, action, and mood
2. Determine which Veo model fits their needs
3. Construct prompt using framework elements
4. Include negative prompts automatically
5. Suggest technical parameters
6. Offer 2-3 variations with different styles

```

### For Claude Projects:

```
System Instructions:
- Use this framework as reference for all video prompt generation
- Always provide both basic and advanced prompt versions
- Explain which framework elements you're using and why
- Suggest improvements based on user's goals
- Remember user preferences for style/mood across conversation

```

### For Automation Tools:

```
Input Required:
- subject: [string]
- action: [string]
- environment: [string]
- style: [string, optional]
- mood: [string, optional]
- audio: [boolean]
- model: [veo-3.1|veo-3.1-fast|veo-3|veo-3-fast|veo-2]

Output Format:
{
  "prompt": "full constructed prompt",
  "negative_prompt": "negative prompt string",
  "parameters": {
    "aspect_ratio": "16:9|9:16",
    "resolution": "720p|1080p",
    "duration": 8,
    "person_generation": "allow_all|allow_adult|dont_allow"
  }
}

```

---

## Quick Reference Card

**Minimum Elements:** Subject + Action + Context
**Optimal Elements:** Subject + Action + Context + Style + Camera + Composition + Ambiance
**With Audio (Veo 3+):** + Dialogue + SFX + Ambient Sound
**Advanced (Veo 3.1):** + Reference Images OR First/Last Frame OR Video Extension

**Prompt Length:**

- Minimum: 15-20 words
- Optimal: 50-100 words
- Maximum: ~200 words (1024 tokens)

**Remember:**

- Be specific, not generic
- Use active language
- Include sensory details
- Negative prompts = list unwanted items (no negation words)
- Audio cues in quotation marks for dialogue
- Technical params match your use case

**Test & Iterate:**

- Generate with basic prompt first
- Add detail progressively
- Compare results
- Refine based on output

---