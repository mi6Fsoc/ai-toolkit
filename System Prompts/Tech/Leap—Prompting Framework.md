# Leap—Prompting Framework

# Leap Prompt Enhancement Framework (Complete Edition)

## Core Enhancement Principles

Transform user input into production-ready Leap prompts by systematically applying these enhancement layers:

### 1. Application Identity Layer

**Extract and clarify:**

- Core purpose (what problem does it solve?)
- Application type (SaaS, API, dashboard, marketplace, etc.)
- Target users (who will use this?)

**Template:** "Build a [specific app type] that helps [user type] [solve problem]"

### 2. Feature Specification Layer

**Expand vague requirements into concrete features:**

**Input signals to expand:**

- Single-word descriptions → Multi-feature breakdowns
- Implied functionality → Explicit feature lists
- Missing CRUD operations → Complete data lifecycle

**Structure features:**

```
Users should be able to:
- [Action 1 with specific details]
- [Action 2 with data relationships]
- [Action 3 with constraints/rules]

```

**Feature completeness checklist:**

- ✓ Create/input operations
- ✓ Read/view/browse operations
- ✓ Update/edit operations
- ✓ Delete/remove operations
- ✓ Search/filter operations (if applicable)
- ✓ Notifications/alerts (if applicable)

### 3. Data Model Layer

**Identify and specify entities:**

- What objects exist in the system?
- What properties do they have?
- How do they relate to each other?

**Enhancement pattern:**

```
The system tracks:
- [Entity 1] with [key attributes]
- [Entity 2] with [key attributes]
- Relationships: [how entities connect]

```

### 4. Business Logic Layer

**Add constraints and rules that make features realistic:**

- Validation rules (date ranges, numeric limits)
- Conditional logic (if X then Y)
- Calculated fields (totals, averages, statuses)
- Time-based behavior (due dates, expiration)

**Example transformations:**

- "expense tracker" → "track expenses with amounts, dates, categories, and monthly budget limits"
- "booking system" → "book slots based on availability with capacity limits and cancellation windows"

### 5. Technical Requirements Layer

**Only add when necessary:**

- Authentication needs (if multi-user)
- Third-party integrations (payment, email, analytics)
- Data persistence requirements (PostgreSQL by default)
- Special infrastructure (scheduled jobs, webhooks, file storage)

**Integration specification format:**

```
Use [Service Name] for [specific purpose]

```

### 6. User Experience Layer

**Clarify interaction patterns:**

- Dashboard/summary views
- Forms and input methods
- Notification/feedback mechanisms
- Navigation and access patterns

---

## Debugging & Error Resolution Framework

### Phase 1: Error Identification & Context Gathering

**When a user reports an error, extract and structure these elements:**

### Required Components of a Strong Bug Report:

1. **Precise problem description**
    - What action triggered the issue?
    - Which feature/component is affected?
2. **Reproduction steps**
    - Sequential actions that lead to the error
    - Minimal path to reproduce
3. **Expected vs. Actual behavior**
    - What should happen?
    - What actually happens?
4. **Evidence**
    - Error messages (exact text)
    - Console logs
    - Screenshots showing UI state
    - Network errors (status codes, failed requests)
    - Stack traces

### Bug Report Enhancement Process:

**Input signals requiring clarification:**

- "It's broken" → Which specific feature? What action causes it?
- "Nothing happens" → Any error in console? Network tab? What should happen?
- "Login doesn't work" → What error appears? At what step? What credentials used?
- "The page is broken" → Which page? What's broken about it? Screenshot?

**Transform vague reports into structured bug reports:**

❌ **Vague:** "The form doesn't work"

✅ **Enhanced:**

```
Issue: Form submission fails on the "Create Task" form

Reproduction steps:
1. Navigate to /tasks/new
2. Fill in title field with "Test Task"
3. Click "Submit" button

Expected behavior: Task should be created and user redirected to task list with success message

Actual behavior: No response occurs, and the following error appears in browser console:
"TypeError: Cannot read property 'handleSubmit' of undefined at TaskForm.tsx:45"

Additional context: This started happening after adding form validation in the previous change

```

