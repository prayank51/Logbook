FLIGHT LOGBOOK — INSTALL FIX

Files to upload to the ROOT of your GitHub Pages repository (same folder as index.html):
- index.html (replace existing)
- manifest.webmanifest (replace existing)
- sw.js (replace existing)
- icon.svg (new)
- icon-192.png (new)
- icon-512.png (new)
- apple-touch-icon.png (new)

Do not delete existing records or clear browser site storage. This update changes the service worker cache version and adds the required app icons to the PWA manifest.

After committing all files, wait for GitHub Pages deployment. Open https://prayank51.github.io/Logbook/ in Chrome, refresh, then use Chrome menu > Install app (or the install button if shown). If the app was previously installed/added as shortcut, remove only that shortcut and try installing again after deployment.

Note: if Chrome still doesn't offer Install app, check that all files are at repository root, Pages is deployed from the branch/folder containing them, and the site is opened over HTTPS.
