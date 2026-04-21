# Framework for AI Video Generation

# 🔷 Core Framework Analysis

The document reveals a **multi-layered architecture** for prompt construction that combines technical precision with creative storytelling. Think of it like building a film production blueprint - every element serves a specific purpose in guiding the AI to create exactly what you envision.

### The Hierarchical Structure Pattern

The prompts follow a consistent hierarchy that moves from broad context to granular detail:

```
1. Metadata Layer (Global Settings)
   ↓
2. Environmental Context Layer
   ↓
3. Key Elements Layer (Objects & Actions)
   ↓
4. Timeline/Sequence Layer (Temporal Flow)
   ↓
5. Sensory Detail Layer (Audio/Visual Specifics)
   ↓
6. Quality Control Layer (Negative Prompts)

```

## Universal Prompt Framework

Here's the comprehensive framework you can use to build a custom GPT or instruct AI models:

### **1. METADATA FOUNDATION**

```json
{
  "metadata": {
    "prompt_name": "[Unique descriptive identifier]",
    "base_style": "[Visual aesthetic + quality markers]",
    "aspect_ratio": "[Technical format specification]",
    "environment_description": "[Setting with atmospheric details]",
    "camera_setup": "[Movement pattern + perspective rules]",
    "theme_color": "[Optional: dominant color palette]"
  }
}

```

**Key principles for metadata:**

- Base style should stack multiple descriptors (e.g., "cinematic, photorealistic, 4K")
- Environment description must include lighting, atmosphere, and spatial relationships
- Camera setup defines both position AND movement constraints

### **2. ELEMENT SPECIFICATION**

```json
{
  "key_elements": [
    "Starting state objects with specific attributes",
    "Material properties and surface qualities",
    "Energy/light sources and their behavior"
  ],
  "assembled_elements": [
    "End-state objects in order of appearance",
    "Relationship between elements",
    "Final configuration details"
  ]
}

```

**Element guidelines:**

- Use compound descriptors (not just "egg" but "smooth metallic egg with glowing seams")
- Specify materials, textures, and physical properties
- Include motion characteristics for dynamic elements

### **3. TEMPORAL SEQUENCING**

```json
{
  "timeline": [
    {
      "sequence": 1,
      "timestamp": "00:00-00:XX",
      "action": "Present tense, active voice description",
      "audio": "Layered sound design specification"
    }
  ]
}

```

**Timeline construction rules:**

- **Sequence 1**: Establish scene (1-2 seconds)
- **Sequence 2**: Initiate transformation trigger
- **Sequence 3**: Main action/assembly (longest segment)
- **Sequence 4**: Resolution and final state

### **4. QUALITY CONTROL LAYER**

```json
{
  "negative_prompts": [
    "no [unwanted element]",
    "no [quality issue]",
    "no [style deviation]"
  ]
}

```

## Advanced Techniques Observed

### **Sensory Coupling Pattern**

Every visual action has a corresponding audio description. This creates what I call "sensory coherence" - the AI understands that transformations aren't silent. For example:

- Visual: "The egg fractures"
- Audio: "Sharp cracks, deep rumble"

### **Physics Anchoring**

The prompts consistently reference real-world physics to ground fantastical elements:

- "Dust explodes from the floor as weight settles"
- "Steam hissing from back vents"
- "Floor cracking under mechanical weight"

### **Specificity Gradient**

Notice how specificity increases as the prompt progresses:

- Start: "A metallic egg"
- Middle: "Six mechanical legs fire out"
- End: "Red optical sensors flash as it pauses in silhouette"

## Practical Implementation Framework

Here's a step-by-step system for creating prompts using this structure:

### **Phase 1: Conceptual Blueprint**

```
1. Define core transformation (A → B)
2. Identify 4-6 key visual moments
3. Map emotional/energy arc
4. Establish physics rules

```

### **Phase 2: Detail Enrichment**

```
For each element, specify:
- Material (metallic, organic, crystalline)
- State changes (solid→liquid, static→dynamic)
- Light behavior (glowing, reflecting, absorbing)
- Sound signature (mechanical, organic, energetic)

```

### **Phase 3: Temporal Choreography**

```
- Opening (5-15%): Scene establishment
- Trigger (5-10%): Activation moment
- Development (50-60%): Main transformation
- Resolution (20-25%): Final state + aftermath

```