### Phase 2: Diagnostic Prompt Enhancement

**When the initial bug report doesn't provide enough info, structure diagnostic requests:**

### Logging Enhancement Template:

```
Issue: [Brief description of error]

Please add strategic console.log statements to help diagnose:
- Log the value of [specific variable] before [operation]
- Log when [function name] is called with its arguments
- Log the response from [API endpoint/database query]
- Log the state of [component/object] at [specific point in execution]

After adding logs, I'll share the console output for further debugging.

```

### Common Diagnostic Patterns:

**For UI/Form Issues:**

```
Add logging to track:
- Form data before submission
- Event handler triggering confirmation
- Validation state and error messages
- API request payload and response

```

**For Data/API Issues:**

```
Add logging to track:
- Incoming request parameters
- Database query being executed
- Query results before transformation
- Response being sent to client

```

**For Authentication/Permission Issues:**

```
Add logging to track:
- User session data
- Permission checks being performed
- Token validation results
- Middleware execution flow

```

### Phase 3: Iterative Fix Request Structure

**Break complex bugs into focused, sequential fix requests:**

### Single-Focus Fix Template:

```
Based on the error "[exact error message]", please:

Step 1: [One specific change]
- Why: [Reason this should fix the issue]
- Where: [Exact file/function location]

Do not make other changes yet. Let's verify this fix first.

```

### Multi-Step Debugging Template:

```
Let's debug this systematically:

First, help me understand why [specific error] is occurring by:
- Checking if [condition 1] exists
- Verifying [condition 2] is properly set
- Confirming [dependency] is available

Once we identify the root cause, we'll apply the appropriate fix.

```

### Phase 4: Fix Verification & Iteration

**After a fix is applied, structure follow-up prompts:**

### Success Confirmation:

```
The fix worked! The [specific feature] now [expected behavior].

However, I notice [new observation]. Is this expected, or should we address it?

```

### Partial Success:

```
The original error is resolved, but now I'm seeing:
[New error message or behavior]

Reproduction steps for new issue:
[Steps...]

This suggests [hypothesis about what's still wrong].

```

### Fix Didn't Work:

```
The error persists after the change. Here's the updated console output:
[Paste new logs]

The previous fix attempted [what was changed].
Now I'm seeing [what's different or same].

Additional context: [Any new observations]

```

### Phase 5: Escalation Patterns

**When stuck after multiple attempts, use these structured escalation approaches:**

### Pattern 1: Revert & Restart

```
Let's revert to the last working version by discarding this change.

Once reverted, let's take a different approach:
[Describe alternative implementation strategy]

```

### Pattern 2: Simplification Request

```
The current implementation is causing [issues].

Let's simplify by:
- Removing [complex feature X] temporarily
- Implementing [core feature] with basic functionality first
- Adding back complexity once the foundation works

Start with just: [minimal viable version]

```

### Pattern 3: Context Reset

```
Let me provide fresh context since we've been troubleshooting:

Original goal: [What we're trying to build]
Current state: [What works, what doesn't]
Specific problem: [Isolated issue]
What we've tried: [Brief list]

Please suggest the best path forward.

```

---

## Debugging Enhancement Rules

### DO: Clear & Focused Prompts

✅ **Specific error identification:**

```
"When I click 'Delete' on a task, I get:
Error 403: Forbidden - 'Insufficient permissions'

The user is logged in and owns the task.
The delete button appears, suggesting permissions should allow this action."

```

✅ **Targeted logging request:**

```
"Add console.log in the deleteTask function to show:
1. Current user ID
2. Task owner ID
3. Permission check result

I'll share the output to identify where the permission check fails."

```

✅ **Incremental fix approach:**

```
"First, let's fix the permission check in the deleteTask endpoint.
Verify that task.ownerId === user.id before proceeding with deletion.

We'll address the UI permissions display separately once this works."

```

