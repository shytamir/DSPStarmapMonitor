# Project steering

This is the sole record of project state, steering, decisions, and acceptance.
The [roadmap](management/ROADMAP.md) defines the workload and its gates; the
[concept](CONCEPT.md) describes the intended experience. Neither tracks progress.

## Current position

**Disposition:** Closed — no-go, owner decision D09 on 2026-11-07.
**Active work:** None.

Repository preparation and the prior-art survey are complete. All remaining
feasibility, implementation, and validation work is cancelled. No mod code,
build project, or CI was created, and no runtime feasibility or delivery
acceptance was established.

**Next action:** None. Reopening requires an explicit owner decision to
reconsider the value proposition. The concept and roadmap remain reference
documents and do not authorize further work.

**Release state:** No build or release exists.

## No-go decision and prior art

The owner decided that the additional value of this project does not justify
the development effort after reviewing the Thunderstore prior-art survey.
Existing mods already serve much of the underlying need for planetary
production visibility, selected-item monitoring, and starmap information.

The survey found no documented exact match for the complete combination of
native Memo-tab product selection, independent memo intervals, and updating
production rates beside planet names. That narrower integration remained a
distinction, but the owner judged it insufficient to proceed. The decision
does not assert that an identical mod exists or that the concept is technically
infeasible.

