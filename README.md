# SZC Studio — iPad Edition

An offline-first Progressive Web App for editing and compiling the current SZC language prototype on iPad.

## What works
- Browser-based SZC code editor
- Local project storage in browser localStorage
- Create and switch between `.szc` files
- Import `.szc` source files through the iPad Files picker
- Compile current implemented SZC subset to an iframe preview
- Compiler error output
- Download individual `.szc` source files
- Export current project as ZIP
- PWA manifest and service worker for offline app shell
- Responsive iPad/tablet/mobile layout

## Requirements
- Modern Safari
- Node.js is not required on the iPad because the compiler prototype runs in JavaScript in the PWA.
- To install as a PWA, serve this folder from HTTPS. Service workers do not work from arbitrary `file://` URLs.

## Install on iPad
1. Host this folder on a static HTTPS host, or run it from a local HTTPS development server.
2. Open the HTTPS address in Safari.
3. Tap Share → Add to Home Screen.
4. Launch SZC Studio from the Home Screen.
5. Open it once while online so the app shell is cached. The editor/compiler then work offline.

## Local testing on a computer
Use any static web server, for example:
```bash
python3 -m http.server 8080
```
Then open `http://localhost:8080`. Service worker support on localhost is permitted by browsers. For actual iPad installation over a network, use HTTPS.

## Important limitations
- This is a PWA, not a native iPadOS app.
- It compiles the current SZC prototype subset only. Full language semantics, complete HTML/CSS/JS compatibility, backend execution, AI integrations and native builds are not implemented yet.
- Project data is stored in this browser's local storage. Export ZIP backups regularly. Clearing Safari website data can remove local projects.
- Large media assets and very large projects are not recommended on a 64 GB iPad.
- Browser preview is sandboxed. Do not add private API keys to client-side source code.

## Validate the bundled compiler
On a computer with Node.js 18+, run:
```bash
node tests/compiler-smoke.mjs
```