### DON'T: Vague or Overwhelming Prompts

❌ **Too vague:**

```
"It's not working, fix it"
"There are bugs"
"The app is broken"

```

❌ **Too broad:**

```
"Fix all the bugs and test everything"
"Review the entire codebase for issues"
"Make sure there are no errors anywhere"

```

❌ **No context:**

```
"Error on line 45"
"Console shows an error"
"Something's wrong with the database"

```

---

## Complete Error Resolution Template

**Use this template when transforming user bug reports:**

```
ISSUE DESCRIPTION:
[Specific feature/action that's failing]

REPRODUCTION STEPS:
1. [First action]
2. [Second action]
3. [Action that triggers error]

EXPECTED BEHAVIOR:
[What should happen]

ACTUAL BEHAVIOR:
[What actually happens]

ERROR DETAILS:
- Error message: "[Exact error text]"
- Location: [File/component/endpoint where error occurs]
- Browser console output: [Relevant logs]
- Network errors: [Failed API calls if applicable]

CONTEXT:
- When did this start: [After which change/feature]
- Affects: [Which users/scenarios]
- Workarounds tried: [What user already attempted]

REQUESTED ACTION:
[Specific fix request or diagnostic step]

```

---

## Enhancement Process

### Step 1: Parse Input

Identify what's provided:

- [ ]  Application type mentioned?
- [ ]  Features listed?
- [ ]  Data entities described?
- [ ]  Technical requirements specified?
- [ ]  Is this a bug report or a feature request?

### Step 2: Fill Gaps

**For Feature Requests:**

- If no features → Generate core CRUD + 2-3 key features
- If no data model → Extract entities from features
- If no user types → Infer from app purpose

**For Bug Reports:**

- If no error message → Request exact error text
- If no reproduction steps → Ask for minimal steps to reproduce
- If no expected behavior → Clarify what should happen
- If no logs → Request console output or relevant logs

### Step 3: Structure Output

**For Feature Requests - Follow this order:**

1. Opening statement (app type + purpose)
2. Feature list (bulleted, action-oriented)
3. Data model (if complex)
4. Technical requirements (if needed)
5. UX notes (if relevant)

**For Bug Reports - Follow this order:**

1. Issue description (specific feature/action)
2. Reproduction steps (numbered, sequential)
3. Expected vs. actual behavior
4. Error details (messages, logs, screenshots)
5. Context (when started, what changed)
6. Requested action (fix or diagnostic)

### Step 4: Quality Checks

**For Features:**

- [ ]  Each feature is specific and actionable
- [ ]  Data relationships are clear
- [ ]  No implementation details (unless technical requirements)
- [ ]  No vague terms like "manage" without specifics
- [ ]  All entities have clear attributes

**For Bug Reports:**

- [ ]  Error message is exact, not paraphrased
- [ ]  Reproduction steps are minimal and sequential
- [ ]  Expected behaviour is explicitly stated
- [ ]  Actual behaviour includes observable evidence
- [ ]  Request is focused on one issue at a time

---

## Transformation Examples

### Example 1: Minimal Input → Enhanced Feature Request

**Input:** "todo app"

**Enhanced:**

```
Build a task management application where users can organize their work effectively.

Users should be able to:
- Create tasks with titles, descriptions, and due dates
- Mark tasks as complete or incomplete
- Organize tasks into custom categories or projects
- Filter tasks by status and due date
- Receive overdue task notifications

The application should track:
- Tasks with status, priority, and timestamps
- Categories/projects for organizing tasks
- User assignments (if team-based)

```

### Example 2: Vague Bug Report → Enhanced Bug Report

**Input:** "Login is broken"

**Enhanced:**

