# Changelog

All notable changes to Fondly are documented here.

---

## [v1.0.7] - 2026-04-23

### Changed
- "Consider supporting Fondly" moved to top-right header (visible when closing); "Tell us what you think" moved to bottom button row
- Window opens 100 px from top, horizontally centred — stays fully on screen when Advanced panel expands
- Dry Run option removed — Scan Only covers the same need without the technical jargon

### Fixed
- Scan Only results now use consistent future-tense language ("would be organised", "would go to") instead of past-tense action verbs

---

## [v1.0.6] - 2026-04-23

### Added
- Feedback link moved to top-right corner of the header — visible on launch without scrolling (#3)
- Non-media files (PDFs, documents, audio, etc.) now moved to `_other/` instead of silently skipped (#4)
- Restore: confirmation dialog shows run date, file count, and folders before restoring (#2)
- Restore: hint line below main buttons explains that every run creates a restore point (#2)

---

## [v1.0.5] - 2026-04-23

### Added
- Results open in a dedicated window (floats above main, pre-built for instant display)
- Collapsible full log in Results window with horizontal + vertical scrollbars
- ttk styling: ACCENT-coloured progress bar, themed combobox and scrollbars
- Hover effects on all buttons (Run, Scan Only, Watch Folder, Restore, Browse)

### Fixed
- Advanced panel expanding pushes Run button off screen — window now auto-resizes (capped at 90% screen height)
- Results window appearing behind main window — fixed with `transient()`
- Delay before Results window appears — window pre-built at startup; "Finalizing…" shown while results are prepared

---

## [v1.0.4] - 2026-04-19

### Changed
- Moved to TechSetGrow GitHub organisation — all download and update links updated
- Buy Me a Coffee link updated to techsetgrow page
- Publisher name in Windows installer updated to TechSetGrow

---

## [v1.0.3] - 2026-04-19

### Changed
- Transferred to TechSetGrow — all links, publisher name, and Buy Me a Coffee updated

---

## [v1.0.2] - 2026-04-18

### Fixed
- Crash on Scan Only ("similar_losers not defined") — stale variable reference in dry-run summary
- Taskbar icon now displays at correct size on Windows (uses bundled .ico via wm_iconbitmap)
- Reduced installer size by excluding unused Python modules from the bundle

---

## [v1.0.1] - 2026-04-18

### Fixed
- Default window width increased so the Support link in the footer is always fully visible
- App icon updated to use the Fondly logo mark (leaf/lens motif) for consistent branding

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
