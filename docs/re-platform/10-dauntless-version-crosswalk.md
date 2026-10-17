# [P1][Dauntless] Evidence-based cross-build function crosswalk: 2018 alpha vs 1.14.7

<!-- BACKLOG-ID: RE-10 -->
**Priority:** [P1]  
**Labels to apply when GitHub Issues enabled:** `priority:P1`, `target:dauntless`, `type:feature`  
**Dependencies (backlog IDs):** 03, 04, 09

## Outcome
Relate functions and subsystem contracts across the 2018 alpha and 1.14.7 without pretending addresses or signatures are stable.

## Scope
- Build/module hash scoped references; compare import graphs, caller/callee neighbourhood, CFG signatures, normalized constants/string hashes (privacy-aware) and reviewed semantic names.
- Show proposed matches with confidence tiers, provenance and reviewer decisions; maintain 1-to-many split/merge and unmatched cases.
- Partition common Unreal Engine/runtime code from game-specific changes to avoid false discoveries.
- Preserve distinct protocol/client lifecycle claims per build, with regression upon rescans.
- Read-only visualization of added/removed/changed candidate clusters; never auto-port functions or copy proprietary code between builds.

## Acceptance
- [ ] Synthetic two-build fixture demonstrates exact, likely, ambiguous, split, and unmatched outcomes.
- [ ] No cross-build identity accepted on address or name alone.
- [ ] Human override is reversible and audited; no bulk silent matching.
- [ ] Dauntless sample pilot generates useful version-delta report with caveats.
- [ ] No binary or proprietary asset committed.

## Depends
Pilot #09 must establish valid first-build data before real crosswalk work.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
