##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Absolute geometric disparity

# Level 1C absolute geometric disparity metrics

## Introduction

This metadata file summarises the comparison between a specific band of processed image and a reference image. 

Tiepoints are collected for both of these images.

Corresponding tiepoints are collected between the reference and processed images. The distances between these corresponding tiepoints are measured.

Note that these tiepoints are independent of the tiepoints collected to process the image. 

## Sample file

**Sample:** [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_GVER_ABS.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_GVER_ABS.json)

## Property details
This section contains explanations on specific properties of the absolute geometric disparity metrics file. All the properties that have been expanded on are listed in a structured manner under the [Reference](#reference-absolute-geometric-disparity-metrics) section.

### Pixel Colour Mappings 
This section describes the `pixelColorMappings` property.
This provides a legend to quantify disparities in colour ranges . This legend is used for the thumbnail referenced in `imageName`. 

## Reference: absolute geometric disparity metrics

The following reference describes the content of the absolute geometric disparity metrics file.

- **`measurements`** *(array)*: A list of disparity metrics grouped by individual bands.
  - **Items** *(object)*
    - **`coordsLonLat`** *(array)*: The (longitude, latitude) coordinates of the evaluated tie-points.
      - **Items** *(array)*
        - **Items** *(number, format: double)*
    - **`disparitiesXYInMeters`** *(array)*: A list of (x,y) disparities of the evaluated tie-points (in meters).
      - **Items** *(array)*
        - **Items** *(number, format: double)*
    - **`id`** *(string)*
    - **`imageName`** *(string)*: An illustration of the quality of all the tie-points evaluated on the image.
    - **`refBand`** *(string)*: The band ID of the reference image being used during comparison.
    - **`refResolution`** *(array)*: The resolution of the reference image used during comparison.
      - **Items** *(number, format: double)*
    - **`refSpacecraft`** *(string)*: The Spacecraft ID of the associated reference image.
- **`pixelColorMappings`** *(string)*: Mappings used to quantify disparities in color ranges (only for display purposes).
