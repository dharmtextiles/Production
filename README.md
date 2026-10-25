# Production Payment Calculator

Static web app (no server). Works offline once opened, installs to the phone home screen, and has voice entry for production figures.

## Put it on GitHub Pages
1. Create a new GitHub repository (e.g. `production-calc`).
2. Upload all files in this folder to the repository root: `index.html`, `manifest.webmanifest`, `sw.js`, `icon.svg`, `icon-192.png`, `icon-512.png`.
3. Repository → **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
4. After a minute the app is at `https://<your-username>.github.io/production-calc/`.
5. On the phone open that link in Chrome → menu → **Add to Home screen / Install app**.

## Voice entry
Click a box (machine + date), press **Voice entry**, speak numbers. Each number fills the box and the next date opens. Say "skip"/"next" for a blank day, "back" to go up, "stop" to finish. Needs Chrome or Edge, internet connection, and microphone permission (GitHub Pages is HTTPS, so it works).

## Notes
- Saved entries live in the browser on that device (localStorage). They are not shared between devices and are lost if browser data is cleared.
- Delete password is set in `index.html` (`const PW='vikram'`). It is visible to anyone who views the page source.
- When you upload a new `index.html`, change `CACHE='ppc-v1'` in `sw.js` to `ppc-v2` so phones pick up the update.
