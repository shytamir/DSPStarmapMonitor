# First-delivery roadmap

This is a workload reference. [PROJECT.md](../PROJECT.md) alone records active
scope, story state, decisions, milestone attainment, and gate outcomes.
The [concept](../CONCEPT.md) supplies the intended player experience.

## Scope and sequencing

Deliver a small BepInEx extension to the planet Memo tab: limited product-grid
selection, a per-memo statistics interval, native persistence, and optional
live production annotations beside starmap planet names. Preserve ordinary
memo use and the game's authority over statistics.

| Phase | Work | Milestone | Dependency gate |
| --- | --- | --- | --- |
| Foundation | SM-0 | M0: Repository and research foundation available | Enables feasibility planning. |
| Feasibility | SM-1 | M1: Product contract and native route established | G1 before plugin implementation. |
| Memo prototype | SM-2 | M2: Memo controls, numbers, and persistence demonstrated | G2 before expanding into live map annotations. |
| Integration and handoff | SM-3, SM-4.1 | M3: Integrated candidate prepared | Builds on G2 and supplies the candidate for G3. |
| Acceptance | SM-4.2 | M4: First delivery accepted | G3 closes the delivery. |

Exclude CI, store publication, a general mod framework, custom production
simulation, dashboards, alerts, aggregation, and multiplayer support. Each
story includes its focused verification; avoid a separate testing programme
that duplicates the implementation workload.

## SM-0 — Foundation

**Value:** Contributors can understand the product and locate authoritative
decisions without reconstructing a development session.

### SM-0.1 — Establish the repository contract

**Story:** As a contributor, I want a clear introduction, concept, work plan,
and agent guidance so that contributions follow the same direction.

**Acceptance:**

- README addresses potential contributors; PROJECT owns steering and state;
  ROADMAP defines work without tracking its execution.
- CONCEPT describes the intended experience, and AGENTS sets concise working
  rules consistent with that division.
- Local research and runtime output are excluded from Git. Documentation
  links resolve, the existing license is preserved, and no mod code is added.

### SM-0.2 — Establish source familiarity

**Story:** As a maintainer, I want a bounded view of the existing game and
loader systems so that feasibility work starts from known surfaces.

**Acceptance:**

- Review relevant local mod patterns and existing assembly research first.
- Identify the Memo, statistics, starmap label, and storage surfaces through
  targeted read-only inspection of identified game inputs.
- Review the selected BepInEx tag's normal plugin contract without changing
  its checkout or transferring another project's architecture.
- Retain detailed evidence locally and distinguish source findings from
  runtime feasibility. Carry consequential uncertainties into PROJECT.

## SM-1 — Feasibility and product choices

**Value:** The first implementation has a small, agreed behaviour contract and
a credible native integration route.

### SM-1.1 — Define the monitoring interaction

**Story:** As a player, I want predictable selections and understandable
numbers so that I know what each planet label represents.

**Acceptance:**

- Set the slot limit, replacement/clear behaviour, defaults, and annotation
  interaction. Use a compact layout sketch if it helps settle the choices.
- Define the eligible local product set, timed interval options, All time
  treatment, and behaviour for selected products with zero or missing data.
- Define comparison with the native Production tab for the same planet and
  interval, including units and rounding.
- Record decisions in PROJECT and align the concept without adding a second
  decision register. No plugin implementation is required by this story.

### SM-1.2 — Establish the native integration and storage route

**Story:** As a maintainer, I want to reuse the game's existing systems without
damaging them so that the extension remains small and save-friendly.

**Acceptance:**

- Identify the narrow UI lifecycle and statistics access needed for the agreed
  behaviour, including use while the Statistics window is closed.
- Explain how memo identity and settings can survive native save/load while
  preserving user text, formatting, reminders, and unmodded save loading.
- Identify how the added UI can be removed and how unsupported inputs fail
  without affecting native controls. Do not assume unused storage fields exist.
- Select a minimal plugin target and dependency surface from actual references.
  Keep source detail and machine-specific evidence in local research material.
- If native storage cannot meet the contract, present the limitation and a
  bounded decision for the owner before implementing a substitute.

### G1 — Design and feasibility gate

Requires SM-1.1 and SM-1.2. The owner agrees the product choices and proposed
native route, and PROJECT records the implementation scope. A static design
must name any behaviour still requiring prototype evidence; it does not
establish successful save round-trips or runtime UI behaviour.

## SM-2 — Memo monitoring

**Value:** Players can configure a planet monitor in the native Memo tab and
recover the same choices after reloading.

### SM-2.1 — Integrate the Memo controls

**Story:** As a player, I want product slots, an interval, and a display toggle
beside my existing memo so that monitoring has one familiar home.

**Dependencies:** G1.

**Acceptance:**

- Introduce the minimal BepInEx plugin and approved controls using native UI
  conventions. Preserve text editing, formatting, reminder controls, and input.
- Bind controls to the inspected planet and support explicit select, replace,
  and clear actions under the agreed limit.