The following findings are a dated snapshot from 2026-11-07. The survey screened
metadata for 760 packages, including 134 deprecated entries, in the
[Thunderstore DSP catalogue](https://thunderstore.io/c/dyson-sphere-program/api/v1/package/)
and examined 24 relevant package READMEs. Versions were checked against the
live catalogue and release archives because some search snapshots were older.

| Prior art examined | Existing value and remaining distinction |
| --- | --- |
| [DSPStarMapMemo 0.0.7](https://thunderstore.io/c/dyson-sphere-program/p/appuns/DSPStarMapMemo/) | Adds descriptive text and icons to star and planet map labels through a separate memo window. Closest visual precedent; live production values and measurement intervals are not documented. |
| [StarSystemProduction 0.2.0](https://thunderstore.io/c/dyson-sphere-program/p/LokiMoonLabs/StarSystemProduction/) | Provides actual recorded planetary production rates using native time windows, plus lifetime totals, in a product/machine/recipe browser. Closest statistics precedent; Memo configuration and live map-label rates are not documented. |
| [Stellogistics 2.1.3](https://thunderstore.io/c/dyson-sphere-program/p/BaCheetah/Stellogistics/) | Integrates a logistics panel into the starmap, with an item-grid picker and saved per-planet/per-system filters. Closest filtering workflow; its measurements concern station stocks, capacity, and inbound cargo. |
| [DSPTaskMaster 1.2.0](https://thunderstore.io/c/dyson-sphere-program/p/ThemeInsideAMind/DSPTaskMaster/) | Offers per-planet selected-item tasks and a live overlay. Production targets use machine capacity and surplus uses the last minute; it has a separate task interface and DSPModSave storage. |
| [DashboardOverhaul 1.4.0](https://thunderstore.io/c/dyson-sphere-program/p/fyyy/DashboardOverhaul/) | Extends native production charts and saved customization through Dashboard pages. It already supports configurable production monitoring in a different presentation. |
| [RateMonitor 0.4.3](https://thunderstore.io/c/dyson-sphere-program/p/starfi5h/RateMonitor/) | Monitors selected machines with theoretical and efficiency-adjusted rates in its own window. It serves related production-monitoring needs at a different scope. |

Additional precedents included
[StatsUITweaks](https://thunderstore.io/c/dyson-sphere-program/p/starfi5h/StatsUITweaks/)
for native statistics controls and intervals,
[DSPAllPlanetInfo](https://thunderstore.io/c/dyson-sphere-program/p/appuns/DSPAllPlanetInfo/)
for starmap information panels, and
[IconFix](https://thunderstore.io/c/dyson-sphere-program/p/TTenYX/IconFix/)
for extending the native icon picker used by memos. Older Bottleneck and
BetterStats entries were marked deprecated in the surveyed catalogue.

This was a documentation and targeted source survey. No candidate mod was
installed or run, and compatibility was not tested. Undocumented features and
sparse older documentation limit the negative finding. Detailed research
material remains outside the tracked repository.

## Steering decisions

D01–D08 retain the concept's original direction for reference. D09 governs
the project's disposition.

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
| D09 | No-go, owner decision on 2026-11-07: the incremental value over prior art does not justify the effort. Close the project and cancel the remaining workload; see the [rationale](#no-go-decision-and-prior-art). |

## Unresolved questions at closure

Q01–Q06 remain unresolved and are closed without action under D09. The original
proposals and resolution points below are retained as context, with no pending
request for the owner to settle them.

| ID | Question and starting proposal | Original resolution point |
| --- | --- | --- |
| Q01 | How many product slots and what happens at capacity? Start with three slots, explicit replacement or clearing, and no automatic eviction. | SM-1.1 / G1 |
| Q02 | Exactly which products qualify? Interpret local as the memo's planet, wherever Icarus is. Start with positive recorded production during the interval, excluding consumption-only or traffic-only entries. Check this against the intended native filtering experience. | SM-1.1 / G1 |
| Q03 | Which intervals and initial selection? Start with the native timed intervals and a 1-minute default. The native All time option displays totals, so omit it from a rate-only first delivery unless a clearly labelled total mode is desired. | SM-1.1 / G1 |
| Q04 | What happens when a selection becomes inactive or unavailable? Retain the selected product, show zero only when measured, and distinguish unavailable data. Newly offered candidates still follow the chosen interval. | SM-1.1 / G1 |
| Q05 | What does an active label do? Start with automatic value updates while visible, an identifying tooltip, and no extra click action. Start the display checkbox off; disabling it preserves selections. | SM-1.1 / G1 |
| Q06 | Can native storage preserve selections, interval, and visibility without damaging memo editing or save compatibility? Choose a viable route from source evidence, then prove its behaviour in the Memo prototype. If none meets the contract, return a scope decision instead of silently adding another store. | SM-1.2 / G1; demonstrated at G2 |

## Work state

Updated 2026-11-07. IDs refer to the [roadmap](management/ROADMAP.md).
Use `Planned`, `Active`, `Blocked`, `Complete`, or `Cancelled` for work.
Cancellation does not mean delivery or gate acceptance. Record gate outcomes
and owner acceptance explicitly; technical completion alone does not pass an
owner gate.

| Epic | State |
| --- | --- |
| SM-0 — Foundation | Complete |
| SM-1 — Feasibility and product choices | Cancelled — D09 |
| SM-2 — Memo monitoring | Cancelled — D09 |
| SM-3 — Live starmap annotations | Cancelled — D09 |
| SM-4 — Candidate validation | Cancelled — D09 |

| Story | State | Evidence or dependency |
| --- | --- | --- |
| SM-0.1 | Complete | Documents and local-artifact exclusions prepared; 14 relative links, 11 story mappings, and 3 gate records checked. License unchanged; whitespace and scope checks passed. |
| SM-0.2 | Complete | Existing mod patterns reviewed; selected current game types and tagged BepInEx source inspected read-only. |
| SM-1.1 | Cancelled | D09; Q01–Q05 closed without resolution. |
| SM-1.2 | Cancelled | D09; native integration and storage feasibility not established. |
| SM-2.1 | Cancelled | D09; no implementation started. |
| SM-2.2 | Cancelled | D09; no implementation started. |
| SM-2.3 | Cancelled | D09; no implementation started. |
| SM-3.1 | Cancelled | D09; no implementation started. |
| SM-3.2 | Cancelled | D09; no implementation started. |
| SM-4.1 | Cancelled | D09; no candidate created. |
| SM-4.2 | Cancelled | D09; no delivery review performed. |

| Milestone / gate | State | Basis |
| --- | --- | --- |
| M0 — Foundation available | Reached | SM-0.1 and SM-0.2 complete. |
| M1 / G1 — Feasible design | Not reached / not assessed | Closed under D09. |
| M2 / G2 — Memo prototype demonstrated | Not reached / not assessed | Closed under D09. |
| M3 — Integrated candidate prepared | Not reached | Closed under D09. |
| M4 / G3 — First delivery accepted | Not reached / not assessed | Closed under D09. |

## Technical evidence at closure

Initial static research used game build 0.10.35.29151 and BepInEx source tag
v5.4.17. These are inspection inputs, not a compatibility claim. The game
contains native Memo persistence, planetary production history, and starmap
label/reminder surfaces. Their suitability for this extension was not
established before closure.

Safe storage of extra memo settings, independent statistics intervals, layout,
refresh cost, and save/reload behaviour remained unverified. These uncertainties
were not demonstrated technical failures; the no-go decision rests on the
prior-art value assessment above. No game was launched or save accessed.
