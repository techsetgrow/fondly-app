# Changelog

All notable changes to Fondly are documented here.

---

## [v1.2.0] - 2026-04-24

### Fixed — Blur detection (reworked)
- Portraits, bokeh shots, and smooth-skin subjects no longer flagged as blurry — sharpness is now measured from the sharpest details in the frame (eyes, hair, jewellery, foliage) rather than averaging across smooth skin and blurred backgrounds
- Old camera photos (2009–2015) no longer unfairly penalised — scoring normalised to a standard resolution so a sharp 8MP shot and a sharp 48MP shot are judged equally
- Motion-blurred scenes with patterned fabric (saris, embroidered clothing, textiles) now correctly caught — Gaussian pre-smoothing removes fine texture before the sharpness test so only genuine optical focus is measured
- Default threshold recalibrated to the new metric (slider range 1–50, default 6)

### Fixed — Similar shot grouping
- Shots from different parts of the day no longer grouped as "similar" — comparison now scoped to 10-minute windows, so ceremony photos are never matched with reception photos
- `_review/similar_shots/` is now a single flat folder instead of one subfolder per burst group — organising a wedding album no longer creates dozens of review folders
- Winner copy placed in the flat folder as `IMG_0234_KEPT.jpg` so it sorts alphabetically adjacent to its alternatives

### Fixed — Progress & UI
- Progress bar now updates smoothly during file copies — previously froze until all copies finished
- Each phase (Detecting duplicates → Rating sharpness → Grouping shots → Moving files) now runs 0–100% independently with a distinct colour, instead of one bar that stalled at 75%
- Grouping step now visible in the progress bar — was previously a silent gap after scoring
- Scan mode shows 3 steps; run mode shows 4 steps
- ETA display is right-aligned and stable — no longer jumped as phases switched
- Results window Close button works on every subsequent run (was broken after first close)
- All UI state fully resets after cancel or error

### Changed
- Burst shot sensitivity moved from Advanced panel to the main settings card
- Cancel button moved to bottom-right of the button row

---

## [v1.1.0] - 2026-04-24

### Added
- Cancel button — stops a run or scan cleanly after the current file; partial runs are fully undoable via Restore
- Disk space preflight check — warns before a copy run if the output drive has insufficient free space

### Fixed
- Runtime crash on launch (`ModuleNotFoundError: No module named 'email'`) — email module now correctly bundled
- Installer now detects and closes a running Fondly instance before upgrading
- Perceptual hash (burst/similar) comparison now scoped per event group — eliminates multi-hour hangs on large libraries

### Changed
- Restore shows a list of all past runs instead of a file picker
- Timestamped restore points in `_fondly/` — every run independently undoable
- Restore dialog warns if an older run is selected while newer runs exist
- Per-file error handling — a single unreadable file no longer aborts the entire run
- Empty folder cleanup after restore walks the full output tree

---

## [v1.0.9] - 2026-04-24

### Fixed
- Per-file error handling in organiser — a single unreadable file no longer aborts the entire run
- Restore crash ("string indices must be integers") when loading enriched restore point JSON
- Empty folder cleanup after restore now walks the full output tree (not just immediate parents), removing all empty intermediate directories except `_fondly/`

### Changed
- Restore now shows a list of all past runs (date, file count, source, output) instead of a file picker — no JSON hunting
- Each run saves a timestamped restore point in `_fondly/` inside your output folder, so multiple runs are all independently undoable
- Restore dialog warns if you select an older run when newer runs exist (files may have moved since)
- Restore point JSON enriched with `reason` and `group` fields per file (used by future review pane)
- Disk space preflight check added — warns before a copy run if the output drive has insufficient free space

---

## [v1.0.8] - 2026-04-23

### Changed
- Restore now shows a list of all past runs (date, file count, source, output) instead of a file picker — no JSON hunting
- Each run saves a timestamped restore point in `_fondly/` inside your output folder, so multiple runs are all independently undoable
- Tooltip style: warm yellow info background with bold title line and wider wrap width

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
