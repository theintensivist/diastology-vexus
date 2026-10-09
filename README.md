# ICU Diastology & VExUS

A guided, single-file web app for bedside assessment in the ICU. It estimates
left-sided filling pressure and grades systemic venous congestion, then
combines both into a fluid tolerance reading and a note ready to paste into the chart.

> Decision support for trained clinicians. Not a diagnostic device.
> Do not enter patient identifiers.

## What it does

**1. Setup**: rhythm (sinus or AF), ventilation and PEEP, LV function, mitral
valve or pericardial confounders. These answers choose the algorithm.

**2. Left heart**: mitral inflow, tissue Doppler e′, TR velocity, LA volume
index, with optional timing intervals. It calculates E/A, average E/e′
(flagging the 8–14 gray zone), TR gradient and PASP, then grades filling
pressure as normal, elevated or indeterminate.

**3. VExUS**: IVC gate, then tap-to-select hepatic, portal and intrarenal
vein waveforms drawn as Doppler schematics. Outputs grade 0–3 with confounder warnings.

**4. Integrate**: a 3×3 fluid tolerance matrix (LV filling × VExUS band),
a fluid responsiveness input, and a structured chart note with one-tap copy.

## Design

- Guided flow, one question per screen, with branching that skips irrelevant steps
- "How to measure" tip, usual range and unit check on every value
- Offline-first: single HTML file, no backend, no tracking
- Inputs persist in local storage; light and dark themes
- Built-in Sources tab with DOI-linked references and a rule-to-source table

## Algorithms

- Preserved-EF screening and grading, AF criteria, MR/MS timing indices
  (ASE/EACVI 2016)
- VExUS grading rules (Beaubien-Souligny et al., 2020)
- Fluid tolerance matrix: a reasoning aid for this app, not a validated score

See the in-app Sources tab for the full reference list.

## Run locally

Open `index.html` in a browser. No build step.

## Deploy

Static hosting works as-is (Vercel, GitHub Pages, Netlify).
For installable offline use, add a web app manifest and a service worker.

## Limitations

Thresholds apply to adult transthoracic echo. Several criteria were derived
outside mechanically ventilated patients, so repeat measurements after PEEP
changes. MAC and mitral stenosis cutoffs are the least certain. Verify
against the original sources before clinical or academic use.

## License

MIT
