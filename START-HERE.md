# Zipline FDE Hackathon Kit

Everything from our prep, in one place.

## What's in here

- **jurisdiction-prescreen/** — the Codex operating-system scaffold (the spine).
  - `AGENTS.md` — the operating contract Codex auto-loads.
  - `.codex/config.toml` — model + subagent defaults (repo-scoped, layers on top
    of the laptop's global config).
  - `.codex/agents/` — five subagents: fetcher, extractor, analyst, drafter, and
    a read-only verifier.
  - `docs/code_review.md` — verifier rubric, also used by `/review`.
  - `docs/PLANS.md` — Plan-mode template.
  - `.agents/skills/jurisdiction-brief/SKILL.md` — the repeatable workflow.
  - `schema/claim.schema.json` — enforces the cite-or-flag rule.
  - `README.md` — demo runbook + a day-one kickoff prompt to paste into Codex.

- **bootstrap.sh** — recreates the entire scaffold on any machine with a shell.
  Paste it into the hackathon laptop's terminal, or `bash bootstrap.sh`. No
  GitHub/USB required. Carries no Zipline data.

- **first-hour-playbook.md** — six hard-boxed phases for converting the day-of
  prompt into a scoped build, plus pressure-decision rules and red flags.

## On the day (10-minute cold start)

1. Get the scaffold onto the laptop (paste `bootstrap.sh`, or clone your repo).
2. `cd jurisdiction-prescreen`, open Codex, run `/status` — check model,
   reasoning effort, and which MCP connectors are already wired.
3. Confirm network access is ON (the fetcher stage needs it).
4. Point `AGENTS.md` at the actual assignment; use `/plan` to scope before building.
5. Follow first-hour-playbook.md from there.

## Reminder

If you pasted a GitHub token anywhere, revoke it (GitHub → Settings → Developer
settings → Personal access tokens) and make a fresh one when needed.
