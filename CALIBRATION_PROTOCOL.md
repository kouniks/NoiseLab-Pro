# NoiseLab Pro — Reference Comparison and Field Validation Protocol

## Scope

A measurement screening tool requiring empirical, device-specific calibration. This document is not a claim of IEC 61672 conformity and cannot replace traceable acoustic calibration or formal sound level meter validation.

## Reference instrument and equipment

- Use a calibrated sound level meter with a current documented calibration status, preferably Class 1 or Class 2.
- Record its manufacturer/model, serial number, mode, microphone orientation, field calibrator verification, location, ambient conditions, and instrument uncertainties.
- Keep the reference meter and phone/external microphone near each other but not so close that their housings obstruct or acoustically shade each other. Position carefully to minimize spatial gradients and reflection differences.
- Prefer stable broadband/steady acoustic conditions; a controlled source is better than rapidly varying traffic noise when learning the sensitivity offset.
- Document microphone placement, orientation, reference measurement duration and software/browser/OS build.

## Compare the same quantity

1. Reference SLM: A frequency weighting, *equivalent continuous level* LAeq over **exactly the same 10-second capture interval**. Do **not** enter an instantaneous FAST reading as if it were 10-second LAeq.
2. NoiseLab: start microphone, check settings, input reference LAeq, and collect 10 seconds of continuously weighted digital samples.
3. Digital level: `10 log10( Σ x_A^2 / n ) dBFS` where `x_A` is an A-weighted normalized Web Audio sample.
4. Offset = `reference LAeq (dB(A)) − digital A-weighted level (dBFS)`. This converts the displayed digital scale to an empirical sound-level estimate for the paired measurement conditions.
5. Repeat across multiple independent level steps to investigate nonlinearity. Save the median paired offset and inspect the **full spread**; a spread above 2 dB triggers an app warning (a software QC heuristic, **not** a standard tolerance).
6. Keep independent verification runs at multiple levels and locations, ideally including real roadway sound, tonal sound, broadband sound and low-frequency-rich noise. Do not use the same captures for both fitting and claiming validation.
7. Estimate mean bias, mean absolute error, RMSE, limits of agreement and uncertainty against the certified reference across conditions in your independent research analysis.

## Calibration limitations

- The app's calibration is a **reference-meter comparison**, not a pressure calibration using a traceable microphone sensitivity and compatible acoustic coupler.
- A sound level calibrator designed for IEC measurement microphones cannot be assumed to fit a smartphone microphone.
- A constant offset cannot repair a distorted frequency response, automatic gain control, compressor or clipping.
- Good performance against one source and one level does not establish Class 1/2 or compliance reliability.
- Any change to microphone, device, browser sample rate, AGC, sound card gain or audio interface invalidates the assumed measurement chain and should trigger new tests.

## Minimum field metadata

Sample/site ID, GPS (when permitted), instrument identities, current calibration verification, sound source/context, A/C/Z weighting, FAST/SLOW mode, clock/time zone, actual duration, weather/wind, monitoring height, device orientation, obstructions, notes, and reference / test sound levels when possible.

## Interpretation

The outdoor standards displayed in the app are an **indicative reference only**, using Indian industrial/commercial/residential/silence-zone day/night limits in dB(A) Leq. Confirm prescribed monitoring protocol, time period, authorized area classification, and applicable legislation before making legal conclusions.

## Suggested validation study

- Repeat at least 3–5 sound levels across a research-relevant range with >=3 repeated runs per level on each device.
- Use at least 2–3 distinct spectral conditions, including traffic, broadband and tonal sound.
- Test at least 3 different smartphones plus one compatible external microphone, where practical.
- Separate calibration and validation observations.
- Examine reference minus app bias, MAE, RMSE, noise floor, clipping, spectral response, orientation, and wind sensitivity.
- Report full hardware/software versions, reference instrument specifications, sampling procedure, discrepancies and uncertainties.

## Sources

NIOSH: https://www.cdc.gov/niosh/noise/about/app.html  
MDN: https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API  
CPCB: https://cpcb.nic.in/displaypdf.php?id=Tm9pc2UtU3RhbmRhcmRzL25vaXNlX3J1bGVzXzIwMDAucGRm
