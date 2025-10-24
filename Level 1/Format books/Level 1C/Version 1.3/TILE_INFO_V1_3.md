##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Tile info

# Level 1C tile info

## Introduction

The tile info JSON (`.json`) file is a metadata file that contains details regards the tile outline and other contents. The properties of this file make reference to MGRS (Military Grid Reference System). This coordinate standard is based on UTM (Universal Transverse Mercator) map projection and UPS (Universal Polar Stereographic) coordinate systems.

## Sample file

**Sample** : [tileInfo.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/tileInfo.json)

## Reference: tile info

- **`cloudyPixelPercentage`** *(number, format: double)*: The percentage of the pixel data that is clouds.
- **`dataCoveragePercentage`** *(number, format: double)*: The percentage of the tile that is valid data.
- **`gridSquare`** *(string)*: The MGRS grid square coordinate.
- **`latitudeBand`** *(string)*: The MGRS latitude band.
- **`path`** *(string)*: The path at which the tile is available.
- **`subSquare`** *(string)*: The MGRS sub-square coordinate.
- **`tileDataGeometry`**: The outline of the data contained within the tile. Refer to [Definitions - Map(String,Object)](#definitions).
- **`tileGeometry`**: The geometry associated with the outline of the tile. Refer to [Definitions - Map(String,Object)](#definitions).
- **`tileID`** *(string)*: The ID of the tile.
- **`tileOrigin`**: The original coordinate of the tile. Refer to [Definitions - Map(String,Object)](#definitions).
- **`timestamp`** *(string)*: The ISO 8601 timestamp associated with the tile (typically the start of the data).
- **`utmZone`** *(integer, format: int32)*: The UTM zone of the data.
## Definitions

- <a id="%24defs/Map%28String%2CObject%29"></a>**`Map(String,Object)`** *(object)*
