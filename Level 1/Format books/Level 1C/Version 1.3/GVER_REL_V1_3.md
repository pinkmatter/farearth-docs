##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Relative geometric disparity

# Level 1C relative geometric disparity metrics

## Introduction

This metadata file summarises the comparison between the two bands of an image. 
Tiepoints are collected for both bands. 

Corresponding tiepoints are collected between the reference and processed images. The distances between these corresponding tiepoints are measured.

Note that these tiepoints are independent of the tiepoints collected to process the image. 

The relative geometric verification metadata file is similar to the absolute geometric verification metadata file. However, the relative geometric verification metadata file contains measurements between the band combinations that were measured.

## Sample file

**Sample:** [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_GVER_REL.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_GVER_REL.json)

## Property details
This section contains explanations on specific properties of the relative geometric disparity metrics file. All the properties that have been expanded on are listed in a structured manner under the [Reference](#reference-relative-geometric-disparity-metrics) section.

### Pixel Colour Mappings 
This section describes the `pixelColorMappings` property.
This provides a legend to quantify disparities in colour ranges. This legend is used for the thumbnail referenced in `imageName`. 

## Reference: relative geometric disparity metrics

The following reference describes the content of the relative geometric disparity metrics file.

- **`measurements`** *(array)*: A list of disparity metrics grouped by individual bands.
  - **Items** *(object)*
    - **`coordsLatLon`** *(array)*: The (longitude, latitude) coordinates of the evaluated tie-points.
      - **Items** *(array)*
        - **Items** *(number, format: double)*
    - **`disparitiesXYInMeters`** *(array)*: A list of (x,y) disparities of the evaluated tie-points (in meters).
      - **Items** *(array)*
        - **Items** *(number, format: double)*
    - **`from`** *(string)*: The band ID of the source used during comparison.
    - **`imageName`** *(string)*: An illustration of the quality of all the tie-points evaluated on the image.
    - **`to`** *(string)*: The band ID of the target used during comparison.
- **`pixelColorMappings`** *(string)*: Mappings used to quantify disparities in color ranges (only for display purposes).
