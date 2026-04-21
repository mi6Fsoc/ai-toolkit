# Lovable—Prompting Framework

# Lovable Vibe Coding Framework

A comprehensive system for generating superior prompts and debugging effectively in Lovable.

---

## Part 1: The Prompt Generation Framework

### Phase 1: Foundation Setup

**Step 1: Clarify the Intent**
Before generating any prompt, answer these core questions:

1. **What** are you building? (Feature, component, page, or full app)
2. **Who** is the target user? (Demographics, technical level, use case)
3. **Why** does this exist? (Problem being solved, value proposition)
4. **What** is the primary user action? (Single most important interaction)

**Output format:**

```
Intent Summary:
- Building: [specific feature/component]
- For: [target user description]
- Because: [core problem/need]
- Primary action: [key user behavior]

```

---

**Step 2: Define Visual Direction**
Establish design language upfront using these elements:

1. **Aesthetic buzzwords** (choose 2-3):
    - Minimal, expressive, cinematic, playful, premium, bold, calm, sleek, developer-focused, wellness-inspired, disruptive
2. **Visual specifics**:
    - Color palette (describe tone: muted earth tones, vibrant gradients, monochrome)
    - Typography (font families, weight preferences)
    - Spacing approach (generous padding, tight/compact, balanced)
    - Surface treatment (flat, shadows, glassmorphism, gradients)
    - Border style (sharp corners, rounded, pill-shaped)

**Output format:**

```
Visual DNA:
- Vibe: [2-3 buzzwords]
- Colors: [palette description]
- Type: [font choices]
- Spacing: [approach]
- Surfaces: [treatment style]
- Borders: [corner style]

```

---

**Step 3: Map User Journey**
Chart the flow from entry to completion:

1. List each screen/section in sequence
2. Define transition logic between steps
3. Identify trust-building moments
4. Mark conversion/action points

**Output format:**

```
Journey Map:
1. [Entry point] → [what builds trust]
2. [Next section] → [what adds value]
3. [Action point] → [what prompts behavior]
4. [Result/confirmation]

```

---

### Phase 2: Prompt Construction Rules

**Rule 1: Atomic Component Thinking**
Break requests into the smallest functional units:

- ✅ "Create a card with profile image, name, verified badge, and follow button."
- ❌ "Create a user profile sectio.n"

**Atomic vocabulary to use:**

- UI atoms: button, input, card, badge, chip, toggle, modal, toast, tooltip, dropdown
- Layout: grid, flex, stack, container, section, wrapper
- States: hover, active, disabled, loading, error, success
- Interactions: click, submit, toggle, dismiss, expand, collapse

---

**Rule 2: Real Content Over Placeholders**
Always use actual copy, never lorem ipsum:

- ✅ "Headline: 'Ship faster with AI' / Subtext: 'Turn ideas into production apps in minutes'"
- ❌ "Headline text here / Description goes here."

**Why:** Real content reveals layout needs, hierarchy issues, and spacing requirements immediately.

---

**Rule 3: Structured Prompt Patterns**
Use consistent formatting for predictable results:

```
[Component type] with [specific elements]:
- [Element 1]: [description + style]
- [Element 2]: [description + style]
- [Element 3]: [description + style]

Style: [visual direction from Phase 1]
Behavior: [interactions/states]
Layout: [positioning/spacing]

```

**Example:**

```
Hero section with centered content:
- Headline: "Design Calmly" (60px, bold, gradient text)
- Subtext: "Turn stress into structure" (18px, muted color)
- CTA button: "Start Free" (rounded, hover lift effect)

Style: Calm, wellness-inspired with soft gradients
Behavior: CTA routes to /signup, gentle fade-in on load
Layout: Centered with 120px vertical padding

```

---

**Rule 4: Layered Detail Application**
Start broad, then refine in iterations:

**Layer 1 (Structure):**

```
Create a pricing table with three tiers

```

**Layer 2 (Content):**

