# Magnific Spaces — Step-by-Step Instruction Manual
### Women's Health Content Pipeline

---

## Before You Start: What You'll Be Building

You are building **four Spaces** in Magnific. Think of each Space as a workstation:

- **Space A** writes the script
- **Space B** designs the opening visual hook
- **Space C** locks the visual rules for the whole video
- **Space D** generates every clip

You build each Space once. After that, every new video just needs you to swap in a new brief and run again — all the wiring stays in place.

You will also build one extra Space called **Space E** — a repair station for fixing clips that don't look right. Build it once and only use it when you need it.

**Total time to build all five Spaces for the first time:** approximately 2–3 hours.
**Time to run them for each new video after that:** approximately 30–60 minutes of active work (plus generation wait times).

---

## What You Need Before You Start

Before opening Magnific, gather the following. You will need these on every production:

1. **Avatar Master Reference Image** — the approved still of the avatar's face and appearance. Save this to your desktop so you can find it quickly.
2. **Avatar Character Sheet** — the document describing the avatar's appearance, wardrobe, and voice in detail.
3. **The system prompts** from the Build Guide — you will copy and paste these into the Assistant nodes. Keep that document open in a separate tab.

---

## How Magnific Spaces Works — A Plain-English Explanation

A **Space** is a canvas — a blank page where you place boxes called **nodes**. Each node does one specific job. You connect nodes together with lines (called **wires**) so that the output of one node flows into the input of the next.

There are a few node types you will use throughout this pipeline:

| Node type | What it does |
|---|---|
| **Upload** | Brings an image file (like your Master Reference Image) into the Space so other nodes can use it |
| **Text** | Holds written content — either your brief, or a locked output from an AI node |
| **Assistant** | An AI brain (Claude). You give it a system prompt (instructions) and it processes whatever text is wired into it |
| **Image Generator** | Takes a text prompt and a reference image and generates a still image |
| **Video Generator** | Takes a still image and a motion prompt and generates a short video clip |

**How to add a node:** Right-click anywhere on the blank canvas → a menu appears → click the node type you want.

**How to wire two nodes together:** Hover over the right edge of a node until you see a small dot (the output port). Click and drag from that dot to the left edge of the next node (the input port). A line will appear connecting them.

**How to label a node:** Double-click the node's title bar and type a new name.

---

# PART 1 — BUILDING SPACE A (SCRIPTING)

Space A is where every video begins. It takes a brief you write and produces a complete script, broken into 8-second chunks.

---

### Step 1 — Open Magnific and create a new Space

1. Log in to Magnific at magnific.ai
2. Click **Spaces** in the left sidebar
3. Click **New Space**
4. Name it: `Space A — Scripting`

---

### Step 2 — Add the Text node: Production Brief

1. Right-click on the blank canvas
2. Select **Text** from the menu
3. A text box appears on the canvas
4. Double-click the title bar and rename it: `Production Brief`
5. Click inside the text area and type the following template exactly — you will fill in the brackets each time you start a new video:

```
AVATAR: [Name + one-line description matching Character Sheet]
PERSONA: [e.g. PCOS insulin resistance / Endometriosis pain / Perimenopause sleep disruption / Fertility TTC / RED-S athletic underfuelling]
VIDEO TYPE: [Type 1 / Type 2 / Type 3 / Type 4]
LENGTH: [15s / 30s / 45s / 60s / 90s / 120s]
```

Leave the brackets in place for now. You will replace them when you run a production.

---

### Step 3 — Add the Assistant node: Script Generator

1. Right-click on the canvas to the right of the Production Brief node
2. Select **Assistant** from the menu
3. Double-click the title bar and rename it: `Script Generator`
4. In the model selector, choose **Claude**
5. Find the **System Prompt** field inside the node (usually at the top or accessible via a settings icon)
6. Open the Build Guide document and find the section **"Assistant Node: Script Generator — System prompt"**
7. Select all of that text (from the first line through to the last line of the output format instructions) and copy it
8. Paste it into the System Prompt field of the Assistant node
9. Close the system prompt field

---

### Step 4 — Add the Text node: Script Output

1. Right-click on the canvas to the right of the Assistant node
2. Select **Text**
3. Rename it: `Script Output — Locked`
4. Leave this node empty — it will be filled by the Assistant node when you run the Space

---

### Step 5 — Wire the nodes together

