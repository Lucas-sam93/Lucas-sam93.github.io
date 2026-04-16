# Lucas Sam — Data Analyst

I'm a data analyst who enjoys turning raw data into clear, actionable insights. I work across the full pipeline — from cleaning and exploring datasets to building ML models, interactive dashboards, and web tools that make the results accessible to others.

This is my portfolio. Each project below has a full case study behind it — methodology, model selection rationale, trade-offs, and results. Click through on the live site to read them.

**[lucas-sam93.github.io](https://lucas-sam93.github.io)**

---

## Projects

| # | Project | What it does | Stack | Key result |
|---|---------|--------------|-------|------------|
| 1 | [Heart On Your Wrist](#1-heart-on-your-wrist) | ML cardiac screening from wearable ECG/PPG signals | Python · scikit-learn · FastAPI · Pandas | 0.91 AUROC · 84.4% sensitivity |
| 2 | [W.O.W. — Worth-Or-What?](#2-wow--worth-or-what) | HDB resale price estimator + town recommender | Python · LightGBM · Flask · Pandas | 95.13% R² · 99.71% accuracy |
| 3 | [JD-Match](#3-jd-match) | Resume-to-job-description alignment scorer | React · Vite · Tailwind · Node.js · Gemini API | Live tool |
| 4 | [SG Elections 1955–2025](#4-singapore-parliamentary-elections-19552025) | 70-year election data story across 6 dashboards | Tableau | Live dashboard |
| 5 | [Gender Pay Gap Analysis](#5-gender-pay-gap-analysis) | UK glass ceiling explorer with custom GCI metric | SQL · BigQuery · Python · Plotly · Pandas | 82,935 submissions · 8 years |

---

### 1. Heart On Your Wrist

Cardiovascular disease kills 22 Singaporeans daily, yet 49% of residents skip annual checkups. This project asks whether a $300 smartwatch can flag cardiac risk as reliably as a $3,000 clinical ECG.

Trained an SVM classifier on 8,187 clinical ECG recordings — selecting it over Logistic Regression, Random Forest, and XGBoost using a five-criterion framework — and validated signal transfer across two wearable modalities (MIMIC finger PPG and Apple Watch). The clinical model achieved **0.91 AUROC** and **84.4% sensitivity**. When applied to wearable PPG, threshold recalibration via Youden's J recovered specificity from 12.5% to 93.8%, confirming the gap is a calibration problem, not a discrimination failure.

Deployed as **BeatCheck**, a FastAPI screening tool that accepts Apple Health exports and returns cardiac risk tiers (Low / Intermediate / High).

`Python` `scikit-learn` `FastAPI` `NeuroKit2` `Pandas` `WFDB` `Jupyter`

[Source code](https://github.com/Lucas-sam93/ga-capstone-heartbeat-or-noise)

---

### 2. W.O.W. — Worth-Or-What?

Singapore's HDB resale market is opaque. A buyer's offer lives or dies on agent intuition. This project replaces that with a data-backed price range and a personalised town recommendation — trained on 270,620 transactions across 26 towns and 76 features.

Led as Product Manager on a 7-person team. LightGBM was chosen over XGBoost for price regression — its faster inference and better train-test gap (0.0013) made it the right call for a production web app. Town recommendation runs in two stages: K-Means profiles the 26 towns on lifestyle features, then a LightGBM classifier matches users to clusters. The price estimator hit **95.13% R²** (RMSE $38,508); the town recommender hit **99.71% accuracy** at 11.23-second runtime.

`Python` `LightGBM` `Flask` `scikit-learn` `K-Means` `Pandas` `NumPy`

---

### 3. JD-Match

A resume-to-job-description alignment tool powered by Google's Gemini API. Upload a resume, paste a job description, get a score across 15 categories, missing keywords flagged, and rewritten bullet points you can apply in one click — in under 5 seconds.

`React` `Vite` `Tailwind CSS` `Node.js` `Gemini API`

[Live app](https://jd-match.vercel.app) · [Source code](https://github.com/Lucas-sam93/JD-Match)

---

### 4. Singapore Parliamentary Elections 1955–2025

70 years of Singapore elections across 6 Tableau dashboards. The Workers' Party wins more than half the votes in every seat they contest — yet holds 9.3% of parliament. Built to show why the quiet revolution is already happening, hidden by a structural bottleneck.

`Tableau` `Data Visualization` `Data Storytelling`

[Live dashboard](https://public.tableau.com/app/profile/lucas.sam4725/viz/SingaporeParliamentaryElections19552025/D1-TheParadox) · [Source code](https://github.com/Lucas-sam93/SG-Elections-Tableau)

---

### 5. Gender Pay Gap Analysis

Queried 82,935 mandatory UK employer submissions (10,409 unique companies) from the Government Gender Pay Gap Reporting Service via Google BigQuery. Developed a custom metric — the **Glass Ceiling Index** (GCI = female% in bottom quartile minus female% in top quartile) — to measure structural progression inequality rather than headline pay differences.

Women's representation drops 13+ percentage points from entry-level to senior roles. Finance is worst; Care is near-parity. 1,617 companies (15.5% of 2025 reporters) have already achieved GCI parity — the "1% Club." Built an interactive dashboard to let users explore the data by sector, year, and company size.

`SQL` `BigQuery` `Python` `Plotly` `Pandas`

[Live dashboard](https://lucas-sam93.github.io/gender-pay-gap-analysis/) · [Source code](https://github.com/Lucas-sam93/gender-pay-gap-analysis)

---

## About this site

Single-page static site. The entire thing — CSS, JavaScript, and HTML — lives in one file: `index.html`. No framework, no build step, no bundler.

**Structure**

```
lucas-sam93.github.io/
├── index.html              # Everything: markup, embedded CSS, embedded JS
├── assets/
│   ├── *-screenshot.png    # Project preview images
│   ├── Lucas_Headshot.png
│   └── og-image.png        # Open Graph preview
└── Lucas_Sam_Resume.pdf
```

**Frontend**
- Vanilla HTML5, CSS3, and JavaScript (ES6+)
- GSAP 3 + ScrollTrigger — sticky pinning, scroll-driven parallax, reveal animations
- Lenis — smooth scroll (with modal scroll isolation)
- Google Fonts: Koulen (display), Inter (body), Roboto Mono (labels/tags)

**Design**
- Dual dark/light theme via CSS custom properties on `[data-theme]`, auto-detected from `prefers-color-scheme` and persisted via `localStorage`
- Custom cursor with hover expansion
- Particle canvas hero
- Project modals with `clip-path` curtain reveal and `history.pushState` back-button support
- Accent: `#ccbb87` gold tone (dark) / `#8a7a4a` (light)

**Deployment**
- GitHub Pages, served directly from the `main` branch root — no CI, no build pipeline

---

## Running locally

No build step required.

```bash
git clone https://github.com/Lucas-sam93/Lucas-sam93.github.io.git
cd Lucas-sam93.github.io
```

Then open `index.html` in a browser. That's it.

If you want a local server (avoids some browser fetch restrictions):

```bash
# Python
python -m http.server 8000

# Node.js
npx serve .
```

---

## Get in touch

I'm always open to connecting with other analysts, developers, and anyone working on interesting problems.

[GitHub](https://github.com/Lucas-sam93) · [LinkedIn](https://www.linkedin.com/in/lucas-sam-54aba3106) · [Email](mailto:lucas.sam93@gmail.com)