```
Add tier names: Basic, Pro, Enterprise
Include monthly prices: $9, $29, $99
List 4 features per tier

```

**Layer 3 (Style):**

```
Use cards with soft shadows
Highlight Pro tier with accent border
Add check icons for features

```

**Layer 4 (Interaction):**

```
Add hover effect: lift + glow
"Choose Plan" buttons route to /checkout
Show annual discount toggle above cards

```

---

**Rule 5: Clarification Trigger**
End complex prompts with:

```
Ask me any questions needed to fully understand this feature and how I envision it working.

```

Use in **Chat Mode** for best results. This surfaces assumptions and edge cases before code generation.

---

### Phase 3: Specialized Prompt Types

**Type A: Data-Driven Components**
When building features that display dynamic content:

```
[Component name] that displays [data type]:

Data source: [Lovable Cloud table/API]
Display fields: [specific fields to show]
Empty state: [what shows when no data]
Loading state: [skeleton/spinner approach]
Error state: [fallback UI]

Conditional logic:
- If [condition]: show [variant]
- If [condition]: hide [element]

Behavior:
- On [interaction]: [action + state change]

```

**Example:**

```
Task list component that displays user tasks:

Data source: Lovable Cloud 'tasks' table
Display fields: title, due_date, status, priority
Empty state: "No tasks yet" with "Add Task" CTA
Loading state: 3 skeleton cards with pulse animation
Error state: Alert with retry button

Conditional logic:
- If status='completed': show checkmark, gray out text
- If due_date < today: show red badge "Overdue"

Behavior:
- On checkbox click: toggle task.completed status
- On card click: open task detail modal

```

---

**Type B: Multi-Step Flows**
For onboarding, forms, or wizards:

```
[Flow name] with [number] steps:

Step 1: [Name]
- Fields: [list inputs]
- Validation: [rules]
- Next trigger: [condition]

Step 2: [Name]
- Fields: [list inputs]
- Validation: [rules]
- Navigation: [back/next logic]

[Continue for each step]

Progress indicator: [type]
Data persistence: [where/when saved]
Exit handling: [save draft/discard]

```

---

**Type C: Responsive Layouts**
Specify breakpoint behavior explicitly:

```
[Component name] with responsive behavior:

Desktop (>1024px):
- Layout: [grid/flex structure]
- Elements: [specific arrangement]

Tablet (768-1024px):
- Layout: [adjusted structure]
- Changes: [what collapses/reflows]

Mobile (<768px):
- Layout: [stack/simplified]
- Hidden elements: [what disappears]
- Touch targets: [minimum sizes]

```

---

**Type D: Interactive Animations**
Define motion clearly:

```
[Component] with [animation type]:

Trigger: [user action/page event]
Animation:
- Element: [what animates]
- Property: [transform/opacity/scale]
- Duration: [ms]
- Easing: [ease-in/out/elastic]
- Delay: [if sequenced]

States:
- Initial: [starting position]
- Active: [mid-animation]
- Final: [end position]

```

---

## Part 2: The Debugging Framework

### Strategy 1: Diagnostic Hierarchy

When errors occur, follow this sequence:

**Level 1: Surface Analysis**

1. Read the error message completely
2. Note the file and line number
3. Identify error type (build, runtime, UI, data)
4. Check if the app is completely broken or partially functional

**Prompt template:**

```
I'm seeing this error: [exact error message]
It occurs in: [file name, line number if available]
The app is: [completely broken / partially working / specific feature broken]

```

---

**Level 2: Context Gathering**
Before attempting fixes, collect:

1. **What changed?** (last prompt or action taken)
2. **What was working?** (previous stable state)
3. **What's affected?** (specific components/features)
4. **Console logs** (copy exact output)
5. **Network calls** (failed requests in dev tools)

**Prompt template:**

```
Debugging context:
- Last change: [what I prompted/edited]
- Previously working: [feature/state description]
- Now broken: [specific issue]
- Console shows: [paste exact logs]
- Network errors: [any failed requests]

Don't fix yet - analyze what could cause this.

```

