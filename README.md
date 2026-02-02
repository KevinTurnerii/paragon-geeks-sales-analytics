# Paragon Geeks — Transaction-Level Sales & Operations Analytics

## Project Overview

This project delivers an end-to-end, transaction-level analytics pipeline built on Square POS data for Paragon Geeks, a multi-location electronics repair and retail business. The objective was to transform raw, inconsistent point-of-sale exports into audit-safe operational insights that support executive decision-making.

The final output includes a fully documented analytics notebook, normalized fact and dimension tables, and an executive-ready Power BI dashboard designed for business stakeholders.

---

## Business Problem

Like many service-based retail businesses, Paragon Geeks faced challenges with:
- Inconsistent transaction documentation
- Free-text service descriptions
- Limited visibility into repair mix, pricing tiers, and operational timing
- Difficulty linking revenue performance to documentation quality

This project addresses those issues by enforcing transaction-level consistency while preserving real-world data complexity.

---

## Data Source

- Square POS exports (2024–2025)
- ~1,900 total transactions
- Combination of structured fields and unstructured free-text notes
- Includes both documented and undocumented transactions

---

## Methodology

The analytics pipeline follows a strict, audit-safe approach:

- Data ingestion and normalization across multiple Square export formats
- Separation of documented vs. undocumented transactions
- Token-based parsing of free-text fields to extract:
  - Repair vs retail classification
  - Device type, brand, and model
  - Service categories and complexity indicators
- Construction of locked fact and dimension tables
- Validation of all aggregates against known revenue totals
- Export of clean, Power BI–ready datasets


All presentation tables and Power BI visuals are generated exclusively from locked, validated outputs to prevent metric drift or silent recomputation.
No manual overrides were applied to final metrics.

---

## Key Insights

- **$262,919.10** in total revenue analyzed across **1,922 transactions**
- **59.1% of revenue** is fully documented (**$155,265.60**), while **40.9% remains undocumented**
- Screen repairs dominate documented revenue, accounting for **$106K+** across **600+ transactions**
- Higher-priced repairs (>$200) show significantly stronger documentation rates than low-ticket transactions
- Peak operational window occurs between **11 AM and 3 PM**, capturing the highest transaction volume and revenue
- Accessory bundles attached to repairs outperform standalone accessory sales by over **4× in revenue**

---

## Power BI Dashboard Overview

The Power BI dashboard is structured across five focused pages:

1. **Executive Revenue Overview**  
   High-level revenue, documentation coverage, and price-tier distribution.

2. **Documentation Coverage & Quality**  
   Breakdown of documented vs undocumented transactions by price tier.

3. **Documented Operations Breakdown**  
   Repair and service mix by category, device type, brand, and model.

4. **Retail & Accessory Performance**  
   Accessory-only sales versus bundled retail activity.

5. **Operational Performance & Timing**  
   Hourly, daily, and monthly transaction patterns.

Pages are intentionally designed with minimal slicing to preserve audit integrity.

---

## Repository Structure

```text
paragon-geeks-sales-analytics/
│
├── data/
│   ├── raw/                 # Original Square POS exports (not modified)
│   └── processed/           # Audit-safe, analysis-ready CSV outputs
│
├── notebooks/               # Data cleaning, classification, and analysis pipeline
│
├── powerbi/                 # Power BI dashboard (.pbix) using processed data only
│
├── images/                  # Exported charts & screenshots for documentation
│
└── README.md                # Project overview and findings
```

## Data Pipeline Overview

This project follows a strict, audit-safe analytics pipeline to ensure reproducibility and metric integrity.

1. **Raw Data Ingestion**
   - Square POS exports from 2024 and 2025 are ingested without modification.
   - Raw files are preserved in the `data/raw` directory for traceability.

2. **Data Cleaning & Normalization**
   - Transaction-level data is standardized across years.
   - Revenue fields are normalized, refunds handled explicitly, and transaction grain is enforced (1 row = 1 transaction).

3. **Text Parsing & Classification**
   - Free-text transaction descriptions are parsed using a token-based approach.
   - Repairs, services, accessories, and retail activity are classified without hardcoding assumptions.
   - Multi-repair, partial payments, and bundled transactions are explicitly flagged.

4. **Documentation Coverage Analysis**
   - Transactions are categorized as **Documented** or **Undocumented** based on description quality.
   - Coverage is analyzed across revenue, transaction counts, and price tiers.

5. **Locked Outputs**
   - All finalized datasets are exported to `data/processed`.
   - These CSVs are treated as immutable and serve as the sole data source for Power BI.

This structure prevents silent recomputation, double counting, or metric drift between analysis and visualization layers.

## Power BI Dashboard Overview

The Power BI dashboard is built **exclusively from the processed datasets** located in `data/processed`.  
No transformations, filters, or calculations are performed in Power Query to preserve audit integrity.

### Dashboard Pages

**1. Executive Overview**
- Total Revenue (All Transactions)
- Documented vs Undocumented Revenue Share
- Documentation Coverage %
- High-level KPI tiles for quick decision-making

