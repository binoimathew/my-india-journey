# My India Journey 2026 — Installable PWA (v1.1.0)

## What is included
Offline-capable itinerary, place checkboxes, wake-up time slots (alert only while the app is open), three-word extra notes, food/drink and other expense logging with timestamps, pooled cost calculation, group size/leader, booking statuses, JSON backup/restore, CSV export, update checks.

## Install on Android
1. Upload **all files in this folder together** to a permanent HTTPS website (e.g. GitHub Pages, Netlify or Cloudflare Pages). `index.html` must be at the published app URL. Do not open `index.html` from the Downloads folder and expect installation/update support: service workers require HTTPS (or localhost).
2. In Chrome on Android open the HTTPS app URL; choose the browser menu → Install app (or Add to Home screen).
3. Open from your home screen. After the first successful online visit, the app can open offline.

## Publish updates
1. Edit `index.html` and any other assets.
2. **Change CACHE_VERSION** in `sw.js` for each release (e.g. 1.1.1). Update the displayed version in `index.html`.
3. Upload all updated files to the **same HTTPS address**. Users can tap Check for updates and approve the new version. The service worker installs it and reloads the app. Updates may not be immediate if offline.
4. Keep the same website origin and path; localStorage is tied to the browser origin. Do not rename the storage key `my-india-journey-2026-v1` unless you migrate its data.

## Data safety and caveats
- Backups are JSON; Restore replaces current app data after confirmation. Expense CSV export is also available.
- Existing HTML-file localStorage records may **not** transfer automatically to the hosted app because the origin differs. Export a backup from the old version and restore it into the hosted PWA.
- PWA cannot guarantee an alarm when backgrounded or the phone is locked. Use Android Clock for critical wake-ups.
- Pooled expenses are divided equally by current member count; individual who-paid-whom settlement is not implemented.
- No live GPS or server synchronization; data remains local to this browser/device. Clearing site data can erase it.
- A static HTTPS host is necessary for remote updates; this package does not create or deploy one.