---

**Level 3: Root Cause Analysis**
Ask investigative questions:

```
What is the root cause of [specific error]?

Consider:
- Data flow: where does this data come from?
- Type mismatches: are we passing wrong types?
- Missing dependencies: is something not imported?
- State issues: is state updating correctly?
- Timing: could this be a race condition?

Explain in simple terms why this is happening.

```

---

### Strategy 2: Surgical Fixes

**Principle:** Change only what's necessary to fix the specific issue.

**Prompt structure:**

```
Fix only the [specific error] without modifying:
- [working component A]
- [working component B]
- [existing styling]

The fix should:
1. [specific change needed]
2. [verification step]
3. [ensure X still works]

Be surgical - preserve everything else.

```

**Example:**

```
Fix only the "undefined user.email" error without modifying:
- The authentication flow
- The user profile display
- Existing navigation

The fix should:
1. Add null check for user object before accessing email
2. Show loading state while user data fetches
3. Ensure profile page still displays other user fields

Be surgical - preserve everything else.

```

---

### Strategy 3: Isolation Testing

When a feature is completely dead:

**Step 1: Minimal reproduction**

```
Create a minimal version of [broken component] with:
- Only core functionality (remove extras)
- Hardcoded test data
- No external dependencies

This will help us identify if the issue is:
- In the component logic itself
- In data fetching
- In parent component integration

```

**Step 2: Progressive integration**

```
The minimal version works. Now add back:
1. [First dependency/feature]
   → Test. Does it still work?
2. [Second dependency/feature]
   → Test. Does it still work?
3. [Continue until issue reappears]

```

---

### Strategy 4: Error Loop Breakers

When "Try to Fix" fails repeatedly:

**Breaker 1: Switch to Chat Mode**

```
Let's debug this in Chat Mode. Don't generate code yet.

The error is: [description]
We've tried: [list previous fix attempts]

Before suggesting more fixes:
1. What haven't we considered?
2. Could the issue be elsewhere in the code?
3. Are we addressing symptoms instead of root cause?

```

**Breaker 2: Alternative approach**

```
The current approach isn't working. Let's try a completely different solution.

Current broken method: [how it works now]
Requirements: [what it needs to do]

Suggest 2-3 alternative approaches that achieve the same goal differently.

```

**Breaker 3: Rollback and replay**

```
I'm rolling back to [previous stable version].

Let's implement [feature] again using a different strategy:
- [New approach/pattern]
- [Key differences from failed attempt]
- [Precautions to avoid previous error]

```

---

### Strategy 5: Advanced Diagnostic Prompts

**Full Codebase Audit:**

```
Perform a comprehensive codebase audit focused on:

Architecture:
- Are components properly organized?
- Is there misplaced logic?
- Are concerns properly separated?

Code health:
- Identify overcomplicated sections
- Find potential bugs or race conditions
- Spot performance issues

Database integration:
- Are queries efficient?
- Is the schema being used correctly?
- Any duplicate or conflicting tables?

Provide prioritized recommendations WITHOUT making changes yet.

```

---

**Performance Analysis:**

```
Analyze performance bottlenecks:

Data fetching:
- Unnecessary duplicate calls?
- N+1 query patterns?
- Missing caching opportunities?

Rendering:
- Components re-rendering excessively?
- Heavy computations on main thread?
- Large lists without virtualization?

Assets:
- Oversized images or bundles?
- Opportunities for lazy loading?
- Code splitting needed?

List findings with severity ratings.

```

---

**Type Safety Check:**

```
Review type safety across the codebase:

Database → Application:
- Are DB types matching TS interfaces?
- Are we handling nulls correctly?
- Number/string mismatches?

Component props:
- Are all props properly typed?
- Any 'any' types that should be specific?
- Missing required props?

Data transformations:
- Are transformations maintaining type safety?
- Where do types break down in the flow?

Identify and list all type issues.

```

---

### Strategy 6: Preventive Debugging

