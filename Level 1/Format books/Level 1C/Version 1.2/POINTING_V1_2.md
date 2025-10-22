# Level 1C geometric pointing metrics

## Introduction

The pointing file contains data structures listing the latitude and longitude of different pixels at different levels of processing. This information is useful for determining the accuracy of the satellites’ attitude and ephemeris data. Measurements are provided for each sensor. This section is only published if the product is precision orthorectified.

These metrics are tracked because they provide insights into the accuracy of the satellite’s sensors. They are used as part of a larger collection of metrics to determine when new calibration data is required to maintain the quality of the images that are processed.

The raw to systematic disparity should only change when calibration data is updated, or between images captured over areas with different elevations.

The raw to precision and systematic to precision disparities are expected to degrade over time as sensors age and become less accurate. When measured over time they are a good indicator of the average error of the sensors.

## Sample file
**Sample** :  [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_POINTING.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.2/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_POINTING.json)

## Properties
|**Property**|**Meaning**|
|---|---|
|`location`|A short string indicating the pixel being measured, UL means Upper Left, LR means Lower Right and CENTER means the center of the image|
|`rawLocation`|Latitude and longitude of the pixel as reported by the satellite. No rotations or corrections have been applied|
|`systematicLocation`|Latitude and longitude of the pixel as reported by the satellite after the image has been systematically orthorectified. This location has been corrected using the calibrated data and digital elevation models only|
|`precisionLocation`|Latitude and longitude of the pixel as reported by the satellite after the image has been precision orthorectified. This location has been corrected using the calibrated data and digital elevation models and then accurately located using reference data|
|`rawToSystematicDisparityMeter`|The difference between the locations in RAW  Location and Systematic Location converted to meters|
|`rawToPrecisionDisparityMeter`|The difference between the locations in RAW Location and Precision Location converted to meters|
|`systematicToPrecisionDisparityMeter`|The difference between the locations in Systematic Location and Precision Location converted to meters|