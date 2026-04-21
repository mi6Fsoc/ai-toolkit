# Supabase—Prompting Framework

# Supabase Vibe-Coding Prompting Framework

Based on the Supabase blog article, here's a plug-and-play prompting framework you can add directly to any AI coding tool.

---

## 🚀 Quick-Start Template

Copy this entire block into your AI coding tool's system prompt or project instructions:

```markdown
# Project Context & Rules

## Project Overview
- Project Name: [YOUR_PROJECT_NAME]
- Description: [Brief description of what you're building]
- Tech Stack: [e.g., Next.js, Supabase, TypeScript, Tailwind CSS]
- Current Phase: [Planning / Prototyping / Development / Refinement]

## Architecture & Structure

```

[Paste your folder structure here or describe your architecture]

```

## Database Schema (if applicable)
```sql
-- Paste your schema or describe your data models

```

## Key Conventions

- Naming: [e.g., camelCase for variables, PascalCase for components]
- File Organization: [e.g., features-based, route-based]
- State Management: [e.g., React Context, Zustand, Redux]
- Error Handling: [Your preferred pattern]

## External Dependencies & APIs

- [List key packages, APIs, or services you're using]

## What NOT to do

- [List anti-patterns or things to avoid in your project]
- [e.g., "Don't use any CSS framework other than Tailwind"]
- [e.g., "Don't create new database tables without asking"]

## Current Task Context

[Update this section for each session with what you're working on]

```

---

## 📋 The 7 Principles Framework

Based on the Supabase article, here are the core principles to follow:

### 1. Provide Rich Context

```markdown
## Context Checklist (include relevant items):
- [ ] Tech stack and versions
- [ ] Existing code structure
- [ ] Database schema
- [ ] API contracts
- [ ] Design system/UI components available
- [ ] Authentication setup
- [ ] Environment constraints

```

### 2. Be Specific and Unambiguous

```markdown
## Task Specification Template:

### Goal
[One sentence: What should be achieved?]

### Acceptance Criteria
- [ ] [Specific, measurable outcome 1]
- [ ] [Specific, measurable outcome 2]
- [ ] [Specific, measurable outcome 3]

### Constraints
- Must use: [specific technologies/patterns]
- Must NOT: [things to avoid]
- Performance: [any requirements]

### Example Input/Output (if applicable)
Input: [example]
Expected Output: [example]

```

### 3. Use Structured Prompts

```markdown
## Structured Prompt Template:

Role: You are a [senior developer / architect / etc.] working on [project type].

Context:
[Relevant background information]

Task:
[Clear, specific task description]

Requirements:
1. [Requirement 1]
2. [Requirement 2]
3. [Requirement 3]

Output Format:
[Specify: code only, explanation + code, pseudocode first, etc.]

```

### 4. Iterate Incrementally

```markdown
## Incremental Development Flow:

### Phase 1: Plan
"Before writing code, outline your approach for [feature].
List the files you'll create/modify and the key functions needed."

### Phase 2: Scaffold
"Create the basic structure with placeholder functions and types.
Don't implement logic yet."

### Phase 3: Implement Core
"Implement the core logic for [specific function].
Focus only on the happy path first."

### Phase 4: Handle Edge Cases
"Add error handling and edge cases for [specific function].
Consider: [list edge cases]"

### Phase 5: Refine
"Review and optimize. Check for [specific concerns]."

```

### 5. Reference Examples

```markdown
## Example Reference Template:

Here's an existing pattern from our codebase:

```[language]
[Paste example code that demonstrates the pattern you want followed]

```

Follow this same pattern for [new feature]. Specifically:

- [Aspect 1 to replicate]
- [Aspect 2 to replicate]
- [What to adapt/change]

```

### 6. Validate and Verify

```markdown
## Verification Checklist:

After generating code, verify:
- [ ] Does it match the existing code style?
- [ ] Are all imports correct and available?
- [ ] Does it handle errors appropriately?
- [ ] Are types complete (no `any` if using TypeScript)?
- [ ] Does it integrate with existing code without conflicts?
- [ ] Are there any security concerns?

Ask: "Review this code for [specific concerns]. What could go wrong?"

```

### 7. Maintain a Living Document

```markdown
## Session Log Template:

### Session: [Date]
Focus: [What you worked on]

Decisions Made:
- [Decision 1]: [Reasoning]
- [Decision 2]: [Reasoning]

Code Added/Changed:
- [File 1]: [What changed]
- [File 2]: [What changed]

Known Issues/TODOs:
- [ ] [Issue 1]
- [ ] [Issue 2]

Next Session:
- [What to work on next]

```

---

## 🎯 Ready-to-Use Prompt Templates

### For New Features

```markdown
## New Feature Request

Feature: [Name]

User Story:
As a [user type], I want to [action] so that [benefit].

Technical Context:
- Related existing code: [files/components]
- Database tables involved: [tables]
- APIs to use/create: [endpoints]

Requirements:
1. [Functional requirement]
2. [UI/UX requirement]
3. [Performance requirement]

Out of Scope:
- [What this feature should NOT do]

Please:
1. First, outline your implementation approach
2. Then implement step by step
3. Explain any architectural decisions

```

### For Bug Fixes

