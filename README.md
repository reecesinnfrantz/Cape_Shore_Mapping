---
# Fine-Scale Shore-Type Mapping: Cape Peninsula
**Author:** Reece Sinn Frantz  
**Date:** March 2026
format: 
  html:
    toc: true
    code-fold: false
---

## 1. Project Overview

In this project, I am using biological data to check if official shore-type maps for the Cape Peninsula are accurate. I chose two species to act as "proxies" for different habitats: \* **Rocky Shores:** Validated using *Scutellastra granularis* (Limpets). \* **Sandy Shores:** Validated using *Bullia rhodostoma* (Plough Snails).

By mapping these species, I can see if their recorded locations align with the expected coastline types.

## 2. GIS Workflow

I followed these steps to build the analysis: 1. **Data Acquisition:** I used the `rinat` package to query the iNaturalist API for research-grade observations. 2. **Spatial Processing:** I turned the raw coordinates into `sf` (Simple Feature) objects using the WGS84 coordinate system (EPSG:4326). 3. **Validation:** I used a 200m buffer logic to see what percentage of sightings fell within the actual shore zone. 4. **Visualisation:** I created a static map for reports and an interactive map for data inspection.

## 3. Installation & Prerequisites

You need **R** and **RStudio** to run this project. I used the following libraries: \* `library(tidyverse)`: Used for data cleaning, piping (%\>%), and general data manipulation. \* `library(sf)`: The core package for handling spatial/GIS data and projections. \* `library(ggspatial)`: Adds map elements to ggplot, like north arrows, scale bars, and OSM tiles. \* `library(rinat)`: Used to download species observation data directly from the iNaturalist API. \* `library(mapview)`: Creates interactive, "zoomable" maps in the RStudio viewer or browser. \* `library(leafpop)`: Used to create organized tables within the interactive map popups.

## To install them all at once, run this in your R console:

``` r
install.packages(c("tidyverse", "sf", "ggspatial", "rinat", "mapview", "leafpop"))
```

## 4. Usage Instructions

Open the Cape_Shore_Mapping.Rproj file in RStudio.

Open the Quarto file: Fine-Scale Shore.qmd.

Click Render. The code will automatically download the data from iNaturalist based on my set coordinates, so you do not need to download a separate data folder.

## 5. Data Terminology

The data pulled from iNaturalist includes several important columns used for filtering and mapping:

quality_grade: I filtered for "research" to ensure high-quality data.

user_login: Handle / username of the observer.

url: URL for the observation, used to make live links in popups.

latitude/longitude: Publicly visible coordinates from the observation location.

captive_cultivated: Used to filter out organisms that exist in a place because humans intended them to be there (e.g., gardens).

## 6. Data Sources

iNaturalist: Species sightings provided by the iNaturalist community via the rinat package.

OpenStreetMap: Background map tiles provided by OSM contributors.
