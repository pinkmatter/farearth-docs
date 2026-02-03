##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > STAC product

# Level 1C STAC product

## Introduction

This document describes the Level 1C product JSON (`.json`) file. The product file contains metadata and references to the other files that make up a product. The Level 1C product file complies with the STAC specification. STAC is a standardized way to expose collections of spatial temporal data. For more information about the STAC specification, refer to [The STAC Specification](https://stacspec.org/en/about/stac-spec/).

## Sample file

**Sample** :  [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_product.json](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1_product.json)

## STAC extensions

The *FarEarth* product file makes use of STAC extensions. The list of the STAC extensions used in *FarEarth*:

* [Projection Extension Specification (proj)](https://github.com/stac-extensions/projection)
* [Electro-Optical Extension Specification (eo)](https://github.com/stac-extensions/eo)
* [View Geometry Extension Specification (view)](https://github.com/stac-extensions/view)

## Assets
Every *FarEarth* product consists of a product file and a set of asset files. The product file describes the product at a high-level and lists the asset files. Each asset file has a type and at least one role associated with it. The role describes the information and intended use of the file. The type describes the file format. 

Product files may also contain high-level metadata used to index the product in the *FarEarth* catalogue.

### Asset Roles

|Role|Asset description|
|---|---|
|`data`|Image data|
|`metadata`| Metadata about the product|
|`quality`| Information about the geometric quality of the products|
|`thumbnail`| Overview / preview images of the products |
|`angles`| Information about the viewing and solar angles |
|`gverify`| Information on the geometric verification of the product|
|`aux`| Additional files required by the product|

## Properties
The Level 1C product JSON has a `properties` section with various details about the product at hand.

Certain *FarEarth* specific properties have been grouped into categories below.

### *FarEarth* Catalogue properties

These properties can be used to specify or find products in the *FarEarth* catalogue.
|Property|Description|
|---|---|
|`subscriptionId`| The ID of the *FarEarth* subscription that owns the product|
|`orderId`|The unique ID for the order for the product. An example is *AAAA-1001*.|
|`dataset`| *FarEarth* Products can be placed into a *dataset*, which is a subset of the *FarEarth* catalogue.| 
|`correlationId`| An ID that is shared for all *FarEarth* products that are either derived from or were used to derive the *FarEarth* product with that correlation ID. It is recommended that this ID is unique|
| `sceneCol`|If an interval is subdivided into multiple scenes, this property will reflect the column number of the scene. Column numbers start at 1 from the left, across the track of the satellite|
| `sceneRow`|If an interval is subdivided into multiple scenes, this property will reflect the row number of the scene. Row numbers start at 1, along the track of the satellite|

### *FarEarth* Quality properties
The properties are specific to *FarEarth* and provide information based on the geometric quality of a *FarEarth* product.

|Property|Description|
|---|---|
|`processingBaseline`|Version of the processing algorithm|
|`orthomodel`| Orthorectification model used during processing of the product. See [Orthorectification](#orthorectification)|
|`fe:qaGeo:ce95`|Circular Error with a 95 % probability. It is a metric used to quantify the geometric accuracy of a product, calculated as an average of all the CE95 errors calculated for each band|
|`fe:qaGeo:gsdX`|Minimum ground sampling distance of all the images in the product, in horizontal direction|
|`fe:qaGeo:gsdY`|This is the minimum ground sampling distance of all the images in the product, in the vertical direction|
|`bandAlignmentModel`|The orthorectification model used to align the sensor bands of the product|

### Orthorectification
The orthorectification type is either **systematic** or **precision**.

#### Systematic orthorectification
Systematic orthorectification uses calibration coefficients, NavAtt data, and rough reference data such as the mean height above ellipsoid for the image.

#### Precision orthorectification
Precision orthorectification uses tiepoints and reference data to refine the geolocation of the image to higher accuracies. Individual pixels of the Digital Elevation Model (DEM) are used to determine precisely where the pixel is.