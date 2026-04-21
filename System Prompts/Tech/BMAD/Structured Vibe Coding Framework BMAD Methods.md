# Structured Vibe Coding Framework: BMAD Methods

**Version:** 2.4 (Alpha-Stabilized)
**Target Architecture:** Human-in-the-Loop Agentic Orchestration
**Domain:** Scalable Software Engineering via LLM Integration

---

## 1. Executive Summary & Core Philosophy

### 1.1 The Paradox of Vibe Coding

“Vibe Coding”—the practice of developing software through high-speed, intuition-driven interaction with Large Language Models (LLMs)—has revolutionized prototyping. It allows developers to bypass syntax friction and focus on pure logic. However, it introduces a critical failure mode known as **Context Collapse**.

As a codebase grows, the LLM’s finite context window and the human’s cognitive load become misaligned. Without a rigid framework, this results in:

1. **Hallucination Loops:** The AI reinvents existing patterns, unaware of global state.
2. **Architectural Drift:** New features violate established security or structural constraints.
3. **Spaghetti Code:** Lack of global state awareness leads to circular dependencies and unmaintainable monoliths.

### 1.2 The BMAD Solution: Structure as an Accelerator

The BMAD (Build-Measure-Analyze-Design) Method acts as the stabilizing chassis for the Vibe Coding engine. It introduces an agentic layer between the developer’s intent and the code generation.

The framework bifurcates the development process:

- **The Rails (BMAD Agents):** Manage state, memory, architecture, and planning. They handle the “boring” cognitive load.
- **The Engine (Vibe Coding):** The developer enters a flow state, executing atomic tasks with high velocity, unburdened by the need to hold the entire system architecture in their head.