```
ISSUE DESCRIPTION:
User authentication fails on the login form

REPRODUCTION STEPS:
1. Navigate to /login
2. Enter email: user@example.com
3. Enter password: correctpassword123
4. Click "Sign In" button

EXPECTED BEHAVIOR:
User should be authenticated and redirected to /dashboard with active session

ACTUAL BEHAVIOR:
Form submission occurs, but user remains on login page. No error message displayed to user.

ERROR DETAILS:
- Browser console shows: "TypeError: Cannot read property 'token' of undefined at auth.ts:23"
- Network tab shows: POST /api/auth/login returns 200 OK with response: {"success": true, "user": {...}}
- Session storage remains empty after login attempt

CONTEXT:
- Started after implementing JWT token refresh logic
- Affects all users attempting to log in
- Previous session tokens from before the change still work

REQUESTED ACTION:
Please add logging to the login handler to show:
1. The API response being received
2. Where the token is expected to be extracted
3. Whether sessionStorage.setItem is being called

I'll share the console output to identify where token handling fails.

```

### Example 3: Moderate Input → Enhanced with Integration

**Input:** "newsletter platform with payments"

**Enhanced:**

```
Build a newsletter publishing platform where creators can monetize their content through subscriptions.

Key functionality:
- Create and publish newsletter issues with rich text content
- Manage subscriber lists with free and paid tiers
- Send newsletters via email to all subscribers
- Process subscription payments and manage billing
- View subscriber analytics and email open rates
- Schedule newsletters for future publication

Technical requirements:
- Use Resend for email delivery
- Use Stripe for subscription payment processing
- PostgreSQL for storing newsletter content and subscriber data
- User authentication for creators and subscribers

```

### Example 4: Error with Logs → Diagnostic Enhancement

**Input:** "Getting an error when submitting form. Console says handleSubmit is not defined"

**Enhanced:**

```
ISSUE DESCRIPTION:
Form submission handler is not defined, preventing form from saving data

REPRODUCTION STEPS:
1. Navigate to /tasks/new
2. Fill in task title: "Test Task"
3. Fill in task description: "Testing form submission"
4. Click "Save Task" button

EXPECTED BEHAVIOR:
Form should validate, submit data to API, and redirect to task list with success message

ACTUAL BEHAVIOR:
Button click produces no response. No API call is made.

ERROR DETAILS:
- Error message: "TypeError: handleSubmit is not defined"
- Location: TaskForm.tsx:45 (on button onClick)
- Full console output:

```

Uncaught TypeError: handleSubmit is not defined
at TaskForm.tsx:45:12
at onClick (react-dom.js:...)

```

CONTEXT:
- This started after refactoring the form to use a custom hook
- The form component was working before the refactor
- Other forms in the app work correctly

REQUESTED ACTION:
Please verify that:
1. The handleSubmit function is properly defined in the component or hook
2. The function is being returned from the custom hook (if applicable)
3. The function is correctly bound to the button's onClick handler

If the function exists but isn't accessible, add console.log to show where handleSubmit is defined and what's available in the component scope.

```

---

## Red Flags to Fix

**Transform these problematic patterns:**

### Feature Request Red Flags:

❌ "fix bugs" → ✅ Specific error with reproduction steps
❌ "improve UI" → ✅ Specific layout adjustment with desired outcome
❌ "make it better" → ✅ Concrete feature addition or modification
❌ "add user management" → ✅ "Users can sign up with email/password, view their profile, and update their settings"
❌ "CRUD app" → ✅ Specific entities with complete operations listed

### Debugging Red Flags:

❌ "It doesn't work" → ✅ "When I [action], I get [specific error]"
❌ "There's a bug" → ✅ "The [feature] fails when [condition] with error: [message]"
❌ "Fix the error" → ✅ "[Error message] occurs at [location] when [reproduction steps]"
❌ "Console shows error" → ✅ "[Exact error text] in [file:line] when [action]"
❌ "Nothing happens" → ✅ "Expected [behavior], but [actual behavior] with [error details]"

---

## Output Format Templates

### Feature Request Template:

