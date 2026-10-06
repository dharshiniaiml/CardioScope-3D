# Demo video script (target about 5 minutes; must be 3 to 10)

Rules: upload to YouTube as **Unlisted** (not Private). Speak English or add English subtitles. Show the project actually running. Record the screen with OBS or Xbox Game Bar (Win+G) and narrate.

Before recording: run `python -m http.server 8765`, open http://localhost:8765 full screen, and start from the "Midlife 55M" preset.

| Time | On screen | Say |
|---|---|---|
| 0:00–0:30 | Title and the heart | "Heart disease is the world's top killer, but risk scores reach patients as one abstract number. CardioScope 3D shows where the risk is, why, and what to do about it." |
| 0:30–1:15 | Hover and rotate the heart, point at LAD/LCx/RCA | "We predict ten-year coronary risk separately for the three main arteries and map it onto an interactive 3D heart. Colors go green to red, and plaque markers grow with risk." |
| 1:15–2:00 | Click **Healthy 35F**, then **High-risk 64M** | "Switching patients changes the whole picture: about 2% overall for a healthy 35-year-old, and about 87% for a 64-year-old smoker with diabetes. Each artery is scored on its own." |
| 2:00–3:00 | Click the RCA, show the bars | "Click an artery to see why. The model is additive in log-odds, so these contributions are exact. For the RCA, smoking and low HDL weigh more, while the LCx leans on diabetes and BMI." |
| 3:00–3:50 | What-if list, click apply on the top item, show the drop | "Here are single changes ranked by risk removed. Quitting smoking or lowering LDL drops the score immediately, and one click applies it." |
| 3:50–4:20 | Trajectory chart | "The ten-year chart compares current habits against optimized risk factors, making the benefit of acting concrete." |
| 4:20–5:00 | Show the code briefly (`index.html`: risk model, Three.js scene), then the README | "It's a single static page: a Three.js scene, an additive risk engine, and a canvas chart. No backend, so it runs anywhere." |
| 5:00–5:30 | Roadmap | "Today the coefficients are illustrative Framingham-style priors, and it is not a medical device. Next: train on UCI Heart Disease with SHAP, add ECG and CT inputs, uncertainty and fairness checks. Thank you." |

Tips
- Keep the browser zoom at 100% and the cursor slow, so viewers can follow.
- Do one rehearsal to keep it under 6 minutes.
- Say the limitations out loud, as judges reward honesty.
- Add English subtitles in YouTube Studio if your accent or audio is unclear.
