# QGIS_CaseStudy

## Overview

This case dirived from [Link](https://www.qgistutorials.com/en/docs/3/raster_mosaicing_and_clipping.html). This tutorial explores basic techniques for working with rasters in QGIS such as mosaicing and subsetting.

![snapshot](./assets/case_snapshot.jpg)

## Data

The Digital Elevation Model(DEM) data is derived from [SRTM30m](https://dwtkns.com/srtm30m/). The shapefile for administrative boundary is derived from [NATURALEARTH](https://www.naturalearthdata.com/).

![](./assets/SRTM_preview.png)

## (Simplified) Workflow

### 0. Preprocess

Get raster data from .zip and add them into QGIS project.

> You can either unzip them manually or call a unzip tool in your gis-agent workflow.

![step0](./assets/step0.png)

### 1. Merge

> GDAL ‣ Raster miscellaneous ‣ Merge tool

Merge several raster layers into a singular layer.

![step1](./assets/step1.png)

![display](./assets/step1_display.png)

### 2. Extract by Attribute

> Vector selection ‣ Extract by Attribute

![step2](./assets/step2.png)

![display2](./assets/step2_display.png)

### 3. Clip by Mask Layer

> GDAL ‣ Raster extraction ‣ Clip raster by mask layer tool

![step3](./assets/step3.png)

![display3](./assets/step3_display.png)

Key Notes:

1. Set "High Compression" in the advanced parameters followed preprocess step and set `0` as `NODATA`, otherwise, the result will still be a rectangle region.
2. The raster value indicate the elevation of this region. It is notable that some of the points are `0m above sea level`, which is also considered as `NODATA` in this step. This should be fixed by adjust the preprocess step.