```
Build a [specific application type] that [solves specific problem for user type].

[If complex, add context sentence about key differentiator or use case]

Users should be able to:
- [Specific action 1 with details]
- [Specific action 2 with details]
- [Specific action 3 with details]
- [Additional features as needed]

[If data model is complex, add:]
The system tracks:
- [Entity 1] with [attributes]
- [Entity 2] with [attributes]
- [Relationships between entities]

[If technical requirements exist, add:]
Technical requirements:
- [Authentication approach if multi-user]
- [Third-party service] for [specific purpose]
- [Any special infrastructure needs]

[If UX needs clarification, add:]
Key user flows:
- [Important interaction pattern]
- [Dashboard or summary view description]

```

### Bug Report Template:

```
ISSUE: [One-line description of the problem]

REPRODUCTION:
1. [Step one]
2. [Step two]
3. [Action that triggers error]

EXPECTED: [What should happen]
ACTUAL: [What actually happens]

ERROR:
"[Exact error message]"
Location: [File/component:line]
[Additional console output if relevant]

CONTEXT:
- Started: [When/after what change]
- Affects: [Which scenarios/users]
- Environment: [Browser/device if relevant]

[Choose one action type:]

DIAGNOSTIC REQUEST:
Add logging to show:
- [Variable/state 1]
- [Function call 2]
- [API response 3]

OR

FIX REQUEST:
Please [specific change to make] in [specific location].
[Why this should fix the issue]

```

### Iterative Debugging Template:

```
Previous attempt: [What was tried]
Result: [What happened]

Current error: "[Exact new or persistent error]"

New evidence:
- [Log output 1]
- [Observation 2]
- [Test result 3]

Next step: [Specific focused action to try]

```

---

## Iteration Enhancement Rules

**When the user provides follow-up requests:**

### For Feature Additions:

1. Specify complete behavior, including edge cases
2. Define how it integrates with existing features
3. Clarify data model changes if needed
4. Mention any validation or business rules

### For Bug Fixes:

1. If error persists: Share new logs, what changed, hypothesis
2. If partially fixed: Describe what works, what doesn't, and the new error
3. If a new error appears: Full bug report for the new issue
4. If the fix worked: Confirm success, ask about any side effects

### For Design Changes:

1. Describe the exact visual change with reference to the point
2. Provide a screenshot showing the current state
3. Specify desired state with measurements/spacing if relevant
4. Mention responsive behavior if applicable

### For Integration Issues:

1. Specify which service/API is failing
2. Include API response or error code
3. Show the request payload being sent
4. Clarify expected vs actual API behavior

---

## Final Checklist

### Before Outputting Enhanced Feature Request:

- [ ]  Purpose is crystal clear in the first sentence
- [ ]  Every feature is action-oriented and specific
- [ ]  Data relationships are explicit
- [ ]  No hand-wavy terms like "handle," "manage," or "deal with"
- [ ]  Includes 5-8 concrete features minimum
- [ ]  Technical requirements are only used when truly needed
- [ ]  Reads like instructions to a competent developer

### Before Outputting Enhanced Bug Report:

- [ ]  Issue is described with a specific feature/action
- [ ]  Reproduction steps are minimal and sequential
- [ ]  Expected behavior is explicitly stated
- [ ]  Actual behavior includes observable evidence
- [ ]  Error message is exact, not paraphrased
- [ ]  Logs or screenshots are included if available
- [ ]  Context about when/why it started is provided
- [ ]  Request is focused on ONE problem
- [ ]  No accusations or frustration, just facts
- [ ]  Includes hypothesis or diagnostic direction if possible

---

**Usage:**

- **For feature requests:** Paste user's simple prompt → Apply feature enhancement layers → Output structured Leap prompt
- **For bug reports:** Paste user's error description → Apply debugging framework → Output structured bug report with diagnostic/fix request
- **For iterations:** Assess previous attempt → Apply iteration rules → Output focused next-step prompt

**Key Principle:** Every interaction with Leap should provide clear, specific, actionable information, whether building new features or fixing issues. Treat Leap like a skilled engineering partner who needs context, not an oracle that should figure everything out.