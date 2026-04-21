# Replit—Prompting Framework

# The Replit Vibe Coding Framework

## A Comprehensive Guide to Crafting Superior AI Prompts

---

## Core Philosophy

Vibe coding transforms AI tools into collaborative partners through strategic guidance. This framework ensures your prompts consistently generate high-quality results by combining procedural thinking, contextual precision, and iterative refinement.

---

## Part 1: The PRECISE Prompting Method

Use this 6-step checklist for every prompt:

### **P - Plan & Purpose**

Define what success looks like before writing your prompt.

**Ask yourself:**

- What specific outcome do I need?
- What does "done" look like for this task?
- Is this one feature or multiple? (Break into separate prompts if multiple)

**Template:**

```
"Create [specific component/feature] that [clear purpose].
It should [primary requirement] and [secondary requirement]."

```

**Examples:**

- ❌ "Make a login page."
- ✅ "Create a login page at /login with email and password fields (both required), a 'Sign In' button, and display error messages below the form if credentials are invalid."

---

### **R - Requirements & Constraints**

Specify exactly what the AI should and shouldn't do.

**Include:**

- **Data formats:** "Use JSON with fields: {name, email, timestamp}"
- **Technologies:** "Use Leaflet.js for maps, fetch data from OpenStreetMap API."
- **Constraints:** "Maximum 5 items per page" or "Must work on mobile screens."
- **Edge cases:** "Handle empty results, validate email format, prevent duplicate entries."

**Template:**

```
"Requirements:
- [Technology/framework to use]
- [Data structure/format]
- [Validation rules]
- [Error handling needs]

Constraints:
- [What to avoid]
- [Performance requirements]
- [Browser/device compatibility]"

```

---

### **E - Examples & Evidence**

Show, don't just tell. Eliminate ambiguity with concrete examples.

**Provide:**

- **Code snippets:** "Style buttons like this: [paste example CSS]"
- **Sample data:** "Process data in this format: [JSON example]"
- **Screenshots/mockups:** Attach wireframes or reference designs
- **Documentation links:** "Follow patterns from [URL]"

**Template:**

```
"Here's an example of what I'm looking for:
[code snippet, screenshot, or sample data]

The output should match this structure/style."

```

**Pro tip:** Upload images directly to Agent for UI/design references.

---

### **C - Context & Scope**

Give relevant information; exclude everything else.

**Do provide:**

- Relevant file names: "Modify @profile.js and @styles.css"
- Error messages: "Getting 'Cannot read property X of undefined' at line 42."
- Current state: "Users can currently add tasks but can't delete them."
- Related functionality: "This connects to the database schema in @db.js"

**Don't provide:**

- Unrelated files or code
- Entire project history for small fixes
- Previous unrelated conversation context

**When to start a New Chat:**

- Switching to a completely different feature
- Previous context is causing confusion
- Starting a fresh implementation approach

---

### **I - Incremental Steps**

Break large tasks into small, testable pieces.

**Strategy:**

1. Start with core functionality (no styling)
2. Test it works
3. Add one enhancement at a time
4. Use Checkpoints after each working step

**Example breakdown:**

```
Large task: "Build a task manager"

Incremental prompts:
1. "Create HTML structure with input field and task list container"
2. "Add JavaScript to append new tasks when user submits form"
3. "Implement task deletion with 'X' button on each item"
4. "Connect to Replit Database to persist tasks"
5. "Add styling with Tailwind classes for modern look"

```

**Rule:** If a prompt requires more than 3 distinct changes, split it up.

---

### **S - Specify Output Format**

Define exactly how you want the result structured.

**Be explicit about:**

- **Function signatures:** "Create function `calculateTotal(items: array) => number`"
- **Component structure:** "Export as default React functional component with hooks"
- **File organization:** "Create separate files: auth.js (login logic), auth.css (styles)"
- **Return values:** "Return object with {success: boolean, error: string, data: object}"

**Template:**

```
"The output should:
- [Structure requirement]
- [Return type/export format]
- [File organization]
- [Naming conventions]"

```

---

## Part 2: Debugging Mastery

### The 5-Step Debug Protocol

When errors occur, follow this systematic approach:

### **Step 1: Capture Complete Error Information**

Gather all diagnostic data before prompting:

**Checklist:**

- [ ]  Exact error message (copy full text)
- [ ]  Error location (file name, line number)
- [ ]  Where the error appears (browser console, terminal, network tab)
- [ ]  Action that triggered it (click, page load, form submit)
- [ ]  Expected vs. actual behavior

