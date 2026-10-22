# Final Cleanup Pass

You are doing a **final cleanup pass** on this project before handoff/deploy. The goal is a leaner, tidier, safer codebase that **behaves exactly the same** as before. When in doubt, leave it alone and report it.

Optional scope from the user (if empty, the whole repo): $ARGUMENTS

---

## Golden rules (read first, never break)

1. **Zero behavior change.** No refactors, renames of public things, logic edits, UI/style changes, dependency upgrades, or "improvements". Only remove what is provably unused and fix lint/format issues.
2. **Use the project's own tools and config.** Use the existing package manager (match the lockfile), linter, formatter, and scripts. Don't add new lint rules, new formatters, or new tooling configs. If no formatter is configured, don't reformat the whole codebase.
3. **Prove before you delete.** Something is "unused" only if you've searched the whole repo for it (including string references, config files, and framework conventions — see "Hidden usage" below). If you can't prove it, list it as "Needs review" instead of deleting.
4. **Nothing destructive or irreversible.** Don't rewrite git history, force-push, delete branches, or run `git clean`. Don't commit or push unless I explicitly ask. Remove tracked generated files with `git rm --cached` (untrack), not by deleting them from disk.
5. **Never print secrets.** If you find one, show only the file, line, and a masked preview (e.g. `sk_live_****9f2a`).
6. **Ask before big removals.** If you want to delete more than ~10 files, a whole folder, a route/page, or any dependency you're less than certain about, stop and show me the list first.

---

## Step 0 — Safety net & baseline

