# Spectral Time Series - Optimal Transport (STS_OT)

A Python-based project for constructing reliable spectral time series of supernovae using Optimal Transport (OT) interpolation methods. This repository contains tools for sample selection, spectral interpolation, calibration, and weighted mean calculations for supernova spectral data.

## Overview

This project implements a methodology for computing interpolated grids of spectra using Optimal Transport for each supernova in the dataset. The workflow includes:

1. **Sample Selection**: Curating high-quality supernova data by comparing synthetic and observed photometry
2. **OT Combinations**: Generating interpolated spectra between pairs of observed spectra using Optimal Transport
3. **Calibration**: Calibrating the generated spectral grids using K-values for different bands
4. **Weighted Mean**: Computing weighted mean spectral time series from the interpolated data

## Features

- Spectral spline calculation and interpolation
- Optimal Transport-based spectral interpolation between observation epochs
- Photometric calibration using synthetic vs observed flux ratios
- Quality assessment using Median Absolute Deviation (MAD)
- Support for multiple supernova types (Type Ia, Ib, Ic)

## Requirements

- Python 3.7 or higher
- Jupyter Notebook or JupyterLab
- See `requirements.txt` for detailed package dependencies

## Installation

1. Clone this repository:
```bash
git clone https://github.com/mramirezz/STS_OT.git
cd STS_OT
```

2. Install the required packages:
```bash
pip install -r requirements.txt
```

## Project Structure

```
STS_OT/
├── Codes/
│   ├── 1 - Sample Selection.ipynb          # Sample curation and spline calculation
│   ├── 2 - OT combinations.ipynb           # Optimal Transport interpolation
│   ├── 3 - Calibrating OT.ipynb            # Calibration of interpolated spectra
│   ├── 4 - Weighted Mean OT .ipynb         # Weighted mean calculation
│   └── Funciones_colab.ipynb               # Common functions and utilities
├── Data/                                    # Data directory (ignored by git)
│   ├── spectra/                             # Input spectral data files
│   └── photometry/                          # Photometric data files
└── requirements.txt                         # Python dependencies
```

## Usage

The notebooks should be executed in sequential order:

1. **Sample Selection** (`1 - Sample Selection.ipynb`): 
   - Reads spectral data from `Data/spectra/`
   - Calculates splines for all spectra
   - Performs quality selection based on K-values and MAD

2. **OT Combinations** (`2 - OT combinations.ipynb`):
   - Generates interpolated spectra between pairs of observations
   - Uses Optimal Transport to create intermediate spectra
   - Handles time gaps and spectral normalization

3. **Calibrating OT** (`3 - Calibrating OT.ipynb`):
   - Calibrates the interpolated spectral grids
   - Uses K-values for different photometric bands

4. **Weighted Mean OT** (`4 - Weighted Mean OT .ipynb`):
   - Computes weighted mean spectral time series
   - Combines interpolated spectra with appropriate weights

## Data Format

- **Spectral files**: Text files in `Data/spectra/` with format `SN[NAME]_spectra.dat`
- **Photometry files**: Text files in `Data/photometry/` with format `SN[NAME]_photometry.dat`

## Methodology

### Sample Selection
The selection criterion uses the ratio K = F_obs / F_syn, where F_obs is the observed flux and F_syn is the corresponding synthetic flux. The Median Absolute Deviation (MAD) is used to evaluate the quality of each K value and identify outliers.

### Optimal Transport Interpolation
The project explores all possible combinations between pairs of spectra for each supernova, generating interpolated spectra that lie between them. This facilitates the generation of a weighted mean spectral time series.

## Author

**Mauricio Ramirez**
- Email: m.ramirezvalenzuela@gmail.com

## License

This project is provided as-is for research purposes.

## Notes

- The `Data/` directory is ignored by git to prevent uploading large data files
- The notebooks were originally designed to work in Google Colab but can be run locally
- Make sure to adjust the working directory paths in the notebooks if running locally
