# codex-openclaw-skill

A practical AgentSkill for using **OpenAI Codex CLI** inside **OpenClaw** coding workflows.

## What this skill does

`codex-openclaw` helps an agent:
- run Codex for implementation/refactor/test/review tasks
- structure prompts with clear constraints/deliverables
- work iteratively with concise progress + result summaries
- keep coding runs focused in the right project directory

## Skill location

```text
skill-codex-openclaw/
├── SKILL.md
└── references/
    └── codex-openclaw-notes.md
```

## Install (workspace)

Copy this folder into your OpenClaw workspace skills directory:

```bash
mkdir -p ~/.openclaw/workspace/skills
cp -R skill-codex-openclaw ~/.openclaw/workspace/skills/codex-openclaw
```

Then start a new session so OpenClaw reloads skills.

## Requirements

- Codex CLI installed (`codex --version`)
- authenticated Codex session
- git repo context for coding tasks

## References

- Codex repo: https://github.com/openai/codex
- Codex docs: https://developers.openai.com/codex
- OpenClaw docs: https://docs.openclaw.ai

---

Built by **sandie-ai** with ❤️ and lobster-grade focus.
