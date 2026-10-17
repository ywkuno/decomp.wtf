# [P0][Dauntless] First Windows PE pilot: one pinned module and a narrow gameplay/network subsystem

<!-- BACKLOG-ID: RE-09 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `target:dauntless`, `type:milestone`  
**Dependencies (backlog IDs):** 01, 03, 04, 05, 06, 07

## Outcome
Prove this fork is useful on Dauntless **before** investing in broad automatic PC reconstruction. Highest-priority game adapter.

## Context/boundaries
The user has a **pre-Epic 2018 alpha** and a **1.14.7 target**. These are separate builds; do not equate their protocols, module layouts, or game behaviours. No installation or executable is stored in this repository.

## Pilot procedure
1. Local operator selects one legally held installation and one *specific* PE executable/DLL after documenting actual hashes, architecture and relevant module names (do not assume filenames).
2. Read-only export of a bounded 200–500 function subset via IDA/Ghidra; favour a tractable subsystem with a clear behavioural fixture/contract over sweeping UE4 engine coverage.
3. Label engine/runtime/library code separately from game-specific code; note detection confidence and false positives.
4. Visualise identified, analysed, reconstructed, and evidence-backed verified units; click through to proof and notes.
5. Run one bounded agent loop: claim -> analyse -> propose -> review -> verify -> render. No write-back to game binaries.
6. Produce pilot findings, cost/runtime, function discovery quality, false-positive rate and go/no-go decision.

## Acceptance
- [ ] Locally reproducible demo with hashes recorded outside the public repo and redacted example screenshots.
- [ ] 200–500 candidate import with correct build/RVA identity, repeat-import deduplication and no unknowns silently excluded.
- [ ] At least one synthetic or independently authorized local contract verified with linked evidence.
- [ ] No client modification, bypass of auth/anti-cheat, proprietary uploads or unintended online contact.
- [ ] Pass/fail table for pilot gates, clearly identifying what is *not* 1:1 matched.

## Note
This pilot should drive the adapter APIs; **StoneHuff is not the first pilot**.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
