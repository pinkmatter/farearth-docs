##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.2](../Version%201.2/) > [Format book](README.md) > Viewing angles

# Level 1C Viewing angle metadata file

## Introduction
This is the viewing angle file pixel data averaged across the whole scene. This is to provide additional detail for applications that require it.

## Sample file 

**Sample:** [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_ANGLES.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.2/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_ANGLES.json)

## Properties
### Mean sun angle 

The `meanSunAngle` section provides details on the averaged sun angles.

This table documents the `meanSunAngle` section.
| **Property** |**Description**|
| ----------- | --- |
|`azimuthAngle` | The azimuth is the angle at the center of the block from true north to the sun measured clockwise in degrees  |
|`azimuthAngleUnit`|The unit of the azimuth measurement (typically degrees)|
|`zenithAngle`| The zenith is the angle from the zenith to the sun in degrees. It is equivalent to a 90°-  *sun elevation* |
|`zenithAngleUnit`|The unit of the zenith measurement (typically degrees)|

### Mean viewing incidence angles

The `meanViewingIncidenceAngles` section is an array of averaged incidence angles listed by band ID. 

This table documents the `meanViewingIncidenceAngles` section 

| **Property** |**Description**|
| ----------- | --- |                           
|`azimuthAngle`| Viewing azimuth angle. The angle measured from the sub-satellite point (point on the ground below the platform) between the scene center and true north. Measured clockwise from north in degrees (0°- 360°)|
|`azimuthAngleUnit`|The unit of the azimuth measurement (typically degrees)|
|`bandId`|The Id of the band that has these viewing incidence angles|
|`zenithAngle`| Viewing zenith angle.  The incidence angle zenith is the angle between the vertical (normal) to the intercepting surface at the centre point of the image or block and the line of sight back to the satellite. Measured in degrees (0°-90°) |
|`zenithAngleUnit`|The unit of the zenith measurement (typically degrees)|                                                                                                                                                    
### Viewing incidence angles
The  `viewingIncidenceAngles` field is an array of mean zenith and azimuth viewing incidence angles for each band.

### Sun angles

The `sunAngles` section is an angle grid describing how the sun is pointing towards the product.

This table documents the `sunAngles`  section. 
| **Property** |**Description**|
| ----------- | --- |   
|`azimuth`| Solar azimuth values where the scene is subdivided in a grid of averaged values. Refer to [Angle](#Angle)|
|`zenith`| Solar zenith values where the scene is subdivided in a grid of averaged values. Refer to [Angle](#Angle)|                                                                                                                                                 

### Angle

| **Property**   | **Description** |
| -------------- | ---- |
| `columnStepSize` | The column size is how many columns map units are included in each block|
| `columnStepUnit` | The unit of measurement used by the `columnStepSize`  |
| `rowStepSize` | The row size is how many rows map units are included in each block |
| `rowStepUnit` | The unit of measurement used by the `rowStepSize` |
| `values` | A square 2 dimensional array of values starting at the upper left. For example values `[3][5]` is row 3, column 5. `Nan` is used to indicate no data values |