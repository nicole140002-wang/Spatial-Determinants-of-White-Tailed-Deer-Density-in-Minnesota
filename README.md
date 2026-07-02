# Spatial-Determinants-of-White-Tailed-Deer-Density-in-Minnesota
### OLS | GWR | MGWR Comparative Spatial Analysis

## Overview
This project is a multi-scale spatial modeling study investigating the drivers of white-tailed deer density across Minnesota, USA using OLS, GWR, and MGWR regression frameworks.

It compares how ecological, climatic, and anthropogenic factors influence deer distribution under two spatial management scales:
·**DPA (Deer Permit Areas, fine-scale ~106 units)**   
·**DMU (Deer Management Units, coarse-scale ~23 units)**  
   

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/b77acdd9-b027-485b-ab96-e6e49c46ac0b" />    
<img width="300" height="300" alt="dmu" src="https://github.com/user-attachments/assets/2e4fa0de-a9dd-451b-a438-d28b918af6e5" />


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

**Spatial distribution of white-tailed deer density across DPAs in 2021**  

<img width="300" height="300" alt="deer_density" src="https://github.com/user-attachments/assets/e82896c4-d8a6-4bb4-8302-de2386996af5" />


## Feature Engineering
#### 1. Habitat Suitability Index (HSI)
1) Derived from NLCD reclassification
2) Combines food + shelter availability
3) Normalized 0–1 ecological index

#### 2.Climate Stress
1) Maximum winter snow depth (Jan–Mar)
2) Proxy for survival constraint

#### 3.Human Disturbance
1) Road accessibility (distance-based metric)

#### 4.Management Pressure
1) Hunting bag limits (ordinal variable 1–6)

## Analytical Workflow