1. Hover over the right edge of the **Production Brief** Text node until you see a small dot appear
2. Click and drag from that dot to the left edge of the **Script Generator** Assistant node → a wire appears
3. Hover over the right edge of the **Script Generator** node
4. Click and drag from that dot to the left edge of the **Script Output — Locked** Text node → a wire appears

Your canvas now has three connected nodes in a row:
`Production Brief → Script Generator → Script Output — Locked`

---

### Step 6 — Test Space A

1. Fill in the Production Brief node with real values (pick any avatar and persona for testing)
2. Click the **Run** button (usually at the top right of the canvas, or on the Assistant node itself)
3. Wait for the Assistant to generate
4. Check the Script Output node — it should now contain a complete script broken into numbered chunks with VOICEOVER and VISUAL DIRECTION per chunk
5. If the output looks correct, Space A is working

**Save the Space** by clicking the save icon or pressing Cmd/Ctrl + S.

---

# PART 2 — BUILDING SPACE B (HOOK GENERATION)

Space B takes the first line of the script and generates the opening visual hook — a still image and a short motion clip.

---

### Step 7 — Create Space B

1. In the Spaces sidebar, click **New Space**
2. Name it: `Space B — Hook Generation`

---

### Step 8 — Add the Upload node: Master Reference Image

1. Right-click on the canvas
2. Select **Upload**
3. Rename it: `[AVATAR NAME] — Master Reference`
4. Click the upload button inside the node and select the avatar's Master Reference Image from your desktop
5. The image appears as a thumbnail inside the node

---

### Step 9 — Add the Text node: Hook Brief

1. Right-click on the canvas below the Upload node
2. Select **Text**
3. Rename it: `Hook Brief`
4. Type the following template into the text area:

```
FIRST LINE: [Paste the exact opening line from Space A script output]
PERSONA: [PCOS / Fertility / Endometriosis / Perimenopause / RED-S / TCM-Holistic]
VIDEO TYPE: [Type 1 / 2 / 3 / 4]
VARIANTS: [1 or 3]
```

---

### Step 10 — Add the Assistant node: Hook Generator

1. Right-click on the canvas to the right of the Hook Brief node
2. Select **Assistant**
3. Rename it: `Hook Generator`
4. Set the model to **Claude**
5. Open the system prompt field
6. Find the section **"Assistant Node: Hook Generator — System prompt"** in the Build Guide
7. Copy the entire system prompt and paste it in
8. Close the system prompt field

---

### Step 11 — Add the Image Generator node

1. Right-click on the canvas below and to the right of the Hook Generator
2. Select **Image Generator**
3. Rename it: `Image Generator — Hook`
4. Set the aspect ratio to **9:16**
5. Set outputs per run to **4**

---

### Step 12 — Add the Video Generator node

1. Right-click on the canvas to the right of the Image Generator
2. Select **Video Generator**
3. Rename it: `Video Generator — Hook`
4. Set duration to **8 seconds**
5. Set aspect ratio to **9:16**

---

### Step 13 — Wire Space B

Connect the nodes in this order:

1. **Upload (Master Reference)** → **Image Generator** (connect to the Reference input port, not the Prompt port — look for a port labelled "Reference" or with an image icon)
2. **Hook Brief** → **Hook Generator** (connect to the prompt input)
3. **Hook Generator** → **Image Generator** (connect to the Prompt input — look for a port labelled "Prompt" or with a text icon)
4. **Image Generator** → **Video Generator** (connect to the Start Frame input)
5. **Hook Generator** → **Video Generator** (connect to the Motion Prompt input — this is a second wire from the Hook Generator)

> **Note on step 5:** The Hook Generator produces two outputs — a START_FRAME prompt and a MOTION prompt. If Magnific shows separate output ports for each, wire them individually. If it outputs everything as one block of text, you may need to manually copy the MOTION section into a separate Text node and wire that Text node to the Video Generator instead. Check the output after your first run to see which approach is needed.

---

### Step 14 — Test Space B

1. Fill in the Hook Brief node with values from your Space A test script
2. Run the Space
3. Check that the Image Generator produces a still image
4. **Do not run the Video Generator yet** — first look at the still. Does it look right? Does it match the avatar? Does it pass the Mute Test (does it communicate something worth stopping for, without sound)?
5. If the still looks right, click Run on the Video Generator
6. If the still doesn't look right, re-run the Image Generator to get a new set of outputs and browse until you find one that works

**Save the Space.**

---

# PART 3 — BUILDING SPACE C (VSD BUILDER)