**Before making fragile changes:**

```
CAUTION: The next change affects [critical system].

Before implementing:
1. Analyze all dependencies
2. Identify potential side effects
3. Plan rollback strategy if needed

Task: [what to change]

Proceed carefully and explain your approach before coding.

```

---

**Before deleting/refactoring:**

```
Before removing [component/code]:

Verify:
- Is this code actually unused?
- Check all imports and references
- Are there hidden dependencies?
- Could other features rely on this?

Only confirm deletion after verification.

```

---

### Strategy 7: Persistent Error Protocols

**When an error won't go away:**

**Protocol A: History review**

```
What have we tried so far for this error?

List:
- Each attempted solution
- Why each might have failed
- Patterns in what's not working

This helps avoid repeating failed approaches.

```

**Protocol B: Explain like I'm five**

```
Explain this error in the simplest possible terms:
- What is actually breaking?
- Why is it breaking?
- What does the system expect vs. what's happening?

Use analogies if helpful.

```

**Protocol C: Dependency chain analysis**

```
Map the dependency chain for [broken feature]:

[User action] → [triggers] → [which calls] → [which updates] → [which affects] → [ERROR]

Identify where in this chain the breakdown occurs.

```

---

## Part 3: Quality Assurance Checklist

### Before Submitting Any Prompt:

**Clarity check:**

- [ ]  Intent is stated in the first sentence
- [ ]  No ambiguous terms ("nice", "good", "better")
- [ ]  Specific measurements/values given where relevant
- [ ]  Real content provided (no placeholders)

**Completeness check:**

- [ ]  Visual direction specified
- [ ]  Behavior/interactions defined
- [ ]  States covered (loading, error, empty, success)
- [ ]  Responsive behaviour is mentioned if relevant

**Atomicity check:**

- [ ]  Broken into the smallest functional units
- [ ]  Using UI vocabulary (button, card, badge, etc.)
- [ ]  One clear focus per prompt
- [ ]  Layered complexity (not everything at once)

**Context check:**

- [ ]  Related to existing codebase features
- [ ]  Doesn't duplicate existing components
- [ ]  Considers data flow (where data comes from)
- [ ]  Specifies Lovable Cloud integration if needed

---

### After Receiving Output:

**Validation check:**

- [ ]  Does it match the intent?
- [ ]  Visual style consistent with direction?
- [ ]  Are all requested elements present?
- [ ]  Do interactions work as expected?

**Integration check:**

- [ ]  Fits with existing components?
- [ ]  Doesn't break other features?
- [ ]  Maintains design system consistency?
- [ ]  Is performance acceptable?

**Refinement questions:**

- What's almost right but needs tweaking?
- What's missing that I assumed would be there?
- What exceeded expectations?
- What should be adjusted in the next iteration?

---

## Part 4: Prompt Templates Library

### Template 1: New Feature Component

```
Create a [component name] that [primary function]:

Purpose: [why this exists]
User action: [what user does with it]

Elements:
- [Element 1]: [description, style, behavior]
- [Element 2]: [description, style, behavior]
- [Element 3]: [description, style, behavior]

Data:
- Source: [where data comes from]
- Fields displayed: [list specific fields]
- States: loading/empty/error handling

Style DNA: [2-3 buzzwords from visual direction]
- Colors: [specific palette]
- Typography: [font choices]
- Spacing: [generous/tight/balanced]

Interactions:
- On [action]: [result]
- Hover: [effect]
- Active/focus: [state]

Responsive:
- Desktop: [layout]
- Mobile: [adjusted layout]

```

---

### Template 2: Page Layout

```
Design a [page name] with [number] sections:

User journey:
[Entry] → [trust builder] → [value add] → [action]

Section 1: [Name]
- Purpose: [why it exists in flow]
- Content: [actual copy, not placeholders]
- Layout: [structure]
- CTA: [specific action]

Section 2: [Name]
- Purpose: [why it exists in flow]
- Content: [actual copy]
- Layout: [structure]
- Transition from Section 1: [how it flows]

[Continue for each section]

Overall vibe: [visual direction]
Navigation: [header/footer/menu approach]
Mobile considerations: [what changes]

```

