# Verra VCS Carbon Registry — Energy Industry Data Analysis

**Exploratory analysis on Verra's public carbon credit registry data**
*Focused on the Energy Industry sector (1,700 projects)*

---

## Overview

This project analyses publicly available data from the [Verra VCS Registry](https://registry.verra.org/), one of the world's largest voluntary carbon credit certification bodies. The dataset covers **1,700 Energy Industry projects** exported from Verra's registry in April 2026.

The analysis is framed as a **data quality and completeness** exercise — not an audit or critique of any organisation. All observations are exploratory and based solely on the public registry export.

---

## What's in This Repo

| File | Description |
|---|---|
| `index.html` | Interactive dashboard — live on GitHub Pages |
| `verra_eda.ipynb` | Exploratory data analysis notebook (Jupyter) |
| `verra_carbon_report_v7.pdf` | LinkedIn carousel-style PDF report (10 slides) |

---

## Live Dashboard

👉 **[View the Interactive Dashboard](https://anditarachmania.github.io/verra-carbon-registry-analysis/)**

Built with plain HTML, CSS, and JavaScript — no frameworks, no dependencies. Fully browser-based.

---

## Key Findings

- **1,700 energy industry projects** across all lifecycle stages (Pipeline → Active → Stalled → Terminated)
- **597 projects (35.1%)** carry a "Late to Verify" status — registered but with no completed verification cycle on record
- **Registration spike in 2020** — consistent with the sunsetting of the UN's Clean Development Mechanism (CDM), which prompted many CDM projects to migrate to VCS
- **Data completeness varies**: Crediting Period dates are missing for 937 projects (55%); Region classification missing for 132 (8%)
- A custom **Quality Score (0–100)** was developed based on field completeness and flags — 103 projects scored below 50 (High Risk)

---

## Methodology

### Quality Score (0–100)
Each project is scored based on field completeness:

| Field | Weight |
|---|---|
| Methodology | 20 pts |
| Registration Date | 15 pts |
| Crediting Period Start | 15 pts |
| Crediting Period End | 15 pts |
| Region | 10 pts |
| Estimated Emissions Reductions | 10 pts |
| Project Name | 5 pts |
| Proponent | 5 pts |
| Valid date order (CP Start < CP End) | +5 pts bonus |

### Risk Classification
| Tier | Count | Rule |
|---|---|---|
| High | 103 | Score < 50, OR score < 75 with 2+ data flags |
| Medium | 1,046 | Score < 75, OR Late to Verify status, OR missing CP dates |
| Low | 551 | Score ≥ 75, no critical flags |

---

## Data Source

- **Verra VCS Registry** — publicly available at [registry.verra.org](https://registry.verra.org/)
- Exported: April 2026
- Sector filter: Energy Industry
- Datasets used: All Projects, Registered, Pipeline, Inactive

> This analysis is independent and not affiliated with Verra or any carbon market organisation.

---

## About

**Andita Rachmania** | Data Analyst | Sustainability
[LinkedIn](https://www.linkedin.com/in/andita-rachmania) · [GitHub](https://github.com/AnditaRachmania)

---

*All data used is publicly available. This project is for portfolio and educational purposes.*
