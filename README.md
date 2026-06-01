# Emploiroire – Ireland Employment Statistics Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Release v1.0](https://img.shields.io/badge/release-v1.0-brightgreen)](https://github.com/your-org/emploiroire/releases/tag/v1.0)

**Emploiroire** is an open‑source, data‑driven dashboard and API that brings together the most important Irish labour‑market indicators in one place.  

It is built on the 2024/25 Employment Statistics in Ireland research report and allows policymakers, researchers, journalists and jobseekers to explore types of employment, unemployment profiles, activation schemes, and re‑employment outcomes through interactive visualisations and downloadable datasets.

---

## Overview

Ireland’s labour market is complex – high employment rates, low headline unemployment, but persistent youth and long‑term joblessness, regional disparities, and a wide array of government activation schemes. Emploiroire makes that complexity transparent by:

- Aggregating official data from the CSO, DSP, SOLAS and evaluation reports.
- Normalising it into a unified, versioned SQLite database.
- Providing a **React + D3.js** web dashboard and a **Python/Flask API**.
- Including the full research report as structured Markdown.

The project was launched to give a living, updatable companion to the static research report, enabling real‑time filtering, scheme comparison, and downloadable re‑employment flow tables.

---

## Features (v1.0)

### 📊 Interactive Dashboard
- Headline metrics: employment rate (74.6%), unemployment rate (4.2%), youth unemployment, NEET.
- Sectoral employment share pie/bar charts.
- Regional unemployment heatmap (NUTS‑3 regions).
- Part‑time/full‑time and temporary contract breakdowns.

### 📈 Activation Scheme Explorer
- Compare all major schemes (CE, Tús, JobsPlus, WPEP, JobPath, etc.) by:
  - Participant numbers
  - Progression‑to‑employment rates
  - Budget allocation per participant
- Visualise the “jobseeker universe”: Live Register + activation participants (21% on schemes).

### ⏳ Re‑employment Dynamics
- Sankey diagrams of quarterly flows: unemployed → employed, inactive, or still unemployed.
- Median duration of unemployment and monthly outflow to employment from the Live Register.

### 📥 Data Export
- Download any chart’s underlying data as CSV/JSON.
- Full database snapshot available as SQLite file in the release assets.
- API endpoints for programmatic access (see below).

### 📝 Embedded Research Report
- The complete “Employment Statistics in Ireland” report is included as a navigable documentation site (via Docusaurus) with in‑line, live‑linked charts.

### 🌐 REST API (v1)
- `GET /api/v1/headlines` – latest macro indicators.
- `GET /api/v1/schemes` – list of schemes with success rates.
- `GET /api/v1/flows?from=Q1_2024&to=Q2_2024` – labour market flows.
- All endpoints return GeoJSON‑ready regional data where applicable.

---

## Roadmap

### ✅ v1.0 (Current Release)
- Core dashboard with static 2023‑2024 data.
- Activation scheme comparison tool.
- PDF‑generated research report.
- Basic REST API.

### 🔜 v1.1 – “Live Data Taps”
- Scheduled scraping/APIs from CSO PxStat and DSP monthly reports.
- Auto‑update of charts and data snapshots.
- Email alerts when unemployment changes >0.3pp.

### 🗺️ v1.2 – Advanced Geospatial & Demographics
- County‑level employment estimates (beyond NUTS‑3).
- Drill‑down by age, gender, and nationality.
- Interactive “commuting zones” view.

### 🔮 v1.3 – Forecasting & What‑If
- Simple ARIMA/prophet‑based unemployment forecast.
- “What‑if” calculator for scheme scaling (e.g., doubling WPEP places).
- Integration with Pobal HP Deprivation Index.

### 📦 v2.0 – Community Contributions & Multi‑country
- Plugin system for new datasets (e.g., job postings from Indeed/OECD).
- Expand to Northern Ireland labour market for all‑island view.
- Mobile‑friendly PWA.

We welcome contributions! Check the [CONTRIBUTING.md](CONTRIBUTING.md) for how to get involved.

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React (TypeScript), D3.js, Leaflet |
| Backend | Python 3.12, Flask, SQLAlchemy |
| Database | SQLite (v1), planned migration to PostgreSQL |
| Deployment | Docker, GitHub Actions CI/CD |
| Documentation | Docusaurus 2 |

---

## Getting Started

1. Clone the repo:  
   `git clone https://github.com/your-org/emploiroire.git`
2. Install backend: `cd backend && pip install -r requirements.txt`
3. Start API: `flask run`
4. Install frontend: `cd frontend && npm install`
5. Launch dashboard: `npm run dev`
6. Visit `http://localhost:5173` and explore the data.

For Docker users:  
`docker compose up` will start both services.

---

## License

Distributed under the MIT License. See `LICENSE` for more information.  
The underlying data is primarily from Irish public sector bodies (CSO, DSP) and is used under their open data licences.

---

**Maintained by Transparency-X**  
*Built to support evidence‑based discussion on Irish employment policy.*