Space C generates the Visual Style Document — the locked set of visual rules that every clip in the video must follow. You run this once per video before starting clip production.

---

### Step 15 — Create Space C

1. Click **New Space**
2. Name it: `Space C — VSD Builder`

---

### Step 16 — Add the Upload node

Same as before: Upload → Master Reference Image → label it with the avatar name.

---

### Step 17 — Add two Text nodes for inputs

**Text node 1:**
1. Right-click → **Text**
2. Rename: `Avatar + Environment Brief`
3. Type this template:

```
AVATAR NAME: [Name]
ARCHETYPE: [e.g. Trusted Friend Educator / Modern Fertility Science Expert / TCM Holistic Wisdom Figure]
VIDEO TYPE: [Type 1 / 2 / 3 / 4]
CLIP COUNT: [Total number of 8-second chunks]
ENVIRONMENT: [e.g. bright modern kitchen / rustic lived-in kitchen / clinical-adjacent office]
WARDROBE: [Full description from Character Sheet]
```

**Text node 2:**
1. Right-click → **Text**
2. Rename: `Script Chunks from Space A`
3. Leave this empty for now — you will paste the full Space A script output here when running a production

---

### Step 18 — Add the Assistant node: VSD Generator

1. Right-click → **Assistant**
2. Rename: `VSD Generator`
3. Set model to **Claude**
4. Open the system prompt field
5. Find **"Assistant Node: VSD Generator — System prompt"** in the Build Guide
6. Copy and paste the full system prompt in
7. Close the system prompt field

---

### Step 19 — Add the locked output Text node

1. Right-click → **Text**
2. Rename: `VSD LOCK — [AVATAR NAME] — [TOPIC]`
3. Leave empty — filled by the VSD Generator when you run

> **This is the most important node in the whole pipeline.** Its output will be wired to every Image Generator and Video Generator in Space D. It is the single source of truth for how every clip looks.

---

### Step 20 — Wire Space C

1. **Avatar + Environment Brief** → **VSD Generator**
2. **Script Chunks from Space A** → **VSD Generator**
3. **Upload (Master Reference)** → **VSD Generator** (as a reference input)
4. **VSD Generator** → **VSD LOCK Text node**

---

### Step 21 — Test Space C

1. Fill in the Avatar + Environment Brief node
2. Paste your Space A test script into the Script Chunks node
3. Run the Space
4. Check the VSD LOCK node — it should contain a fully filled-out Visual Style Document with no blank fields
5. Read through it. Does every section make sense for the avatar? Are all fields filled with specific values (not generic placeholders)?

**Save the Space.**

---

# PART 4 — BUILDING SPACE D (CHUNK PRODUCTION)

Space D is the main production canvas. You will build one chain of nodes per clip. For a 45-second video with 5–6 clips, you will have 5–6 identical chains running in parallel.

**Build one chain first and test it completely before duplicating it for the rest of the clips.**

---

### Step 22 — Create Space D

1. Click **New Space**
2. Name it: `Space D — Chunk Production`

---

### Step 23 — Pin the VSD LOCK node

Before building anything else, bring in the VSD from Space C.

1. Open Space C
2. Find the **VSD LOCK** Text node
3. Look for a **Share** or **Export** option on the node, or check if Magnific allows you to reference a node from another Space
4. **If cross-Space wiring is available:** Wire the VSD LOCK output directly into Space D — it will appear as a reference node
5. **If cross-Space wiring is not available:** After running Space C for each video, copy the full VSD text output and paste it into a new Text node at the top-left of Space D. Label it `VSD LOCK — [AVATAR NAME] — [TOPIC]` and treat it as pinned

Wire this VSD LOCK node's output to **every** Image Generator and Video Generator you build in this Space.

---

### Step 24 — Build Clip 01 chain

**Add Upload node 1 — Master Reference Image:**
1. Right-click → **Upload**
2. Rename: `Master Reference`
3. Upload the avatar's Master Reference Image

**Add Text node — Chunk 01 Brief:**
1. Right-click → **Text**
2. Rename: `Chunk 01 Brief`
3. Type this template and fill in the values from your Space A script output:

```
CHUNK: 01
TIMESTAMP: 00:00–00:08
VOICEOVER: [Paste exact spoken text from Space A Chunk 01]
VISUAL DIRECTION: [Paste visual direction from Space A Chunk 01]
AVATAR: [AVATAR NAME] — Master Reference Image and Character Sheet attached. Match VSD Avatar Identity Lock exactly.
```

