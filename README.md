# Global Vaccination Coverage Explorer
**Automated ETL Pipeline and Interactive Dashboard for Public Health Teams**

An end-to-end ETL pipeline and interactive Streamlit dashboard that automates 
the extraction, cleaning, and visualisation of global vaccination coverage data 
from OWID, UNICEF, and WHO sources. The database refreshes automatically every 
week via GitHub Actions — no manual updates required.

Built to support public health programme officers, researchers, and policy teams 
who need current, reliable immunisation data in an accessible format.

---

## The Problem This Solves

Immunisation data is scattered across multiple sources and updated periodically. 
Analysts need a single source of truth that stays current without manual 
intervention. This tool automates the full pipeline — from raw OWID data to a 
clean SQLite database to an interactive dashboard.

---

## What This Tool Produces

| Output | Description |
|---|---|
| Country and antigen trends | Interactive time-series charts filterable by country and vaccine |
| Before/after campaign analysis | Statistical testing (t-test) comparing coverage before and after campaigns |
| Executive KPI cards | High-level snapshot of coverage rates and trend direction |
| Downloadable outputs | vaccination.db, cleaned CSVs, and plots from GitHub Actions artifacts |
| Weekly automated refresh | Database updates every Monday at 03:00 UTC via GitHub Actions |

---

## Quickstart

git clone https://github.com/S-ABDUL-AI/GLOBAL-VACCINATION-COVERAGE-EXPLORER.git
cd GLOBAL-VACCINATION-COVERAGE-EXPLORER
pip install -r requirements.txt
streamlit run streamlit_app.py

---

## System Architecture

**ETL Pipeline (etl_pipeline.py)**
Extracts vaccination coverage data from OWID, cleans and transforms by antigen 
and country, loads into vaccination.db.

**Dashboard (streamlit_app.py)**
Reads from vaccination.db. Interactive filtering by country and antigen with 
Plotly visualisations and executive KPI cards.

**Automation (.github/workflows/refresh_vaccination_db.yml)**
Runs weekly every Monday 03:00 UTC. Refreshes vaccination.db and saves 
artifacts for download after each run.

---

## Repository Structure

GLOBAL-VACCINATION-COVERAGE-EXPLORER/
  streamlit_app.py              # Main Streamlit dashboard
  etl_pipeline.py               # ETL pipeline
  report_generator.py           # Report export engine
  vaccination.db                # SQLite database (auto-refreshed weekly)
  requirements.txt
  runtime.txt
  .github/workflows/
    refresh_vaccination_db.yml  # GitHub Actions CI/CD workflow
  README.md

---

## Data Sources

- Vaccination coverage: Our World in Data sourced from UNICEF and WHO
- Antigens: DTP3, MCV1, MCV2, PCV3, and related indicators
- Geographic coverage: 190+ countries

---

## About the Author

Sherriff Abdul-Hamid is a development economist and public-sector AI researcher 
applying cost-effectiveness analysis and causal inference to social protection, 
public health, and benefits delivery systems.

- Founder and Executive Director, Poverty 360 — 58,000+ beneficiaries across 
  five countries
- Partnered with Ghana NHIA to enrol 1,250 vulnerable women into national 
  health coverage
- Secured and managed multi-year institutional funding from USAID, UKAID, 
  UNDP, and USADF
- Obama Foundation Leaders Award — Top 1.3% globally, 2023
- Mandela Washington Fellow — Top 0.3%, U.S. Department of State, 2018
- Harvard Business School Senior Executive Programme

---

## Related Projects

- Medicaid Healthcare Access Risk Monitor
- Safety Net Risk Monitor
- GovFund Allocation Engine

---

## Scope Note

All built-in data is sourced from publicly available OWID/UNICEF/WHO datasets. 
Validate against national immunisation registry data for programme-level use.