---

### Template 3: Data-Connected Feature

```
Build a [feature name] connected to Lovable Cloud:

Database:
- Table: [table name]
- Fields used: [list specific columns]
- Relationships: [any joins needed]

Display:
- Layout: [how data is shown]
- Filtering: [any user controls]
- Sorting: [default and options]

States:
- Loading: [skeleton/spinner approach]
- Empty: [message + suggested action]
- Error: [fallback UI]
- Success: [normal view]

Interactions:
- On [user action]: [update to database]
- Validation: [rules before saving]
- Feedback: [toast/modal confirmation]

Real-time: [should updates appear live?]

```

---

### Template 4: Fix Existing Bug

```
There's an issue with [specific feature]:

Current behavior: [exactly what's happening]
Expected behavior: [what should happen]
Steps to reproduce:
1. [step]
2. [step]
3. [error occurs]

Error details:
- Message: [exact error text]
- Location: [file/line if known]
- Console logs: [paste relevant logs]

Context:
- Last working state: [when it worked]
- Recent changes: [what changed since]
- Affected scope: [what's broken]

Fix requirements:
- Resolve [specific issue]
- Preserve [working features]
- Don't modify [unrelated components]

Verify the fix doesn't introduce new issues.

```

---

### Template 5: Refinement/Polish

```
Refine [specific component] by improving:

Current state: [what exists now]
Issues to address:
- [specific problem 1]
- [specific problem 2]
- [specific problem 3]

Improvements:
1. [Change]: [from X to Y because Z]
2. [Change]: [from X to Y because Z]
3. [Change]: [from X to Y because Z]

Maintain:
- [aspect that should stay the same]
- [aspect that should stay the same]

Visual polish:
- [specific enhancement]
- [specific enhancement]

This is refinement only - don't rebuild from scratch.

```

---

## Part 5: Advanced Techniques

### Technique 1: Style Propagation

Create reusable style definitions:

```
Establish design system tokens:

Colors:
- primary: [value]
- secondary: [value]
- accent: [value]
- neutral-[100-900]: [scale]

Typography:
- heading-1: [size, weight, line-height]
- heading-2: [size, weight, line-height]
- body: [size, weight, line-height]
- small: [size, weight, line-height]

Spacing:
- xs: [value]
- sm: [value]
- md: [value]
- lg: [value]
- xl: [value]

Effects:
- shadow-sm: [definition]
- shadow-md: [definition]
- rounded-sm: [value]
- rounded-md: [value]

Apply these tokens consistently across all components going forward.

```

Then reference in subsequent prompts:

```
Create [component] using established design tokens

```

---

### Technique 2: Progressive Complexity

Build features in discrete layers:

**Layer 1 - Structure:**

```
Create basic [component] structure with:
- [core elements only]
- Static content
- No interactivity yet

```

**Layer 2 - Data:**

```
Connect to Lovable Cloud:
- Fetch from [table]
- Display [fields]
- Basic loading state

```

**Layer 3 - Interaction:**

```
Add user interactions:
- [specific action 1]
- [specific action 2]
- Form validation

```

**Layer 4 - Polish:**

```
Apply final touches:
- Animations
- Error handling
- Edge cases
- Accessibility

```

---

### Technique 3: Constraint-Based Prompting

Use constraints to guide better solutions:

```
Design [feature] with these constraints:

Must:
- [non-negotiable requirement]
- [non-negotiable requirement]

Must not:
- [forbidden approach]
- [forbidden approach]

Prefer:
- [desired approach]
- [desired approach]

Within these boundaries, optimize for [goal].

```

**Example:**

```
Design task creation form with constraints:

Must:
- Submit with Enter key
- Validate title is not empty
- Save to Lovable Cloud 'tasks' table

Must not:
- Use a modal (inline form only)
- Require more than title to create task

Prefer:
- Minimal UI (single input + button)
- Instant feedback on save
- Clear empty state

Within these boundaries, optimize for speed of task entry.

```