**Add the Compliance Gate Assistant node:**
1. Right-click → **Assistant**
2. Rename: `Compliance Gate — Clip 01`
3. Set model to **Claude**
4. Open the system prompt field
5. Find **"Assistant Node: Compliance Gate — System prompt"** in the Build Guide
6. Copy and paste it in
7. Close the system prompt field

**Add the Image Generator:**
1. Right-click → **Image Generator**
2. Rename: `Image Generator — Clip 01`
3. Set aspect ratio to **9:16**
4. Set outputs per run to **4**

**Add the Video Generator:**
1. Right-click → **Video Generator**
2. Rename: `Video Generator — Clip 01`
3. Set duration to **8 seconds**
4. Set aspect ratio to **9:16**

---

### Step 25 — Wire Clip 01 chain

1. **Chunk 01 Brief** → **Compliance Gate — Clip 01**
2. **Compliance Gate — Clip 01** → **Image Generator — Clip 01** (Prompt input)
3. **Master Reference (Upload)** → **Image Generator — Clip 01** (Reference input)
4. **VSD LOCK** → **Image Generator — Clip 01** (Style/Reference input — look for a secondary reference port)
5. **Image Generator — Clip 01** → **Video Generator — Clip 01** (Start Frame input)
6. **Compliance Gate — Clip 01** → **Video Generator — Clip 01** (Motion Prompt input)
7. **VSD LOCK** → **Video Generator — Clip 01** (Style/Reference input)

---

### Step 26 — Test Clip 01

1. Paste your test script values into Chunk 01 Brief
2. Run the chain
3. Check the Compliance Gate output — is the prompt clean and compliant?
4. Check the Image Generator — browse the 4 outputs. Does the avatar match the VSD? Does the expression match the beat (before the line, not during it)?
5. **Do not run the Video Generator yet.** Only run it after approving the still.
6. Once the still is approved, run the Video Generator
7. Watch the 8-second clip. Does it look right?

If yes — **save the Space** and proceed to Step 27.
If the still drifts (wrong skin tone, wrong hair, wrong wardrobe) — **stop and go to Space E** (built in Part 5 below) before continuing.

---

### Step 27 — Add Upload node for Clip 01 approved still

After approving the Clip 01 still:

1. Download the approved still to your desktop
2. Right-click on the Space D canvas → **Upload**
3. Rename it: `Approved Still — Clip 01`
4. Upload the downloaded still

This node will be the reference input for Clip 02's Image Generator. This is the Seed Reference Chain — each clip's approved still becomes the anchor for the next clip.

---

### Step 28 — Build Clip 02 chain

Repeat Steps 24–27 for Clip 02 with these differences:

- The Text node content comes from Space A Chunk 02
- The Compliance Gate is renamed `Compliance Gate — Clip 02`
- The Image Generator is renamed `Image Generator — Clip 02`
- The Video Generator is renamed `Video Generator — Clip 02`
- The **Reference input** of the Image Generator connects to **Approved Still — Clip 01** (not the Master Reference Image — that was only for Clip 01)

Continue this pattern for every clip:
- Clip 03's Image Generator reference input → Approved Still — Clip 02
- Clip 04's Image Generator reference input → Approved Still — Clip 03
- And so on

---

### Step 29 — Group each clip chain

Once all clip chains are built:

1. Click and drag to select all nodes belonging to Clip 01 (Chunk Brief, Compliance Gate, Image Generator, Video Generator)
2. Right-click → **Group**
3. Name the group: `Clip 01`
4. Repeat for every clip

Grouped chains are much easier to manage on the canvas when you have 6, 8, or 10 clips.

---

### Step 30 — Colour-code your Text nodes (optional but recommended)

If Magnific supports node colour customisation:
- Blue → Image Generator prompt Text nodes
- Green → Video Generator prompt Text nodes
- Grey → Locked reference nodes (VSD LOCK, Master Brief)

This makes it faster to scan the canvas and find the right node.

---

# PART 5 — BUILDING SPACE E (DRIFT CORRECTION)

Space E is a repair station. You use it when a clip's start frame does not match the avatar correctly — wrong skin tone, wrong hair, wrong wardrobe, or the face has shifted from the reference.

Build this Space once. It stays empty until you need it.

---

### Step 31 — Create Space E

1. Click **New Space**
2. Name it: `Space E — Drift Correction`

---

### Step 32 — Add Upload nodes

