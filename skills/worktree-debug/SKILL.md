---
name: worktree-debug
description: Debug a specific commit by creating a git worktree, auto-detecting how to start the app, optionally injecting debug logging, and cleaning up on exit. Use when you need to test older code, bisect a bug, or compare behaviour between commits.
argument-hint: "[commit_hash]"
---

# worktree-debug

Debug any project at a specific commit using a git worktree.

## Step 1 — Ask which commit

Ask the user:
> "Which commit hash, tag, or branch do you want to debug?"

This is required — do not proceed without a clear answer.

## Step 2 — Ask about debug logging

Ask the user:
> "Should I add any debug logging to the code? If yes, describe what you want to log and where (file, function, or behaviour)."

If the user says yes, collect enough detail to locate the right file and function in Step 5.

## Step 3 — Create the git worktree

- Derive a worktree path: `../<current-repo-name>-debug`
- If the path already exists, remove it first: `git worktree remove --force <worktree_path>`
- Create the worktree: `git worktree add <worktree_path> <commit_hash>`
- Verify creation with: `git worktree list`

## Step 4 — Detect how to start the project

Read the project root at `<worktree_path>` and apply the first matching rule:

| Signal | Action |
|---|---|
| `package.json` with a `dev` script | Install deps (`npm/yarn/pnpm install`), then run `dev` script |
| `package.json` with a `start` script | Install deps, then run `start` script |
| `Makefile` with a `dev` or `start` target | `make dev` / `make start` |
| `requirements.txt` or `pyproject.toml` | `pip install -r requirements.txt`, then detect entry point |
| `Cargo.toml` | `cargo run` |
| `index.html` (static site) | `python3 -m http.server <port>` from the project root |

Choose a free port (default `5174`) or ask the user if the detected framework has a fixed port.

Run the server/app in the background and redirect output to `/tmp/worktree-debug.log`.

Verify it started: check the log and/or `curl` the local URL if applicable.

## Step 5 — Inject debug code (if requested in Step 2)

Based on the user's description:

1. Locate the relevant file and function inside `<worktree_path>`
2. Add clearly marked debug statements:

```
// DEBUG START
console.log('...', value);
// DEBUG END
```

(Use the language-appropriate logging mechanism: `console.log`, `print`, `println!`, `logging.debug`, etc.)

3. Restart the app if necessary so the new logging takes effect.

## Step 6 — Debug

- If a browser URL is available, open it with Chrome DevTools (`mcp__chrome-devtools`)
- Capture relevant output (console logs, network requests, UI interactions)
- Help the user interpret results and identify the issue

## Step 7 — Cleanup

Once the user is done:

```bash
# Kill the background process (HTTP server or dev server)
lsof -ti:<port> | xargs kill -9

# Remove the worktree
git worktree remove --force <worktree_path>
git worktree list
```

Confirm cleanup completed. Any debug code added in Step 5 is discarded together with the worktree.
