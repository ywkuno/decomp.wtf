# [P0][ui] Scalable green-pixel map, multi-target drilldown and performance budgets

<!-- BACKLOG-ID: RE-06 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:ui`, `type:feature`  
**Dependencies (backlog IDs):** 03, 05

## Outcome
Keep the recognisable decomp.wtf visual progress map, make it honest for PC projects and performant for very large analyses.

## Scope
- Workspace/build/module/subsystem selection, colored evidence facets, confidence filters, unknown/blocked status, and proof drilldown.
- At overview zoom, render aggregated buckets/tiles or server-side summaries; fetch function detail on zoom/selection. Avoid DOM node per function at 750k candidates.
- Separate metric cards: analysed candidates, reconstructed units, behavioural verification and eligible byte-exact matches.
- Support stable deep links, accessible legend/colorblind differentiation, search by RVA/name, and quick navigation to relevant external local analysis IDs.
- Preserve original console map and real-time feed behind compatibility tests.
- Establish bounded SQL queries, pagination/cursors, indexed indexes, and UI latency/heap budgets.

## Acceptance
- [ ] Synthetic 1k, 100k and 750k candidate datasets tested without locking the browser or scanning all assembly/source per refresh.
- [ ] No false green from unverified evidence; legends and denominators are obvious.
- [ ] Tile -> candidate -> evidence drilldown works with multiple target builds.
- [ ] Keyboard search/filter and screenshots documented.
- [ ] Existing demo map regression test remains green.

## Pointers
`src/decompnet/app/static/app.js`, `src/decompnet/app/static/app.css`, `src/decompnet/app/server.py`, `src/decompnet/store.py`.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
