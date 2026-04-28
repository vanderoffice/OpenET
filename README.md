[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-green.svg)](LICENSE)
[![Status: Research](https://img.shields.io/badge/Status-Research-blue.svg)]()

# OpenET Evapotranspiration Platform: Comprehensive Research Report

**Prepared for:** State Water Resources Control Board (SWRCB) project evaluation
**Date:** April 9, 2026 (updated April 10, 2026: meter accuracy comparison and regulatory pathway analysis)
**Author:** Brent Vanderburgh

---

## Executive Summary

OpenET is a nonprofit, satellite-based evapotranspiration (ET) platform providing field-scale (30m) actual ET data across all 48 contiguous U.S. states. Built by a consortium led by the Environmental Defense Fund, NASA, USGS, and the Desert Research Institute, it combines six peer-reviewed ET models into an ensemble estimate using Landsat thermal and optical imagery.

**For SWRCB purposes, eight findings matter most:**

1. **SWRCB already uses OpenET.** The Delta Alternative Compliance Plan (Delta ACP), launched March 2023, allows 70%+ of Bay-Delta farmers to report consumptive water use via OpenET satellite data instead of physical meters, under SB 88's measurement regulation (23 CCR section 935). It achieved 98% compliance vs. 39% statewide with physical meters.

2. **Accuracy is well-documented but has limits.** The definitive 2024 *Nature Water* study (152 flux tower sites) shows ensemble accuracy of ~11% MAE annually and ~17% MAE monthly for croplands. Non-agricultural lands perform significantly worse (35-63% relative MAE for forests, shrublands, grasslands).

3. **Physical meters fail the same accuracy standard in practice.** The Bureau of Reclamation's own Water Measurement Manual states field accuracy "often degrades to +/-5% or worse (>+/-10% in nonstandard installations)." LADWP found only 60% of meters complied at all flow rates. 47% of mechanical meters stop functioning properly after 3 years in agricultural conditions. No systematic audit of California agricultural meter accuracy exists.

4. **Meters measure the wrong thing.** Meters capture gross diversions; only 16-40% of diverted water is consumed through ET (the rest returns as percolation and tailwater). OpenET measures actual consumptive use: the water permanently removed from the hydrologic system. For water resource management, consumptive use is the metric that matters.

5. **No new legislation is needed.** Water Code section 1840 says "device or employ a method," which is technology-neutral. Section 1841 delegates broad rulemaking authority to SWRCB. The Board can authorize satellite ET through regulation alone under existing statutory authority.

6. **The strongest interstate regulatory precedent** is the Upper Colorado River Commission's unanimous adoption of eeMETRIC (June 2022) after a nine-year study, resolving decades of incompatible methods across four states and the Bureau of Reclamation.

7. **No state has legislated OpenET by name.** Adoption follows a pattern: existing law creates a measurement requirement, and OpenET is adopted as the compliant method under existing authority. California could be the first state to codify satellite ET in regulation.

8. **A tiered accuracy framework resolves the standards conflict.** Rather than requiring one accuracy standard for all purposes, different tiers for enforcement (+/-5%, meters), compliance reporting (+/-10-15%, meters or satellite ET), and planning (+/-20%, satellite ET) would allow immediate OpenET adoption for reporting while building the evidence base for enforcement use.

---

## Table of Contents

1. [Platform Overview](#1-platform-overview)
2. [Regulatory Case Studies by State](#2-regulatory-case-studies-by-state)
3. [Legislation and Administrative Rules](#3-legislation-and-administrative-rules)
4. [Accuracy and Validation](#4-accuracy-and-validation)
5. [Known Limitations and Biases](#5-known-limitations-and-biases)
6. [Relationship to Physical Water Measurement](#6-relationship-to-physical-water-measurement)
7. [California-Specific Policy Context](#7-california-specific-policy-context)
8. [Data Access and Technical Integration](#8-data-access-and-technical-integration)
9. [Regulatory Risk Assessment](#9-regulatory-risk-assessment)
10. [Physical Meter Accuracy: Spec vs. Reality](#10-physical-meter-accuracy-spec-vs-reality)
11. [The Case for Satellite ET Over Physical Meters](#11-the-case-for-satellite-et-over-physical-meters)
12. [Regulatory Pathways Forward](#12-regulatory-pathways-forward)
13. [Hydrologic Variability: Why One Size Does Not Fit All](#13-hydrologic-variability-why-one-size-does-not-fit-all)
14. [Supplementary Data Requirements for Compliance](#14-supplementary-data-requirements-for-compliance)
15. [Source Index](#15-source-index)

---

## 1. Platform Overview

### Consortium

| Organization | Role |
|---|---|
| Environmental Defense Fund (EDF) | Lead development, stakeholder engagement |
| NASA Ames Research Center / CSUMB | Scientific and technical leadership |
| USGS EROS Center | SSEBop model, Landsat data, accuracy assessment |
| Desert Research Institute (DRI) | Core science team, eeMETRIC |
| Google Earth Engine | Cloud computing infrastructure |
| University of Idaho | eeMETRIC development |
| University of Maryland | DisALEXI model |
| University of Nebraska-Lincoln | Additional model support |
| University of Wisconsin-Madison | Additional model support |
| HabitatSeven | Web platform development |

Over 100 stakeholder entities (growers, water districts, agencies) participated in platform design.

### Six-Model Ensemble

| Model | Type | Lead Institution |
|---|---|---|
| **DisALEXI** | Atmospheric Land Exchange Inverse, sharpened to 30m | University of Maryland / USDA ARS |
| **eeMETRIC** | Earth Engine METRIC (internalized calibration) | University of Idaho / DRI |
| **geeSEBAL** | Earth Engine Surface Energy Balance Algorithm | University of Brazil |
| **PT-JPL** | Priestley-Taylor Jet Propulsion Laboratory | NASA JPL |
| **SIMS** | Satellite Irrigation Management Support (crop-focused) | CSUMB / NASA Ames |
| **SSEBop** | Simplified Surface Energy Balance operational | USGS EROS |

**Ensemble method:** Simple arithmetic mean after Median Absolute Deviation (MAD) outlier removal. Minimum four models retained even if more are flagged. Performance-based weighting has been explored in research (2024 WRR paper) but is not in production.

### Coverage and Resolution

| Dimension | Specification |
|---|---|
| Spatial resolution | 30m x 30m (~0.22 acres per pixel) |
| Temporal resolution | Daily, monthly, annual |
| Geographic coverage | 48 contiguous U.S. states (full CONUS as of Dec 2025) |
| Historical record | 1999-present (varies by model; some back to 1984) |
| Primary satellite | Landsat (thermal + optical) |
| Supporting satellites | Sentinel-2, GOES, Suomi NPP, Terra, Aqua, ECOSTRESS |
| Reference ET sources | gridMET (nationwide), Spatial CIMIS (California only, from 2003) |
| License | CC-BY-4.0 |

### Timeline

| Date | Milestone |
|---|---|
| 2016 | Development begins |
| October 2021 | Public launch, 17 western states |
| 2023 | Expanded to 23 states |
| Early 2025 | Expanded to 27 states |
| December 2025 | Full CONUS coverage (48 states) |

---

## 2. Regulatory Case Studies by State

### California

#### Delta Alternative Compliance Plan (Delta ACP)

> The most mature regulatory implementation of OpenET in the United States.

| Detail | Value |
|---|---|
| **Administering agencies** | Central Delta Water Agency (CDWA), South Delta Water Agency (SDWA), overseen by Delta Watermaster (SWRCB) |
| **Legal basis** | Water Code sections 1840 (SB 88), 5101, 5104; 23 CCR section 935 |
| **Launch date** | March 16, 2023 |
| **Adoption rate** | 70%+ of Bay-Delta farmers in first year |
| **Coverage** | ~415,000 farmed acres, 70+ crop types in the Legal Delta |
| **How it works** | Participants' places-of-use polygons linked to OpenET via API; monthly ET data auto-populates diversion reports to SWRCB's Report Management System |
| **Delta Watermaster quote** | Michael George: OpenET is "the only reliable method for discerning consumptive use" in the Delta's complex tidal hydrology |

#### SGMA Implementation (Statewide)

DWR has a formal contract with OpenET providing free California-specific API access to GSAs.

| GSA / District | Basin | Application |
|---|---|---|
| Merced Irrigation-Urban GSA | Merced County | Groundwater Accounting Platform, consumptive use tracking |
| Colusa Groundwater Authority | Colusa Subbasin | Water budgets, consumptive use, GSP annual reports |
| Glenn Groundwater Authority | Colusa Subbasin | Same (coordinated with CGA) |
| Vina GSA | Butte County | 2023 Annual Report, precipitation/ET analysis |
| Rosedale-Rio Bravo Water Storage District | Kern County | Parcel-level irrigation, water trading platform |
| Madera County GSAs | Madera County | Allocation accounting with flowmeter integration |
| Eastern San Joaquin GSA | San Joaquin County | Water use tracking |
| Butte County GSA | Butte County | Water use tracking |

#### Scott/Shasta Curtailment Evaluation

The Riverbend Sciences study (Asarian, 2023), published on the SWRCB's drought webpage, used OpenET to evaluate 2021-2022 irrigation curtailments:

- **Shasta Valley:** OpenET showed substantial ET reductions in 2022 following curtailments; streamflow increased.
- **Scott Valley:** OpenET showed NO reduction in ET despite curtailment orders. No streamflow increase. Attributed to continued groundwater pumping under Local Cooperative Solutions agreements with inflated baselines and no metering.
- **Conclusion:** "OpenET is an effective tool for quantifying changes in consumptive water use and assessing the effectiveness of water management actions."

### Upper Colorado River Basin (Colorado, Utah, New Mexico, Wyoming)

> The strongest formal adoption of an OpenET model for interstate regulatory water accounting.

| Detail | Value |
|---|---|
| **Body** | Upper Colorado River Commission (UCRC) |
| **Action** | Unanimous adoption of eeMETRIC as standard method |
| **Date** | June 2022 |
| **Study duration** | Nine years (Consumptive Use Study Workgroup) |
| **Participants** | All four Upper Division States, UCRC, Bureau of Reclamation, academic researchers |
| **Why eeMETRIC** | Accuracy, consistency, cost, timeliness |
| **Result** | Bureau of Reclamation now produces Consumptive Uses and Losses Reports using eeMETRIC |

The Colorado River Authority of Utah (CRAU) uses OpenET for historical ET datasets (1991-2023), drought planning, and verification of the System Conservation Pilot Program (SCPP), where participants download monthly eeMETRIC data to measure conservation.

### Nevada: Diamond Valley Critical Management Area

| Detail | Value |
|---|---|
| **Designation** | Sole Critical Management Area in Nevada (2015) |
| **Legal authority** | NRS 534.037, NRS 534.110(7); State Engineer Order 1302 (Jan 2019) |
| **Court status** | Upheld by Nevada Supreme Court, 4-3 ruling, June 16, 2022 |
| **OpenET role** | Field-level consumptive use data integrated into Groundwater Evaluation Toolbox (GET) |
| **Accuracy** | Predicts groundwater pumping with 50-70% variance explained (field scale), 90% (basin scale) |
| **Scale** | ~26,000 irrigated acres, pumping reductions up to 40% |

### Oregon: Harney Basin

| Detail | Value |
|---|---|
| **Agency** | Oregon Water Resources Department (OWRD) |
| **Published** | Statewide ET historical review, November 2024 (1990-2022 data) |
| **Accuracy findings** | Field-scale: ~11-14% MAE/RMSE; basin-scale volume within 17% of metered data |
| **Uses** | Consumptive use tracking, water budget gaps, place-based planning, demand forecasting |

### Nebraska: Twin Platte Natural Resources District

Collaboration with Nebraska Department of Natural Resources for Ogallala Aquifer water budgets and integrated management plans. Aims to achieve sustainability without new regulations.

### Other States

| State | Status |
|---|---|
| **Kansas** | Pilot projects with open-source groundwater accounting platform |
| **Idaho** | Pre-pilot evaluation; participates in Columbia River Basin ET Mapping Tool |
| **Arizona** | Salt River Project integration |
| **Texas** | Water Development Board use case partner |

---

## 3. Legislation and Administrative Rules

### No State Has Legislated OpenET by Name

The adoption pattern across all states: existing law creates the measurement requirement, OpenET is adopted as the compliant method under existing authority.

| Jurisdiction | Legal Authority | How OpenET Fits |
|---|---|---|
| **California** | Water Code sections 1840, 5101, 5104 (SB 88, 2015); 23 CCR section 935 | Delta ACP approved under these sections as alternative compliance |
| **California** | SGMA (AB 1739, SB 1168, SB 1319, 2014) | DWR provides OpenET to GSAs for water budgets/GSP reporting |
| **California** | AB 1755 (2016) Open & Transparent Water Data Act | CA Water Data Consortium incorporates OpenET into groundwater accounting |
| **California** | SB 155 (2021) | Standardized reporting framework under which OpenET-based compliance operates |
| **Nevada** | NRS 534.037, NRS 534.110(7); State Engineer Order 1302 | Diamond Valley GMP uses OpenET; upheld by Nevada Supreme Court |
| **Oregon** | Updated 2024 groundwater rules (OWRD) | Incorporate ET data for stability assessments; OpenET operational |
| **Upper Colorado** | 1922 Colorado River Compact; UCRC Resolution (June 2022) | eeMETRIC formally adopted for interstate accounting |

### Federal Legislation

The **Open Access Evapotranspiration Data Act** (OpenET Act) was introduced by Rep. Susie Lee (D-NV) and Sen. Catherine Cortez Masto (D-NV). Would establish an Open Access Evapotranspiration Data Program within USGS. Status: introduced, no confirmed passage as of April 2026.

---

## 4. Accuracy and Validation

### Definitive Study: Volk et al. 2024, Nature Water

The largest ET accuracy assessment ever published: 152 flux tower sites, 46 cropland sites, 1,791 paired monthly records.

#### Cropland Ensemble Performance

| Time Period | Sites | Bias (MBE) | MAE | RMSE | R-squared |
|---|---|---|---|---|---|
| Monthly | 46 sites (1,791 records) | -5.27 mm (-5.8%) | 15.84 mm (17.3%) | 20.44 mm (22.4%) | 0.90 |
| Growing Season | 39 sites (177 records) | -11.9 mm (-2.0%) | 78.14 mm (12.9%) | 93.79 mm (15.5%) | 0.87 |
| Water Year (Annual) | 16 sites (72 records) | -73.91 mm (-7.5%) | 112.12 mm (11.3%) | 121.87 mm (12.3%) | 0.84 |

#### Ensemble vs. Individual Models (Monthly, Croplands)

| Metric | Ensemble | Individual Model Range |
|---|---|---|
| MAE | 15.84 mm | 17.9-22.7 mm |
| RMSE | 20.44 mm | 23.1-29.1 mm |
| R-squared | 0.90 | 0.81-0.89 |

The ensemble consistently outperforms or matches the best individual model due to error cancellation across models with different physics.

#### Accuracy by Crop Type

| Crop | Monthly MAE (approx.) | Notes |
|---|---|---|
| Annual crops (corn, wheat) | 10-20% | Best performance category |
| Alfalfa | 20-30% RMSE | Bias generally <5% in irrigated conditions |
| Almonds/orchards | ~17% | Shadow effects from taller vegetation |
| Rice | +/-15-20% bias | Standing water complicates modeling |
| Vineyards | 25-35% RMSE | Spatial heterogeneity, variable canopy |
| Wheat | 15-20% RMSE | Among best-performing crops |

#### Accuracy by Land Cover (Non-Agricultural)

| Land Cover | R-squared | Relative MAE | Key Bias |
|---|---|---|---|
| Evergreen/mixed forests | Low | ~35% | Overestimates by 20-25% |
| Grasslands | 0.54 | ~57% | High relative errors despite low absolute errors |
| Shrublands | 0.48 | ~63% | Highest relative uncertainty |
| Wetlands/marshes | Poor | 30-40% RMSE | Systematic underestimation 10-25% |
| Urban/built-up | Very poor | >40% RMSE | Systematic overestimation 15-20% |

#### Accuracy by Region

| Region | Performance | Notes |
|---|---|---|
| Semi-arid (CA Central Valley, Southwest) | Best: RMSE 15-25% | More clear-sky days, strong ET signal |
| Mediterranean zones | MAE 13.3 mm, RMSE 16.5 mm | Best documented performance |
| Humid (Midwest) | RMSE 25-35% | Higher cloud cover causes data gaps |
| High elevation (>2,000m) | Degraded: bias +/-25% | Aerosol optical depth retrieval issues |
| Coastal | Increased uncertainty | Fewer Landsat scenes for interpolation |

#### Seasonal Performance

| Season | RMSE | Bias Pattern |
|---|---|---|
| Summer (Jun-Aug) | 15-20% | Near zero (+/-5%), best performance |
| Spring (Apr-May) | 25-30% | Underestimation 5-15% (lag on green-up) |
| Fall (Sep-Oct) | 20-28% | Overestimation 10-20% (slow on senescence) |
| Winter (Nov-Mar) | 30-40% | Overestimation 15-25%, worst performance |

### Other Validation Studies

| Study | Focus | Key Finding |
|---|---|---|
| Melton et al. 2022, JAWRA | Platform architecture, initial accuracy targets | Established the multi-model framework and stakeholder-informed accuracy goals |
| Knipper et al. 2024, Ag. Forest Meteorology | California almond orchards | Addressed tree crop challenges (shadow, canopy structure) |
| Performance Mapping (WRR 2024) | Performance-based model weighting | Evaluated weighted alternatives to simple mean; SIMS limitations documented |
| Oregon OWRD Historical Review (Nov 2024) | Statewide 1990-2022 | Field-scale 11-14% MAE; basin-scale within 17% of metered data |
| Utah CRAU Review (Jan 2025) | Colorado River Basin 1990-2023 | Confirmed cropland accuracy consistent with Phase II intercomparison |

### Federal Agency Validation

| Agency | Activity |
|---|---|
| **USGS EROS** | Directly assesses accuracy; released performance maps, weights, and datasets for v2.0 |
| **Bureau of Reclamation** | Uses eeMETRIC for official Consumptive Uses and Losses Reports |
| **NASA** | Co-leads development; provides satellite data and GEE infrastructure |

---

## 5. Known Limitations and Biases

### Model-Specific Issues

| Model | Known Issue |
|---|---|
| **SIMS** | Positive bias for rainfed, deficit-irrigated, and fallow ag land; very high positive bias for non-ag land covers |
| **DisALEXI** | Wet bias in arid grasslands; spatial artifacts |
| **eeMETRIC** | Fails when thermal contrasts within images are too small (winter); sensitive to limited clear observations |
| **SSEBop** | No additional cloud screening: outlier ET values from cloud mask errors; overestimation on shaded hillslopes |
| **PT-JPL** | When land cover information is incorrect, alpha adjustment fails, producing low bias |
| **geeSEBAL** | Topographic and climate sensitivity |

### Platform-Level Known Issues (from etdata.org)

1. **Landsat 7 SLC failure artifacts** (May 2003 onward): Wedge-shaped data gaps, especially problematic Nov 2011 through May 2013
2. **ASTER emissivity dataset gaps** in parts of CO, KS, TX: Largest hole ~30x60 km; reduces ensemble to 1-2 models
3. **Unmasked clouds** causing extreme ET values (both high and low)
4. **Problematic interpolation** when zero clear-sky observations exist in a month (defaults to single observation from +/-32 day window)
5. **SIMS positive bias** for rainfed, deficit-irrigated, and fallow fields
6. **California crop type data incorrect** for years other than 2016 and 2018
7. **Coastal regions** have increased uncertainty from fewer Landsat scenes
8. **Low ET conditions** (fallow, pasture) show large ensemble spread with unresolved differences

### Critical Item for California Regulatory Use

> **California crop type data is incorrect for years other than 2016 and 2018.** This is a documented known issue on OpenET's own accuracy page. Since crop type classification influences the SIMS model and some ensemble calculations, this introduces additional uncertainty for California applications outside those two years.

---

## 6. Relationship to Physical Water Measurement

### ET vs. Traditional Water Measurement

| Method | Measures | Strengths | Limitations |
|---|---|---|---|
| **OpenET (satellite ET)** | Total actual ET from all water sources | Field-scale, no instrumentation needed, consistent, wall-to-wall coverage | Cannot distinguish water source; misses return flows |
| **Diversion records** | Gross water taken from source | Direct, legally established | Miss return flows; don't measure actual consumption |
| **Stream gauges** | Streamflow volume | Direct physical measurement | Only at gauge locations; don't measure field-level use |
| **Meters (SB 88)** | Point-of-diversion flow | Direct, legally required | Expensive to install/maintain; measure gross, not net |
| **CIMIS + crop coefficients** | Estimated crop ET (ETc) | Long California track record | Point-based stations; interpolation degrades remotely; estimates, not observations |

### The Critical Legal Distinction

This is the most important conceptual issue for SWRCB regulatory use:

| Concept | Definition | What It Includes |
|---|---|---|
| **Satellite ET (what OpenET measures)** | Total evapotranspiration from all water sources | Precipitation, groundwater, irrigation, soil moisture |
| **Legal consumptive use (what water law typically defines)** | Beneficial, unrecoverable use of diverted/applied water | Only the irrigation-sourced portion that cannot be recovered |

**When the two are nearly equivalent:** Heavily irrigated agriculture in arid regions where precipitation is minimal and groundwater contributions are small. The Sacramento-San Joaquin Delta has complex hydrology (tidal influence, shallow groundwater), which may complicate this equivalence.

**When the gap is substantial:** Mixed rainfed/irrigated systems, areas with significant groundwater contributions, riparian zones, natural lands.

### Basin-Scale Integration

OpenET alone cannot produce a complete water budget. Full accounting requires integration with:
- Stream gauge data (USGS, state networks)
- Diversion records (SWRCB eWRIMS database)
- Return flow estimates
- Groundwater level data (CASGEM/SGMA monitoring)
- Precipitation data (PRISM, gridMET)
- Soil moisture (SMAP, in-situ sensors)

The WestDAAT tool (Internet of Water) combines OpenET ET with water rights, diversions, and gauge data for regional water budgets.

---

## 7. California-Specific Policy Context

### SWRCB Touchpoints

| Program/Initiative | OpenET Connection | Status |
|---|---|---|
| **Delta ACP** | Direct integration via API for SB 88 reporting | Operational since March 2023 |
| **UPWARD/CalWATRS** | Parallel modernization track ($60M); no direct OpenET integration | CalWATRS core completed Nov 2024 |
| **Scott/Shasta Curtailments** | Post-hoc evaluation study hosted on SWRCB website | Published 2023, peer-reviewed 2025 |
| **Water rights curtailments** | Not used for curtailment design or enforcement | No use documented |
| **Cannabis water reporting** | Not used | No proposals found |

### Comparison with Existing California ET Methods

| Feature | OpenET | CIMIS | CalSIMETAW | DETAW | IDC Model |
|---|---|---|---|---|---|
| **What it measures** | Actual ET (ETa) | Reference ET (ETo) | Crop ET (ETc) | Applied water ET | Consumptive use |
| **Method** | Satellite energy balance (6-model ensemble) | Ground weather stations + Penman-Monteith | Crop coefficients x CIMIS ETo | Crop coefficients x CIMIS ETo + local hydrology | Hydrologic model |
| **Spatial resolution** | 30m (field-scale) | Point-based; Spatial CIMIS ~2km | County-level | Delta-regional | Basin/diversion scale |
| **Key user** | DWR (SGMA), Delta Watermaster, GSAs | DWR (statewide standard) | DWR (statewide crop ET reporting) | DWR (Delta operations) | SWRCB (diversion tracking) |

**OpenET's key advantage:** Measures actual ET directly from satellite observations at field scale, rather than estimating ET from weather station data and crop coefficients. Its 30m resolution enables individual field queries that coarser methods cannot provide.

**OpenET's key disadvantage for CA regulatory use:** It measures total ET, not the portion attributable to a specific diversion. California water law cares about how much of a specific diversion was beneficially consumed, not total ET from all sources.

### Agricultural Industry Position

- **Kern Groundwater Authority** (Patty Poire): Concerns about ground validation in Kern subbasin. "Because there's not a lot of equipment on the ground, the data is not as validated."
- **California Farm Bureau Federation:** Publicly supportive, describing OpenET as "promising" for water efficiency and precision farming.
- **Delta water agencies:** Active supporters with cash and in-kind contributions.
- **No organized opposition found** from Western Growers, Kern County Farm Bureau, or irrigation district associations.

Industry appears broadly supportive for voluntary management but cautious about regulatory/enforcement applications where individual field accuracy matters.

### Court Cases and Administrative Proceedings

**No court cases or administrative proceedings have been identified where OpenET data was directly cited, challenged, or used as evidence in California.** However:
- Experts anticipate future litigation as SGMA enforcement tightens
- Water rights attorney Brett Baker (Central Delta Water Agency) has characterized satellite ET as a promising, less invasive alternative to traditional reporting
- Satellite data as digital evidence would require authentication under California Evidence Code (Sections 1400, 1401)

---

## 8. Data Access and Technical Integration

### Web Application

| Resource | URL |
|---|---|
| Main site | https://etdata.org/ |
| Data Explorer | https://explore.etdata.org/ |
| Account portal | https://account.etdata.org/ |

Free access includes viewing field-scale monthly/annual ET for 23+ western states, browsing pre-computed field summaries for millions of agricultural fields, and limited downloads.

### API

**Base URL:** `https://openet-api.org/`
**Authentication:** API keys from account.etdata.org, passed via `Authorization` header

#### Raster API Endpoints

| Endpoint | Purpose |
|---|---|
| `POST /raster/timeseries/point` | ET timeseries for a single lon/lat point |
| `POST /raster/timeseries/multipolygon` | ET timeseries for multiple polygons |
| `POST /raster/export/multipolygon` | Large polygon exports (async) |
| `POST /raster/export/stack` | Stack of raster GeoTIFFs |

#### Geodatabase API Endpoints (Pre-Computed Field-Level)

| Endpoint | Purpose |
|---|---|
| `POST /geodatabase/metadata/ids` | Get OpenET field IDs within a polygon |
| `POST /geodatabase/metadata` | Crop type attributes and area for field IDs |
| `POST /geodatabase/metadata/boundaries` | GeoJSON boundaries for field IDs |
| `POST /geodatabase/timeseries` | Monthly/annual timeseries for field IDs |

#### Key Parameters

- `model`: `"Ensemble"`, `"SSEBop"`, `"SIMS"`, `"DisALEXI"`, `"eeMETRIC"`, `"geeSEBAL"`, `"PTJPL"`
- `variable`: `"ET"`, `"ETo"`, `"ETr"`, `"ETof"`, `"NDVI"`, `"PR"`, `"COUNT"`
- `reference_et`: `"gridMET"` or `"CIMIS"` (California only)
- `interval`: `"daily"`, `"monthly"`, `"annual"`
- `units`: `"mm"` or `"in"`

#### Rate Limits and Quotas

| Tier | Queries/Month | Max Area/Query | Max Polygons | Notes |
|---|---|---|---|---|
| Free (default) | 100 | 50,000 acres | 50 | Basic API key |
| GEE-Linked (free) | 400 | 200,000 acres | 200 | Link Google Earth Engine account |
| CA DWR Contract | Expanded | Expanded | Expanded | Contact support@openetdata.org |

**Rate limits:** 20 requests/minute, 500 requests/hour per user.

### Google Earth Engine (Bulk Access)

All OpenET datasets are published in the GEE Public Data Catalog. This is the recommended path for bulk/large-area access.

**Collection IDs (all v2.0, 30m, monthly):**

| Dataset | Earth Engine Collection ID |
|---|---|
| Ensemble | `OpenET/ENSEMBLE/CONUS/GRIDMET/MONTHLY/v2_0` |
| DisALEXI | `OpenET/DISALEXI/CONUS/GRIDMET/MONTHLY/v2_0` |
| eeMETRIC | `OpenET/EEMETRIC/CONUS/GRIDMET/MONTHLY/v2_0` |
| geeSEBAL | `OpenET/GEESEBAL/CONUS/GRIDMET/MONTHLY/v2_0` |
| PT-JPL | `OpenET/PTJPL/CONUS/GRIDMET/MONTHLY/v2_0` |
| SIMS | `OpenET/SIMS/CONUS/GRIDMET/MONTHLY/v2_0` |
| SSEBop | `OpenET/SSEBOP/CONUS/GRIDMET/MONTHLY/v2_0` |

**Availability:** 1999-10 through 2024-12 on GEE.

### Python Libraries

| Package | Purpose | Install |
|---|---|---|
| `openet-client` | REST API wrapper with geopandas integration | `pip install openet-client[spatial]` |
| `openet-core` | Core functions: cloud masking, interpolation, MAD | `pip install openet-core` |
| `openet-ssebop` | SSEBop model on GEE | `pip install openet-ssebop` |
| `openet-sims` | SIMS model on GEE | `pip install openet-sims` |
| `openet-ptjpl` | PT-JPL model on GEE | `pip install openet-ptjpl` |
| `openet-geesebal` | geeSEBAL model on GEE | `pip install openet-geesebal` |

**R package:** `openet` at https://github.com/codeswitching/openet

**GitHub organization:** https://github.com/Open-ET (15 repositories)

### Data Formats

| Access Method | Formats |
|---|---|
| API raster point timeseries | JSON, CSV |
| API raster export stack | GeoTIFF |
| API geodatabase boundaries | GeoJSON |
| API geodatabase timeseries | CSV |
| GEE export | GeoTIFF, Earth Engine asset, CSV |

### Cloud Platform Availability

OpenET data lives exclusively in the Google Earth Engine ecosystem. It is NOT on AWS Open Data or Azure. Cross-cloud access requires export from GEE to Google Cloud Storage, then transfer.

---

## 9. Regulatory Risk Assessment

### Strengths for SWRCB Regulatory Use

1. **Existing SWRCB precedent.** The Delta ACP demonstrates the Board already accepts OpenET data for SB 88 compliance reporting. This is a strong internal precedent.
2. **Well-validated for croplands.** 11% annual MAE, 17% monthly MAE, documented in *Nature Water* with 152 flux towers.
3. **Interstate precedent.** UCRC's formal adoption after a nine-year study provides a rigorous model for evidence-based agency adoption.
4. **Nevada Supreme Court.** The Diamond Valley GMP (which uses OpenET) survived judicial review.
5. **Consistent, wall-to-wall coverage.** Unlike point-based measurements, provides the same methodology everywhere, eliminating instrumentation gaps.
6. **Open, reproducible.** CC-BY-4.0 license, published methods, individual model outputs available for independent review.

### Risks and Gaps

| Risk | Severity | Detail |
|---|---|---|
| **ET ≠ legal consumptive use** | HIGH | OpenET measures total ET from all sources; water law cares about use of specifically diverted water. In complex hydrology (Delta, areas with shallow groundwater), the gap may be significant. |
| **Non-agricultural accuracy** | HIGH | 35-63% relative MAE for forests, shrublands, grasslands. If SWRCB needs ET estimates for riparian areas, wetlands, or natural lands, OpenET is significantly less reliable. |
| **California crop type data errors** | MEDIUM | Documented incorrect for years other than 2016 and 2018. Affects SIMS model and potentially ensemble quality. |
| **No court testing** | MEDIUM | No California court has ruled on the admissibility or weight of OpenET evidence. First use in enforcement could face challenge. |
| **Individual field accuracy** | MEDIUM | 11% annual MAE is an average across many sites. Individual fields can deviate more, especially for orchards, vineyards, and non-standard crops. |
| **Seasonal bias** | LOW-MEDIUM | Systematic underestimation in spring, overestimation in fall/winter. May affect monthly reporting accuracy. |
| **Data gaps** | LOW | Landsat 7 SLC failure artifacts, cloud masking issues, coastal uncertainty. Generally manageable but need awareness. |

### Recommended Approach for SWRCB

1. **Leverage the existing Delta ACP precedent** as a template for expanded use, since the Board's own Watermaster office has already accepted the methodology.
2. **Contact OpenET about the CA DWR contract** for expanded state-agency API access at no cost.
3. **For any enforcement-grade application**, establish a validation protocol specific to the geography and crop types in question. The 11% annual MAE is an average; local validation matters.
4. **Do not rely on OpenET for non-agricultural lands** without supplementary data. The accuracy drops dramatically.
5. **Address the ET vs. consumptive use distinction explicitly** in any policy document. The Delta ACP's approach (ET as a proxy for consumptive use in irrigated agriculture) works because precipitation is a small fraction of total ET on irrigated Delta farmland. This assumption may not hold in all contexts.

---

## 10. Physical Meter Accuracy: Spec vs. Reality

### The Fundamental Problem

California's water measurement regulation (23 CCR section 933) requires post-2016 devices to achieve +/-5% accuracy (laboratory-certified) or +/-10% accuracy (field-tested for diversions over 100 AF/year). The implicit assumption is that installed meters reliably meet these standards. The evidence says otherwise.

### Laboratory vs. Field Accuracy by Meter Type

| Meter Type | Lab/Spec Accuracy | Real-World Field Accuracy | Source |
|---|---|---|---|
| Propeller/Turbine | +/-2% | +/-2% to +/-5% new; degrades to +/-15% with wear | USBR Water Measurement Manual Ch. 14 |
| Electromagnetic (spool) | +/-0.2-0.5% | +/-0.3-0.5% ideal; +/-1-2% fouled; total system +/-6.9% | USU Extension |
| Electromagnetic (insertion) | +/-0.5-1% | +/-1.0% at low velocity; >=50% error with chemical injection | ITRC Report F20-001 |
| Ultrasonic (clamp-on) | +/-1-2% | Up to 8% error from pipe offsets; sensor drift | USU thesis |
| Ultrasonic (inline) | +/-0.5-1% | Drift requires 6-12 month recalibration | IPS guidance |

> "Some devices reach +/-1% in laboratories, but field accuracies often degrade to +/-5% or worse (>+/-10% in nonstandard installations) without special construction, recalibration, and maintenance."
> -- Bureau of Reclamation, Water Measurement Manual, Chapter 4

### Propeller/Impeller Meter Degradation

Propeller meters are the most common type in agricultural diversions. They are also the most vulnerable to field conditions:

| Degradation Factor | Effect | Accuracy Impact |
|---|---|---|
| Sediment/abrasive particles | Erodes bearings and blades, increases rotor clearance | 5-15% negative bias (under-reading) |
| Bearing wear | Progressive mechanical friction | Negative bias, worsens over time |
| Biological fouling | Organic deposits on blades increase resistance | Negative bias (under-reading) |
| Cavitation | Vapor bubbles chip metal surfaces; impellers wear to 0.3-0.5mm thickness after ~2,680 hours | Severe accuracy loss |
| Low-velocity operation | Small frictional changes produce large errors below 1-1.5 ft/s | Large errors, direction unpredictable |

The USBR warns against permanent propeller installations in water with weeds, debris, or sediment, and requires "continuous inspection and time-based bearing replacement." This describes the majority of California agricultural diversions.

### Electromagnetic Meter Vulnerabilities

EM meters are often presented as the "gold standard" alternative to propellers. Field reality is more complicated:

- **Chemical injection:** ITRC tested 10 mag meters in California irrigation pipelines. Large, continuous upstream chemical injections caused >=50% flow fluctuations due to non-uniform fluid properties.
- **Suboptimal installations:** ITRC field-tested six SeaMetrics AG2000 mag meters on Central Coast strawberry fields. Proximity to valves and filters (only 2-15 pipe diameters of straight run) degraded accuracy from turbulence.
- **Total system accuracy:** USU Extension reports that accounting for velocity measurement error, depth measurement error, pipe configuration, and installation factors, total system accuracy reaches +/-6.9% even with properly functioning meters.
- **Electrode fouling and liner degradation:** Sediment, organic matter, and chemicals degrade electrode surfaces and liners over time.

### The Missing Audit

**No systematic program audits the accuracy of installed California agricultural water meters.**

The state requires +/-10% accuracy but has no mechanism to verify compliance. The contrast with municipal utilities is instructive:

| Audit | Finding |
|---|---|
| LADWP (1,073 small meters tested) | Only 60% complied with AWWA accuracy limits at all flow rates |
| Atlanta DWM | Only one-third of small meters met all accuracy standards |
| General meter aging data | Meters at 10 years show weighted accuracy of ~93-99% (decay 0.68%/year). At 15+ years, cumulative loss of 8-30% |
| Agricultural meters after 3 years | 47% of mechanical meters stop functioning properly |

If a major urban utility with dedicated meter testing programs has 40% non-compliance, agricultural meters with less oversight are almost certainly worse. The 10% accuracy standard is aspirational, not verified.

### Calibration Burden

| Item | Cost | Notes |
|---|---|---|
| Lab calibration (propeller) | $200-$600 | Plus shipping and downtime |
| Lab calibration (magnetic) | $400-$1,000 | |
| Lab calibration (ultrasonic) | $700-$2,000+ | |
| On-site calibration | $500-$2,000+ | Requires qualified technician |
| Calibration interval (regulation) | Every 5 years | 23 CCR section 937 |
| Calibration interval (best practice) | Every 2-4 years (general); 6-12 months (ultrasonic) | |
| Turnaround time | 5-15 business days | Diversion point is unmeasured during this period |

The double-meter rotation described by water users (buying twice as many meters to rotate through calibration while maintaining continuous measurement) is a rational response to the regulatory requirement, but it doubles capital costs. The alternative is to have no measurement at the diversion point for 1-3 weeks during calibration, which technically puts the diverter out of compliance.

---

## 11. The Case for Satellite ET Over Physical Meters

### Meters Measure the Wrong Thing

This is the most important conceptual point for the regulatory argument:

| What meters measure | What OpenET measures |
|---|---|
| **Gross diversion:** volume of water leaving a source | **Consumptive use:** water actually consumed via evapotranspiration |
| Records water taken from the river | Records water permanently removed from the watershed |
| Cannot distinguish between consumed water and return flows | Directly measures the consumed portion |
| Single point at the diversion structure | Every quarter-acre (30m pixel) of the landscape |

A Central Valley-wide analysis found **only 16% of diverted irrigation water is consumed through ET by crops; 84% results in runoff, deep percolation, or conveyance loss** (much of which returns to the system as reusable water).

| Irrigation Method | Water Consumed (% of Diverted) | Return Flow |
|---|---|---|
| Flood/Furrow | 20-40% | 60-80% |
| Sprinkler | 50-85% | 15-50% |
| Drip/Micro | 70-95% | 5-30% |

A meter reading 100 AF diverted with +/-2% precision tells you 98-102 AF was diverted. But only 16-40 AF was actually consumed. OpenET measuring that 16-40 AF consumed with +/-11% error provides a more useful number for water resource management.

### Compliance: 39% vs. 98%

The statewide SB 88 compliance rate with physical meters is **39%** (as of early 2023). The Delta ACP using OpenET achieved **98%** reporting compliance within its first full year.

A measurement regime that 61% of users fail to comply with is not producing useful regulatory data regardless of meter precision. The best meter in the world produces zero regulatory value if the diverter never installs it, never calibrates it, or never files the report.

### Cost Comparison

| Cost Category | Physical Meters | OpenET |
|---|---|---|
| Equipment purchase | $311-$19,840 per point of diversion | $0 |
| Installation | $350-$755 (small); included in purchase (large) | $0 |
| Annual maintenance | $1,000-$5,000 per operation | $0 |
| Calibration | $200-$2,000+ per event, every 5 years | $0 (validated by USGS/NASA against 152 flux towers) |
| Telemetry/SCADA | $2,100-$2,820/year | $0 |
| Reporting labor | $500-$1,000/year (or 8+ hours per report) | Under 10 minutes (Delta ACP) |
| Statewide one-time (SB 88) | $4.7 million | $0 |
| Statewide annual | $470,000 | $0 |
| Typical mid-size ag operation | $10,000-$50,000+/year (including SGMA fees) | $0 |

### Operational Advantages Beyond Accuracy

| Advantage | Detail |
|---|---|
| **Consistency** | Same six satellite models applied uniformly everywhere. No variation by meter type, installer, or calibration state. |
| **Transparency** | Publicly accessible data. Any stakeholder can independently verify. Meters produce private readings. |
| **Historical record** | Data back to ~1999. No comparable record exists for unmetered diversions. |
| **Tamper-proof** | Satellite observations cannot be manipulated at the point of measurement. Physical meters can be bypassed, under-registered, or disconnected. |
| **Zero burden** | Nothing for the water user to install, maintain, calibrate, or report. |
| **Universal coverage** | Every quarter-acre of irrigated land. Meters only cover installed points. |
| **Accuracy stability** | Consistent year over year. Meters degrade from day one. |

### The Delta Experience

Delta farmers described traditional metering as a **"fool's errand."** They tested all available meter technologies without success due to tidal fluctuation, siphon turbulence, debris ingestion, and below-sea-level pumping setups. Brett Baker (water rights attorney, Central Delta Water Agency): satellite ET is "a promising, less invasive alternative."

Delta Watermaster Jay Ziegler: "OpenET, and the use of publicly accessible data measuring ET, is the only way to really discern consumptive use of water in the Delta on a reliable basis."

SWRCB Engineer Lindsay Kammeier: "It is a reliable and accurate way for diverters, wider Delta water interests and the regulator to understand consumptive water use. It improves data collection and reporting for both users and the SWRCB's analysis."

### Cautions

Two areas require honest acknowledgment:

1. **Orchard/vineyard accuracy.** Preliminary UC research (not yet peer-reviewed) suggests OpenET overestimates citrus and pistachio ET by 20-80%. The peer-reviewed almond study (T-REX, USGS 2024) shows 13% accuracy at monthly scale, which is strong. But opponents will cite the citrus numbers.

2. **Diversion volume still matters for some purposes.** Water rights administration sometimes requires knowing how much water left the source (e.g., where return flows are relevant to junior rights holders, or for real-time curtailment enforcement). A hybrid approach using meters at key diversion points and OpenET for consumptive use accounting may be appropriate for some contexts.

---

## 12. Regulatory Pathways Forward

### Statutory Authority Already Exists

**No new legislation is required.** The critical statutory language is in Water Code section 1840, which requires measurement using a "device or employ a method." This language is technology-neutral. It does not mandate physical meters.

Water Code section 1841(a) grants SWRCB explicit authority to "adopt regulations" for measurement and reporting. This delegation is broad enough to authorize satellite ET through regulation alone.

### Current Regulatory Framework (23 CCR Chapter 2.8)

| Section | Purpose | Relevance to Satellite ET |
|---|---|---|
| **931** | Definitions (accuracy = 100 x (measured - actual) / actual) | Defines accuracy standard that satellite ET must meet |
| **933** | Measuring device requirements (+/-5% lab, +/-10% field) | Would need amendment to add satellite ET as approved method |
| **934** | Measurement methods (protocols achieving comparable accuracy) | Already allows non-device methods; could support satellite ET |
| **935** | Alternative Compliance Plans (when strict compliance is infeasible) | Current pathway for Delta ACP; scalable but requires per-region justification |
| **937** | Calibration requirements (every 5 years by qualified individual) | Not applicable to satellite ET; would need parallel validation framework |

### Three Pathways Ranked by Speed and Impact

#### Pathway 1: Expand ACP Framework (6-12 months per region)

**How it works:** Additional regions file ACPs under existing 23 CCR 935 authority, following the Delta ACP model. Each ACP must demonstrate that strict compliance with sections 933/934 is infeasible, unreasonably expensive, or would result in waste or unreasonable use.

| Pro | Con |
|---|---|
| Uses existing authority, no rulemaking needed | Requires per-region justification |
| Delta ACP is proven template | 5-year renewal cycle creates administrative burden |
| Can begin immediately | Does not resolve the statewide accuracy standard question |
| SWRCB has operational experience | Each ACP needs local agency coordination |

**Best for:** Near-term expansion to regions with measurement challenges similar to the Delta (tidal areas, complex hydrology, groundwater-dependent systems).

#### Pathway 2: Amend 23 CCR 933/934 to Add Satellite ET (12-24 months)

**How it works:** SWRCB initiates a standard rulemaking under the Administrative Procedure Act (Gov. Code 11340 et seq.) to add satellite ET as an approved measurement method with defined accuracy standards and conditions.

| Phase | Duration | Requirements |
|---|---|---|
| Initial Notice | Day 0 | Public notice, Initial Statement of Reasons, proposed text, economic/fiscal impact |
| Public Comment | 15-45+ days | Written comments; may extend for multiple rounds |
| Board Adoption | Board meeting | Staff presentation, address all comments, adopt via resolution |
| Final Statement of Reasons | Post-adoption | Respond to all substantive comments |
| OAL Review | 30-60 working days | Six APA standards (clarity, necessity, consistency, etc.) |
| Secretary of State Filing | Post-OAL | Regulations become operative on specified date |

| Pro | Con |
|---|---|
| Statewide applicability; no per-region ACPs needed | 12-24 month timeline |
| Eliminates the argument that satellite ET is an "exception" | Must navigate public comment and potential opposition |
| Sets clear accuracy standards for satellite ET | The 2025 restructuring was a missed window; new cycle required |
| First-in-nation regulatory codification | |

**Recommended approach:** This is the most impactful pathway. It establishes satellite ET as a standard method rather than an exception. The Delta ACP provides the operational track record needed to support the rulemaking.

**Note on timing:** SWRCB is currently amending SB 88 regulations (2025 restructuring, adoption targeted August-December 2025). Those proposed amendments do not address satellite ET. A separate rulemaking cycle would be needed.

#### Pathway 3: New Legislation (18-24 months, unnecessary)

**How it works:** A bill explicitly authorizing satellite ET for water measurement, directing SWRCB to adopt implementing regulations.

| Pro | Con |
|---|---|
| Strongest legal foundation | Unnecessary given existing authority |
| Legislative intent provides political cover | Slower than regulatory pathway |
| Could include funding for validation | Subject to legislative politics |

**Not recommended** unless Pathway 2 encounters legal challenges to SWRCB's authority.

### Proposed Tiered Accuracy Framework

The core regulatory design question is how to reconcile OpenET's ~11% annual accuracy with the current +/-10% standard. A tiered framework resolves this by matching accuracy requirements to use cases:

| Tier | Accuracy Standard | Authorized Uses | Approved Technology |
|---|---|---|---|
| **Tier 1: Enforcement** | +/-5% | Water rights enforcement, curtailment orders, penalty assessments | Lab-certified physical meters |
| **Tier 2: Compliance Reporting** | +/-10-15% | Annual diversion/use reporting, supplemental statements, trend monitoring | Physical meters (non-lab) OR satellite ET with regional ground calibration |
| **Tier 3: Planning and Screening** | +/-20% | Basin-scale water budgets, GSP compliance, drought assessment, historical analysis | Satellite ET without ground calibration, modeled estimates |

This mirrors how air quality monitoring uses reference-grade monitors for enforcement and lower-cost sensors for screening. It also aligns with the current regulation's existing tiered structure (different accuracy requirements for pre-2016 vs. post-2016 devices, different recording frequencies for different diversion sizes).

**For the specific SWRCB goal of using OpenET in lieu of meters for compliance reporting,** Tier 2 is the target. OpenET's 11.3% annual MAE for croplands falls within the +/-15% standard already applied to pre-2016 devices and approaches the +/-10% standard for post-2016 non-lab devices.

### Legal Defensibility

Satellite ET data would need to satisfy evidentiary standards if used in enforcement actions:

| Standard | Requirements | OpenET's Position |
|---|---|---|
| **Daubert** (federal) | Relevance, testability, peer review, known error rate, general acceptance | *Nature Water* study (152 sites, peer-reviewed), documented error rates, growing agency acceptance |
| **Frye** (some state courts) | General acceptance in relevant scientific community | USGS, NASA, USDA, DRI, 6 universities in the consortium |
| **FRE 702** | Expert testimony based on sufficient facts, reliable principles | Six-model ensemble with documented methodology |
| **CA Evidence Code 1400-1401** | Authentication via testimony or circumstantial proof | Automated pipeline from satellite to report provides audit trail |

**No court has ruled against satellite ET data.** No court has tested its admissibility either. The strongest legal position is to (a) codify it in regulation with defined accuracy standards, creating a presumption of reliability, and (b) maintain ground-truth calibration records as supporting evidence.

**Relevant analogies:** Courts routinely admit satellite imagery, GPS data, and remote sensing products. The evidentiary foundation for satellite ET is stronger than many forms of environmental monitoring currently used in enforcement.

### Recommended Strategy

**The strategy must be regional, not statewide.** OpenET's reliability as a diversion proxy varies by at least an order of magnitude across California (see Section 13). A single policy will be wrong everywhere. The approach should sequence regions by suitability.

1. **Immediate (0-6 months): Start where OpenET is strongest.** Expand the ACP model to the Tulare Lake Basin and Southern San Joaquin Valley. Deep groundwater (100+ ft) means total ET closely approximates irrigation consumptive use. Low precipitation (<10% of crop ET) requires only a simple correction. SGMA critically-overdrafted basins have the strongest need and weakest existing measurement infrastructure.

2. **Medium-term (6-18 months): Initiate formal rulemaking.** Amend 23 CCR 933/934 to add satellite ET as an approved measurement method, but with a **regional suitability framework** that defines conditions for use (groundwater depth thresholds, required supplementary data by zone). Use Delta ACP operational data and the *Nature Water* validation study as the evidentiary basis.

3. **Parallel (ongoing): Commission California-specific validation.** Fund a ground-truth study comparing OpenET to metered diversions and flux towers across representative crop types, regions, and hydrologic conditions. Prioritize: (a) orchards/vineyards given the preliminary UC findings, (b) rice paddies given standing-water biases, and (c) Delta crops to quantify the groundwater contribution gap.

4. **Parallel (ongoing): Adapt existing DWR models.** Work with DWR to integrate OpenET as input to CalSIMETAW, DETAW, and IDC. These models already solve the precipitation/groundwater subtraction problem. Using satellite-measured actual ET instead of estimated Kc-ETo would combine OpenET's measurement strength with the models' accounting framework.

5. **Stakeholder engagement:** The agricultural industry is broadly supportive of OpenET for voluntary use. Converting that support to regulatory acceptance requires demonstrating that satellite ET reduces their compliance burden (cost, time, complexity) without creating new enforcement risk. The Delta ACP's 98% compliance rate (vs. 39% with meters) is the strongest talking point.

6. **Long-term: Address the groundwater contribution gap.** Fund field research to quantify groundwater contribution to crop ET in shallow-groundwater areas (primarily the Delta and near-river zones). Until this data exists, OpenET-based compliance in shallow-groundwater areas should be understood as reporting total consumptive use, not diversion-specific consumptive use.

---

## 13. Hydrologic Variability: Why One Size Does Not Fit All

### The Core Problem

OpenET measures **total evapotranspiration from all water sources combined**: precipitation, applied irrigation, and groundwater uptake. California water law requires knowing how much of a **specific diversion** was consumptively used. The gap between "total ET" and "irrigation-sourced ET" varies enormously across California's diverse hydrology.

```
Irrigation Consumptive Use = Total ET (OpenET) - Effective Precipitation - Groundwater Contribution
```

In the Tulare Lake Basin (deep groundwater, low rainfall), that equation simplifies to roughly: Irrigation Consumptive Use ≈ Total ET. In the Delta (groundwater at the surface, complex seepage), the groundwater term is large but unquantified, making the equation unreliable without supplementary data.

### Regional Suitability Matrix

| Region | GW Depth | GW Contribution to ET | Precip Contribution | OpenET as Total Consumptive Use | Source Attribution Complexity | Key Issue |
|--------|----------|----------------------|--------------------|-------------------------------|-------------------------------|-----------|
| **Tulare Basin** | 100-1,000+ ft | Zero | <10% | **Excellent** | **High**: conjunctive use universal, water banking, 6+ right types per farm | ET accuracy is strong; attributing ET to specific water rights is the problem |
| **Imperial Valley** | 100-500+ ft | Zero | <5% | **Excellent** | **Low-Moderate**: primarily Colorado River (IID/CVWD) | Simpler rights structure; most water from single source |
| **Central San Joaquin** | Variable (50-800 ft) | Low-moderate | 10-15% | **Good** (where GW deep) | **Moderate-High**: mixed surface/GW | Need local GW depth data + district delivery records |
| **Sacramento Valley** | 10-100 ft | Low-moderate | 15-35% | **Moderate** | **Moderate**: CVP + local rivers + GW | Precip correction significant; rice has standing-water bias |
| **Salinas Valley** | 50-300 ft | Low | 10-20% | **Moderate-Good** | **Moderate**: primarily local GW + Nacimiento/San Antonio | Fog reduces satellite observations |
| **Delta** | 2-4 ft | **High (unquantified)** | Moderate | **Poor as diversion proxy** | **Moderate**: primarily surface diversions from Delta channels | Shallow GW inflates ET well beyond diversion use |
| **Mountain/Foothill** | Variable | Variable | Variable | **Poor** | **Low**: typically single riparian diversion | Small fields, mixed cover, terrain effects |

### Region-by-Region Analysis

#### Tulare Lake Basin / Southern San Joaquin Valley: Best for Total ET, Complex for Source Attribution

When groundwater is 100+ feet deep, capillary rise and root access to the water table are physically impossible. Plant roots typically extend 3-6 feet; capillary rise in most soils reaches 1-3 feet above the water table. At 100+ ft depth, the groundwater contribution to ET is effectively **zero**.

| Parameter | Value |
|---|---|
| Depth to groundwater | 300-1,000+ ft (wells typically 150-2,000 ft) |
| Overdraft | ~2 million acre-feet/year |
| Annual rainfall | 5-8 inches |
| Irrigated acres | ~3 million |
| Precipitation share of crop ET | <10% |
| Agriculture's share of water use | 97% |

In the Tulare Basin: **Total ET = Effective Precipitation + Applied Water (all sources)**. The precipitation correction is small and well-characterized. DRI/NASA studies confirm OpenET supports SGMA water budgets at field-scale where meters are scarce.

**OpenET accurately measures total consumptive use here.** But that is not the same as measuring consumptive use under a specific water right.

#### The Conjunctive Use Reality

Conjunctive use of surface water and groundwater is near-universal in the Tulare Basin. Virtually every farm operates with access to both, and the ratio shifts dramatically by water year type:

| Condition | Groundwater Share | Surface Water Share |
|---|---|---|
| Wet years (e.g., 2011, 2023) | ~25-40% | ~60-75% |
| Normal years | ~40-60% | ~40-60% |
| Drought years (e.g., 2014-2015, 2021) | ~70-90% | ~10-30% |

During the 2012-2016 drought, San Joaquin Valley groundwater pumping surged to 8-9+ MAF from a 1960s baseline of ~4.8 MAF.

#### Multiple Surface Water Systems

The Tulare Basin is served by multiple major conveyance systems, each with different water rights frameworks:

| System | Annual Delivery (approx.) | Variability | Rights Type |
|---|---|---|---|
| **Friant-Kern Canal (CVP)** | 1.0-1.2 MAF average | 58,000 AF (2015) to 1,720,000 AF (2005) | Federal contract (Class 1/Class 2) |
| **California Aqueduct (SWP)** | ~1 MAF to East Branch | 17,000 AF (1962) to 3.7 MAF (2006) statewide | State contract (Table A) |
| **Kings River** | 1.8 MAF average | Largest southern Sierra river | Pre-1914 appropriative + post-1914 |
| **Kern River** | 515-621,000 AF median | 82,000 to 2,318,000 AF | Pre-1914 + post-1914 + adjudicated |
| **Kaweah/Tule Rivers** | Smaller volumes | Highly variable | Mixed rights |

A single Tulare Basin farm may hold or receive water under **six or more distinct legal categories simultaneously:**

1. Pre-1914 appropriative rights (not subject to SWRCB permitting)
2. Post-1914 appropriative rights (SWRCB permits)
3. CVP contract water (Bureau of Reclamation, Friant Division)
4. SWP contract water (DWR, Table A amounts)
5. Groundwater (historically unregulated, now under SGMA)
6. Water transfers, exchanges, recycled water

**OpenET sees one number: total crop ET.** It cannot tell you whether that ET came from the CVP allocation, the SWP allocation, the Kings River right, or the groundwater well.

#### Kern County Water Banking: Source Attribution at Its Hardest

Kern County operates one of the world's largest groundwater banking systems (~$300M invested since 1977, ~5.7 MAF total storage capacity). Major facilities include the Kern Water Bank, Semitropic WSD (1.65 MAF capacity), Rosedale-Rio Bravo WSD, and Arvin-Edison WSD.

Water banking creates a source attribution problem that no satellite technology can solve:

1. **Physical indistinguishability.** SWP water spread in recharge ponds percolates into the aquifer and becomes molecularly identical to native groundwater. No measurement technology can distinguish banked from native groundwater when pumped.

2. **Temporal displacement.** Water banked in a wet year may be recovered 3-5 years later in a drought. OpenET measures consumption in real time, but the water right that authorized the water traces back to a different allocation year.

3. **Loss accounting ambiguity.** Rosedale-Rio Bravo's 3:1 storage-to-recovery ratio means 2/3 of stored water is "lost" to aquifer spreading. Whether that loss counts against the original SWP right or local groundwater yield is legally undefined.

#### The Back-Calculation Method: A Partial Solution

Irrigation districts in the Tulare Basin typically track surface water deliveries to individual farms (volumetrically measured at district turnouts). This enables a residual calculation:

> **Groundwater Pumping = Total ET (OpenET) - Surface Water Delivered - Effective Precipitation**

This has been validated outside California with promising results:

| Study Location | Method | Accuracy |
|---|---|---|
| Diamond Valley, NV | OpenET minus precip | 7% at basin scale; 11-14% field scale |
| Harney Basin, OR | OpenET minus precip | 17% error |
| Multi-site (DRI 2024) | OpenET minus precip/surface water | 1.6-4.9% bias (multi-year) |

**No California study has validated this method.** The approach has not been peer-reviewed for regulatory enforcement use. Factors that degrade accuracy include deep percolation (unaccounted), canal seepage (surface delivery overstatement), and soil moisture storage changes.

**The back-calculation method tells SWRCB total groundwater pumping, but not which type of groundwater right it falls under** (native vs. banked, pre-SGMA allocation vs. post-SGMA cap). That is a legal-structural gap, not a data gap.

> **Revised assessment:** The Tulare Basin is the best region for OpenET as a measure of **total consumptive use**. But using it for **source-specific water rights administration** requires pairing OpenET with district delivery records, and even then, the multi-source attribution problem remains unsolved for farms with commingled water supplies. The most realistic near-term application follows the Delta ACP model: report total consumptive use via OpenET, handle source attribution through separate administrative records.

#### Sacramento-San Joaquin Delta: The Hardest Case

| Parameter | Value |
|---|---|
| Depth to groundwater | 0.8-1.2 m (2.6-3.9 ft) below land surface |
| Land subsidence | -3 to -9 m below sea level across ~100,000 ha |
| Total crop ET | ~1.4 million acre-feet/year |
| Groundwater contribution to crop ET | **High but unquantified** |

Shallow water tables (2.6-3.9 ft) enable significant capillary rise and direct root access to groundwater. The peat soils create "saucer-shaped" topography on subsided islands, with seepage inflows from channels sustaining the shallow water table. **No published study directly quantifies the fraction of crop ET from groundwater vs. applied irrigation in the Delta.**

The DETAW model (DWR) estimates applied water as total crop ET demand minus effective rainfall and seepage (a proxy for groundwater contribution), but does not isolate uptake fractions. Seven models agree within 11% on total ET, but none partition by source.

> **The Delta is paradoxically where satellite ET was first adopted (via the Delta ACP) and where its proxy relationship to diversions is weakest.** The Delta ACP reports total ET as the compliance value without subtracting groundwater contributions. Whether this matters depends on whether SWRCB's goal is measuring total consumptive use (for basin-level water budgets) or diversion-specific consumptive use (for water rights enforcement). These are different questions.

#### Sacramento Valley: Rice and Mixed Conditions

| Parameter | Value |
|---|---|
| Depth to groundwater | 10-100 ft (variable) |
| Annual rainfall | 18-20 inches |
| Precipitation share of crop ET | 15-35% (higher in wet years) |
| Rice growing season ET | 29-34 inches (April-September) |
| Rice total water use | 3.6-7.7 acre-feet/acre (including seepage/percolation) |

Standing water in rice paddies creates **significant biases** in thermal ET models. Standing water cools surfaces uniformly, reducing the land surface temperature variability that energy-balance models rely on. SEBAL showed rice ET 5% higher than ground-based Surface Renewal, with larger discrepancies for wet surfaces. Winter flooding for waterfowl habitat adds 5-10 inches to annual ET.

Northern Sacramento Valley precipitation contributes **15-35% of total crop ET** via stored soil moisture, a significant correction factor that varies substantially between wet and dry years.

#### Coastal California: Fog and Data Gaps

Fog **suppresses** ET rather than supplementing it. The primary mechanism is reduced solar radiation and vapor pressure deficit, which lowers evaporative demand. Direct fog drip is minimal (4 mm total over a summer season). Crops in foggy coastal areas need less irrigation than inland crops of the same type, and OpenET should capture this lower ET.

The bigger issue is **data availability**: marine layer cloud cover directly contaminates Landsat observations, reducing the number of usable satellite images. OpenET's multi-temporal interpolation partially compensates, but coastal zones have wider temporal gaps in the data.

#### Mountain/Foothill Watersheds: The Other Hard Case

| Issue | Impact |
|---|---|
| Steep terrain | Shadows, aspect-dependent solar radiation |
| Small field sizes | Mixed pixels at 30m resolution; fields under 2-5 acres are problematic |
| Mixed land cover | Adjacent forest/riparian/agriculture causes pixel contamination |
| Natural vegetation accuracy | 35% (forests), 50-63% (shrublands/grasslands) |

Mountain/foothill areas combine the worst OpenET accuracy (small fields, steep terrain, mixed cover) with the most complex hydrology (riparian groundwater, variable precipitation). These are probably the hardest areas for satellite-based regulation and may still require traditional measurement.

### Groundwater Contribution to ET: What the Global Literature Shows

This is the single most important variable determining whether OpenET works as a regulatory proxy for diversion consumptive use. Field-scale ET source partitioning is an **active research frontier, not a solved problem**. No regulatory agency anywhere in the world has operationalized it. However, a substantial body of research (primarily from China, Pakistan, the US Great Plains, and California) provides consistent quantitative estimates.

#### The Consistent Finding: Exponential Decay with Depth

Across all published studies, groundwater contribution to crop ET declines exponentially with water table depth and becomes negligible beyond approximately 2.5-3.0 meters (8-10 feet) in most soils.

| Water Table Depth | GW Contribution to Crop ET | Confidence | Key Sources |
|---|---|---|---|
| < 0.5 m (< 1.6 ft) | **60-80%+** (but waterlogging reduces yields) | High | Kahlown & Ashraf 2005, Liu et al. 2022 |
| 0.5-1.0 m (1.6-3.3 ft) | **40-75%** | High | Luo & Sophocleous 2010, Kahlown 2005 |
| 1.0-1.5 m (3.3-5 ft) | **20-50%** | High | Luo & Sophocleous 2010, Liu 2022, Han 2018 |
| 1.5-2.0 m (5-6.5 ft) | **10-30%** | Moderate | Deines et al. 2024, Hetao studies |
| 2.0-2.5 m (6.5-8 ft) | **5-15%** | Moderate | Deines 2024, Soylu 2011 |
| 2.5-3.0 m (8-10 ft) | **< 5%** | Moderate | Luo & Sophocleous 2010 |
| > 3.0 m (> 10 ft) | **Negligible (< 3%)** | High | Multiple studies |

These ranges vary by soil texture (clay sustains capillary rise from deeper tables), crop rooting depth, salinity, and climate. The "optimal subsidy zone" where groundwater benefits crops without waterlogging is consistently identified as 1.1-2.5 m across studies.

#### Published Field-Scale Studies

| Study | Location | Crop | Method | GW Contribution Finding |
|---|---|---|---|---|
| **Luo & Sophocleous (2010)** *J. Hydrology* | Kansas, USA | Winter wheat | Lysimeters + HYDRUS-1D modeling | 75% at 1.0 m depth (no irrigation), 3% at 3.0 m (irrigated). Gold-standard quantification. |
| **Shouse et al. (2011)** *Agric. Water Manag.* | **San Joaquin Valley, CA** | Multiple crops | USDA-ARS field data review | Up to 50% of crop water from shallow GW depending on salt tolerance and GW quality |
| **UC Davis (Hopmans, Grismer)** | **Western SJV, CA** | Cotton | Extension research + field measurements | 40-60% of cotton ET from shallow groundwater |
| **Kahlown & Ashraf (2005)** | Pakistan | Wheat, sunflower | Lysimeters with controlled water tables | No supplemental irrigation needed at 0.5 m; 41% at 1 m, 6% at 2 m |
| **Huang et al. (2016)** | Hetao, Yellow River, China | Irrigated crops | 8-year field dataset + daily ET model | Mean 228 mm/year GW-ET = 20-40% of total ET |
| **Liu et al. (2022)** *Agric. Water Manag.* | China | Maize (saline GW) | SIMDualKc + lysimeters | 40-60% at 0.4 m, <20% at 1.2 m |
| **Han et al. (2018)** *HESS* | NW China | Cotton | HYDRUS-1D + simplified crop model | Capillary rise = ~23% of crop transpiration at 1.84 m avg depth |
| **Deines et al. (2024)** *PNAS* | US-wide | Multiple | Observational evidence | 3.4% mean yield boost from GW; 7% in drought years |

#### Available Methods for ET Source Partitioning

| Method | How It Works | Strengths | Limitations |
|---|---|---|---|
| **Lysimeters** | Weighing containers with controlled water tables measure GW uptake directly | Gold-standard direct measurement | Expensive, site-specific, limited locations globally |
| **Stable isotopes (d18O, d2H)** | Irrigation, precipitation, and groundwater have distinct isotopic signatures; plant xylem water reveals source mix | Can distinguish three water sources if signatures are distinct | Intensive sampling required; end-member uncertainty; no study has achieved full three-source crop ET partition at field scale |
| **Soil water balance (residual)** | ET = Irrigation + Precipitation + Capillary Rise - Drainage - Storage Change; solve for capillary rise | Uses standard hydrologic data | Requires accurate measurement of all other terms; errors accumulate |
| **Coupled vadose zone models (HYDRUS-1D, SWAP-WOFOST)** | Simulate water movement through unsaturated zone including capillary rise from water table | Physics-based, can vary conditions | Highly sensitive to soil hydraulic parameters; requires local calibration |
| **USGS VegET/NetET** | Separates "green water" ET (precipitation-sourced) from "blue water" ET (irrigation + GW) at 1 km resolution | Operational USGS product; adopted by Bureau of Reclamation | 1 km too coarse for field-scale; does not separate irrigation from GW within "blue water" |

#### What Does NOT Exist

- **No satellite method** can determine groundwater contribution. Satellites measure total ET from the land surface. Partitioning requires ancillary data (groundwater levels, soil moisture profiles, irrigation records).
- **No regulatory agency anywhere** has operationalized field-scale ET source partitioning.
- **The USGS has not** published field-scale validation of the groundwater component of crop ET.
- **Australia's Murray-Darling Basin** research, despite extensive irrigation regulation, has the same gap: no field-scale crop ET source partitioning.
- **European Mediterranean agriculture** (Spain, Italy) has the same gap.
- **No existing water accounting framework** (including the Water Accounting Plus framework) explicitly separates groundwater ET for water rights administration.

#### California-Specific Research That Exists

Two California research groups have directly measured groundwater contribution to crop ET:

1. **USDA-ARS (Ayars, Soppe, Hutmacher):** San Joaquin Valley field studies documenting up to 50% of crop water use from shallow groundwater. Published as Shouse et al. 2011.

2. **UC Davis (Hopmans, Grismer):** 40-60% of cotton ET from shallow groundwater in western San Joaquin Valley. Published as extension guidance and research papers.

Neither study was designed for regulatory application, and neither covers the Delta's unique peat-soil/tidal hydrology. But they provide the scientific foundation and demonstrate the magnitude of the effect in California conditions.

#### What a California Regulatory Study Would Require

For SWRCB to have field-scale groundwater ET partitioning data for the Delta and other shallow-GW areas:

| Component | What's Needed | Estimated Timeline |
|---|---|---|
| **Dense GW monitoring** | Continuous water table monitoring across Delta agricultural parcels (minimum quarterly, ideally hourly) | 1 year to install; 2+ years of data |
| **Soil hydraulic characterization** | Delta peat and mineral soils have distinctive properties; capillary rise parameters need site-specific calibration | 6-12 months |
| **Lysimeter installation** | 2-4 weighing lysimeters at representative Delta sites with controlled water tables | 12-18 months to build; 2+ growing seasons of data |
| **Isotopic validation** | Delta conditions are favorable: Sacramento River water (Sierra snowmelt) has a very different d18O signature from local precipitation and Delta groundwater | 1-2 growing seasons of sampling |
| **Coupled model development** | Link OpenET satellite ET with a groundwater flow model (MODFLOW) and vadose zone model (HYDRUS) to partition ET sources per field | 12-24 months of model development |
| **Total estimated timeline** | 3-5 years for a pilot; less if scoped to a few representative Delta islands | |

**The regulatory implication:** This research is worth doing, but it should not block OpenET adoption in deep-groundwater areas (Tulare Basin, Imperial Valley) where the groundwater contribution is zero and the partitioning problem does not exist. The strategy should sequence: adopt OpenET where the science is clear now, fund the research to extend it to shallow-GW areas later.

### Precipitation Correction: Required Everywhere

Even in dry areas, precipitation contributes to crop ET. The correction varies by region and year:

| Region | Annual Rainfall | Precip Share of Crop ET | Wet Year Variation |
|---|---|---|---|
| Southern SJV / Tulare | 5-8 inches | <10% | Up to 15% in wet years |
| Central SJV | 8-12 inches | 10-15% | Up to 20% |
| Northern Sacramento Valley | 18-20 inches | 15-35% | Up to 40% in very wet years |
| Salinas Valley | 12-15 inches | 10-20% | Up to 25% |
| Imperial Valley | 2-3 inches | <5% | Negligible |

California's regulatory framework defines effective precipitation as **25% of total annual precipitation** (or a lower CalSIMETAW-modeled value). This 25% rule-of-thumb is crude. The USGS VegET/NetET approach (separating "green water" ET from "blue water" ET) or CIMIS-based daily soil-deficit calculations would be more accurate.

### Return Flows and the Double-Counting Problem

In **shallow groundwater areas**, deep percolation from irrigation rapidly recharges the water table and is frequently re-consumed via ET from crops or phreatophytes. This creates a recycling effect where the same water contributes to ET multiple times. OpenET captures each cycle of ET but cannot distinguish recycled water from new diversions.

In **deep groundwater areas**, deep percolation is essentially lost to the deep aquifer (especially where the Corcoran Clay acts as an aquitard). Central Valley saline sinks receive ~843,000 acre-feet/year of irrecoverable percolation. The double-counting problem is minimal here.

| Irrigation Method | Deep Percolation (% of applied) | Return Flow Character |
|---|---|---|
| Flood/Furrow | 20-40% | High tailwater + deep percolation; recycled in shallow GW areas |
| Sprinkler | 10-20% | Intermediate; moderate recycling potential |
| Drip/Micro | <10% | Minimal return flow; ET closely matches applied water |

### The USGS NetET Product: A Potential Solution

The USGS produces a product that directly addresses the ET source partitioning problem:

- **VegET** (root-zone water balance model): captures ET from "green water" (precipitation) sources only
- **SSEBop ET**: total water use from all sources
- **NetET = SSEBop ET - VegET = irrigation water use estimate**

This was adopted in 2022 by the Bureau of Reclamation and Upper Colorado River Commission. However, it operates at 1 km resolution (too coarse for field-scale California regulation) and does not separate irrigation-sourced blue water from groundwater-sourced blue water. Combining OpenET's 30m field-scale accuracy with USGS's source-partitioning methodology could yield a superior regulatory product.

---

## 14. Supplementary Data Requirements for Compliance

### OpenET Is Not a Magic Bullet

OpenET provides a high-quality measurement of total ET. Converting that to regulatory-grade "irrigation consumptive use" requires accounting for hydrologic context. The supplementary data requirements form a stack, and each layer addresses a specific gap between what OpenET measures and what water law requires.

### The Supplementary Data Stack

| Layer | Data Needed | Best Available Source | Current Gap |
|---|---|---|---|
| **1. Crop Type** | Annual field-level crop ID | DWR Statewide Crop Mapping (only 2016/2018/2019); USDA CDL for other years | No annual statewide mapping; CDL weak on CA specialty crops |
| **2. Precipitation** | Effective precipitation at field scale | gridMET (~4 km) with soil-deficit calculation | No field-scale validation in CA; 4 km resolution vs. field boundaries |
| **3. Groundwater Depth** | Seasonal water table levels near points of use | CASGEM + SGMA monitoring wells | No protocol for flagging phreatophytic ET zones; thresholds are site-specific |
| **4. Soil Properties** | Water holding capacity, texture | SSURGO (1:24,000) | Integration with OpenET not standardized |
| **5. Water Source ID** | Which right supplies which field | Self-reported via CalWATRS + meter data where available | **No satellite method to attribute ET to specific rights** |
| **6. Irrigation Method** | Flood, sprinkler, drip | DWR periodic surveys (1991, 2001, 2010) | No current statewide data; not part of water rights reporting |
| **7. Diversion Season** | Permit-specific diversion periods | CalWATRS water right records | Partial-month alignment requires daily pro-rating |
| **8. QC Flags** | Cloud, model failure, crop misID detection | OpenET v2.1 QA_PIXEL + ensemble flags | No regulatory-grade flag system; no independent validation protocol |

### What the Delta ACP Actually Collects (and Doesn't)

The Delta ACP collects three core data elements from OpenET:
- Digitized Place of Use (POU) boundary polygons
- Monthly evapotranspiration estimates per POU
- POU acreage under claimed beneficial use

The Delta ACP **does not independently collect crop type, irrigation method, or detailed supplemental field data**. It prepopulates most Supplemental Statement fields using satellite-derived ET and historical report responses. Participants verify and submit.

**The Delta ACP does not correct for groundwater contribution.** In the Delta, where water tables are 2-4 feet deep, this means reported "consumptive use" likely overstates actual diversion use by an unknown amount. SWRCB has determined OpenET is a "scientifically-sound basis for accurately measuring ET," but this determination addresses ET accuracy, not the proxy relationship between ET and diversion consumptive use.

### The Water Source Attribution Problem

This is the **single hardest unsolved problem** for ET-based water rights compliance, and it applies across all of California, not just shallow-groundwater areas.

OpenET measures total ET at the field level without differentiating by water source. When a field receives water from surface diversions, groundwater pumping, recycled water, and/or transfers simultaneously, there is no way to attribute a portion of ET to a specific water right from satellite data alone.

**This problem is most severe in the Tulare Basin,** where conjunctive use is near-universal. A single farm may hold pre-1914 Kings River rights, a CVP contract (Friant Division), SWP Table A water, groundwater pumping rights under SGMA, and water transfer agreements, all irrigating the same fields. The ratio of surface-to-groundwater shifts from ~75/25 in wet years to ~10/90 in drought years. OpenET sees one ET number regardless.

In Kern County, groundwater banking adds another layer: SWP water recharged into the aquifer becomes physically and molecularly identical to native groundwater. When pumped years later, no technology can distinguish banked from native water. The Kern Water Bank (~5.7 MAF capacity) represents over $300M in infrastructure built on this commingling.

**California water law has no framework for attributing commingled consumption to specific rights.** Each layer of rights developed independently, assuming relatively exclusive water sourcing. The statutes do not authorize SWRCB to allocate actual consumption across multiple legal water sources when the sources are physically mixed.

**The back-calculation method** (Total ET minus surface water deliveries minus precipitation = groundwater use) is a partial solution. Irrigation districts track surface deliveries to individual turnouts. Validated at 7-17% accuracy outside California (Diamond Valley NV, Harney Basin OR). But it tells SWRCB total groundwater pumping, not which type of groundwater right it falls under.

**The practical implication:** OpenET can serve as a measure of **total consumptive use** at the field level regardless of source. This is valuable for basin-scale water budgets, SGMA compliance, drought assessment, and aggregate reporting. But attributing that consumption to specific water rights requires administrative records (district delivery data, pumping logs, banking recovery records) that exist independently of satellite data.

### Oregon's Cautionary Position

The Oregon Water Resources Department's March 2025 memo explicitly states that OpenET satellite data is **"not suitable as the sole source for water rights compliance evaluations"** and prohibits its use for:
- Direct regulatory evaluation of duty (water use per acre)
- In-season regulatory actions
- Establishing use/non-use of water rights
- Quantifying applied water for individual fields needing high accuracy

Oregon allows OpenET for screening, trend analysis, basin-scale planning, and voluntary water management. This is a more conservative position than California's Delta ACP but reflects legitimate concerns about the gap between total ET and per-right consumptive use.

### Crop Type Identification Gaps

OpenET's accuracy varies by crop, making correct identification essential:

| Data Source | Resolution | CA Specialty Crop Accuracy | Years Available |
|---|---|---|---|
| DWR Statewide Crop Mapping | Field-level, ground-validated | Superior, CA-calibrated | 2016, 2018, 2019 only |
| USDA CDL | 30m (new 10m from 2024) | Weak on peppers, greens, squash, cucumbers | Annual |
| County Ag Commissioner Reports | County-level aggregates | Authoritative local ID | Annual |

**OpenET's own documentation acknowledges** California crop type data is incorrect for years other than 2016 and 2018. Since crop type influences the SIMS model and some ensemble calculations, this introduces additional uncertainty.

### Quality Control Requirements

OpenET provides built-in QC through Landsat cloud masking and MAD outlier filtering. For regulatory use, SWRCB would need to add:

1. **Automated range tests:** Flag negative ET, extreme spikes, values outside crop-specific expected ranges
2. **Temporal consistency checks:** Flag anomalous month-to-month changes (>3 standard deviations)
3. **Spatial consistency:** Compare field ET to neighboring fields with similar crop/soil
4. **Independent ground-truth validation:** Periodic eddy covariance or lysimeter audits at representative sites
5. **Crop type cross-check:** Validate ET against expected ranges per identified crop
6. **QARTOD-style flag system:** 1 = good, 3 = suspect, 4 = fail; retain qualifiers for audit trail

### Existing California Models That Can Help

Three DWR models already handle the precipitation/groundwater subtraction that SWRCB needs:

| Model | Owner | Coverage | Key Capability |
|---|---|---|---|
| **CalSIMETAW** | DWR | Statewide, 482 DAUs | Daily soil water balance: ETaw = ETc - Effective Rainfall - Bare Soil Evap - Seepage |
| **DETAW** | DWR | 168 Delta islands | Daily applied water calculation with explicit seepage credits |
| **IDC** | DWR | Regional (C2VSim) | FAO-56 root-zone water balance with groundwater contribution |

**These models could use OpenET as input.** CalSIMETAW already supports Spatial CIMIS (remote sensing-enhanced ETo). The most promising path: replace the models' estimated Kc-ETo calculation with OpenET's satellite-measured actual ET, then run the existing soil water balance to subtract precipitation and groundwater. This combines OpenET's measurement strength with the models' accounting framework.

Comparisons between DETAW and remote sensing methods show ~16% disagreement, suggesting calibration would be needed. But the architecture already exists.

### Recommended Supplementary Data Strategy

| Priority | Action | Timeline | Cost |
|---|---|---|---|
| **1. High** | Fund annual DWR statewide crop mapping (currently only 3 years available) | Ongoing | Moderate |
| **2. High** | Develop groundwater depth screening protocol using CASGEM/SGMA data to flag shallow-GW zones | 6-12 months | Low |
| **3. High** | Adapt CalSIMETAW/DETAW to accept OpenET as input for the precipitation/GW subtraction | 12-18 months | Moderate |
| **4. Medium** | Commission CA-specific ground-truth validation study (orchards, vineyards, rice, Delta crops) | 12-24 months | Moderate-High |
| **5. Medium** | Develop regulatory QC flag system for OpenET data ingestion | 6-12 months | Low |
| **6. Medium** | Evaluate USGS NetET product for CA-specific green/blue water partitioning at higher resolution | 12 months | Low |
| **7. Low** | Collect irrigation method data through CalWATRS reporting | Ongoing | Low |
| **8. Long-term** | Fund field research on groundwater contribution to crop ET in Delta and near-river zones | 2-4 years | High |

---

## 15. Source Index

### Peer-Reviewed Publications

| Citation | DOI / URL |
|---|---|
| Volk et al. 2024, "Assessing the accuracy of OpenET," *Nature Water* | `10.1038/s44221-023-00181-7` |
| Melton et al. 2022, "OpenET: Filling a Critical Data Gap," *JAWRA* | `10.1111/1752-1688.12956` |
| Knipper et al. 2024, California almond orchards, *Ag. Forest Meteorology* | `10.1016/j.agrformet.2024.110146` |
| Performance Mapping and Weighting, *Water Resources Research* 2024 | `10.1029/2024WR038899` |
| Asarian 2023, Scott/Shasta curtailment evaluation | waterboards.ca.gov/drought/scott_shasta_rivers/docs/2023/ |
| Asarian et al. 2025, Pairing OpenET with streamflow | repository.library.noaa.gov/view/noaa/71668 |

### Government and Agency Sources

| Source | URL |
|---|---|
| Delta ACP filing | waterboards.ca.gov/water_issues/programs/delta_watermaster/docs/deltaacpfinal.pdf |
| SWRCB ACP list | waterboards.ca.gov/waterrights/water_issues/programs/measurement_regulation/acp_list.html |
| USGS EROS accuracy assessment | usgs.gov/centers/eros/news/usgs-eros-helps-assess-openet-accuracy |
| USGS performance data release | usgs.gov/data/performance-maps-weights-and-associated-data-sets-version-20-openet-evapotranspiration-models |
| Oregon OWRD historical review | oregon.gov/owrd/WRDPublications1/OpenET_HIST_REV_OR_241122FINAL.pdf |
| Utah CRAU historical review | cra.utah.gov/wp-content/uploads/2025/01/CRAU_OpenET_historical_reviewFINAL10.10.pdf |
| UCRC eeMETRIC adoption | ucrcommission.com/openet-upper-colorado-river-commission-and-bureau-of-reclamation-move-to-satellite-based-et |
| NASA OpenET page | nasa.gov/general/openet-balancing-water-supply-and-demand-in-the-west/ |
| DWR SGMA partnership | etdata.org/impact-stories/advancing-groundwater-sustainability-with-california-dwr-openet/ |
| Federal OpenET Act | susielee.house.gov/sites/evo-subsites/susielee-evo.house.gov/files/Factsheet%20-%20OpenET%20Act_0.pdf |

### OpenET Platform Resources

| Resource | URL |
|---|---|
| Main site | etdata.org |
| Data Explorer | explore.etdata.org |
| API documentation | openet-api.org |
| API Gitbook docs | openet.gitbook.io/docs/ |
| Accuracy and known issues | etdata.org/accuracy-known-issues/ |
| Methods | etdata.org/methods/ |
| Impact stories | etdata.org/impact-stories/ |
| GEE catalog | developers.google.com/earth-engine/datasets/tags/openet |
| GitHub organization | github.com/Open-ET |
| Python client docs | openet-client.readthedocs.io/ |

### Additional References

| Source | URL |
|---|---|
| Delta ET thesis (Jankowski 2018, UC Davis) | wla.engineering.ucdavis.edu/students/JesseJankowski_MSThesis2018.pdf |
| WestDAAT tool | internetofwater.org/blog/unveiling-westdaat-a-breakthrough-for-water-rights-data-management-in-the-western-united-states |
| Colusa Subbasin impact story | etdata.org/openet-enables-efficient-calculation-of-consumptive-water-use-to-support-sustainable-groundwater-management-in-californias-colusa-subbasin |
| DRI accuracy announcement | dri.edu/a-new-rigorous-assessment-of-openet-accuracy/ |
| Water Education Foundation coverage | watereducation.org/western-water/california-uncloak-water-rights-it-moves-records-online |
| HESS 2023 uncertainty assessment | hess.copernicus.org/articles/27/4505/2023/ |
| Reclamation WaterSMART report | usbr.gov/watersmart/appliedscience/docs/2023/057_Western_States_Water_Council_508.pdf |

### Meter Accuracy and Calibration Sources

| Source | URL |
|---|---|
| USBR Water Measurement Manual, Ch. 4 (field accuracy) | usbr.gov/tsc/techreferences/mands/wmm/chap04_03.html |
| USBR Water Measurement Manual, Ch. 14 (propeller meters) | usbr.gov/tsc/techreferences/mands/wmm/chap14_04.html |
| USU Extension (total system accuracy) | extension.usu.edu/irrigation/research/accurate-irrigation-water-flow-pipes |
| ITRC Report F20-001 (mag meter chemical injection) | itrc.org/flowreports/f20-001.htm |
| ITRC/Cal Poly (mag meter field testing, Central Coast) | waterboards.ca.gov/waterrights/water_issues/programs/measurement_regulation/docs/water_measurement/itrc_1.pdf |
| McCrometer (debris in flow meters) | blog.mccrometer.com/debris-in-flow-meter-recommendations-for-agricultural-applications/ |
| LADWP Water Audit Component Analysis | ladwp.com |

### Regulatory Framework Sources

| Source | URL |
|---|---|
| 23 CCR section 931 (definitions) | law.cornell.edu/regulations/california/23-CCR-931 |
| 23 CCR section 933 (measuring devices) | law.cornell.edu/regulations/california/23-CCR-933 |
| 23 CCR section 934 (measurement methods) | law.cornell.edu/regulations/california/23-CCR-934 |
| 23 CCR section 935 (alternative compliance plans) | law.cornell.edu/regulations/california/23-CCR-935 |
| 23 CCR section 937 (calibration) | law.cornell.edu/regulations/california/23-CCR-937 |
| Water Code section 1841 (rulemaking authority) | law.justia.com/codes/california/code-wat/division-2/part-2/chapter-12/article-3/section-1841/ |
| SB 88 text | legiscan.com/CA/text/SB88/id/1251586 |
| SWRCB measurement regulation text | waterboards.ca.gov/waterrights/water_issues/programs/diversion_use/docs/measurement_regs.pdf |
| SWRCB 2025 proposed changes summary | waterboards.ca.gov/waterrights/water_issues/programs/diversion_use/docs/2025/summary-of-proposed-changes.pdf |
| SWRCB 2025 Initial Statement of Reasons | waterboards.ca.gov/waterrights/water_issues/programs/diversion_use/docs/2025/initial-statement-of-reasons.pdf |
| SWRCB 2025 economic impact assessment | waterboards.ca.gov/waterrights/water_issues/programs/diversion_use/docs/2025/eia-sb88.pdf |
| SWRCB Resolution 2025-0021 | waterboards.ca.gov/board_decisions/adopted_orders/resolutions/2025/rs2025-0021.pdf |
| Delta ACP website | deltaacp.com |
| DMEC history | cawaterdata.org/wp-content/uploads/2023/11/History-of-DACP-Final-231205.pdf |
| OAL Administrative Procedure Act | oal.ca.gov/publications/administrative_procedure_act/ |
| SB 88 FAQ | waterboards.ca.gov/waterrights/water_issues/programs/diversion_use/docs/faq_sb88.pdf |

### Consumptive Use and Water Budget Sources

| Source | URL |
|---|---|
| Central Valley irrigation efficiency analysis | ui.adsabs.harvard.edu/abs/2022AGUFM.H22M..05B/abstract |
| USGS deep percolation study | pubs.usgs.gov/sir/2011/5001/ |
| Pacific Institute (CA ag water efficiency) | pacinst.org/wp-content/uploads/2014/06/ca-water-ag-efficiency.pdf |
| PPIC (water use in CA agriculture) | ppic.org/publication/water-use-in-californias-agriculture/ |
| BAERI/OpenET (Delta consumptive use) | baeri.org/openet-balancing-water-supply-and-demand-in-the-west/ |

### Legal and Evidentiary Sources

| Source | URL |
|---|---|
| Duke Law (EPA remote sensing evidence) | scholarship.law.duke.edu/cgi/viewcontent.cgi?article=1136&context=delpf |
| University of Miami Law Review (satellite surveillance) | repository.law.miami.edu/cgi/viewcontent.cgi?article=1434&context=umiclr |
| Harvard HRJ (satellite imagery as evidence) | journals.law.harvard.edu/hrj/2023/11/privacy-and-veracity-implications-of-the-use-of-satellite-imagery-from-private-companies-as-evidence-in-human-rights-investigations/ |
| Western States Water Council testimony (S. 2568) | westernstateswater.org/testimony/2022/s-2568-open-access-evapotranspiration-open-et-data-act/ |

### Hydrologic and Regional Sources

| Source | URL |
|---|---|
| Deverel et al. 2016 (Delta subsidence and groundwater) | pmc.ncbi.nlm.nih.gov/articles/PMC4944668/ |
| Delta ET Study 2015-2016 (UC Davis, 7-model comparison) | watershed.ucdavis.edu/sites/g/files/dgvnsk8531/files/products/2022-05/01_DeltaET_FinalReport_20180628.pdf |
| USGS Circular 1182 (Delta subsidence and hydrology) | pubs.usgs.gov/circ/circ1182/pdf/11Delta.pdf |
| DWR Bulletin 118 (Tulare Lake Subbasin) | water.ca.gov/-/media/DWR-Website/Web-Pages/Programs/Groundwater-Management/Bulletin-118/Files/2003-Basin-Descriptions/5_022_12_TulareLakeSubbasin.pdf |
| DRI groundwater monitoring with OpenET | dri.edu/groundwater-use-can-be-accurately-monitoredwith-satellites-using-openet/ |
| USGS green/blue water partitioning (NetET) | usgs.gov/publications/partitioning-evapotranspiration-green-and-blue-water-sources-conterminous-united |
| USGS EROS NetET product | eros.usgs.gov/doi-remote-sensing-activities/2021/usgs/remote-sensing-model-evaluation-netet-irrigation-water-use-nation |
| Lal & Clark 2012 (Sacramento Valley rice SEBAL ET) | mountainscholar.org/items/49d52b3d-52f8-4e2c-9f9f-35c5377e2864 |
| UC Davis rice ET factsheet | alfalfa.ucdavis.edu/sites/g/files/dgvnsk12586/files/media/documents/factsheet5_growing_season_water_use_in_california_rice_systems.pdf |
| Baguskas et al. 2018 (fog and WUE, Salinas Valley) | environment.sfsu.edu/sites/default/files/2022-05/Baguskas-etal-Coastal-low-cloudiness-and-fog-increase-WUE-of-crops-AFM-2018.pdf |
| PMC meta-analysis (groundwater contribution to ET) | pmc.ncbi.nlm.nih.gov/articles/PMC5585407/ |

### Supplementary Data and Compliance Sources

| Source | URL |
|---|---|
| Oregon OWRD ET Applications Memo (March 2025) | oregon.gov/owrd/WRDPublications1/FINAL_OWRD_ET_Applications_Memo_28MAR2025.pdf |
| CalWATRS (SWRCB electronic reporting) | waterboards.ca.gov/upward/calwatrs/ |
| DWR Land Use Surveys | water.ca.gov/programs/water-use-and-efficiency/land-and-water-use/land-use-surveys |
| DWR Statewide Crop Mapping | lab.data.ca.gov/dataset/statewide-crop-mapping |
| NASS 10m CDL paper | nass.usda.gov/Research_and_Science/Cropland/docs/IGARSS2024_Proceedings_10mCDL_Li_etal.pdf |
| DWR Irrigation Systems Methods Surveys | water.ca.gov/Programs/Water-Use-And-Efficiency/Land-And-Water-Use/Statewide-Irrigation-Systems-Methods-Surveys |
| Majumdar et al. 2024 (ET to applied water estimation) | transcendresearchproject.com/wp-content/uploads/2025/03/Estimating-irrigation-water-use-from-remotely-sensed-evapotranspiration-data.pdf |
| CASGEM (groundwater monitoring) | water.ca.gov/programs/groundwater-management/groundwater-elevation-monitoring--casgem |
| Groundwater Resource Hub threshold framework | groundwaterresourcehub.org/content/dam/tnc/nature/en/documents/groundwater-resource-hub/GroundwaterThresholdFramework_Final_updated_Dec2020.pdf |
| CalSIMETAW technical appendix | watershed.ucdavis.edu/sites/g/files/dgvnsk8531/files/products/2022-05/AppendixC_CalSIMETAW_20180409.pdf |
| DETAW model | water.ca.gov/Library/Modeling-and-Analysis/Bay-Delta-Region-models-and-tools/DETAW |
| IDC model | water.ca.gov/Library/Modeling-and-Analysis/Modeling-Platforms/Integrated-Water-Flow-Model-Demand-Calculator |
| Orang et al. 2013 (CalSIMETAW) | cawaterlibrary.net/wp-content/uploads/2019/07/Orang-et-al-2013.pdf |
| SSURGO/STATSGO soil comparison | scirp.org/journal/paperinformation?paperid=28700 |
| Pacific Institute (CA ag water efficiency) | pacinst.org/wp-content/uploads/2014/06/ca-water-ag-efficiency.pdf |
| PPIC (water use in CA agriculture) | ppic.org/publication/water-use-in-californias-agriculture/ |

### Groundwater ET Partitioning Literature

| Source | URL / DOI |
|---|---|
| Luo & Sophocleous 2010 (Kansas lysimeters, gold-standard GW-ET) | pubs.usgs.gov/publication/70032578 / DOI: 10.1016/j.jhydrol.2010.06.011 |
| Shouse et al. 2011 (USDA-ARS San Joaquin Valley GW contribution) | pc-progress.com/Documents/Jirka/Shouse_et_al_AWM_2011.pdf / DOI: 10.1016/j.agwat.2010.08.016 |
| Deines et al. 2024 (GW influence on crop yields, PNAS) | pnas.org/doi/10.1073/pnas.2400085121 |
| Soylu et al. 2011 (GW depth effect on ET, model sensitivity) | hess.copernicus.org/articles/15/787/2011/ / DOI: 10.5194/hess-15-787-2011 |
| Han et al. 2018 (HYDRUS-1D cotton capillary rise, NW China) | hess.copernicus.org/articles/22/2937/2018/ / DOI: 10.5194/hess-22-2937-2018 |
| Evaristo et al. 2015 (Ecohydrological separation, Nature) | pubmed.ncbi.nlm.nih.gov/26333467/ / DOI: 10.1038/nature14983 |
| Xiao et al. 2018 (Isotopic ET partitioning review) | yncenter.sites.yale.edu/sites/default/files/files/xiao_wei_afm_2018.pdf |
| Wang et al. 2023 (MARMITES-MODFLOW coupled model) | frontiersin.org/journals/water/articles/10.3389/frwa.2023.1055934/full |
| Grismer (UC Davis, shallow GW resource potential) | ars.usda.gov/research/publications/publication/?seqNo115=180529 |
| UC Davis / Hopmans (shallow GW and crop production) | lawr.ucdavis.edu/using-shallow-ground-water-crop-production |
| Zipper et al. 2015 (GW effects on crop yields, WRR) | agupubs.onlinelibrary.wiley.com/doi/10.1002/2015WR017522 |
| USGS green/blue water partitioning (NetET) | usgs.gov/publications/partitioning-evapotranspiration-green-and-blue-water-sources-conterminous-united |
| Kahlown & Ashraf 2005 (Pakistan lysimeters) | pcrwr.gov.pk/wp-content/uploads/2020/Water-Management-Reports/ |
| Huang et al. 2016 (Hetao 8-year dataset, AGU) | ui.adsabs.harvard.edu/abs/2016AGUFM.H51H1608H/abstract |

### Tulare Basin Conjunctive Use and Water Rights Sources

| Source | URL |
|---|---|
| Friant Water Authority (Friant-Kern Canal) | friantwater.org |
| Kings River Water Association | kingsriverwater.org |
| Kern River Ecological Watershed Study 2016 | kern-river-ecological-watershed-study (multiple public sources) |
| SWRCB Order WRO 2010-0010 (Kern River adjudication) | waterboards.ca.gov |
| Kern Water Bank Authority | kwb.org |
| Semitropic WSD (water banking) | semitropic.com |
| Rosedale-Rio Bravo WSD | rrbwsd.com |
| DWR Bulletin 118, Tulare Lake Subbasin | water.ca.gov (Basin Descriptions) |
| Pacific Institute (groundwater banking report) | pacinst.org |
| DRI OpenET groundwater monitoring validation | dri.edu/groundwater-use-can-be-accurately-monitoredwith-satellites-using-openet/ |
| Oregon OWRD ET Applications Memo (March 2025) | oregon.gov/owrd/WRDPublications1/FINAL_OWRD_ET_Applications_Memo_28MAR2025.pdf |
| Tulare Basin Watershed Partnership | tulareid.org |
| SWRCB SGMA Tulare Lake subbasin probation (2024) | waterboards.ca.gov/groundwater |

## Related

- [Water-Rights](https://github.com/vanderoffice/Water-Rights) -- parent modernization workspace (OpenET research feeds curtailment methodology)
- [State-Modernization](https://github.com/vanderoffice/State-Modernization) -- broader CA department modernization research (includes SWRCB audit)
