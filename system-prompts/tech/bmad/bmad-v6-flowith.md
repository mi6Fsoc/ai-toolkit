# BMAD v6 — Flowith

Here is the comprehensive, production-ready Master Summary Document for the BMAD v6 Vibe Coding Framework. This document aggregates all protocols, configurations, and workflows into a single executable guide.

---

# BMAD v6: The Vibe Coding Operating System

**Master Reference & Implementation Guide**

## 1. Executive Overview

BMAD (Breakthrough Method for Agile AI-Driven Development) v6 transforms chaotic "vibe coding" into a sustainable **Flow State**. It replaces unstructured prompting with **Context Engineering**, providing the invisible rails—context sharding, scale-adaptive intelligence, and role-based agents—that allow you to code at the speed of thought without accumulating technical debt.

**Core Architecture**

The v6 architecture unifies the framework under a hidden  `.bmad`  directory, separating core logic from user configuration.

| Path | Description |
| --- | --- |
| **`.bmad/core/`** | **CORE**: Orchestration & Reflection Engine (The Kernel) |
| **`.bmad/bmm/`** | **BMM**: Software Development Module (Agile Framework) |
| **`.bmad/_cfg/`** | **USER CONFIG**: Persistent customization layer (Update-safe) |
| **`docs/stories/`** | **CONTEXT SHARDS**: Atomic instruction files for agents |

---

## 2. Installation & Migration

**One-Shot Installation**

The intelligent installer detects legacy setups, backs up data to  `.bmad/.bak` , and configures the environment.

**Prerequisites:** Node.js v20+, Git.

```
# Install or Update to the latest Alpha (Recommended for Vibe Coding)
npx bmad-method@alpha install

```

BashCopy

**v4 to v6 Migration Protocol**

If migrating from a legacy v4 monolithic expansion pack:

1. **Backup:** The installer will auto-backup, but ensure you have committed changes to Git.
2. **Run Installer:** Execute the command above.
3. **Init Project:** Run the analyst trigger to re-establish project levels.
- *Trigger:* `workflow-init`
- *Selection:* Choose **Level 3** or **Level 4** for existing mature projects.
1. **Rebuild Agents:** Migration resets core prompts. You must rebuild to apply customizations.

```
npx bmad-method@alpha build

```

BashCopy

---

## 3. Agent Customizations ( `_cfg` )

BMAD v6 uses **Update-Safe Customization**. Never edit files in  `.bmad/bmm/agents/` . Instead, create overrides in  `.bmad/_cfg/agents/` .

**Apply Changes:** After creating/editing any file below, run  `npx bmad-method@alpha build <agent-name>` .

**Product Manager (PM) Personas**

*File Path:*  `.bmad/_cfg/agents/bmm-pm.customize.yaml`

**Variant: Captain Blacklog (Ruthless Prioritizer)**

*Use Case: Hackathons, MVP Crunches.*

```
customization:
  name: 'Captain Blacklog'

  persona: |
    Role: Pirate Captain Product Owner
    Identity: A ruthless prioritizer who speaks in 17th-century nautical slang.
    Style:
      - Direct, commanding, metaphorical.
      - Features are "treasure" or "barnacles" (tech debt).
      - "Walk the plank" means deleting a feature.
  menu:
    - trigger: "parley"
      description: "Aggressively negotiate MVP scope to cut 50% of requirements."
      path: "workflows/custom/cut-scope.yaml"
    - trigger: "set sail"
      description: "Approve the sprint plan and start development."
      workflow: "sprint-planning"

```

YAMLCopy

**Variant: The Visionary (Steve Jobs Mode)**

*Use Case: Pitch decks, non-technical founder interactions.*

```
customization:
  name: "The Visionary"

  persona: |
    Role: Reality Distortion Field Generator
    Identity: You believe software is art. You reject mediocrity.
    Style:
      - Inspirational, demanding, perfectionist.
      - Focus on emotional connection over functional specs.
  memories:
    - "Users don't know what they want until we show it to them."
    - "Design is not just how it looks, it's how it works."

```

YAMLCopy

**Developer (Dev) Personas**

*File Path:*  `.bmad/_cfg/agents/bmm-dev.customize.yaml`

**Variant: FlowState (Vibe Coder)**

*Use Case: Rapid prototyping, Shadcn/Tailwind stacks.*

```
customization:
  name: "FlowState"

  persona: |
    Role: Rapid Prototyper
    Identity: You are a Vibe Coder. You prioritize working UI and visual impact.
    Style: Minimalist, rapid, visually oriented.
    Stack Preference: Tailwind, Lucide, Shadcn, Framer Motion.
  memories:
    - "If the spec is vague, choose the most modern/beautiful UI pattern."
    - "Don't ask for permission to refactor for readability."
    - "Console logs are fine for now, we clean up later."

```

YAMLCopy

**Variant: Neo (Security/Hacker)**

*Use Case: Hardening, security audits, complex logic.*

```
customization:
  name: "Neo"

  persona: |
    Role: Grey Hat Hacker
    Identity: You see the Matrix. You find the vulnerabilities others miss.
    Style:
      - Cryptic, elite, technical.
      - Uses 'l33t' speak sparingly for flavor.
    Principles:
      - Security by design.
      - Trust no input.
      - Automate everything.

```

YAMLCopy

**Scrum Master Personas**

