# bg-runner

Claude Code plugin: runs Bash commands in the background by default, so you can keep working. Minimal token use.

## Install

```
/plugin marketplace add giamat13/bg-cmd-for-claude
/plugin install bg-runner@bg-local
```

## What it does

- Bash commands run with `run_in_background: true`, except trivial instant ones.
- No polling or waiting; output is read only when needed (tail / error lines).
- Reports only failures or decisions needed.

Single skill: [skills/background-runner/SKILL.md](skills/background-runner/SKILL.md)

## License

MIT
