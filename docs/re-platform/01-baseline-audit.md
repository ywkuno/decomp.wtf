# [P0][foundation] Baseline and audit upstream 0.10.6 before PC extensions

<!-- BACKLOG-ID: RE-01 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:foundation`, `type:task`  
**Dependencies (backlog IDs):** None

## Outcome
Establish a reproducible, risk-aware starting point for this fork. **Audit first; do not rewrite the product or merge into main.**

## Scope
- Pin fork HEAD/upstream version and document upstream licence and any bundled third-party licences.
- Run `uv sync --group dev`, `uv run pytest`, the bundled demo, and CLI/MCP smoke tests on a supported environment. Capture actual pass/fail/skip counts and OS/toolchain constraints; don't claim tests passed without running them.
- Audit Windows/WSL install scripts, update paths, subprocess/toolchain execution, local data directory, database schema/migrations, auth/cookies, potential telemetry/remote connectivity and collab-room behaviour.
- Document safe development command, local-only test fixture, rollback/recovery, and whether an existing install would be migrated.
- Identify whether current UI/store APIs rely on `status = matched` and exactly which tests guard that assumption.

## Pointers
`pyproject.toml`, `src/decompnet/app/engine.py`, `src/decompnet/store.py`, `src/decompnet/app/server.py`, `src/decompnet/app/updates.py`, `src/decompnet/wsl.py`, `tests/`.

## Acceptance
- [ ] A short audit with reproducible commands, environment, test counts, and honest limitations.
- [ ] Upstream ROM/demo workflows still work; failures tracked rather than hidden.
- [ ] Written risk register for Windows/WSL, SQLite migration, network defaults, and file access.
- [ ] Explicitly identifies reusable code versus console/objdiff-only assumptions.
- [ ] No proprietary binary or game artefact committed.

## Hand-off
Small documentation/audit PR; do not bundle new platform code. Stop and report if local tests are not runnable.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
