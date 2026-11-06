# DSPStarmapMonitor concept

## Purpose

A planet's name in the starmap is a useful place to answer a small question:
how much of the products I care about is this planet making?

The design extends the existing Memo tab with a compact production monitor.
Players choose a few products and a statistics interval for that memo, then
optionally display their production rates alongside the planet's name. The
game's own Production statistics remain the reference for those numbers.

This document describes the design target. [PROJECT.md](PROJECT.md) owns
decisions, unresolved choices, implementation scope, and delivery state.

## Player flow

1. Select a planet in the starmap and open its existing Memo tab.
2. Choose a statistics interval for this memo using the game's familiar
   interval vocabulary.
3. Use a small set of filter-style item-grid selectors to choose products.
   The available candidates come from this planet's statistics for that
   interval, rather than the entire recipe catalogue.
4. Enable a separate **Show production on starmap** checkbox.
5. Read a compact sequence of product icons and updating values beside the
   planet's ordinary name while navigating the starmap.

For example, one planet's memo could monitor iron ingots and magnets over ten
minutes, while another monitors processors over an hour. Each would show the
native production rate for its own interval. Opening either memo should make
its selections and interval apparent without opening Statistics first.

## Controls that belong in the Memo tab

The selectors, interval control, and display checkbox should share the native
controls' visual language, spacing, tooltips, and input behaviour. Ordinary
memo text, formatting, and its reminder checkbox retain their purpose.

A selection must be easy to identify, replace, or clear. The limited slot
count keeps both the Memo tab and the map label readable. Changing an interval
must not silently substitute a different product. An empty candidate list is
a normal condition with a short explanation, not a reason to offer unrelated
products.

The display checkbox controls visibility independently of the native reminder.
Turning it off should preserve the player's monitoring choices.

## Numbers with a clear meaning

“Local” refers to the planet owning the memo. It does not follow Icarus's
location, and it does not include the whole star system or galaxy.

The selected interval is a measurement window. For a timed interval, the
native Production tab presents the average rate per minute; the monitor
should use the same meaning, units, and rounding. The native All time view
is a total and must not be presented as a rate.

Product eligibility must be evaluated for that planet and interval. The game
also records consumption and traffic, so merely appearing somewhere in its
statistics is not sufficient evidence of local production. The exact
eligibility policy belongs to the product decisions in PROJECT.md.

The monitor reads existing statistics rather than collecting its own history
or estimating theoretical machine output. It should work while the Statistics
window is closed, and selecting a memo interval should not change that window's
filters or another memo's settings.

A real zero is different from missing data. Stopped production, a newly created
factory, a removed item definition, and unavailable history must not produce
a fabricated number. Previously selected products should remain identifiable
when their availability changes, according to the agreed selection policy.

## Live starmap presentation

Annotations belong to the displayed planet label; they do not become part of
the planet's saved name. Product icons identify the values, units remain clear,
and a tooltip can explain the measurement interval when space is tight.

The presentation should follow native label visibility and remain readable
with long names, different UI scales, and nearby reminders. Values should
update without requiring the player to reopen the memo. Refresh work should
be limited to what is useful for the visible map rather than repeatedly
scanning every factory.

Native planet selection, rename actions, navigation, and reminder interaction
must remain usable. New controls should neither intercept unrelated actions
nor let their clicks pass through to the map.

## Native ownership and persistence

Product choices, interval, and display preference belong to the memo in its
save. The intended route is the game's native storage and save lifecycle.
Settings must stay associated with the correct planet across reopening,
save/reload, and switching between games.

Native storage reuse must preserve memo text and formatting and keep saves
usable without the mod. Removing the plugin should remove its presentation
without renaming planets or damaging their notes. A storage design must explain
what remains visible and what happens to its settings when the plugin is absent.
The feasibility phase must establish this before persistence is implemented.

## First-delivery boundaries

The focus is a few planetary production figures integrated into existing UI.
Separate dashboards, additional production histories, consumption or balance
views, alarms, automated factory actions, and star/galaxy aggregation are
outside this design. The mod changes presentation and memo-owned settings;
it does not change production, inventory, logistics, or simulation rules.