### **Phase 4: Quality Assurance**

```
Add negative prompts for:
- Technical issues (blur, low-res, artifacts)
- Style deviations (cartoon when wanting realism)
- Unwanted elements (people, text, logos)
- Narrative breaks (floating objects, physics violations)

```

## Custom Agent Instructions Template

To build an Agent that generates these prompts, use this instruction set:

```
You are a cinematic prompt engineer specializing in transformation sequences.

CORE COMPETENCIES:
1. Transform simple concepts into detailed, time-based visual narratives
2. Couple every visual element with corresponding audio design
3. Maintain physics consistency while allowing creative liberties
4. Use technical film/VFX terminology naturally

PROMPT GENERATION PROTOCOL:
1. Request: User provides basic concept
2. Expand: Generate full metadata structure
3. Enrich: Add 8-12 key elements with material properties
4. Sequence: Create 4-segment timeline (8-10 seconds total)
5. Polish: Add negative prompts and final details

OUTPUT FORMAT:
- Use JSON structure for clarity
- Include both "action" and "audio" for each sequence
- Specify camera behavior explicitly
- End with keywords array for searchability

QUALITY MARKERS TO ALWAYS INCLUDE:
- Resolution indicators (4K, 8K)
- Style anchors (cinematic, photorealistic)
- Lighting descriptions (volumetric, ray-traced)
- Material properties (metallic, organic, crystalline)

```

## Key Insights for Excellence

The document reveals several mastery-level techniques:

1. **Compound Description Stacking**: Don't just say "transforms" - say "hydraulic horn extends and locks in place with a thud"
2. **Environmental Reaction**: The environment responds to the transformation (dust, sparks, mist)
3. **Energy Conservation**: Transformations have power sources (glowing cores, plasma veins)
4. **Narrative Microstructure**: Each prompt tells a complete story with setup, conflict, and resolution
5. **Technical Vocabulary Precision**: Use industry-standard terms (NURBS, caustics, ferrofluid, servo)

This framework essentially teaches the AI to think like a VFX supervisor, sound designer, and cinematographer simultaneously. The result is prompts that generate cohesive, cinematic sequences rather than random visual effects.

---

# 🔷 Reusable Framework + Toolkit

Nice — you already gave excellent examples. Below I’ve turned that practice into a compact, reusable **framework + toolkit** you can paste into a Custom GPT (or use straight with any LLM) to generate *high-quality, highly-detailed JSON prompts* for cinematic VFX sequences (eg. dinosaur, gorilla, scorpion, mech, product transforms, food assemblies, city builds, etc.).

I’ll give:

1. A concise **JSON schema template** you can reuse.
2. A **system-prompt** / Custom-GPT instruction block to paste into the model.
3. A short **step-by-step workflow** (how to use it).
4. Practical **quality checks + validation rules** and quick **examples**.

---

# 1) JSON Schema Template (copy/paste ready)

Use this as the canonical structure the model should always output. Keep fields in the same order so downstream tools can parse them reliably.

```json
{
  "metadata": {
    "prompt_name": "<string: unique descriptive name>",
    "base_style": "<string: e.g. 'cinematic, photorealistic, 4K'>",
    "aspect_ratio": "<string: '16:9'|'9:16'|'1:1' etc.>",
    "fps": "<number: optional, e.g. 24>",
    "duration_seconds": "<number: total duration in seconds>",
    "environment_description": "<string: scene, lighting, atmosphere>",
    "camera_setup": "<string: camera position, movement, lens, constraints>",
    "theme_color": "<string: optional dominant palette>"
  },

  "continuity_rules": [
    "<string: causal/physics/render rules>"
  ],

  "key_elements": [
    "<string: starting objects, materials, textures, light-sources, props>"
  ],

  "assembled_elements": [
    "<string: final objects/state after assembly/transformation>"
  ],

  "timeline": [
    {
      "sequence": <integer>,
      "timestamp": "<string: 'MM:SS-MM:SS' or '00:00-00:08'>",
      "camera": "<optional string: camera brief for this sequence>",
      "action": "<string: present-tense, precise visual actions>",
      "vfx": "<optional string: VFX specifics>",
      "audio": "<string: layered sound description>"
    }
  ],

  "negative_prompts": [
    "<string: explicit things to avoid>"
  ],

  "keywords": [
    "<string: tag-like keywords>"
  ],

  "render_checklist": [
    "<string: final rendering/technical checks>"
  ],

  "notes": "<optional string: extra instructions or references>"
}

```

