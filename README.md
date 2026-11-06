# DSPStarmapMonitor

Keep useful production figures beside the planets that produce them.
DSPStarmapMonitor aims to extend Dyson Sphere Program's existing Starmap Memo
tab through BepInEx, using the game's own production statistics and interface.

The intended workflow is small:

1. Open a planet's Memo tab and choose a production-statistics interval.
2. Select a few products through compact item-grid controls, with candidates
   drawn from that planet's statistics for the chosen interval.
3. Enable a separate checkbox to display those products and their updating
   production rates beside the planet's name in the starmap.

Each memo would keep its own choices. Ordinary memo text and reminders would
remain available, and the displayed rates would follow the game's Production
tab for the same planet and interval.

## Explore the project

- [Concept](docs/CONCEPT.md): the intended experience and product boundaries.
- [Project steering](docs/PROJECT.md): current scope, implementation and release
  state, decisions, and the next work to consider.
- [Roadmap](docs/management/ROADMAP.md): epics, user stories, and delivery gates.

## Contributing

The project is AI authored and human managed. Contributions are welcome from
people interested in unobtrusive UI, native game integration, and clear,
verifiable behaviour. Start with the concept and project steering; discuss
substantial changes to the experience or data storage before implementing them.

Prefer small changes that reuse the game's systems. Describe the player-facing
result and how it was checked. Keep game binaries, decompiled source, saves,
and local tooling out of contributions. Coding agents should also read
[AGENTS.md](AGENTS.md).

## License

[Apache License 2.0](LICENSE).
