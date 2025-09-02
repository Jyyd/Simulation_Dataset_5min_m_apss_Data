# Quick Prediction Simulation Dataset

## Overview

This dataset contains simulated **hazardous gas dispersion data** generated using the [GRAMM GRAL](https://gral.tugraz.at/features.html).
The simulations are based on the **Chemical Park model** (available in the [University of Hamburg Wind Tunnel Laboratory dataset](https://www.mi.uni-hamburg.de/en/arbeitsgruppen/windkanallabor/data-sets.html)), which provides realistic **chemical park building layouts** used as the underlying geometry for the dispersion experiments.
The dataset is designed for research in **quick prediction of hazardous gas dispersion**, atmospheric environment modeling, and data-driven methods such as deep learning.

* **File format**: `.npz` (NumPy compressed archive)
* **Leak duration**: **5 minutes**

## Simulation Scenarios

### Meteorological Conditions

* **Wind direction (°)**: `0`, `90`, `180`, `270` (4 directions)
* **Wind speed (m/s)**: `0.5`, `1.5`, `2.5`, `3.5`, `4.5`, `5.5` (6 classes)
* **Atmospheric stability**: `2` (unstable), `4` (neutral), `6` (stable) (3 classes)

### Geographic Information

* **Building distribution**: Derived from the **Hamburg University Chemical Park model**
* **Terrain features**: Terrain and building information included in the simulations

### Hazardous Gas Source Terms

* **Substance**: Liquefied Natural Gas (LNG)
* **Source locations**: 98 potential release points available; **60 selected sources** are used for deep learning experiments

## Data Files

The dataset is provided as `.npz` files. Each file contains the following arrays:

* **`three_channel_data`** – Preprocessed 3-channel input data
* **`con_data_98`** – Concentration fields for 98 potential hazardous gas sources
* **`con_series_data`** – Time-series concentration data over the 5-minute simulation period
* **`meteo_vec`** – Encoded meteorological condition vectors (wind speed, wind direction, stability class)
* **`meteo_series_vec`** – Time-series meteorological inputs
* **`source_vec`** – Hazardous gas source term information (location and emission parameters)
* **`file_id`** – Unique identifier for each simulation case
* **`points_4`, `points_8`, `points_16`, `points_32`, `points_64`, `points_128`, `points_256`, `points_512`** – Sampling point data at different spatial resolutions

## Usage

The `.npz` files can be loaded directly using [NumPy](https://numpy.org/):

```python
import numpy as np

data = np.load("dataset_example.npz")

three_channel = data["three_channel_data"]
con_data = data["con_data_98"]
con_series = data["con_series_data"]
meteo_vec = data["meteo_vec"]
meteo_series = data["meteo_series_vec"]
source_vec = data["source_vec"]
points_32 = data["points_32"]

print("Three-channel data shape:", three_channel.shape)
```

## License and Citation

Please refer to the dataset license for usage conditions.

If you use this dataset, please cite as:
Jianyao, Y., & Zhang, X. (2025). 5min_m_apss_Data (1.0.0) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.17008799[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17008799.svg)](https://doi.org/10.5281/zenodo.17008799 (2025))
