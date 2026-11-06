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


## Calibration update 1.2

Start the microphone inside Calibration lab. Allow permission, then wait for 5 seconds of real audio so the SLOW filter settles. The page now shows raw A/SLOW input, explicit input errors and why capture is unavailable. Permission failures, audio suspension, disconnection and missing samples stay visible.

For the PCE-322A: choose Steady sound · A/SLOW, select dBA and SLOW on the meter, disable HOLD/MAX/MIN and use the appropriate level range. At around 47 dB, select LOW 30–80 or AUTO, not MED 50–100. Match the app's range selector to the meter. Use a stable sound near both microphones, capture 10 seconds, enter the stable reading actually observed during capture (including its decimal), confirm the settings and click Add paired observation, then Save & activate profile. A changing FAST display or an old photograph cannot be substituted for this comparison.

Steady mode uses the energy mean of captured A/SLOW readings and rejects clipping, silence and an input spread above 2 dB. That spread threshold is a practical guard, not an IEC tolerance. An integrating instrument can instead use the separate matched-interval LAeq method. Neither mode confers an instrument class or corrects microphone frequency response. Reference-meter identity, mode, range, timestamps and confirmation are retained in saved profile observations and exported calibration snapshots.

Manufacturer reference: https://www.pce-instruments.com/english/api/getartfile?_fnr=1045398