![Flowchart detailing the iterative BMAD Build-Measure-Analyze-Design cycle for vibe coding efficiency](https://r2.flowith.net/files/jpeg/BC8F6-bmad_cycle_flowchart_index_0@1024x1024.jpeg)

Flowchart detailing the iterative BMAD Build-Measure-Analyze-Design cycle for vibe coding efficiency

> Karpathy’s Law of Vibe: “The goal is to forget the code exists, but ensure the system behaves as if a Senior Architect never left the room.”
> 

---

## 2. The Agentic Roster (The “Party”)

In the BMAD framework, you do not chat with a generic AI. You invoke specialized personas. Each has distinct permissions, distinct context scopes, and produces specific artifacts.

| Agent Role | ID | Primary Directive | Context Scope | Output Artifacts |
| --- | --- | --- | --- | --- |
| **Analyst** | `AG-01` | **Brainstorm & Init.** Conducts feasibility studies and initializes the project structure. | Global World Knowledge + User Intent | `bmm-workflow-status.yaml`, Project Root |
| **Product Manager** | `AG-02` | **Define.** Translates abstract vibes into concrete specifications. Prevents scope creep. | User Intent + Business Logic | `PRD.md`, `tech-spec.md`, `epics/` |
| **Architect** | `AG-03` | **Structure.** Enforces patterns, security, and scalability. The “No” agent. | Tech Stack + PRD | `architecture.md`, `implementation-readiness` |
| **UX Designer** | `AG-04` | **Visualize.** Defines user flows and interface constraints. | PRD + Design System | `ux-design.md`, Mocks |
| **Scrum Master** | `AG-05` | **Orchestrate.** Manages the flow of work, breaks down Epics, and updates status. | `sprint-status.yaml` + Epics | `stories/story-X.md`, `sprint-status.yaml` |
| **DEV** | `AG-06` | **Execute.** The “Vibe Coder.” Writes code, runs tests, and performs self-review. | Story Context + Architecture | Source Code, Unit Tests |

### 2.1 Interaction Diagram

The flow of information is strictly hierarchical to prevent context contamination.

```
[HUMAN INTENT]
      |
      v
[ANALYST] --> (Determines Track: Quick/Standard/Enterprise)
      |
      v
   [PM] <----> [UX DESIGNER]
      |             |
      +-------------+
      |
      v
[ARCHITECT] --(Gate Check)--> [Approved Architecture]
      |
      v
[SCRUM MASTER] --(Decomposition)--> [Atomic Stories]
                                          |
                                          v
                                    [DEV AGENT] <==> [HUMAN FLOW STATE]
                                          |
                                    (Code + Tests)
```

---

## 3. Operational Tracks: The Scaling Logic

Not all projects require the full weight of enterprise architecture. The `Analyst` agent determines the track during Phase 2 based on the “Vibe Check.”

### 3.1 Decision Matrix

| Criteria | **Quick Flow (Level 0-1)** | **BMad Method (Level 2-3)** | **Enterprise Track (Level 4+)** |
| --- | --- | --- | --- |
| **Time Horizon** | < 48 Hours | 2 - 6 Weeks | 6 Months+ |
| **Complexity** | Single Feature / Script | Micro-SaaS / MVP | Multi-tenant / Distributed |
| **Agents Active** | Analyst, PM, SM, DEV | All Agents | All Agents + Security Audit |
| **Artifacts** | `tech-spec.md` | `PRD.md`, `architecture.md` | Full Suite + RFCs |
| **Context Strategy** | Single Context Window | Epic-Level Context Injection | Sharded Context & RAG |

---

## 4. Phase 1: Environment & Tooling Alignment

**Objective:** Establish the “Physical” digital workspace.

### 1.1 Directory Structure (Standard)

The BMAD installer generates a strictly opinionated folder structure. This consistency allows the AI to “know” where to look without burning tokens on directory tree explanations.

```bash
/project-root├── .bmad/                  # System instructions and prompts├── docs/
│   ├── architecture.md     # Generated by Architect│   ├── prd.md              # Generated by PM│   ├── epics/              # High-level groupings│   ├── stories/            # Atomic tasks│   └── context/            # Generated context shards├── src/                    # Source code├── bmm-workflow-status.yaml # High-level state└── sprint-status.yaml      # Implementation state
```

### 1.2 IDE Configuration (Cursor/Windsurf)

To enforce the framework, create a `.cursorrules` or `.windsurfrules` file in the root. This acts as a “System Prompt” for the IDE’s native AI, preventing it from going rogue.

```json
// .cursorrules{  "version": "2.0",  "role": "BMAD_Enforcer",  "instructions": [    "YOU ARE NOT ALLOWED to plan architecture. Refer to docs/architecture.md.",    "BEFORE writing code, read the active story file in docs/stories/.",    "DO NOT update sprint-status.yaml manually. Instruct user to run the SM agent.",    "IF a file is >200 lines, suggest refactoring based on Single Responsibility Principle.",    "ALWAYS checking 'docs/context/active-epic-context.md' for variable naming conventions."  ]}
```

---

## 5. Execution Phases: From Vibe to Product

### Phase 2: Initiation (The Vibe Check)

**Objective:** Capture intent and select the complexity track.

**Workflow:** `workflow-init`**Agent:** Analyst
**Process:**

1. **Input:** Raw user brain-dump (voice-to-text recommended).
2. **Analysis:** Assess technical risk and requirements.
3. **Selection:** Select Track (Quick vs. Standard).
4. **Output:** Initialize `bmm-workflow-status.yaml`.

**Example Prompt:**

> “I want to build a CLI tool that scrapes GitHub issues and summarizes them using OpenAI API. It needs to cache results locally.”
> 

**Output (`bmm-workflow-status.yaml`):**

```yaml
project_name: "gh-issue-summarizer"track: "quick-flow"current_phase: "planning"agents:  - analyst: "completed"  - pm: "pending"
```

### Phase 3: High-Velocity Planning

**Objective:** Solidify *what* we are building without writing code.

**Workflow:** `tech-spec` (Quick Flow) vs `prd` (Standard)
**Agent:** PM
**Constraint:** The AI must produce a document that serves as the “Source of Truth.”

**Template: The BMAD PRD Structure**

1. **Executive Summary:** One paragraph pitch.
2. **User Stories:** “As a [role], I want [feature].”
3. **Functional Requirements:** The “Must Haves.”
4. **Non-Functional Requirements:** Performance, Security, Cost.
5. **Risks & Constraints:** What could go wrong?

### Phase 4: Architectural Grounding (Standard/Enterprise)

**Objective:** Prevent structural collapse. This phase is skipped in Quick Flow but is mandatory for long-term viability.

**Workflow:** `create-architecture`**Agent:** Architect
**Directives:**

- **Stack Selection:** Language, DB, Framework.
- **Data Models:** Schema definition.
- **API Interfaces:** REST/GraphQL signatures.
- **Directory Structure:** The Architect enforces modularity *before* the first line of code is written.

**Workflow:** `implementation-readiness`**Agent:** Architect
**Action:** A strict “Gate Check.” The Architect reviews the PRD and UX docs. If inconsistencies exist (e.g., UX requires data not in the DB schema), the workflow halts and requests revision.

### Phase 5: Decomposition (The Context Bridge)

**Objective:** Break the monolith into manageable chunks that fit into an LLM context window.

**Workflow:** `create-epics-and-stories`**Agent:** Scrum Master (SM)

- **Epic:** A major feature (e.g., “User Authentication”).
- **Story:** An atomic unit of work (e.g., “Create Login API Endpoint”).

**The Golden Rule of Decomposition:**

> “A story must be small enough to be coded, tested, and reviewed in a single LLM context session (approx. 20-50 lines of logic).”
> 

**Workflow:** `sprint-planning`**Agent:** SM
**Output:** Generates `sprint-status.yaml`. This file is the dashboard for the entire project.

```yaml
# docs/sprint-status.yamlcurrent_sprint: 1epics:  - id: "EPIC-01"    name: "Core Infrastructure"    status: "in-progress"    stories:      - id: "STORY-01"        name: "Setup Express Server"        status: "todo"        context_file: "docs/context/epic-01-context.md"
```

### Phase 6: The Vibe Loop (Implementation)

**Objective:** High-speed execution. This is where the developer spends 80% of their time.

### 6.1 The “Fresh Chat” Protocol

**CRITICAL FAILURE POINT:** Do not maintain one long chat session.

1. Select a Story (e.g., `STORY-01`).
2. Open a **NEW** Chat Window.
3. Copy/Paste the `Context Injection`.
4. Vibe Code.
5. Commit.
6. Close Chat.

### 6.2 Workflow: `context-injection`

**Agent:** SM
**Process:** The SM generates a context block for the specific story.

**Template (Copy to Clipboard):**

```markdown
@docs/architecture.md @docs/epics/story-01.md @docs/context/epic-01-tech.md
**ROLE:** You are the DEV Agent (Ag-06).
**TASK:** Implement STORY-01.
**CONSTRAINTS:**
1. Adhere strictly to architecture.md.
2. Use the variables defined in epic-01-tech.md.
3. Write unit tests for the implementation.
4. Do not modify files outside the scope of this story.
**START:** Analyze the requirements and propose a plan.
```

### 6.3 The Flow State

Because the context is handled by files, the human prompts become minimal:

- *“Looks good, scaffold the files.”*
- *“Fix the error on line 42, it’s a type mismatch.”*

### Phase 7: Quality Assurance & Closure

**Workflow:** `code-review`**Agent:** DEV
**Trigger:** Before closing a story.
**Prompt:** “Review the code written in this session against `docs/architecture.md`. Check for: 1. Hardcoded secrets. 2. Lack of error handling. 3. Type safety. Output a diff if changes are needed.”

**Workflow:** `story-done`**Agent:** SM
**Action:**

1. Mark story as `completed` in `sprint-status.yaml`.
2. Update `epic-tech-context.md` with new discoveries.

---

## 6. Advanced Efficiency Optimizations & Integration

To truly leverage Vibe Coding, one must understand how the human flow state integrates with the rigid BMAD rails. The diagram below illustrates the “Safe Zone” where hallucination is prevented by architectural consistency.

![Diagram illustrating how Vibe Coding integrates with BMAD methods through context management and agentic rails](https://r2.flowith.net/files/jpeg/3YL3J-vibe_coding_bmad_integration_diagram_index_1@1024x1024.jpeg)

Diagram illustrating how Vibe Coding integrates with BMAD methods through context management and agentic rails

### 6.1 Context Sharding & “Just-In-Time” RAG

For Enterprise tracks, the codebase is too large for one context window.

- **Technique:** The SM maintains `context-map.json`.
- **Mechanism:** When generating `story-context`, the SM reads the map and only includes the markdown summaries of *related* modules, not the raw code.

### 6.2 “Party Mode” (Orchestrated Multi-Agent Debate)

Used when the human is stuck on a trade-off (e.g., “SQL vs NoSQL”).

- **Command:** `/party-mode topic="Database Selection"`
- **Behavior:**
    - **Architect:** Argues for structure/ACID compliance.
    - **PM:** Argues for speed-to-market.
    - **DEV:** Argues for ease of implementation.
    - **Human:** Acts as the Judge, selecting the winner.

### 6.3 Prompt Caching Strategy

If using API-based access (Anthropic/OpenAI), structured documents like `architecture.md` and `PRD.md` should be placed at the *top* of the prompt to leverage caching (Prefix Caching). This reduces latency by 80% and cost by 90%.

---

## 7. Brownfield Integration (Legacy Code)

BMAD isn’t just for new projects. It can tame legacy beasts.

**Workflow:** `document-project` (The Deep Scan)
**Agent:** Analyst + Architect
**Steps:**

1. **Tree Map:** Generate a file tree.
2. **Dependency Audit:** Analyze `package.json` / `requirements.txt`.
3. **Pattern Recognition:** AI reads key entry points (`index.js`, `main.py`) to infer architecture.
4. **Output:** Reverse-engineered `docs/architecture.md` and `docs/tech-spec.md`.

**Prompt for Brownfield Scan:**

```markdown
I am onboarding onto an existing codebase.
1. Analyze the file structure.
2. Identify the primary architectural pattern (MVC, Microservices, Monolith).
3. Create a `docs/architecture.md` that describes the CURRENT state.
4. Create a `docs/sprint-status.yaml` treating the current state as "Baseline".
```

---

## 8. Troubleshooting Guide

| Symptom | Root Cause | Resolution |
| --- | --- | --- |
| **“The AI keeps ignoring my folder structure.”** | Context Drift. The AI has “forgotten” the root directives. | **Fix:** Re-inject the `.cursorrules` or strictly reference `@architecture.md` in the prompt. |
| **“I have to explain the database schema every time.”** | Missing Epic Context. | **Fix:** Run `update-epic-context`. Ensure schema definitions are in the shared context file. |
| **“The code works but looks different from the last feature.”** | Style Drift. | **Fix:** Add a `.editorconfig` and a `style-guide.md`; force the Linter Agent to run before the DEV agent. |
| **“I am overwhelmed by the number of markdown files.”** | Process Fatigue. | **Fix:** Switch to **Quick Flow**. Delete the Epics folder and work directly from `tech-spec.md`. |

---

## 9. Appendix: Ready-to-Use Templates

This section provides visual references and schemas for the core artifacts used in the BMAD method.

![Infographic detailing BMAD key templates, hotkeys, and file schemas](https://r2.flowith.net/files/jpeg/O91AU-bmad_infographic_templates_index_2@1024x1024.jpeg)

Infographic detailing BMAD key templates, hotkeys, and file schemas

### 9.1 The `sprint-status.yaml` Schema

```yaml
version: 1.0project_name: Stringtrack: [quick-flow, bmad-method, enterprise]current_sprint: Integerepics:  - id: String    name: String    description: String    status: [pending, in-progress, completed, blocked]    context_file: Path    stories:      - id: String        name: String        acceptance_criteria: List<String>        status: [todo, in-progress, review, done]        assigned_agent: String
```

### 9.2 The Vibe Coder’s Hotkeys (Suggested)

- **CMD+Shift+K (Cursor/VSCode):** Clear Terminal.
- **CMD+L:** New Chat (Mapped).
- **CMD+I:** Inline AI Edit.
- **Snippet `!vibe`:** Inserts: “Ref: [active-story](mention:active-story). Keep it simple. Follow existing patterns. Go.”

---

**Status:** Ready for Implementation.
**Next Step:** Run `npx bmad-method@alpha install`.