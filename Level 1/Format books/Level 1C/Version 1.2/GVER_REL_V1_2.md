##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.2](../Version%201.2/) > [Format book](README.md) > Relative geometric disparity

# Level 1C relative geometric disparity metrics

## Introduction

This metadata file summarises the comparison between the two bands of an image. Tiepoints are collected for both. These tiepoints are independent of the tiepoints collected to process the image. The tiepoints between the reference and the image are matched to find similar ones. The distance between the geolocation of the tiepoints on the reference image and the tiepoints on the processed image is measured.

The geometric verification relative metadata file is similar to the geometric verification absolute metadata file. However, the geometric verification relative metadata file contains measurements between the band combinations that were measured.

## Sample file
**Sample:** [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_GVER_REL.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.2/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_GVER_REL.json)

## Properties

| Property | Description |
|----|----|
| `measurements` | An array that repeats the below data for each band combination that is measured |
| `measurements:imageName` | The filename of the thumbnail image that corresponds the data in this file |
| `measurements:from` | The band id of the reference band used in this comparison |
| `measurements:to` | The band id of the image that is being measured |
| `measurements:disparitiesXYInMeters` | An array of the distances in meters from the reference tiepoints to the image tiepoints. These are stored as `[x_distance, y_distance]` for each tiepoint |
| `coordsLatLon`| An array of (longitude, latitude) coordinates of the tiepoints on the reference image and the image. These are stored as: `[lon_ref, lat_ref, lon_img, lat_img]` for each tiepoint |
| `pixelColorMappings` | A legend to quantify disparities in colour ranges. This legend is used for the thumbnail referenced in `measurements:imageName` |
