
# Paragon Geeks — Transaction-Level Sales & Operations Analytics (Square POS)

## 🚀 Business Impact Snapshot
- Analyzed **$262,919 in revenue across 1,922 transactions**
- Identified **$107,653 (40.9%) undocumented revenue exposure**
- Built a **transaction-level, audit-safe analytics system** from raw POS data
- Engineered a **text-to-structured data pipeline** for unstructured transactions
- Delivered an **executive Power BI dashboard** for real business operations
  
---

## Table of Contents

- [Executive Overview](#executive-overview)
- [Text Standardization & Feature Engineering](#text-standardization--feature-engineering)
- [Business Questions Answered](#business-questions-answered)
- [My Role](#my-role)
- [Core Outcomes](#core-outcomes)
- [Tech Stack](#tech-stack)
- [Project Overview](#project-overview)
- [Why This Project Matters](#why-this-project-matters)
- [Data Source](#data-source)
- [Methodology](#methodology)
- [Technical Architecture](#technical-architecture)
- [Data Validation & Controls](#data-validation--controls)
- [Skills Demonstrated](#-skills-demonstrated)
- [Key Insights](#key-insights)
- [Strategic Business Impact](#strategic-business-impact)
- [Repository Structure](#repository-structure)
- [Reproducibility](#reproducibility)
- [Dashboard Preview](#dashboard-preview)

---

## Executive Overview

I designed and implemented a transaction-level analytics system for a multi-location electronics repair business, transforming raw Square POS exports into structured, audit-safe datasets and decision-ready insights.

This project demonstrates how unstructured, inconsistent business data can be converted into reliable operational intelligence while preserving real-world complexity and financial accuracy.

---

## Text Standardization & Feature Engineering

A core differentiator of this project was transforming unstructured POS transaction text into structured, analysis-ready data.

Square POS records contained inconsistent, free-text descriptions with no standardized schema for repairs, devices, or services. To address this, I engineered a text-to-structured pipeline using NLP-assisted token analysis (bi-grams / tri-grams) combined with rule-based classification.

This approach enabled systematic extraction and standardization of key analytical dimensions:

- Repair / Service Type (Screen, Battery, Back Glass, Charging Port, etc.)
- Device Type (Phone, Tablet, Computer, Gaming Console, etc.)
- Brand (Apple, Samsung, Google, etc.)
- Model (iPhone 14 Pro Max, Galaxy S23 Ultra, etc.)
- Multi-repair and multi-device transaction indicators

### Example Transformation

**Raw Input:**  
"iphone 14 pro max screen battery back glass"

**Structured Output:**
- Device: iPhone 14 Pro Max  
- Repairs: Screen, Battery, Back Glass  
- Multi-Repair: Yes  

This transformation layer enabled:
- Accurate aggregation of repair categories across inconsistent inputs  
- Device-level and brand-level performance analysis  
- Identification of bundled services and complex repair behavior  
- Reliable feature generation for downstream analytics  

Without this step, meaningful analysis of service mix, pricing behavior, and operational performance would not have been possible.

---

## Business Questions Answered

- Where is revenue leakage occurring?
- Which services drive the most revenue?
- How does pricing impact documentation behavior?
- When are peak operational hours?
- How can operations improve revenue capture and efficiency?

---

## My Role

- Operations Manager overseeing two retail locations  
- Led end-to-end analytics initiative from raw data to executive dashboard  
- Designed and implemented full **raw → processed → visualization pipeline**  
- Engineered structured datasets from unstructured POS transaction text  
- Translated operational challenges into measurable analytics solutions  

---

## Core Outcomes

- Reconciled **100% of revenue** to transaction-level source data  
- Identified **$107K+ undocumented revenue exposure (40.9%)**  
- Discovered documentation gaps concentrated in **$100–$200 price tiers**  
- Identified peak operational window (**11 AM – 3 PM**) for staffing optimization  
- Measured **4× revenue lift** from accessory bundles vs standalone sales  
- Delivered **audit-safe Power BI dashboard** with validated outputs  

---

## Tech Stack

- Python (pandas, numpy)  
- Power BI (DAX)  
- NLP / Text Processing (CountVectorizer)  
- Data Engineering (ETL pipelines)  
- Jupyter Notebook  
- GitHub  

---

## Project Overview

Built an end-to-end analytics pipeline using real-world Square POS data to transform inconsistent, free-text-heavy transaction records into structured, audit-safe datasets.

The system enables reliable operational insights while preserving raw business complexity and ensuring full financial traceability.

---

## Why This Project Matters

Retail POS data is often inconsistent, free-text heavy, and operationally messy. 

This project demonstrates the ability to:

- Govern imperfect business data without distorting reality  
- Quantify financial reporting risk tied to documentation behavior  
- Normalize unstructured transaction text into structured analytical dimensions  
- Translate operational data into executive-level decision intelligence  

This mirrors real enterprise analytics environments where data integrity, reproducibility, and business alignment are critical.

---

## Data Source

**Data Privacy Note:**  
All transaction data has been anonymized. No customer-identifiable information is included.

- Square POS exports (2024–2025)  
- ~1,900 transactions  
- Mix of structured and unstructured fields  
- Includes documented and undocumented transactions  

Raw data is preserved without modification for audit traceability.

---

## Methodology

The analytics pipeline follows a strict, audit-safe methodology designed to prevent metric drift and ensure reproducibility.

### Core Steps

- Ingestion and normalization of multiple POS export formats  
- Enforcement of transaction grain (**1 row = 1 transaction**)  
- Explicit separation of documented vs undocumented transactions  
- NLP-assisted token analysis (bi-grams / tri-grams)  
- Rule-based feature engineering from unstructured text  
- Construction of validated fact and dimension tables  
- Revenue reconciliation against source data  
- Export of Power BI–ready datasets  

All dashboard visuals are generated exclusively from validated outputs.

---

## Technical Architecture

### Raw Layer (Immutable)
- Square POS exports (2024–2025)  
- Stored in `data/raw/`  
- Never modified  

### Processing Layer (Python)
- Data cleaning and normalization  
- Revenue reconciliation and refund handling  
- Text parsing and classification  
- Documentation tagging  
- Price tier segmentation  
- Time-based feature engineering  

### Output Layer (Locked Tables)
- Transaction-level fact table  
- Device / brand / model dimensions  
- Pricing and documentation metrics  
- Time-based performance tables  

### Visualization Layer (Power BI)
- DAX-only calculations  
- No Power Query transformations  
- Connected exclusively to processed datasets  

---

## Data Validation & Controls

- Revenue reconciled to original POS exports  
- Transaction counts validated pre/post processing  
- Refund normalization verified  
- Documented baseline snapshot locked  
- Cross-validation between Python and Power BI  
- No dashboard-side transformations allowed  

---

## 💼 Skills Demonstrated

### Data Engineering
- Built transaction-level ETL pipeline  
- Enforced raw → processed architecture  
- Designed reproducible workflows  

### Data Cleaning & Feature Engineering
- NLP-based text parsing (CountVectorizer)  
- Rule-based classification of services  
- Device, brand, and model extraction  
- Multi-repair and bundled transaction handling  

### Analytics & Business Insight
- Revenue risk analysis tied to documentation gaps  
- Pricing tier behavioral analysis  
- Service mix and attach-rate evaluation  
- Operational timing optimization insights  

### Business Intelligence
- Executive dashboard design in Power BI  
- DAX-based KPI development  
- Full reconciliation between backend and visuals  

### Data Governance
- Transaction-level data integrity enforcement  
- No silent filtering or recomputation  
- Full traceability from raw data to dashboard  

---

## Key Insights

### Revenue & Documentation
- Total Revenue: **$262,919.10**  
- Documented Revenue: **$155,265.60 (59.1%)**  
- Undocumented Revenue: **$107,653.50 (40.9%)**  

Documentation gaps represent a **material financial reporting risk**.

---

### Service Mix
- Screen repairs generate **$106K+ revenue** across 600+ transactions  
- Core services dominate total revenue contribution  
- Multi-repair transactions increase ticket size  

---

### Pricing Behavior
- Higher-priced repairs show stronger documentation discipline  
- Undocumented revenue concentrated in **$100–$200 range**  
- Improving documentation here yields immediate gains  

---

### Operational Timing
- Peak hours: **11 AM – 3 PM**  
- Midday drives highest volume and revenue  

---

### Retail Performance
- Accessory bundles outperform standalone sales by **4×+ revenue**  
- Bundling increases average ticket size significantly  

---

## Strategic Business Impact

This system enables:

- Reduction of undocumented revenue exposure  
- Improved pricing and documentation discipline  
- Staffing optimization based on demand patterns  
- Increased revenue through bundling strategies  
- Stronger audit defensibility  

---

## Repository Structure
~~~
paragon-geeks-sales-analytics/
│
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
├── powerbi/
├── images/
└── README.md
~~~
---

## Reproducibility

- Raw data remains unchanged  
- All transformations are traceable  
- Outputs reconcile to source data  
- Power BI uses processed datasets only  
- No hidden logic or recalculations  

---

## Dashboard Preview

> **Data Integrity Note:**  
> All visuals reconcile exactly to validated notebook outputs. No Power BI-side filtering,
> aggregation, or transformation alters source metrics.


Below are selected previews from the executive Power BI dashboard.  
All visuals are generated exclusively from audit-safe processed datasets.

### Executive Overview
![Executive Overview](paragon-geeks-sales-analytics/images/01_Executive_Overview.png)

### Documentation Coverage
![Documentation Coverage](paragon-geeks-sales-analytics/images/02_Documentation_Quality.png)

### Documented Operations
![Documented Operations](paragon-geeks-sales-analytics/images/03_Documented_Revenue_Breakdown.png)

### Retail Performance
![Retail Performance](paragon-geeks-sales-analytics/images/04_Retail_Performance.png)

### Operational Timing
![Operational Timing](paragon-geeks-sales-analytics/images/05_Operational_Performance_Timing.png)

---

## Final Note

This project demonstrates the ability to transform messy, real-world business data into structured, audit-safe, decision-ready analytics systems aligned with enterprise data practices.




 
