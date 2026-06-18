# JMA-Model-Plot
JMA GSM Operational Weather Forecast Plotting Suite is a Python/Jupyter toolkit developed at the Bushehr Meteorological Office for downloading and visualizing JMA GSM forecasts over Iran and the Middle East. It automatically retrieves GRIB2 data and generates operational weather maps, PNGs, and animated GIFs using cfgrib, Matplotlib, and Cartopy.


# JMA GSM Operational Weather Forecast Plotting Suite

A complete Jupyter notebook for downloading and visualizing Japan Meteorological 
Agency (JMA) Global Spectral Model (GSM) forecast output over Iran and the wider 
Middle East. Developed at the Bushehr Meteorological Office, it brings the entire 
operational workflow into a single reproducible environment — from authenticated 
data acquisition through to publication-quality forecast maps.

## Features

### Data Download
A robust GRIB2 downloader that retrieves both surface and pressure-level fields 
(925, 850, 700, 600, 500, 300, and 200 hPa). Engineered for operational reliability:

- Automatically selects the correct model run (00 / 06 / 12 / 18 UTC) based on 
  real-time publication windows
- Organizes output by the actual run date
- Resumes interrupted sessions by skipping already-validated files
- Writes through temporary `.part` files with size checks, so corrupt transfers 
  or HTML error pages never leave behind unusable data
- Recognizes missing files (HTTP 404) and retries on transient network errors

### Forecast Products

**Surface fields**
- 3-hourly, 24-hour, and run-accumulated rainfall
- Total cloud cover
- 2 m temperature with 10 m wind streamlines
- 10 m wind with MSLP isobars and automated L/H pressure-center detection

**Upper-air fields**
- 925 hPa wind streamlines
- 850 hPa temperature advection
- 700 / 600 hPa relative humidity
- 500 hPa relative vorticity with geopotential height and temperature contours
- 300 / 200 hPa jet-level wind speed with height and vertical-velocity overlays

**Regional sea panels**
- Wind arrows and estimated wave height for the Persian Gulf, Gulf of Oman, 
  and Caspian Sea (land-masked to show marine fields over water only)

Each product is exported as time-stamped images and compiled into animated 
forecast loops, with wide-domain variants of several key fields for synoptic context.

## Requirements

- Python 3.13
- `requests`, `cfgrib`, `xarray`, `numpy`, `matplotlib`, `cartopy`, 
  `scipy`, `imageio`

Install with:

```bash
pip install requests cfgrib xarray numpy matplotlib cartopy scipy imageio
```

## Setup & Usage

1. Register for a WIS-JMA account at https://www.wis-jma.go.jp/ to obtain a 
   username and password.
2. Open the notebook and enter your credentials in the **CONFIG** cell:
```python
   USERNAME = ''   # your WIS-JMA username
   PASSWORD = ''   # your WIS-JMA password
```
3. Set your preferred save location in `OUTPUT_ROOT_DEFAULT`.
4. Run all cells. The downloader fetches the latest model cycle, then each 
   plotting cell generates its product set.

## Sample Output

You can view sample forecast maps [here](https://github.com/hshokoohi/JMA-Model-Plot/tree/plots-samples).

## Authors

Developed by **Hossein Shokoohi** & **Hussein Mastaneh** 
at the [Bushehr Meteorological Office](https://bushehrmet.ir).

## License

Released under the MIT License — see the [LICENSE](LICENSE) file for details.


