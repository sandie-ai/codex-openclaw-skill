# Codex + OpenClaw notes

## Codex
- Repo: https://github.com/openai/codex
- Install: `npm i -g @openai/codex` or `brew install --cask codex`
- Typical entrypoints: `codex`, `codex exec "..."`

## OpenClaw execution advice
- Run coding CLIs with PTY when possible.
- Set explicit `workdir` to the target project.
- For long jobs, run in background and monitor logs.
- Share concise progress updates when milestones change.
