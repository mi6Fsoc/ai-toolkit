# Bolt—Prompting Framework

Based on Bolt’s official documentation and best practices for "vibe coding," here is a comprehensive framework designed to help you build a custom GPT or tool. This framework transforms vague ideas into high-precision prompts that maximize Bolt’s AI capabilities.

---

# The Bolt Vibe-Coding Framework

## Part 1: The Philosophy

"Code at the speed of thought."

Effective vibe coding with Bolt isn't about writing code; it's about writing specifications. The AI is your Junior Developer, UI Designer, and DevOps Engineer rolled into one. Your job is to be the Product Manager.

**Core Rule:** Never prompt with "Make an app." Prompt with a **Blueprint**.

---

## Part 2: The Perfect Prompt Structure (The Blueprint)

When generating the initial prompt, your Custom GPT should enforce this 5-section structure.

### 1. Context & Identity (The "Who")

- **Goal:** Define what the app is and who it is for.
- **Key Elements:** Project Name, User Persona, Core Problem Solved.
- **Example:** "Build a 'Plant Parent' dashboard for urban gardeners to track watering schedules."

### 2. The Tech Stack (The "How")

- **Goal:** Eliminate hallucinated libraries and enforce Bolt’s preferred stack.
- **Bolt Best Practice:** Stick to standard web technologies.
- **Standard Stack:**
    - **Framework:** React (Vite) or Next.js.
    - **Styling:** Tailwind CSS (Crucial for "vibe" coding as it handles design tokens easily).
    - **Icons:** Lucide React (Standard, low overhead).
    - **Backend/Data:** Supabase (if auth/DB needed) or LocalStorage (for prototypes).
- **Constraint:** *“Use functional components and TypeScript.”*

### 3. The Vibe (The "Look")

- **Goal:** Define the aesthetic before a single pixel is drawn. This prevents the "generic Bootstrap" look.
- **Parameters:**
    - **Palette:** Primary, Secondary, Background colors (e.g., "Deep Forest Green #0A3F2C with Sand backgrounds").
    - **Typography:** Sans-serif/Serif pairing (e.g., "Inter for UI, Playfair Display for headers").
    - **Radius/Spacing:** "Generous padding, rounded-xl corners, glassmorphism effects."
    - **Tone:** Professional, Playful, Minimalist, Cyberpunk.

### 4. Core Features (The "What")

- **Goal:** List *only* the MVP features. Overloading the first prompt leads to half-baked code.
- **Format:** Bullet points with user stories.
    - *“User can add a plant with a photo and name.”*
    - *“Dashboard shows a ‘Needs Water’ alert list.”*

### 5. File Structure & Constraints (The "Rules")

- **Goal:** Prevent messy code.
- **Directives:**
    - "Store components in `/src/components`."
    - "Use a `types.ts` file for all TypeScript interfaces."
    - "Ensure mobile responsiveness first."

---

## Part 3: Iterative Prompting Strategy

The custom tool should advise users to **never** build the whole app in one go. Use the **"Feature Loading"** method:

1. **Prompt 1 (The Skeleton):** Set up the project structure, routing, and a "Hello World" landing page with the correct Vibe.
2. **Prompt 2 (The Layout):** Build the static UI components (Navbar, Sidebar, Cards) without logic.
3. **Prompt 3 (The Logic):** Connect state management and functionality.
4. **Prompt 4 (The Polish):** Add animations, transitions, and error handling.

---

## Part 4: Debugging & Error Handling Protocol

When Bolt errors out, the GPT should generate a "Rescue Prompt" based on the error type.

### Strategy 1: The "Thinking" Fix (For Logic Errors)

If the preview is broken or logic fails:

- **Do not** just say "It's broken."
- **Prompt:** *"Stop coding. Analyze the current `App.tsx` and `types.ts`. I am seeing [Error Message]. Explain step-by-step why this is happening, then propose a fix that does not break [Working Feature]. Only after explaining, implement the fix."*

### Strategy 2: The "Clean Slate" (For Build/Dependency Errors)

If the terminal shows endless red text or packages fail to install:

- **Prompt:** *"I am facing dependency conflicts. Please perform a manual cleanup:
    1. List all current dependencies.
    2. Identify conflicting versions.
    3. Rewrite `package.json` with standard, compatible versions.
    4. Instruct me to run `npm install`."*

### Strategy 3: The Context Window Refresh (For "Lazy" AI)

If Bolt forgets previous instructions or writes truncated code:

- **Action:** The user needs to create a `.bolt/ignore` file.
- **Prompt:** *"The project is getting too large. Generate a `.bolt/ignore` file to exclude `node_modules`, `dist`, `coverage`, and standard documentation files to free up context window space."*

---

## Part 5: System Instructions for Your Custom GPT

Copy and paste the following into your Custom GPT/Claude Project instructions. This drives the framework.

Markdown

`### ROLE
You are the "Bolt Architect," an expert in Vibe Coding using Bolt.new. Your goal is to take a user's rough idea and transform it into a precision-engineered "Mega Prompt" that guarantees a high-quality, bug-free application.

### PROCESS
1. ****Analyze:**** Read the user's request. Identify missing critical information (Tech stack? Design vibe? Data persistence?).
2. ****Interrogate:**** If the request is too vague (e.g., "Build a CRM"), ask 3 specific questions to clarify the "Vibe" and "MVP Scope."
3. ****Draft:**** Generate a single, comprehensive prompt block that the user can copy/paste into Bolt.

### THE OUTPUT FORMAT (The "Mega Prompt")
You must output the final prompt in this specific structure:

---
****[Copy This Into Bolt]****Project Context:****
[One sentence summary of the app]

****Tech Stack:****- Framework: React + Vite (Typescript)
- Styling: Tailwind CSS
- Icons: Lucide React
- Animation: Framer Motion (only if requested)
- State: [Zustand/Context API]

****The Vibe (Design System):****- Colors: [Primary Hex] | [Background Hex]
- Typography: [Font Names]
- Aesthetics: [e.g., Glassmorphism, Brutalist, Apple-Clean]
- UI Rules: [e.g., "Use 8px border radius, plenty of whitespace"]

****Core Features (MVP):****1. [Feature 1 Name]: [Specific details of how it works]
2. [Feature 2 Name]: [Specific details]
3. [Feature 3 Name]: [Specific details]

****Technical Constraints:****- Use functional components only.
- Ensure fully responsive design (Mobile First).
- Handle all loading states and empty states visually.
- Create a specific `types.ts` for all interfaces.

****Step-by-Step Implementation Plan:****1. Setup project scaffolding and design system.
2. Build static UI shell.
3. Integrate logic and state.
---

### DEBUGGING MODE
If the user provides an error message, provide a "Rescue Prompt":
"Review the code in [File Name]. The error is [Error]. Think step-by-step to find the root cause. Fix it by [Specific Action], ensuring you do not break [Related Feature]."`