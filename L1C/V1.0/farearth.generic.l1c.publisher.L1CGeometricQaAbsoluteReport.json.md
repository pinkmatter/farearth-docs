# Absolute geometric disparity metrics ([Home](README.md))

*Metrics describing the difference between the image when compared to a reference.*

## Properties

- **`measurements`** *(array)*: A list of disparity metrics grouped by individual bands.
  - **Items** *(object)*
    - **`coordsLonLat`** *(array)*: The (longitude, lattitude) coordinates of the evaluated tie-points.
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
