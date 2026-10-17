# [P0][verification] Provenance ledger and truthful recovery metrics

<!-- BACKLOG-ID: RE-05 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:verification`, `type:feature`  
**Dependencies (backlog IDs):** 02, 03

## Outcome
Replace the misleading idea that Windows RE progress can always be measured by the upstream zero-score binary match.

## Evidence model
Track independently: `discovered`, `analysed`, `reconstructed`, `behaviour_verified`, `byte_exact`, `uncertain/blocked`. These are **facets**, not one exclusive enum: a candidate may be analysed and reconstructed but later lose verification after its oracle changes. Record confidence, reviewer/tool, immutable input hash, method, fixture version, check results and expiry/staleness.

## Metrics
- Per-build counts and denominator declarations (eligible candidates, confirmed functions, total candidates, unknowns, library-engine exclusions).
- Exact-match % only for actually byte-checked eligible functions; behavioural % only for features/contracts with declared tests. Never add these percentages.
- Proof drill-down from each colored tile; reject LLM-only claims of verification.
- Invalidate stale evidence if target hash, analysis identity, test/oracle or implementation changes.
- Track rename/split/merge history without losing provenance.

## Acceptance
- [ ] Explicit metric contract and SQL/API schema with forward/backward migration tests.
- [ ] Counterexample tests prevent “analysed = byte exact” and duplicate counting.
- [ ] Reimport and changed evidence inputs cause correct recomputation/invalidation.
- [ ] UI/API expose unknown denominator and reasons for blocked/uncertain status.
- [ ] Existing console exact matches remain exact and are not reinterpreted.

## Pointers
`src/decompnet/store.py`, `src/decompnet/scoring.py`, `src/decompnet/app/engine.py`, `src/decompnet/app/static/app.js`.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
