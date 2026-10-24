# ASE Crimson Chat / Version 2.9 — Command Suite

This ZIP is the complete **browser website project**, built from the previous ASE 2.8.1 easy-upload edition. It still includes the chat, private rooms, picture-based map, reports, radio, live/video calls, wallpapers and Mission Lab. It now allows **up to SIX people online**. No app or Android Studio is necessary for visitors.

## Easiest GitHub/Render installation

1. Download and **extract** the ZIP.
2. Go to your GitHub repository. Remove or overwrite older root files as appropriate so the newest version takes effect.
3. Upload the **contents** of the extracted folder into the repository **root**. Do not add the outer ZIP or an extra nesting folder. Keep the `public/` folder intact.
4. The top level must contain `server.js`, `package.json`, `wallpapers.bundle.json`, `README.md`, plus the `public/` directory.
5. The `public/` directory contains `index.html`, `app.js`, `suite.js`, `suite.css`, `style.css`, `lab.js`, `lab.css`, `ops.js`, the map image, sample videos and a grit texture.
6. On Render, use a **Web Service**, language **Node**, Build Command `npm install`, Start Command `npm start`, and root directory **blank** for a repository-root upload. Deploy the newest commit.
7. Check `https://YOUR-RENDER-URL/health` — it should show `status: ok` and `wallpapers: 140`.
8. Open the bare site URL (not `/public/index.html`) on phones and computers. Camera and microphone features need HTTPS and browser permission.

The 140 static wallpapers are still packaged in ONE `wallpapers.bundle.json` file. The two moving wallpapers use CSS. You do not need to upload 140 separate SVG files. This edition uses fewer than 100 project files, so GitHub's browser upload limit is not a problem.

## New / Version 2.9

Press **ASE / OPS** in the lower-left of the site to open the Command Suite. Access the **WHEEL** button as a shortcut. The new features are:

1. **ASE Command Center** — six-user status roster, authorized chat/map overview, activity panel and links to existing missions, media and radio.
2. **Complete UI Editor** — theme color, text scale, message size and chat width; saved in your current browser.
3. **Secret Vault** — encrypted device-local notes and optional encrypted photos, video clips or wallpapers (up to 8 MB per attachment; up to 20 files). Requires a 6+ character passphrase. Uses Web Crypto AES-GCM + PBKDF2; no server receives this content. Password reset/recovery is unavailable. Note-JSON export does NOT include encrypted attachment bytes; keep originals.
4. **Sonar Ping** — tap a map point to send an ephemeral animated ping to everyone in the *selected* authorized public or private conversation. Server enforces membership and a rate limit. It is not a real-location service.
5. **Command Wheel** — accessible from WHEEL; can also appear with a long-press on an empty portion of the chat pane.
6. **3D Map Tilt** — adjustable simulated perspective preview of your original fixed map; no live map service and no real-time coordinates.
7. **CCTV Clip Editor** — load a sample or personal video, select the start/end interval (up to 30 seconds), apply color treatments, save a CCTV-stamped frame or export a **silent WebM** clip where MediaRecorder/canvas capture is supported. Editing dates are not claimed to be the original capture time.
8. **User Dossiers** — each joined user chooses their own profile photo and status line. The browser compresses the image to a small JPEG; the server distributes only the user's chosen image during their connection. Not a login or identity-verification system.
9. **Cinematic Boot Sequence** — skippable ASE startup and reduced-motion support.
10. **Event Timeline** — recent allowed public/private messages and map events, and local session events, never data from other people's unrelated private rooms.
11. **Thermal Camera Studio** — simulated heat/night-vision filters for your **own permitted camera**; not a thermal sensor.
12. **Radio Spectrum** — an actual waveform analyzer for your own microphone, only after explicit permission; remote radio events have a visual 'on air' indicator.
13. **Surveillance Wall** — local camera (with permission), illustrative map, included video demo, and a *consensual* LIVE stream you already opened in chat. It cannot secretly open a private camera.
14. **Floating Windows** — draggable, resizable chat, map, radio and timeline widgets over the main screen. Floating chat sends to the currently selected conversation.
15. **Six simultaneous connected users** instead of three, with up to six person tabs and a six-person status roster.
16. **Click and sonar sounds**, synthesized in-browser with Web Audio, with on/off and volume controls in the Command Suite. Audio requires user interaction and obeys browser rules.

Extra local chat command shortcuts: `//COMMANDCENTER`, `//ASEOPS`, `//ASEEDITOR`, `//ASEVAULT`, `//SONAR`, `//CCTVEDITOR`, `//DOSSIER`, `//EVENTS`, `//CAMERASTUDIO`, `//SPECTRUM`, `//VIDEO-WALL`.

## Important limitations

- Messages, photo reports and map items currently live in **server memory** and can disappear when the service restarts. Markers and reports are removed when their creator disconnects, as requested earlier. Private room data is isolated by the server but **not end-to-end encrypted**.
- The vault's passphrase encrypts only **local vault data**; it does not protect ordinary chat messages. Avoid using shared browsers for personal secrets.
- Six tabs means up to six *concurrent connected browser sessions*, not six registered accounts.
- The server's `profile:update` checks that the socket owns the edited dossier. Other users can't change a profile via the profile endpoint.
- Phone browsers vary in fullscreen, MediaRecorder, sound, camera switching and WebRTC support. Calls and multi-phone streaming still need end-to-end testing on your real deployed HTTPS site.
- Black Box and Mission Archive retain their existing local storage and backup limitations.
- If Render shows `Cannot GET /`, check that `server.js` and `public/index.html` are in the correct paths and Render is running the latest successful Web Service deploy.

## Tests run during packaging

- `node --check` for server and all client JavaScript files.
- Embedded Chromium UI simulations on 390x844 portrait, 844x390 landscape and 1200x800 desktop; no page JavaScript exceptions in those runs.
- Static checks for new IDs, server room boundaries, 6-person capacity and project assets.
- The public/private events are routed by existing server membership checks. A deployed six-phone and real WebRTC/camera test is still recommended before relying on these features.
