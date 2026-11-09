# Data Documentation
## Rwanda Crop Production and Market Intelligence System

**Student:** Christeva Ikuzwe  
**Student ID:** 20251SEN203  
**Project:** Rwanda Crop Production and Market Intelligence System

## 1. Purpose of the Data Folder

This folder contains documentation and, where permitted, prepared datasets required for developing the Rwanda Crop Production and Market Intelligence System.

The data will support analysis of crop production, cultivated land, fertilizer use, productivity, post-harvest losses and potential marketable crop supply in Rwanda.

## 2. Primary Data Source

**Institution:** National Institute of Statistics of Rwanda (NISR)

**Survey:** Rwanda Seasonal Agricultural Survey 2025

**Source link:** https://www.statistics.gov.rw/print/pdf/node/793

The survey is the primary planned source for agricultural statistics covering Rwanda's agricultural seasons.

## 3. Required Data

The project will identify suitable datasets containing the following information:

| Data category | Required information | Planned use |
|---|---|---|
| Geographic information | District and province | Compare agricultural performance by location |
| Crop information | Crop name and category | Organize crop records |
| Agricultural seasons | Season A, B and C | Compare seasonal production |
| Production | Harvested quantities | Analyze crop production |
| Land use | Cultivated area | Calculate crop yields |
| Fertilizer use | Fertilizer types and quantities | Analyze fertilizer application |
| Fertilizer sources | Supplier or source categories | Examine fertilizer sourcing patterns |
| Fertilizer costs | Recorded application expenditure | Analyze fertilizer costs |
| Crop utilization | Recorded crop-use categories | Support supply estimation |
| Post-harvest losses | Loss quantities and causes, where available | Analyze agricultural losses |

The actual availability of these variables will be confirmed by inspecting the original datasets.

## 4. Data Preparation

Before importing data into Oracle Database, the following activities will be performed:

1. Obtain the relevant datasets from NISR or another documented authorized source.
2. Inspect the dataset structure, variables and record counts.
3. Check missing values, duplicate records and inconsistent entries.
4. Verify measurement units for production, area, fertilizer quantities and costs.
5. Identify suitable identifiers and relationships between datasets.
6. Remove personal identifying information and unnecessary fields.
7. Clean and transform the selected records for database loading.
8. Document the data preparation process.

## 5. Data Privacy and Usage

Only data suitable for educational use will be included.

Personal identifying information will not be stored in the project database or published in this repository.

The applicable data access and redistribution conditions will be checked before sharing any downloaded dataset.

## 6. Planned Folder Structure

```text
data/
├── README.md
├── raw/
│   └── Original authorized datasets
└── processed/
    └── Cleaned datasets prepared for Oracle
```

## 7. Data Import and Database Integration

The selected and cleaned data will be prepared for loading into Oracle Database.

SQL scripts and appropriate data-loading methods will be used to populate the normalized database tables.

Data quality checks will be performed after loading to confirm record counts, relationships and data consistency.

## 8. Current Data Status

**Status:** Data source identified; underlying datasets still need to be obtained and inspected.

The published NISR report is a reference source. It should not be treated as the raw dataset.

Actual dataset names, file formats, record counts, variables and licensing conditions will be added after verification.
