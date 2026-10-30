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

## Import from photo (new in v5)
Entry tab → step 2 → **📷 Import from photo** → pick the photo of the monthly sheet (gallery or camera).
1. First time only: press **⚙ AI key** and paste an API key (Google Gemini has a free tier; Anthropic Claude is pay-per-use). The key stays in that browser only.
2. The photo is auto-cropped to the pink sheet and read by the AI. A review table opens next to the photo: Column 1 / Column 2 for each machine (left block / right block), days 1-15 and 16-end, with the operator name above each half.
3. Yellow = AI was unsure, orange = not a number (e.g. BF), red = over 50 m. Fix anything that does not match the photo. Check **month, year, machine numbers and operator names** (month and year are usually not readable on the sheet; default is last month).
4. **Save N entries** creates one saved entry per operator (an operator whose name is the same in both halves becomes one entry for the whole month). Re-importing the same operator and dates updates the figures and keeps rate / loss / advance. New entries get the default rate (2.2); open the entry to change rate, add loss / advance.
If no key is set you can still type the figures in the same review table while looking at the photo.
