# Rwanda Crop Production and Market Intelligence System

**Repository:** `Christeva_20251SEN203_RwandaCropIntel`

**Project Short Name:** RwandaCropIntel

**Student:** Christeva Ikuzwe  
**Student ID:** 20251SEN203  
**Course:** INSY 8311 — Database Development with PL/SQL  
**Project Type:** Individual Capstone / Final Examination  
**Domain:** Agriculture and Food  
**Technology:** Oracle Database, PL/SQL and Oracle APEX

---

## 1. Problem Statement

Agricultural decision-making in Rwanda requires reliable information about crop production, cultivated land, fertilizer use, productivity and post-harvest losses. However, agricultural information may be scattered across different reports and datasets, making it difficult to compare production performance, understand fertilizer-use patterns and estimate the quantity of crops potentially available for sale.

This project proposes an integrated Oracle database system that organizes and analyzes agricultural production and input-use information in Rwanda. It will use PL/SQL to perform agricultural calculations and enforce database business rules, while Oracle APEX will provide an interactive dashboard for presenting production trends, fertilizer-use patterns, post-harvest losses and potential marketable-supply estimates.

## 2. Objectives

### Main Objective

To design and implement an Oracle database system using PL/SQL and Oracle APEX to analyze crop production, fertilizer use, post-harvest losses and potential marketable supply in Rwanda.

### Specific Objectives

- Organize agricultural data into normalized relational database tables following Third Normal Form (3NF).
- Analyze crop production and yield across districts, crops and agricultural seasons.
- Examine fertilizer types, sources, quantities applied and associated costs.
- Calculate and analyze post-harvest losses and their possible causes.
- Estimate potential marketable crop supply using production, loss and utilization information where the necessary data is available.
- Implement PL/SQL procedures, functions, cursors, packages and triggers for agricultural data processing.
- Develop an interactive Oracle APEX dashboard for agricultural reporting and decision support.

## 3. Data Source

### Primary Data Source

