# 🚖 Automatidata × NYC TLC — Taxi Fare Prediction
> **Google Advanced Data Analytics Certificate | Capstone Project**  
> Completed by **Subham Joshi** | Data Operations Analyst

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0-green?logo=pandas)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)](https://jupyter.org/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen)]()
[![Certificate](https://img.shields.io/badge/Google-Advanced%20Data%20Analytics-4285F4?logo=google)]()

---

## 📌 Project Overview

This project simulates a real-world data analytics engagement at **Automatidata**, a data consulting firm contracted by the **New York City Taxi & Limousine Commission (TLC)**. The goal is to build a regression model that **predicts taxi fares before the ride begins**, enabling riders to make informed decisions.

The analysis follows the **PACE** workflow — *Plan, Analyze, Construct, Execute* — as taught in the Google Advanced Data Analytics Certificate.

---

## 🎯 Business Problem

> *"How accurately can we predict a taxi fare before a ride begins, using only pre-trip information?"*

TLC processes **~1 million trips per day** across 200,000+ licensees. A reliable pre-ride fare estimator would:
- Build **rider trust** and reduce fare disputes
- Enable **dynamic pricing transparency**
- Provide data-driven support for **regulatory decisions**

---

## 📂 Repository Structure

```
automatidata-nyc-tlc/
│
├── automatidata_tlc_analysis.ipynb   # Main Jupyter notebook (EDA + findings)
├── 2017_Yellow_Taxi_Trip_Data.csv    # Dataset — NYC TLC Yellow Taxi, Jan 2017
├── README.md                         # This file
└── executive_summary.docx            # Non-technical summary for TLC stakeholders
```

---

## 📊 Dataset

| Property | Value |
|----------|-------|
| Source | NYC Taxi & Limousine Commission (TLC) |
| Period | January 2017 |
| Records | 22,699 rows |
| Features | 19 columns |
| Format | CSV |

**Key columns:**

| Column | Type | Description |
|--------|------|-------------|
| `tpep_pickup_datetime` | DateTime | Ride start timestamp |
| `tpep_dropoff_datetime` | DateTime | Ride end timestamp |
| `trip_distance` | Float | Distance in miles |
| `fare_amount` | Float | Base fare charged |
| `total_amount` | Float | Total including extras, tip, tolls |
| `RatecodeID` | Integer | Fare rate (Standard, JFK, Newark, etc.) |
| `payment_type` | Integer | 1=Credit Card, 2=Cash, 3=No Charge, 4=Dispute |
| `PULocationID` | Integer | Pickup zone (TLC taxi zone) |
| `DOLocationID` | Integer | Dropoff zone |

---

## 🔬 Analysis — PACE Workflow

### Stage 1 — PLAN
- Defined business requirements with Automatidata leadership team
- Identified key stakeholders: technical (Udo Bankole, Deshawn Washington) and non-technical (Titus Nelson, Juliana Soto)
- Scoped deliverables: EDA → feature engineering → regression model → executive summary

### Stage 2 — ANALYZE
- Loaded and inspected 22,699 records across 19 columns
- **No critical nulls** detected — dataset is complete
- Identified data type distribution: 11 integers/floats, 2 datetimes, 1 categorical
- Built descriptive statistics table with coefficient of variation

### Stage 3 — CONSTRUCT
**Feature Engineering:**
- `trip_duration_mins` — derived from pickup/dropoff timestamps
- `pickup_hour`, `pickup_day_of_week` — temporal features
- `speed_mph` — distance / duration ratio

**Key Findings:**

| Insight | Detail |
|--------|--------|
| Top predictor of fare | `trip_distance` (r ≈ 0.90) |
| Second predictor | `trip_duration_mins` (r ≈ 0.85) |
| Peak ride hours | 6–9 AM and 3–8 PM |
| Payment split | 67% credit card, 30% cash |
| Outlier rate | ~3–5% in fare & distance (IQR method) |
| Avg fare | ~$14.50 |
| Avg trip distance | ~2.9 miles |

### Stage 4 — EXECUTE
- Prepared visualizations suitable for non-technical TLC stakeholders
- Flagged outlier records requiring review before model training
- Documented recommended next steps for the regression model build

---

## 📈 Key Visualizations

The notebook contains:
- Distribution histograms for all numeric features
- Hourly ride volume and avg fare line charts
- Payment type breakdown (pie + bar)
- **Distance vs Fare scatter plot** with regression line
- **Duration vs Fare scatter plot** with regression line
- Correlation heatmap (lower triangle)
- Tip behavior analysis (credit card rides only)

---

## 🛠️ Tech Stack

```python
pandas       # DataFrames, datetime parsing, groupby aggregations
numpy        # Statistical calculations, IQR outlier detection
matplotlib   # Charts, subplots, regression lines
seaborn      # Heatmap, theme styling
jupyter      # Interactive notebook environment
```

---

## 🚀 How to Run

```bash
# 1. Clone the repo
git clone https://github.com/Zolow-kuni/automatidata-nyc-tlc.git
cd automatidata-nyc-tlc

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 3. Launch the notebook
jupyter notebook automatidata_tlc_analysis.ipynb
```

---

## 📋 Next Steps (Model Build)

1. **Outlier capping** at 99th percentile for `fare_amount` and `trip_distance`
2. **One-hot encoding** of `RatecodeID`, `VendorID`, `payment_type`
3. **Baseline model**: `fare_amount ~ trip_distance + trip_duration_mins`
4. **A/B test** model variants (recommended by Director of Data Analysis)
5. **Holdout validation** before TLC stakeholder presentation

---

## 👤 About

**Subham Joshi** — Data Operations Analyst based in Dehradun, India.  
Experienced in Python, SQL, Power BI, and data pipeline operations.

- 🔗 [LinkedIn](https://linkedin.com/in/subham-joshi-b25778280)
- 💼 [Data Portfolio 1](https://github.com/Zolow-kuni/data-portfolio)
- 💼 [Data Portfolio 2](https://github.com/Zolow-kuni/data-portfolio-2)
- 📧 joshisubham442@gmail.com

---

*This project is part of the [Google Advanced Data Analytics Certificate](https://www.coursera.org/professional-certificates/google-advanced-data-analytics) on Coursera. The dataset and scenario are used for educational purposes.*
