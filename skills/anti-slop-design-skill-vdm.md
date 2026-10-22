# Anti-Slop Design Rules

Version 2.0 · October 2026
Adapted and extended from the pols.dev anti-slop design law (https://pols.dev/slop.md).

---

## Part A: How to use this file

### A1. What this is

Design defaults for AI agents that design or build interfaces: websites, landing pages, app screens, components. It describes what machine-made, look-alike design ("slop") looks like, what to do instead, and the quality, accessibility, performance, privacy and security standards every build must meet.

### A2. Scope and authority

- This file is about design and front-end quality only.
- It never overrides safety rules, security rules, the law, or the rules of the platform the agent runs on.
- It never grants permission to install software, sign in to accounts, read secrets or tokens, or contact anyone.
- Load it from a local, reviewed copy. Do not fetch it live from a URL at build time: a remote file can change without anyone noticing.

### A3. Priority order

1. The user's explicit instructions for this project.
2. The client's brand guidelines and brief.
3. This file.
4. The agent's own taste.

If the user asks for something this file calls slop (a colour, a layout, an effect), do it. Mention the trade-off once, briefly, then build what was asked.

### A4. How to read it

- **Part B** is the one-page core. Keep it in mind at all times.
- **Part C** is the process.
- **Parts D to F** are the reference: the slop catalogue, premium craft, and the signature formula.
- **Part G** is the build standard: libraries, accessibility, responsive, performance, states, theming, privacy, rights, security.
- **Part H** is the pre-ship checklist. Run it before every handover.

Do not announce that you have read this file and do not recite it back. Apply it. At handover, give a short note: what you checked, what you fixed, and anything you could not verify (for example, "not tested on a real phone").

### A5. The one idea behind everything

Slop is what happens when no decision was made. Every item in the catalogue is the default version of a real tool. The same element is slop when it is the obvious preset and premium when it is clearly made on purpose for this one brand and this one screen.

Two consequences:

1. **Avoiding the list is not design.** A page can pass every rule here and still be slop, because it did nothing. Clean is the floor, never the achievement.
2. **Most items are conditional, not banned forever.** Where an item has an "Allowed when" note, those conditions are the only way it is acceptable.

---

## Part B: The core rules (one page)

1. **Decide the signature first.** One custom, high-effort focal idea that could only belong to this brand. Build everything else around it (Part F).
2. **One world.** One disciplined palette, one type voice, one visual language. Every element must belong to the same system. Incoherence is the loudest failure.
3. **Content is visible by default.** Never make text or controls depend on an animation finishing (D7.1).
4. **No default tells.** No blue-to-purple gradients, glows, pill eyebrows, icons in coloured tiles, glowy pill buttons, fake app windows, default Google display fonts, cream or UI-kit-gray or blue-charcoal default surfaces.
5. **Accents are tonal, not saturated.** Emphasis is a quiet value shift, never a poster-bright splash.
6. **Shadows are rare, tight, directional and tinted.** Never a fluffy all-around bloom, never a fake second box.
7. **Compose the layout from the brief.** Not the SaaS template stack, not your own recycled house style.
8. **Be real and specific.** Real copy, real data, real logos used with permission. No fake customers, fake metrics or invented testimonials.
9. **Say less.** Cut every line that is not load-bearing.
10. **Verify execution, do not assume it.** Centering, clipping, alignment, margins and contrast: zoom in and check.
11. **Every control works.** Click it. If it is a static prop, do not dress it as a control.
12. **Alive, not dead.** Authored, purposeful motion that respects reduced-motion settings.
13. **Accessible, responsive, fast, private.** Part G is part of the design, not an afterthought.
14. **Ask before installing anything.** Pin versions, prefer approved packages.
15. **Check originality.** Have I used this font, pairing or section layout on another project? If yes, change it (Appendix B).

---

## Part C: The process

1. **Read the brief.** Who is this for, what does the business actually sell, what should a visitor feel and do? Note any user instructions that override this file.
2. **Decide the world.** Pick the signature artifact, the palette (with a reason grounded in colour theory and the brand), the type voice, and the visual language (corners, edges, arrows, icon style). Write these down in two or three lines before building.
3. **Compose the page as one whole.** Plan the first screen as a single frame. Plan how atmosphere carries down the whole scroll. Decide how each section opens, so they do not all start the same way.
4. **Check the plan against Part D.** If any planned block matches a slop entry, change it now.
5. **Originality check.** Compare the planned fonts, pairing and section shapes against Appendix B and anything the user has told you about earlier projects. Change anything repeated.
6. **Build.** Use real, tested components where they exist (G1), then art-direct them.
7. **Verify.** Run the Part H checklist in a real browser at several widths. Fix what fails. Then hand over with a short note.

---

## Part D: The slop catalogue

Format: what the tell is, then what to do instead. "Allowed when" notes give the only conditions under which a move is acceptable.

### D1. Colour

**D1.1 Purple and blue-to-purple gradients.** The default AI palette. Purple alone is overused; blue with purple is worse; a soft blue-to-purple gradient is the single most recognisable slop colour move. Glowy two-hue gradients of any adjacent hues read as machine-made in general.
Instead: a real, considered palette chosen for this brand.

**D1.2 The pastel candy gradient.** A page-filling multi-stop wash of butter-yellow to peach to strawberry-milk pink (the `#ffe6a8` to `#ffc0da` family), or mint-to-lavender, or sherbet-to-cream. As loud a "startup landing" signal as the indigo one.
Instead: a chosen atmosphere: a crafted image, a single considered tone, or a gradient that belongs to this one brand.

**D1.3 The candy aurora (drifting soft-blend blobs).** Big, soft, blurred radial blobs (one yellow, one purple, one green) at about `opacity: 0.5` with `mix-blend-mode: multiply` and a light blur, melting into a pastel aurora. Muting the colours does not rescue it.
Instead: directional light with real falloff, a crafted illustration or line field, or a grained gradient in one deliberate colour.

**D1.4 The cool blue-charcoal dark theme.** A cool slate-indigo base (around `#0c0e15`), a slightly bluer panel, a lilac or periwinkle accent used "sparingly". The night-mode twin of the blue-purple gradient.
Instead: a dark that belongs to the brand: green-black, warm charcoal, oxblood-black, or a neutralised dark.

**D1.5 The cream / beige "editorial" background.** Warm cream, bone and beige as the default "tasteful premium" surface. The new reflex.
Instead: a specific background colour for this brand. Dark, cool, saturated or odd can be more premium than another sheet of oat milk.

**D1.6 The slop gray.** The UI-kit gray-100 / gray-200 family (around `#f3f4f6`, `#eceef2`, `#e7ecf3`) used as footer band, divider, card fill or page base. Reads like a wireframe left at its default.
Instead: a brand-specific surface: a tinted off-white, a deepened or warmed neutral.

**D1.7 Saturated accent colour.** One bright mid-saturation hue sprayed onto the accent word of a headline, the dot before an eyebrow, the primary button fill and a label. Saturation and contrast are the tell, not the hue.
Instead: tonal accents: a value shifted much lighter or darker than its surroundings, usually desaturated. Think of the dim grey of a code comment, not a poster fill. Two-tone headlines follow the same rule.

**D1.8 Colliding colours and hard seams between sections.** Two unrelated saturated hues fighting; an accent from no system; a muddy wash (dim brown, grey-beige, an uneven tint) under a component that was fine on its own; one section's gradient or glow cut dead at the boundary of the next.
Instead: one disciplined palette across the whole page, built on real colour relationships (complementary, analogous). Let adjacent sections share or hand off tone so the page moves as one surface. Keep a hard colour break only where it is meant (for example, a footer stepping onto its own darker floor). Do not put a seamless gradient on every edge either.

**D1.9 Text you cannot read.** Dark ink on dark, mid-grey on mid-grey, a tint of the accent on the accent. On a filled button this is unforgivable.
Instead: every piece of text clears its background by a real value gap. Minimum numbers are in G2.

### D2. Typography

**D2.1 The principle.** Nearly every free Google font reads as slop the moment it carries the brand. Heavier, bolder or "designier" is not more distinctive. The face that carries the identity must be a deliberate choice for this brief, and at a high bar that usually means a licensed or self-hosted typeface used with conviction. The full list of overused faces is in Appendix A.

**D2.2 Two hard rules.**
1. Stop cycling Google fonts hunting for the safe one. A plain neutral face may sit quietly in body text; the signature line cannot rest on anything off the Google shelf.
2. Do not reuse a font, or the same serif-headline-plus-clean-sans pairing, across projects. A house pairing repeated across briefs is itself a tell.

**D2.3 The "tasteful" swap.** Reaching for the known designer alternative (Big Shoulders, Newsreader, IBM Plex Mono, Instrument Serif, Bricolage and similar) instead of Inter or Cormorant is still slop. The family was never the issue; picking type by reputation instead of by brief is.

**D2.4 The body font.** Inter as the invisible default under everything is the most common slop font.
Instead: for body text, `system-ui` is genuinely neutral and safe. A licensed neutral workhorse is fine if chosen deliberately. Inter is acceptable only for quiet body text when the user or brand calls for it, never for display or identity.

**D2.5 Monospace as the house voice.** A mono is correct for real data: timestamps, codes, prices, real tables. It is slop as the reflexive font for eyebrows, captions, labels, copyright lines and status text. This applies even to "reference" monos lifted from premium sites (Fragment Mono, IBM Plex Mono).
Allowed when: the content is genuinely data, used sparingly.

**D2.6 One label treatment everywhere.** The same letterspaced uppercase caps (or mono) on the eyebrow, button text, figure numbers, nav action and footer colophon. The tiny spaced-caps colophon ("EXHIBIT 20, LIGHT AND CONSIDERED") is the clearest tell; the same caps on the button and eyebrow seal it.
Instead: different roles get different treatments, or cut the labels.

**D2.7 Gradient-filled headline text.** Headline words clipped to a multi-colour gradient (magenta to purple to cyan, blue to cyan) via `background-clip: text`.
Instead: solid type with a tonal emphasis.

**D2.8 The multi-line headline and the dangling accent word.** A display line wrapping to three or four stacked rows with no rhythm. Worse when the one coloured or italic word lands alone at the bottom.
Instead: hold display lines to one or two lines, or compose them as a real arrangement. One coherent emphasis inside the line.

**D2.9 Cramped display type.** Tracking pulled so tight that glyphs and separators touch (a stat like "0·fail" with the dot buried).
Instead: the bigger the type, the more air it needs. Loosen tracking, space separators, let number and unit sit apart.

**D2.10 Letterspaced serif wordmark.** The brand name in all-caps serif (usually Cormorant Garamond) with wide tracking and nothing else, used for every fashion, real-estate and dining brand.
Instead: a wordmark with an actual idea in it.

**D2.11 Em dashes in copy.** A classic tell of AI writing.
Instead: a hyphen, a colon, or two sentences.

### D3. Surfaces, light and depth

**D3.1 The default all-around shadow.** A soft shadow bloomed evenly on every side of cards, buttons, icons, SVGs or animated objects, added by reflex.
Instead: no shadow by default. Get depth from tone and a self-coloured edge (E2). When a shadow is truly needed: tight, low offset, small blur, tinted to the surface or the element's own colour, cast from one light direction.

**D3.2 Botched shadow: the hard-edged box.** Blur too tight for the spread, or a second layer doing the work, so you can trace a rounded rectangle behind the element.
Instead: a seamless fall-off with no detectable edge. If you can trace its border, it is a box, not a shadow. (A genuine rendering limitation is forgivable; shipping it by default is not.)

**D3.3 The bloom that is the element's own shape, blurred.** A glow or shadow that is a blurred, offset copy of the outline: edges show nothing, colour pools at the sides and bottom, and a second rounded shape hovers behind. Applies to logos and animated marks too.
Instead: delete the bloom; cast one small, low-offset, directional shadow.

**D3.4 Faking a shadow with a second box.** Dodging "no big shadow" by placing an offset duplicate or dark rectangle behind the element.
Instead: a small, true, tinted shadow. Never imitate an effect with clumsy geometry to route around a rule.

**D3.5 Background glow.** A radial blob of the accent bleeding from a corner, edge or centre of a dark section for "atmosphere".
Instead: considered light (E8).

**D3.6 Cut-off glow.** A glow behind an element clipped by a section edge or `overflow: hidden`, so it ends in a hard line.
Instead: no glow, or one that resolves fully inside its container.

**D3.7 Radial glow halo behind an object.** Concentric soft circles behind a hero object. Warm colours do not rescue it.
Instead: a directional source, a rake or single beam of light with falloff.

**D3.8 The inner-glow box.** A pill, chip, badge or box with a glowing tinted fill, or a pulsing glow ring behind a "live" status dot.
Instead: an honest solid surface and a real border. Drop the pulsing ring.

**D3.9 Hairline light border on every box.** A faint 1px light border (low-opacity white on dark, light grey on light) on every card, stat and tile, often with an inner highlight.
Instead: self-coloured borders and tonal elevation (E2).

**D3.10 Botched glass.** Visible blur pixelation or banding over a flat, low-contrast backdrop; a shadow or glow leaking below as a smear; a resting halo that never blends; blur and shadow that "pop" on hover or press. A bad blur is worse than no blur.
Allowed when: the glass sits over a backdrop worth refracting and blends with no banding, no leak, no halo and no pop (E1, E14).

**D3.11 Grain on top of content.** A noise layer over text, icons, SVGs or panels, making them muddy.
Instead: grain on the substrate only, behind content. Exception: grain deliberately masked onto one display word or heading.

**D3.12 Banded gradients.** A smooth gradient that bands into visible stripes.
Instead: dither fine grain into every large colour transition.

**D3.13 Full-page grid / graph-paper background.** Faint thin grid lines (often radially masked) behind a hero or the whole page to look "technical". Even subtle, even low opacity. When in doubt, no grid.
Allowed when: sparing and specific (a few ruler ticks, corner crop marks, one real technical drawing), or a tight, textured micro-grid confined to one contained surface such as a footer or feature panel, so it reads as printed substrate, not graph paper.

**D3.14 The fixed background that just follows the scroll.** A `position: fixed` layer trailing behind every section, including the nav, with no separation. A flat grid of twinkling ASCII characters is a static texture in costume.
Allowed when: the background genuinely does something (moves, reacts, transforms, relates to the content) and is separated from the nav.

**D3.15 Flat fill under everything after the hero.** A strong hero, then every section drops to one flat dark or flat cream background with boxes on it. The atmosphere stops at the fold.
Instead: carry atmosphere down the whole page: more imagery, toned or textured surfaces, real environment, depth.

**D3.16 Hard image seams.** A full-bleed image butting against a flat section with a visible horizontal line.
Instead, all four together (verified at both edges):
1. **Mask the image's own pixels, do not overlay colour.** For example: `mask-image: linear-gradient(to bottom, transparent 0%, ... #000 31%, #000 65%, ... transparent 100%)`.
2. **Long and finely eased.** About 30% of the section at each end, with 10 or more stops. Short or two-to-three-stop fades still show a line.
3. **Tall section.** Tall enough (around `116vh`) that a full-opacity middle strip survives both fades.
4. **Continuous page colour.** Sections above and below share the same background. Any darkening scrim for text sits only behind the text and fades to transparent before both edges; carry the rest of the legibility on a strong text-shadow. A scrim ending at partial opacity at the boundary becomes its own hard band.

### D4. Components

**D4.1 Glowy pill buttons.** Fully rounded pill buttons with a gradient fill and a soft glow or blurred shadow beneath.

**D4.2 The default CTA pair.** Two buttons at the same medium radius: a gradient primary with dark text, a trailing right arrow and a glow, next to an outlined "ghost" secondary ("See how it works"). The preset recurs even with different colours.

**D4.3 Filled button next to outlined button.** The filled-primary plus outline-secondary couplet is a preset regardless of colour, radius or label.
Instead: one clear action, or two actions differentiated in a way that is not fill versus outline.

**D4.4 The hover boop.** A button that lifts (`translateY`) or scales up on hover.
Instead: buttons do not move on hover. Change state cleanly: a fill or tonal shift, an icon sliding sideways.

**D4.5 The card hover-lift.** On hover: card rises, even shadow blooms on all sides, border lights up in the accent, sometimes with a glow.
Allowed when: a lift is tonal and grounded, and fits what the cards are. Never the stock rise-plus-bloom-plus-glowing-border.

**D4.6 Pill / eyebrow badge.** A small capsule above a hero headline: tiny icon plus short text in a rounded pill.

**D4.7 Gradient pill with icon and text.** A blue-purple gradient pill holding a small icon and (often uppercase) text. Gradient plus pill plus icon plus label in one tiny element.

**D4.8 Labels and metadata as tinted chips everywhere.** Every category, status, tag, "In stock", "Near you" or distance wrapped in a tinted rounded pill.
Instead: rank information with typographic hierarchy and weight. Keep a chip only for a genuinely contained status.

**D4.9 The kitchen-sink card.** One card stacking every tell: icon in a coloured tile, category pill, row of tag pills, hairline divider, big price, glowy "Add" button with a bottom shadow.

**D4.10 The accent-bar card.** A plain dark box with one bright accent line down one edge, holding an icon, a big number and a caption.
Allowed when: the edge has an invented silhouette (E3), not a straight bar.

**D4.11 Floating cards.** Small cards layered over a hero that bob or float on a loop, often with parallax or hover lift. Decorative motion with no purpose.

**D4.12 Floating tag pinned to an image.** A small pill (icon plus "28°C & clear") stuck to a corner of an image, almost always top-left.

**D4.13 The image card with overlay caption.** Portrait image tile, bottom gradient scrim, small uppercase meta label, serif name, place line, description, "link arrow". The image is fine; the wrapper is the template.

**D4.14 The three-tier pricing block.** Free / Pro / Enterprise; tiny pill above each heading; big price with "/ mo"; checkmark list; slop CTA; middle card highlighted with a glowing gradient border and a floating "MOST POPULAR" pill.
Instead: compose pricing from the actual offer. If columns are used, see D9.3 for alignment.

**D4.15 The testimonial / quote card.** Wide rounded card, big quote-mark icon centred on top, centred quote, avatar, name and job title ("VP Engineering, Northwind Labs"), plus a fake impressive metric ("velocity jumped 32%"). Sibling tell: wrapping example text in big decorative curly quotes or a giant quote glyph to make it feel human.
Instead: real quotes from real, consenting people, set with real type and space, no ornamental quote marks.

**D4.16 Gradient-circle initials avatar.** Two letters on a gradient circle as a stand-in for a photo. Doubly slop in blue-to-purple.
Instead: real photos with permission, or no avatar.

**D4.17 Countdown timer.** DAYS / HRS / MIN / SEC boxes to fake urgency.
Allowed when: something is genuinely ending at that time, and the timer is designed for the brand.

**D4.18 The email-pill plus button form.** A long pill email input beside a pill button ("you@email.com" + "Request an opening"). The single most repeated component.
Instead: design the capture for this brand and this moment.

**D4.19 The sun-and-moon theme toggle.** A rounded pill sliding a knob between a sun and a moon.
Instead: a theme control that belongs to the visual language (G6).

**D4.20 The dot under the active nav item.**
Instead: mark the current page with a weight or colour shift on the link itself. A genuine sliding tab indicator is a real pattern; a stray dot is not.

**D4.21 Dead controls and fake interactivity.** A tab switch, accordion, slider, toggle or button that looks interactive but does nothing.
Instead: every control works, confirmed by a real click. Static props (a faux search bar, a mock tab strip) must not invite clicks they cannot answer.

### D5. Icons, logos and illustration

**D5.1 Lucide everywhere.** `lucide-react` is a library of clean, consistent open-source line icons (https://lucide.dev): Sparkles, Coffee, Dumbbell, Plane, MapPin and so on. It has no brand logos. Its uniform thin-stroke look is a giveaway when it appears on every project.

**D5.2 Oversized icon in a coloured tile.** One big icon centred in a filled rounded square or circle, as a hero visual or feature bullet.

**D5.3 Any icon or logo with a box behind it.** An icon, brand mark, social glyph or integration logo set on a filled tile, chip, circle or bordered box.
Instead: the bare mark on the surface, sized and coloured with intent. Separation comes from the mark's own weight, colour and spacing.

**D5.4 Redrawn line icons.** Hand-drawing the usual shapes (a document with a checkmark, linked circles for "agent", a shield with a tick) does not make them yours. If an icon could sit on any other product unchanged, it is slop.
Instead: custom iconography with a real point of view (E6).

**D5.5 No icons at all.** Stripping every icon to dodge the icon-pack look leaves a flat, lifeless interface.
Instead: your own icons, not zero icons.

**D5.6 The logo lockup.** An icon in a small gradient rounded square (an app-icon "squircle") with the company name beside it in a generic geometric font.

**D5.7 Missing or faked logos.** Two failures, one coin. Leaving out real marks where they would add legitimacy (a social row in the footer, a "works with" strip, a real customer wall) can look thin. Inventing logos or faking customers is worse.
Instead: if marks are not needed, leave them out. If needed, use the real ones from an official source (the brand's own asset or a reputable brand-icon package), at one consistent size, in one quiet treatment, with the rights to show them (G8) and sanitised (G9).

**D5.8 Crude CSS/SVG "illustrations".** Bar charts from rounded divs, floating circles and spheres, a "plate" of gradient balls, dashed orbit rings, mock stat cards.
Instead: real photography, real illustration, real product UI, or a crafted SVG (E13).

**D5.9 Fake macOS / app window mockup.** A CSS window at Mac radius with red/yellow/green dots and a mock UI inside (kanban columns, avatars, status pills).
Allowed when: it shows a real, fully populated product (F4). If the product is just a file, show the file.

**D5.10 The fake code-snippet window.** Dark panel, traffic-light dots, a `quickstart.ts` tab, a syntax-highlighted call to a made-up SDK in the same palette (purple keywords, green strings, grey comments) in JetBrains Mono.
Allowed when: the code is real, for a real product, styled for the brand.

### D6. Layout and composition

A recoloured layout is still slop. Each of these compositions is a tell on its own.

**D6.1 The default hero stack.** Eyebrow, headline, subline, primary button plus a secondary text link, stacked down the middle.

**D6.2 The hero stack with a panel on the right.** The same stack on the left, with a product panel, image or card floating on the right. It does not matter what is in the panel; the skeleton is the slop.

**D6.3 The split hero ("premium" version).** Text column (letterspaced kicker, big serif headline with one emphasised word, quiet subline, two buttons, a stat row under a hairline) and a framed visual card with a caption and a floating tag. Reused for photographer, restaurant and real-estate brands with only colours changed.
For D6.1 to D6.3, instead: change the axis, split or offset the pieces, drop pieces, let the signature artifact own the space.

**D6.4 A hero that does not own the first screen.** A short hero with a stray half-section peeking in below, unaligned.
Instead: size the hero to the viewport (use `svh`/`dvh` units on mobile) or deliberately control exactly what shows at the bottom edge. The first frame is balanced.

**D6.5 Small label over big heading.** A tiny label or uppercase kicker above a large heading, in any typeface. The kicker-plus-serif-H2 is the most common version, at the top of nearly every section.
Instead: vary how sections begin: no label, a different scale, open with an image, a number, a full sentence, or nothing.

**D6.6 The eyebrow tick.** A short (~30px) hairline, often a fading gradient, beside a kicker label.
Instead: drop it. Give the label presence through type, weight, colour or spacing.

**D6.7 The big serif statement block.** A section that is just a kicker plus one large serif sentence with one italic accent word, used as the "philosophy" beat.

**D6.8 The inset enquiry island.** A rounded panel floated with margin on all sides, holding kicker, serif headline with italic accent, one-line lead and a form, used as the default closing section every time.
Allowed when: the island is a composed, one-off choice for this page (E11), not the default closer.

**D6.9 The pre-footer CTA banner.** A wide rounded slab flooded with a gradient, centred headline, a byline ("Free to start, no credit card required"), and one or two buttons.

**D6.10 Numbered steps beside a vertical line.** A "how it works" column of 01 / 02 / 03 with a rule down the side. A square-capped line makes it worse.
Instead: compose sequences some other way.

**D6.11 Unrounded hairline rules as decoration.** A thin square-capped line dropped in to separate, set beside text, under a label, or down a list.
Instead: real spacing and hierarchy. If a line must exist, give it intent: rounded caps or part of an invented shape.

**D6.12 Content flung to the far edges.** Pieces split to opposite rims (tagline hard left, link columns hard right) with a dead gulf between.
Instead: unless the asymmetry is composed on purpose, put content on a real grid aligned to the margins above, and balance weight across the width.

**D6.13 The standard footer.** Big wordmark plus one-line tagline, a full-width rule, four columns of links under uppercase mono labels, another rule, then a copyright row with a cute sign-off. Tidy and empty of ideas.

**D6.14 The oversized footer wordmark done as slop.** It fails when: it is not centred or aligned to anything; the tops of capitals or ascenders are clipped; a gradient inside the type clashes with the gradient behind; the face is a default and the treatment is nothing; there is empty space beneath it; or it is buried under a background grid.
Allowed when: composed (E19): on the layer above any texture, flush to the bottom edge (bleeding off only intentionally while staying whole and centred elsewhere), with a deliberate case and tracking, room above, and a colour or texture that belongs to the brand. Otherwise, leave it out.

**D6.15 Recycling your own house style.** Kicker heads, a serif statement, image cards, an inset island with a pill form, a serif-plus-sans pairing, an oversized wordmark, reskinned for every brief. That kit is a template.

**D6.16 The same skeleton, recoloured.** Documenting a layout as slop and then rebuilding it in new colours, or as flat ink-on-paper, is still the same prefab.

**D6.17 Stacking slop layouts.** Individually arguable blocks stacked in one page multiply into something unmistakably generated. "The pieces are fine" is not a defence.

**D6.18 The whole SaaS product-page template.** The Stripe / Linear / Vercel clone in this order: two-column hero with a shadowed product panel; three feature cards with icons in tinted tiles; a "for shoppers / for stores" tab switch; two or three pricing cards; an FAQ accordion; a full-width CTA slab; a multi-column footer split by rules. It feels safe and professional and it is pure slop. If you are about to build this stack, stop and decide a signature first.

### D7. Motion

**D7.1 The invisible-content trap (absolute rule).** Content that starts at `opacity: 0` or translated away, waiting for JavaScript, a scroll timeline or an animation library to reveal it. When the reveal does not fire (background tab, unsupported timeline, throttled engine, hydration hiccup, screenshot pass) the section is empty. This applies to CSS `animation-timeline: view()`, to IntersectionObserver class toggles, and to Motion/Framer `initial={{opacity: 0}}`.
Rule: content is visible by default. Animate things already on screen (hover states, marquees, a spinning mark, a sliding tab indicator, a counting number, parallax on visible elements). An entrance effect is acceptable only if, with no JavaScript and no animation, the content still shows fully. Prefer animating position (`y`) over fading in from zero.

**D7.2 Underline animations on links, nav and buttons.** Underlines that grow, wipe or travel in on hover. Do not animate underlines at all.
Instead: a clean tonal shift or a sliding icon.

**D7.3 Botched fill animations.** A bar whose caps flip from sharp to round mid-transition (the sign of `scaleY` on a rounded shape), that fills only part of its track, or that stutters.
Instead: animate a clip, or width/height with stable caps, fill the full track, and ease smoothly. This is how custom fills on bespoke elements (progress, a signature marker) must be done.

**D7.4 Dead-looking pages.** "Boring, static, the menu has no animation" is a real rejection even when nothing is slop.
Instead: authored, purposeful motion: a nav that enters and responds, a signature that drifts, scroll-linked parallax, crafted hovers. Calm is allowed; dead is not.

### D8. Copy and content

**D8.1 Walls of copy.** Many stacked lines read as filler. Say less; let hierarchy and visuals carry meaning.

**D8.2 Generic placeholders.** Lorem ipsum, "Northwind Labs", invented job titles, round fake metrics. Use real names, real data and real copy, or clearly ask the user for them.

**D8.3 Fake proof.** Invented testimonials, customers, ratings or statistics. Never.

**D8.4 Em dashes and decorative quotes.** See D2.11 and D4.15.

### D9. Execution failures

These are craft mistakes that make good designs look broken. Check each one by zooming in, not by eye at normal size.

**D9.1 Nothing is actually centred.** A number high in its circle, a glyph low in its tile, a label off-axis in its pill. Verify every intended centre, mathematically and optically. In SVG: `text-anchor: middle` centres horizontally only; add `dominant-baseline: central` (or a measured `dy`) for vertical. A glyph's optical centre is not its bounding-box centre. Rotation, stroke and padding move the real centre.

**D9.2 Clear the cut.** Text or controls shaved by a `clip-path`, notch, `overflow: hidden` or fixed height: headline caps sliced flat, a control missing its top pixels, vanished descenders. Whenever you add any of these, pad content clear of the cut by more than the cut removes, then zoom into that exact edge and check pixel by pixel.

**D9.3 Misaligned parallel columns.** In any side-by-side comparison (pricing, plans, features, before/after), title, price, description, list start and button must sit on shared lines across all columns, whatever the copy length. Equal-height cards, buttons anchored to the bottom, reserved space for variable copy, one shared grid. Hold the slot when a value is missing rather than collapsing it.

**D9.4 Text jammed against the edge.** Copy touching the viewport or container edge. Give every text block a deliberate, consistent gutter. Exception: an oversized wordmark cropped on purpose.

**D9.5 Content clipped where sections overlap.** A higher layer (a panel rising over a sticky screen, a sliding sheet) guillotines content that should continue. Keep continuing content on the visible layer and clear it past the seam.

**D9.6 The off-centre strike or cut line.** A strike-through, cross-out or redaction bar that floats low or high. Run it through the true vertical centre of the letterforms, measured against the real x-height.

**D9.7 Contrast.** See D1.9 and G2.

---

## Part E: What premium actually looks like

These are the crafted versions of tools that appear as slop in Part D. The difference is execution, restraint and uniqueness.

**E1. Real translucency (liquid glass).** A material, not a frosted box. It sits over a backdrop worth showing (a photograph, a rich colour field, live content), refracts it, carries faint chromatic dispersion at the edges, a bright highlight along the top lip, light frost, and tightly tuned inner and drop shadows. It reacts to what is behind it.

**E2. Self-coloured borders and tonal elevation.** Shift the container's surface a hair lighter or darker than the background, add a 1px stroke in the surface's own colour at low opacity, and a soft inner highlight on the top edge. An edge you sense rather than see.

**E3. Bespoke geometry.** Invent the shape instead of accepting the rectangle. A straight accent bar is a preset; a marker that cuts in on a diagonal, runs straight down, then kicks back out on a diagonal at the base reads as drawn on purpose. Same for chamfers, notches, brackets, connectors, dividers and corners.

**E4. Bare icons, no container.** Only what must be on screen is on screen.

**E5. Say less.** Terse, short lines. Confidence shows in what you leave out.

**E6. Custom iconography.** A bespoke set, consistent in stroke, corner and grid, with an invented detail or construction that belongs to the brand.

**E7. Authored micro-interactions.** Motion written for one element: tuned easing, a slightly over-extended "popped" cap on a custom fill, tight shadows in motion. Not a global fade-and-translate. (Never on link underlines: D7.2.)

**E8. Considered light.** When light is used, its colour, direction and falloff are chosen: a warm volumetric amber wash, a single directional ray. Never the reflexive blue-purple bloom.

**E9. Premium noise.** Fine film grain or perlin noise at very low opacity on surfaces and gradients. Removes banding and adds tactility. Felt, not seen.

**E10. Full-page, large-scale composition.** Pages composed as one frame: confident scale, oversized headlines, generous negative space, an enormous wordmark used as a deliberate watermark.

**E11. Inset "island" sections.** A section floated as a rounded panel with equal margin on all sides, on a subtly different surface (often with grain), so it reads as a detached object. Used once, on purpose, never as the default closer.

**E12. Real logo walls.** Recognisable marks ("used in production by") in a single colour, even sizing, quiet treatment. Only brands you can honestly claim, with permission.

**E13. Crafted custom SVG.** A product or illustration hand-built with correct proportions, layered detail, considered colour and light. When a bespoke SVG object is the strongest thing on the page, it is done right.

**E14. The gloss is the good part of glass.** The clean specular sheen across the top usually works. Keep it, and fix the blur, leak, halo and pop around it.

**E15. Blueprint / canvas details.** Sparing engineering marks: ruler ticks along one edge, corner registration or crop marks, a few dashed guides at low opacity, monochrome. Buildable with small SVG marks and `repeating-linear-gradient`. Never a full-bleed grid (D3.13).

**E16. A fine textured micro-grid.** A precise small module grid with grain or a noise gradient, confined to one surface (footer or feature panel). If it looks like graph paper, it failed; if it looks like printed substrate, it works.

**E17. Grainy gradients.** Every large colour transition carries dithered grain.

**E18. Scroll-authored motion.** Elements that shift, settle or parallax as they move through the viewport. Subtle, fast, tied to scroll, gated behind `prefers-reduced-motion`, and never hiding content (D7.1).

**E19. The footer wordmark placed right.** On the layer above any texture. Anchored flush to the bottom with no gap beneath, bleeding slightly off the bottom edge if intended, while links and colophon sit above it. Deliberate tracking and case, centred or deliberately aligned.

**E20. Licensed type.** The least-slop reference sites license or self-host signature type (for example Perfectly Nineties from Pangram Pangram, Matter from Displaay, and peers like Söhne, GT America, Tiempos and Klim families) and pair it with a quiet neutral body. Identify fonts from the source, never from memory, and license them properly (G8).

**E21. Professional does not mean lifeless.** A correct, sparse, well-typed page with zero invention feels unfinished. Clean is the floor. Add a few authored moments: precise hover states, a row of marks that drift gently, a footer with oversized type and its own texture, a scroll-driven detail, a kinetic accent. Calm can be gorgeous; empty is a miss.

**E22. Liquid-glass button: a reference recipe.** Real parameter values from one glass-button spec, kept to show what premium glass is made of. Swap the colour and typeface for the brand; keep the structure. Always over a real photographic or rich backdrop.

Shared base:
- Fill `#2575FF`. Thick variant: fill at 50% opacity so the backdrop reads through. Thin variant: solid.
- Label and icon: `#FFFFFF` at 100%. Type in the example: Geist Medium, 20. Icon-to-label gap 8.
- Padding: 20 horizontal, 14 vertical.
- Two hairline strokes at 20% opacity in near-surface colours (one cyan `#22BBFD`, one white `#FFFFFF`): a self-coloured edge, not a contrasting outline.
- Inner shadow (top highlight): `#FFFFFF`, 20%, offset Y 1, blur 32.
- Drop shadow tinted to the fill (`#2575FF`, not black): 6% opacity, offset Y 3, blur 3.

Material parameters:
- Thin pill: light angle -45°, light 80%, refraction 80, depth 2, dispersion 40, frost 6, splay 0.
- Thick pill: light angle -50°, light 60%, refraction 64, depth 44, dispersion 67, frost 2, splay 20.

What they mean: light angle/intensity is the specular highlight direction and strength; refraction is how hard the backdrop bends; depth is apparent thickness (2 is a thin sheet, 44 a thick slab); dispersion is the chromatic edge split; frost is blur; splay is how far refraction spreads past the shape.

In CSS (no native refraction or dispersion): `backdrop-filter: blur()` for frost plus `saturate()`/`contrast()` for lensing; an inset white `box-shadow` for the top highlight; the two low-opacity strokes via layered border or box-shadow; the tight colour-matched drop shadow; fake dispersion with a 1px cyan/magenta edge offset or a thin edge gradient. SVG `feDisplacementMap` can do true refraction if worth the performance cost (G4).

---

## Part F: The signature: how uniqueness is made

The reference sites (Craft, Paper, Podqi, Droppable, Portal) look nothing alike, yet make uniqueness the same way. A flat background with boxes and a neutral grotesque scores zero on every line below.

**F1. One signature artifact.** One custom, high-effort focal object that could not be pasted into another site. Craft: a torn-paper collage sky. Portal: a painted dusk landscape with a tiny robot on a rock. Podqi: a flowing green silk render. Droppable: a starfield with a bold green wordmark. Paper: a layered design canvas with a terminal over it. Decide this first. Without external assets, it is a crafted SVG scene, a detailed product UI, or a pre-generated image you have rights to.

**F2. Atmosphere, not a flat fill.** A composed environment with depth and mood behind the content, carried down the page.

**F3. Layered depth.** Foreground copy, a midground focal object, a background scene, with at least one element crossing a layer boundary (overlap, bleed off an edge).

**F4. The product as a real, populated artifact.** A detailed, fully populated UI with real names, data and copy (and working controls if interactive), floated with depth, often clipped at the bottom edge. Empty placeholder boxes are what boring is made of. Show a product UI only when there is one.

**F5. Character in the display type.** A distinctive serif or characterful display face, set large. Body can be neutral; the signature line cannot.

**F6. One bespoke silhouette.** One custom-cut shape signs the page (Droppable's pricing card shaped like a receipt with a torn zigzag edge; a notch; a contained pill nav).

**F7. A treated nav.** Not a flush default row of links: contained, centred, large, or carrying real marks. A decision, part of the same visual language.

**F8. Real specificity.** Real logos, real names, real data, real copy.

**The formula:** uniqueness = one signature artifact + atmosphere + layered depth + a character display face + one bespoke silhouette + a treated nav + real specifics. Miss the signature artifact and no amount of clean spacing rescues the page.

### F9. A kit of premium moves

These are tools for the right context, never a checklist. Two equal failures: using everything (noise), and using nothing that fits (flat). Every move must complement the others in one system.

- **Signature serif headline.** A distinctive, slightly high-contrast serif with real character, set very large, optionally with one word in italic or one tonal accent. Must be a licensed or deliberate face (not Cormorant, not a Didone on autopilot), headline held to one or two lines, and not repeated from your last project.
- **Two-tone headline.** One word or the second line set apart by italic or a tonal shift. One emphasis per headline.
- **Full-bleed atmospheric hero.** One photographic, rendered or painted scene edge to edge, headline over it, nav floating on top. Serene and immersive. Approximate with a crafted SVG scene, grained layered gradients, or a licensed image.
- **Animated character field.** Scattered monospace glyphs drifting over a soft gradient, faintly twinkling in a slow seamless loop. Low contrast, behind content, gated behind reduced motion. Must genuinely move and relate to the content (D3.14). Good for data, dev, AI and security products.
- **Gradient-filled icons.** A brand mark or single icon whose fill is a small multi-stop gradient, like an enamel jewel. Tiny, contained, sparing. Not the slop background gradient.
- **The up-right arrow.** The default horizontal right arrow is a stock tell. An up-right diagonal arrow drawn to match the system's stroke and corners shows care. Every glyph is part of the identity.
- **One cohesive visual language.** Nav, buttons, arrows, radius, borders and background all speak the same language (sharp corners everywhere, one arrow reused, one gradient threaded through mark, button and background).
- **The premium glass CTA.** Glossy, softly blurred glass over a rich background, executed cleanly (E1, E14, E22). Pointless over a flat fill.

### F10. Field notes: what actually landed

- **Cohesion is the whole game.** The loudest failure was incoherence: individually fine parts that did not belong together. "Blue AND green AND a warm accent" read as ugly. One palette, one type voice (one family across weights or optical sizes, or one display plus one quiet neutral), one signature, then compose sections from that world.
- **"Creative" is not "realistic".** When a brief asks for creative or maximal, literal stock-style realism (a photoreal lake) reads as the opposite. Use one authored medium (cyanotype prints, one illustration style, pixel art, a riso look, a painted sky). A limited-palette medium makes images cohere automatically: a cyanotype's own blue became the page's blue, with zero seams.
- **Take the design language from references, never the content.** Lift palette mood, type energy, motion and kind of hero; write original copy, layout and artifact. Copying a reference's headline and product window shows.
- **Distinctive type keeps moving.** Fontshare is a free source outside the Google rotation, but its popular faces (Clash Display, General Sans, Satoshi, Switzer, Cabinet Grotesk) already read as the generic startup look. Reach further for character (for example Fontshare's Pally, Gambarino, Sentient, Tanker, or Velvetyne faces), render candidates before choosing, and pair with a true neutral body such as `system-ui`.
- **Dead-looking is a fail on its own.** See D7.4.

---

## Part G: Build standards

### G1. Components, libraries and dependency safety

**Use real components, art-directed.** Hand-rolling generic UI tends to reproduce slop defaults (sun-moon toggle, fill-plus-outline pair, underline hover) and ships broken controls. Use a tested, accessible library's primitives, then art-direct them hard for the brand.

**The standing toolkit** (all free; verify current status and licence before use):
- **Motion** (motion.dev, formerly Framer Motion). Install `motion`, import from `motion/react`. The animation engine; works without Tailwind. Springs, gestures, scroll-linked transforms (`useScroll`, `useTransform`), animated numbers, marquees, layout animation. Motion+ and its AI kit are paid: do not use them unless the user provides access.
- **shadcn/ui** (ui.shadcn.com). React + Radix + Tailwind accessible primitives (button, dialog, tabs, accordion, form, table, command palette), added via its CLI.
- **tailark** (tailark.com). Tailwind + shadcn marketing blocks and pages.
- **motion-primitives** (motion-primitives.com). Motion + Tailwind animated components (text effects, marquee, animated tabs, morphing dialog).
- **kokonut UI** (kokonutui.com). Tailwind v4 + Motion components, including AI input and loading states, added through the shadcn CLI with the kokonut registry.

**Tailwind or not.** In a Tailwind project, use these directly. In a project without Tailwind, use Motion for animation and adapt the structure of the others into the project's own styling. Never add global Tailwind to a large existing non-Tailwind codebase to use one block: it can break every other page.

**De-slop every prebuilt piece.** Libraries ship slop defaults (blue-purple gradients, glowy pills, fill-plus-outline pairs, tracked caps everywhere, the default hero stack). Keep the behaviour and structure; replace the styling. Run prebuilt blocks through this whole file like your own work.

**Dependency safety (required):**
- Ask the user before installing any package, CLI or registry component. Say what it is and why.
- Prefer packages already in the project or on the user's approved list.
- Pin exact versions and commit the lockfile.
- Copy-paste registries (shadcn, kokonut and similar) put third-party code directly into the project: read the added files before keeping them.
- Never run install scripts or code from unknown sources, and never paste tokens or secrets into commands, config or chat.

### G2. Accessibility (target: WCAG 2.2 level AA)

- **Contrast:** at least 4.5:1 for body text, 3:1 for large text (about 24px, or 19px bold) and for UI component boundaries, icons that carry meaning and focus indicators. Tonal accents (D1.7) must still meet these.
- **Focus:** every interactive element has a visible `:focus-visible` style designed as part of the visual language. Never remove outlines without replacing them. Focus must not be hidden behind sticky headers.
- **Keyboard:** everything works with a keyboard alone, in a logical order. No keyboard traps. Menus, dialogs, tabs and accordions follow standard keyboard patterns (the library primitives in G1 handle this; keep them).
- **Structure:** semantic HTML (`header`, `nav`, `main`, `footer`, real `button` and `a` elements), one `h1`, headings in order, `lang` set on `html`.
- **Images:** meaningful images have alt text describing their purpose; decorative ones have `alt=""`. Decorative SVGs get `aria-hidden="true"`; meaningful icons get an accessible name.
- **Colour alone:** never the only signal for state, errors or links in running text.
- **Targets:** interactive targets at least 24×24px (aim for 44×44px on touch).
- **Motion:** respect `prefers-reduced-motion` (reduce or stop non-essential motion). Anything that moves for more than five seconds needs a way to pause it. No flashing more than three times a second. No autoplaying sound.
- **Forms:** visible labels (placeholders are not labels), errors in text next to the field and announced, correct `autocomplete` and input types.
- **Zoom and reflow:** usable at 200% zoom and at 320px width without horizontal scrolling.
- **Hover-only content:** anything revealed on hover must also be reachable by focus and touch.

### G3. Responsive design

- Design and check at around 360, 390, 768, 1024, 1280 and 1440px wide.
- No horizontal scroll at any width.
- Fluid type with `clamp()`, with display lines still held to one or two lines on mobile, or recomposed.
- The hero owns the first screen on phones too (use `svh`/`dvh`, not `vh`, for full-height sections).
- Signature artifacts, overlaps, layered depth and parallax must have a deliberate mobile composition, not a squashed desktop one.
- Gutters (D9.4) and alignment (D9.3) hold at every width; comparison columns stack cleanly.
- Hover effects are an enhancement; touch users get the same information.

### G4. Performance

Targets (Core Web Vitals, measured on mobile): LCP under 2.5s, CLS under 0.1, INP under 200ms.

- **Images:** AVIF or WebP, sized with `srcset`/`sizes`, width and height set to prevent layout shift. Lazy-load below the fold; never lazy-load the hero image.
- **Fonts:** self-hosted WOFF2 (in Next.js, via `next/font/local`), subset to needed characters, `font-display: swap`, preload only the signature face. At most two families and a few weights.
- **Effects budget:** `backdrop-filter`, large blurs, `mix-blend-mode` and SVG filters are expensive. Use few, keep their areas small, avoid stacking them.
- **Motion:** animate `transform` and `opacity` only. Pause canvas or WebGL backgrounds when off-screen or when the tab is hidden.
- **Grain:** a small tiled noise texture, not a full-screen live filter.
- **Scripts:** ship as little JavaScript as possible; no heavy libraries for effects CSS can do.

### G5. States

Design all of these, not just the happy path:
- Hover, focus, active, disabled, selected, for every control.
- Loading (skeletons that match the final layout, so nothing jumps).
- Empty (a useful message and next step).
- Error and success, including form validation next to each field and a clear form-level message.
- A designed 404 page.
- Long content and short content (a very long name, a missing image, a missing value: hold the slot, D9.3).

### G6. Light and dark themes

- If the site offers both, design both deliberately. Never just invert colours.
- Define colours as tokens (CSS custom properties) and respect `prefers-color-scheme` by default.
- Each theme meets contrast rules (G2) and avoids its own slop defaults (D1.4 for dark, D1.5 and D1.6 for light).
- Prevent a flash of the wrong theme on load.
- The theme control belongs to the visual language (D4.19), has an accessible name and shows its current state.

### G7. Privacy and GDPR

For sites serving EU visitors, and German clients in particular. This is general guidance, not legal advice: confirm specifics with the client's legal adviser.

- **Self-host fonts.** Loading Google Fonts from Google's servers sends visitors' IP addresses to Google; a Munich court (LG München I, January 2022) found this breached GDPR. Self-hosting is the default.
- **No third-party calls before consent.** Embedded YouTube, Google Maps, social feeds, chat widgets and non-essential analytics must not load until the visitor agrees. Use click-to-load placeholders.
- **Consent banners without dark patterns.** "Reject" as easy and as visible as "Accept", no pre-ticked boxes, choices can be changed later.
- **Forms collect the minimum.** Link the privacy policy at the point of collection; use double opt-in for newsletters.
- **Legal pages.** Privacy policy, and for German businesses an Impressum, reachable from every page.
- **Analytics.** Prefer privacy-friendly, EU-hosted or cookieless tools.

### G8. Rights and licensing

- **Fonts:** a web licence covering this site and its traffic. Never copy font files from another site. Free fonts: check the licence (Fontshare and Google fonts allow commercial use; others may not).
- **Images and video:** owned, licensed, or generated with clear usage rights. Keep a record of sources.
- **Logos:** customer and partner logos only with permission. Brand icons (social, integrations) used per the brand's guidelines, unaltered.
- **Testimonials and names:** real, with consent.
- **References:** take the design language, never their text, assets or layouts verbatim (F10).

### G9. Front-end security basics

This file is not a security standard, but design work touches these:
- **Sanitise SVGs** from the web (logos, icons) before inlining: remove `<script>`, `on*` event attributes, `<foreignObject>` and external references (for example with SVGO plus a sanitiser such as DOMPurify).
- **Never inject untrusted content as HTML** (`innerHTML`, `dangerouslySetInnerHTML`).
- **External links** opening in a new tab use `rel="noopener noreferrer"`.
- **Forms:** validate on the server as well as the client; add spam protection (honeypot or a privacy-friendly challenge); never put API keys or secrets in front-end code.
- **Third-party scripts:** as few as possible, from trusted sources, with Subresource Integrity where supported; recommend a Content Security Policy.
- **No external CDNs for core assets** where self-hosting is practical (also helps G7).

---

## Part H: Pre-ship checklist

Run this in a real browser before every handover. Fix failures, then report briefly.

**Idea**
- [ ] There is one signature artifact that could only belong to this brand.
- [ ] Palette, type voice and visual language form one coherent world.
- [ ] Atmosphere carries below the fold.
- [ ] Sections open in different ways; no block matches a Part D layout tell.
- [ ] Fonts, pairing and layouts differ from earlier projects (Appendix B).
- [ ] The page is alive: authored motion exists and responds.

**Slop scan**
- [ ] No blue-purple, candy, aurora, cream, slop-gray or blue-charcoal defaults.
- [ ] Accents are tonal; no gradient text; no saturated splashes.
- [ ] No glows, halos, inner glows, cut-off glows, blooms or fake shadow boxes.
- [ ] No icons or logos in boxes; no pill eyebrows; no chips everywhere.
- [ ] No fill-plus-outline button pair; buttons do not jump on hover; no animated underlines.
- [ ] Display type is not from the overused list; no mono house voice; no single label treatment everywhere.
- [ ] No em dashes or fake proof in the copy.

**Craft**
- [ ] Every intended centre verified by zooming in (including SVG text).
- [ ] No content clipped by any cut, notch, overflow, fixed height or overlapping section.
- [ ] Parallel columns aligned row by row, buttons on one line.
- [ ] Every text block has a gutter; no content flung to edges by default.
- [ ] Shadows (if any) are tight, directional, tinted, seamless.
- [ ] Glass (if any): no banding, leak, halo or pop.
- [ ] Image edges feathered with no seams; grain only behind content; no banded gradients.

**Function**
- [ ] Every control clicked and confirmed working.
- [ ] Content fully visible with JavaScript disabled and with animations off.
- [ ] Hover, focus, active, disabled, loading, empty, error and success states designed.

**Accessibility**
- [ ] Contrast meets G2 everywhere, including tonal accents and both themes.
- [ ] Full keyboard pass with a visible focus style.
- [ ] Semantic structure, alt text, labels, reduced motion respected.

**Responsive and performance**
- [ ] Checked at phone, tablet and desktop widths; no horizontal scroll; hero owns the first screen on mobile.
- [ ] Images optimised and sized; fonts self-hosted and subset; effects budget respected.

**Privacy, rights, security**
- [ ] No third-party requests before consent; fonts self-hosted.
- [ ] Rights confirmed for fonts, images, logos and testimonials.
- [ ] SVGs sanitised; no secrets in front-end code; external links safe.
- [ ] No package installed without the user's approval; versions pinned.

**Handover note**
- [ ] Short summary of what was checked and fixed, plus anything not verified.

---

## Appendix A: Overused fonts

Faces observed as overused when they carry the brand. Not exhaustive: the principle in D2.1 matters more than the list.

**Sans and grotesque:** Inter (the most common), Space Grotesk (usually with Inter, the "techy SaaS" voice), Sora ("AI / deep-tech" headings), Syne ("edgy / music / creative" in bold uppercase), Archivo (heavy all-caps "streetwear / sporty", often shown solid, accent-coloured and outlined at once so it reads as three fonts), Work Sans (with Fraunces), Onest, Darker Grotesque, Geologica, Hanken Grotesk, Spline Sans, Schibsted Grotesk, Gabarito, Figtree, Quicksand. "Tasteful" swaps: Big Shoulders, Bricolage.

**Rounded display novelty faces:** Bagel Fat One, Baloo, Fredoka, Chewy, Lobster and similar, especially when they carry headings, wordmark, prices and buttons over a default `system-ui` body.

**Serif:** Fraunces (with Work Sans), Cormorant Garamond (the default "elegant / luxury / editorial" serif, usually with one italic word, swapping Jost, Mulish or Inter beside it), the Didones (Bodoni Moda, Didot, Playfair and kin, the reflexive "luxury / fashion / watch" serif), Petrona, Hedvig Letters Serif, Brygada 1918, Young Serif (the free "warm, chunky, antique spec-sheet" serif carrying headlines and stats), Newsreader, Instrument Serif.

**Mono:** JetBrains Mono (the default for every fake code block), IBM Plex Mono, Spline Sans Mono, Fragment Mono. Any mono used as the house voice.

**Popular "safe alternatives" that now read generic:** Fontshare's Clash Display, General Sans, Satoshi, Switzer, Cabinet Grotesk.

**Pairings:** Fraunces + Work Sans; Space Grotesk + Inter; Cormorant Garamond + any clean sans; any serif headline + clean sans repeated across projects.

---

## Appendix B: Project log

The agent cannot remember other projects unless told. Keep this log updated (or give the agent your own) so the originality check (Part C, step 5) has something to check against.

| Project | Date | Display face | Body face | Palette (main tones) | Signature artifact | Section shapes used |
|---|---|---|---|---|---|---|
| | | | | | | |
| | | | | | | |
