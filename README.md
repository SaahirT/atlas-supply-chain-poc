# ATLAS — Advanced Therapies Logistics & Scheduling

ATLAS is a proof-of-concept logistics and risk-monitoring dashboard created to explore how data and visualization could support **Johnson & Johnson Advanced Therapies Supply Chain (ATSC)** operations.

The project combines **synthetic shipment data**, **public hospital information**, and **historical New Jersey traffic data** to identify time-sensitive shipments that may require additional attention.

> **Note:** ATLAS is an independent portfolio project and does not use Johnson & Johnson operational data. All shipment records are synthetic.

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
- Interactive filtering by risk level
- Individual shipment selection through the map

---

## Why I Built ATLAS

The idea for ATLAS came from my experience working as an Uber Eats delivery driver.

Traffic was one of the biggest challenges I encountered. A trip that should have taken twenty minutes could quickly become forty because of an accident, roadwork, or unexpected congestion. Over time, I began learning which roads to avoid, when certain areas became congested, and which alternate routes could save time.

That experience showed me how valuable transportation data can be when something needs to arrive on schedule.

When I learned more about **Advanced Therapies Supply Chain**, I saw a much more important version of that same logistics problem. Advanced therapies can involve a complex journey between treatment centers and manufacturing operations before ultimately reaching the patient. Unlike food delivery, a process this sensitive cannot depend on someone simply knowing the best route. Operations teams need data that can help identify potential issues early and support informed decision-making.

That led me to build **ATLAS — Advanced Therapies Logistics & Scheduling**.

The goal is not to recreate Johnson & Johnson's actual supply chain. Instead, ATLAS explores how logistics data, historical transportation patterns, and dashboarding could be combined to help an operations team quickly understand what is happening and which shipments may need attention.

---

## Core Question

ATLAS was designed around one simple question:

> **Which shipments may be at risk and require attention?**

The project combines timing and transportation information to create a simple risk-monitoring view.

For example, a shipment with a limited remaining delivery buffer traveling toward a county with relatively higher historical traffic risk may receive a higher ATLAS risk score.

---

## How ATLAS Works

### 1. Timing Risk

Each shipment includes:

- Scheduled arrival
- Estimated arrival
- Delivery deadline
- Remaining delivery buffer

A smaller remaining time buffer represents greater timing risk.

---

### 2. Traffic Risk

Historical New Jersey traffic incidents are aggregated by county to create a relative transportation-risk measure.

Factors in the traffic dataset include information such as:

- Accident location
- County
- Start and end time
- Severity
- Weather conditions

The original traffic dataset contains approximately **7.7 million U.S. traffic incidents**, which was filtered to New Jersey for this project.

---

### 3. ATLAS Risk Score

Timing risk and traffic risk are combined into a single **ATLAS Risk Score**.

Shipments are then grouped into simple operational categories:

- 🔴 **High Risk** — shipment may require attention
- 🟡 **Medium Risk** — possible delay or reduced delivery buffer
- 🟢 **Low Risk** — shipment appears to be on schedule

These categories are intended to make it easier for an operations team to quickly prioritize shipments.

---

## Data Sources

### Hospital Data

**Source:** Centers for Medicare & Medicaid Services (CMS)  
**Dataset:** Hospital General Information

CMS provides public information on thousands of Medicare-registered hospitals across the United States.

For ATLAS, the data was filtered to hospitals located in **New Jersey** and reduced to relevant fields such as:

- Facility ID
- Hospital name
- Address
- City
- County
- ZIP code

These hospitals serve as possible destinations for the synthetic shipments.

---

### Historical Traffic Data

**Source:** US Accidents Dataset  
**Original dataset:** approximately 7.7 million U.S. traffic incidents

The dataset was filtered to New Jersey and cleaned to retain relevant transportation information.

Traffic incidents were then aggregated by county to estimate relative transportation risk.

---

### Synthetic Shipment Data

Real medical shipment data is private, so ATLAS uses a **synthetically generated shipment dataset**.

