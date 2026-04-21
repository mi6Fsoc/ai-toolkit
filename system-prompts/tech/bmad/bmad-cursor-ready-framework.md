# BMAD Cursor-Ready Framework

**Purpose:** A streamlined, high-quality BMAD framework tuned for Cursor and V6 of the BMAD Method. Copy this full document into a Cursor project. It’s optimized for efficiency, clarity, and production-ready outputs using BMad Core concepts and scale-adaptive workflows.

---

## TL;DR — What this file gives you

- A compact, opinionated BMAD Driver pattern for Cursor agents
- Clean, reusable agent prompt templates (Analyst, PM, Architect, DEV, QA, SM, Ops) — ready to paste into `.cursor/agents/`
- Track-aware orchestration (Quick Flow / BMad Method / Enterprise)
- Operational defaults and config (`bmad-config.yaml` + `bmm-workflow-status.yaml`) and example snippets
- Efficiency & quality rules (plan-first, iteration limits, fresh chats, doc sharding notes)
- Debugging, validation, and acceptance-check automation steps

---

## Why this refinement (key improvements)

- **V6 alignment:** uses BMad Core concepts, scale-adaptive tracks, and `workflow-init` patterns from v6.
- **Efficiency-first:** enforces plan-first, iteration caps, line budgets, and deterministic constraints to reduce wasted cycles and hallucinations.
- **Production hygiene:** built-in QA/test-first, mermaid-first for complex logic, and deployment/ops checklists.

---

## Quick Start (3 commands to run in Cursor)

1. Add these agent prompt files into `.cursor/agents/` (Analyst, PM, Architect, SM, DEV, QA, Ops).
2. Paste your project brief into `bmad-config.yaml` (example below).
3. Start Driver in a fresh chat and run `workflow-init`.

---

## Tracks & When to use them (auto-selected by `workflow-init`)

- **Quick Flow (⚡)** — Bug fixes, small features, 1–15 stories. Use `tech-spec` and go straight to DEV. Time-to-start: < 5 min.
- **BMad Method (📋)** — Products & platforms. Full PRD + architecture + UX. Good for 10–50 stories. Time-to-start: < 15 min.
- **Enterprise (🏢)** — Compliance, scale, governance. Full governance suite and security. Time-to-start: < 30 min.

> workflow-init should analyze your brief and recommend a track. If unsure, default to BMad Method.
> 

---

## Core Principles (enforced by Driver)

1. **Plan-first**: every agent returns a 2–4 line plan before producing main output.
2. **Acceptance-as-contract**: PM-created acceptance criteria are the pass/fail gate for QA.
3. **Single-source constraints**: driver-passed constraints (forbidden libs, budgets) are authoritative.
4. **Max iterations**: default `max_iters = 3` to avoid runaway cost/time.
5. **Fresh chats**: use new chat for each major workflow to maximize model context and prevent hallucination.
6. **Document sharding**: v6 improves sharding/token savings — use built-in BMad Core settings; avoid manual micro-sharding unless necessary.

---

## Recommended Files (add to project root)

- `bmad-config.yaml` (project brief, default constraints)
- `docs/bmm-workflow-status.yaml` (auto-managed progress file)
- `.cursor/agents/*.prompt.md` (agent prompts)
- `.cursor/rules/bmad.rules.mdc` (line budgets, forbidden libs)

### Example `bmad-config.yaml`

```yaml
project: "My Project"
track: auto  # auto|quick|method|enterprise
stack: browser
lineBudget: 200
forbiddenLibs: ["x-lib"]
maxIters: 3

```

---

## Driver Orchestration (concise pseudocode)

```
# Driver.start(brief)
track = workflow_init(brief)  # Quick|Method|Enterprise
call Analyst -> analyst_out (plan-first)
call PM with analyst_out -> prd_or_spec (plan-first)
if track != quick:
  call Architect -> arch_out (plan-first + mermaid)
  call PM -> create_epics_and_stories(prd, arch)
else:
  call PM -> tech_spec
call SM -> sprint_planning(if implementation)
for each story in sprint:
  call SM -> story_context
  call DEV -> dev_story (plan-first -> code + test harness)
  call QA -> run_tests & report
  if checks fail: create refinement_patch; loop up to maxIters
on success: call Ops -> deploy_ready
update bmm-workflow-status.yaml

```

---

## Agent Prompt Templates (paste each to `.cursor/agents/*.prompt.md`)

Use these as-is or tweak tone/personality.

### Driver (starter)

