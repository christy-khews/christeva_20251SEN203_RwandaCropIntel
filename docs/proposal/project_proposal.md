# PROJECT PROPOSAL

## Rwanda Crop Production and Market Intelligence System

**Student:** Christeva Ikuzwe  
**Student ID:** 20251SEN203  
**Course:** INSY 8311 — Database Development with PL/SQL  
**Domain:** Agriculture and Food  
**Technology:** Oracle Database, PL/SQL and Oracle APEX

### 1. Problem Statement

Agricultural decision-making in Rwanda requires reliable information about crop production, cultivated land, fertilizer use, productivity and post-harvest losses. However, relevant agricultural information may be scattered across different reports and datasets, making it difficult to compare productivity, understand fertilizer-use patterns and estimate potential marketable crop supply.

This project proposes an integrated Oracle database system that organizes and analyzes agricultural production information in Rwanda. It will use PL/SQL for agricultural calculations and business rules, while Oracle APEX will provide interactive dashboards for presenting useful information to support agricultural planning and decision-making.

### 2. Proposed Solution

The proposed system will use Oracle Database to store and organize agricultural information in normalized relational tables. PL/SQL procedures, functions, packages and triggers will process agricultural records, calculate crop yields, analyze fertilizer use, evaluate post-harvest losses and estimate potential marketable supply where sufficient data is available.

An interactive Oracle APEX application will allow users to explore crop production trends, compare fertilizer-use patterns, examine post-harvest losses and view analytical reports by crop, district and agricultural season.

### 3. Data Source

The primary source will be the National Institute of Statistics of Rwanda (NISR) Seasonal Agricultural Survey 2025.

**Source link:** https://www.statistics.gov.rw/print/pdf/node/793

The survey will support research into crop production, cultivated area, agricultural seasons, yields and agricultural practices. Suitable underlying datasets will be identified and inspected before implementation. Additional NISR agricultural reports and credible research publications will support the analysis.

Only appropriate data for educational use will be included, and personal identifying information will be excluded.

### 4. Planned Database Tables

The proposed database will include:

- DISTRICT — stores district information.
- CROP — stores crop reference information.
- AGRICULTURAL_SEASON — stores agricultural seasons.
- CROP_PRODUCTION — records crop production and cultivated area.
- FERTILIZER_TYPE — stores fertilizer categories.
- FERTILIZER_SOURCE — stores fertilizer sources.
- FERTILIZER_APPLICATION — records fertilizer quantities and application costs.
- CROP_UTILIZATION — records documented crop-use categories.
- LOSS_CAUSE — stores post-harvest loss categories.
- POSTHARVEST_LOSS — records crop losses.
- SUPPLY_ESTIMATE — stores calculated potential marketable-supply estimates.
- SUPPLY_ALERT — stores analytical alerts.
- SYSTEM_AUDIT — records important database changes.

The final structure will be refined after inspecting the actual datasets and confirming their relationships.

### 5. Planned PL/SQL Features

- **Procedures:** Process agricultural records and generate production and loss reports.
- **Functions:** Calculate crop yield, fertilizer costs per area, loss percentages and potential marketable supply.
- **Cursors:** Process agricultural observations for crop, district and seasonal analysis.
- **Packages:** Organize production analysis, fertilizer-use analysis and supply calculations.
- **Triggers:** Validate important database operations and maintain audit records.
- **Exception handling:** Handle invalid quantities, missing records and calculation errors.
- **Scheduler:** Support periodic analytical processing and configured alerts where appropriate.

### 6. Planned Innovation

The innovation will be an interactive Oracle APEX dashboard connected to the Oracle database and PL/SQL business logic.

It will provide crop production comparisons, fertilizer-use analysis, productivity trends, post-harvest loss reports and potential marketable-supply estimates. It will also support what-if simulations showing how hypothetical yield improvements or reduced losses could affect potential marketable supply.

All calculations and business rules will remain in PL/SQL, while APEX will provide the interactive user interface.

### 7. Expected Results

The project is expected to deliver a functional Oracle database, reusable PL/SQL components, agricultural analytical reports and an interactive Oracle APEX dashboard. The system will transform available agricultural data into useful information for understanding production performance, fertilizer-use patterns, post-harvest losses and potential marketable supply in Rwanda.

### 8. References

Benimana, G. U., Ritho, C., & Irungu, P. (2021). Assessment of factors affecting the decision of smallholder farmers to use alternative maize storage technologies in Gatsibo District-Rwanda. *Heliyon, 7*(10), e08235. https://doi.org/10.1016/j.heliyon.2021.e08235

Benimana, G. U., Ritho, C., & Irungu, P. (2023). Impact of adopting maize hermetic storage technologies on smallholder farmers' income in Gatsibo District, Rwanda. *Heliyon, 9*(3), e14592. https://doi.org/10.1016/j.heliyon.2023.e14592

National Institute of Statistics of Rwanda. (2025). *Seasonal Agricultural Survey 2025.* https://www.statistics.gov.rw/print/pdf/node/793

Food and Agriculture Organization of the United Nations. (n.d.). *FAO Food Loss App (FLAPP).* https://www.fao.org/platform-food-loss-waste/food-loss/fao-flapp/

Oracle. (2026). *Oracle APEX documentation: Visualizing and analyzing data.* https://docs.oracle.com/en/database/oracle/apex/26.1/apxdc/visualizing-and-analyzing-data.html
