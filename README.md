# AI Customer Support Performance Analysis


📓 View the full analysis notebook → (ai_support_analysis)[https://github.com/AnfisaAnalytics/AI-support-analysis/blob/2de977ddf4f4d06cebccd22040f65298252d801c/ai_support_analysis.ipynb]


> **Confidentiality Notice**
> This project is based on real analytical work completed at a previous employer.
> The company name has been anonymised as **"Company X"** in accordance with confidentiality obligations.
> All data presented here is either synthetically reconstructed or fully anonymised —
> no proprietary or personally identifiable information has been disclosed.
> The analytical approach, methodology, and code are entirely my own.

---

## Project Overview

**Company X** is an AI-as-a-Service provider that deploys intelligent virtual agents to replace or augment human customer support teams — handling inbound requests via **chat, email, phone, and voice bot** channels.

As a data analyst on this project, I was responsible for evaluating the performance of multiple AI agent versions deployed across several client companies, using support ticket data as the primary source of truth.

This repository presents a full end-to-end analysis: from raw data ingestion to business impact modelling.

---

## Business Context

| Dimension | Detail |
|-----------|--------|
| **Service type** | AI-powered customer support (chat / phone / email / voice bot) |
| **Deployment model** | Multi-tenant — one AI platform, multiple client companies |
| **Geography** | Russia — 15 regions including Moscow, Saint Petersburg, Novosibirsk |
| **Analysis period** | January 2024 – June 2024 |
| **Ticket volume** | 34,200 support tickets |
| **Client industries** | Telecommunications, Banking, Logistics, E-commerce, Insurance |

---

## Repository Structure

```
├── data/
│   ├── tickets.csv          # 34,200 support tickets with full metadata
│   ├── companies.csv        # 5 client companies and their configurations
│   └── ai_agents.csv        # 4 AI agent versions with capability specs
│
├── ai_support_analysis.ipynb   # Main analysis notebook (11 sections)
└── README.md
```

---

## Dataset Description

### `tickets.csv` — 34,200 rows × 19 columns

| Column | Type | Description |
|--------|------|-------------|
| `ticket_id` | string | Unique ticket identifier |
| `company_id` / `company_name` | string | Client company |
| `industry` | string | Industry vertical |
| `ai_agent_id` / `ai_agent_name` | string | Assigned AI agent version |
| `agent_tier` | string | Lite / Pro |
| `channel` | string | chat / email / phone / voice_bot |
| `category` | string | Request type (20 categories) |
| `region` | string | Customer location in Russia |
| `created_at` / `resolved_at` | datetime | Ticket timestamps |
| `resolution_time_min` | int | Total handling time in minutes |
| `first_response_sec` | int | Time to first AI response (seconds) |
| `interaction_turns` | int | Number of back-and-forth exchanges |
| `was_escalated` | bool | Whether ticket was escalated to a human |
| `resolution_status` | string | `resolved_by_ai` / `escalated_to_human` |
| `customer_sentiment` | string | positive / neutral / negative |
| `satisfaction_score` | float | CSAT score 1–5 (~70% fill rate) |
| `complexity_flag` | bool | High-complexity ticket indicator |

### `ai_agents.csv` — 4 agent versions

| Agent | Tier | Resolution Rate | Escalation Rate | Avg Response |
|-------|------|----------------|-----------------|-------------|
| TargetAI Lite v1.0 | Lite | 77.9% | 22.1% | 18s |
| TargetAI Lite v2.0 | Lite | 80.4% | 19.6% | 14s |
| TargetAI Pro v2.0  | Pro  | 86.0% | 14.0% | 9s  |
| TargetAI Pro v3.0  | Pro  | **89.6%** | **10.4%** | **6s** |

---

## Notebook Structure

The analysis is organised into 11 sections:

| # | Section | Key Output |
|---|---------|------------|
| 1 | Environment Setup | Libraries, plot style, colour palette |
| 2 | Data Overview | Schema, missing values, descriptive stats |
| 3 | KPI Dashboard | 8 top-level performance metrics |
| 4 | Agent Comparison | 6-metric bar charts + radar chart |
| 5 | Escalation Analysis | By category, company, and channel heatmap |
| 6 | Temporal Trends | Monthly KPI lines + hour × weekday heatmap |
| 7 | Regional Analysis | Bubble chart + CSAT by region |
| 8 | CSAT & Sentiment | Score distribution, AI vs escalated, donut |
| 9 | Category Deep-Dive | Resolution time vs escalation scatter map |
| 10 | Business Impact | Cost model — ROI of agent upgrade |
| 11 | Findings & Recommendations | 7 findings, 5 actionable recommendations |

---

## Key Findings

1. **TargetAI Pro v3.0** achieves an **85.1% overall AI resolution rate** — the highest across all deployed agents.
2. Escalation rate drops from **22.1% (Lite v1.0) → 10.4% (Pro v3.0)** — a 52% reduction.
3. **Fraud alerts and transaction disputes** consistently trigger the highest escalation rates (up to 45%) regardless of agent version.
4. **CSAT for AI-resolved tickets (avg 3.85)** significantly outperforms escalated tickets (avg 2.8) — escalation hurts customer experience.
5. Ticket volume peaks on **Tuesday–Thursday, 09:00–17:00 MSK**, with weekend volume ~40% lower.
6. **Moscow and Saint Petersburg** account for 35%+ of total ticket volume — highest priority deployment regions.
7. Upgrading all Lite-tier clients to Pro v3.0 is estimated to save **$30,000+ annually** in human-agent handling costs.

---

## Tech Stack

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557C?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-4C72B0?style=flat)
![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?style=flat&logo=numpy&logoColor=white)

```
pandas      — data manipulation and aggregation
numpy       — numerical computing
matplotlib  — custom visualisations with dark theme
seaborn     — heatmaps and statistical plots
```

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/AnfisaAnalytics/ai-support-analysis.git
cd ai-support-analysis

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 3. Launch the notebook
jupyter notebook ai_support_analysis.ipynb
```

> Python 3.10+ recommended. No API keys or external services required.

---

## Skills Demonstrated

- Exploratory Data Analysis (EDA) on large-scale operational datasets
- Multi-dimensional KPI design and executive dashboard layout
- Cohort comparison and A/B-style agent performance benchmarking
- Escalation root-cause analysis by category, channel, and region
- Time series decomposition and seasonality identification
- Business impact modelling and cost-benefit analysis
- Production-quality data visualisation with custom dark theme

---

*Analysis period: Jan–Jun 2024 | Tickets analysed: 34,200 | Regions covered: 15*
