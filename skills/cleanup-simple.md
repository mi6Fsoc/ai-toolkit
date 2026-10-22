# Cleanup Pass

Do a final cleanup of this project. **Don't change how anything works or looks** — only remove clutter and fix errors. Scope (optional): $ARGUMENTS

**Before you start**
- Check `git status`. If there are uncommitted changes, stop and tell me.
- Run the project's existing lint, typecheck, test, and build commands and note the results.

**Clean up**
1. Remove debug leftovers: `console.log`, `print()`, `debugger`, test flags left on. Keep real error logging.
2. Remove unused imports, variables, functions, files, and commented-out code. Keep TODO comments.
3. Remove unused dependencies, but not ones used by config files, scripts, or type definitions.
4. Fix lint and format errors using the project's own settings.
5. Make sure no secrets (API keys, passwords, `.env` files) are committed. If one was, tell me to replace it.
6. Make sure `.gitignore` covers build output, `node_modules`, caches, logs, and `.env` files. Untrack anything that shouldn't be committed with `git rm --cached`.

**Be careful**
- Only delete something if you're sure nothing uses it. Check routes, config files, and assets referenced by URL. If unsure, leave it and tell me.
- Ask me before deleting more than 10 files or a whole folder.
- Don't commit, push, or rewrite git history.

**When done**
- Re-run lint, typecheck, test, and build. Nothing should be worse than before. If something broke, undo that change.
- Give me a short, plain-language summary: what you removed, what you fixed, and what you left alone and why.
