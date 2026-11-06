# NoiseLab Pro

Environmental sound monitoring and field-survey web app for Kounik De Sarkar.

## Upload to GitHub

1. Extract `NoiseLab_Pro_GitHub.zip`.
2. Upload **all extracted contents** to your repository, preserving the `assets` folder.
3. Keep `index.html` at the repository root, alongside this README.
4. Enable GitHub Pages to serve the repository root from your chosen branch.
5. Open the resulting HTTPS website. No build or package installation is needed.

Deployment documentation: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## Included files

- `index.html` — complete application interface
- `assets/styles.css` — responsive styling
- `assets/app.js` — microphone, charts, calibration, surveys, GPS, exports and reports
- `assets/meter-worklet.js` — continuous audio signal processing
- `favicon.svg` — application logo and browser icon
- `social.svg` — social graphic source
- `.nojekyll` — serves this static app without Jekyll processing
- `README.md` — deployment and usage notes

## Use

The app opens in clearly labelled demo mode. Click **Start microphone** for real measurements, then use **Calibration lab** to create a device-specific reference profile. Use **Start survey** and **Finish & save** to store a session. Saved surveys support CSV export and printable reports. JSON backup exports all saved surveys and profiles.

Microphone and GPS access require a supported browser, HTTPS (or localhost), and permission. Raw audio is never saved or uploaded. Records are stored in the current browser, so export backups before clearing site data. Measurements saved on another website address are not automatically carried over to your GitHub Pages address.

Keep the tab visible while recording: hiding it stops and saves the survey to protect measurement timing. Microphone disconnection or audio suspension also stops recording.

Optional Google Fonts are loaded when internet access permits; system fonts are used otherwise. The app does not require any external JavaScript libraries.

## Local preview

Run from this folder:

```sh
python -m http.server 8000
```

Then open http://localhost:8000 in your browser. Use a local server rather than opening index.html directly, because the AudioWorklet needs a proper web origin.

## Social previews

The included social.svg is editable artwork. For reliable WhatsApp and other social previews, export it to a 1200 × 630 PNG and update og:image and twitter:image in index.html to that PNG's absolute published HTTPS URL. SVG social previews are not supported consistently.

## Measurement limitations

Browser readings are research-support estimates, not certified IEC 61672 measurements. Absolute sound pressure levels require reference-meter calibration and validation of the complete microphone/device/browser setup. The A/C digital filters use a bilinear approximation normalized at 1 kHz; the empirical sensitivity offset does not correct microphone frequency response. The same offset is used for A, C and Z. Statistical levels and extrema are based on sampled FAST readings. Ambient-noise reference values do not establish compliance.

Demo recording, saved-record persistence, CSV downloading and report rendering were tested. DSP checks covered normalization, low-frequency weighting, timing and clipping at 44.1 and 48 kHz. Actual microphone sensitivity and physical reference-meter calibration still require hardware validation.
