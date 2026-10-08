---
name: background-runner
description: Use for every Bash command except a fixed list of trivial ones, so it runs in the background.
---

- Every Bash command runs with `run_in_background: true`. No judging duration, no "it's quick" exceptions.
- Foreground ONLY for: `ls`, `pwd`, `echo`, `cat`, `git status`, `git log`, `git diff`. Nothing else, even if it seems fast (tests, python, node, sed, builds, installs, chains with `&&` or `;`).
- Needing the result is NOT a reason for foreground: launch in background, do other work, then read the output when it's needed.
- Don't poll or wait. Read only the tail or error lines (`tail -n 30`, `grep -iE "error|fail"`), never the whole output.
- Redirect long output to a log file (`cmd > run.log 2>&1`) and read only what's needed.
- Don't announce each launched command. Report only failures or when a decision from the user is needed.
