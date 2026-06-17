# External Data

Project external-data layout:

- `raw-untracked/` — raw external downloads or exports. Git-ignored by default.
- `derived/` — small curated/reproducible outputs that may be tracked when useful.
- `derived-untracked/` — large derived outputs, bulky intermediates, and local-only generated files. Git-ignored by default.
- `scripts/` — data acquisition, parsing, cleaning, and regeneration scripts.

See `~/Projects/PROJECT_DATA_CONVENTIONS.md` for the shared convention.
