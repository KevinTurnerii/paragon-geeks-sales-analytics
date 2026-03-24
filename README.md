# Paragon Geeks — Operational Intelligence & Revenue Analytics System (Square POS)

## Business Problem
Inconsistent, unstructured POS transaction data prevented accurate revenue tracking, operational visibility, and reliable financial reporting across multiple retail locations.

## Solution
Designed and implemented an end-to-end analytics system to transform raw Square POS exports into structured, validated datasets and executive-level dashboards.

## Key Outcomes
- Analyzed **$262,919 in revenue across 1,922 transactions**
- Identified **$107,653 (40.9%) undocumented revenue exposure**
- Built a **transaction-level, audit-safe analytics system**
- Engineered a **text-to-structured pipeline for unstructured transaction data**
- Delivered an **executive Power BI dashboard for operational decision-making**

---

Built and deployed within a real multi-location electronics repair business (**Paragon Geeks**), where I manage daily operations, customer intake, and service workflows.

This project transforms unstructured transaction data into structured operational intelligence, enabling accurate analytics, financial visibility, and data-driven business decisions.

---

## 📑 Table of Contents

- [Executive Overview](#executive-overview)
- [End-to-End Pipeline](#end-to-end-pipeline)
- [Text Standardization & Feature Engineering](#text-standardization--feature-engineering)
- [Business Questions Answered](#business-questions-answered)
- [My Role](#my-role)
- [Core Outcomes](#core-outcomes)
- [Tech Stack](#tech-stack)
- [Methodology](#methodology)
- [Dual-Layer Analysis Strategy](#dual-layer-analysis-strategy)
- [Technical Architecture](#technical-architecture)
- [Data Validation & Controls](#data-validation--controls)
- [Skills Demonstrated](#skills-demonstrated)
- [Key Insights](#key-insights)
- [Strategic Business Impact](#strategic-business-impact)
- [Repository Structure](#repository-structure)
- [Dashboard Preview](#dashboard-preview)

---

## Executive Overview

I designed and implemented a transaction-level analytics system within a real retail operations environment, transforming raw Square POS data into structured, audit-safe datasets and decision-ready insights.

This system demonstrates how unstructured business data can be transformed into reliable operational intelligence to support revenue tracking, performance analysis, and business decision-making.

---

## End-to-End Pipeline

This project was executed as a complete analytics pipeline:

### Data Ingestion Layer
- Imported raw Square POS exports across multiple formats  
- Preserved raw data as an immutable source for audit traceability  

### Processing & Transformation Layer (Python)
- Cleaned and standardized transaction records  
- Parsed unstructured text using NLP-assisted tokenization (bi-grams / tri-grams)  
- Engineered structured features (repair, device, brand, model)  
- Classified multi-repair and multi-device transactions  
- Segmented documented vs undocumented transactions  

### Analytical Layer
- Performed revenue, service mix, pricing, and timing analysis  
- Quantified documentation gaps and financial exposure  
- Generated validated, transaction-level datasets  

### Visualization Layer (Power BI)
- Built executive dashboard using DAX-only measures  
- Ensured full alignment with validated backend outputs  
- Delivered operational and financial insights for decision-making  

---

## Text Standardization & Feature Engineering

Square POS records contained inconsistent, free-text descriptions with no standardized schema.

To address this, I engineered a **text-to-structured pipeline** using NLP-assisted token analysis combined with rule-based classification.

### Extracted Dimensions:
- Repair / Service Type  
- Device Type  
- Brand  
- Model  
- Multi-repair indicators  

### Example Transformation

**Raw Input:**  
"iphone 14 pro max screen battery back glass"

**Structured Output:**
- Device: iPhone 14 Pro Max  
- Repairs: Screen, Battery, Back Glass  
- Multi-Repair: Yes  

### Impact

This enabled:
- Reliable aggregation across inconsistent inputs  
- Device and service-level performance analysis  
- Identification of bundled services  
- Structured datasets for downstream analytics and reporting  

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
- Led full analytics initiative from raw data to dashboard  
- Designed and implemented a complete **data pipeline + analytics system**  
- Translated operational challenges into measurable business insights  

---

## Core Outcomes

- Reconciled **100% of revenue to source transactions**  
- Identified **$107K+ undocumented revenue exposure (40.9%)**  
- Found documentation gaps in **$100–$200 pricing tier**  
- Identified peak hours (**11 AM – 3 PM**)  
- Identified that accessory add-ons significantly increase average transaction value when combined with repair services  
- Delivered **audit-safe Power BI dashboard**  

---

## Tech Stack

- Python (pandas, numpy)  
- Power BI (DAX)  
- NLP / Text Processing (CountVectorizer)  
- Jupyter Notebook  
- GitHub  

---

## Methodology

- Enforced **1 row = 1 transaction grain**  
- Separated documented vs undocumented transactions  
- Applied NLP-based tokenization  
- Built rule-based classification system  
- Constructed structured analytical datasets  
- Reconciled all outputs to raw data  

---

## Dual-Layer Analysis Strategy

### Structured Layer (Documented Transactions)
- Used for feature engineering and detailed analysis  
- Enabled service mix, pricing, and device insights  

### Completeness Layer (Undocumented Transactions)
- Retained for full revenue reconciliation  
- Used to quantify data quality and reporting risk  

### Impact

- **100% revenue preserved**  
- **Insights derived only from reliable structured data**  
- **Data quality issues explicitly measured**  

---

## Technical Architecture

- Raw Layer (immutable POS exports)  
- Processing Layer (Python transformations)  
- Output Layer (validated fact tables designed for SQL-based querying)  
- BI Layer (Power BI dashboard)  

Structured outputs were designed for downstream SQL-based querying and seamless integration with business intelligence tools.

---

## Data Validation & Controls

- Revenue fully reconciled  
- Transaction counts validated  
- Refund handling verified  
- No dashboard-side transformations  
- Full traceability maintained  

---

## Skills Demonstrated

- Data Engineering (ETL pipeline design)  
- NLP & Text Processing  
- Feature Engineering  
- Data Cleaning & Standardization  
- Business Intelligence & Analytics  
- Power BI & Data Visualization  
- Data Governance & Validation  

---

## Key Insights

### Revenue Integrity
- $262,919 total revenue  
- 40.9% undocumented → major reporting risk  

### Service Performance
- Screen repairs dominate revenue  
- Multi-repair transactions increase ticket size  

### Pricing Behavior
- Documentation improves at higher price tiers  
- Mid-tier ($100–$200) drives most gaps  

### Operations
- Peak window: 11 AM – 3 PM  

### Retail Strategy
- Accessory add-ons increase average transaction value when paired with repair services  

---

## Strategic Business Impact

- Reduced financial reporting risk  
- Improved operational visibility  
- Identified revenue optimization opportunities  
- Strengthened audit readiness  

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
> All visuals reconcile exactly to validated notebook outputs. No Power BI-side transformations alter source metrics.

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

This project demonstrates the ability to transform messy, real-world business data into structured, audit-safe, and decision-ready analytics systems aligned with enterprise data practices.
 
