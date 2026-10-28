# Anti-slop: production interface design playbook

Version 3.0 · Extended edition · 29 October 2026

**Purpose:** Create distinctive, coherent interfaces that serve real people and real tasks. Prevent interchangeable layouts, invented content, decorative clutter, and unfinished behaviour. Preserve usability, accessibility, performance, and maintainability throughout.

Adapted from the supplied [pols.dev anti-slop design law](https://pols.dev/slop.md). This is an independent revision, not an official update.

**Navigation:** [Execution path](#2-quick-execution-path) · [Art direction](#4-art-direction-and-project-specificity) · [Components](#10-component-instructions) · [Accessibility](#14-accessibility-requirements) · [Verification](#17-verification-procedure) · [Release gate](#19-release-gate-and-handoff) · [Templates](#20-reusable-working-templates)

## 1. Operating principles

### 1.1 What quality means

A strong interface makes its purpose clear, presents trustworthy information, helps users act, and expresses a coherent point of view. It works beyond the ideal screenshot: on small screens, with long content, through keyboard navigation, during loading, and after failures.

“Slop” means choices made without regard to the brief: generic copy, unrelated visuals, repeated stock compositions, arbitrary effects, or controls with no working outcome. No individual font, colour, layout, punctuation mark, or icon library proves poor quality or AI authorship.

**Decision order:** truthful and functional → usable and accessible → faithful to the brief → coherent and distinctive → decorative refinement. Later qualities cannot compensate for failures in earlier ones.

### 1.2 Requirement levels

- **MUST / MUST NOT:** delivery requirements within the applicable scope. A failure must be fixed or disclosed as an unresolved blocker; never mark it passed.
- **SHOULD / SHOULD NOT:** defaults. Depart when the brief, existing system, or user evidence supports a better choice. Record only material exceptions.
- **MAY:** optional techniques. Their absence is not a defect.

Numbered procedures describe the execution sequence. Use relevant modules; do not treat every optional component or effect as work that must be added.

### 1.3 Authority and scope

Apply this playbook within the governing project instructions. Explicit user direction and project requirements override aesthetic defaults. If a direction conflicts with accessibility, truthful content, or required behaviour, identify the conflict and propose a concrete resolution.

MUST preserve approved features, content, routes, assets, CMS connections, analytics, metadata, and integrations unless changing them is part of the task. Do not use a design improvement as permission to rebuild unrelated areas.

Do not recite this document, announce compliance rituals, or promise perfection. Show decisions through the work and support completion claims with actual verification.

## 2. Quick execution path

Use this sequence as the working checklist. The later sections explain how to execute each step.

1. **Read the brief:** identify the audience, primary task, deliverable, and preservation constraints.
2. **Inspect the system:** review affected screens, routes, components, tokens, assets, data, and required checks.
3. **Choose the direction:** define the visual character and content structure; extend an approved direction when one exists.
4. **Map the journey:** specify what users need to understand, what they can do, and what confirms the result.
5. **Build a representative slice:** complete one meaningful screen or section with real content and working behaviour.
6. **Establish the system:** extract reusable tokens and components from decisions that have proved useful.
7. **Complete applicable states:** include loading, empty, error, success, unavailable, keyboard, and touch behaviour.
8. **Refine expression:** add justified imagery, composition, and motion after the foundation works.
9. **Verify:** inspect rendering, exercise interactions, test relevant edge cases, and run required project checks.
10. **Close:** fix failures by impact, recheck affected areas, and report verified results and remaining limitations.

### Choose the appropriate depth

| Task | Required approach | Avoid |
| --- | --- | --- |
| Local fix | Inspect the affected component and callers; make the smallest coherent change; verify affected states and widths. | Restarting brand exploration or refactoring unrelated code. |
| New page or feature | Define the task, content, direction, states, responsive behaviour, and relevant integration checks. | Completing only the desktop happy path. |
| Broad redesign | Inventory shared patterns and preserved systems; establish direction with a representative slice; roll out and verify systematically. | Replacing every page independently with inconsistent styling. |

Scale the review to the risk. Shared navigation, checkout, authentication, and data mutations require more coverage than a decorative local change. Small tasks do not require separate planning documents.

## 3. Discovery and preservation

### 3.1 Establish the brief

Resolve these points from supplied context, existing content, and the project itself:

| Question | Working answer |
| --- | --- |
| Who is this for? | Audience, familiarity, device context, language, and relevant constraints. |
| What must they accomplish? | One primary task and the supporting tasks needed to complete it. |
| What must they understand? | Offer, capability, price, conditions, evidence, or workflow. |
| What is already true? | Verified product behaviour, approved copy, genuine proof, existing data. |
| What must remain intact? | Features, design assets, CMS fields, routes, tracking, integrations, and approved behaviours. |
| What defines success? | Observable acceptance criteria within the deliverable. |
| What is unavailable? | Missing assets, unknown facts, incomplete endpoints, or unverified assumptions. |

Ask only when an unknown materially changes the outcome or would cause costly rework. Otherwise use a reversible assumption and identify it briefly. Never invent facts to fill a gap.

### 3.2 Inspect an existing project

1. Read applicable project instructions and identify the framework, styling approach, package manager, and scripts.
2. Inspect the affected route and its shared dependencies before editing.
3. Review the current interface in the browser when available; note behaviour as well as appearance.
4. Locate existing tokens, components, assets, validation, loading, and error patterns.
5. Identify content sources and connections that the change must preserve.
6. Record a compact baseline: affected areas, known defects, existing check failures, and intended changes.

For a redesign, use a preservation list. For a local fix, a short working note is enough. Do not produce a lengthy inventory that will not influence implementation or verification.

### 3.3 Define acceptance before polishing

Write acceptance criteria as observable outcomes: the destination opens, the submitted value is retained on error, the mobile menu can be dismissed, or the comparison remains readable at narrow widths.

Do not substitute “looks premium,” “feels modern,” or “passes the anti-slop check” for task criteria. Visual character belongs in the direction note; behaviour needs observable results.

## 4. Art direction and project specificity

### 4.1 Choose a coherent direction

For a new visual direction:

1. Derive two plausible approaches from the audience, content, and brand.
2. Compare them for relevance, clarity, asset availability, accessibility, and implementation cost.
3. Select one. Do not build two complete interfaces unless requested.
4. Write a five-line direction note using the template in Section 20.
5. Build a representative slice before extending the direction across the project.

For an established product, extend its system. Introduce a new direction only when the task calls for one.

Use specific design commitments: composition, image treatment, density, typographic character, contrast, and interaction tone. Adjectives alone are insufficient; translate each intended quality into something visible or behavioural.

### 4.2 Establish a signature where useful

Brand-led interfaces SHOULD have a recognisable defining decision. It can be a typographic composition, photographic treatment, accurate product demonstration, illustration system, or distinctive arrangement of useful content.

Select a signature that:

- Relates directly to the product, organisation, or audience.
- Remains legible and meaningful on a small screen.
- Can be executed with available assets and time.
- Extends naturally into other relevant sections.
- Does not delay the primary action or consume the performance budget without justification.

A signature does not require a 3D object, mascot, paid font, custom silhouette, animated background, or full-screen hero. In a task-heavy application, excellent information hierarchy and workflow can carry the identity.

### 4.3 Use references as evidence

1. Identify what is relevant in each reference: hierarchy, density, pacing, typography, material, or interaction.
2. Separate those principles from the reference's brand, copy, assets, and product.
3. Translate the principles into the current brief.
4. Check that the resulting composition is original and appropriate.

Do not reproduce a reference's content, identity, artwork, or distinctive composition wholesale. Do not claim to have inspected a reference when it was unavailable.

### 4.4 Run the specificity checks

- **Substitution:** Would replacing the name make the page fit an unrelated business? Strengthen its content, proof, and composition.
- **Purpose:** Does each element explain, organise, guide, prove, or express something relevant? Remove elements that do none of these.
- **Accumulation:** Are several stock effects or section patterns doing the visual work? Simplify the combination.
- **Continuity:** Does the direction remain coherent after the hero, in forms, in the footer, and on mobile?

Do not apply the substitution test to standard controls in isolation. Familiar buttons, inputs, navigation, and tables should remain understandable.

## 5. Information architecture, copy, and action

### 5.1 Build the content sequence

1. List the questions users need answered to complete the primary task.
2. Attach real content or evidence to each question.
3. Order the answers by decision sequence and importance.
4. Remove sections that repeat another section or exist only to fill a template.
5. Make each section's role clear through its heading, content, and relationship to adjacent sections.
6. Identify the action that follows understanding; place it where useful.

Marketing pages need relevance, evidence, and a credible next step. Product screens need orientation, available actions, system state, and recovery. Do not force both into the same page structure.

### 5.2 Write useful copy

- MUST preserve supplied facts, meaning, required conditions, and material limitations.
- SHOULD use concrete descriptions of what the product does, who it serves, and what happens next.
- SHOULD remove repeated claims, empty superlatives, redundant labels, and decorative slogans that obscure the offer.
- MUST retain instructions, pricing terms, qualifications, and error-recovery guidance that affect decisions.
- SHOULD use familiar language and short paragraphs. Vary sentence structure naturally; punctuation is not a quality test.
- MUST keep names, amounts, units, dates, and terminology consistent across screens.

When a fact is missing, omit it, mark it as unresolved in working material, or use an explicitly labelled prototype fixture. Do not publish an unresolved placeholder as final content.

### 5.3 Design the action hierarchy

1. Identify the primary action for the current context.
2. Name it by its outcome, using enough context to be understood.
3. Add a secondary action only when it supports a real alternative path.
4. Differentiate importance through placement and visual emphasis.
5. Confirm that the destination or operation matches the label.

Filled and outlined buttons are valid tools; using the same pair everywhere without considering the task is the failure. Keep actions stable under pointer movement. A hover effect must not make a target difficult to activate.

### 5.4 Keep proof and persuasion honest

MUST NOT invent customers, reviews, testimonials, certifications, outcomes, usage metrics, integrations, scarcity, countdown deadlines, or popularity claims.

Use actual product behaviour, authorised work, documented capabilities, or verified relationships as evidence. A genuine deadline may have a countdown; an open-ended offer must not pretend to expire. Do not conceal important costs or introduce friction to prevent declining an offer.

## 6. Tokens and system consistency

### 6.1 Establish semantic roles

Reuse an existing system first. Where one is missing, define only the tokens the project needs:

| Group | Roles to define |
| --- | --- |
| Colour | Page, surface levels, primary/secondary text, border, action, focus, success, warning, error. |
| Typography | Display if needed, heading levels, body, supporting text, labels, data/code where relevant. |
| Layout | Content widths, gutters, spacing scale, grid gaps, control heights. |
| Shape and depth | Radii, border weights, elevation levels, overlay layers. |
| Motion | Feedback/transition durations, easing, reduced-motion alternatives. |

Use names that express function. A semantic action token can change across themes without rewriting component styling. Do not build a large theoretical token system for a small page.

### 6.2 Suggested starting values

These are adjustable design starting points, not compliance thresholds or universal rules. Use existing project values when they work.

| Property | Starting approach | Verify |
| --- | --- | --- |
| Spacing | A small scale such as 4, 8, 12, 16, 24, 32, 48, 64 CSS px. | Clear grouping and appropriate density at every width. |
| Body typography | Roughly 16–18 CSS px with line-height around 1.45–1.7 for Latin body copy. | Actual font, language, reading distance, zoom, and content density. |
| Reading measure | Roughly 45–75 characters for sustained Latin prose. | Long words, headings, narrow screens, and the reading task. |
| Corners | A small set of role-based radii. | Controls and containers feel related without making every shape identical. |
| Elevation | A few levels for surfaces that genuinely overlap. | No accidental halos, unclear stacking, or competing shadows. |
| Motion | Roughly 100–180 ms for brief feedback and 180–300 ms for small transitions. | Device performance, travel distance, reduced motion, and task interruption. |

### 6.3 Extend the system deliberately

Before introducing a new treatment, ask whether an existing role can serve it. If a new pattern is necessary, define its purpose, states, and relationship to existing patterns. Use it consistently afterward.

Do not vary established controls from page to page for novelty. Distinctiveness should coexist with predictable product behaviour.

## 7. Layout and typographic execution

### 7.1 Compose the page

1. Choose content width and alignment axes.
2. Establish the main hierarchy before adding containers or decoration.
3. Group related content with spacing; use containers only when they improve grouping, interaction, or surface meaning.
4. Vary section emphasis according to content importance.
5. Review the whole scroll for rhythm, density, repeated shapes, and abrupt changes in direction.

Symmetry and asymmetry are both valid. Empty space should separate, emphasise, or pace content; it should not result from groups pushed to opposite viewport edges without a shared structure.

The hero does not need to occupy the full viewport. Compose the initial view to communicate the offer or task. A deliberate view of the next section is acceptable; an accidental fragment that confuses the hierarchy is not.

### 7.2 Keep comparisons aligned

For plans, specifications, before/after panels, and parallel summaries:

1. Identify corresponding roles: title, price/value, explanation, features, and action.
2. Use shared layout tracks or another resilient alignment strategy.
3. Align comparable information and position actions predictably.
4. Test the longest content in each role.
5. Stack or change the comparison format before the columns become unreadable.

Do not fix alignment by clipping copy, forcing identical text lengths, or freezing heights that break under zoom or translation. Equal outer height alone does not align the information inside.

### 7.3 Select and set type

1. Confirm licences, language support, available weights, and delivery constraints.
2. Render candidate fonts using actual headings, body copy, labels, and numbers.
3. Check legibility and character distinction at real sizes.
4. Choose a restrained role hierarchy, usually one or two families.
5. Tune scale, line-height, measure, tracking, and emphasis together.
6. Test fallback loading, long content, and narrow layouts.

Free, system, and commercial fonts are all valid. Do not pay for a typeface to compensate for weak composition. Monospace is useful for appropriate data and code; it is not a default voice for every small label.

### 7.4 Protect text and controls

- MUST keep meaningful text and controls clear of notches, masks, overflow boundaries, sticky layers, and fixed-height containers.
- MUST allow required content to grow. Avoid fixed heights for variable copy unless overflow is intentionally handled.
- SHOULD inspect glyph tops, descenders, line-height, icon view boxes, and focus rings near clipped edges.
- SHOULD correct accidental widows and stranded emphasis on supported widths without forcing fragile line breaks everywhere.
- MAY crop decorative display type deliberately if meaning and accessibility remain intact. Never apply that exception to instructions, prices, form labels, or controls.

## 8. Colour, surfaces, depth, and effects

### 8.1 Build a functional palette

1. Choose a base and text relationship appropriate to the brand and environment.
2. Define surfaces, actions, focus, borders, and semantic statuses.
3. Check contrast in actual states and contexts.
4. Review the whole page for competing accents and unclear hierarchy.
5. Repeat the checks for each supported theme.

Bright colours, cream, grey, purple, dark blue, and monochrome are all valid. The decision must serve the brief and remain readable. Do not weaken an action or label into an inaccessible tint to make it look restrained.

Status meaning must survive without colour alone. Use text, shape, iconography, or other appropriate reinforcement.

### 8.2 Use surfaces and elevation intentionally

- Use a container when it communicates grouping, separation, a manipulable object, or an interactive region.
- Use borders when they clarify boundaries; a quiet hairline is not inherently a defect.
- Use shadows when they clarify elevation. Keep their direction, softness, and strength consistent with the surface system.
- Use section boundaries deliberately. A hard transition can organise content; a continuous surface can preserve atmosphere.
- Remove accidental duplicate silhouettes, clipped glows, muddy overlays, and misaligned layers.

Neither rounded cards nor flat surfaces are mandatory. A stack of boxed sections is not a substitute for content hierarchy; removing all boundaries is not a substitute either.

### 8.3 Apply optional effects with a fallback

| Technique | Use when | Required checks |
| --- | --- | --- |
| Glass/translucency | Seeing content behind the surface contributes to the design. | Readability over changing backdrops, supported-browser behaviour, stable transitions, opaque fallback. |
| Gradient | Direction, light, or a brand treatment benefits from it. | Contrast across the entire text area, visible banding, section seams, fallback. |
| Grain/texture | A surface treatment reinforces the chosen medium. | Text remains crisp; overlay does not intercept input; scale and opacity remain appropriate. |
| Grid/rulers | The visual language relates to the content or task. | Decorative marks remain subordinate and distinct from usable controls. |
| Custom silhouette | Shape expresses a relevant identity or structure. | Internal padding, small-screen adaptation, text growth, hit area, focus visibility. |
| Layered overlap | It clarifies depth or a relationship between objects. | Reading order, z-index, occlusion, scrolling, and responsive layout. |

Do not add these effects as a checklist. If one cannot be executed reliably, simplify or remove it. Never keep a broken effect because it is the supposed signature.

## 9. Imagery, icons, and product evidence

### 9.1 Select assets

1. Identify the information or emotion the visual must convey.
2. Prefer relevant supplied assets and accurate product material.
3. Confirm usage rights and required attribution.
4. Check crop, resolution, focal point, colour treatment, and delivery size.
5. Inspect the asset within the actual layout at narrow and wide widths.
6. Provide meaningful text alternatives where needed; mark purely decorative visuals accordingly.

Do not use unrelated stock imagery merely to fill a hero. Do not present generated people, reviews, product results, or customer evidence as real. Conceptual artwork may be appropriate when its role is clear and it does not misrepresent the offer.

### 9.2 Show the actual thing

When showing a product:

- Use a real screenshot, accurate demonstration, or faithful illustrative reconstruction.
- Make sample data clearly identifiable when it could be mistaken for real activity.
- Include enough detail to communicate the actual capability.
- Match visible functionality to what the product can deliver.
- Keep static demonstrations distinct from live controls.

Do not add fake operating-system chrome, a made-up SDK, or a dashboard unrelated to the product. A service, document, or physical product should be represented on its own terms.

### 9.3 Use icons and marks consistently

- SHOULD use a coherent icon family with compatible weight, size, and visual density.
- MUST give icon-only controls accessible names and understandable states.
- SHOULD retain familiar symbols for standard functions; novelty must not reduce recognition.
- MAY use icon containers for grouping, hit targets, contrast, or a justified brand treatment.
- MUST use genuine third-party marks and respect their usage guidance. Normalise optical size without distorting proportions.

Custom iconography is optional. Zero icons is also valid when labels and hierarchy communicate the interface clearly.

## 10. Component instructions

Apply only the rows relevant to the deliverable. Each component needs both visual execution and the corresponding behaviour.

| Component | Precise instructions | Verification |
| --- | --- | --- |
| Button | Use a native button for actions. Set its form type deliberately. Define focus, pressed, pending, and disabled behaviour as applicable. Keep its label understandable. | Pointer, touch, Enter/Space, form submission, repeated activation, and pending state. |
| Link | Use a real destination. Make purpose clear from the text and context. Distinguish navigation from actions. | Destination, keyboard activation, visited/active treatment where relevant, and expected browser navigation. |
| Navigation | Keep labels understandable and the current location identifiable. Use a simple disclosure for ordinary expandable site navigation where appropriate. | Keyboard traversal, mobile open/close, route changes, focus visibility, and sticky-header overlap. |
| Input/select | Provide a persistent label, appropriate input type, useful autocomplete, and associated help/errors. Prefer native controls when they meet the need. | Typing, paste, autofill, keyboard, long values, invalid values, and mobile keyboard behaviour. |
| Checkbox/switch | Use a checkbox for selection and a switch where an on/off setting is appropriate. Expose the current state and make the label activate the control. | Keyboard, touch, label click, state persistence, and disabled explanation when needed. |
| Tabs | Use tabs for switching related panels, not as a disguise for page navigation. Expose selection and panel relationships. Use automatic activation only when panels appear without noticeable delay. | Left/Right for horizontal tabs, Up/Down for vertical tabs; Enter/Space for manual activation; focus versus selected state; panel content and responsive layout. |
| Accordion/disclosure | Use an operable trigger and expose expanded state. Keep headings meaningful. Allow multiple sections open unless the task calls for exclusivity. | Enter/Space, pointer, content growth, and removal of hidden panel controls from the tab sequence. |
| Modal dialog | Provide a title and explicit dismissal. Move focus inside; contain its tab sequence; make the background inert; support Escape; return focus appropriately. | Open, close, Tab/Shift+Tab, Escape, long content, small screens, and unsaved-work handling where relevant. |
| Tooltip/popover | Use tooltips for supplementary information, not essential instructions or required actions. Use an appropriate interactive popover/dialog when controls are inside. | Keyboard and pointer access; dismissal without moving focus where required; pointer can enter hover content; content persists until dismissed, the trigger is removed, or the information is invalid; touch alternative. |
| Card | Use a card when it groups a meaningful unit. Make interactivity clear. Avoid nested interactive elements that conflict with a whole-card link. | Long copy, consistent hierarchy, keyboard access, target boundaries, and static versus interactive styling. |
| Search/filter | Define what is searched, how filtering applies, and how to reset it. Keep the query and selected filters visible. Distinguish loading from no results. | Empty query, no match, multiple filters, reset, pagination interaction, stale responses, and recovery. |
| Table/list | Preserve meaningful labels and relationships. Align comparable values. Expose sorting state when sorting exists. Use a responsive format that preserves the task. | Long cells, empty data, sort/filter, keyboard access, small screens, and clear scrolling boundaries. |
| Pricing/comparison | Show billing period, currency, relevant inclusions, and material conditions. Align comparable rows. Substantiate highlighted-plan claims. | Long copy, currency format, billing switch behaviour, calculations, mobile comparison, and action destinations. |
| Notification | Use persistent inline feedback for information users must act on. Keep noncritical notifications proportionate and accessible. | Announcement behaviour, dismissal, stacking, focus interference, and sufficient reading time. |
| Theme control | Add only if required or useful. Provide an accessible label and state, honour the intended default, and persist a deliberate preference when appropriate. | Initial rendering, preference changes, reload, contrast in both themes, and transition stability. |
| Media/carousel | Add usable controls and required alternatives. Avoid forcing automatic movement. Do not hide important information solely on a later slide. | Keyboard/touch controls, pause, captions, loading failure, reduced motion, and small-screen crops. |
| Chart | Use accurate data, units, labels, and an appropriate scale. Supply a useful text summary or equivalent data access. Never use generated artwork for an exact chart. | Source values, legend, contrast, non-colour distinctions, resize, and accessible access to the information. |
| Footer | Include the navigation, contact, company, or legal information relevant to the project. Carry the page's system through it. | Real destinations, correct details, mobile order, and no unfinished decorative wordmark or cropped links. |

Use the appropriate interaction pattern rather than applying ARIA roles by appearance. Ordinary site navigation is not automatically an ARIA menu. A custom component is not complete until its behaviour and semantics are verified.

## 11. State design, forms, and asynchronous work

### 11.1 Define applicable states before implementation

For each affected component or workflow, identify:

| State | Required design decision |
| --- | --- |
| Default | What users see and can do before interaction. |
| Hover/focus/active | How affordance and current interaction are communicated. |
| Loading/pending | What is happening, what remains usable, and how duplicate work is prevented. |
| Empty | Why no content exists and the useful next step. |
| No results | Which query or filters produced no match and how to broaden or reset them. |
| Partial/stale | What is missing or out of date and whether proceeding is appropriate. |
| Invalid/error | What failed, where it failed, what input is retained, and how to recover. |
| Success | What actually completed and what happens next. |
| Disabled/unavailable | Why the action is unavailable and how to make it available, when useful. |

Not every state applies to every component. Document relevant states once and reuse the pattern.

### 11.2 Build forms as complete journeys

1. Ask only for information needed at this stage.
2. Provide persistent labels, format guidance, and required/optional indication.
3. Validate at a useful point without interrupting normal entry.
4. Associate field errors with the affected controls; include a clear summary when the form warrants it.
5. On submit, prevent duplicate operations and communicate progress.
6. Preserve entered values after recoverable failures.
7. Show success only after the intended operation is confirmed.
8. Offer the appropriate next step; handle resubmission or editing where relevant.

Client validation improves feedback; it does not replace server validation. Do not block paste or password managers without a justified requirement. Do not rely on placeholder text as the only label.

### 11.3 Handle asynchronous reality

- MUST handle failures as well as successful responses. Avoid indefinite spinners with no recovery path.
- SHOULD keep unaffected content usable while a local region updates.
- MUST prevent stale responses from silently replacing newer user intent.
- SHOULD retain useful state across retry, navigation, or cancellation when the workflow requires it.
- MUST distinguish “saving” from “saved.” Optimistic updates need a failure/reconciliation path.
- MUST NOT hide implementation gaps behind simulated confirmations.

Test with controlled fixtures or test endpoints. Do not use real customer submissions, payments, or destructive records as routine UI test data.

## 12. Motion and progressive enhancement

### 12.1 Decide whether motion earns its place

For each animation:

1. State its purpose: feedback, spatial continuity, explanation, or brand expression.
2. Identify the trigger and affected element.
3. Define its beginning, end, duration, and interruption behaviour.
4. Define the static or reduced-motion equivalent.
5. Confirm that it does not delay a task or compete with reading.

If the purpose is only “make it feel premium,” reconsider it. Motion is optional. A calm interface with clear feedback can be complete.

### 12.2 Keep content visible by default

MUST NOT make essential text or controls depend on a decorative animation completing. Do not leave them at zero opacity, outside the viewport, or inside a closed clipping region while waiting for JavaScript, an observer, or a scroll timeline.

Build the final readable layout first. Add enhancements that cannot strand content in an invisible state. If a reveal cannot provide a reliable visible fallback, use a different treatment.

This rule does not prohibit intentional tabs, menus, and dialogs. Their hidden state must be part of an operable, accessible interaction rather than an unfinished entrance effect.

### 12.3 Constrain movement

- SHOULD use consistent motion tokens and a restrained number of simultaneous effects.
- SHOULD prefer inexpensive properties; profile large blur, filter, layout, and canvas work.
- MUST preserve stable hit targets and focus indicators.
- MUST respect reduced-motion preferences and provide usable nonmoving equivalents.
- MUST meet applicable requirements for flashing and automatically moving content, including pause/stop/hide controls where required.
- MUST avoid scroll hijacking and avoid locking navigation behind an animation.

Default card lifts, floating tags, growing underlines, and animated backgrounds are not forbidden techniques. Applying them everywhere without purpose is the failure.

### 12.4 Verify motion failures

Check repeated activation, interruption, resize, background-tab return, unsupported enhancement, and reduced motion. Confirm the final state, usable controls, stable geometry, and readable content in each relevant case.

A JavaScript application does not automatically promise full no-JavaScript operation. Preserve baseline content where the architecture supports it; handle runtime failures and identify unavailable functionality honestly. Decorative animation failure must not produce an empty interface.

## 13. Responsive design and localisation

### 13.1 Design from content pressure

1. Establish the narrowest useful layout for the primary task.
2. Expand until the content benefits from another column or larger composition.
3. Add breakpoints at those pressure points.
4. Check immediately above and below each important transition.
5. Confirm the reading order and action priority in every arrangement.

Do not design only at framework presets. Do not shrink the desktop page until it fits.

### 13.2 Use a practical viewport matrix

Unless the project specifies another matrix, use these as representative checks, not a claim of exhaustive device support:

| Condition | Check |
| --- | --- |
| Narrow layout | Reflow at 320 CSS px where applicable; no loss of information or functionality. |
| Common mobile width | A width around 390 CSS px; touch controls, crops, menus, and forms. |
| Intermediate width | A width around 768 CSS px plus actual layout breakpoints. |
| Desktop | A width around 1440 CSS px plus the project's intended content maximum. |
| Constrained height | A short viewport and the mobile on-screen keyboard; dialogs and actions remain reachable. |
| Enlarged content | Text resize, browser zoom, and user text-spacing overrides. |

Test portrait and landscape when the interface has orientation-sensitive behaviour. Simulated widths do not prove real-device performance or browser compatibility.

### 13.3 Handle growth and language

- MUST allow long names, translations, URLs, large values, and multi-line labels without collisions or lost actions.
- SHOULD use flexible sizing, sensible wrapping, and logical properties where appropriate.
- MUST format dates, times, units, numbers, and currencies consistently with the intended locale.
- MUST preserve meaning when abbreviating; expose full information when truncation is necessary.
- MUST review RTL order, directional icons, alignment, and mixed-direction content when RTL languages are supported.
- MUST NOT reduce body text to preserve an English desktop line break.

Keep intentional two-dimensional content, such as complex tables or canvases, in a clearly usable region. Avoid whole-page horizontal scrolling caused by an oversized decorative element or inflexible child.

## 14. Accessibility requirements

MUST meet applicable WCAG 2.2 Level A and AA criteria within the delivered scope, alongside project requirements. Report unverified criteria and inherited limitations. A partial review does not establish full-product conformance.

### 14.1 Semantics and operation

1. Use native HTML elements where they provide the required behaviour.
2. Structure landmarks and headings logically.
3. Give controls accessible names and associate labels, help, and errors.
4. Preserve a sensible reading and focus order.
5. Operate the primary journey with keyboard alone; avoid unintended focus traps.
6. Keep focus visible and ensure focused controls are not entirely obscured by author-created content.
7. Expose changing states and important status feedback to assistive technology without excessive announcements.

### 14.2 Measurable checks

| Requirement | Baseline |
| --- | --- |
| Text contrast | At least 4.5:1; 3:1 for qualifying large text: at least 18 pt regular or 14 pt bold. Apply defined exceptions accurately. |
| Non-text contrast | Required graphical objects and indicators of controls/states meet 3:1 against adjacent colours, subject to the standard's exceptions. |
| Pointer target size | Meet 24 × 24 CSS px or a defined exception. SHOULD prefer roughly 44 × 44 CSS px for touch when practical; that preference is not the AA minimum. |
| Resize/reflow | Support 200% text resizing and applicable reflow at an equivalent width of 320 CSS px. Preserve exceptions for content requiring two-dimensional layout. |
| Text spacing | No loss of content/function when users set line-height to 1.5×, paragraph spacing to 2×, letter spacing to 0.12×, and word spacing to 0.16× the font size, where applicable. These are override tests, not mandatory default styling. |

### 14.3 Additional checks

- Provide text alternatives for meaningful visuals and required alternatives for media.
- Do not rely on colour, hover, position, or animation alone for required information or operation.
- Provide a single-pointer alternative to dragging unless a defined exception applies.
- Apply requirements for hover/focus content, error identification, authentication, and moving/flashing content to relevant patterns.
- Respect reduced motion. Check supported high-contrast or forced-colour environments where relevant to the project.

Use automated checks plus manual keyboard and appropriate assistive-technology review. Automated success is not an accessibility certificate. The checks here are a working baseline; consult the full standard for criteria and exceptions.

## 15. Implementation, data, and integration discipline

### 15.1 Reuse before adding

1. Prefer an existing suitable project component.
2. Prefer native platform behaviour when sufficient.
3. Use a compatible, established primitive when the requirement warrants it.
4. Add a dependency only after considering capability, integration cost, maintenance, licence, accessibility, and runtime cost.
5. Verify the final customised component; inherited behaviour can break during adaptation.

Do not add a new styling framework to use one block. Do not hand-roll complex interaction semantics when a suitable existing primitive is available. Neither dependency count nor custom code volume is a design achievement.

### 15.2 Keep changes maintainable

- MUST work within the existing architecture unless the task justifies a change.
- SHOULD separate data/state logic from presentation when that improves clarity and testing.
- SHOULD extract genuinely reused patterns without creating abstractions for every small variation.
- MUST keep shared changes compatible with their consumers; inspect affected callers and routes.
- SHOULD avoid scattered magic values, global selector collisions, duplicated markup, and layers of local CSS patches.
- MUST remove debug output and temporary placeholders introduced by the work before calling it complete.
- MUST preserve meaningful existing comments, contracts, and documentation unless they become inaccurate.

### 15.3 Honour real data boundaries

MUST use the actual API and CMS contracts. Handle missing, invalid, partial, and delayed data. Keep stable identifiers where identity matters. Do not silently replace a failed integration with local demo content.

MUST keep secrets and privileged operations out of client code. Reuse established validation, authentication, authorisation, and data-handling mechanisms. Interface completion does not replace the project's security and privacy review.

For prototypes, label simulated functionality and state what is connected. Never imply that a demonstration sent a message, created a booking, saved a record, or processed payment when it did not.

### 15.4 Preserve discoverability and tracking

For affected public pages, preserve or intentionally update titles, descriptions, canonical handling, headings, link destinations, social metadata, and relevant structured data. Do not invent schema claims.

Keep CMS field mappings and analytics event contracts intact unless changing them is in scope. Check for duplicate events after modifying controls. Do not expose personal or sensitive form values through new analytics.

## 16. Performance and delivery cost

### 16.1 Set a proportionate budget

Before introducing heavy imagery, video, 3D, canvas, or animation, identify its expected benefit and cost. Use the project's existing budgets. If none exist, establish practical limits for added JavaScript, asset transfer, initial rendering, and continuing animation work based on the target environment.

No universal bundle-size limit fits every product. Do not claim a performance improvement without comparable measurements.

### 16.2 Optimise the critical path

1. Deliver appropriately sized and compressed images with responsive variants where useful.
2. Reserve space for media and dynamic elements to limit layout movement.
3. Prioritise the actual initial-view content; do not lazy-load the primary above-the-fold image by default.
4. Defer noncritical media, scripts, and expensive enhancements.
5. Load only the font families, styles, and weights needed; account for fallback rendering.
6. Avoid continuous rendering for off-screen or inactive decoration.
7. Measure the result on representative device/network conditions.

### 16.3 Use meaningful measurements

SHOULD target Core Web Vitals of **LCP ≤ 2.5 s**, **INP ≤ 200 ms**, and **CLS ≤ 0.1** at the **75th percentile** of real visits, assessed separately for mobile and desktop.

Use lab tools to diagnose pre-release performance. Record the page, environment, throttling, and measurement type when reporting results. A lab score is not field verification; a fast local development server is not evidence of production performance.

Keep interaction responsiveness and stability in view after the initial load. Review long lists, filtering, overlays, and any expensive ongoing effects relevant to the task.

## 17. Verification procedure

### 17.1 Inspect the rendered result

1. Run the project using its documented workflow.
2. Inspect each affected route or representative shared-component consumer.
3. Review the complete page, not only the first viewport.
4. Check the responsive matrix and affected content-growth cases.
5. Inspect high-risk edges closely: clipped shapes, overlaps, masks, shadows, glyph boundaries, and focus rings.
6. Compare the result against the brief and direction note.

Use the project's supported-browser matrix. If none is defined, record the browsers and versions actually checked and leave broader compatibility unverified. Do not equate a responsive viewport simulation with testing a different browser engine.

MUST NOT claim browser inspection from code review alone. A screenshot can verify appearance at a captured state; it cannot prove interaction, timing, integration, or accessibility.

### 17.2 Exercise the user journey

1. Complete the primary journey with realistic test data.
2. Exercise each distinct affected control behaviour.
3. Repeat with keyboard; check touch-relevant behaviour on suitable surfaces.
4. Test relevant failures: invalid input, missing data, network rejection, empty results, and interrupted operations.
5. Confirm actual outcomes through the test system or integration response.
6. Recheck focus, announcements, retained input, and recovery after state changes.

Testing one instance may be sufficient for identical component behaviour. Test variations when data, props, layout, or integration changes the outcome. Do not click hundreds of identical static items to manufacture coverage.

### 17.3 Run project checks

Run required formatting, linting, type, build, unit, integration, or end-to-end checks appropriate to the change. Add meaningful tests for new logic and regression risks. Do not write brittle tests that only mirror markup or arbitrary style values.

Distinguish new failures from pre-existing ones. Do not suppress errors, weaken assertions, or remove coverage to obtain a passing result. If checks cannot run, record what is missing and which claims remain unverified.

### 17.4 Fix by severity

| Severity | Examples | Required action |
| --- | --- | --- |
| Blocker | Primary task fails; false success; sensitive data exposure; essential content inaccessible. | Fix before claiming completion of the affected scope. |
| Major | Important secondary behaviour fails; severe mobile clipping; unusable error recovery; substantial visual mismatch. | Fix within scope; explicitly disclose inherited or unavailable dependencies. |
| Minor | Local spacing inconsistency; nonessential decorative mismatch; small optical adjustment. | Fix after higher-impact issues; avoid destabilising completed functionality. |

After a fix, recheck the failure and affected shared consumers. Repeat broader checks only when changes or unresolved concerns justify them. Do not cycle indefinitely through subjective redesigns after the acceptance criteria are met.

## 18. Anti-slop review and repair

### 18.1 Common failures

| Failure | Why it fails | Repair sequence |
| --- | --- | --- |
| Recoloured template | The content and section order do not reflect this product. | Revisit user questions → reorder evidence → remove filler → strengthen the defining composition. |
| Decorative clutter | Pills, tiles, borders, tags, arrows, and glows have equal emphasis. | Identify primary information → remove redundant containers → restore hierarchy → retain only purposeful detail. |
| Hero-only quality | Later sections lose the direction or repeat empty cards. | Review the whole scroll → carry typography/image language through useful content → refine transitions and footer. |
| Typeface substitution | A fashionable font disguises an unchanged generic structure. | Check hierarchy and measure → adjust composition → assess font fit with real text. |
| Unreadable restraint | Tonal styling removes necessary contrast and affordance. | Restore readable values and clear states → simplify decoration → verify contrast and focus. |
| Fake product visual | A window, chart, or terminal implies capabilities that do not exist. | Replace with accurate product evidence → label samples → distinguish demo from live functionality. |
| Fragile motion | Content vanishes or controls jump when an animation fails. | Restore readable base state → remove gating → add safe enhancement → test interruption and reduced motion. |
| Ragged comparison | Variable copy shifts corresponding information unpredictably. | Map comparable roles → share tracks → allow growth → change mobile format. |
| Desktop-only composition | Small screens inherit tiny text, overlap, and unusable controls. | Re-establish narrow hierarchy → stack by task order → adapt visuals → test real content and touch. |
| Correct but generic | The interface works but says little specific about the brand or offer. | Improve real content and evidence → strengthen one relevant defining decision → keep behaviour familiar. |
| Overdesigned utility | Novel geometry or motion slows a routine workflow. | Restore task hierarchy → simplify controls → reserve expression for nonblocking areas. |
| Integration theatre | The UI looks complete while operations are simulated or unconfirmed. | Expose the connection status → implement actual outcomes → handle failure → report remaining gaps. |

### 18.2 Do not overcorrect

- Do not ban familiar layouts; justify their use with the content.
- Do not remove every icon, border, neutral colour, or conventional control.
- Do not require paid type, custom artwork, glass, grain, or animation.
- Do not force every component to have a unique appearance.
- Do not change an established product identity to avoid resemblance to unrelated work.
- Do not reduce useful copy into vague slogans to make a screen look minimal.
- Do not add a signature object where accurate product evidence is stronger.

The goal is relevance and execution. Avoiding a list is not a design direction.

## 19. Release gate and handoff

Use this checklist after the final changes. Reuse evidence gathered during implementation; do not repeat work solely to populate a report.

Mark applicable items **PASS**, **FAIL**, or **NOT VERIFIED**. Use **N/A** only with a reason. An unchecked box is not a pass.

| Gate | Pass condition |
| --- | --- |
| Brief and scope | Required tasks, content, and preservation constraints are satisfied. |
| Specificity | Copy, assets, and composition reflect the product and audience; the page is not an unexplained stack of stock sections. |
| Cohesion | Tokens, type, imagery, controls, surfaces, and motion form a consistent system across affected screens. |
| Truthfulness | No fabricated proof, misleading claims, unlabeled demo data, false success, or unresolved production placeholders. |
| Visual execution | No accidental clipping, collisions, broken crops, unreadable text, misaligned comparisons, or covered controls. |
| Responsive behaviour | Representative widths, layout transitions, content growth, zoom, and relevant mobile interactions are verified. |
| Accessibility | Applicable criteria and relevant manual/automated checks are addressed; remaining uncertainty is recorded. |
| Component states | Applicable loading, empty, invalid, error, success, pending, and unavailable states work. |
| Journey and integrations | Primary journey and distinct affected controls produce the intended real outcomes. |
| Reliability and motion | Relevant failure paths recover; reduced motion works; decorative failure does not hide essential content. |
| Performance | Required budget checks are complete; evidence distinguishes lab from field measurements. |
| Implementation | Required project checks pass, or existing/unavailable checks are identified; affected routes have no new unresolved errors. |
| Handoff | Remaining blockers, unverified work, and external dependencies are explicit. |

### Completion rules

- A failed MUST requirement blocks claiming the affected scope is complete.
- A NOT VERIFIED item remains unknown. Do not turn it into a pass through confidence or visual plausibility.
- N/A must describe why a criterion does not apply, not why it was inconvenient to check.
- A prototype can be delivered as a prototype with clear limitations.
- A visually complete interface does not establish backend, security, privacy, operational, or deployment readiness.

Do not use an averaged design score to excuse a broken critical journey or accessibility defect. Do not promise increased conversion or revenue without relevant measurement.

### Final handoff

Keep the user-facing handoff brief:

1. **Changed:** the concrete change and the task or design goal it serves.
2. **Verified:** actual checks, representative environments, and results.
3. **Remaining:** blockers, unavailable checks, integration work, or material limitations; omit if none.

Provide the full checklist only when requested, required by the project, or useful for a formal review. Never claim “everything tested” without a defined scope.

## 20. Reusable working templates

Use these as compact working notes, not mandatory extra deliverables. Fill them only with known information. Keep unknowns explicit.

### Direction note

```text
Audience and primary task:
Intended character and visible expression:
Defining decision or established system to extend:
Content/journey structure:
Preservation constraints and material assumptions:
```

### Component or workflow contract

```text
Component/workflow:
User intent:
Inputs and data source:
Trigger and confirmed outcome:
Applicable states and recovery:
Keyboard/touch/focus requirements:
Responsive and content-growth behaviour:
Acceptance checks:
```

### Verification record

```text
Scope and relevant revision:
Route/component and state:
Viewport/browser/input method:
Action or check performed:
Expected result:
Observed result:
Status: PASS / FAIL / NOT VERIFIED / N/A
Remaining issue or reason for N/A:
```

### Material exception

```text
Default being departed from:
Brief, evidence, or constraint supporting the exception:
Chosen alternative and tradeoff:
How the result will be verified:
```

## 21. Maintain the playbook

1. Add a rule only when it addresses a recurring failure or a material missing requirement.
2. State the failure, required action, and way to verify it.
3. Distinguish universal requirements from contextual advice.
4. Update the relevant section instead of appending a contradictory field note.
5. Remove duplicated rules and obsolete framework-specific recipes.
6. Recheck external standards and library guidance when the project's baseline changes.

Keep the core stable. Project-specific colours, fonts, component choices, asset references, and integration details belong in the project's direction and technical documents.

## Reference standards

- [WCAG 2.2](https://www.w3.org/TR/WCAG22/): normative accessibility criteria and exceptions.
- [Target size](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html), [reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html), [text spacing](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html), and [focus visibility under overlays](https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html): explanations for common implementation checks.
- [ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/patterns/): interaction guidance, including [modal dialogs](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/), [tabs](https://www.w3.org/WAI/ARIA/apg/patterns/tabs/), and [disclosures](https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/). Guidance and examples do not replace testing the actual implementation.
- [Content on hover or focus](https://www.w3.org/WAI/WCAG22/Understanding/content-on-hover-or-focus.html): dismissal, pointer access, and persistence requirements for applicable additional content.
- [Web Vitals](https://web.dev/articles/vitals): performance definitions, thresholds, and measurement guidance.

**Final principle:** Make purposeful decisions, use familiar behaviour where it helps, and verify the interface people will actually use. Distinctiveness comes from relevance, coherence, and execution.
