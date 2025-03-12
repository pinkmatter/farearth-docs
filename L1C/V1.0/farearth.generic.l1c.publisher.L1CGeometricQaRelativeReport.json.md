# Relative geometric disparity metrics ([Home](README.md))

*Metrics describing the disparity between different bands of the image.*

## Properties

- **`measurements`** *(array)*: A list of disparity metrics grouped by individual bands.
  - **Items** *(object)*
    - **`coordsLatLon`** *(array)*: The (longitude, lattitude) coordinates of the evaluated tie-points.
      - **Items** *(array)*
        - **Items** *(number, format: double)*
    - **`disparitiesXYInMeters`** *(array)*: A list of (x,y) disparities of the evaluated tie-points (in meters).
      - **Items** *(array)*
        - **Items** *(number, format: double)*
    - **`from`** *(string)*: The band ID of the source used during comparison.
    - **`imageName`** *(string)*: An illustration of the quality of all the tie-points evaluated on the image.
    - **`to`** *(string)*: The band ID of the target used during comparison.
- **`pixelColorMappings`** *(string)*: Mappings used to quantify disparities in color ranges (only for display purposes).
