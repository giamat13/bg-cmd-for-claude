---
name: background-runner
description: Use for every Bash command except trivial instant ones, so it runs in the background by default.
---

- Default: every Bash command runs with `run_in_background: true`. Don't estimate or deliberate about duration.
- Run in foreground only for trivial instant commands (ls, cat, git status, echo, pwd) or when the very next step needs the output right now.
- After launching: don't poll, don't wait. Continue with the next task.
- Check output only when its result is needed. Read just the tail or error lines (e.g. `tail -n 30`, `grep -iE "error|fail"`), never the whole output.
- Redirect long output to a log file (`cmd > run.log 2>&1`) and read only what's needed.
- Don't announce each launched command. Report only failures or when a decision from the user is needed.