**Template:**

```
"I'm getting this error:
[paste exact error message]

Location: [file name, line number]
Occurs when: [user action]
Expected: [what should happen]
Actual: [what's happening instead]

Relevant code:
[paste 10-20 lines around error location]"

```

---

### **Step 2: Reproduce & Isolate**

Make the error predictable:

**Questions to answer:**

- Does it happen every time or intermittently?
- Does it occur with specific inputs/data?
- Does it happen in the browser console or server logs?
- Can you trigger it with a minimal example?

**Debugging aids:**

- Browser DevTools Console (F12)
- Network tab (check API responses)
- Replit Console (server-side errors)
- Add `console.log()` statements to trace execution

---

### **Step 3: Analyze & Hypothesize**

Before asking AI for help, form a hypothesis:

**Use this framework:**

```
"The error seems to be caused by [hypothesis] because [reasoning].

I think the issue is in [specific area] where [explanation].

I've already tried:
- [attempt 1 - result]
- [attempt 2 - result]"

```

**Common error patterns:**

- `undefined` → Variable not initialized or null check missing
- `404` → Wrong API endpoint or file path
- `CORS` → Server configuration or request headers issue
- `Type Error` → Data type mismatch or validation problem

---

### **Step 4: Craft Targeted Debug Prompt**

Provide AI with focused debugging context:

**Effective debug prompt structure:**

```
"I'm debugging [specific feature/function].

Error: [exact message]
Location: [file:line]

Here's the relevant code:
[paste focused snippet - 10-30 lines]

What I've verified:
- [working part 1]
- [working part 2]

What's not working:
- [failing behavior]

Context:
[any relevant data structures, API responses, or state]

Can you identify the issue and suggest a fix?"

```

**❌ Ineffective:**
"My code is broken, fix it [paste 200 lines]"

**✅ Effective:**
"My login validation fails when the email field is empty. Getting 'Cannot read property includes of undefined' at line 45 in auth.js. Here's the validation function: [paste function]. Email should show an error if empty."

---

### **Step 5: Use Checkpoints Strategically**

**Checkpoint before major changes:**

- Attempting a different implementation approach
- Refactoring working code
- Adding a complex new feature

**Rollback when:**

- AI solution breaks more than it fixes
- Error becomes more complex after changes
- You want to try a different debugging approach

**Rollback strategy:**

```
1. Identify last fully working checkpoint
2. Select "Rollback to here"
3. Try alternative prompt or approach
4. If databases involved, enable "Restore databases" option

```

---

## Part 3: Framework Application Workflow

### The Complete Vibe Coding Cycle

```
┌─────────────────────────────────────────────┐
│ 1. PLAN (Procedural Thinking)              │
│    - Define feature/fix clearly             │
│    - Break into smallest testable unit      │
│    - Visualize success state                │
└────────────────┬────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────┐
│ 2. PROMPT (Apply PRECISE Method)           │
│    ✓ Purpose clear                          │
│    ✓ Requirements specified                 │
│    ✓ Examples provided                      │
│    ✓ Context curated                        │
│    ✓ Incremental scope                      │
│    ✓ Specify output format                  │
└────────────────┬────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────┐
│ 3. CHECKPOINT (Before execution)            │
│    - Agent auto-creates checkpoint          │
│    - Note: captures full dev environment    │
└────────────────┬────────────────────────────┘
                 │
                 ▼
┌─────────────────────────────────────────────┐
│ 4. TEST (Verify results)                    │
│    - Run the code                           │
│    - Check console for errors               │
│    - Verify expected behavior               │
│    - Test edge cases                        │
└────────────────┬────────────────────────────┘
                 │
                 ▼
        ┌────────┴────────┐
        │   Works? (Y/N)  │
        └────────┬────────┘
                 │
         ┌───────┴───────┐
         │               │
    [NO] │               │ [YES]
         ▼               ▼
┌────────────────┐  ┌──────────────┐
│ 5a. DEBUG      │  │ 5b. SUCCESS  │
│ (5-Step        │  │ - Document   │
│  Protocol)     │  │ - Move next  │
│                │  │ - Checkpoint │
│ If stuck:      │  │   remains    │
│ → Rollback     │  └──────────────┘
│ → Try new      │
│   approach     │
└────────────────┘
         │
         │ [Fixed]
         └──────────┐
                    │
                    ▼
            ┌───────────────┐
            │ 6. ITERATE    │
            │ - Next feature│
            │ - Refinement  │
            │ - Enhancement │
            └───────────────┘

```

