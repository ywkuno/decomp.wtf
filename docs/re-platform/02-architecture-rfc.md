# [P0][core] RFC: target/build/module identity and pluggable verification backends

<!-- BACKLOG-ID: RE-02 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:core`, `type:rfc`  
**Dependencies (backlog IDs):** 01

## Outcome
RFC first, then an additive implementation: separate target ingestion, analysis, task management and verification from the existing ROM/objdiff engine.

## Proposed model
`Workspace -> TargetBuild (SHA-256 + arch + provenance) -> Module (hash, name, image base, arch) -> FunctionCandidate (RVA, size, confidence, tool provenance) -> Evidence -> VerificationRun`.
Introduce `Subsystem/Contract` IDs for feature-level work; packet coverage is *not* native function coverage.

## Scope
- Define typed backend capabilities: `discover/import`, `read_analysis`, `claim_task`, `verify_candidate`, `progress`, optional `compile_exact`. Unsupported operations must be explicitly unavailable.
- Keep existing ROM and public-decomp/objdiff flows behind adapters or a compatibility facade, without gratuitous rewrite.
- Define stable identity across repeated analysis, code relocation/ASLR (RVA vs VA), changed binaries and multiple builds. Names alone are not IDs.
- Version metadata schema, migrations, rollback, compatibility and read-only import boundaries.
- Decide which data stays in SQLite and which large analysis artefacts are content-addressed local files.
- Document a minimal backend interface and an end-to-end sequence diagram before implementation.

## Acceptance
- [ ] RFC contains interface examples, capability matrix, migration plan, schema and explicit trade-offs.
- [ ] Repeat import is idempotent; different binaries/versions cannot overwrite each other's findings.
- [ ] Legacy `matched` status retains its original exact semantics.
- [ ] Synthetic adapter and existing engine work in the same installation.
- [ ] Backward-compatibility tests and migration/rollback tests exist.

## Pointers
`src/decompnet/project.py`, `src/decompnet/store.py`, `src/decompnet/network.py`, `src/decompnet/app/engine.py`, `src/decompnet/app/forkengine.py`.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