```markdown
## Bug Fix Request

Bug: [Description]

Expected Behavior: [What should happen]

Actual Behavior: [What's happening]

Reproduction Steps:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Relevant Code:
```[language]
[Paste the code where the bug likely exists]

```

Error Messages (if any):

```
[Paste error messages]

```

Please:

1. Identify the root cause
2. Explain why it's happening
3. Propose a fix
4. Consider if this bug might exist elsewhere

```

### For Code Review

```markdown
## Code Review Request

Code to Review:
```[language]
[Paste code]

```

Context: [What this code does, why it was written this way]

Please review for:

- [ ]  Correctness
- [ ]  Performance
- [ ]  Security
- [ ]  Maintainability
- [ ]  Edge cases
- [ ]  Alignment with project conventions

Specific Concerns:
[Any particular areas you're uncertain about]

```

### For Refactoring

```markdown
## Refactoring Request

Current Code:
```[language]
[Paste current implementation]

```

Problems with Current Code:

- [Issue 1]
- [Issue 2]

Goals for Refactored Code:

- [Goal 1: e.g., "Improve readability"]
- [Goal 2: e.g., "Make it more testable"]
- [Goal 3: e.g., "Reduce duplication"]

Constraints:

- Must maintain same external interface/API
- Must not change: [things that shouldn't change]

Please:

1. Explain your refactoring strategy
2. Refactor incrementally, explaining each change
3. Highlight any behavior changes (there should be none)

```

---

## 📁 Project Rules File

Save this as `.cursorrules`, `CLAUDE.md`, `AGENTS.md`, or similar in your project root:

```markdown
# Project Rules for AI Assistants

## Identity
You are an expert developer working on [PROJECT_NAME], a [description].

## Tech Stack
- Frontend: [e.g., Next.js 14, React 18, TypeScript 5]
- Backend: [e.g., Supabase, PostgreSQL]
- Styling: [e.g., Tailwind CSS, shadcn/ui]
- Other: [e.g., Zod, React Query]

## Code Style
- Use TypeScript strict mode
- Prefer functional components with hooks
- Use named exports (not default exports)
- Error messages should be user-friendly
- All functions should have JSDoc comments for complex logic

## File Naming
- Components: PascalCase (e.g., `UserProfile.tsx`)
- Utilities: camelCase (e.g., `formatDate.ts`)
- Types: PascalCase with `.types.ts` suffix
- Hooks: camelCase with `use` prefix (e.g., `useAuth.ts`)

## Project Structure

```

src/
├── app/          # Next.js app router pages
├── components/   # Reusable UI components
├── lib/          # Utility functions and configurations
├── hooks/        # Custom React hooks
├── types/        # TypeScript type definitions
└── styles/       # Global styles

```

## Database Conventions
- Table names: snake_case, plural (e.g., `user_profiles`)
- Use Row Level Security (RLS) for all tables
- Always include `created_at` and `updated_at` timestamps
- Use UUID for primary keys

## API Conventions
- Use server actions for mutations when possible
- Handle errors with try/catch and return structured responses
- Validate all inputs with Zod

## Do NOT
- Use `any` type in TypeScript
- Skip error handling
- Create components larger than 200 lines
- Use inline styles (use Tailwind)
- Commit sensitive data or API keys

## When Uncertain
- Ask clarifying questions before implementing
- Propose multiple approaches for complex decisions
- Reference existing patterns in the codebase

```

---

## 🔄 Workflow Visualization

```
{
  "title": {
    "text": "Vibe-Coding Workflow",
    "left": "center",
    "textStyle": { "fontSize": 16 }
  },
  "tooltip": { "trigger": "item" },
  "series": [
    {
      "type": "sankey",
      "layout": "none",
      "emphasis": { "focus": "adjacency" },
      "data": [
        { "name": "Context" },
        { "name": "Specify" },
        { "name": "Structure" },
        { "name": "Generate" },
        { "name": "Validate" },
        { "name": "Iterate" },
        { "name": "Document" }
      ],
      "links": [
        { "source": "Context", "target": "Specify", "value": 10 },
        { "source": "Specify", "target": "Structure", "value": 10 },
        { "source": "Structure", "target": "Generate", "value": 10 },
        { "source": "Generate", "target": "Validate", "value": 10 },
        { "source": "Validate", "target": "Iterate", "value": 7 },
        { "source": "Validate", "target": "Document", "value": 3 },
        { "source": "Iterate", "target": "Generate", "value": 5 },
        { "source": "Iterate", "target": "Document", "value": 2 }
      ],
      "lineStyle": { "color": "gradient", "curveness": 0.5 }
    }
  ]
}

```

---

## ✅ Quick Reference Checklist

Before each prompt, ensure you've included:

| Element | Check |
| --- | --- |
| Context | Tech stack, relevant files, constraints |
| Goal | Clear, single objective |
| Requirements | Specific, measurable criteria |
| Examples | Reference patterns or code |
| Scope | What's in AND out of scope |
| Format | Expected output format |

---

## 💡 Pro Tips from the Article

1. Start with planning prompts before coding prompts
2. Keep context fresh — update your rules file as the project evolves
3. Use the AI to review its own code before accepting
4. Break complex features into multiple prompts
5. Save successful prompts as templates for reuse
6. Include "what not to do" to prevent common mistakes

---

*Copy the sections you need directly into your coding tool. Customize the bracketed `[PLACEHOLDERS]` for your specific project.*