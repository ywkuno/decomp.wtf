# Dauntless-first RE platform — detailed report & issue backlog

> **Planning only.** This is a portable issue pack because GitHub currently returns **HTTP 410: Issues has been disabled in this repository**. None of the files below represents an actual GitHub issue. Enable **Settings → General → Features → Issues** to publish them as issues. Until then, this draft PR is the agent handoff. Do not merge automatically.

## Executive decision
Extend the decomp.wtf fork as a **local-first, multi-build RE evidence and agent dashboard**, **not** as a universal 1:1 PC decompiler. Preserve the upstream green-pixel map, function claims, notes, MCP agents and exact-match path. Add **Windows PE x86/x64 and metadata-only IDA 9.4/Ghidra exchange**, an evidence/proof ledger, behavioural contract verification, and scalable indexing for very large candidate sets. Agents propose work; independent or human-approved oracles verify it.

**Revised priorities (user preference):** **P0 Dauntless** first; **P1 Neko265** second; **P1 Sudden Attack Preservation** third; **P3 StoneHuff deferred**. Optional Project Trinity integration is **P2, after pilot**.

## Why not run the original matching workflow unchanged?
The upstream 0.10.6 source focuses on period compiler/toolchain byte matching and objdiff when building a compatible source-fork. Windows games may lack the exact compiler, flags, object layout or source trees. Reconstructed behaviour and 1:1 binary identity are different measurable outcomes. Never turn a tile 'byte-exact green' because an agent says its pseudocode looks correct.

## Proposed architecture

```text
Local game installations (ignored, never uploaded)
       │
IDA 9.4 / Ghidra metadata exports ── PE module inventory
       │                                 │
       └──────── versioned analysis manifest
                          │
                  Backend/Target registry
                          │
          Workspace → Build → Module → Candidate
                          ├─ call graph / names / confidence
                          ├─ feature / packet contract
                          ├─ evidence & proof ledger
                          └─ bounded agent task claims
                          │
               API / MCP / visual progress map
                          │
           Verification adapters (byte / fixture / trace)
```

**Likely source seams:** `src/decompnet/store.py` (SQLite), `src/decompnet/app/engine.py` (ROM), `src/decompnet/app/forkengine.py` (objdiff/source fork), `src/decompnet/forks/ghidra.py` (existing draft tooling), `src/decompnet/app/tools.py` and `agents.py` (MCP/agents), `src/decompnet/app/server.py` and `static/app.js` (API/map). Paths are review targets, not permission to refactor everything.

## Metric semantics and denominators
Treat **discovered**, **analysed**, **reconstructed**, **behaviour verified**, **byte exact**, and **uncertain** as provenance-backed facets, not a falsely linear 0–100% ladder. Count native function candidates only against a declared build/module/candidate denominator. Track protocol/feature contract coverage separately. Byte-exact matches count only when truly verified against pinned target bytes under a suitable comparator. Track unknown confidence and misidentified candidates explicitly. Stale oracle or build hash must invalidate previous proof.

## Ordered delivery & go/no-go gates

| Phase | Issues | Go/no-go evidence |
|---|---|---|
| 0. Safety & baseline | 01, 15 | Upstream tests and demos recorded; no unexpected uploads; old DB safe |
| 1. Core design | 02, 05 | RFC approved, identity/version schema and proof semantics locked |
| 2. Imports | 03, 04 | Synthetic x86/x64 + IDA/Ghidra metadata roundtrip |
| 3. UI & agents | 06, 07, 08 | Honest drill-down map; bounded tasks; deterministic proof |
| 4. **Dauntless pilot** | 09 | 200–500 local functions imported with evidence, no client modification |
| 5. Dauntless versions | 10 | 2018 alpha and 1.14.7 treated as distinct baselines |
| 6. Other adapters | 11, 12 | Neko synthetic scale gate; Sudden Attack dialect segregation |
| Later | 14, 13 | Trinity optional; StoneHuff remains deferred |

### Non-goals for v1
No promise of fully automatic Windows 1:1 reconstruction; no authentication/anti-cheat bypass; no game launcher/server implementation; no live production service probing; no auto-push to third-party decomp communities; no rewritten IDA/Ghidra; no unreviewed merge into `main`.

