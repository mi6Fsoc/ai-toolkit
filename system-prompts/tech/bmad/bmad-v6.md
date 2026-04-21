# BMAD v6

# BMAD Method: Vibe Coding Efficiency Framework

> Transform chaotic "vibe coding" into professional, structured AI-driven development
> 

---

## 🚀 Quick Setup (5 Minutes)

### Installation

```bash
# Install v6 Alpha (Recommended - Latest features)
npx bmad-method@alpha install

# Or v4 Stable (Production-ready)
npx bmad-method install

```

**During installation, you'll be prompted for:**

- Project path
- Module selection (choose BMM for software/game development)
- Language preferences
- IDE integration (Claude Code, Cursor, Windsurf, VS Code)

---

## 📋 The BMAD Advantage Over "Vibe Coding"

| Traditional Vibe Coding | BMAD Method |
| --- | --- |
| ❌ Random prompts | ✅ Structured workflows |
| ❌ Context loss | ✅ Story-based context engineering |
| ❌ Inconsistent results | ✅ Repeatable processes |
| ❌ No documentation | ✅ Auto-generated PRD/Architecture |
| ❌ Single agent chaos | ✅ 21 specialized agents |

---

## 🎯 The Two-Phase Workflow

### Phase 1: PLANNING (Web UI - Cost Effective)

**Use:** Gemini 2.5 Pro/Flash, Claude, or ChatGPT Web UI

**Why:** Cheaper tokens, larger context windows

**Output:** PRD, Architecture, UX docs

### Phase 2: EXECUTION (IDE - Your Codebase)

**Use:** Claude Code, Cursor, Windsurf, VS Code

**Why:** Direct code generation with full context

**Output:** Production-ready code via story-driven development

---

## 🤖 Essential Agents & Commands

### Planning Phase Agents (Web UI)

### 1. **Analyst** 👨‍💼

```
*analyst

```

**Purpose:** Create comprehensive project brief

**Output:** Market analysis, user personas, competitive insights

**When:** Starting any new project

### 2. **PM (Product Manager)** 📝

```
*pm
*create-prd

```

**Purpose:** Transform brief into detailed PRD

**Output:** Feature requirements, user stories, acceptance criteria

**When:** After project brief is approved

### 3. **Architect** 🏗️

```
*agent architect
*create-architecture

```

**Purpose:** Design system architecture

**Output:** Tech stack, data models, API design, file structure

**When:** After PRD is complete

### 4. **UX Designer** 🎨 (Optional)

```
*agent ux
*create-ux-plan

```

**Purpose:** Design user experience

**Output:** User flows, wireframes, design system

**When:** For user-facing applications

### Execution Phase Agents (IDE)

### 5. **Scrum Master** 📊

```
*agent sm
*sprint-planning

```

**Purpose:** Break PRD into implementable stories

**Output:** Detailed story files with full context

**When:** Ready to start coding

### 6. **Developer** 💻

```
*agent dev
*implement-story <story-number>

```

**Purpose:** Implement code based on stories

**Output:** Production-ready code, tests

**When:** During development sprints

### 7. **QA (Quality Assurance)** 🧪

```
*agent qa
*review-story <story-number>

```

**Purpose:** Test and validate implementation

**Output:** Test results, bug reports

**When:** After story implementation

---

## 🔄 Complete Greenfield Workflow

### Step 1: Initialize Project

```
*workflow-init

```

Select project level:

- **Level 1-2:** Bug fixes, small features
- **Level 3-4:** Full products (PRD + Architecture)
- **Level 5:** Enterprise with compliance

### Step 2: Planning Phase (Web UI)

### Create Project Brief

```
*analyst

[Describe your project idea in natural language]
Example: "I want to build a task management app for freelancers
that integrates with Stripe for invoicing and uses AI to suggest
task priorities based on deadlines and client importance."

```

### Generate PRD

```
*pm
*create-prd

[Review and iterate on the PRD]

```

### Design Architecture

```
*agent architect
*create-architecture

[Confirm tech stack choices and architectural decisions]

```

### Optional: UX Design

```
*agent ux
*create-ux-plan

```

### Step 3: Switch to IDE

**Transfer your docs to IDE:**

- PRD → `docs/prd.md`
- Architecture → `docs/architecture.md`
- UX Plan → `docs/ux-plan.md`

### Step 4: Execution Phase (IDE)

### Generate Sprint Stories

```
*agent sm
*sprint-planning

```

### Implement Stories

```
*agent dev
*implement-story story-001

[Follow the story implementation workflow]

```

### Quality Assurance

```
*agent qa
*review-story story-001

```

### Iterate

```
*sprint-planning  # Next sprint

```

---

## ⚡ Quick Flow Workflows (For Smaller Tasks)

### Quick Feature Addition

```
*workflow quick-flow

[Describe feature]

```

**Output:** Tech spec only (no PRD), faster implementation

### Bug Fix Workflow

```
*workflow-init
# Select Level 1-2

*agent dev
[Describe the bug]

```

### Brownfield Enhancement

```
*workflow brownfield-enhancement

[Describe existing project and desired changes]

```

---

## 🎯 Workflow Selection Guide

| Project Type | Workflow | Planning Docs | Time to Code |
| --- | --- | --- | --- |
| **Bug Fix** | Quick Flow | Tech Spec | 5 min |
| **Small Feature** | Quick Flow | Tech Spec | 10 min |
| **New Product** | Greenfield | PRD + Architecture + UX | 30 min |
| **Major Update** | Brownfield | Architecture Update | 20 min |
| **Enterprise App** | Enterprise Flow | Full Governance Suite | 45 min |

---

