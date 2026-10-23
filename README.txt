# Flight Logbook — free offline app

## Included files
- `index.html`: the app
- `manifest.webmanifest`: install metadata
- `sw.js`: offline app-shell cache
- `flight-logbook-pdf-import.json`: 46 flight entries transcribed from the provided DGCA e-Log Book PDF
- `README.txt`: this guide

## Import the supplied PDF flight entries
1. Open the app.
2. Select **Import Excel / CSV** (the file picker also accepts JSON).
3. Choose `flight-logbook-pdf-import.json`.
4. Confirm the import. The app adds 46 entries, and the dashboard/report totals update.
5. Review the records and compare them with the original DGCA e-Log Book PDF.

If the same JSON file is imported repeatedly, its stable IDs update the same bundled entries instead of duplicating them. However, if you already typed the same flights manually with different IDs, those manually entered copies may duplicate. Back up first and check the flight list before importing.

## Data transcribed and assumptions
- Source PDF is dated 24 October 2026 and contains 46 approved entries.
- Flight dates, aircraft types/registrations, instructor names, route, departure/arrival times, flight durations, exercise remarks and landings were transcribed from the PDF.
- All flights are recorded as single-engine because the source labels the aircraft `SINGLE`.
- When the PDF lists Prayank as co-pilot/student and another pilot as PIC, the printed duration is recorded as Dual and Day Dual. The 13 September 2026 “First solo” flight is recorded as 00:10 PIC and Local PIC.
- The PDF shows BARAMATI as both departure and arrival, so cross-country categories are left at 00:00. Night and instrument categories are also left at 00:00 because no values are shown in those columns.
- The “Emergency sortie?” flag is enabled only when the remarks explicitly include “Emergency procedures.” This is treated as an emergency-training exercise for the dashboard's last-emergency date, not an actual in-flight emergency.
- The PDF lists landings, but does not give a separate take-off count. Take-offs are therefore left as 0/unknown rather than guessed.
- Date of entry and arrival date are set to the flight date because the PDF shows the same date for those fields on the entries.

## Quick test
Open `index.html` in a recent browser. Local storage works, but install and service-worker offline caching require HTTPS or localhost.

## Recommended free installation using GitHub Pages
1. Sign in to GitHub and create a public repository, e.g. `flight-logbook`.
2. Upload `index.html`, `manifest.webmanifest`, `sw.js`, and `flight-logbook-pdf-import.json` to the repository root.
3. Open repository Settings → Pages. Select deploy from branch, choose `main` and `/ (root)`, and save.
4. Wait for the Pages URL, then open it once while online.
5. On Android Chrome, open the URL → menu (⋮) → Install app or Add to Home screen.
6. On Windows/macOS Chrome or Edge, open the URL and choose Install from the address bar or browser menu.
7. Launch the installed app once while online. The app shell should then load offline.

## Importing your own logbook later
- Prefer `.xlsx` or `.csv`. The first worksheet is read from `.xlsx`; the first row with common flight-log headings is used as the header row.
- Import adds records; it does not clear existing records. Check imported dates, durations and category totals.
- Complex Excel formulas, merged headers, multi-sheet workbooks, unusual time formats, and legacy `.xls` files may need to be saved as `.xlsx` or CSV first.

## Privacy and backups
Records are stored in IndexedDB in the browser profile on the device. They are not automatically synced across devices. Use Backup to download a JSON file and restore it on another device. Keep backups private.

## Important
This is a personal tracking aid, not an official DGCA logbook or verified flight record. Verify all imported records and totals against your school's records and applicable requirements. The app does not provide automatic cloud backup.
