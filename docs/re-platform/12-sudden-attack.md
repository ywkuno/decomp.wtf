# [P1][Sudden Attack] Version/dialect-safe protocol compatibility workspace

<!-- BACKLOG-ID: RE-12 -->
**Priority:** [P1]  
**Labels to apply when GitHub Issues enabled:** `priority:P1`, `target:sudden-attack`, `type:milestone`  
**Dependencies (backlog IDs):** 04, 05, 07

## Outcome
Support Sudden Attack preservation as a third adapter through evidence-backed protocol and compatibility progress.

## Scope
- Separate historical client/server build families explicitly: older SEA-era baseline and later Proud-family client builds must not be merged into one packet dialect.
- Link clean-room packet/wire contracts to source-derived or test-derived provenance and to synthetic deterministic fixtures.
- Track modern independently implemented compatibility modules separately from original client binaries.
- Show baseline uncertainty, observed-vs-inferred semantics, mismatched packet dialects and 'not tested live' status.
- Maintain strict separation of original archival material from this repo; no redistribution of proprietary source, database, binaries, logs or packet payloads.

## Acceptance
- [ ] Two synthetic dialect/build manifests coexist without data leakage or false matches.
- [ ] At least one isolated wire-format fixture links to its contract, test result and reviewed evidence.
- [ ] Compatibility progress cannot be labelled 'playable' without corresponding end-to-end tests.
- [ ] Fail-closed dialect mismatch test and reimport tests.
- [ ] No live public game connection; isolated/offline tests only.

## Priority
After Dauntless; may overlap with Neko if core infrastructure is stable.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