---

## Part 4: Advanced Techniques

### Leveraging Frameworks & Libraries

**Discovery prompt pattern:**

```
"What are the best options for [specific functionality]
in [your tech stack]?

I need to [requirement], considering:
- Ease of integration
- Performance
- Documentation quality

Please recommend 2-3 options with brief pros/cons."

```

**Implementation prompt pattern:**

```
"Implement [feature] using [recommended library].

Follow the patterns from [library documentation URL].

Specific requirements:
- [requirement 1]
- [requirement 2]

Here's an example from the docs that's similar: [paste example]"

```

---

### Multimodal Context Usage

**When to attach files:**

- Modifying existing code (attach 1-3 relevant files)
- Fixing bugs (attach file with error)
- Matching existing patterns (attach example file)

**When to attach images:**

- UI/UX design requirements (wireframes, mockups)
- Visual bugs (screenshot of issue)
- Reference designs (inspiration images)

**When to provide URLs:**

- API documentation
- Design system guidelines
- Library/framework docs
- Reference applications

---

### Context Management Rules

**Too much context causes:**

- AI confusion between old and new requirements
- Slower response times
- Mixed implementation patterns
- Difficulty tracking changes

**Signs you need a New Chat:**

- Switching major features (authentication → payments)
- AI keeps referencing outdated context
- Prompt requires explaining "ignore previous instructions"
- Starting an alternative implementation approach

**How to transfer context to a new chat:**

1. Summarize current state: "I have a working login system using [tech]"
2. State the new goal clearly
3. Attach only files relevant to the new feature
4. Provide specific integration points if needed

---

## Part 5: Prompt Templates Library

### Template 1: New Feature from Scratch

```
Create [feature name] for [application context].

User Story: As a [user type], I want to [action] so that [benefit].

Requirements:
- [Core requirement 1]
- [Core requirement 2]
- [Core requirement 3]

Technical Specs:
- Use [framework/library]
- Data structure: [describe or provide example]
- Integration: [how it connects to existing code]

Acceptance Criteria:
- [ ] [Testable criterion 1]
- [ ] [Testable criterion 2]

Constraints:
- [Performance/security/compatibility needs]

Here's a mockup of the expected UI: [attach image]

```

---

### Template 2: Bug Fix

```
Bug Report:

Issue: [One-sentence description]

Error Message:

```

[Exact error text]

```

Steps to Reproduce:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Expected Behavior:
[What should happen]

Actual Behavior:
[What's happening instead]

Affected Code:
File: [filename]
Lines: [line numbers]

```

[Paste relevant code section]

```

Environment:
- Browser/Device: [if relevant]
- User state: [logged in, specific data loaded, etc.]

Attempts Made:
- [What you've tried]

```

---

### Template 3: Code Refactoring

```
Refactor [specific component/function] in @[filename].

Current Issues:
- [Problem 1: e.g., hard to test]
- [Problem 2: e.g., duplicate code]
- [Problem 3: e.g., poor performance]

Goals:
- [Improvement 1: e.g., extract reusable function]
- [Improvement 2: e.g., improve readability]
- [Improvement 3: e.g., add error handling]

Constraints:
- Must maintain existing functionality
- Don't break: [specific dependencies]
- Keep same API/interface: [specify if applicable]

Current Code:

```

[Paste current implementation]

```

Preferred Pattern:
[Describe or show example of desired structure]

```

---

### Template 4: Enhancement/Iteration

```
Enhance [existing feature] in @[filename].

Current State:
[Brief description of what exists]

Enhancement Request:
Add [specific enhancement] that [purpose/benefit].

New Requirements:
- [Requirement 1]
- [Requirement 2]

Integration:
- Should work with existing [related feature]
- Use the same [data structure/API/style] as [existing component]

Example:
[Provide code snippet or screenshot of desired enhancement]

Edge Cases to Handle:
- [Edge case 1]
- [Edge case 2]

```

---

### Template 5: Debugging Prompt (Detailed)

```
Debug assistance needed for [feature/component].

Symptom:
[Clear description of unexpected behavior]

Error Details:

```

Error: [exact message]
File: [filename:line]
Stack trace: [if available]

```

Context:
This occurs when [triggering action/condition].
The feature should [expected behavior].

Relevant Code:

```

[Paste focused code section - 15-30 lines]

