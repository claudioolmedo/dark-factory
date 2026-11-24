# Dark Factory — a generic agent factory in Band Desktop

A five-seat team of coding agents in [Band Desktop](https://band.ai) that builds software from a written specification, autonomously: one human dispatch per task, then the seats plan, attack the plan, seal an acceptance plan, build, and verify — talking to each other directly in one room.

Built at HackwithBay 4.0 / BAND Dark Factory Buildathon kickoff (Nov 24, 2026). Currently being run against the buildathon's Dossier track; the factory itself is track-agnostic.

## The team

| Seat | Harness | Job |
|---|---|---|
| Delivery Manager | Codex | Owns the run: requirement ledger, sequencing, evidence, close-out |
| Plan Author | Claude Code | Writes the implementation plan and the acceptance plan |
| Plan Reviewer | Codex | Attacks the plan before any code exists; seals the acceptance plan (SHA-256) |
| Code Author | Claude Code | Builds to the spec and the sealed plan |
| Code Reviewer | Codex | Verifies from a clean copy; never edits what it reviews |

## The process

1. **Ledger** — the Delivery Manager breaks the spec into numbered requirements, one owner each.
2. **Plan** — the Plan Author writes the plan and the acceptance plan.
3. **Attack & seal** — the Plan Reviewer challenges the plan; the acceptance plan is sealed with its SHA-256 in the room before code exists.
4. **Build** — the Code Author implements, handing off by @mention.
5. **Verify** — the Code Reviewer checks from a clean copy, end to end.
6. **Close** — the Delivery Manager reports outcome, elapsed time, and cost against the ledger.

The communication graph lives in the seats' instructions (see `mandates/`): each mandate names exactly who to @mention when a step is done or blocked, and any seat can tag any other directly — no orchestrator relay.

## Reuse it

The mandates in `mandates/` are process-only and generic: they name no product, endpoint, or field. Copy them into your own Band seats, then dispatch your own specification in the room. See `FACTORY.md` for the full setup.

## Status

Work in progress — factory stood up and configured Nov 24, 2026; first full autonomous runs in progress.
