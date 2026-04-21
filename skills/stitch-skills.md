---
name: stitch-skills
description: Comprehensive guide to Stitch Agent Skills for design systems, React components, prompt enhancement, video generation, and automated website building
---

# Stitch Agent Skills

A comprehensive library of Agent Skills designed to work with the Stitch MCP server. Each skill follows the Agent Skills open standard, ensuring compatibility with coding agents such as Antigravity, Gemini CLI, Claude Code, and Cursor.

**Repository:** [google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills)

## Overview

Stitch Agent Skills enable AI coding agents to work seamlessly with Stitch (Google's UI generation tool) to create, analyze, and transform design systems and UI components. The skills cover the full lifecycle from design documentation to code generation, video walkthroughs, and component library integration.

## Installation & Discovery

Install any skill from this repository using the `skills` CLI. This command automatically detects your active coding agents and places the skill in the appropriate directory.

```bash
# List all available skills in this repository
npx skills add google-labs-code/stitch-skills --list

# Install a specific skill
npx skills add google-labs-code/stitch-skills --skill react:components --global
```

---

## Available Skills

### 1. design-md

**Purpose:** Analyzes Stitch projects and generates comprehensive `DESIGN.md` files documenting design systems in natural, semantic language optimized for Stitch screen generation.

**Installation:**
```bash
npx skills add google-labs-code/stitch-skills --skill design-md --global
```

#### Key Features
- Extracts project identity and design tokens from Stitch screens
- Translates technical CSS/Tailwind values into descriptive, natural language
- Creates reusable design system documentation for consistent screen generation
- Maps color palettes with functional roles and hex codes
- Documents typography, component styling, and layout principles

#### Prerequisites
- Access to the Stitch MCP Server
- A Stitch project with at least one designed screen
- Access to the [Stitch Effective Prompting Guide](https://stitch.withgoogle.com/docs/learn/prompting/)

#### Workflow

**1. Retrieval and Networking**
- **Namespace discovery:** Run `list_tools` to find the Stitch MCP prefix (e.g., `mcp_stitch:`)
- **Project lookup:** Call `[prefix]:list_projects` to retrieve user projects
- **Screen lookup:** Call `[prefix]:list_screens` with the project ID
- **Metadata fetch:** Call `[prefix]:get_screen` to get screenshot and HTML code URLs
- **Asset download:** Use `web_fetch` to download HTML and parse design tokens

**2. Analysis & Synthesis**
- **Extract Project Identity:** Locate project title and ID from JSON metadata
- **Define Atmosphere:** Evaluate screenshot and HTML to capture the overall "vibe" (e.g., "Airy," "Dense," "Minimalist")
- **Map Color Palette:** Identify key colors with descriptive names, hex codes, and functional roles
  - Example: "Deep Muted Teal-Navy (#294056) for primary actions"
- **Translate Geometry:** Convert technical values to physical descriptions
  - `rounded-full` → "Pill-shaped"
  - `rounded-lg` → "Subtly rounded corners"
- **Describe Depth:** Explain shadow usage and elevation patterns

**3. Output Format**

```markdown
# Design System: [Project Title]
**Project ID:** [Insert Project ID Here]

## 1. Visual Theme & Atmosphere
(Description of the mood, density, and aesthetic philosophy.)

## 2. Color Palette & Roles
(List colors by Descriptive Name + Hex Code + Functional Role.)

## 3. Typography Rules
(Description of font family, weight usage for headers vs. body, and letter-spacing character.)

## 4. Component Stylings
* **Buttons:** (Shape description, color assignment, behavior).
* **Cards/Containers:** (Corner roundness description, background color, shadow depth).
* **Inputs/Forms:** (Stroke style, background).

## 5. Layout Principles
(Description of whitespace strategy, margins, and grid alignment.)
```

#### Best Practices
- **Be Descriptive:** Use "Ocean-deep Cerulean (#0077B6)" instead of just "blue"
- **Be Functional:** Always explain what each design element is used for
- **Be Consistent:** Use the same terminology throughout the document
- **Be Visual:** Help readers visualize the design through descriptions
- **Be Precise:** Include exact values (hex codes, pixel values) in parentheses

#### Common Pitfalls to Avoid
- ❌ Using technical jargon without translation (e.g., "rounded-xl" instead of "generously rounded corners")
- ❌ Omitting color codes or using only descriptive names
- ❌ Forgetting to explain functional roles of design elements
- ❌ Being too vague in atmosphere descriptions
- ❌ Ignoring subtle design details like shadows or spacing patterns

---

### 2. react-components

**Purpose:** Converts Stitch designs into modular Vite and React components using system-level networking and AST-based validation.

**Installation:**
```bash
npx skills add google-labs-code/stitch-skills --skill react:components --global
```

#### Key Features
- Transforms Stitch HTML into clean, modular React components
- Automated AST-based validation for code quality
- Design token consistency with Tailwind configuration
- Logic isolation using custom hooks
- Data decoupling with mock data files
- TypeScript type safety with `Readonly` interfaces

#### Prerequisites
- Access to the Stitch MCP Server
- Node.js and npm installed
- Vite + React project setup

#### Architectural Rules
- **Modular components:** Break designs into independent files, avoid large single-file outputs
- **Logic isolation:** Move event handlers and business logic into `src/hooks/`
- **Data decoupling:** Move all static text, image URLs, and lists into `src/data/mockData.ts`
- **Type safety:** Every component must include a `Readonly` TypeScript interface named `[ComponentName]Props`
- **Style mapping:** Extract `tailwind.config` from HTML `<head>` and sync with `resources/style-guide.json`

#### Workflow

**1. Retrieval and Networking**
- **Namespace discovery:** Run `list_tools` to find the Stitch MCP prefix
- **Metadata fetch:** Call `[prefix]:get_screen` to retrieve design JSON
- **High-reliability download:** Use Bash tool to run:
  ```bash
  bash scripts/fetch-stitch.sh "[htmlCode.downloadUrl]" "temp/source.html"
  ```
  (This script handles Google Cloud Storage redirects and security handshakes)
- **Visual audit:** Check `screenshot.downloadUrl` to confirm design intent

**2. Execution Steps**
1. **Environment setup:** If `node_modules` is missing, run `npm install`
2. **Data layer:** Create `src/data/mockData.ts` based on design content
3. **Component drafting:** Use `resources/component-template.tsx` as base
   - Find and replace all instances of `StitchComponent` with actual component name
4. **Application wiring:** Update `App.tsx` to render new components
5. **Quality check:**
   - Run `npm run validate <file_path>` for each component
   - Verify against `resources/architecture-checklist.md`
   - Start dev server with `npm run dev` to verify live result

#### Troubleshooting
- **Fetch errors:** Ensure the URL is quoted in bash command to prevent shell errors
- **Validation errors:** Review AST report and fix missing interfaces or hardcoded styles

---

### 3. stitch-loop

**Purpose:** Generates a complete multi-page website from a single prompt using Stitch, with automated file organization and validation.

**Installation:**
```bash
npx skills add google-labs-code/stitch-skills --skill stitch-loop --global
```

#### Key Features
- Autonomous website development through a "baton" system
- Continuous iteration: reads task, generates page, integrates, writes next task
- Automated file organization and navigation wiring
- Optional visual verification with Chrome DevTools MCP
- Site documentation tracking with `SITE.md`

#### Prerequisites
**Required:**
- Access to the Stitch MCP Server
- A `DESIGN.md` file (generate using `design-md` skill if needed)
- A `SITE.md` file documenting site vision and roadmap

**Optional:**
- Chrome DevTools MCP Server for visual verification

#### The Baton System

The `next-prompt.md` file acts as a relay baton between iterations:

```markdown
---
page: about
---
A page describing how jules.top tracking works.

**DESIGN SYSTEM (REQUIRED):**
[Copy from DESIGN.md Section 6]

**Page Structure:**
1. Header with navigation
2. Explanation of tracking methodology
3. Footer with links
```

**Critical rules:**
- The `page` field in YAML frontmatter determines the output filename
- The prompt content must include the design system block from `DESIGN.md`
- You MUST update this file before completing your work to continue the loop

#### Execution Protocol

**Step 1: Read the Baton**
- Parse `next-prompt.md` to extract page name and prompt content

**Step 2: Consult Context Files**
- Read `SITE.md` for site vision, Stitch Project ID, existing pages (sitemap), roadmap
- Read `DESIGN.md` for required visual style
- Check Section 4 (Sitemap) to avoid recreating existing pages
- Check Section 5 (Roadmap) for pending tasks

**Step 3: Generate with Stitch**
1. Discover namespace: Run `list_tools` to find Stitch MCP prefix
2. Get or create project:
   - If `stitch.json` exists, use the `projectId` from it
   - Otherwise, call `[prefix]:create_project` and save ID to `stitch.json`
3. Generate screen: Call `[prefix]:generate_screen_from_text` with:
   - `projectId`: The project ID
   - `prompt`: Full prompt from baton (including design system block)
   - `deviceType`: `DESKTOP` (or as specified)
4. Retrieve assets: Call `[prefix]:get_screen` to get:
   - `htmlCode.downloadUrl` → Download and save as `queue/{page}.html`
   - `screenshot.downloadUrl` → Download and save as `queue/{page}.png`

**Step 4: Integrate into Site**
1. Move generated HTML from `queue/{page}.html` to `site/public/{page}.html`
2. Fix any asset paths to be relative to the public folder
3. Update navigation:
   - Find existing placeholder links (e.g., `href="#"`) and wire them to the new page
   - Add the new page to global navigation if appropriate
4. Ensure consistent headers/footers across all pages

**Step 4.5: Visual Verification (Optional)**
If Chrome DevTools MCP Server is available:
1. Check availability: Run `list_tools` to see if `chrome*` tools are present
2. Start dev server: Use Bash to start local server (e.g., `npx serve site/public`)
3. Navigate to page: Call `[chrome_prefix]:navigate` to open `http://localhost:3000/{page}.html`
4. Capture screenshot: Call `[chrome_prefix]:screenshot`
5. Visual comparison: Compare against Stitch screenshot
6. Stop server: Terminate the dev server process

**Step 5: Update Site Documentation**
Modify `SITE.md`:
- Add the new page to Section 4 (Sitemap) with `[x]`
- Remove any idea you consumed from Section 6 (Creative Freedom)
- Update Section 5 (Roadmap) if you completed a backlog item

**Step 6: Prepare the Next Baton (Critical)**
**You MUST update `next-prompt.md` before completing.** This keeps the loop alive.

1. Decide the next page:
   - Check `SITE.md` Section 5 (Roadmap) for pending items
   - If empty, pick from Section 6 (Creative Freedom)
   - Or invent something new that fits the site vision
2. Write the baton with proper YAML frontmatter

---

### 4. enhance-prompt

**Purpose:** Transforms vague UI ideas into polished, Stitch-optimized prompts. Enhances specificity, adds UI/UX keywords, injects design system context, and structures output for better generation results.

**Installation:**
```bash
npx skills add google-labs-code/stitch-skills --skill enhance-prompt --global
```

#### Key Features
- Converts vague UI ideas into structured, detailed prompts
- Adds UI/UX keywords and component-specific terminology
- Injects design system context from `DESIGN.md` if available
- Amplifies visual style with descriptive adjectives
- Formats colors properly with hex codes and functional roles
- Structures page layouts with numbered sections

#### Prerequisites
- Consult the [Stitch Effective Prompting Guide](https://stitch.withgoogle.com/docs/learn/prompting/) for latest best practices

#### When to Use This Skill
Activate when a user wants to:
- Polish a UI prompt before sending to Stitch
- Improve a prompt that produced poor results
- Add design system consistency to a simple idea
- Structure a vague concept into an actionable prompt

#### Enhancement Pipeline

**Step 1: Assess the Input**

Evaluate what's missing from the user's prompt:

| Element | Check for | If missing... |
|---------|-----------|---------------|
| **Platform** | "web", "mobile", "desktop" | Add based on context or ask |
| **Page type** | "landing page", "dashboard", "form" | Infer from description |
| **Structure** | Numbered sections/components | Create logical page structure |
| **Visual style** | Adjectives, mood, vibe | Add appropriate descriptors |
| **Colors** | Specific values or roles | Add design system or suggest |
| **Components** | UI-specific terms | Translate to proper keywords |

**Step 2: Check for DESIGN.md**

**If DESIGN.md exists:**
1. Read the file to extract the design system block
2. Include color palette, typography, and component styles
3. Format as a "DESIGN SYSTEM (REQUIRED)" section in output

**If DESIGN.md does not exist:**
Add this note at the end of the enhanced prompt:

```
---
💡 **Tip:** For consistent designs across multiple screens, create a DESIGN.md 
file using the `design-md` skill. This ensures all generated pages share the 
same visual language.
```

**Step 3: Apply Enhancements**

**A. Add UI/UX Keywords**

Replace vague terms with specific component names:

| Vague | Enhanced |
|-------|----------|
| "menu at the top" | "navigation bar with logo and menu items" |
| "button" | "primary call-to-action button" |
| "list of items" | "card grid layout" or "vertical list with thumbnails" |
| "form" | "form with labeled input fields and submit button" |
| "picture area" | "hero section with full-width image" |

**B. Amplify the Vibe**

Add descriptive adjectives to set the mood:

| Basic | Enhanced |
|-------|----------|
| "modern" | "clean, minimal, with generous whitespace" |
| "professional" | "sophisticated, trustworthy, with subtle shadows" |
| "fun" | "vibrant, playful, with rounded corners and bold colors" |
| "dark mode" | "dark theme with high-contrast accents on deep backgrounds" |

**C. Structure the Page**

Organize content into numbered sections:

```markdown
**Page Structure:**
1. **Header:** Navigation with logo and menu items
2. **Hero Section:** Headline, subtext, and primary CTA
3. **Content Area:** [Describe the main content]
4. **Footer:** Links, social icons, copyright
```

**D. Format Colors Properly**

When colors are mentioned, format them as:
```
Descriptive Name (#hexcode) for functional role
```

Examples:
- "Deep Ocean Blue (#1a365d) for primary buttons and links"
- "Warm Cream (#faf5f0) for page background"
- "Soft Gray (#6b7280) for secondary text"

**Step 4: Format the Output**

Structure the enhanced prompt in this order:

```markdown
[One-line description of the page purpose and vibe]

**DESIGN SYSTEM (REQUIRED):**
- Platform: [Web/Mobile], [Desktop/Mobile]-first
- Theme: [Light/Dark], [style descriptors]
- Background: [Color description] (#hex)
- Primary Accent: [Color description] (#hex) for [role]
- Text Primary: [Color description] (#hex)
- [Additional design tokens...]

**Page Structure:**
1. **[Section]:** [Description]
2. **[Section]:** [Description]
...
```

---

### 5. remotion

**Purpose:** Generates walkthrough videos from Stitch projects using Remotion with smooth transitions, zooming, and text overlays to showcase app screens professionally.

**Installation:**
```bash
npx skills add google-labs-code/stitch-skills --skill remotion --global
```

#### Key Features
- Creates professional walkthrough videos from Stitch screens
- Smooth transitions and zoom effects
- Contextual text overlays with proper timing
- Automated screen sequencing
- Remotion-based video composition using React

#### Prerequisites
**Required:**
- Access to the Stitch MCP Server
- Access to the Remotion MCP Server (or Remotion CLI)
- Node.js and npm installed
- A Stitch project with designed screens

**Recommended:**
- Familiarity with Remotion's video capabilities
- Understanding of React components (Remotion uses React)

#### Execution Steps

**Step 1: Gather Screen Assets**
1. Identify target Stitch project
2. List all screens in the project
3. Download screenshots for each screen
4. Organize in order of walkthrough flow
5. Create a manifest file (`screens.json`):

```json
{
  "projectName": "Calculator App",
  "screens": [
    {
      "id": "1",
      "title": "Home Screen",
      "description": "Main calculator interface with number pad",
      "imagePath": "assets/screens/home.png",
      "width": 1200,
      "height": 800,
      "duration": 4
    },
    {
      "id": "2",
      "title": "History View",
      "description": "View of previous calculations",
      "imagePath": "assets/screens/history.png",
      "width": 1200,
      "height": 800,
      "duration": 3
    }
  ]
}
```

**Step 2: Generate Remotion Components**

Create video components following Remotion best practices:

1. **Create `ScreenSlide.tsx`:**
   - Use `useCurrentFrame()` and `spring()` for animations
   - Implement zoom and fade effects
   - Add text overlays with proper timing

2. **Create `WalkthroughComposition.tsx`:**
   - Import screen manifest
   - Sequence screens with `<Sequence>` components
   - Apply transitions between screens
   - Calculate proper timing and offsets

3. **Update `remotion.config.ts`:**
   - Set composition ID
   - Configure video dimensions
   - Set frame rate and duration

**Reference Resources:**
- Use `resources/screen-slide-template.tsx` as starting point
- Follow `resources/composition-checklist.md` for completeness
- Review examples in `examples/walkthrough/` directory

**Step 3: Preview and Refine**
1. **Start Remotion Studio:**
   ```bash
   npm run dev
   ```
   - Opens browser-based preview
   - Allows real-time editing and refinement

2. **Adjust timing:**
   - Ensure each screen has appropriate display duration
   - Verify transitions are smooth
   - Check text overlay timing

3. **Fine-tune animations:**
   - Adjust spring configurations for zoom effects
   - Modify easing functions for transitions
   - Ensure text is readable at all times

**Step 4: Render Video**
1. **Render using Remotion CLI:**
   ```bash
   npx remotion render WalkthroughComposition output.mp4
   ```

2. **Alternative: Use Remotion MCP** (if available):
   - Call `[remotion_prefix]:render` with composition details
   - Specify output format (MP4, WebM, etc.)

3. **Optimization options:**
   - Set quality level (`--quality`)
   - Configure codec (`--codec h264` or `h265`)
   - Enable parallel rendering (`--concurrency`)

---

### 6. shadcn-ui

**Purpose:** Expert guidance for integrating and building applications with shadcn/ui components. Helps discover, install, customize, and optimize shadcn/ui components with best practices for React applications.

**Installation:**
```bash
npx skills add google-labs-code/stitch-skills --skill shadcn-ui --global
```

#### Core Principles

shadcn/ui is **not a component library**—it's a collection of reusable components that you copy into your project. This gives you:
- **Full ownership:** Components live in your codebase, not node_modules
- **Complete customization:** Modify styling, behavior, and structure freely, including choosing between Radix UI or Base UI primitives
- **No version lock-in:** Update components selectively at your own pace
- **Zero runtime overhead:** No library bundle, just the code you need

#### Project Setup

**Initial Configuration**

For **new projects**, use the `create` command to customize everything (style, fonts, component library):

```bash
npx shadcn@latest create
```

For **existing projects**, initialize configuration:

```bash
npx shadcn@latest init
```

This creates `components.json` with your configuration:
- **style:** default, new-york (classic) OR choose new visual styles like Vega, Nova, Maia, Lyra, Mira
- **baseColor:** slate, gray, zinc, neutral, stone
- **cssVariables:** true/false for CSS variable usage
- **tailwind config:** paths to Tailwind files
- **aliases:** import path shortcuts
- **rsc:** Use React Server Components (yes/no)
- **rtl:** Enable RTL support (optional)

**Required Dependencies**

shadcn/ui components require:
- **React** (18+)
- **Tailwind CSS** (3.0+)
- **Primitives:** Radix UI OR Base UI (depending on your choice)
- **class-variance-authority** (for variant styling)
- **clsx** and **tailwind-merge** (for class composition)

#### Component Discovery and Installation

**1. Browse Available Components**
Visit [ui.shadcn.com](https://ui.shadcn.com) to explore the component catalog

**2. Component Installation**
```bash
npx shadcn@latest add button
npx shadcn@latest add card dialog form
```

**3. Registry and Custom Registries**
- Components are fetched from the official registry by default
- You can create custom registries for team-specific components

#### Customization Best Practices

**1. Theme Customization**
- Modify CSS variables in your global CSS file
- Use the theme configurator at ui.shadcn.com/themes
- Customize colors, border radius, and spacing

**2. Component Variants**
- Use `class-variance-authority` (cva) for variant styling
- Define variants in the component file
- Compose variants with the `cn()` utility

**3. Extending Components**
- Components are in your codebase, so modify freely
- Add new props, variants, or functionality
- Maintain consistency with the design system

#### Common Patterns

**Form Building**
- Combine Form + Input + Label + Button components
- Use React Hook Form for validation
- Leverage Zod for schema validation

**Dialog/Modal Patterns**
- Use Dialog component for modals
- Combine with Form for dialog forms
- Use AlertDialog for confirmations

**Data Display**
- Use Table component for data grids
- Combine Card + Badge for status displays
- Use Tabs for organized content sections

#### Troubleshooting

**Import Errors**
- Verify path aliases in `tsconfig.json` match `components.json`
- Check that components are installed in the correct directory

**Style Conflicts**
- Ensure Tailwind CSS is properly configured
- Check for conflicting global styles
- Verify CSS variable definitions

**Missing Dependencies**
- Run `npm install` after adding new components
- Check that peer dependencies are installed
- Verify Radix UI or Base UI primitives are present

**Version Compatibility**
- Keep React and Tailwind CSS up to date
- Check component documentation for specific version requirements
- Update components selectively as needed

---

## Repository Structure

Every directory within `skills/` or at the root level follows a standardized structure to ensure the AI agent has everything it needs for "few-shot" learning and automated quality checks:

```text
skills/[category]/
├── SKILL.md           — The "Mission Control" for the agent
├── scripts/           — Executable enforcers (Validation & Networking)
├── resources/         — The knowledge base (Checklists & Style Guides)
└── examples/          — The "Gold Standard" syntactically valid references
```

## Adding New Skills

All new skills need to follow the file structure above to implement the Agent Skills open standard.

### Great Candidates for New Skills
* **Validation:** Skills that convert Stitch HTML to other UI frameworks and validate the syntax
* **Decoupling Data:** Skills that convert static design content into external mock data files
* **Generate Designs:** Skills that generate new design screens in Stitch from a given set of data

---

## Integration Workflows

### Workflow 1: Design System to Multi-Page Website

1. **Create Design System Documentation**
   - Use `design-md` skill to analyze existing Stitch screen
   - Generate `DESIGN.md` with color palette, typography, and component styles

2. **Enhance Prompts**
   - Use `enhance-prompt` skill to transform vague ideas into structured prompts
   - Inject design system context from `DESIGN.md`

3. **Build Website Loop**
   - Use `stitch-loop` skill to generate multi-page website
   - Each iteration reads baton, generates page, integrates, and writes next task

4. **Create Walkthrough Video**
   - Use `remotion` skill to generate professional video showcasing all screens
   - Add transitions, zoom effects, and text overlays

### Workflow 2: Stitch to React Application

1. **Generate Stitch Screens**
   - Use enhanced prompts with design system context
   - Generate multiple screens in Stitch project

2. **Convert to React Components**
   - Use `react-components` skill to transform Stitch HTML
   - Automated validation ensures code quality
   - Components follow modular architecture with hooks and mock data

3. **Integrate shadcn/ui**
   - Use `shadcn-ui` skill to add pre-built components
   - Customize components to match design system
   - Maintain consistency with Tailwind configuration

---

## Best Practices Across All Skills

### 1. Design System Consistency
- Always create or reference a `DESIGN.md` file for multi-screen projects
- Use descriptive color names with hex codes
- Maintain consistent terminology across documentation

### 2. Networking with Stitch MCP
- Always run `list_tools` first to discover the Stitch MCP prefix
- Use numeric IDs only (not full paths) for `projectId` and `screenId` parameters
- Handle Google Cloud Storage downloads with Bash scripts for reliability

### 3. Validation and Quality
- Run automated validation tools before considering work complete
- Verify visual output against Stitch screenshots
- Check against architecture checklists and style guides

### 4. Documentation and Tracking
- Keep `SITE.md` updated with sitemap and roadmap
- Use baton files (`next-prompt.md`) for iterative workflows
- Document design decisions and functional roles

### 5. Modular Architecture
- Break large files into smaller, focused components
- Isolate logic in custom hooks
- Decouple data into separate files
- Use TypeScript for type safety

---

## Resources

- **Stitch Effective Prompting Guide:** https://stitch.withgoogle.com/docs/learn/prompting/
- **shadcn/ui Documentation:** https://ui.shadcn.com
- **Remotion Documentation:** https://remotion.dev
- **Repository:** https://github.com/google-labs-code/stitch-skills

---

## Disclaimer

This is not an officially supported Google product. This project is not eligible for the [Google Open Source Software Vulnerability Rewards Program](https://bughunters.google.com/open-source-security).