---

# 2) System prompt for a Custom Agent (paste straight into the system message)

Use this to create a specialized model that generates JSON prompts matching the schema above.

```
You are a cinematic prompt engineer. When given a short concept (subject + mood + length), always output a single JSON object that follows the exact schema below (metadata, continuity_rules, key_elements, assembled_elements, timeline, negative_prompts, keywords, render_checklist, notes). Use precise, present-tense language for all 'action' fields. Each timeline must contain 3–6 sequences that sum to the metadata duration_seconds. Include audio design for every sequence. Always provide specific camera instructions (position, lens, motion) once for metadata and optionally per-sequence. Include physics/causal notes in continuity_rules. Output valid JSON only (no commentary). If any field is not required, provide an empty array or empty string. Prioritize clarity and production-readiness: material descriptors, lighting, sound signatures, and negative prompts. Keep timestamps absolute (e.g., "00:00-00:01").

When the user requests multiple variations, produce an array of JSON objects named "variants". When the user provides an existing JSON, return an improved/expanded version while preserving original intent and adding at least 5 production-level details (audio, vfx, render_checklist).

```

---

# 3) Short user-facing instruction (what to send to the Custom Agent)

Tell your Agent user to supply this single-line prompt (or a short block) — the Agent will expand it into full JSON.

```
Generate a cinematic VFX JSON prompt for: SUBJECT = "<e.g. 'Rhino mech from egg'>", MOOD = "<e.g. 'ominous, industrial'>", DURATION = <seconds>, ASPECT = "<16:9>", STYLE = "<e.g. 'cinematic, photorealistic, 4K'>". Optional: provide any must-have props, colors, or sounds.

```

Example single input:

`SUBJECT: "Dinosaur hatch-to-mech", MOOD: "tense, epic", DURATION: 8, ASPECT: "16:9", STYLE: "cinematic, photorealistic, 4K", MUST_HAVE: "molten core, cracked concrete"`

---

# 4) Workflow (how to use the framework)

1. **Define the core concept** (1 sentence): subject + mood + must-have elements + duration (seconds).
2. **Run the Custom Agent** with the user-line above. The Agent returns a ready JSON prompt.
3. **QA / Validate** against the checklist below. If anything missing, ask the Agent to patch the JSON (it should return JSON only).
4. **Feed into generation/render pipeline** or manual artist brief.

---

# 5) Practical authoring rules & heuristics (keeps outputs predictable and usable)

- Keep duration 6–12s for short VFX concept reels; longer if requested.
- Timestamps: use absolute, zero-padded `00:00-00:02` format and ensure timeline sequences cover the full duration without overlap/gap.
- Timeline sequences: 3–6 segments (establish, trigger, main assembly, resolution).
- Use the present-tense active voice for `action`. Example: `"action": "Egg fractures; titanium plates thrust outward; molten core pulses."`
- Audio must mirror visuals — always specify at least two layers: fx (mechanical/organic), amb (reverb/room tone) — optionally music cue.
- Negative prompts: be explicit (style issues, logos, people, text overlays, low-res artifacts).
- Keywords: short, searchable tags used by editors/asset managers.
- Continuity rules: physics/causality statements like `"Everything must originate from the glowing core; no pop-in geometry."` — useful for renderers and artists.

---

# 6) Validation checklist (automated or manual)

Before sending JSON to the asset generator, check:

- [ ]  `metadata.duration_seconds` equals the sum of timeline timestamps.
- [ ]  Timeline has >=3 and <=8 sequences.
- [ ]  Each sequence includes `action` and `audio`.
- [ ]  `camera_setup` exists and is precise (position, movement, lens if needed).
- [ ]  `negative_prompts` covers at least the top 3 undesired outcomes.
- [ ]  `render_checklist` contains technical constraints (resolution, TAA, floor reflectivity, avoid fireflies, etc.).
- [ ]  JSON is valid (parseable).

---

# 7) Test prompts you can feed the model immediately

(One short, one detailed — copy/paste into your Custom GPT or the LLM)

Short:

