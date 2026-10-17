# [P0][agents] Bounded MCP analysis jobs, leases, approval gates and evidence-only writes

<!-- BACKLOG-ID: RE-08 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:agents`, `type:feature`  
**Dependencies (backlog IDs):** 02, 05, 07

## Outcome
Let Claude/Codex/DeepSeek-class agents perform narrow, reviewable RE analysis tasks without arbitrary mutation.

## Scope
- Typed jobs: `classify_candidate`, `annotate_function`, `map_call_graph`, `compare_versions`, `propose_contract`, `review_evidence`; no default executable patching or commit.
- Claims with TTL, renewal, heartbeat, reclaim-on-crash, dedupe, retry ceiling, token/cost budget and task provenance.
- Agent writes are **proposals**; privileged promotion of evidence, edited local implementation files, network use and commits need explicit operator approval.
- Validate all external analysis text as untrusted input; prevent prompt injection from strings/symbols/comments becoming tool instructions.
- Reuse local existing MCP and agent runtime; an optional Project Trinity adapter must be separate, permission-minimal, and not on the critical path.
- Do not send proprietary excerpts to remote models by default; opt-in previews with understandable data-classification gate.

## Acceptance
- [ ] Concurrent agents do not claim the same unit; lease recovery and resumability tested.
- [ ] Simulated hostile symbols/instructions cannot escalate privileges.
- [ ] Unapproved tasks cannot edit code, invoke shell/network, or assert verified status.
- [ ] Every proposal is attributable to model, context, target hash and evidence revision.
- [ ] Existing `claim_function`/ROM flows still work.

## Pointers
`src/decompnet/app/tools.py`, `src/decompnet/app/agents.py`, `src/decompnet/network.py`, `src/decompnet/app/bridge.py`.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
