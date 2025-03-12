# Viewing angle file ([Home](README.md))

*JSON meta-data file describing viewing angles associated with the product.*

## Properties

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
- **`viewingIncidenceAngles`** *(array)*: Angle grid listing the incidence angles per band and detector ID.
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