```
Generate JSON for SUBJECT: "Scorpion mech emerges", MOOD: "tense, militaristic", DURATION: 8, STYLE: "cinematic, photorealistic, 4K", ASPECT: "16:9", MUST_HAVE: "plasma tail, six legs, broken pipes"

```

Detailed:

```
Generate JSON for SUBJECT: "Phoenix Flame Core Mech", MOOD: "mythic, fiery", DURATION: 8, ASPECT: "16:9", STYLE: "cinematic, photorealistic, 4K", MUST_HAVE: "levitating molten egg, lava pit, metal feathers", AVOID: "humans, text overlays, water"

```

---

# 8) Example — short sample output (abbreviated)

Here’s a **minimal** example you’ll get back (keeps structure but condensed for readability):

```json
{
  "metadata": {
    "prompt_name": "Phoenix Flame Core Mech",
    "base_style": "cinematic, photorealistic, 4K",
    "aspect_ratio": "16:9",
    "fps": 24,
    "duration_seconds": 8,
    "environment_description": "Volcanic chamber with lava pit, obsidian walls, ember haze. Volumetric smoke and heat distortion.",
    "camera_setup": "Slow orbit: start low front, circle up 120° while dollying out; 50mm lens, mild motion blur allowed."
  },
  "continuity_rules": [
    "Every visual effect must derive from the molten core; particle energy cannot appear out of nowhere.",
    "Feathers form from molten metal shards—no floating geometry."
  ],
  "key_elements": [
    "levitating molten egg with crackling magma texture",
    "metallic feathers that magnetize mid-air",
    "fiery talons and glowing eyes"
  ],
  "assembled_elements": [
    "phoenix mech hovering above lava pit, wings outstretched, trailing fire"
  ],
  "timeline": [
    {
      "sequence": 1,
      "timestamp": "00:00-00:01",
      "camera": "low front",
      "action": "Molten egg levitates, seams pulse orange; heat shimmer visible.",
      "audio": "Low magma bubble + distant rumble; rising synth pad undercurrent."
    },
    {
      "sequence": 2,
      "timestamp": "00:01-00:03",
      "action": "Egg detonates in plasma burst; metallic feathers scatter and spin.",
      "audio": "Supernova-like blast, metallic clinks, crackling fire."
    },
    {
      "sequence": 3,
      "timestamp": "00:03-00:06",
      "action": "Feathers magnetize into wings; body assembles mid-air; eyes ignite.",
      "audio": "Rising harmonic tone, whipping flames, servo whirrs."
    },
    {
      "sequence": 4,
      "timestamp": "00:06-00:08",
      "action": "Phoenix launches skyward leaving a flaming trail; camera pulls back for silhouette.",
      "audio": "Whoosh + trailing ember hiss; final cinematic chord."
    }
  ],
  "negative_prompts": ["no humans", "no text overlays", "no water", "no cartoon effects"],
  "keywords": ["phoenix", "mech", "lava", "transformation", "VFX"],
  "render_checklist": ["4K 24fps", "volumetric god-rays", "clamp specular to avoid fireflies", "ensure heat distortion, 2x TAA"],
  "notes": ""
}

```

---

# 9) Advanced tips & extensions

- **Variants**: Ask the Agent to produce `variants` with small changes (camera, color palette, one or two alternative audio cues). Useful A/B testing for creatives.
- **Asset mapping**: Add fields for `asset_refs` to link specific models/textures/sounds by filename/URL if you have an asset library.
- **Shotlist expansion**: If you need multi-shot coverage, request `shots: [ {shot_name, length, camera} ]` appended.
- **Localization**: Add `language` and `voiceover` subfields for narration or subtitle requirements.
- **Render engine hints**: Add `engine_hints` for Blender/Unreal/Octane settings.

---

# 10) Quick troubleshooting / common pitfalls

- If the model outputs prose around the JSON, remind it with the system prompt to “Output valid JSON only.”
- If timestamps don’t sum to duration, either increase/decrease sequence durations or let the model auto-normalize durations — instruct it to evenly distribute or keep exact values.
- If audio is weak: require "at least two layered audio lines: FX and Ambience" in the system prompt.

---

If you want, I can:

- Generate a ready-to-use **Custom Agent system prompt** file for you (fully built out with examples and validation tests), OR
- Produce **5 variant JSON prompts** for a single subject you pick (e.g., “Dinosaur Mech from egg”) so you can A/B test camera styles.