- Reopening and switching planets does not duplicate controls or retain the
  previous planet's bindings. Teardown releases owned UI and subscriptions.
- Compile against the selected references and check selection/lifecycle rules
  independently where practical.

### SM-2.2 — Connect local production statistics

**Story:** As a player, I want the offered products and values to reflect this
planet's selected interval so that monitoring agrees with Statistics.

**Dependencies:** SM-2.1 and the statistics contract from G1.

**Acceptance:**

- Populate candidates from the agreed planet/interval eligibility rule.
- Obtain and format values from existing production statistics, preserving
  the native meaning without creating a parallel history collector.
- Cover independent memo intervals, absent factories/history, zero production,
  unavailable item definitions, and retained selections under interval changes.
- Leave the Statistics window's own filters and selection untouched. Prepare
  a focused comparison for G2, including a planet different from Icarus's.

### SM-2.3 — Persist memo-owned settings

**Story:** As a player, I want my choices to survive saving and reloading so
that I do not have to rebuild every planet monitor each session.

**Dependencies:** SM-2.1 and the storage route agreed at G1.

**Acceptance:**

- Store product identities, interval, and visibility through the agreed native
  route. Do not persist sampled rates as a second statistics history.
- Preserve ordinary memo text, formatting, and reminders through edits,
  reopening, and save/load. Keep different planets and saves independent.
- Define safe handling of missing, malformed, and unsupported settings, and
  document the observable behaviour when the mod is absent.
- Check the settings logic offline where useful and supply the save/reload
  and plugin-removal procedure needed at G2.

### G2 — Memo prototype gate

Requires SM-2.1–SM-2.3. Focused build and offline checks pass, and an identified
prototype is available for in-game review. The review demonstrates native
statistics agreement, ordinary memo operation, independent settings, and
save/reload plus unmodded loading on a disposable save copy. Record the actual
observations and the owner's decision in PROJECT. Resolve storage or numeric
contract failures before adding live map presentation.

## SM-3 — Live starmap annotations

**Value:** Players can read the production they selected while navigating the
map, without repeatedly opening Statistics.

### SM-3.1 — Display selected production beside planet names

**Story:** As a player, I want an optional compact product-and-rate annotation
beside a planet's name so that its useful output is visible at a glance.

**Dependencies:** G2.

**Acceptance:**

- Render the chosen products and values when their memo's display toggle is
  enabled, using the approved interval, units, and interaction.
- Keep the actual planet name and native rename, selection, navigation, memo
  reminder, and marker behaviour intact.
- Follow native label visibility and communicate zero/unavailable data under
  the agreed policy. Turning the toggle off removes the annotation promptly.

### SM-3.2 — Maintain readable and bounded updates

**Story:** As a player, I want live labels to remain accurate and unobtrusive
across map navigation and session changes.

**Dependencies:** SM-3.1.

**Acceptance:**

- Update visible annotations from native statistics without unbounded factory
  scans or repeated broad reflection in UI update loops.
- Handle reopen, planet rename, interval/selection changes, save switching,
  and teardown without stale values, duplicate UI, or cross-save state.
- Check long names, the maximum selection, UI scale, zoom, nearby reminders,
  and native visibility transitions. Keep any truncation or tooltip meaningful.
- Verify focused lifecycle and mapping rules offline and identify the small
  set of visual/refresh observations needed from the final in-game review.

## SM-4 — Candidate validation

**Value:** The owner can assess a specific integrated build against a concise
and reproducible player workflow.

### SM-4.1 — Prepare the candidate and review procedure

**Story:** As the maintainer, I want one identified candidate and clear checks
so that review results refer to the same implementation.

**Dependencies:** SM-3.2.

**Acceptance:**

- Build against the selected references, run relevant focused checks, and
  inspect the deliverable for unintended dependencies or local data.
- Identify the source and candidate, and prepare complete setup, actions,
  expected results, and reporting instructions for a short in-game review.
- Cover numeric agreement, Memo preservation, native storage, live labels,
  UI/input behaviour, and session cleanup. Reuse G2 evidence where unchanged;
  repeat a check when later changes affect its result.
- Keep build output and raw evidence local. This story does not require CI
  or authorize store publication.

### SM-4.2 — Review the integrated experience

**Story:** As the owner, I want to assess the actual in-game experience so
that acceptance reflects the behaviour players will receive.

**Dependencies:** SM-4.1.

**Acceptance:**

- Record observations against the identified candidate and tested conditions.
- Resolve delivery-blocking defects and recheck affected behaviour. Put any
  explicitly deferred work and its disposition in PROJECT.
- Record an explicit owner acceptance or rejection without inferring either
  from compilation, elapsed time, or a partial test report.

### G3 — Delivery acceptance gate

Requires SM-4.1 and SM-4.2. The owner accepts the integrated candidate and the
required evidence supports its product contract. Record the gate result and
delivery state in PROJECT. Release publication remains a separate decision.