### Privacy and governance
The fork is **public**; this issue pack deliberately excludes private source excerpts, captures, hashes, authentication data, IDBs, binary names that are not verified, and proprietary game code. All local project references must be intentionally outside Git tracking. Respect rights/licences and upstream's AI contribution cautions. Keep original gameplay assets local. Task agents work from branches and submit PRs only.

## Label taxonomy (to create once GitHub Issues are enabled)
`priority:P0`, `priority:P1`, `priority:P2`, `priority:P3`; `area:foundation`, `area:core`, `area:import`, `area:ui`, `area:verification`, `area:agents`, `area:quality`; `target:dauntless`, `target:neko265`, `target:sudden-attack`, `target:stonehuff`; `type:task`, `type:feature`, `type:rfc`, `type:milestone`; `status:deferred`, `status:blocked`.

**Recommended import steps:** 1) enable Issues; 2) create these labels in repository settings (or via `gh label create`); 3) publish each issue pack file with its exact title, body, and listed labels using `gh issue create -R ywkuno/decomp.wtf --title ... --body-file ... --label ...`; 4) replace dependency IDs with returned GitHub issue links; 5) paste this roadmap into an umbrella epic issue. Avoid duplicates: search the repo for each title before creating.

## Issue pack
- **01** [[P0][foundation] Baseline and audit upstream 0.10.6 before PC extensions](01-baseline-audit.md) — depends on None
- **02** [[P0][core] RFC: target/build/module identity and pluggable verification backends](02-architecture-rfc.md) — depends on 01
- **03** [[P0][import] PE/COFF x86-x64 module inventory and deterministic metadata import](03-pe-coff-import.md) — depends on 02
- **04** [[P0][import] Versioned read-only IDA 9.4 / Ghidra analysis exchange](04-ida-ghidra-export.md) — depends on 02, 03
- **05** [[P0][verification] Provenance ledger and truthful recovery metrics](05-evidence-and-metrics.md) — depends on 02, 03
- **06** [[P0][ui] Scalable green-pixel map, multi-target drilldown and performance budgets](06-progress-map-scale.md) — depends on 03, 05
- **07** [[P0][verification] Pluggable deterministic behavioural oracles alongside exact match](07-behaviour-oracles.md) — depends on 02, 05
- **08** [[P0][agents] Bounded MCP analysis jobs, leases, approval gates and evidence-only writes](08-bounded-agent-tasks.md) — depends on 02, 05, 07
- **09** [[P0][Dauntless] First Windows PE pilot: one pinned module and a narrow gameplay/network subsystem](09-dauntless-first-pilot.md) — depends on 01, 03, 04, 05, 06, 07
- **10** [[P1][Dauntless] Evidence-based cross-build function crosswalk: 2018 alpha vs 1.14.7](10-dauntless-version-crosswalk.md) — depends on 03, 04, 09
- **11** [[P1][Neko265] IDA 9.4-scale inventory, packet-contract tracking and huge-index UX](11-neko-scale.md) — depends on 04, 05, 06, 08
- **12** [[P1][Sudden Attack] Version/dialect-safe protocol compatibility workspace](12-sudden-attack.md) — depends on 04, 05, 07
- **13** [[P3][StoneHuff] Deferred native/Lua/Rust evidence adapter — design notes only](13-stonehuff-deferred.md) — depends on 02, 05, 07
- **14** [[P2][agents] Optional Project Trinity orchestration integration after standalone MCP is proven](14-trinity-integration-deferred.md) — depends on 08, 09
- **15** [[P0][quality] CI fixture matrix, migration regression, local data safety and release gates](15-ci-safety.md) — depends on 01, 02

## First assignment for the agent
**Start with 01 + 02 as two small, reviewable deliverables**: reproducible baseline/audit and an architecture RFC. Do not start Dauntless ingest until build/module identity, legal data boundaries and verification semantics are agreed. Pilot owner may begin planning 09 in parallel.

## Sources (code review anchors)
[decomp.wtf fork README](../../README.md) · [core storage](../../src/decompnet/store.py) · [ROM engine](../../src/decompnet/app/engine.py) · [source fork engine](../../src/decompnet/app/forkengine.py) · [Ghidra export code](../../src/decompnet/forks/ghidra.py) · [tests](../../tests)
