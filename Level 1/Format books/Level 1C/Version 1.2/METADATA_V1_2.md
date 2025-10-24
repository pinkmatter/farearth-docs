##### [Home](../../../../README.md) > [Level 1](../../../../Level%201/) > [Format books](../../../Format%20books/) > [Level 1C](../../Level%201C/) > [Version 1.2](../Version%201.2/) > [Format book](README.md) > Product metatdata

# Level 1C product metadata

## Introduction
This is the main metadata file that describes the product. This file has the extension `.geojson` and is readable by third-party applications. This file is made up of a feature collection with a single feature representing the product properties which includes sensor properties. 

Note that only selected properties distinct to *FarEarth* are documented here.

## Sample file
**Sample** : [LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1.geojson](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.2/L1C/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L1C_R1C1.geojson)

## Properties

The GeoJSON file contains an array of features. Each feature has a `properties` object. This section describes the content of this object.

Each GeoJSON feature contains three objects:
* `type`: Always "Feature"
* `properties`: See [Feature properties](#feature-properties)
* `geometry`: See [Feature geometry](#feature-geometry)

### Feature properties

*FarEarth* products contains a `product` property in the `feature`, described below.

The Product properties consist of these objects:

| **Property** |  **Description** |  
| --- | ----- |
|`descriptor`|Describes the product. See [Descriptor](#product-descriptor)|
|`sensors`|Details relating to the sensors relevant to the product.See [Sensors](#sensors) |
|`elevation`|Details relating to the elevation of the product.See [Elevation](#elevation)|
|`pixelCount`| Number of pixels |
|`software`| Information regarding the software used to generate the product . See [Software](#software)|
|`thumbnailImageType`|The image format of the generated thumbnails. Must be one of: `["GEOTIFF_COG", "GEOTIFF", "BIG_GEOTIFF", "MEMORY", "PNG", "JPEG", "JP2000", "JP2000_LOSSLESS"]`|
|`thumbnails`|An array of thumbnails. See [Thumbnails](#thumbnails)|
|`viewingAngles`|The file containing the viewing angle information for the L1C product|
|`spectralResponses`| The file containing the spectral responses of the bands|
|`bandMapping` | A mapping of band ID to index|
|`cloudCover`|The cloud cover percentage (0.0 to 100.0)|
|`cloudsImage`|The file name of the cloud probability image|

### Product descriptor
The `descriptor` section contains general product properties. 

This table documents the `descriptor` section.

| **Property** |  **Description** |  
| --- | ----- |
| `generationDate` | An ISO-8601 date and time indicating when this product was generated |
| `productId` | An identifier for this product. Identifiers do not necessarily need to be unique within the *FarEarth* Catalogue, but it is recommended that the naming scheme be designed in such a way that it is unique |
| `productType`    | For Level 1C products this is always L1C |
| `sceneCol`       | If an interval is subdivided into multiple scenes, this property will reflect the column number of the scene. Column numbers start at 1 from the left |   
| `sceneRow`       | If an interval is subdivided into multiple scenes, this property will reflect the row number of the scene. Row numbers start at 1, along the track of the satellite  |
| `sensors`        | A list of identifiers to uniquely identify the sensor modules on the spacecraft |
| `spacecraft`     | The name of spacecraft that captured this product | 
| `temporalRange`  | A pair of UTC dates and times indicating the start and end of the period when the sensor was capturing pixels | 

### Sensors 

The `sensors` section contains details of each sensor module on the satellite. Each sensor module listed in the *descriptor:sensors* property of the product section has a corresponding entry here.

Each sensor has a descriptor section and a bands section.

This table documents the `sensors` section.

| **Property** | **Description**      |
|--------------|----------------------|
| `descriptor` | The sensor descriptor is made up of properties describing the sensor. See [Descriptor](#sensor-descriptor) for more details |
|`images` | The images section is an array of grouped bands, known as images in *FarEarth*. You can configure bands to certain groups. Bands with similar GSDs are typically grouped; bands with dissimilar GSDs cannot be grouped. This grouping does not affect the processing; it only affects the generated products. See [Images](#images) |
| `angles` | Solar and viewing angles relevant to the image. See [Angles](#angles) for more details |
|`quality`|Describes the sensor geometric quality. See [Quality](#orthorectification-quality)|

### Sensor descriptor

| **Property** | **Description**      |
|--------------|----------------------|
| `ids` | Identifier that the processing system uses internally to uniquely identify each band on the sensor |
| `name` | Human readable name for the sensor. This is not guaranteed to be unique within the product |
| `ancillaries` | A list of the ancillary files or products that were used to process this image. Ancillaries include a reference to the calibration files. See [Ancillaries](#ancillaries) for more details |

### Ancillaries

| **Property** | **Description**      |
|--------------|----------------------|
|`cpf`| The name of the general geometric calibration parameter file used during processing|
|`rpf`|The name of the radiometric calibration parameter file used during processing|

### Images

| **Property** | **Description**      |
|--------------|----------------------|
| `group` | A human readable name for the group of bands |
| `ids`| Identifier that the processing system uses internally to identify the band|
| `bands` | Identification of the bands that make up this image as used in *FarEarth*  |
| `image` | The filename of the data asset that corresponds with this image |
| `qaMask`| Reference to the image file containing the quality assessment mask for this band image (see Section 5 Quality assessment ) |
|`radiometric`|The radiometric section of the band. See [Radiometric](#radiometric)|
|`geometric`| The geometric section of the band. See [Geometric](#geometric)|

### Angles

| **Property** | **Description**      |
|--------------|----------------------|
| `sunAzimuth` | Sun azimuth angle. From the scene centre point on the ground, this is the angle between true north and the sun. Measured clockwise in degrees (0° - 360°)     |
| `sunElevation` | Sun elevation angle. The angle from the tangent of the scene centre point to the sun. Measured from the horizon in degrees (-90° - 90°). Negative values indicate the sun is below the horizon, e.g. sun elevation of -10° means the data was captured during nautical twilight |
| `viewOffNadir` | The angle from the sensor between nadir (straight down) and the scene center. Measured in degrees (0°-90°) |
| `viewIncidence` | The incidence angle is the angle between the vertical (normal) to the intercepting surface and the line of sight back to the satellite at the scene center. Measured in degrees (0°-90°) |
| `viewAzimuth` | Viewing azimuth angle. The angle measured from the sub-satellite point (point on the ground below the platform) between the scene center and true north. Measured clockwise from north in degrees (0°-360°) |

### Radiometric

| **Property** | **Description**      |
|--------------|----------------------|
| `units` | This property specifies the units of the pixel data See Section 3 for details |
| `esun` | The ESUN units and value that was used to process this band |
| `earthSunDistance` | The distance between the earth and the sun used to produce this L1C product in astronomical units |
| `spectral` | Spectral properties. See [Spectral](#spectral) |

### Geometric

| **Property** | **Description**      |
|--------------|----------------------|
| `dimensions` | A pair of numbers representing the number of pixels across track and along track respectively |
| `resolution` | The target size of each pixel when projected onto the Earth across track and along track respectively. The along track value may be negative, to reflect the convention of the upper left corner of the image having coordinate `[0, 0]`, while pixel rows are counted from the first row of the sensor. In this case the absolute value of the number is the along track GSD |
| `geometry` | A polygon representing the footprint on the band on Earth. Coordinates are for the projection above 
| `quality` | This property indicates whether a systematic or precision band alignment strategy was followed for the band. See the description for orthorectification below for details. See [Quality](#image-band-quality) |
| `projection` | The geometric projection of this band onto the Earth. EPSG projections are used in the form “EPSG:XXXXX” |

### Spectral

| **Property** | **Description**      |
|--------------|----------------------|
| `band` | The name of the imaging band |
| `centerWavelength ` | The center band wavelength (in nanometers) |
| `fullWidthHalfMax ` | The full-width half-max bandwidth of the band in question (in nanometers) |

### Orthorectification quality

This table documents the `quality` section under the `sensors` section.
| **Property** | **Description** |
|--------------|----------------------|
| `orthorectification` | The orthorectification type is either **systematic** or **precision**. The orthorectification type of an image is precision if every band has an orthorectification type of precision. |
| `metrics` | Metrics are listed in this property if the orthorectification type is precision. The metrics are identical to the metrics in the pointing files. |

**Systematic orthorectification**
Systematic orthorectification uses calibration coefficients, NavAtt data, and rough reference data such as the mean height above ellipsoid for the image.

**Precision orthorectification**
Precision orthorectification uses tiepoints and reference data to refine the geolocation of the image to higher accuracies. Individual pixels of the Digital Elevation Model (DEM) are used to determine precisely where the pixel is.

### Image band quality

This table documents the `quality` section under the `geometric` section.
| **Property** | **Description**      |
|--------------|----------------------|
| `bandAlignment` | A listing of which bands were corrected to what quality level. Best results would require that all bands are precision aligned |
| `precisionBands` | The names of the bands that were precision aligned against a reference orthorectfied image, or other ground control points |
| `systematicBands` | The name of the bands that were systematically aligned as fallback when precision alignment failed or were disabled |

### Elevation

The `elevation` section contains details relating to the elevation of the product.

| **Property** | **Description**      |
|--------------|----------------------|
| `averageMsl` | The average meters above sea level of the area covered in the product |
| `averageHae` | The average Height Above Ellipsoid of the area covered in the product |

### Software

The `software` section contains details related to the software used to generate the product.

| **Property** | **Description**      |
|--------------|----------------------|
| `name` | The software/executor used to generate the product |
| `version`| The version of the software/executor used to generate the product |

### Thumbnail image type

The `thumbnailImageType` field the image format of the generated thumbnails. Must be one of: `["GEOTIFF_COG", "GEOTIFF", "BIG_GEOTIFF", "MEMORY", "PNG", "JPEG", "JP2000", "JP2000_LOSSLESS"]`.

### Thumbnails

The `thumbnails` section is an array of thumbnail details.

This table documents the `thumbnails` section.

| **Property** | **Description**      |
|--------------|----------------------|
| `image` | The reference to the thumbnail image file |
| `name` | The human readable name of the thumbnail |

### Feature geometry 

The geometry section defines the full footprint of the image. It is formatted according to RFC 7946.

This table documents the descriptor section of the sensor.
| **Property** |**Description** |
| ------ | ---|
| `type` | The type of shape that is described in the `coordinates` property |
| `coordinates` | A list of (x,y) coordinates forming a closed image outline (with units in the stated projection). |