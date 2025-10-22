# Navigation and attitude file

*A set of measurements describing the available navigation and attitude points associated with the image.*

## Properties

- **`attitude`** *(array)*
  - **Items** *(object)*
    - **`quaternion`** *(array)*: Attitude point expressed as a quaternion. Length must be equal to 4.
      - **Items** *(number)*
    - **`timestamp`** *(string, format: date-time)*: A (seconds, nanoseconds) representation of the timestamp.
- **`ephemeris`** *(array)*
  - **Items** *(object)*
    - **`eciPos`** *(array)*: The ECI postion 3D vector. Length must be equal to 3.
      - **Items** *(number)*
    - **`eciVel`** *(array)*: The ECI velocity 3D vector. Length must be equal to 3.
      - **Items** *(number)*
    - **`ecrPos`** *(array)*: The ECR postion 3D vector. Length must be equal to 3.
      - **Items** *(number)*
    - **`ecrVel`** *(array)*: The ECR velocity 3D vector. Length must be equal to 3.
      - **Items** *(number)*
    - **`timestamp`** *(string, format: date-time)*: A (seconds, nanoseconds) representation of the timestamp.
- **`inertialFrame`** *(string)*: The reference frame in which the attitude points are expressed in. Must be one of: `["J2000", "TOD", "ITRF", "GTOD", "MOD", "CIRF", "GCRF", "TIRF", "TEME", "ICRF"]`.
