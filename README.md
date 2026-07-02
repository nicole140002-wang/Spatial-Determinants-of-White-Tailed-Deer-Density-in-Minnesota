# Spatial-Determinants-of-White-Tailed-Deer-Density-in-Minnesota
### OLS | GWR | MGWR Comparative Spatial Analysis

## Overview
This project is a multi-scale spatial modeling study investigating the drivers of white-tailed deer density across Minnesota, USA using OLS, GWR, and MGWR regression frameworks.

It compares how ecological, climatic, and anthropogenic factors influence deer distribution under two spatial management scales:
<p align="center">DPA (Deer Permit Areas, fine-scale ~106 units)</p>
<p align="center">
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/b77acdd9-b027-485b-ab96-e6e49c46ac0b" /> 
</p>

<p align="center">DMU (Deer Management Units, coarse-scale ~23 units)</p>

<p align="center">
<img width="300" height="300" alt="dmu" src="https://github.com/user-attachments/assets/2e4fa0de-a9dd-451b-a438-d28b918af6e5" />
</p>

The study highlights how spatial scale (MAUP) and spatial non-stationarity affect ecological interpretation and wildlife management decisions.

## Research Objectives
1) Identify key drivers of deer density across Minnesota
2) Evaluate spatial non-stationarity of ecological relationships
3) Compare performance of:
·OLS (global model)
·GWR (single-bandwidth local model)
·MGWR (multi-scale spatial processes)
4) Assess how spatial aggregation (DPA vs DMU) affects inference
5) Support evidence-based wildlife management zoning

## Methodology Stack
1) ArcGIS Pro
2) Spatial Models: OLS, GWR, MGWR
3) Spatial Statistics: Moran’s I, LISA
4) Feature Engineering: Raster + vector spatial aggregation
5) CRS: EPSG:26915

## Data Sources

| Component            | Source               | Description                  |
| -------------------- | -------------------- | ---------------------------- |
| Deer Density (2021)  | Minnesota DNR        | Response variable            |
| NLCD Land Cover      | MRLC                 | Habitat structure            |
| PRISM Climate        | PRISM Group          | Snow depth / winter severity |
| Road Network         | MnDOT / OSM          | Human accessibility proxy    |
| Hunting Regulation   | MNDNR                | Bag limit policy variable    |
| Administrative Units | Minnesota GIS Portal | DPA / DMU boundaries         |


<p align="center"> Spatial distribution of white-tailed deer density across DPAs in 2021</p> 

<p align="center">
<img width="300" height="300" alt="deer_density" src="https://github.com/user-attachments/assets/e82896c4-d8a6-4bb4-8302-de2386996af5" />
</p>

## Feature Engineering
#### 1. Habitat Suitability Index (HSI)
1) Derived from NLCD reclassification
2) Combines food + shelter availability
3) Normalized 0–1 ecological index

#### 2.Climate Stress
1) Maximum winter snow depth (Jan–Mar)
2) Proxy for survival constraint

#### 3.Human Disturbance
Road accessibility (distance-based metric)

#### 4.Management Pressure
Hunting bag limits (ordinal variable 1–6)

## Analytical Workflow
#### 1. Data Preprocessing
1) CRS harmonization (EPSG:26915)
2) Spatial clipping to Minnesota boundary
3) Zonal aggregation to DPA / DMU
4) KNN imputation for missing values
5) Multicollinearity screening (VIF < 5)

#### 2. Exploratory Spatial Analysis (ESDA)
1) Global Moran’s I (spatial clustering detection)
2) Local Indicators of Spatial Association (LISA)
3) Correlation and multicollinearity analysis

<p align="center"> Local GWR coefficients for four predictors at the DPA scale </p>
<p align="center"> 
<img width="300" height="300" alt="local coefficients" src="https://github.com/user-attachments/assets/29b72642-f9d6-4fbb-aaeb-7b9dc746ed71" />  
</p>

<p align="center"> Local MGWR coefficients for distance to roads </p>
<p align="center">
<img width="300" height="300" alt="Local MGWR coefficients" src="https://github.com/user-attachments/assets/1d052a3e-27f1-415b-b7d0-4e01db6f5042" />
</p>


## Spatial Regression Models 

#### 1. OLS (Global Model)  
1) Baseline linear regression
2) Assumes spatial stationarity

#### 2. GWR (Local Variation Model)
1) Allows spatially varying coefficients
2) Single bandwidth for all variables

#### 3. MGWR (Multi-Scale Model)
1) Each variable has its own spatial scale
2) Captures hierarchical spatial processes

## Model Comparison (Key Results)
#### 1. DPA Scale (Fine Resolution)
1) OLS: R² ≈ 0.63 → Significant residual spatial autocorrelation
2) GWR: R² ≈ 0.72 → Reduced spatial clustering in residuals
3) MGWR: R² ≈ 0.81 (best model) → No significant residual spatial autocorrelation

**Key Finding:**
Road distance = local-scale driver
Habitat & snow = global-scale drivers
Hunting pressure = broad-scale management driver

#### 2. DMU Scale (Coarse Resolution)
1) OLS already performs well (R² ≈ 0.78)
2) Spatial heterogeneity largely smoothed
3) MGWR adds limited improvement

**Key Insight:**
Spatial aggregation reduces detectable local human disturbance effects (MAUP effect)

## Spatial Insights
1) Northern forests: habitat dominates deer density
2) Agricultural south: human infrastructure strongly influences distribution
3) Snow depth consistently suppresses population across all regions
4) Road effects are spatially context-dependent: Forest: edge attraction / Farmland: disturbance avoidance

## Limitations
1) Single-year cross-sectional dataset (no temporal dynamics)
2) Road metrics do not include traffic intensity
3) Hunting data is regulatory proxy, not actual harvest
4) MAUP effects remain due to administrative zoning
5) Missing ecological variables (terrain, disease, land ownership)

## Skills Demonstrated
1) Spatial econometric modeling (OLS / GWR / MGWR)
2) Multi-scale spatial analysis (MAUP evaluation)
3) Remote sensing feature engineering (NLCD-derived indices)
4) Spatial statistics (Moran’s I, LISA)
5） Geospatial data engineering (vector + raster integration)
6） Model diagnostics & spatial validation

## Future Work
1) Temporal MGWR / panel spatial models
2) Integration of traffic volume + actual harvest data
3) Multi-grid spatial comparison (reduce MAUP bias)
4) WebGIS dashboard for wildlife management decision support
5) Extend framework to other ungulate species
