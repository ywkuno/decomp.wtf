# [P0][quality] CI fixture matrix, migration regression, local data safety and release gates

<!-- BACKLOG-ID: RE-15 -->
**Priority:** [P0]  
**Labels to apply when GitHub Issues enabled:** `priority:P0`, `area:quality`, `type:task`  
**Dependencies (backlog IDs):** 01, 02

## Outcome
Make PC adapter work safe to review and maintain without breaking upstream exact-matching use cases.

## Scope
- Python 3.12+ test matrix and documented Windows/WSL optional runner; use synthetic PE x86/x64 fixtures and a tiny dual-version metadata dataset.
- Golden tests for original demo import, ROM matching, public-decomp/objdiff flow where dependencies available, claims, UI API, migrations and security restrictions.
- Explicit negative tests: malformed PE, stale evidence, wrong build hash, import dedupe, deny network, deny unapproved agent writes, injection in imported symbol/notes.
- Document licensing/reuse attribution and what data must be gitignored; audit collaboration defaults and protect against accidental remote sharing.
- Small PRs only, no main merges by agents, tests in acceptance checks, no actual Windows game binaries in CI.

## Acceptance
- [ ] Reproducible `uv run pytest` baseline with new test paths and exact skip reasons.
- [ ] Changed schema can migrate/back up safely; old ROM projects are not corrupted.
- [ ] Redaction and data-boundary tests are exercised.
- [ ] GitHub PR checklist flags scope creep, resource ceilings and proof requirements.
- [ ] Exit criteria for Dauntless pilot are documented as an actionable go/no-go rubric.

---
*Import note: this file is an issue-ready draft, not an actual GitHub issue. Link to the roadmap at `docs/re-platform/README.md`; retain this BACKLOG-ID marker to deduplicate issue imports.*
