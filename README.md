# AirGuitar — Virtual Air Guitar (Android-ready PWA prototype)

This project is a mobile-first virtual guitar prototype. It uses the phone's front camera and MediaPipe Hand Landmarker (2 hands) to track index fingertips, draws six neon strings, and triggers plucked-string synthesized tones when a fingertip crosses a string. Chord buttons change the six-string tuning/harmony.

## Run on Android

1. Host this folder on an HTTPS static host (GitHub Pages, Netlify, or a secure local development server). Camera access requires a secure context (HTTPS; `localhost` is also allowed).
2. Open the site in Chrome on Android and grant camera permission.
3. Tap **Start camera**, then show your hand(s). Move an index fingertip across one of the six strings to pluck it.
4. Use the chord buttons to change the harmony. Use **Sound: ON/OFF** to mute.
5. In Chrome, use **⋮ → Add to Home screen** / **Install app** to install it as a home-screen app.

## Notes and limitations

- This is a working prototype, not a compiled native APK. It requires internet on first load to download the MediaPipe JavaScript/WASM runtime and hand-landmarker model from their public CDNs. Once cached, the app shell can open offline, but model/runtime caching may still depend on the browser cache.
- Camera inference is performed locally in the browser; camera frames are not uploaded by this app.
- Current prototype uses the index fingertip crossing a string as the pluck gesture and selectable chord presets. It does not yet infer guitar fretboard finger placements or reproduce recorded acoustic-guitar samples. Tones are synthesized plucked-string sounds.
- For a store-quality native app, package the same experience with Android Studio/Gradle and use a native MediaPipe Tasks Vision integration plus a low-latency audio engine.

## Files

- `index.html` — user interface
- `app.js` — MediaPipe tracking, string crossing detection, audio synthesis and effects
- `manifest.webmanifest` — installable web app metadata
- `sw.js` — app-shell service worker