```
You are the BMAD Driver (Orchestrator).
Input: brief (project description) and bmad-config.yaml
Behavior:
- Determine track via workflow-init
- Enforce constraints from config
- Require plan-first from all agents
- Collect artifacts and update bmm-workflow-status.yaml
- Limit iterations to maxIters
Respond with a 2–3 sentence execution plan and next command (which agent to call).

```

### Analyst

```
You are Analyst. Input: brief.
Return JSON: { summary, userStories[], assumptions[], metrics[] }
Also include 3 quick research pointers (URLs or short rationale).

```

### PM

```
You are Product Manager. Input: analyst JSON.
Return:
- PRD.md or tech-spec.md (depending on track)
- Acceptance criteria per user story (Gherkin optional)
- Prioritization: MVP vs stretch

```

### Architect

```
You are Architect. Input: PRD/tech-spec.
Produce:
- Mermaid architecture diagram (text only)
- API contracts (endpoints + sample payloads)
- Data models (JSON schema)
- Performance & security notes + tradeoffs
Return plan-first outline (2 lines) before code/artifacts.

```

### SM (Scrum Master)

```
You are SM. Input: PRD + Architecture.
Produce sprint-status.yaml and break PRD into epics and stories.
Return a prioritized backlog and per-epic contexts.

```

### DEV

```
You are Developer. Input: story context + architecture.
Rules:
- Plan-first (3 steps)
- Single-file demo unless specified
- Include top-of-file constants (SPEED, PALETTE)
Produce: code, comments, minimal test harness, run-log template.

```

### QA

```
You are QA. Input: code + acceptance criteria.
Produce test suite (unit + integration + manual checks) with clear reproduction steps.
Return failing traces and suggested fixes.

```

### Ops

```
You are Ops. Input: deploy-ready artifacts.
Produce: deployment checklist, infra snippet (terraform/docker-compose), monitoring & rollback plan.

```

---

## Automation: Static checks and Acceptance pipeline

Driver runs these after each DEV->QA handoff:

- `line_count <= config.lineBudget`
- `banned_imports` scan
- `loop_duration` check (if animation)
- `accessibility` flags for UI (WCAG quick checks)
- `tests_pass` (unit + integration)

If any check fails, Driver generates `refinement_patch` with exact edits and re-invokes DEV. Repeat until pass or maxIters.

---

## Debugging & Recovery (practical checklist)

- **Syntax error**: return offending 5-line block + one-line fix.
- **Runtime fail**: capture stack + minimal repro HTML/entry.
- **Vibe mismatch**: request 3 micro-variants with toggles.
- **Performance**: advise low-res buffer + profiler hooks.
- **Hallucinated imports**: add to `forbiddenLibs` and re-run safe-subset.

---

## Best Practices — Efficiency & Quality (must-follow)

1. **Plan-first always** — saves tokens and iterations.
2. **Fresh chats per workflow** — prevents context bleed / hallucinations.
3. **Constrain aggressively** — line budgets, forbidden libs, single-file demos.
4. **Tests-as-contract** — QA writes tests before full feature impl.
5. **Mermaid-first for complex flows** — catches design mistakes early.
6. **Expose constants** — top-of-file for quick A/B and tuning.
7. **Use BMad Core features** — document sharding & community bundles to save tokens.
8. **Automate status updates** — Driver updates `bmm-workflow-status.yaml` after each phase.

---

## Example: Minimal Driver Starter (paste into a Cursor agent)

```
const brief = `{{PASTE BRIEF HERE}}`;
const config = readYaml('bmad-config.yaml')
const track = await workflowInit(brief, config)
// call Analyst, PM, Architect etc. following orchestration pseudocode

```

---

## Deliverables & Templates to Create in Cursor Project

- `.cursor/agents/driver.prompt.md` (Driver template)
- `.cursor/agents/analyst.prompt.md`
- `.cursor/agents/pm.prompt.md`
- `.cursor/agents/architect.prompt.md`
- `.cursor/agents/sm.prompt.md`
- `.cursor/agents/dev.prompt.md`
- `.cursor/agents/qa.prompt.md`
- `.cursor/agents/ops.prompt.md`
- `bmad-config.yaml`
- `docs/bmm-workflow-status.yaml`
- `.cursor/rules/bmad.rules.mdc`

---

## Final Notes

This refined BMAD framework is tuned for V6: scale-adaptive, architect-aware, and optimized for Cursor workflows. It keeps the best of the BMAD Method (specialized agents, tracks, BMad Core) while enforcing strict rules for quality and efficiency. Paste it into the Cursor, add the `.cursor/agents` prompts, and run `workflow-init` to let the agents recommend the ideal track and next steps.