## 💡 Pro Tips for Efficient Vibe Coding

### 1. **Use Natural Language Commands**

BMAD has excellent fuzzy matching:

```
*workflow init        ✅
*workflow-init        ✅
"workflow init"       ✅
"please init workflow" ✅

```

### 2. **Context is King**

Always reference existing docs:

```
*agent dev
@docs/prd.md @docs/architecture.md
Implement the user authentication feature from story-003

```

### 3. **Review Before Implementation**

Stop after each planning step:

- ✅ Review project brief
- ✅ Review PRD
- ✅ Review architecture
- ✅ Commit docs to git

### 4. **Use Web UI for Planning**

**Why:** 80%+ token savings

```
Planning:  Web UI (Gemini/Claude/ChatGPT)
Execution: IDE (Claude Code/Cursor/Windsurf)

```

### 5. **Keep Story Files Clean**

Each story should be:

- **Self-contained** (no external references)
- **Context-rich** (full implementation details)
- **Testable** (clear acceptance criteria)

### 6. **Leverage Agent Memory**

Stories contain everything the Dev agent needs:

- Full context from PRD/Architecture
- Implementation guidelines
- Code examples
- Testing requirements

---

## 🛠️ Advanced Commands

### Document Management

```
*shard-documents         # Break large docs into smaller files
*validate-architecture   # Check architecture consistency
*update-prd <section>   # Update specific PRD section

```

### Sprint Management

```
*sprint-review          # Review completed stories
*sprint-retrospective   # Team retrospective
*next-sprint            # Plan next sprint

```

### Agent Customization

```
*customize-agent <agent-name>  # Customize agent behavior
*list-agents                   # See all available agents
*agent-help <agent-name>       # Get agent-specific help

```

---

## 📊 Scale-Adaptive Intelligence

BMAD automatically adjusts planning depth:

### Level 1-2: Quick Changes

- ✅ Tech spec only
- ✅ Direct implementation
- ⏱️ 5-15 minutes to code

### Level 3-4: Products

- ✅ Full PRD
- ✅ Architecture design
- ✅ UX planning
- ⏱️ 30-60 minutes to code

### Level 5: Enterprise

- ✅ Compliance documentation
- ✅ Security reviews
- ✅ Governance tracking
- ⏱️ 1-2 hours to code

---

## 🎨 Customization Examples

### Customize Agent Personality

Create: `.bmad/_cfg/agents/bmm-dev.customize.yaml`

```yaml
persona:
  name: 'Senior Dev'
  communication_style: |
    - Concise and direct
    - Use code examples
    - Focus on best practices

custom_instructions: |
  - Always suggest performance optimizations
  - Include error handling in all functions
  - Write comprehensive JSDoc comments

```

### Project-Specific Settings

Edit: `.bmad/_cfg/project.yaml`

```yaml
project:
  name: 'MyAwesomeApp'
  primary_language: 'en'
  code_output_language: 'typescript'

paths:
  docs: 'documentation/'
  stories: 'planning/stories/'
  architecture: 'docs/arch/'

```

---

## 🚨 Common Pitfalls & Solutions

### Problem: Context Loss Between Agents

**Solution:** Use story files - they contain full context

```
*agent dev
*implement-story story-005  # Story has everything needed

```

### Problem: Inconsistent Code Style

**Solution:** Create coding standards document

```
docs/coding-standards.md
- Include style guide
- Code examples
- Best practices

```

### Problem: Planning Takes Too Long

**Solution:** Use appropriate workflow level

```
# Don't use full PRD for small features
*workflow quick-flow  # For small changes

```

### Problem: Agent Doesn't Understand Codebase

**Solution:** Provide context files

```
*agent dev
@docs/architecture.md
@src/config/database.ts
[Your request]

```

---

## 📈 Success Metrics

Track your improvement:

- **Story Completion Rate:** Aim for 80%+ first-pass success
- **Context Clarity Score:** Stories should be self-explanatory
- **Planning Time:** Should decrease with practice
- **Code Quality:** Should match or exceed manual coding

---

## 🔗 Quick Reference Links

- **Installation:** `npx bmad-method@alpha install`
- **Discord Community:** https://discord.gg/gk8jAdXWmj
- **GitHub Repo:** https://github.com/bmad-code-org/BMAD-METHOD
- **Web Bundles:** https://bmad-code-org.github.io/bmad-bundles/
- **YouTube Tutorials:** https://www.youtube.com/@BMadCode

---

## 🎯 Your First BMAD Project (10 Minutes)

### 1. Install BMAD

```bash
npx bmad-method@alpha install

```

### 2. Open Web UI (Gemini/Claude/ChatGPT)

Upload BMAD bundle or create custom GPT/Gem

### 3. Start Planning

```
*analyst
I want to build a simple bookmark manager that lets users
save links with tags and search functionality. Target audience
is developers who need to organize technical resources.

```

### 4. Generate PRD

```
*pm
*create-prd

```

### 5. Create Architecture

```
*agent architect
*create-architecture

```

### 6. Move to IDE

- Copy docs to project
- Load Dev agent

### 7. Generate Stories

```
*agent sm
*sprint-planning

```

### 8. Start Coding

```
*agent dev
*implement-story story-001

```

**Congratulations!** You've transformed from vibe coder to professional AI-driven developer! 🎉

---

## 📚 Next Steps

1. **Join Discord** - Get help from the community
2. **Watch Tutorials** - Learn advanced workflows
3. **Customize Agents** - Make BMAD match your style
4. **Build Your First Product** - Put theory into practice
5. **Share Your Success** - Help others learn

---

**Remember:** BMAD doesn't replace your expertise—it amplifies it! 🚀