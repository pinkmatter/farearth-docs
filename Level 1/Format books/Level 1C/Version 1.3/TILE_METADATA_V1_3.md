##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Tile metadata

# Level 1C tile metadata

## Introduction

The tile metadata XML(`.xml`) file is an ISO 19115-compliant XML metadata file that provides information about the image tile.

## Sample file

**Sample** : [MTD_TL.xml](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/MTD_TL.xml)

## Detailed Property Explanations
This section contains explanations on specific properties of the tile metadata file. 

### Tile Geocoding

The tile geocoding section gives information based on the coordinate system and geometry of the tile.

### Tile Angles

The tile angles section gives data regarding both viewing incidence and sun angles for the tile. 

#### Viewing incidence angles

**Azimuth** is the viewing azimuth angle. This is the angle measured from the sub-satellite point (point on the ground below the platform) between the scene center and true north. Measured clockwise from north in degrees (0°- 360°) 

**Zenith** is the viewing zenith angle. This is the angle measured between the vertical (normal) to the intercepting surface at the centre point of the image or block and the line of sight back to the satellite. Measured in degrees (0°-90°)  

#### Sun angles

**Azimuth** is the sun azimuth angle. This is the angle at the center of the block from true north to the sun measured clockwise in degrees 

**Zenith**  is the sun zenith angle. This is the angle from the zenith to the sun in degrees. It is equivalent to 90°-*sun elevation* 

