# Zombie Outbreak: Last Stand

A self-contained, offline-first 3D zombie survival game designed for GitHub hosting and later Android WebView/Capacitor packaging.

## What is included
- `index.html` entry point
- No backend, database, login, PHP, Node runtime, cloud service or API dependency
- Procedural low-poly 3D world rendered with the browser's built-in WebGL API
- Local procedural audio via Web Audio API (no copyrighted audio files)
- Offline LocalStorage save system
- Character and weapon unlocks/upgrades
- Endless wave survival with five zombie classes and bosses
- Missions, XP/levels, inventory, settings, mobile touch controls
- PWA manifest and Android-friendly relative paths

## Run locally
For the broadest WebView/GitHub compatibility, serve the folder as static files. GitHub Pages can host it directly. Gameplay does not fetch remote assets.

## GitHub
Create a repository, upload the contents of this folder, and enable GitHub Pages. The game uses only relative paths.

## Android / Capacitor workflow
1. Put this project in a Capacitor web app's web-assets directory (commonly `www/`) or configure Capacitor's `webDir` to this project directory.
2. Run the normal Capacitor Android initialization/sync commands on a development machine.
3. Open the generated Android project in Android Studio.
4. Choose a release/debug build to produce an APK, or a signed release bundle for AAB.

Typical workflow:

`Game Project → GitHub → Capacitor Android Wrapper → Android Studio → APK/AAB`

The game itself needs no server after packaging. Do not replace its relative asset paths with localhost URLs.

## App name and icon
- Change the `<title>` in `index.html` for the browser title.
- Change `manifest.json` name/short_name for the web app metadata.
- Replace `assets/icons/icon.svg` or configure the Android launcher icon during Capacitor/Android setup.
- Android's native application label/icon live in the generated Android project, not in game JavaScript.

## Controls
### Touch
- Left virtual stick: move
- Fire: shoot
- Reload: reload
- ◎: aim mode toggle
- Ⅱ: pause

### Desktop
- Left stick area can be used with pointer input; Space shoots, R reloads, Esc pauses.

## Offline save
Progress is stored locally using LocalStorage. Save data is not secure against tampering, which is expected for an offline game. Missing/corrupt data falls back to a fresh save. Reset Progress is available in Settings.

## Asset policy
The game uses original procedural geometry and generated UI/audio. No ripped characters, maps, logos, or copyrighted game music are included. This keeps the package self-contained and avoids external CDN requirements.

## Performance
The renderer uses simple low-poly geometry, a small number of dynamic entities, capped device pixel ratio, and no external 3D engine. Graphics settings are persisted as a foundation for further tuning.
