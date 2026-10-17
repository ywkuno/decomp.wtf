# [P0][import] PE/COFF x86-x64 module inventory and deterministic metadata import

<!-- BACKLOG-ID: RE-03 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:import`, `type:feature`  
**Dependencies (backlog IDs):** 02

## Outcome
Support local Windows PE/COFF x86 and x64 executables/DLLs as read-only target inventories; do not promise 1:1 matching.

## Scope
- Parse basic PE architecture, machine type, sections, entry point, image base, RVA, size, timestamp, module hash and optional symbol metadata; distinguish file offsets, RVA and loaded VA.
- Import *functions as evidence-backed candidates* from a versioned sidecar exporter; don't equate linear disassembly with confirmed function boundaries.
- Handle thunks, overlapping/duplicate candidates, stripped symbols, imports, vtables, compiler libraries and overlay/module boundaries with explicit provenance/flags.
- Keep payloads local and ignored: database may store hashes, source tool and metadata but not upload proprietary raw bytes.
- Validate malformed/oversized imports, path traversal, address overflow, architecture mismatch and duplicate hashes.
- Design for lazy or streaming import rather than loading huge binaries into API responses.

## Acceptance
- [ ] Synthetic x86/x64 PE fixtures import deterministically and reimport without duplicating functions.
- [ ] Address conversion tests cover ASLR/image base differences and section boundaries.
- [ ] Corrupt metadata and mixed-build imports fail closed with clear errors.
- [ ] Import reports accepted/rejected/uncertain candidate counts; no “decompiled %” implied.
- [ ] No binary patching, live process attachment, forced network access or proprietary fixtures.

## Pointers
`src/decompnet/store.py`, `src/decompnet/app/server.py`, `src/decompnet/elfobj.py`, `src/decompnet/rom/detect.py`; new isolated PE module recommended.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