The current proof of concept contains **50 synthetic shipments** originating in New Jersey and traveling to hospital destinations throughout the state.

Each shipment includes fields such as:

- Shipment ID
- Origin
- Destination hospital
- Destination county
- Scheduled arrival
- Estimated arrival
- Delivery deadline
- Remaining delivery buffer
- Package temperature
- Timing risk score
- Traffic risk score
- ATLAS risk score
- Risk level

Using synthetic shipment data allows the dashboard to demonstrate the logistics concept without using confidential company information.

---

## Project Methodology

### Step 1 — Clean Hospital Data

The CMS Hospital General Information dataset was:

- Filtered to New Jersey
- Reduced to relevant hospital and location fields
- Cleaned for use as shipment destinations

---

### Step 2 — Clean Traffic Data

The US Accidents dataset was:

- Filtered to New Jersey
- Reduced to relevant traffic fields
- Cleaned for missing values and timestamps
- Used to calculate incident duration
- Aggregated by county
- Converted into relative county-level traffic risk scores

---

### Step 3 — Generate Synthetic Shipments

A synthetic shipment dataset was created with:

- New Jersey hospital destinations
- Scheduled arrival times
- Estimated arrival times
- Delivery deadlines
- Remaining delivery buffers
- Temperature values

Traffic risk was then merged into each shipment based on destination county.

---

### Step 4 — Calculate Shipment Risk

Timing and traffic information were combined to calculate an **ATLAS Risk Score**.

Each shipment was classified as:

- High Risk
- Medium Risk
- Low Risk

The resulting dataset became the source for the Tableau dashboard.

---

### Step 5 — Build the Dashboard

The final Tableau dashboard brings the different sources together into one operational view focused on:

- Shipment volume
- At-risk shipments
- Remaining delivery buffer
- Shipment risk distribution
- Hospital destinations
- Geographic transportation risk
- Priority deliveries

The goal is to turn several different data sources into a simple dashboard that helps an operations team understand **what is happening, what may become a problem, and where action may be needed**.

---

## Dashboard Interactivity

ATLAS includes several interactive Tableau features:

- Click a **risk level** to filter shipments
- Click an individual **map pin** to isolate the corresponding shipment
- Hover over map points to view shipment and destination information
- Review shipment risk directly in the priority table
- Scroll through shipment records for additional detail

---

## Technologies

- **Python**
- **pandas**
- **Jupyter Notebook**
- **Tableau Public**
- **Git**
- **GitHub**
- **CMS Hospital General Information**
- **US Accidents Dataset**

---

## Project Structure

```text
atlas-supply-chain-poc/
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
│   └── ATLAS_Dashboard.twbx
│
├── images/
│   └── Dashboard Preview.png
│
└── README.md
```

*Exact file names may vary slightly as the project evolves.*

---

## Purpose

ATLAS was created as a personal proof of concept while I was preparing for an interview for a **Johnson & Johnson Advanced Therapies Supply Chain (ATSC) co-op**.

I wanted to go beyond simply researching the role and instead build something that helped me better understand the kinds of logistics and operational challenges an advanced therapies supply chain team may encounter.

The project allowed me to explore how several areas of data work can come together in a real operational use case:

- Data cleaning
- Data integration
- Synthetic data generation
- Risk modeling
- Transportation analytics
- Geographic visualization
- Dashboard development
- Operational decision support

Most importantly, the project focuses on the idea that data is most useful when it helps someone identify a potential problem early enough to act.

ATLAS is not intended to recreate Johnson & Johnson's actual supply chain. It is an independent learning project built to better understand the role, the business problem, and how data could support decision-making in a time-sensitive logistics environment.

---

## Disclaimer

ATLAS is an independent educational and portfolio project.

**Johnson & Johnson is not affiliated with, sponsoring, or endorsing this project.**

The project does not contain confidential or proprietary Johnson & Johnson information. All shipment records are synthetic, and external datasets used in the project are publicly available.