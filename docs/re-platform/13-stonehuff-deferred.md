# [P3][StoneHuff] Deferred native/Lua/Rust evidence adapter — design notes only

<!-- BACKLOG-ID: RE-13 -->
**Priority:** [P3]  
**Labels to apply when GitHub Issues enabled:** `priority:P3`, `target:stonehuff`, `status:deferred`  
**Dependencies (backlog IDs):** 02, 05, 07

## Status
**DEFERRED BY USER. Not a pilot. Not on the critical path.** Do not assign implementation work until prioritisation changes.

## Long-term fit
A future adapter could connect recovered native symbols, Lua components and independent Rust runtime contracts, recording behavioural parity and performance regression evidence separately from exact native bytes.

## Parked design questions
- How should the UI represent links between native functions, script components and rewritten runtime modules?
- Which benchmark/trace fixtures would prove a behaviour or stability improvement?
- How to prevent accidental proprietary asset/source export?

## Acceptance for now
- [ ] Maintain this issue as a parking-lot design note.
- [ ] No StoneHuff-specific code, importer, binaries, or tests added under this ticket.
- [ ] Revisit only after the Dauntless pilot and explicit reprioritisation.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
