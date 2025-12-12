##### [Home](../../../../README.md) > [Level 2](../../../../Level%202/) > [Format books](../../../Format%20books/) > [Level 2A](../../Level%202A/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Viewing angles

# Level 2A angle metadata file

## Introduction
This files gives gridded solar and viewing angle values as well as the averaged values across the whole scene

## Sample file 

**Sample:** [LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1_ANGLES.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L2A/LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1_ANGLES.json)

## Property details
This section contains explanations on specific properties of the angle metadata file. All the properties that have been expanded on are listed in a structured manner under the [Reference](#reference-angle-metadata-file) section.

### Mean sun angle 

The `meanSunAngle` section provides details on the averaged sun angles.

This table details certain properties of the `meanSunAngle` section.

| Property      | Description |
| ------------- | ----------- |
|`azimuthAngle` | The azimuth is the angle at the center of the block from true north to the sun measured clockwise in degrees  |
|`zenithAngle`  | The zenith is the angle from the zenith to the sun in degrees. It is equivalent to 90°-*sun elevation* |

### Mean viewing incidence angles

The `meanViewingIncidenceAngles` section is an array of averaged incidence angles listed by band ID. 

This table details certain properties of the  `meanViewingIncidenceAngles` section 

| Property | Description |
| ----------- | --- |                           
| `azimuthAngle` | Viewing azimuth angle. The angle measured from the sub-satellite point (point on the ground below the platform) between the scene center and true north. Measured clockwise from north in degrees (0°- 360°) |
| `zenithAngle` | Viewing zenith angle. The incidence angle zenith is the angle between the vertical (normal) to the intercepting surface at the centre point of the image or block and the line of sight back to the satellite. Measured in degrees (0°-90°) | 

### Viewing incidence angles
The  `viewingIncidenceAngles` field is an array of mean zenith and azimuth viewing incidence angles for each band.

### Sun angles

The `sunAngles` section is an angle grid describing how the sun is pointing towards the product.

This table documents the `sunAngles`  section. 
| Property | Description |
| ----------- | --- |   
|`azimuth`| Solar azimuth values where the scene is subdivided in a grid of averaged values. Refer to [Angle](#Angle)|
|`zenith`| Solar zenith values where the scene is subdivided in a grid of averaged values. Refer to [Angle](#Angle)|

### Angle

| Property | Description |
| -------------- | ---- |
| `columnStepSize` | The column size is how many columns map units are included in each block|
| `columnStepUnit` | The unit of measurement used by the `columnStepSize`  |
| `rowStepSize`    | The row size is how many rows map units are included in each block |
| `rowStepUnit`    | The unit of measurement used by the `rowStepSize` |
| `values`         | A square 2 dimensional array of values starting at the upper left. For example values `[3][5]` is row 3, column 5. `Nan` is used to indicate no data values |

## Reference: angle metadata file

The following reference describes the content of the angle metadata file.

- **`meanSunAngle`** *(object)*: Averaged solar angles.
  - **`azimuthAngle`** *(number, format: double)*: The azimuth angle measurement.
  - **`azimuthAngleUnit`** *(string)*: The unit of the azimuth measurement (typically degrees).
  - **`zenithAngle`** *(number, format: double)*: The zenith angle measurement.
  - **`zenithAngleUnit`** *(string)*: The unit of the zenith measurement (typically degrees).
- **`meanViewingIncidenceAngles`** *(array)*: Averaged incidence angles listed by band ID.
  - **Items** *(object)*
    - **`azimuthAngle`** *(number, format: double)*: The azimuth angle measurement.
    - **`azimuthAngleUnit`** *(string)*: The unit of the azimuth measurement (typically degrees).
    - **`bandId`** *(string)*
    - **`zenithAngle`** *(number, format: double)*: The zenith angle measurement.
    - **`zenithAngleUnit`** *(string)*: The unit of the zenith measurement (typically degrees).
- **`sunAngles`** *(object)*: Angle grid describing how the sun is pointing towards the product.
  - **`azimuth`**: Solar azimuth values where the scene is subdivided in a grid of averaged values. Refer to *[#/$defs/Angle](#%24defs/Angle)*.
  - **`zenith`**: Solar zenith values where the scene is subdivided in a grid of averaged values. Refer to *[#/$defs/Angle](#%24defs/Angle)*.
- **`viewingIncidenceAngles`** *(array)*: Angle grid listing the incidence angles per band and detector ID, in a grid defined as specified by the column and row step size and units.
  - **Items** *(object)*
    - **`azimuth`**: An averaged grid of azimuth viewing incidence angles. Refer to *[#/$defs/Angle](#%24defs/Angle)*.
    - **`bandId`** *(string)*
    - **`detectorId`** *(string)*
    - **`zenith`**: An averaged grid of zenith viewing incidence angles. Refer to *[#/$defs/Angle](#%24defs/Angle)*.
    
## Definitions

- <a id="%24defs/Angle"></a>**`Angle`** *(object)*
  - **`columnStepSize`** *(number, format: double)*: The number of unit steps included as a single column of which values are averaged in.
  - **`columnStepUnit`** *(string)*: The column step unit (typically pixels or the map projection units).
  - **`rowStepSize`** *(number, format: double)*: The number of unit steps included as a single row of which values are averaged in.
  - **`rowStepUnit`** *(string)*: The row step unit (typically pixels or the map projection units).
  - **`values`** *(array)*: A matrix of row and column values representing the averaged values.
    - **Items** *(array)*
      - **Items** *(number, format: double)*
