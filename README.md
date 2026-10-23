# ATLAS — Advanced Therapies Logistics & Scheduling

ATLAS is a proof-of-concept logistics and risk-monitoring dashboard designed to explore how advanced therapy shipments can be tracked across New Jersey.

The project combines **synthetic shipment data**, **public hospital information**, and **historical traffic data** to identify shipments that may be at greater risk of missing their delivery window.

> **Note:** ATLAS is an independent portfolio project. Shipment data is synthetic and does not represent Johnson & Johnson operational data.

---

## Dashboard

![ATLAS Dashboard](images/Dashboard%20Preview.png)

The Tableau dashboard provides a centralized view of shipment activity, including:

- Total shipments
- High-risk shipments
- Average remaining delivery buffer
- Shipment distribution by risk level
- Geographic shipment risk map
- Priority shipment details
- Interactive filtering by risk level and individual shipments

---

## How ATLAS Works

Each synthetic shipment is assigned a risk level using information related to:

### Timing Risk
Measures how much time remains between the estimated arrival and the shipment's delivery deadline.

Lower remaining buffer indicates greater timing risk.

### Traffic Risk
Uses historical New Jersey traffic incident data to estimate relative transportation risk by destination county.

### ATLAS Risk Score
Timing and traffic risk are combined into a single score used to prioritize shipments.

Shipments are categorized as:

- 🔴 **High Risk**
- 🟡 **Medium Risk**
- 🟢 **Low Risk**

The dashboard allows users to quickly identify shipments that may require additional attention.

---

## Data Sources

### Hospital Data

Hospital information comes from the **Centers for Medicare & Medicaid Services (CMS) Hospital General Information dataset**.

The dataset was filtered to include only hospitals located in New Jersey and provides potential shipment destinations.

### Traffic Data

Historical traffic incident data was derived from the **US Accidents dataset** and filtered to New Jersey.

Traffic information was cleaned and aggregated by county to create a relative traffic-risk measure.

### Shipment Data

Shipment records used in ATLAS are **synthetically generated for demonstration purposes**.

The synthetic data includes fields such as:

- Shipment ID
- Origin
- Destination hospital
- Destination county
- Scheduled arrival
- Estimated arrival
- Delivery deadline
- Remaining buffer
- Temperature
- Timing risk
- Traffic risk
- ATLAS risk score
- Risk level

---

## Data Pipeline

The project was built in several stages:

1. **Hospital Data Cleaning**
   - Filter CMS hospital data to New Jersey
   - Select relevant hospital and location fields
   - Prepare hospitals for use as shipment destinations

2. **Traffic Data Cleaning**
   - Filter the US Accidents dataset to New Jersey
   - Clean timestamps and missing values
   - Calculate incident duration
   - Aggregate traffic activity by county
   - Generate county-level traffic risk scores

3. **Synthetic Shipment Generation**
   - Generate 50 synthetic advanced-therapy shipments
   - Assign New Jersey hospital destinations
   - Create shipment timing information
   - Merge county-level traffic risk
   - Calculate ATLAS risk scores and risk categories

4. **Dashboard Development**
   - Build an interactive Tableau dashboard
   - Visualize shipment risk levels
   - Map destination risk geographically
   - Surface priority shipments for review

---

## Technologies

- **Python**
- **pandas**
- **Jupyter Notebook**
- **Tableau Public**
- **Git / GitHub**
- **CMS Hospital General Information**
- **US Accidents Dataset**

---

## Project Structure

```text
ATLAS/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── hospital_data_cleaning.ipynb
│   ├── traffic_data_cleaning.ipynb
│   └── shipment_generation.ipynb
│
├── dashboard/
│   ├── ATLAS_Dashboard.twbx
│
│
├── images/
│
└── README.md
```

*File and folder names may vary slightly depending on the current repository structure.*

---

## Dashboard Interactivity

ATLAS includes several interactive Tableau features:

- Select a **risk level** to filter the dashboard
- Select a **shipment location on the map** to view its corresponding shipment details
- Hover over map points to view shipment and hospital information
- Scroll through priority shipment records for additional detail

---

## Purpose

Advanced therapies can involve highly time-sensitive logistics, where transportation delays may affect the ability to deliver a therapy within its required window.

ATLAS explores how data from multiple sources could be combined into a simple operational view that helps identify:

- Which shipments require attention
- Where transportation risk may be higher
- How much delivery buffer remains
- Which shipments should be prioritized for review

The project was created as a personal proof of concept to demonstrate the use of **data engineering, risk scoring, visualization, and logistics analytics** in a healthcare-focused setting.

---

## Disclaimer

This project is an independent educational and portfolio project.

**Johnson & Johnson is not affiliated with, sponsoring, or endorsing this project.**

All shipment records are synthetic. Public datasets are used solely for analytical and demonstration purposes.