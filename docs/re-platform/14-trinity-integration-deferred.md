# [P2][agents] Optional Project Trinity orchestration integration after standalone MCP is proven

<!-- BACKLOG-ID: RE-14 -->
**Priority:** [P2]  
**Labels to apply when GitHub Issues enabled:** `priority:P2`, `area:agents`, `status:deferred`  
**Dependencies (backlog IDs):** 08, 09

## Outcome
Reuse external agent orchestration when valuable, **without making it a mandatory dependency or bypassing approval boundaries**.

## Scope (not for pilot)
- Define versioned API/MCP interface between dashboard task/evidence records and external runner job IDs.
- Preserve job provenance, lease ownership, crash recovery, receipts, per-task budgets and human approval gates.
- Avoid sharing game bytes/pseudocode to remote agents by default; classify every tool argument and response.
- Keep agents' filesystem permissions narrower than original project repositories; no unreviewed commits or issue updates.

## Acceptance
- [ ] Standalone decomp.wtf workflow continues to work without Trinity.
- [ ] Optional adapter passes reconnect/resume, duplicate-receipt, permission-denial and failure-injection tests.
- [ ] All privilege changes and remote data paths are explicitly visible and approved.

## Priority
P2 **after** Dauntless proof of concept; no early coupling.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