*File Path:*  `.bmad/_cfg/agents/bmm-scrum-master.customize.yaml`

**Variant: Drill Sergeant**

*Use Case: Low velocity teams, missed deadlines.*

```
customization:
  name: "Sarge"
  persona: |
    Role: Agile Drill Instructor
    Identity: You are here to turn a ragtag group of scripts into a shipping machine.
    Style:
      - Loud (ALL CAPS), motivating, strict.
      - No excuses.
    Principles:
      - A ticket without AC is AWOL.
      - Standup is 15 minutes, not a tea party.
      - Shipping is the only victory condition.

```

YAMLCopy

---

## 4. Workflows & The Vibe Loop

Workflows are the nervous system of BMAD. They utilize **Context Sharding** to prevent hallucinations.

**The Golden Workflow Loop**

1. **Analyst:** `workflow-init`  (Setup)
2. **Scrum Master:** `run sprint-planning`  (Create `sprint-status.yaml` )
3. **Scrum Master:** `create story`  (Generate sharded context)
4. **Developer:** `dev story`  (Execute code)

**Detailed Command Reference**

**1. Initialization**

- **Trigger:** `workflow-init`
- **Agent:** Analyst
- **Vibe Tip:** Select **Level 1** for Hackathons (single file arch), **Level 3** for SaaS (detailed docs).

**2. Sprint Planning**

- **Trigger:** `run sprint-planning`  OR "Let's plan the sprint"
- **Agent:** Scrum Master
- **Input:** Reads `docs/architecture.md` .
- **Output:** Updates `sprint-status.yaml`  (The Brain).

**3. Context Sharding (CRITICAL)**

- **Trigger:** `create story for login`  OR `story-001`
- **Agent:** Scrum Master
- **Output:** `docs/stories/story-001-login.md`
- **Content:**

```
# Story-005: Login UI
**Epic:** EPIC-01 - User Authentication
## Description
As a user, I want...
## Acceptance Criteria
- [ ] Form contains email/password inputs
- [ ] Styled with Tailwind
## Technical Notes
- Use React Hook Form

```

MarkdownCopy

**4. Vibe Coding**

- **Trigger:** `dev story 001`  OR `implement story 1`
- **Agent:** Developer
- **Process:** Reads *only* the specific story file + referenced files. Zero noise.

---

## 5. IDE Integrations (The Cockpit)

**Cursor (Recommended)**

Cursor requires explicit whitelisting to read the hidden BMAD configuration.

**1. Create/Edit**  **`.cursorignore**`  **in project root:**

```
# .cursorignore
# Ignore standard junk
node_modules/
dist/
# CRITICAL: Allow BMAD context
!/.bmad/
!/.bmad/**/*.md
!/.bmad/**/*.yaml
!/.bmad/**/*.json

```

Plain TextCopy

**2. Chat Usage:**

- Mention `@Analyst`  for high-level questions.
- Mention `@ScrumMaster`  for planning.
- Mention `@Dev`  for coding.

**VSCode / Claude Desktop**

If using Claude Desktop or other LLM interfaces, you may need to manually attach the context or use the CLI flattening tool to paste context.

```
# Flatten codebase to XML for LLM context injection
npx bmad-method@alpha flatten

```

BashCopy

---

## 6. Best Practices & Troubleshooting

**The Flow State Checklist**

Before a coding session:

1. **Fresh Chat:** New window for new phase.
2. **Config Loaded:** `.bmad/_cfg`  has correct personas.
3. **Repo Clean:** Git status clean.
4. **Target Locked:** You know exactly which `story-XXX`  is next.

**Troubleshooting "Vibe Kills"**

| Symptom | Probable Cause | The Fix |
| --- | --- | --- |
| **Agent Hallucinates Files** | Context Window Full | **Start a Fresh Chat.** Point agent to  `story.md`  only. |
| **"I can't find the plan"** | Missing  `sprint-status.yaml` | Run  `@ScrumMaster run sprint-planning` . |
| **Code != Architecture** | Skipped Story Phase | Do not jump from Arch -> Code. Run  `create-story`  first. |
| **Custom Persona Ignored** | Agent Not Rebuilt | Run  `npx bmad-method@alpha build <agent>` . |
| **Module not found** | Legacy v4 paths | Run  `npx bmad-method@alpha install`  again. |

**Deprecated Modules (v4 -> v6)**

| v4 Module | v6 Replacement | Action |
| --- | --- | --- |
| `.bmad-core` | `.bmad/core/` | Automatic migration |
| Expansion Packs | `.bmad/bmm/` ,  `.bmad/bmb/` | Consolidated into core |
| Static Prompts | Dynamic Build System | Use  `_cfg`  +  `build`  command |

---

## 7. Master Reference Commands

**Installation & Update**

```
npx bmad-method@alpha install
npm view bmad-method@alpha version

```

BashCopy

**Build & Customize**

```
# Rebuild ALL agents (Run after update)
npx bmad-method@alpha build
# Rebuild specific agent (Run after editing YAML)
npx bmad-method@alpha build bmm-pm
npx bmad-method@alpha build bmm-dev
npx bmad-method@alpha build bmm-scrum-master

```

BashCopy

**Utilities**

`# Validate project structure integrity`

`npx bmad-method@alpha validate`

`# Generate XML dump of project for LLM pasting`

`npx bmad-method@alpha flatten`