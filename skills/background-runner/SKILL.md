---
name: background-runner
description: Use for every Bash and PowerShell command except a bare trivial one, so it runs in the background.
---

- Every Bash AND PowerShell tool call runs with `run_in_background: true`. No judging duration, no "it's quick" exceptions.
- Foreground ONLY if the WHOLE command is a single bare `ls`, `pwd`, `echo`, `cat`, `git status`, `git log` or `git diff` (PowerShell: `Get-ChildItem`, `Get-Location`).
- Anything else is background: any `&&`, `;`, `||`, `|` or heredoc, and any other program (python, node, npx, tsc, playwright, sed, builds, tests, installs).
- A leading `cd X;` / `cd X &&` is NOT trivial and never makes the command foreground. Judge by the rest; if anything non-trivial follows, background it.
- Needing the result is NOT a reason for foreground: launch in background, do other work, then read the output when it's needed.
- Don't poll or wait. Read only the tail or error lines (`tail -n 30`, `grep -iE "error|fail"`), never the whole output.
- Redirect long output to a log file (`cmd > run.log 2>&1`) and read only what's needed.
- Don't announce each launched command. Report only failures or when a decision from the user is needed.
