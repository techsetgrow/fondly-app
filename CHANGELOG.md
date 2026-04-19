# Changelog

All notable changes to Fondly are documented here.

---

## [v1.0.0] - 2026-04-18

### Added
- Sort photos and videos into date-based event folders automatically
- GPS location names in folder titles (e.g. 2024-06-10 - Rome, Italy)
- Duplicate detection — exact copies moved to `_review/exact_duplicates/`
- Blur detection — only flags camera-shake blur; portrait/bokeh shots are unaffected
- Burst shot triage — keeps the sharpest photo, moves alternatives to a named subfolder in `_review/similar_shots/<winner>/` so you can see exactly which shot was chosen
- Winner comparison copy — a `_KEPT_` prefixed copy of the kept shot is placed in the burst review folder so you can compare all versions side-by-side
- Copy mode — organise without touching your originals (default on for safety)
- Rename files to date-sequence format (2024-06-10_001.jpg)
- Folder hierarchy options: flat, by year, or by year and month
- Scan Only report — full preview before moving anything
- Watch folder — auto-organise new arrivals every 60 seconds
- Undo any run with one click using the built-in Restore feature
- Update notifications — Fondly checks for a new version on startup and shows a banner with a download link (works offline with no error)
- Hover tooltips on every setting in plain English
- Advanced settings panel (collapsed by default): burst sensitivity, date format, folder structure, file renaming, dry-run mode
