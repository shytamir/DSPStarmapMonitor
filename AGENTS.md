# Working on DSPStarmapMonitor

## Read first

Read this file and [docs/PROJECT.md](docs/PROJECT.md) before changing the
repository. Read [docs/CONCEPT.md](docs/CONCEPT.md) for product intent and the
[roadmap](docs/management/ROADMAP.md) for the relevant story and dependencies.
Current owner instructions govern the task; neighbouring repositories are
examples, not inherited requirements.

## Management as code

- `README.md` introduces the project to players and potential contributors.
- `docs/PROJECT.md` alone records steering, decisions, open decisions, authorized
  scope, progress, gate outcomes, acceptance, and release state.
- `docs/management/ROADMAP.md` defines epics, stories, dependencies, milestones,
  and gate criteria. Do not add status columns, progress checkboxes, completion
  notes, or dated work logs there.
- `docs/CONCEPT.md` describes the intended player experience and its boundaries.
  It is not a second backlog, decision register, or implementation report.

Keep each fact in its owning document and link to it elsewhere. Record state
changes in PROJECT.md using the roadmap's stable identifiers. A roadmap entry
does not itself authorize execution. An owner request may authorize a whole
phase or several stories; do not seek repeated permission within that scope.
Do not present planned behaviour as delivered or technical checks as owner
acceptance. Avoid adding management files when these documents suffice.

## Product discipline

Extend the native Memo tab and starmap presentation. Use the game's production
statistics as the authority for quantities, intervals, and units. Keep planet
scope explicit, including when Icarus is on a different planet.

Prefer native controls, assets, lifecycle, identity, and storage. Investigate
the smallest viable integration before introducing replacement machinery.
Preserve ordinary memo editing, formatting, reminders, planet names, and
statistics-panel settings. Display annotations must not rename planets.

Persistence belongs to each memo in its save. Establish a safe native storage
route before implementing it; do not assume unused fields or undocumented
extension points are available. Record a blocking limitation and alternatives
in PROJECT.md if that route cannot meet the product contract. Do not silently
substitute external storage or change the native save format.

Keep production and factory simulation read-only. Bound refresh work to the
relevant UI and selected products. Keep runtime access, selection rules, and
presentation sufficiently separate to check them without recreating the game.
Prefer a few direct components over a general framework.

## Research and implementation

Start with existing local evidence and the selected BepInEx source tag. Check
the identity of cached assembly evidence before relying on it. Inspect only
the types or methods needed to resolve a concrete question. Treat game and
dependency files as read-only inputs, and do not execute game assemblies just
to inspect them. Leave the BepInEx checkout at its selected tag; do not edit,
build inside, or switch that dependency checkout.

Keep decompiled source, binaries, hashes, machine paths, exploratory scripts,
and session notes in ignored `artifacts/` or `runtime/`, or a project-specific
folder in the shared untracked resource area. Do not publish them as repository
content. Public documentation should explain the product and contributor
contract, not narrate an agent session.

Use the selected BepInEx version's ordinary plugin lifecycle, metadata, and
logging. Use narrowly scoped Harmony patches where the confirmed integration
requires them, and clean up only this plugin's hooks and UI. Do not alter the
loader or introduce extra runtime dependencies without a concrete need.

Inspect Git status before editing and preserve unrelated work. Make the
smallest coherent change that satisfies the task. Do not add unrelated
features, speculative compatibility layers, or infrastructure.

## Verification and delivery

For documentation changes, check links, identifiers, scope, and the separation
of work definitions from state. For code changes, build against the selected
references and run focused checks of the behaviour being changed. Add tests
where they provide useful protection, not as a ritual.

Keep source inspection, compilation, automated checks, in-game observations,
and owner acceptance distinct. Report unavailable checks accurately. Prepare
a concise procedure and identified candidate when a roadmap gate needs live
evidence. Installation, game execution, save access, and publication must be
within the owner's requested scope; repository editing does not imply them.

Review the final diff and changed files. Commit and push only when requested;
stage reviewed paths and avoid destructive Git operations. Keep generated
output, proprietary dependencies, player data, and credentials out of Git.
Report the result, relevant checks, and material limitations concisely.
