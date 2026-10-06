# CardioScope 3D

**Explainable coronary artery disease risk, mapped onto an interactive 3D heart.**
Built for the Multimodal AI Hackathon 2026, Track A: Cardiovascular Risk Visualization & Prediction.

CardioScope 3D takes a patient's physiological and clinical data and predicts the 10-year risk of coronary artery disease (CAD) for each of the three main coronary arteries (LAD, LCx, RCA) plus an overall cardiac risk. The predictions are drawn directly on an interactive 3D anatomical heart model, colored by risk, with plaque markers that grow as risk rises. Clicking an artery explains exactly which factors drive its score.

> **Status / honesty note:** this is a hackathon prototype. The risk model uses illustrative Framingham-style coefficients, not a model trained and clinically validated on patient data. It is decision-support demo software, **not a medical device and not a diagnosis.** See [Roadmap](#roadmap).

## Features

- **3D anatomical visualization:** beating heart with LAD, LCx and RCA, rotate/zoom, click-to-select (Three.js).
- **Per-artery risk:** each vessel has its own risk, driven by different factor weightings (for example smoking and low HDL weigh more on the RCA, diabetes and BMI on the LCx).
- **Explainability:** the model is additive in log-odds, so every feature's contribution is exact and shown as a diverging bar chart for the whole heart or a selected artery.
- **What-if simulator:** lists the risk reduction from single changes (quit smoking, LDL to 100, BP to 120, BMI to 25, HDL to 50) with one-click apply.
- **10-year trajectory:** projected risk under current habits vs. optimized risk factors.
- **Presets:** Healthy 35F, Midlife 55M, High-risk 64M for quick demos.

## Inputs

| Type | Fields |
|---|---|
| Continuous | Age, systolic BP, LDL, HDL, BMI, ST depression |
| Flags | Male sex, smoker, diabetes, family history, exercise angina |

## How it works

1. Each feature's deviation from a reference value is multiplied by a weight (and a vessel-specific multiplier).
2. Per-vessel log-odds = vessel offset + sum of contributions, converted with a sigmoid to a probability.
3. Overall risk = 1 − Π(1 − p<sub>vessel</sub>).
4. The 3D scene maps each vessel's probability to color (green → red) and plaque count/size.
5. The what-if and trajectory views re-run the same model on modified inputs.

Because the model is additive, attribution is exact, with no approximation as in SHAP on tree models. Training a non-linear model is on the roadmap, where SHAP would be used.

## Prerequisites

- A modern browser (Chrome, Edge, Firefox) with WebGL enabled
- Internet access on first load (Three.js is loaded from a CDN)
- *Optional:* Python 3 (any version) for a local web server

No build step, no `npm install`, no API keys.

## Setup and run

```bash
git clone https://github.com/<your-username>/cardioscope-3d.git
cd cardioscope-3d
python -m http.server 8765
```

Then open <http://localhost:8765> in your browser.

You can also simply double-click `index.html`, though serving it over HTTP is more reliable across browsers.

## Using the app

1. Click a preset (top right) or move the sliders and flags on the left.
2. Watch the arteries recolor and plaque appear in the 3D view.
3. Click an artery (or its card on the right) to see why it scores what it does.
4. Use the what-if list to see which change helps most, and the trajectory chart for the 10-year effect.

## Project structure

```
index.html   # entire app: risk model, 3D scene (Three.js), UI
README.md
```

## Roadmap

- Train and calibrate a model on UCI Heart Disease (Cleveland) and report AUC/calibration; add SHAP for non-linear models.
- Multimodal input: ECG signals (PTB-XL) and imaging (coronary CT) alongside tabular data.
- Uncertainty bands and fairness checks across sex and age groups.
- Replace the procedural heart with a segmented anatomical mesh.
- Benchmark against Framingham/ASCVD pooled cohort scores.

## Disclaimer

For education and demonstration only. Not for clinical use. Do not use it to make medical decisions.

## Team

<!-- Replace with real full names, matching the Devpost submission -->
- Full Name 1
- Full Name 2

## License

MIT, see `LICENSE` (add one before publishing).