| Item | Detail |
|---|---|
| Dataset / Survey | Rwanda Seasonal Agricultural Survey 2025 |
| Institution | National Institute of Statistics of Rwanda (NISR) |
| Geographic coverage | Rwanda — all 30 districts |
| Agricultural periods | Seasons A, B and C |
| Source link | [NISR Seasonal Agricultural Survey 2025 Report](https://statistics.gov.rw/sites/default/files/documents/2025-12/SAS%202025%20Final%20report.pdf) |
| Data type | Agricultural survey statistics and production information |
| Planned use | Crop production, cultivated area, yields and agricultural input analysis |

### Planned Data Requirements

The project will identify and obtain suitable underlying survey data containing relevant variables such as:

- District and agricultural season.
- Crop type and cultivated area.
- Harvested crop quantities and production.
- Fertilizer type and application information.
- Fertilizer sources, quantities and costs, where recorded.
- Crop utilization and post-harvest loss information, where available.

**Data preparation note:** The linked PDF is the published survey report, not the raw microdata. The underlying datasets will be obtained and inspected separately before finalizing the database design. Actual record counts, field names, measurement units, data licence and available relationships will be documented after inspection. Personal identifying information will be excluded.

Additional credible research papers and NISR agricultural reports will support the analysis and research documentation.

## 4. Innovation

**Option chosen:** User Interface  
**Tool:** Oracle APEX  
**Database and business logic:** Oracle Database and PL/SQL

### What the Innovation Does

The project will provide an interactive agricultural intelligence application connected to the Oracle database. Users will be able to explore agricultural information through dashboards, reports, charts and analytical views.

### Planned Dashboard Features

**1. Crop Production Dashboard**

- View production quantities by crop, district and season.
- Compare crop yields across districts.
- Identify crops and locations with higher or lower production.

**2. Fertilizer-Use Analysis**

- Compare organic and inorganic fertilizer use.
- Analyze fertilizer sources and types.
- Examine quantities applied and reported application costs.
- Compare fertilizer-use patterns with crop productivity.

**3. Post-Harvest Loss Dashboard**

- Analyze recorded crop losses.
- Compare loss quantities and percentages.
- Examine recorded causes of post-harvest losses.
- Identify crops and locations with significant losses.

**4. Potential Marketable-Supply Analysis**

- Estimate the quantity potentially available for sale using production, recorded losses and other documented utilization categories.
- Compare potential marketable supply across crops and districts.
- Generate analytical summaries to support agricultural planning.

**5. What-If Analysis**

- Simulate how a hypothetical increase in yield could affect production.
- Estimate how reducing post-harvest losses could change potential marketable supply.
- Compare different analytical scenarios.

The calculations and business rules will remain in PL/SQL. Oracle APEX will provide the user interface and display the results generated by the database.

## 5. Planned Database Tables

The following tables are proposed. Their final structure and relationships will be refined after inspecting the actual survey datasets and identifying their available keys.

| Table | Purpose | Proposed key columns |
|---|---|---|
| DISTRICT | Stores Rwanda district information | district_id (PK), district_name, province |
| CROP | Stores crop reference information | crop_id (PK), crop_name, crop_category |
| AGRICULTURAL_SEASON | Stores agricultural seasons | season_id (PK), season_name, year |
| CROP_PRODUCTION | Stores crop production observations | production_id (PK), district_id (FK), crop_id (FK), season_id (FK), cultivated_area, harvested_quantity |
| FERTILIZER_TYPE | Stores fertilizer categories | fertilizer_type_id (PK), fertilizer_name, fertilizer_category |
| FERTILIZER_SOURCE | Stores fertilizer sources | source_id (PK), source_name |
| FERTILIZER_APPLICATION | Records fertilizer-use information | application_id (PK), fertilizer_type_id (FK), source_id (FK), quantity_applied, application_cost |
| CROP_UTILIZATION | Records documented crop-use categories | utilization_id (PK), production_id (FK), utilization_type, quantity |
| LOSS_CAUSE | Stores post-harvest loss categories | cause_id (PK), cause_name |
| POSTHARVEST_LOSS | Records post-harvest loss observations | loss_id (PK), production_id (FK), cause_id (FK), loss_quantity |
| SUPPLY_ESTIMATE | Stores calculated potential marketable-supply estimates | estimate_id (PK), production_id (FK), estimated_quantity, calculation_date |
| SUPPLY_ALERT | Stores analytical alerts and notifications | alert_id (PK), district_id (FK), alert_type, alert_message |
| SYSTEM_AUDIT | Records important database changes | audit_id (PK), table_name, action_type, action_date |

**Database design consideration:** The fertilizer application and production records will only be directly linked where the survey identifiers and observation levels support that relationship. Otherwise, the system will preserve their actual reporting levels and avoid unsupported joins.

## 6. Planned PL/SQL Features

| Feature | Planned implementation |
|---|---|
| Procedures | Procedures to calculate crop yields, process fertilizer-use records, calculate losses and generate supply estimates. |
| Functions | `calculate_crop_yield()` to calculate harvested quantity per cultivated area; `calculate_loss_percentage()` to calculate recorded loss rates; `calculate_marketable_supply()` to estimate potential supply when utilization data is sufficient. |
| Cursors | Process agricultural observations by crop, district and season for reporting and analysis. |
| Packages | `PKG_CROP_ANALYSIS` for production and yield calculations; `PKG_AGRICULTURAL_INPUTS` for fertilizer-use analysis; `PKG_SUPPLY_ANALYSIS` for loss and potential supply calculations. |
| Triggers | Audit important database changes, validate input quantities and maintain appropriate system records. |
| Exception Handling | Handle invalid quantities, missing reference records, invalid agricultural observations and calculation errors. |
| Scheduler | Where appropriate, schedule periodic analytical processing and generate alerts for defined production or loss conditions. |

### Example Business Rules

- Cultivated area and recorded production quantities must be valid positive values where required.
- Crop yield is calculated using harvested quantity divided by cultivated area, with consistent units.
- Post-harvest loss percentage is calculated using recorded loss quantity divided by harvested quantity, multiplied by 100.
- Potential marketable supply must account for recorded losses and other relevant utilization categories without double-counting.
- Fertilizer costs and application quantities must retain their documented units.
- Analytical alerts may be generated when configured production or loss thresholds are exceeded.

## 7. Repository Structure

The repository will be organized as follows:

```text
Christeva_20251SEN203_RwandaCropIntel/
│
├── README.md
├── .gitignore
│
├── data/
│   ├── README.md
│   └── raw/
│
├── docs/
│   ├── research/
│   │   └── research_log.md
│   │
│   ├── proposal/
│   │   └── project_proposal.md
│   │
│   └── presentation/
│
├── sql/
│   ├── schema/
│   ├── procedures/
│   ├── functions/
│   ├── packages/
│   ├── triggers/
│   └── tests/
│
└── innovation/
    └── apex/
```

## 8. Expected Results

The project is expected to produce:

- A functional and normalized Oracle relational database.
- PL/SQL procedures, functions, packages and triggers for agricultural data processing.
- Agricultural production and fertilizer-use analytical reports.
- Post-harvest loss analysis and potential marketable-supply estimates.
- An interactive Oracle APEX dashboard.
- Technical documentation, testing evidence and a final project presentation.

## 9. Project Scope and Limitations

The initial project focuses exclusively on Rwanda's agricultural production and related analytical information.

It will examine crop production, fertilizer use, productivity, post-harvest losses and potential marketable supply.

It will not implement crop transportation tracking, warehouse stock management, fertilizer inventory management or physical supply-chain monitoring.

The accuracy of the analysis will depend on the variables, coverage, measurement units and quality of the datasets obtained. Fertilizer-use comparisons will show associations with productivity and will not automatically establish causation.

## 10. References

Benimana, G. U., Ritho, C., & Irungu, P. (2021). Assessment of factors affecting the decision of smallholder farmers to use alternative maize storage technologies in Gatsibo District-Rwanda. *Heliyon, 7*(10), e08235. https://doi.org/10.1016/j.heliyon.2021.e08235

Benimana, G. U., Ritho, C., & Irungu, P. (2023). Impact of adopting maize hermetic storage technologies on smallholder farmers' income in Gatsibo District, Rwanda. *Heliyon, 9*(3), e14592. https://doi.org/10.1016/j.heliyon.2023.e14592

Food and Agriculture Organization of the United Nations. (n.d.). *FAO Food Loss App (FLAPP).* https://www.fao.org/platform-food-loss-waste/food-loss/fao-flapp/

National Institute of Statistics of Rwanda. (2025). *Seasonal Agricultural Survey 2025.* https://statistics.gov.rw/sites/default/files/documents/2025-12/SAS%202025%20Final%20report.pdf

National Institute of Statistics of Rwanda. (2025). *Agricultural Household Survey 2024: Main report.*

Oracle. (2026). *Oracle APEX documentation: Visualizing and analyzing data.* https://docs.oracle.com/en/database/oracle/apex/26.1/apxdc/visualizing-and-analyzing-data.html

---

**Project status:** Phase 0 — Research, data source identification and project proposal.
