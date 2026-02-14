# 15-Minute Health-Equity Index (15MinHealthEquity-Chicago)
Assess neighborhood health accessibility in Chicago using 15-minute walking isochrones for pharmacies, parks, grocery stores, and cooling hubs.

## Case Study: Chicago, USA
> **Work in Progress:** This repository represents the design and scoping phase of the project. MVP implementation is ongoing.
---

## Executive Summary

Access to health-promoting assets is a critical determinant of urban well-being. In many cities, residents—particularly those in low-income or underserved neighborhoods—face significant barriers to reaching pharmacies, parks, grocery stores with fresh food, or community cooling hubs within a reasonable walking distance.  

This project develops a reproducible workflow to quantify health accessibility in Chicago using a 15-minute walk threshold. By mapping assets, modeling walkable isochrones, and identifying service gaps, the analysis produces actionable insights for equitable urban planning and targeted interventions.

---

## Policy & Strategic Relevance

This work aligns with global and local priorities:

- **SDG 11.3 / 11.7** — Safe, inclusive, and sustainable urban spaces  
- **SDG 3.d** — Reducing health inequities through accessible urban services  
- **New Urban Agenda** — Promoting urban planning as a public health intervention  
- **City of Chicago Resilience Goals** — Enhancing access to health-promoting resources for all neighborhoods  

---

## Case Study: Why Chicago?

Chicago offers a robust test environment due to:

- Clear socio-economic and spatial disparities across neighborhoods  
- Publicly available datasets for health assets, street networks, and population demographics  
- Walkable urban form with a mix of high-density and low-density neighborhoods  
- Opportunities to evaluate equity and climate resilience impacts  

### Local Urban & Health Risks

- Unequal distribution of pharmacies, grocery stores, parks, and cooling centers  
- Vulnerable populations include elderly, children, and low-income households  
- Heat waves and urban heat islands exacerbate inequities in access to cooling hubs  

---

## Project Objectives

- Map health-promoting assets across Chicago  
- Model 5-, 10-, and 15-minute walking isochrones around these assets  
- Identify “Health Deserts” where residents lack timely access  
- Produce neighborhood-level Health Accessibility Scorecards for planners  
- Support data-driven decision-making for equitable urban resilience  

---

## Methodological Overview

The workflow combines GIS mapping, pedestrian network analysis, and socio-demographic overlay.

**Analytical Components:**

1. **Asset Mapping**  
   - Geolocate pharmacies, parks, grocery stores with fresh food, and cooling hubs  

2. **Isochrone Modeling**  
   - Generate walking polygons at 5, 10, and 15 minutes using QGIS with the ORSA plugin or network analysis tools  

3. **Service Gap Analysis**  
   - Overlay isochrones with population data to identify neighborhoods lacking access  
   - Stratify results by age, income, and other vulnerability indicators  

4. **Equity Scoring**  
   - Compute neighborhood Health Accessibility Score  
   - Highlight areas with highest inequity for prioritization  

5. **Reporting & Visualization**  
   - Produce maps, tables, and scorecards for planners  
   - Optional interactive dashboards for city officials  

---

## Technical Architecture

### Core Tools & Packages

| Tool / Package | Purpose |
|----------------|--------|
| **QGIS** | Spatial visualization, isochrone modeling |
| **ORSA / pgRouting** | Network-based walking analysis |
| **R / tidyverse / sf** | Data preprocessing, spatial joins, metric calculations |
| **leaflet / plotly** | Interactive visualization of health deserts |
| **Quarto** | Reproducible reporting and portfolio-ready outputs |

### Optional Extensions

- Heatwave or climate overlay to assess accessibility to cooling hubs  
- Multi-modal accessibility (biking, public transit)  
- Time-of-day analysis for asset availability  

---

## Project Structure
```
15-Minute-Health-Equity-Chicago/
├── R/  
│ ├── utils.R # CRS handling & helper functions  
│ ├── asset_mapping.R # Geolocation and data cleaning for assets  
│ ├── isochrones.R # Pedestrian network isochrone calculations  
│ ├── equity_scoring.R # Neighborhood Health Accessibility Score calculation  
│ ├── gap_analysis.R # Identify Health Deserts  
│ └── plotting.R # Maps & visualizations  
├── data/  
│ ├── raw/ # Source datasets (read-only)  
│ │ ├── assets/ # Pharmacies, parks, grocery stores, cooling hubs  
│ │ ├── streets/ # Chicago street network (OpenStreetMap / City of Chicago)  
│ │ └── population/ # Census / demographic data  
│ └── processed/ # Cleaned and merged datasets  
├── output/  
│ ├── maps/ # Static 2D maps of accessibility  
│ ├── dashboards/ # Optional interactive maps/dashboards  
│ └── report.qmd # Quarto summary report  
├── renv.lock # Dependency lockfile  
└── README.md # Project documentation  
```
---

