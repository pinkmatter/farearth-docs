# L1C geometric pointing metrics

*Metrics describing how the image location was adjusted from raw to processed.*

## Properties

- **`measurements`** *(array)*: Listed by different sensors.
  - **Items** *(object)*
    - **`metrics`** *(object)*: Metrics describing how the image location was adjusted from raw to processed, listed by sensor ID.
    - **`orthorectification`** *(string)*: To what model quality orthorectifcation was achieved (either 'systemic' or 'precision'). Any detector which failed precision refinement will result in a fallback to 'systematic'. Must be one of: `["systematic", "precision"]`.
    - **`sensorIds`** *(array)*
      - **Items** *(string)*
    - **`sensorName`** *(string)*
