# [P1][Neko265] IDA 9.4-scale inventory, packet-contract tracking and huge-index UX

<!-- BACKLOG-ID: RE-11 -->
**Priority:** [P1]  
**Labels to apply when GitHub Issues enabled:** `priority:P1`, `target:neko265`, `type:milestone`  
**Dependencies (backlog IDs):** 04, 05, 06, 08

## Outcome
Bring Neko265's established native RE workflow into the same workspace after Dauntless demonstrates the core.

## Scope
- Consume an IDA 9.4 export with explicit program/module hashes and tool revision, without cloning IDBs into this repo.
- Candidate inventories may run into hundreds of thousands; distinguish code/data/thunk/lib/runtime classifications and detect bogus/merged functions.
- Provide lazy query/indexing, module/subsystem partition, durable notes, address search and stable tiles at 100k–750k synthetic scale before real import.
- Track packet/protocol progress at **contract level**, not as a % of native functions; link contracts to relevant candidate functions, fixtures, and independently built server implementation where meaningful.
- Integrate with existing reverse-engineering outputs **via file exchange first**; optional live IDA MCP integration later.

## Acceptance
- [ ] Synthetic performance gates passed and measured.
- [ ] Import is repeatable, resumable and memory bounded; partial exports visibly marked.
- [ ] Function and packet/contract metrics never share a deceptive denominator.
- [ ] Example packet contract links to analysis candidates and a verification fixture.
- [ ] No games, packet payloads, IDBs or private implementation source copied into this public fork.

## Non-goal
Not a Neko game pipeline rewrite or a requirement to automate every candidate function.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
