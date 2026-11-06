# NoiseLab Pro — corrected standalone build

## Fix your existing GitHub Pages website

1. Extract this ZIP.
2. In the repository serving https://kouniks.github.io/NoiseLab-Pro/, replace the existing root-level `index.html` with this ZIP's `index.html` and commit the change.
3. Wait for the GitHub Pages deployment to finish, then refresh the site with Ctrl+F5.

The app's design, code, audio processor, logo and fonts are embedded directly in `index.html`. It does not need an `assets` folder. Existing asset files may remain; this build does not use them. If you upload the whole package, keep `index.html` directly at the repository root, not inside another folder. Upload the extracted files, not the ZIP itself.

`favicon.svg` and `social.svg` are editable graphic originals. `licenses/` contains the required license notices for the embedded fonts; retain it when redistributing the package. Font license notices are also included in index.html.

## What caused the broken page

The deployed index.html was accessible, but assets/styles.css, assets/app.js and assets/meter-worklet.js returned HTTP 404 during inspection. The browser therefore displayed unstyled HTML and could not initialize the app. The fixed build eliminates those three file requests.

## Usage and measurement notes

The app opens in a clearly labelled simulated demo. Click Start microphone to measure real input. Real microphone access requires a supported browser, HTTPS or localhost, and permission. A device-specific reference-meter calibration is needed before interpreting absolute sound levels. Browser estimates are not certified compliance measurements.

Calibration profiles remain in localStorage and surveys in IndexedDB on the same website origin. Updating index.html does not change their storage keys. Exports are local CSV/JSON downloads and reports use your browser's print/PDF feature. Raw microphone audio is never uploaded or saved.

For local preview, run `python -m http.server 8000` in the extracted folder and open http://localhost:8000. Opening the HTML directly is sufficient to inspect the design and demo, but microphone features should be used over HTTPS or localhost.
