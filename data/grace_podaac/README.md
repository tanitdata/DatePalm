# GRACE/GRACE-FO Data

The GRACE/GRACE-FO JPL Mascon RL06.3M v04 CRI NetCDF file is too large
for GitHub (~500 MB).

## Download instructions

1. Go to NASA PO.DAAC: https://podaac.jpl.nasa.gov/
2. Search for "GRACE JPL Mascon RL06.3"
3. Download: `GRCTellus.JPL.200204_202501.GLO.RL06.3M.MSCNv04CRI.nc`
4. Place the file in this directory

The data pipeline notebook (`notebooks/DatePalm_GEE_Data_Pipeline.ipynb`)
expects this file at `data/grace_podaac/GRCTellus.JPL.200204_202501.GLO.RL06.3M.MSCNv04CRI.nc`
