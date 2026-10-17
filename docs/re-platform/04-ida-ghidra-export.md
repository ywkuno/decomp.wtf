# [P0][import] Versioned read-only IDA 9.4 / Ghidra analysis exchange

<!-- BACKLOG-ID: RE-04 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:import`, `type:feature`  
**Dependencies (backlog IDs):** 02, 03

## Outcome
Allow existing reverse-engineering work to drive the dashboard rather than recalculate it from scratch.

## Scope
- Define schema `re-analysis/v1`: build/module hashes, tool/version, timestamp, RVA+size, function flags, names/demangled names, boundary confidence, calls/callers, imports, source references, subsystem tags and optional evidence locators.
- Provide an IDA 9.4 headless-friendly exporter and compatible Ghidra exporter with equivalent minimal fields. Review existing `src/decompnet/forks/ghidra.py` and `ghidra_scripts/DecompWtfExport.java` before reinventing them; note those currently serve public-decomp drafts.
- Export **metadata only by default**: no pseudocode, assembly, raw data, string payloads or proprietary source; optional privileged local-only detailed view may be proposed separately.
- Stream/chunk JSONL + manifest; incremental hash-based rescan and import resume; collision handling.
- Keep human overrides and the original exporter provenance when tools disagree.

## Acceptance
- [ ] IDA and Ghidra export/import the same synthetic fixture without schema ambiguity.
- [ ] Unknown fields are handled by version policy; bad records are quarantined with diagnostics.
- [ ] Repeated imports are idempotent and changed analyses preserve history.
- [ ] Import can be run offline, headlessly, without modifying the original IDB/Ghidra project.
- [ ] User review can mark false-positive function candidates; no silent promotion to “verified”.

## Pointers
`src/decompnet/forks/ghidra.py`, `src/decompnet/forks/ghidra_scripts/DecompWtfExport.java`, `src/decompnet/store.py`.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