**2. Repair & Service Mix**
- Revenue and transaction volume by `bucket_final`
- Identifies dominant repair categories (e.g., Screen, Back Glass, Battery)
- Highlights operational revenue drivers

**3. Device & Brand Performance**
- Revenue and volume by device type (Phone, Tablet, Computer, etc.)
- Brand-level performance (Apple, Samsung, Google, etc.)
- Top device models by revenue and average ticket size

**4. Pricing & Documentation Analysis**
- Price tier distribution across all transactions
- Documentation rate by price tier
- Identifies where undocumented revenue is most concentrated

**5. Time-Based Performance**
- Monthly revenue and transaction trends (audit-safe)
- Day-of-week performance
- Hourly revenue and transaction patterns

### Design Principles
- One fact table driving all visuals
- Measures calculated in DAX only
- No hidden filters or silent exclusions
- Totals reconcile exactly to notebook outputs

## Key Findings & Business Insights

### Revenue Concentration
- **Screen repairs dominate operations**, accounting for the highest transaction volume and revenue among all repair categories.
- A small number of repair types (Screen, Back Glass, Battery) generate the majority of documented revenue, indicating clear operational focus areas.

### Documentation Gap
- Only **59.1% of total revenue is documented**, leaving **$107K+** in undocumented transactions.
- Undocumented revenue is disproportionately concentrated in **mid-to-high price tiers**, representing elevated audit and reporting risk.
- Higher-priced jobs show stronger documentation discipline, but gaps remain below the $150 range.

### Pricing Structure
- The **$100–$250 price tiers** represent the core revenue engine of the business.
- Extremely high-ticket jobs ($500+) are rare but materially impactful, requiring special handling and documentation controls.

### Device & Brand Performance
- **Phones drive the business**, followed by tablets and computers.
- **Apple devices generate the majority of revenue**, followed by Samsung.
- Certain models (e.g., flagship iPhones and premium Android devices) deliver higher average ticket sizes, justifying targeted inventory and staffing strategies.

### Operational Timing
- Peak revenue occurs during **midday to early evening hours**, aligning with staffing optimization opportunities.
- Monthly trends show consistent growth into mid–late 2025, validating demand stability.

### Strategic Implications
- Improving documentation coverage in mid-priced repairs could materially increase financial transparency without changing volume.
- Operational focus should prioritize:
  - High-volume phone repairs
  - Apple and Samsung inventory readiness
  - Midday staffing optimization

## Metrics & KPI Definitions

This project uses clearly defined, audit-safe metrics to ensure consistency between analysis, reporting, and visualization layers.

### Core Revenue Metrics
- **Transactions**  
  Count of unique Square POS transactions. Each transaction represents one completed customer interaction.

- **Revenue (Net Sales)**  
  Net sales after discounts and refunds, derived from Square POS exports and normalized into `net_sales_num`.

- **Average Ticket**  
  Calculated as total revenue divided by number of transactions within a group.

### Documentation Metrics
- **Documented Transaction**  
  A transaction with sufficient descriptive detail (notes, item descriptions, or tokens) to confidently classify device, brand, and repair/service type.

- **Undocumented Transaction**  
  A transaction lacking sufficient detail for reliable classification.

- **Documentation Coverage (%)**  
  Percentage of total revenue and transactions that are documented:



### Repair & Service Classification
- **bucket_final**  
Final, mutually exclusive classification representing the primary repair or service performed (e.g., Screen Repair, Battery Repair, Diagnostic, Deposit).

- **Multi-Repair Flag**  
Identifies transactions involving more than one repair event.

- **Accessory Bundles**  
Accessory sales occurring alongside a repair transaction.

### Device & Brand Metrics
- **device_type_final**  
Final classified device category (phone, tablet, computer, console, accessory, etc.).

- **brand_final**  
Standardized manufacturer classification derived from device and text tokens.

- **device_model_exact_refined**  
Refined device model extracted from transaction text and normalized for reporting.

### Pricing Metrics
- **Price Tier**  
Transaction-level bucketing based on net sales value (e.g., $100–$125, $250–$300).

- **Price Tier Name**  
Human-readable label describing typical job complexity at each tier.

### Time-Based Metrics
- **Hour of Day**  
Transaction hour derived from POS timestamps and normalized to a 12-hour format.

- **Day of Week**  
Weekday extracted from transaction date.

- **Month**  
Monthly aggregation used for trend analysis and seasonality inspection.

### Audit & Integrity Controls
- All KPIs are derived **only from processed CSVs** in the `data/processed/` directory.
- Power BI dashboards reference **no raw data** and apply **no hidden filters**.
- Row counts and revenue totals are validated against locked snapshot baselines.

## Power BI Dashboard Overview

The Power BI dashboard was built exclusively on audit-safe, processed datasets generated by the Python notebook pipeline. No raw data, manual edits, or Power BI–side transformations were used.