---

### Technique 4: Component Inheritance

Build new components from existing patterns:

```
Create [new component] based on [existing component]:

Inherit:
- [aspect to keep the same]
- [aspect to keep the same]

Modify:
- [aspect to change]: from [old] to [new]
- [aspect to change]: from [old] to [new]

Add:
- [new feature]
- [new feature]

This maintains consistency while adding new capabilities.

```

---

### Technique 5: Behavior-Driven Prompting

Start with user behavior, then describe UI:

```
User needs to [accomplish goal].

Behavior flow:
1. User [action] → System [response]
2. User [action] → System [response]
3. User [action] → System [result]

Build UI that supports this exact flow:
- [UI element] for step 1
- [UI element] for step 2
- [UI element] for step 3

Style: [visual direction]

```

**Example:**

```
User needs to quickly filter tasks by status.

Behavior flow:
1. User clicks status chip → Tasks instantly filter
2. User clicks different chip → Previous filter clears, new filter applies
3. User clicks active chip again → Filter removes, shows all tasks

Build UI that supports this exact flow:
- Horizontal row of status chips (All, Active, Completed)
- Active chip has accent background
- Smooth transition when tasks filter (200ms fade)
- Task count updates next to each status

Style: Minimal, fast, developer-focused

```

---

## Part 6: Meta-Prompting Strategies

### Strategy 1: Reverse Engineering

When you see good UI elsewhere:

```
I want to recreate this type of [component/layout]:

[Describe or show reference]

Key aspects to capture:
- [visual characteristic]
- [interaction pattern]
- [structural approach]

Adapt it to fit [your context/brand]:
- Change [aspect] to [your version]
- Keep [aspect] the same
- Add [unique element]

Make it feel native to our existing design system.

```

---

### Strategy 2: Assumption Surfacing

Let the AI challenge your thinking:

```
I want to build [feature] this way: [description]

Before implementing:
- What assumptions am I making?
- What edge cases should I consider?
- Are there better approaches I haven't thought of?
- What could go wrong with this approach?

Ask me clarifying questions before proceeding.

```

---

### Strategy 3: Documentation Generation

Have AI explain what it built:

```
Document the [component/feature] you just created:

Include:
- Purpose and use case
- Props/configuration options
- Data requirements
- Key behaviors
- Integration examples
- Known limitations

Format as inline code comments or separate doc.

```

---

### Strategy 4: Test Case Generation

Define expected behavior systematically:

```
Generate test scenarios for [feature]:

Happy path:
- User does [action] → expects [result]

Edge cases:
- What if [unusual condition]?
- What if user tries [unexpected action]?
- What if data is [edge state]?

Error cases:
- What if [failure scenario]?
- How should system recover?

List all scenarios with expected outcomes.

```

---

## Part 7: Common Patterns & Anti-Patterns

### ✅ DO: Prompt Patterns That Work

**Pattern: Incremental specificity**

```
Start: "Create a dashboard"
Better: "Create a dashboard with 4 metric cards"
Best: "Create a dashboard with 4 metric cards showing: Total Users (number + trend), Revenue (currency + percentage change), Active Projects (number + status breakdown), Tasks Completed (number + completion rate). Use grid layout, soft shadows on cards, accent color for positive trends."

```

**Pattern: State-first thinking**

```
"Create a [component] that handles:
- Loading: show skeleton
- Empty: show [message]
- Error: show [fallback]
- Success: show [normal view]
- [Special state]: show [variant]"

```

**Pattern: Behavioral specifications**

```
"On [trigger]:
1. [Immediate visual feedback]
2. [System action]
3. [Confirmation]
4. [Next state]"

```

---

### ❌ DON'T: Anti-Patterns to Avoid

**Anti-pattern: Vague direction**