```

Data State:
[Relevant variable values, API responses, or state]

Investigation:
I've verified:
- ✓ [Working part 1]
- ✓ [Working part 2]

I suspect:
[Your hypothesis about the cause]

Tried:
1. [Attempt 1] - Result: [outcome]
2. [Attempt 2] - Result: [outcome]

Request:
Please identify the root cause and suggest a fix.

```

---

## Part 6: Quality Assurance Checklist

Before submitting any prompt, verify:

### Clarity Checks

- [ ]  Could someone unfamiliar with my project understand this prompt?
- [ ]  Have I used specific terms instead of vague words? ("login form" not "that thing")
- [ ]  Is my goal stated in the first 1-2 sentences?
- [ ]  Have I broken down complex requests into steps?

### Completeness Checks

- [ ]  Have I specified required technologies/frameworks?
- [ ]  Have I defined the expected output format?
- [ ]  Have I included relevant examples or mockups?
- [ ]  Have I mentioned important constraints or edge cases?
- [ ]  Have I provided error messages or context if debugging?

### Context Checks

- [ ]  Have I attached only relevant files (not the entire project)?
- [ ]  Have I mentioned integration points with existing code?
- [ ]  Is this a new feature (stay in chat) or a different feature (new chat)?
- [ ]  Have I provided enough context but not too much?

### Scope Checks

- [ ]  Is this prompt focused on ONE thing?
- [ ]  Can I test the result in under 5 minutes?
- [ ]  If not, should I break it into smaller prompts?
- [ ]  Have I planned my next checkpoint?

---

## Part 7: Common Pitfalls & Solutions

### Pitfall 1: Vague Instructions

**Problem:** "Make it better" or "Fix the styling"

**Solution:**

```
"Improve the navigation bar styling:
- Increase font size to 16px
- Add 20px horizontal padding to links
- Change hover background to #f0f0f0
- Make logo 40px height
- Align items vertically centered"

```

---

### Pitfall 2: Overloading Single Prompt

**Problem:** "Build user authentication, add profile pages, implement notifications, and create settings"

**Solution:** Break into sequence:

```
Prompt 1: "Create user signup/login with email/password"
[Test & Checkpoint]

Prompt 2: "Add profile page displaying user info from auth"
[Test & Checkpoint]

Prompt 3: "Implement notification system for user actions"
[Test & Checkpoint]

Prompt 4: "Create settings page for user preferences"

```

---

### Pitfall 3: Missing Error Context

**Problem:** "I get an error when logging in"

**Solution:**

```
"Login fails with error: 'TypeError: Cannot read property
email of null' at line 34 in auth.js.

Occurs when: User submits form with valid credentials
Expected: Redirect to dashboard
Actual: Error message, no redirect

Code at line 34:
if (user.email === loginEmail) { ... }

The user object seems to be null even though database
query returns successfully in previous line."

```

---

### Pitfall 4: Ignoring Incremental Testing

**Problem:** Requesting 10 features, then discovering nothing works

**Solution:**

- Request 1 feature
- Test thoroughly
- Create checkpoint
- Only then request the next feature
- If an error occurs, you have a clean rollback point

---

### Pitfall 5: Not Using Checkpoints

**Problem:** AI makes breaking change, you keep prompting to fix, gets worse

**Solution:**

- Before major changes: verify checkpoint exists
- After breaking change: immediately rollback
- Try different approach with new prompt
- Don't try to "fix forward" repeatedly

---

## Part 8: Prompt Refinement Process

### How to Transform Basic → Superior Prompts

### Example 1: Task Manager

**Basic Prompt (❌):**

```
"Create a task manager app"

```

**Apply PRECISE Method:**

**P - Plan & Purpose:**
"Create a task manager where users can add, complete, and delete tasks with persistent storage."

**R - Requirements:**

- Tasks have: title (required), optional description, completion status
- Store in Replit Database
- Display in list format

**E - Examples:**
Task object structure: `{id: 1, title: "Buy milk", description: "", completed: false}`

**C - Context:**
New project, no existing code, need a full-stack solution

**I - Incremental:**
Start with basic HTML/JS, then add a database

**S - Specify Output:**
Single-page app with inline JavaScript, use Replit Database for persistence

**Superior Prompt (✅):**

```
Create a task manager web application.

Core Features:
- Add new tasks with title (required) and optional description
- Mark tasks as complete/incomplete
- Delete tasks
- Tasks persist using Replit Database

Requirements:
- Single HTML page with inline JavaScript
- Task structure: {id: number, title: string, description: string, completed: boolean}
- Display tasks as a list with checkboxes for completion
- Show "No tasks yet" message when list is empty
- Add button should be disabled if title is empty

UI Layout:
- Input fields for title and description at top
- "Add Task" button
- Task list below showing: checkbox, title, delete button
- Completed tasks show with line-through text

Start with basic HTML structure and JavaScript for adding/displaying tasks.
We'll add database persistence in the next step.

```