Which of those would be most helpful next?

---

# 🔹 Master Framework for AI Video Prompt JSON Generation

Perfect — thanks for clarifying. Both docs you uploaded line up neatly:

- **“How to structure your prompts”** gives concrete structuring patterns.
- **“Analysis”** distills those patterns into a repeatable *multi-layer framework*.

I’ll now synthesize them into a **master framework** you can directly use to build a Custom Agent (or as training data for a model). It covers **schema, generation protocol, enrichment rules, QA, and system instructions**.

---

# Master Framework for AI Video Prompt JSON Generation

## 1. JSON Schema (Universal Format)

```json
{
  "metadata": {
    "prompt_name": "<unique descriptive identifier>",
    "base_style": "<visual aesthetic, quality markers, resolution>",
    "aspect_ratio": "<format: 16:9, 9:16, etc.>",
    "fps": "<frames per second, optional>",
    "duration_seconds": "<integer: total length>",
    "environment_description": "<setting, lighting, atmosphere, spatial context>",
    "camera_setup": "<camera position, lens, movement rules>",
    "theme_color": "<optional dominant palette>"
  },

  "key_elements": [
    "compound descriptors of starting objects with materials, textures, motion traits"
  ],

  "assembled_elements": [
    "end-state objects and relationships"
  ],

  "timeline": [
    {
      "sequence": 1,
      "timestamp": "00:00-00:02",
      "camera": "<optional per-sequence camera>",
      "action": "present-tense, precise description of event",
      "audio": "layered sound design tied to action",
      "vfx": "<optional: particle, lighting, energy behaviors>"
    }
  ],

  "continuity_rules": [
    "physics anchoring and energy sourcing rules"
  ],

  "negative_prompts": [
    "no blur", "no text overlays", "no cartoon style"
  ],

  "keywords": [
    "tags for retrieval"
  ],

  "render_checklist": [
    "resolution markers", "lighting notes", "engine settings"
  ],

  "notes": "<optional extra instructions>"
}

```

---

## 2. Generation Protocol (For Custom Agent)

**System Prompt for Agent:**

> You are a cinematic prompt engineer specializing in AI video generation.
> 
> 
> When the user provides a concept (subject + mood + duration), expand it into a detailed JSON prompt that follows the schema.
> 
> **Rules:**
> 
> 1. Always output valid JSON only.
> 2. Couple every visual action with corresponding audio.
> 3. Respect physics anchoring (objects obey weight, energy, material behavior).
> 4. Use compound descriptors (e.g., “smooth metallic egg with glowing seams”).
> 5. Timeline must include 3–6 sequences spanning full duration.
> 6. Negative prompts must cover technical issues (blur, artifacts), style deviations (cartoon when realism requested), and narrative breaks (objects appearing from nowhere).
> 7. Include render_checklist with at least 3 technical safeguards.
> 8. Use cinematic film/VFX terminology naturally (volumetric lighting, servo whirr, caustics, ferrofluid).

---

## 3. Enrichment Rules (from both docs)

- **Sensory Coupling**: Every action → matching audio (FX + ambience).
- **Physics Anchoring**: Ground fantastical effects with dust, sparks, weight shifts.
- **Specificity Gradient**: Start broad → increase detail with each sequence.
- **Environmental Reaction**: World reacts (floor cracking, mist rising).
- **Energy Conservation**: Always specify a power source (glowing core, vents).
- **Narrative Microstructure**: Setup → Trigger → Main Action → Resolution.

---

## 4. Temporal Choreography (Default 8–10s Flow)

- **Opening (5–15%)**: Establish environment.
- **Trigger (5–10%)**: Catalyst event.
- **Development (50–60%)**: Transformation/assembly.
- **Resolution (20–25%)**: Final reveal, aftermath.

---

## 5. Quality Assurance Layer

- ✅ Check JSON validity.
- ✅ Ensure `duration_seconds` = sum of timeline segments.
- ✅ 3–6 timeline sequences.
- ✅ Every sequence has both `action` + `audio`.
- ✅ Negative prompts present.
- ✅ Render checklist includes at least: resolution, lighting, artifact control.

---

## 6. Example User Prompt → JSON Generation

