##### [Home](../../../../README.md) > [Level 2](../../../../Level%202/) > Format books](../../../Format%20books/) > [Level 2A](../../Level%202A/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Geometric pointing

# Level 2A geometric pointing metrics

## Introduction

The pointing file contains geolocation measurements as well as the type of orthorectification model used. 

These metrics provide insights into the geolocation accuracy of the satellite's sensors. They can inform when new calibration data is required to maintain the quality of the images.

## Sample file

**Sample** :  [LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1_POINTING.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L2A/LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1_POINTING.json)

## Detailed Property Explanations

This section contains explanations on specific properties of the geometric pointing metrics file. All the properties that have been expanded on are listed in a structured manner under the [Reference](#reference-geometric-pointing-metrics) section.

### Orthorectification

This section describes the `orthorectification` property.
Each sensor can independently orthorectify either by **systematic orthorectification** or **precision orthorectification** models. 

#### Systematic orthorectification

Systematic orthorectification uses calibration coefficients, NavAtt data, and rough reference data such as the mean height above ellipsoid for the image.

#### Precision orthorectification

Precision orthorectification uses tiepoints and reference data to refine the geolocation of the image to higher accuracies. Individual pixels of the Digital Elevation Model (DEM) are used to determine precisely where the pixel is.

## Reference: Geometric pointing metrics

The following reference describes the content of the geometric pointing metrics file.

- **`measurements`** *(array)*: Listed by different sensors.
  - **Items** *(object)*
    - **`orthorectification`** *(string)*: To what model quality orthorectification was achieved (either 'systemic' or 'precision'). Any detector which failed precision refinement will result in a fallback to 'systematic'. Must be one of: `["systematic", "precision"]`.
    - **`points`** *(array)*: Metrics describing how the image location was adjusted from raw to processed, listed by sensor ID.
      - **Items** *(object)*
        - **`location`** *(string)*: The location in the image where the metrics are applicable to. The possible locations are: upper-left corner, lower-left corner, lower-right corner, upper-right corner, and scene center. Must be one of: `["UL", "LL", "LR", "UR", "CENTER"]`.
        - **`precisionLocation`** *(array)*: The precision corrected coordinate in (longitude, latitude). Length must be equal to 2.
          - **Items** *(number)*
        - **`rawLocation`** *(array)*: Raw location in (longitude, latitude) prior to any corrections being applied. Length must be equal to 2.
          - **Items** *(number)*
        - **`rawToPrecisionDisparityMeter`** *(number, format: double)*: The difference in meters between the raw and precision coordinate locations.
        - **`rawToSystematicDisparityMeter`** *(number, format: double)*: The difference in meters between the raw and systematic coordinate locations.
        - **`systematicLocation`** *(array)*: The systematically corrected coordinate in (longitude, latitude). Length must be equal to 2.
          - **Items** *(number)*
        - **`systematicToPrecisionDisparityMeter`** *(number, format: double)*: The difference in meters between the systematic and precision coordinate locations.
    - **`sensorId`** *(string)*
    - **`sensorName`** *(string)*