---

### Example 2: Bug Fix

**Basic Prompt (❌):**

```
"My app is broken, please fix"

```

**Apply 5-Step Debug Protocol:**

1. Capture error: "TypeError: Cannot read property 'map' of undefined at line 67"
2. Reproduce: Happens when loading /dashboard before data loads
3. Analyze: tasks array undefined on initial render
4. Hypothesize: Component renders before data fetch completes
5. Craft targeted prompt

**Superior Prompt (✅):**

```
Debug: Dashboard crashes on initial load

Error:
TypeError: Cannot read property 'map' of undefined
File: Dashboard.jsx, line 67

Occurs when: User navigates to /dashboard
Expected: Show loading state, then display tasks
Actual: Immediate crash before data loads

Relevant code (Dashboard.jsx):
```jsx
function Dashboard() {
  const [tasks, setTasks] = useState();

  useEffect(() => {
    fetchTasks().then(data => setTasks(data));
  }, []);

  return (
    <div>
      {tasks.map(task => <TaskCard key={task.id} task={task} />)}
    </div>
  );
}

```

Analysis:
The tasks state is undefined initially, causing map() to fail
before the fetch completes.

Request:
Add proper loading state and null checking to prevent crash
while data loads.

```

---

## Part 9: Agent vs. Assistant Usage Guide

### When to Use Replit Agent

**Best for:**
- Starting new projects from scratch
- Scaffolding entire applications
- Setting up development environments
- Creating multiple connected files/features
- Complex multi-step implementations

**Agent strengths:**
- Automatic checkpoint creation
- Environment configuration
- Package installation
- Multi-file coordination
- Plan generation and approval

**Optimal Agent prompt:**
"Create [full application concept] with [key features]. Use [tech stack].
Here's a mockup: [attach image]"

---

### When to Use Replit Assistant

**Best for:**
- Quick edits to existing code
- Targeted bug fixes
- Refactoring specific functions
- Adding small enhancements
- Code explanations

**Assistant strengths:**
- Faster for small changes
- Direct file editing
- Inline suggestions
- Quick iterations
- Lower cost per interaction

**Optimal Assistant prompt:**
"In @filename, modify [specific function/section] to [precise change].
Current behavior: [X]. Desired behavior: [Y]."

---

### Transition Strategy

```

Project Start → Use Agent
↓
Build MVP → Agent checkpoints
↓
MVP Complete → Switch to Assistant
↓
Refinements → Assistant for tweaks
↓
Major Feature → Back to Agent
↓
Polish → Assistant again

```

---

## Part 10: Framework Summary Card

**THE PRECISE METHOD**

```

P - Plan & Purpose (What's the goal?)
R - Requirements & Constraints (What must/mustn't it do?)
E - Examples & Evidence (Show concrete samples)
C - Context & Scope (Relevant info only)
I - Incremental Steps (One thing at a time)
S - Specify Output Format (Define the structure)

```

**THE DEBUG PROTOCOL**

```

1. Capture (Error message, location, context)
2. Reproduce (Make it predictable)
3. Analyze (Form a hypothesis)
4. Prompt (Targeted debug request)
5. Checkpoint/Rollback (Strategic undo)

```

**THE VIBE CYCLE**

```

Plan → Prompt → Checkpoint → Test → [Works? Yes: Next feature | No: Debug] → Iterate

```

**QUALITY CHECKS**

```

✓ Clear goal in first sentence?
✓ Specific technologies mentioned?
✓ Examples/mockups provided?
✓ Only relevant context included?
✓ Testable in <5 minutes?
✓ Output format defined?

```

---

## Conclusion

This framework transforms AI from a unpredictable tool into a reliable development partner. By applying PRECISE prompting, systematic debugging, and strategic checkpointing, you'll achieve consistent, high-quality results.

**Remember:** The best prompts are clear, complete, and focused. Start with this framework, adapt it to your workflow, and iterate based on results.

**Next steps:**
1. Bookmark this framework
2. Use the templates for your next prompt
3. Apply the quality checklist before submitting
4. Track which patterns work best for your projects
5. Refine your personal prompting style over time

Happy vibe coding! 🚀

```