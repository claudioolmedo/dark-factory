# FACTORY.md — how this factory works and how to stand up your own

## What it is
A reusable software factory made of five Band Desktop seats with generic, process-only mandates. You bring a specification; the factory brings the process: ledger → plan → plan attack → sealed acceptance plan → build → clean-copy verification → evidence close-out. One human dispatch starts a run; the seats hand off to each other by @mention in a single room, which doubles as the run's audit trail.

## Seats and mandates
Create five seats (names and harnesses as in the README table, or your equivalents) and paste each file from `mandates/` into the matching seat's Instructions, appended after any built-in instructions:

- `mandates/delivery-manager.md` — coordination, the living ledger, evidence discipline
- `mandates/plan-author.md` — plan + acceptance plan authorship
- `mandates/plan-reviewer.md` — adversarial plan review; seals the acceptance plan with SHA-256 before code
- `mandates/code-author.md` — implementation to spec, tests, handoff hygiene
- `mandates/code-reviewer.md` — independent verification from a clean copy; never edits what it reviews

The mandates are deliberately generic — they describe how to work, never what to build. The specification travels in the dispatch message, not in the mandates.

## Running a task
1. Create a room with all five seats.
2. Send one dispatch @mentioning the Delivery Manager, containing: the full specification, the absolute path of the result repository the seats should work in, the definition of done, and the numbered process steps (ledger → plan → attack/seal → build → verify → close).
3. Do not steer mid-run. The seats ask each other; blockers and rejections are handled inside the room and recorded against the ledger.
4. Read the Delivery Manager's close-out: per-requirement evidence, elapsed time, and cost.

## Design choices worth copying
- **Sealed acceptance plan:** the reviewer fixes how success will be checked — and its hash — before any code exists, so the goalposts cannot move.
- **Reviewer never edits:** verification is independent; fixes route back to the author.
- **Living ledger in the room:** one shared plan, updated in the open with @mentions — never a private copy per agent.
- **Clean-copy verification:** the reviewer works from a fresh copy, and exercises the result end to end, not only part by part.

## Provenance
Stood up on Nov 24, 2026 during the BAND Dark Factory Buildathon (Dossier track) and HackwithBay 4.0, San Francisco.