**Upload node 1:**
1. Right-click → **Upload**
2. Rename: `Master Reference Image`
3. Upload the avatar's Master Reference Image

**Upload node 2:**
1. Right-click → **Upload**
2. Rename: `Most Recent Approved Still`
3. Leave empty for now — when you need this Space, you will upload the last approved still from the Seed Reference Chain here

---

### Step 33 — Add the Text nodes

**Text node 1:**
1. Right-click → **Text**
2. Rename: `Original Chunk Prompt`
3. Leave empty — when using this Space, paste the original chunk's Compliance Gate output here

**Text node 2:**
1. Right-click → **Text**
2. Rename: `Drift Correction Addendum`
3. Type this template — fill it in when you need to use the Space:

```
DRIFT CORRECTION — CLIP [NUMBER] — ATTEMPT [N]

IDENTIFIED DRIFT:
[Describe what went wrong — e.g. "Skin tone shifted cooler and lighter" / "Hair appears straighter and shorter" / "Wardrobe colour shifted from sage to pale blue"]

CORRECTION DIRECTIVES:
⚠ CORRECTION: Skin tone must match VSD exactly: [paste exact skin descriptor from VSD]. Previous generation shifted [direction].
⚠ CORRECTION: Hair is [paste exact hair descriptor from VSD]. Previous generation produced [incorrect result] — do not reinterpret.
⚠ CORRECTION: [Any additional specific corrections]

REGENERATION NOTE: Use the most recent approved still in the Seed Reference Chain as the image reference — not the Master Reference alone.
```

---

### Step 34 — Add the Image Generator

1. Right-click → **Image Generator**
2. Rename: `Image Generator — Drift Fix`
3. Set aspect ratio to **9:16**
4. Set outputs per run to **5** (more options help find a clean match)

---

### Step 35 — Wire Space E

1. **Original Chunk Prompt** → **Image Generator — Drift Fix** (Prompt input)
2. **Drift Correction Addendum** → **Image Generator — Drift Fix** (second Prompt input, or append to the same input if only one prompt port is available)
3. **Most Recent Approved Still (Upload)** → **Image Generator — Drift Fix** (Reference input — use this, NOT the Master Reference)
4. **Master Reference Image (Upload)** → **Image Generator — Drift Fix** (as a secondary reference if a second reference port is available)

---

### Step 36 — How to use Space E when you need it

When a clip in Space D produces a drifted still:

1. **Do not run the Video Generator for that clip.** Stop.
2. Open Space E
3. Upload the **last approved still** (not the drifted one) to the `Most Recent Approved Still` Upload node
4. Paste the original chunk's Compliance Gate prompt output into the `Original Chunk Prompt` Text node
5. Fill in the `Drift Correction Addendum` describing what drifted and what to correct
6. Run the Image Generator
7. Browse the 5 outputs. If one matches the VSD Avatar Identity Lock — approve it, download it, and return to Space D to continue
8. If none of the 5 outputs match after 2 attempts — go one step further back in the Seed Reference Chain. Upload the approved still from two clips back instead of one, and run again

---

# PART 6 — RUNNING A FULL PRODUCTION

Once all five Spaces are built, here is the workflow for every new video.

---

### Step 37 — Prepare your files

Before opening Magnific:
1. Confirm which avatar you are producing for
2. Have the Master Reference Image on your desktop
3. Have the Character Sheet document open
4. Know the persona, video type, and target length

---

### Step 38 — Run Space A (Script)

1. Open `Space A — Scripting`
2. Fill in the **Production Brief** node:
   - Replace `[Name + one-line description]` with the avatar's name and description
   - Replace `[Persona]` with the correct health persona
   - Replace `[Video Type]` with Type 1, 2, 3, or 4
   - Replace `[Length]` with the target duration
3. Click **Run**
4. Read the script output carefully. Check:
   - Does it contain a genuine Science Fact (not generic wellness advice)?
   - Does it include a specific Home Remedy (not a default fallback ingredient)?
   - Does it include a specific Recipe?
   - Does it feel like a trusted friend speaking, not a content marketer?
5. If the script needs changes, edit the Production Brief to add more specific direction and run again
6. When approved, leave the Script Output node as-is. Do not edit it.

---

### Step 39 — Run Space B (Hook)

1. Open `Space B — Hook Generation`
2. Fill in the **Hook Brief** node:
   - Paste the exact first line of the script from Space A
   - Fill in the persona and video type
   - Choose 1 or 3 variants
