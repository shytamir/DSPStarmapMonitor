# Project steering

This is the sole record of project state, steering, decisions, and acceptance.
The [roadmap](management/ROADMAP.md) defines the workload and its gates; the
[concept](CONCEPT.md) describes the intended experience. Neither tracks progress.

## Current position

**Phase:** Concept preparation. **Active implementation:** None.

Repository setup and initial source familiarization are complete. The authorized
scope is documentation and read-only research; no mod code, build project, CI,
installation, game execution, or release work is included. No runtime feasibility
or owner acceptance has been established.

**Next proposed work:** SM-1.1 and SM-1.2, to resolve the product choices below
and establish a viable native integration and storage route. They are not active.
The owner may authorize them together or revise the concept first.

**Release state:** No build or release exists.

## Steering decisions

| ID | Direction |
| --- | --- |
| D01 | Extend the existing planet Memo tab with a limited product selection and an interval owned by that memo. |
| D02 | Offer products based on the memo planet's statistics for that interval. Use the native Production tab as the reference for displayed quantities and units. |
| D03 | Add a separate checkbox for updating product annotations beside the planet name. Preserve the native memo reminder control and the actual planet name. |
| D04 | Reuse native UI, statistics, identity, and save storage. Preserve user memo content and formatting. A safe storage route is a feasibility requirement, not an assumed capability. |
| D05 | Keep the first delivery focused on planetary production monitoring. Star/galaxy aggregation, consumption or net-rate views, alerts, graphs, factory control, and multiplayer integration are outside its scope. |
| D06 | Use BepInEx 5.4.17 as the dependency baseline. The dependency checkout is a read-only reference and must remain at its v5.4.17 tag. Framework target and exact hooks belong to subsequent feasibility work. |
| D07 | Keep management in README, PROJECT, and ROADMAP, with CONCEPT for product intent and AGENTS for working rules. PROJECT alone records all work state. |
| D08 | Defer CI, distribution, and publication planning. Keep local investigation material outside tracked product documentation. |

## Decisions to resolve before implementation

These are proposals for the first feasibility phase, not settled settings.
Resolve them together at G1 rather than allowing implementation to choose
implicitly.

| ID | Question and starting proposal | Resolution point |
| --- | --- | --- |
| Q01 | How many product slots and what happens at capacity? Start with three slots, explicit replacement or clearing, and no automatic eviction. | SM-1.1 / G1 |
| Q02 | Exactly which products qualify? Interpret local as the memo's planet, wherever Icarus is. Start with positive recorded production during the interval, excluding consumption-only or traffic-only entries. Check this against the intended native filtering experience. | SM-1.1 / G1 |
| Q03 | Which intervals and initial selection? Start with the native timed intervals and a 1-minute default. The native All time option displays totals, so omit it from a rate-only first delivery unless a clearly labelled total mode is desired. | SM-1.1 / G1 |
| Q04 | What happens when a selection becomes inactive or unavailable? Retain the selected product, show zero only when measured, and distinguish unavailable data. Newly offered candidates still follow the chosen interval. | SM-1.1 / G1 |
| Q05 | What does an active label do? Start with automatic value updates while visible, an identifying tooltip, and no extra click action. Start the display checkbox off; disabling it preserves selections. | SM-1.1 / G1 |
| Q06 | Can native storage preserve selections, interval, and visibility without damaging memo editing or save compatibility? Choose a viable route from source evidence, then prove its behaviour in the Memo prototype. If none meets the contract, return a scope decision instead of silently adding another store. | SM-1.2 / G1; demonstrated at G2 |

## Work state

Updated 2026-11-06. IDs refer to the [current roadmap](management/ROADMAP.md).
Use `Planned`, `Active`, `Blocked`, or `Complete` for work; record gate outcomes
and owner acceptance explicitly. Technical completion alone does not pass an
owner gate. Keep evidence summaries short and implementation detail elsewhere.

| Epic | State |
| --- | --- |
| SM-0 — Foundation | Complete |
| SM-1 — Feasibility and product choices | Planned |
| SM-2 — Memo monitoring | Planned |
| SM-3 — Live starmap annotations | Planned |
| SM-4 — Candidate validation | Planned |

| Story | State | Evidence or dependency |
| --- | --- | --- |
| SM-0.1 | Complete | Documents and local-artifact exclusions prepared; 14 relative links, 11 story mappings, and 3 gate records checked. License unchanged; whitespace and scope checks passed. |
| SM-0.2 | Complete | Existing mod patterns reviewed; selected current game types and tagged BepInEx source inspected read-only. |
| SM-1.1 | Planned | Resolve Q01–Q05. |
| SM-1.2 | Planned | Establish the native route and resolve Q06's design choice. |
| SM-2.1 | Planned | Depends on G1. |
| SM-2.2 | Planned | Depends on SM-2.1 and G1's statistics contract. |
| SM-2.3 | Planned | Depends on SM-2.1 and G1's storage choice. |
| SM-3.1 | Planned | Depends on G2. |
| SM-3.2 | Planned | Depends on SM-3.1. |
| SM-4.1 | Planned | Depends on SM-3.2. |
| SM-4.2 | Planned | Depends on SM-4.1. |

| Milestone / gate | State | Basis |
| --- | --- | --- |
| M0 — Foundation available | Reached | SM-0.1 and SM-0.2 complete. |
| M1 / G1 — Feasible design | Not assessed | Product choices and native storage route remain open. |
| M2 / G2 — Memo prototype demonstrated | Not assessed | Requires implementation and focused in-game evidence. |
| M3 — Integrated candidate prepared | Not reached | Requires SM-3 and SM-4.1. |
| M4 / G3 — First delivery accepted | Not assessed | Requires owner review of an identified candidate. |

## Evidence limits and risks

Initial static research used game build 0.10.35.29151 and BepInEx source tag
v5.4.17. These are inspection inputs, not a compatibility claim. The game
contains native Memo persistence, planetary production history, and starmap
label/reminder surfaces. Their suitability for this extension still needs the
SM-1 feasibility work and the later prototype gates.

The main uncertainty is storing the extra per-memo settings without interfering
with ordinary memo behaviour. A second is reproducing the native statistics
meaning while supporting independent intervals. Layout, refresh cost, and
save/reload behaviour need in-game evidence after implementation. No game was
launched or save accessed during preparation.