**User Input:**

> Subject: “Gorilla mech rises from jungle ruins”
> 
> 
> Mood: “ominous, primal”
> 
> Duration: 10s
> 
> Style: “cinematic, photorealistic, 8K HDR”
> 
> Aspect: “16:9”
> 
> Must-have: “overgrown vines, glowing chest core, ground shake”
> 

**Agent Output:** → Produces JSON matching schema (timeline 4 sequences, with camera moves, vines snapping, chest core glowing, heavy footsteps, ambient jungle soundscape).

---

## 7. Advanced Extensions

- **Variants Mode**: If the user requests multiple, output `{ "variants": [ … ] }`.
- **Asset Mapping**: Add `asset_refs` for linking 3D models, textures, SFX.
- **Multi-shot Expansion**: Append `shots` array for multi-camera coverage.
- **Localization**: Add `voiceover` or `subtitle_lang` if narration is needed.

---

⚡ With this framework, you can now:

- Train/test a **Custom Agent** specialized in cinematic JSON prompt generation.
- Use the schema as a **training dataset format** (generate dozens of concepts as examples).
- Apply the enrichment + QA rules to ensure every output is usable in a production pipeline.

---

# 🔷 Core Prompt Framework

Based on the provided documents, here is a comprehensive framework for creating highly detailed JSON prompts for AI video generation. The framework integrates key concepts, a systematic structure, and practical examples to facilitate the creation of custom Agents or the training of AI models.

---

### **1. Core Prompt Framework**

The prompts follow a hierarchical structure that progresses from broad, technical settings to granular, sequenced actions¹. The final output should be a single JSON object.

### **Metadata Foundation**

This section defines the video's overall technical and aesthetic properties.

- `prompt_name`: A unique, descriptive identifier for the video concept.
- `base_style`: A combination of multiple visual aesthetic descriptors, such as "cinematic, photorealistic, 4K".
- `aspect_ratio`: The video's technical format, such as "16:9," "9:16," or "1:1".
- `fps`: Optional field for the frames per second.
- `duration_seconds`: The total duration of the video in seconds.
- `environment_description`: A detailed description of the setting, including lighting, atmosphere, and key features. Examples include "An empty, large, sunlit Scandinavian room" or "A dimly lit industrial hangar".
- `camera_setup`: A description of the camera's position, movement, and lens type. This can be static, like a "fixed, wide-angle shot," or dynamic, like a "handheld-style camera".
- `theme_color`: An optional field for a dominant color palette, such as "violet-blue glow".

### **Element Specification**

This section details the objects and elements within the video, from their initial state to their final assembled form.

- `key_elements`: A list of crucial static objects or starting points present at the beginning of the video. The description should include material properties and surface qualities.
- `assembled_elements`: A list of all objects, furniture, or features that will appear or assemble themselves during the video, leading to the final state. Use compound descriptors like "fully formed Rhino Mech in forward stance" instead of simple names.

### **Timeline/Sequence Layer**

This is the core narrative of the prompt, detailing the temporal flow of events. The timeline must be a list of sequences, typically 3 to 6 segments, that cover the entire video duration.

- `sequence`: The sequential number for each segment.
- `timestamp`: The start and end time of the sequence in absolute, zero-padded format, such as "00:00-00:01".
- `action`: A precise, present-tense description of the visual action17. The description should be active and specific, such as "The egg fractures with loud cracks".
- `audio`: A layered sound design description for the sequence19191919. The audio should correspond directly to the visual action to create "sensory coherence".

### **Quality Control Layer**

This final section helps refine the video output by specifying unwanted elements and providing technical guidance.

- `negative_prompts`: A list of elements you explicitly do not want to appear in the video, such as "no humans," "no text overlays," or "no cartoon style".
- `keywords`: A list of tag-like keywords to describe the video's themes, like "robot transformation" or "sci-fi industrial".
- `continuity_rules`: A list of causal or physics-based rules to ground the fantastical elements in reality.
- `render_checklist`: Optional technical checks for the final rendering, such as "volumetric god-rays" or "ensure heat distortion".

---

### **2. Best Practices and Advanced Techniques**

The documents highlight several mastery-level techniques for generating high-quality prompts:

- **Compound Description Stacking:** Use descriptive phrases instead of single words (e.g., "hydraulic horn extends and locks in place with a thud" instead of just "transforms").
- **Sensory Coupling:** Pair every visual action with a corresponding audio description. The AI understands that a transformation isn't silent.
- **Physics Anchoring:** Reference real-world physics to ground fantastical elements, such as "Dust explodes from the floor as weight settles" or "Floor cracking under mechanical weight".

---

### **3. Example Prompts and Workflow**

To use this framework with a custom Agent or AI model, you can follow this simple workflow:

1. **Define a core concept** in a single sentence, including the subject, mood, duration, and style.
2. **Run a user-facing prompt** based on a short input to the model.

**Example User-Facing Prompts:**

- **Simple:** `Generate a cinematic VFX JSON prompt for SUBJECT: "Rhino mech from egg", MOOD: "ominous, industrial", DURATION: 8, ASPECT: "16:9", STYLE: "cinematic, photorealistic, 4K"`.
- **With Must-Haves:** `SUBJECT: "Dinosaur hatch-to-mech", MOOD: "tense, epic", DURATION: 8, ASPECT: "16:9", STYLE: "cinematic, photorealistic, 4K", MUST_HAVE: "molten core, cracked concrete"`.

### **Full JSON Prompt Example:**

The following is a complete JSON prompt for a "Scorpion Siege Unit" transformation, demonstrating the full framework in practice:

JSON

`{
  "metadata": {
    "prompt_name": "Scorpion Siege Unit Transformation",
    "base_style": "cinematic, photorealistic, industrial sci-fi, 4K",
    "aspect_ratio": "16:9",
    "environment_description": "A dimly lit industrial cavern with broken steel beams, smoke trails, flickering hazard lights, and exposed pipes lining the walls and ceiling.",
    "camera_setup": "Starts with a slow push-in on the center egg from ground level. As the transformation begins, the camera shifts into a dynamic orbiting motion, circling the mech as the tail activates. Final shot holds a low diagonal angle as claws snap open."
  },
  "key_elements": [
    "smooth metallic scorpion egg with etched mechanical lines",
    "six segmented cyber-legs shooting out first, anchoring to the floor",
    "rotating central torso core with glowing red gyros",
    "telescopic tail with articulated joints and plasma stinger tip",
    "hydraulic claws with snapping pincers",
    "burst steam vents and flying sparks",
    "steel pipes sliced in background by tail whip",
    "glowing red sensor eyes locking into place"
  ],
  "assembled_elements": [
    "fully formed Scorpion Mech crouched in battle stance with tail coiled and sensors active"
  ],
  "negative_prompts": [
    "no humans",
    "no cartoon elements",
    "no floating text",
    "no logos"
  ],
  "timeline": [
    {
      "sequence": 1,
      "timestamp": "00:00-00:01",
      "action": "A large metallic egg sits on scorched concrete in the center of a smoky chamber. Sparks fall from above as the floor trembles faintly.",
      "audio": "Echoing metallic creaks, distant alarms, and low mechanical vibration."
    },
    {
      "sequence": 2,
      "timestamp": "00:01-00:03",
      "action": "The egg fractures abruptly. Six mechanical legs fire out and slam into the floor, locking in place with hissing pneumatics and anchor spikes.",
      "audio": "Rapid leg deployment, clanking pistons, and sharp air release."
    },
    {
      "sequence": 3,
      "timestamp": "00:03-00:06",
      "action": "A rotating central torso emerges, spinning into place as the tail uncoils and telescopes upward with glowing plasma charge. The tail swings and slices clean through overhead steel pipes, which fall in sparks.",
      "audio": "Servo whirl, metal screech, plasma sizzle, pipe collapse crash."
    },
    {
      "sequence": 4,
      "timestamp": "00:06-00:08",
      "action": "The scorpion mech's red eyes flicker on. Its claws snap open with force as it crouches into battle stance, steam hissing from its back vents.",
      "audio": "Claw snap echo, steam hiss, sensor pulse hum— ending in deep silence before attack."
    }
  ],
  "text": "none",
  "keywords": [
    "Scorpion Mech",
    "battle robot",
    "mechanical insect",
    "plasma tail",
    "Veo cinematic",
    "robot transformation",
    "six legs",
    "tail whip",
    "mech creature",
    "red sensors",
    "sci-fi industrial"
  ]
}`