3. Click **Run**
4. Check the Image Generator outputs. Browse using arrow buttons.
5. **Mute test:** Look at the still with no context. Does it communicate something worth stopping for?
6. If yes, approve the still. **Do not run the Video Generator yet.**
7. Look at the still one more time — does it match the avatar reference exactly? Correct skin tone, hair, expression?
8. If yes, run the Video Generator
9. Watch the motion clip. Does the motion feel natural and UGC-authentic?
10. Approved hook still → download to desktop and save as `[AVATAR NAME]-hook-approved.jpg`

---

### Step 40 — Run Space C (VSD)

1. Open `Space C — VSD Builder`
2. Fill in the **Avatar + Environment Brief** node with the avatar's details
3. Paste the full script from Space A into the **Script Chunks from Space A** node
4. Click **Run**
5. Read the VSD output carefully. Check every section:
   - Is every field filled with a specific value? No placeholder brackets remaining?
   - Does the environment match the avatar's character and persona?
   - Does the Prop State Registry account for every clip?
6. If any field needs adjustment, update the Avatar + Environment Brief and run again
7. When the VSD is approved, the **VSD LOCK** node is locked — do not edit it again for this production
8. Copy the full VSD text. Paste it into the VSD LOCK Text node in Space D (or wire from Space C if cross-Space wiring is available)

---

### Step 41 — Run Space D (Clip Production) — Clip by Clip

Work through every clip in sequence. Do not skip ahead.

**For each clip:**

1. Open `Space D — Chunk Production`
2. Find the **Chunk [N] Brief** Text node for this clip
3. Paste the VOICEOVER and VISUAL DIRECTION from Space A's corresponding chunk
4. Run the **Compliance Gate** node for this clip
5. Read the output — does it look like a valid, policy-clean image prompt?
6. Run the **Image Generator** for this clip
7. Browse the outputs (4–5 options). Ask yourself:
   - Does the avatar's face match the Master Reference and VSD exactly?
   - Is the expression correct for this beat in the script? (Beat before the line — not during it)
   - Are the props correct per the VSD Prop State Registry?
   - Does the lighting and environment match the VSD?
8. **If the still looks right:** Approve it. Download it to desktop. Save as `[AVATAR NAME]-clip-[NUMBER]-approved.jpg`
9. **Upload the approved still** as the reference for the next clip (Step 27 logic)
10. Run the **Video Generator** for this clip
11. Watch the 8-second clip. Does the motion feel natural? Does the lip-sync look right?
12. If yes: export/download the clip. Save as `[AVATAR NAME]-clip-[NUMBER].mp4`
13. Move to the next clip

**If the still drifts at any point:** Stop. Go to Space E. Fix the drift. Return to Space D and continue.

---

### Step 42 — Export all clips

After all clips are generated and approved:

1. Download each clip individually
2. Name files consistently: `[AVATAR NAME]-clip-01-[topic].mp4`, `[AVATAR NAME]-clip-02-[topic].mp4`, etc.
3. Store all clips in a dedicated folder: `[AVATAR NAME] / [TOPIC] / [DATE]`

You now have all the raw clips ready for your editing and publishing workflow.

---

## Final Production Checklist

Run through this before considering the production complete.

```
SPACE A — SCRIPT
[ ] Production Brief filled correctly (no placeholder brackets remaining)
[ ] Script contains a genuine Science Fact (not generic)
[ ] Script contains a new Home Remedy (not repeated from a previous video)
[ ] Script contains a new Recipe Element (not repeated)
[ ] Script approved and locked

SPACE B — HOOK
[ ] Hook still passes the Mute Test
[ ] Hook still matches the avatar reference exactly
[ ] Hook motion clip generated from the approved still only
[ ] Approved hook still downloaded and saved

SPACE C — VSD
[ ] All VSD fields filled — no placeholder brackets
[ ] Prop State Registry covers every clip
[ ] VSD LOCK node in Space D updated with this video's VSD

SPACE D — CLIP PRODUCTION
[ ] Every chunk brief filled from Space A script output
[ ] Seed Reference Chain followed in order (Master Ref → Clip 01 → Clip 02 → Clip 03...)
[ ] Every start frame approved before Video Generator ran
[ ] Every clip checked for drift before moving to the next
[ ] All clips downloaded and named consistently

SPACE E — DRIFT CORRECTION (only if needed)
[ ] Drifted clip identified and fixed before production continued
[ ] Fixed still approved and re-entered into the Seed Reference Chain
```
