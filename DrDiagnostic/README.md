# Dr Diagnostic

Standalone analyzer companion for RimWorld 1.6 that captures snapshots from **Dubs Performance Analyzer** and writes portable logs you can review or share. Originally forked from the in-house diagnostics tools, Dr Diagnostic is designed for any load order.

## Features
- Automated CSV exports of Analyzer samples on a configurable interval.
- Optional console summaries highlighting hotspots that break the configured CPU/average/spike thresholds.
- Desktop-first log storage (`DrDiagnostic Logs`) with automatic fallback to RimWorld’s save-data folder if Desktop access is unavailable.
- Manual “Export latest snapshot now” button inside Mod Settings for ad-hoc profiling.

## Requirements
- RimWorld 1.6
- [Dubs Performance Analyzer](https://steamcommunity.com/sharedfiles/filedetails/?id=2032157151) enabled and loaded before Dr Diagnostic.

## Installation
1. Copy the `release/DrDiagnostic/` folder into your RimWorld `Mods/` directory (or point your mod manager at it).
2. In the RimWorld mod list, enable **Dubs Performance Analyzer** and place **Dr Diagnostic** immediately after it.
3. Restart the game if prompted.

## Configuration
Open **Options → Mod Settings → Dr Diagnostic** to adjust:
- **Enable automatic exports** – turns scheduled CSV dumps on/off.
- **Export interval** – default 30 seconds (≈1,800 ticks).
- **Hotspot thresholds** – CPU %, average ms, and spike ms cut-offs used for the warning summary.
- **Manual export button** – available while a save is running; writes a snapshot instantly.

## Log Locations
1. Primary: `Desktop/DrDiagnostic Logs/`
   - Contains rolling CSV files (`AnalyzerExports/`) plus `top-samples.log`.
2. Fallback: `<RimWorld save data>/DrDiagnostic/`
   - Used automatically if Desktop access is blocked or the folder cannot be created.

On macOS you may see a Files & Folders permission prompt when the mod first targets the Desktop. Grant access to keep logs on the Desktop; otherwise the fallback path engages automatically.

## Releases
- **r001 (2025-10-17)** – Initial public fork from Nano Diagnostics; independent packageId `roseberry.drdiagnostic`.
- **r002 (2025-10-17)** – Desktop log directory, automatic fallback handling, refreshed release binaries.

## Troubleshooting
- **No CSV files appear:** Check RimWorld’s console/log for `[DrDiagnostic]` warnings. If Desktop access was denied, look under the fallback path shown in the warning message.
- **Manual export fails:** Ensure Dubs Performance Analyzer is enabled; the mod logs a warning if it cannot reflect into Analyzer types.
- **Hotspot spam:** Increase the thresholds in Mod Settings or disable the hotspot summary checkbox.

## Contributing / Support
This repository is part of the Nano workspace. Updates are logged in `DrDiagnostic/Notes/progress_log.txt`; release binaries live under `release/DrDiagnostic/`.
