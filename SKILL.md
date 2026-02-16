---
name: codex-coding
description: Use OpenAI Codex CLI to implement, refactor, test, and review code from the terminal. Trigger when the user asks to code with Codex, run Codex on a repo, automate coding tasks via Codex CLI, or orchestrate iterative coding sessions.
---

# Codex Coding Skill

Use this skill to run **Codex CLI** as the coding engine.

## Prerequisites

- `codex` installed and available in PATH.
- Run inside a trusted git repo whenever possible.
- For OpenClaw tool execution, run Codex with **PTY enabled**.

## Fast checks

```bash
codex --version
git rev-parse --is-inside-work-tree
```

If not in a repo:

```bash
mkdir -p /tmp/codex-scratch && cd /tmp/codex-scratch && git init
```

## Recommended execution patterns (OpenClaw)

### One-shot task

```bash
# with OpenClaw exec tool: pty=true, set workdir to project
# IMPORTANT: Use --sandbox workspace-write to allow file modifications
codex exec --sandbox workspace-write "Add input validation to the signup endpoint and update tests."
```

### Long task in background

```bash
# Use --sandbox workspace-write for write access
codex exec --sandbox workspace-write "Implement feature X with tests, then summarize changed files and remaining risks."
```

Use process monitoring to read logs and intervene only if needed.

## Working style

1. Define a precise task (scope + constraints + done criteria).
2. Ask Codex to implement and run tests/lint.
3. Review diff, rerun checks, iterate with focused follow-ups.
4. Summarize:
   - changed files
   - behavior impact
   - test results
   - known limitations

## Prompt template

Use this template when dispatching Codex:

```text
Context: <project + goal>
Constraints:
- Keep changes minimal and targeted
- Preserve existing style
- Update/add tests for modified behavior
- Run relevant checks before finishing
Deliverables:
- Summary of edits by file
- Commands run and results
- Remaining risks / TODOs
```

## Safety / quality guardrails

- Prefer small iterative changes over large rewrites.
- Require tests for logic changes.
- Do not claim success without command output.
- If Codex is blocked by missing env/secrets, stop and report exact requirement.

## References

- `references/codex-readme.md`
- Codex docs: https://developers.openai.com/codex
