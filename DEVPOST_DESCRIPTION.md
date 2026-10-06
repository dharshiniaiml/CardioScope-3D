# Devpost project description (paste into the project page)

## Project name
CardioScope 3D

## Tagline
See your heart's risk, artery by artery: explainable cardiac risk prediction on an interactive 3D heart.

## Inspiration
Heart disease is the leading cause of death worldwide, and risk scores reach patients as a single abstract number ("you're 18%"). People don't act on numbers they can't picture or understand. We wanted a tool that shows where the risk sits, why it's there, and what would change it.

## What it does
CardioScope 3D predicts 10-year coronary artery disease risk from clinical data (age, blood pressure, LDL/HDL, BMI, ST depression, smoking, diabetes, family history, exercise angina) and maps the result onto an interactive 3D heart:

- **Per-artery risk:** the LAD, LCx and RCA are each scored separately and colored green to red, with plaque markers that grow with risk.
- **Explainability:** click any artery to see exactly which factors push its risk up or down.
- **What-if simulator:** ranks single lifestyle or treatment changes (quit smoking, lower LDL, control BP) by how much risk they remove, and applies them in one click.
- **10-year trajectory:** compares future risk under current habits versus optimized risk factors.

## How we built it
- **Frontend and 3D:** Three.js. The heart is a procedural parametric surface with arteries as tube geometries routed along it. Raycasting handles artery selection and a heartbeat animation adds realism.
- **Risk engine:** an additive log-odds model with vessel-specific factor weights, so every prediction decomposes exactly into per-feature contributions, giving fully faithful explanations. Overall risk combines the vessel risks as 1 − Π(1 − p).
- **UI:** vanilla JavaScript and canvas charts. There is no backend, so it runs anywhere from a static file.

## Challenges
- Making the 3D view carry real information (per-vessel risk, plaque, selection) and not just decorate a score.
- Calibrating outputs so presets give plausible risks (about 2%, 18% and 87% for healthy, midlife and high-risk profiles).
- Keeping the explanations exact and understandable to non-experts.

## Accomplishments
A complete working flow from input to 3D prediction to explanation to action, in one lightweight page that is easy to demo.

## What we learned
Visualization changes how risk is understood. Explaining *why* matters more than the number, and counterfactuals ("what if you quit?") are what make a prediction actionable.

## Limitations (honest)
The current coefficients are illustrative Framingham-style priors, not a model trained and validated on patient data. This is decision-support demo software, not a diagnostic tool.

## What's next
Train and calibrate on UCI Heart Disease with SHAP, add multimodal inputs (ECG from PTB-XL, coronary CT), uncertainty and fairness checks, benchmark against Framingham/ASCVD scores, and swap in a segmented anatomical mesh.

## Built with
JavaScript, Three.js, HTML5 Canvas, Python (static server)

## Links
- GitHub: <paste public repo URL>
- Demo video: <paste YouTube URL (unlisted is fine, not private)>