1. Run `git status`. If there are uncommitted changes, stop and tell me (so my work-in-progress doesn't get mixed with cleanup). Suggest creating a branch like `chore/cleanup`.
2. Detect the stack: framework(s), language(s), package manager, monorepo/workspaces, platforms (web, iOS, Android, desktop, server).
3. Find the project's check commands (from `package.json` scripts, `Makefile`, `pyproject.toml`, README, CI config, etc.): **install, lint, format check, typecheck, test, build**.
4. Run them **before changing anything** and record the results as the baseline. Note any errors/warnings that already exist so you don't blame them on the cleanup — and so you know what "no worse than before" means.

---

## Step 1 — Audit (report before changing)

Scan and build a findings list in these categories. For each item: file/path, what it is, evidence it's unused or problematic, and confidence (**Safe** / **Needs review**).

### A. Debug leftovers
- `console.log/debug/info/table/dir`, `print()`, `var_dump`, `dd()`, `debugger;`, `alert()` used for debugging, leftover `console.time`, test-only flags left on (e.g. `DEBUG = true`, mock data switched on, `.only` / `.skip` in tests).
- **Keep** intentional logging: `console.error`/`console.warn` in real error handling, calls through a logger utility, and anything in scripts/CLI tools whose job is to print output.

### B. Dead code
- Unused imports, variables, functions, types, exports, components, hooks, styles/CSS classes, and whole files nothing references.
- Commented-out code blocks (old code kept "just in case"). Keep explanatory comments, license headers, and `TODO/FIXME` notes — list the TODOs in the report instead of deleting them.
- Unused assets (images, fonts, icons, videos) — **only** if no reference exists anywhere, including CSS, HTML, JSON, CMS content, and native project files.
- Use a proper tool when available (e.g. `knip`, `ts-prune`, `eslint --report-unused-disable-directives`, `vulture` for Python, the compiler's unused warnings) and then double-check its results manually — these tools give false positives.

### C. Unused dependencies
- Check each dependency in the manifest against actual usage (e.g. `knip` or `depcheck` for JS/TS).
- **Do not remove** packages that are used indirectly: config-referenced plugins (Babel, PostCSS, Tailwind, ESLint, Prettier, Vite/Webpack/Metro), CLI tools used in scripts, `@types/*` packages, peer dependencies, polyfills, Expo/React Native native modules, and anything imported dynamically.
- Flag packages in the wrong section (runtime code using a `devDependency`, or build-only tools in `dependencies`) — report, don't move, unless clearly safe.
- Flag multiple lockfiles (e.g. both `package-lock.json` and `yarn.lock`) — report, don't delete.

### D. Lint, format & type errors
- Run the project's linter with autofix and formatter on the files you touch (or the whole repo if it was already formatted that way).
- Fix remaining lint/type errors **only** when the fix can't change behavior (unused vars, missing types, import order, etc.). If a fix might change behavior, list it as "Needs review".
- Don't silence errors with `eslint-disable`, `@ts-ignore`, `any`, or `# noqa` unless it was already the pattern used and you explain why.

### E. Secrets & sensitive data
- Search tracked files for API keys, tokens, passwords, private keys, connection strings, webhook URLs, service-account JSON, `.pem`/`.p12`/`.keystore` files, `.env` files, and hardcoded credentials in config (e.g. `firebase` configs with admin keys, Stripe `sk_live`, Supabase `service_role`, AWS keys).
- Use `gitleaks` or `trufflehog` if installed; otherwise use careful pattern searches.
- Note: some keys are meant to be public (e.g. Stripe publishable keys, Firebase web config, Supabase anon key). Mark those as "public by design" rather than as leaks.
- If a real secret is tracked: untrack the file (`git rm --cached`), add it to `.gitignore`, move the value to an env variable **without changing behavior** (only if trivial — otherwise report), and make sure there's a `.env.example` with placeholder values.
- If a secret appears in **git history**, do not rewrite history — tell me clearly that the key must be **rotated** (replaced) at the provider, because removing it from the code doesn't un-leak it.

### F. Generated & junk files / .gitignore
- Check that generated or machine-specific files are ignored and not tracked. Typical examples:
  - Dependencies: `node_modules/`, `vendor/` (PHP), `.venv/`, `Pods/`
  - Build output: `dist/`, `build/`, `out/`, `.next/`, `.nuxt/`, `.svelte-kit/`, `.output/`, `.expo/`, `android/app/build/`, `ios/build/`, `DerivedData/`
  - Caches: `.turbo/`, `.cache/`, `.parcel-cache/`, `.eslintcache`, `__pycache__/`, `.pytest_cache/`, `coverage/`
  - Env & local: `.env`, `.env.local`, `.env.*.local` (but keep `.env.example`), `.vercel/`, `.netlify/`
  - OS/editor junk: `.DS_Store`, `Thumbs.db`, `*.log`, `*.swp`, `.idea/` (unless the team shares it)
- Add missing entries to `.gitignore` (append, grouped with a comment — don't reorganize the whole file).
- Untrack anything that's already committed but should be ignored, with `git rm --cached`.
- **Don't** ignore things the project needs committed (lockfiles, `.env.example`, required native config, shared editor settings the team uses).

---

## Hidden usage — check before calling anything "unused"

Code and files can be used without a direct import. Before deleting, check for:
- **File-based routing & conventions:** Next.js `app/` & `pages/` (incl. `layout`, `loading`, `error`, `route`, `middleware`), Nuxt/SvelteKit/Remix/Astro routes, Expo Router `app/`, WordPress templates, Laravel/Rails views.
- **Dynamic references:** `import()` with variables, `require` by string, lazy-loaded components, registries/maps keyed by name, reflection.
- **Config & tooling:** files referenced in build configs, `package.json` (`main`, `bin`, `exports`, scripts), CI workflows, Dockerfiles, deploy configs (`vercel.json`, `netlify.toml`).
- **Outside the code:** assets referenced from CMS content, emails, markdown, `public/` files linked by URL (favicons, `robots.txt`, `sitemap`, OG images, `manifest.json`, `.well-known/`), native iOS/Android projects (`Info.plist`, `AndroidManifest.xml`, app icons/splash).
- **Public API:** exports of a library/package other projects consume, server endpoints called by mobile apps or third parties, webhooks.
- **Tests, stories & fixtures:** used by test/Storybook setup even if not imported by app code.

If any of these might apply, mark it **Needs review**.

---

## Step 2 — Apply the safe fixes

1. Show me the findings summary first (counts per category + anything risky). If there are no big/risky removals, continue with the **Safe** items; otherwise wait for my OK.
2. Work **one category at a time** (debug logs → unused imports → dead code → dependencies → lint/format → secrets/gitignore), so each change is easy to review and revert.
3. After removing dependencies, reinstall with the project's package manager so the lockfile stays in sync.

---

## Step 3 — Verify nothing broke

1. Re-run the same baseline commands: install, lint, format check, typecheck, test, build.
2. Compare to the baseline. Results must be **equal or better** — no new errors, no new failing tests, build still succeeds.
3. If something got worse, revert the change that caused it (or ask me) — don't "fix forward" with new logic.
4. If there's a dev server or app, mention which pages/screens I should click through manually to confirm.

---

## Step 4 — Final report

Give me a short, plain-language report:

1. **Summary** — one or two sentences on what changed.
2. **Removed** — debug logs, dead code, files, dependencies (with counts and the notable items).
3. **Fixed** — lint/format/type issues.
4. **Security** — secrets found (masked), what you did, and anything I must **rotate**.
5. **.gitignore** — entries added, files untracked.
6. **Checks** — before vs. after for lint, typecheck, tests, build.
7. **Needs review** — everything you deliberately left alone and why (including TODO/FIXME list).
8. **Suggested commit message(s)** — conventional style, e.g. `chore: remove debug logs and unused imports`.

Keep explanations simple — assume I'm not a developer.
