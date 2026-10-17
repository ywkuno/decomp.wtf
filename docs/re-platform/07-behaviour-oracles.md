# [P0][verification] Pluggable deterministic behavioural oracles alongside exact match

<!-- BACKLOG-ID: RE-07 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:verification`, `type:feature`  
**Dependencies (backlog IDs):** 02, 05

## Outcome
Verify independently reimplemented behaviour without pretending to reproduce original compiler output.

## Scope
- Define `VerificationProvider` with `exact_binary`, `unit_fixture`, `wire_contract`, `trace_replay`, `human_review` proof types and declared trust levels.
- Consume reproducible local fixtures with input hash, expected output hash, comparator/tolerance and hermetic runner; retain stdout/stderr/redacted results.
- Capture mismatches and regressions at contract/module scope; never mark entire project verified from a small passing sample.
- Separate trusted evidence from AI explanations; include negative fixtures to demonstrate false claims are caught.
- No live production endpoints or instructions to bypass third-party services. Limit test runners by CPU/time/memory/filesystem/network capabilities.

## Acceptance
- [ ] Deterministic synthetic oracle round-trip and negative/regression tests.
- [ ] Changed fixture or implementation invalidates old proof and visibly changes the dashboard.
- [ ] Byte-exact still requires byte-level comparator (when supported).
- [ ] Local-only storage and redaction policy documented.
- [ ] Failure/retry and non-deterministic traces are marked appropriately, not green.

## Pointers
`src/decompnet/scoring.py`, `src/decompnet/app/forkengine.py`, `src/decompnet/store.py`, `tests/test_fork_judge.py`.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