## Data Sources

### Urban & Geographic

- **OpenStreetMap / City of Chicago GIS Portal** — street networks, walkable paths  
- **Parks and Public Spaces** — Chicago Park District  
- **Pharmacies & Grocery Stores** — commercial listings, municipal datasets  
- **Cooling Hubs** — Chicago Emergency Management Agency  

### Socio-Demographic

- **U.S. Census / ACS** — population density, age, income, vulnerability metrics  
- Chicago Department of Public Health — neighborhood-level health statistics  

---

## Modeling Workflow

1. **Asset Mapping**  
   - Import and clean location data for all relevant health-promoting assets  

2. **Isochrone Generation**  
   - Calculate walking polygons for 5, 10, 15 minutes using pedestrian network  

3. **Overlay Population Data**  
   - Identify which population segments are within reach of assets  

4. **Health Desert Identification**  
   - Flag neighborhoods with no access within 15 minutes  
   - Apply age and income filters to highlight vulnerable populations  

5. **Equity Scoring & Visualization**  
   - Compute neighborhood Health Accessibility Score  
   - Generate maps and dashboards for urban planners  

6. **Reporting**  
   - Quarto report with methodology, maps, scorecards, and policy recommendations  

---

## Key Indicators

**Accessibility Metrics**

- Percentage of population within 5 / 10 / 15 minutes of assets  
- Number of neighborhoods with zero access within 15 minutes  

**Equity Metrics**

- Correlation of access with income, age, or vulnerability indices  
- Identification of high-priority intervention neighborhoods  

**Portfolio Deliverables**

- 2D accessibility maps  
- Neighborhood Health Accessibility Scorecards  
- Optional interactive dashboards  
- Quarto policy summary report  

---

## Reproducibility & Engineering Practices

- Modular R scripts for each step  
- Dependency management via `renv`  
- Reproducible Quarto report for documentation and portfolio  
- Optional GitHub Actions CI for workflow testing  

---

## MVP Scope (Minimum Viable Product)

**Geographic Scope:** City of Chicago municipal boundary  
**Assets:** Pharmacies, parks, grocery stores with fresh food, cooling hubs  
**Analysis:** 15-minute walking isochrones, Health Accessibility Score calculation  
**Outputs:**  
- 1 static map per asset type  
- 1 combined neighborhood Health Accessibility Score map  
- Quarto summary report  
**Success Criteria:**  
- Fully reproducible end-to-end workflow  
- Clear demonstration of health-equity gaps  
- Maps and outputs suitable for portfolio & LinkedIn  

---

## Known Limitations

- Assumes static walking speed; does not account for physical barriers or mobility constraints  
- Asset data may be incomplete or outdated  
- Aggregation at neighborhood level may obscure intra-neighborhood disparities  

---

## Future Enhancements

**Advanced Modeling**  
- Multi-modal accessibility (public transit, cycling)  
- Time-of-day or seasonal access variations  
- Integration of climate risk layers (heat, flooding)  

**City-Specific Extensions**  
- Policy simulations for placement of new assets  
- Incorporation of public transportation accessibility  
- Scenario modeling for equity-based urban planning  

---

## Project Status

**Stage:** Design & scoping  
**Next Steps:**  
- Acquire Chicago GIS datasets for assets, streets, and population  
- Build preliminary isochrone models  
- Compute initial Health Accessibility Scores  
- Produce first set of maps and Quarto report  

---

## Portfolio Purpose

This repository demonstrates the ability to:  

- Quantify neighborhood-level health accessibility  
- Integrate GIS, network analysis, and socio-demographic data  
- Identify actionable interventions for urban planners  
- Build reproducible, portfolio-ready workflows  

---

## License

To be determined.

---

## Author

Brianna Cole  
Spatial Analytics | Urban Health Equity | Resilience  

---

## Suggested Citation (Future)

Cole, B. (2026). 15-Minute Health-Equity Index: Chicago. GitHub repository.
