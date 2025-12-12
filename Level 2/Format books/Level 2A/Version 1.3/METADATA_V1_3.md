##### [Home](../../../../README.md) > [Level 2](../../../../Level%202/) > [Format books](../../../Format%20books/) > [Level 2A](../../Level%202A/) > [Version 1.3](../Version%201.3/) > [Format book](README.md) > Product metadata

# Level 2A product metadata

## Introduction
This is the main metadata file that describes the product. This file has the extension `.geojson` and is readable by third-party applications. This file is made up of a feature collection with a single feature representing the product properties, including sensor properties. 

Note that only selected properties distinct to *FarEarth* are documented here.

Refer to the [Reference](#reference-product-metadata) for a full breakdown of all the properties in the file.

## Sample file

**Sample** : [LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1.geojson](https://stfarearth3b2cstatic.blob.core.windows.net/product-samples/products/v1.3/L2A/LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1/LANDSAT-9_OLI_20220804T083603_20220804T083634_L2A_R1C1.geojson)

## Property details
This section contains explanations on specific properties of the product metadata file. All the properties that have been expanded on are listed in the [Reference](#reference-product-metadata) section.

The GeoJSON (`.geojson`) file contains an array of features. 

Each GeoJSON feature contains three objects:
* `type`: Always "Feature"
* `properties`: *FarEarth* products contain a `product` property in the `feature`. See [Product descriptor](#product-descriptor)
* `geometry`: See [Feature geometry](#feature-geometry)

### Feature properties
Each feature has a `properties` object. This section describes the content of this object.

*FarEarth* products contain a `product` property in the `feature`, described below.

### Product descriptor
The `descriptor` section contains general product properties. 

This table details certain properties of the `descriptor` section.

| Property |  Description |  
| --- | ----- |
| `productId` | An identifier for this product. Identifiers do not necessarily need to be unique within the *FarEarth* Catalogue, but it is recommended that the naming scheme be designed in such a way that it is unique |
| `temporalRange`  | A pair of UTC dates and times indicating the start and end of the period when the sensor was capturing pixels | 

### Sensors 

The `sensors` section contains details of each sensor module on the satellite. Each sensor module listed in the *descriptor:sensors* property of the product section has a corresponding entry here.

This table details certain properties of the `sensors` section.

| Property | Description      |
|--------------|----------------------|
|`images` | The images section is an array of grouped bands, known as images in *FarEarth*. You can configure bands to certain groups. Bands with similar GSDs are typically grouped; bands with dissimilar GSDs cannot be grouped. This grouping does not affect the processing; it only affects the generated products. See [Images](#images) |

### Images

| Property | Description      |
|--------------|----------------------|
| `qaMask`| Reference to the image file containing the quality assessment mask for this band image. The pixel values and bit representations are provided : 0 (000) is a normal pixel, 1 (001) is under saturated, 2 (010) is over saturated, 5 (101) is  under saturated and filled and 6 (110) is over saturated and filled. |

### Image Geometry

This table details certain properties of the `geometric` section under the `images` section.
| Property | Description      |
|--------------|----------------------|
| `quality` | This property indicates whether a systematic or precision band alignment strategy was followed for the image |
| `projection` | The geometric projection of this image onto the Earth. EPSG projections are used in the form "EPSG:XXXXX" |
| `imageDimensions` | A pair of numbers representing the number of pixels in the horizontal and vertical directions respectively |
| `spatialResolution` | The target size of each pixel when projected onto the Earth across track and along track respectively. The along track value may be negative, to reflect the convention of the upper left corner of the image having coordinate `[0, 0]`, while pixel rows are counted from the first row of the sensor. In this case the absolute value of the number is the along track target resolution (often set the same as the GSD) |
| `geometry` | A polygon representing the footprint on the image on Earth. Coordinates are for the projection above |

### Angles

This table details certain properties of the `angles` section.

| Property        | Description      |
|-----------------|----------------------|
| `sunAzimuth`    | Sun azimuth angle. From the scene centre point on the ground, this is the angle between true north and the sun. Measured clockwise in degrees (0° - 360°)     |
| `sunElevation`  | Sun elevation angle. The angle from the tangent of the scene centre point to the sun. Measured from the horizon in degrees (-90° - 90°). Negative values indicate the sun is below the horizon, e.g. sun elevation of -10° means the data was captured during nautical twilight |
| `viewOffNadir`  | The angle from the sensor between nadir (straight down) and the scene center. Measured in degrees (0°-90°) |
| `viewIncidence` | The incidence angle is the angle between the vertical (normal) to the intercepting surface and the line of sight back to the satellite at the scene center. Measured in degrees (0°-90°) |
| `viewAzimuth`   | Viewing azimuth angle. The angle measured from the sub-satellite point (point on the ground below the platform) between the scene center and true north. Measured clockwise from north in degrees (0°-360°) |

### Orthorectification quality

This table documents the `quality` section under the `sensors` section.
| Property             | Description      |
|----------------------|----------------------|
| `orthorectification` | The orthorectification type is either **systematic** or **precision**. The orthorectification type of an image is precision if the reference band has an orthorectification type of precision |

#### Systematic orthorectification
Systematic orthorectification uses calibration coefficients, NavAtt data, and rough reference data such as the mean height above ellipsoid for the image.

#### Precision orthorectification
Precision orthorectification uses tiepoints and reference data to refine the geolocation of the image to higher accuracies. Individual pixels of the Digital Elevation Model (DEM) are used to determine precisely where the pixel is.

### Feature geometry 

The geometry section defines the full footprint of the image. It is formatted according to RFC 7946.

This table documents the descriptor section of the sensor.
| Property | Description |
| ------------- | ---|
| `type`        | The type of shape that is described in the `coordinates` property |
| `coordinates` | A list of (x,y) coordinates forming a closed image outline (with units in the stated projection). |

## Reference: product metadata

The following reference describes the content of the product metadata file.
- **`ancestry`** *(array)*: A list of references comprising the inputs used to create the product.
  - **Items** *(object)*
    - **`productId`** *(string)*: The unique product ID.
    - **`productType`** *(string)*: The type or level of the product (e.g., RAW, DEM, L1A, L1C or L2A).
    - **`references`** *(array)*: A list of references which was used to generate the product.
      - **Items** *(object)*
        - **`productId`** *(string)*: The product ID uniquely identifying the reference.
        - **`productType`** *(string)*: The product type of the reference.
        - **`properties`** *(object)*: Any additional optional properties that serves to describe the reference product.
    - **`software`** *(object)*: Details relating to the software responsible for generating the product.
      - **`buildDate`** *(string)*: An ISO date timestamp describing when the software package was built.
      - **`name`** *(string)*: The name or ID of the software package.
      - **`revision`** *(string)*: A revision hash that further serves as identifying the exact software package version.
      - **`version`** *(string)*: A version uniquely identifying the software package.
- **`atmosImage`** *(string)*: The file name of the atmospheric data used for corrections.
- **`bandMapping`** *(object)*: A mapping of band ID to index.
- **`cloudCover`** *(number, format: float)*: The cloud cover percentage (0.0 to 100.0).
- **`cloudsImage`** *(string)*: The file name of the cloud probability image.
- **`descriptor`** *(object)*: Meta-data relevant to the product (Spacecraft, sensor, date-range of the product).
  - **`processedDate`** *(string, format: date-time)*: The date on which the product was generated.
  - **`productId`** *(string)*: The ID identifying the product.
  - **`productType`** *(string)*: The product type.
  - **`sceneCol`** *(integer, format: int32)*: If an interval is subdivided into multiple scenes (or tiles), the column index will reflect adjacent tiles across track starting counting at 1 for left-most scene. The interval will have at least one column, even it the interval is not subdivided.
  - **`sceneRow`** *(integer, format: int32)*: If an interval is subdivided into multiple scenes (or tiles), the row index will increment proportionally along track (starting at 1). The interval will have at least one row, even it the interval is not subdivided.
  - **`sensors`** *(array)*: A list of sensor IDs relevant to the product (if required, with preference for hyphenated separators instead of spaces or underscores).
    - **Items** *(string)*
  - **`spacecraft`** *(string)*: The ID of the spacecraft (if required, with preference for hyphenated separators instead of spaces or underscores, e.g., 'LANDSAT-7').
  - **`temporalRange`** *(object)*: The UTC start and end date of the product (with leap-seconds included).
    - **`from`**
      - **One of**
        - *string*
        - *number*
    - **`to`**
      - **One of**
        - *string*
        - *number*
- **`elevation`** *(object)*: Details relating to the elevation of the product.
  - **`averageHae`**: The average height above ellipsoid in meters. Refer to *[#/$defs/ValueMeters](#%24defs/ValueMeters)*.
  - **`averageMsl`**: The average height above the mean sea level in meters. Refer to *[#/$defs/ValueMeters](#%24defs/ValueMeters)*.
- **`pixelCount`** *(integer, format: int64)*: The total number of pixels across all bands of the product.
- **`sensors`** *(array)*: Details relating to the sensors relevant to the product.
  - **Items** *(object)*
    - **`descriptor`** *(object)*: Details relating to the imaging sensor (name, detector ID's, etc).
      - **`ancillaries`** *(object)*: Ancillary reference files used as calibration input during processing.
        - **`apf`** *(string)*: The name of the atmospheric calibration parameter file used during processing.
        - **`cpf`** *(string)*: The name of the general geometric calibration parameter file used during processing.
        - **`rpf`** *(string)*: The name of the radiometric calibration parameter file used during processing.
      - **`ids`** *(array)*: The detector IDs associated with the sensor.
        - **Items** *(string)*
      - **`name`** *(string)*: The name or unique ID for the sensor.
    - **`images`** *(array)*: Details related to images that were generated that is associated with the sensor.
      - **Items** *(object)*
        - **`angles`** *(object)*: Solar and view angles relevant to the image.
          - **`sunAzimuth`**: From the scene center point on the ground, this is the angle between truth north and the sun (measured clockwise in degrees between 0 and 360). Refer to *[#/$defs/ValueDegrees](#%24defs/ValueDegrees)*.
          - **`sunElevation`**: The angle from the tangent of the scene center point to the sun. Measured from the horizon in degrees (-90 to 90). Negative values indicate the sun is below the horizon, e.g. sun elevation of -10 means the data was captured during nautical twilight. Refer to *[#/$defs/ValueDegrees](#%24defs/ValueDegrees)*.
          - **`viewAzimuth`**: The angle measured from the sub-satellite point (point on the ground below the platform) between the scene center and true north (Measured clockwise from north in degrees between 0 and 360). Refer to *[#/$defs/ValueDegrees](#%24defs/ValueDegrees)*.
          - **`viewIncidence`**: The angle between the vertical (normal) to the intercepting surface and the line of sight back to the satellite at the scene center (in degrees, between 0 and 90). Refer to *[#/$defs/ValueDegrees](#%24defs/ValueDegrees)*.
          - **`viewOffNadir`**: The angle from the sensor between nadir and the scene center (in degrees, between 0 and 90). Refer to *[#/$defs/ValueDegrees](#%24defs/ValueDegrees)*.
        - **`bands`** *(array)*: The names of the bands available in this group. Non-unique names that matches the band IDs. Examples could include PAN, RED, GREEN, SWIR1, TIR1.
          - **Items** *(string)*
        - **`geometric`** *(object)*: Details relating to the geometric data of the image.
          - **`geometry`** *(array)*: A multi-sequence of (x,y) coordinates forming a closed image outline (with units in the stated projection).
            - **Items** *(array)*
              - **Items** *(array)*: Length must be equal to 2.
                - **Items** *(number)*
          - **`imageDimensions`** *(array)*: The pixel dimensions of the image (total rows and columns). Length must be equal to 2.
            - **Items** *(number)*
          - **`projection`** *(string)*: The projection string of the image (e.g., 'EPSG:32629').
          - **`quality`** *(object)*: The quality of the geometric corrections applied (e.g., the band-to-band alignment).
            - **`bandAlignment`** *(object)*: A listing of which bands were corrected to what quality level. Best results would require that all bands are precision aligned.
              - **`precisionBands`** *(array)*: The names of the bands that were precision aligned against a reference ortho image, or other ground control points.
                - **Items** *(string)*
              - **`systematicBands`** *(array)*: The name of the bands that were systematically aligned as fallback when precision alignment failed or were disabled.
                - **Items** *(string)*
          - **`spatialResolution`** *(array)*: The spatial resolution for any pixel in the image (as meters). Length must be equal to 2.
            - **Items** *(number)*
        - **`group`** *(string)*: The ID used to group different bands or their respective detector IDs together. Typically grouped together in the same image file by matching GSD resolutions. Examples include 'MS', 'RGB', 'VNIR' or 'VIS'.
        - **`ids`** *(array)*: The IDs of the bands available in this group. If multiple sensor assemblies are published separately, these ID's will be unique to allow differentiation between bands available on different sensors. Examples include 'SCA1_PAN', 'SCA1_RED', where another group could be 'SCA2_PAN', 'SCA2_RED'.
          - **Items** *(string)*
        - **`image`** *(string)*: The name of the file of which this group refers to.
        - **`qaMask`** *(string)*: The name of the quality mask file of which this group refers to.
        - **`radiometric`** *(object)*: Details relating to the radiometric data of the image.
          - **`earthSunDistance`** *(number, format: double)*: The average distance between the center of the earth and the center of the sun in Astronomical Units (AU). Typical values are between 0.9832 and 1.0167.
          - **`emissiveConstants`** *(array)*: A list of emissive conversion constant values for for each band. Emissive constants will vary only for emissive bands, with unity constants for reflective bands. Will be omitted if empty.
            - **Items** *(object)*
              - **`band`** *(string)*: The name of the imaging band.
              - **`constants`** *(array)*: The emissive constants are model parameters used for radiance to brightness temperature conversion.
                - **Items** *(number, format: double)*
          - **`esun`** *(array)*: A list of mean exo-atmospheric solar irradiance (ESUN) values for each band. ESUN values will only be available for reflective bands. Will be omitted if empty.
            - **Items** *(object)*
              - **`band`** *(string)*: The name of the imaging band.
              - **`units`** *(string)*: Typically 'W / (m^2 * um)'.
              - **`value`** *(number, format: double)*: The ESUN value of the band in question.
          - **`pixelUnits`** *(string)*: The pixel value representation of the image data ('Surface Reflectance x 10k', 'Surface Temperature x 100', or 'Surface Emissivity x 10k (optional)').
          - **`radianceConversion`** *(array)*: A list of radiance conversion values for for each band. The conversion values are only applicable to reflective bands. Will be omitted if empty.
            - **Items** *(object)*
              - **`band`** *(string)*: The name of the imaging band.
              - **`gain`** *(number, format: double)*: The gain of the imaging band.
              - **`offset`** *(number, format: double)*: The offset of the imaging band.
          - **`spectral`** *(array)*: The spectral band layout of the sensor.
            - **Items** *(object)*
              - **`band`** *(string)*: The name of the imaging band.
              - **`centerWavelength`** *(number, format: double)*: The center band wavelength (in nanometers).
              - **`fullWidthHalfMax`** *(number, format: double)*: The full-width half-max bandwidth of the band in question (in nanometers).
    - **`quality`** *(object)*: Quality metrics generated during processing.
      - **`atmospheric`** *(object)*: Quality of the atmospheric data used during processing.
        - **`aerosols`** *(object)*: The quality of the aerosol data used for atmospheric correction.
          - **`source`**: The source of the data for this atmospheric band (DETECTED, PREDICTED, ANCILLARY or FALLBACK). Refer to *[#/$defs/L2AAuxDataSource](#%24defs/L2AAuxDataSource)*.
        - **`ozone`** *(object)*: The quality of the ozone data used for atmospheric correction.
          - **`source`**: The source of the data for this atmospheric band (DETECTED, PREDICTED, ANCILLARY or FALLBACK). Refer to *[#/$defs/L2AAuxDataSource](#%24defs/L2AAuxDataSource)*.
        - **`waterVapor`** *(object)*: The quality of the water vapor data used for atmospheric correction.
          - **`source`**: The source of the data for this atmospheric band (DETECTED, PREDICTED, ANCILLARY or FALLBACK). Refer to *[#/$defs/L2AAuxDataSource](#%24defs/L2AAuxDataSource)*.
      - **`geometric`** *(object)*: Geometric quality metrics generated during processing.
        - **`orthorectification`** *(string)*: To what model quality orthorectification was achieved (either 'systemic' or 'precision'). Any detector which failed precision refinement will result in a fallback to 'systematic'. Must be one of: `["systematic", "precision"]`.
- **`software`** *(object)*: Details regarding the software used to generate the L2A product.
  - **`name`** *(string)*
  - **`version`** *(string)*
- **`spectralResponses`** *(string)*: The file name in which all the spectral responses for all bands can be found.
- **`thumbnailImageType`** *(string)*: The image format of the generated thumbnails. Must be one of: `["GEOTIFF_COG", "GEOTIFF", "BIG_GEOTIFF", "MEMORY", "PNG", "JPEG", "JP2000", "JP2000_LOSSLESS"]`.
- **`thumbnails`** *(array)*: Thumbnails of different band or sensor combinations.
  - **Items** *(object)*: Thumbnail details.
    - **`image`** *(string)*: The file name of the thumbnail image.
    - **`name`** *(string)*: The ID used to distinguish between different thumbnails.
- **`viewingAngles`** *(string)*: The file name in which all the viewing angles of the product can be found.
## Definitions

- <a id="%24defs/L2AAuxDataSource"></a>**`L2AAuxDataSource`** *(string)*: Must be one of: `["DETECTED", "PREDICTED", "ANCILLARY", "FALLBACK"]`.
- <a id="%24defs/ValueDegrees"></a>**`ValueDegrees`** *(object)*
  - **`units`** *(string)*: The SI unit the value is expressed in.
  - **`value`** *(number, format: double)*: The scalar value quantity.
- <a id="%24defs/ValueMeters"></a>**`ValueMeters`** *(object)*
  - **`units`** *(string)*: The SI unit the value is expressed in.
  - **`value`** *(number, format: double)*: The scalar value quantity.