The dashboard is structured into **five analytical pages**, each answering a distinct business question.

### Page 1 — Executive Overview
**Purpose:** High-level performance snapshot for leadership.

**Key visuals:**
- Total Revenue (All Transactions)
- Documented vs Undocumented Revenue Share
- Average Ticket Size
- Transaction Volume
- Revenue Trend Over Time

**Business Value:**  
Provides immediate visibility into overall sales performance and highlights the documentation gap impacting analytical accuracy.

---

### Page 2 — Repair & Service Mix
**Purpose:** Understand what drives revenue operationally.

**Key visuals:**
- Revenue by Repair / Service Category
- Transaction Count by Repair Type
- Accessory Bundles vs Standalone Accessories

**Business Value:**  
Identifies the most profitable repair types and surfaces opportunities to optimize pricing, staffing, and upsell strategies.

---

### Page 3 — Device & Brand Performance
**Purpose:** Analyze demand by device ecosystem.

**Key visuals:**
- Revenue by Device Type
- Revenue by Brand
- Top 25 Device Models by Revenue

**Business Value:**  
Supports inventory planning, technician specialization, and targeted marketing based on high-demand devices.

---

### Page 4 — Pricing & Documentation Analysis
**Purpose:** Evaluate pricing strategy and data quality simultaneously.

**Key visuals:**
- Revenue by Price Tier
- Documented vs Undocumented Share by Price Tier
- Average Ticket by Price Tier

**Business Value:**  
Reveals where high-value work lacks documentation and where operational discipline can significantly improve insight quality.

---

### Page 5 — Time-Based Performance
**Purpose:** Optimize staffing and operating hours.

**Key visuals:**
- Revenue by Hour of Day
- Revenue by Day of Week
- Monthly Revenue Trends

**Business Value:**  
Informs scheduling, labor allocation, and promotional timing based on actual transaction behavior.

## Tools & Technologies Used

**Data Processing & Analysis**
- Python (Pandas, NumPy)
- Jupyter Notebook
- Token-based text parsing and rule-based classification
- Audit-safe aggregation and validation checks

**Business Intelligence & Visualization**
- Power BI Desktop
- Star-schema–friendly fact and dimension tables
- DAX measures (no Power Query transformations)

**Data Sources**
- Square POS transaction exports (2024–2025)
- Combined and normalized into a single transaction-level dataset

**Version Control & Documentation**
- Git & GitHub
- Markdown documentation
- Structured repository layout for reproducibility
 
 
 ## How to Reproduce This Analysis

This project is designed to be fully reproducible and audit-safe. All results shown in the notebook and Power BI dashboard are derived exclusively from processed datasets generated by the notebook pipeline.

### 1. Clone the Repository

    git clone https://github.com/KevinTurneri/paragon-geeks-sales-analytics.git
    cd paragon-geeks-sales-analytics

### 2. Raw Data Placement

Place the original Square POS exports into the following directory:

    data/raw/
    ├── 2024 sales.csv
    └── 2025 sales.csv

Raw files are treated as immutable source data and are never modified directly.

### 3. Run the Analysis Notebook

Open the main notebook located at:

    notebooks/paragon_geeks_transaction_level_analysis.ipynb

Run all cells top-to-bottom to:

- Normalize transaction-level data across years  
- Enforce transaction grain (1 row = 1 transaction)  
- Parse free-text descriptions using token-based classification  
- Classify repairs, services, accessories, and retail activity  
- Apply documentation coverage flags  
- Validate all transaction counts and revenue totals  
- Export audit-safe datasets to the data/processed directory  

### 4. Processed Outputs

After successful execution, the following files will be generated in:

    data/processed/

    fact_repair_service.csv
    dim_device_type.csv
    dim_brand.csv
    dim_model_top25.csv
    kpi_accessory.csv
    price_tier_totals.csv
    documentation_share_by_price_tier.csv
    hourly_performance.csv
    dow_performance.csv
    monthly_performance.csv

These files are treated as locked outputs and serve as the single source of truth for all reporting.

### 5. Open the Power BI Dashboard

Open the Power BI file located at:

    powerbi/Paragon_Geeks_Executive_Dashboard.pbix

The dashboard connects only to the processed CSV files in data/processed.

No Power Query transformations, filters, or manual edits are applied.  
All calculations are performed using DAX measures to preserve audit integrity.

### Reproducibility & Integrity Notes

- Raw data is never altered  
- All metrics reconcile exactly to notebook validation totals  
- Power BI uses processed data only  
- No silent recomputation or hidden filters exist  
- Results are fully traceable from raw data to final dashboard  

## Dashboard Preview

Below are selected previews from the executive Power BI dashboard.
All visuals are generated exclusively from audit-safe processed datasets.

![Executive Overview](images/executive_overview.png)
![Documentation Coverage](images/documentation_coverage.png)
![Documented Operations](images/documented_operations.png)
![Retail Performance](images/retail_performance.png)
![Operational Timing](images/operational_timing.png)