```
❌ "Make it look nice"
❌ "Add some styling"
❌ "Improve the design"
✅ "Apply soft shadows, increase padding to 24px, use rounded corners (12px radius), add hover lift effect"

```

**Anti-pattern: Feature dumping**

```
❌ "Add login, dashboard, settings, profile, notifications, and dark mode"
✅ [Break into 6 separate, detailed prompts]

```

**Anti-pattern: Assuming context**

```
❌ "Fix the bug"
✅ "The login button throws 'undefined user' error when clicked. Console shows: [paste error]. This started after adding OAuth flow."

```

**Anti-pattern: Placeholder content**

```
❌ "Title text here, description goes here"
✅ "Title: 'Ship Faster', Description: 'Turn ideas into production apps in minutes, not months'"

```

**Anti-pattern: Style afterthoughts**

```
❌ Build feature → then → "Make it pretty"
✅ Define style upfront → build with style baked in

```

---

## Part 8: Workflow Integration

### Daily Workflow

**Morning session:**

1. Review what you built yesterday
2. Test functionality in preview
3. List 3 improvements or fixes needed
4. Prioritize by impact

**Building session:**

1. Start with one component/section
2. Write a detailed prompt using templates
3. Review output
4. Refine with edit button (not full rewrites)
5. Test in context
6. Move to the next component

**Debugging session:**

1. Gather all error info first
2. Ask diagnostic questions in Chat Mode
3. Understand the root cause before fixing
4. Apply surgical fix
5. Verify the fix doesn't break other features
6. Document what was fixed and why

**Polish session:**

1. Review the entire app in preview
2. Note inconsistencies
3. Prompt refinements one section at a time
4. Focus on: spacing, colors, interactions, copy
5. Test responsive behavior
6. Final accessibility check

---

### Collaboration Workflow

**When working with others:**

1. Document design decisions in prompts
2. Use version labels before major changes
3. Share specific prompts that worked well
4. Maintain style guide prompts
5. Review each other's outputs for consistency

---

## Part 9: Mastery Checklist

You've mastered Lovable prompting when you can:

**Foundation:**

- [ ]  Articulate intent in 1-2 sentences
- [ ]  Define visual direction with specific buzzwords
- [ ]  Map the user journey before building
- [ ]  Use real content from the start

**Prompting:**

- [ ]  Break features into atomic components
- [ ]  Use consistent prompt patterns
- [ ]  Specify all states (loading/error/empty/success)
- [ ]  Layer complexity progressively
- [ ]  Reference established design tokens

**Debugging:**

- [ ]  Gather complete context before fixing
- [ ]  Ask diagnostic questions first
- [ ]  Apply surgical fixes (not full rewrites)
- [ ]  Verify fixes don't break other features
- [ ]  Document root causes

**Quality:**

- [ ]  Maintain design system consistency
- [ ]  Consider responsive behavior
- [ ]  Handle edge cases
- [ ]  Optimize performance
- [ ]  Test accessibility

**Advanced:**

- [ ]  Create reusable prompt templates
- [ ]  Build component inheritance patterns
- [ ]  Generate test scenarios
- [ ]  Document as you build
- [ ]  Refactor with intention

---

## Quick Reference Card

### Prompt Formula

```
[Component type] that [function]:

Elements: [list with specifics]
Data: [source + fields + states]
Style: [vibe + specifics]
Behavior: [interactions]
Responsive: [breakpoint changes]

```

### Debug Formula

```
Issue: [specific problem]
Context: [what changed, what broke]
Error: [exact message + logs]
Analysis needed: [don't fix yet, explain]
Fix: [surgical change only]
Verify: [what must still work]

```

### Quality Gates

1. Intent clear?
2. Visual direction set?
3. Real content used?
4. States handled?
5. Responsive specified?
6. Atomic components?
7. Behavior defined?

---

This framework is your system for consistently generating superior prompts and debugging effectively in Lovable. Practice the patterns, use the templates, and adapt to your specific needs. The more you internalize these principles, the faster and better your results will become.