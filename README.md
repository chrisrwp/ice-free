# ice-free

## Journal article using this analysis
Wyburn-Powell, C. & Jahn, A. Brief Communication: The Interdecadal Pacific Oscillation is not a Reliable Indicator of the Timing of an Ice-Free Arctic. *The Cryosphere*. Manuscript EGUSPHERE-2026-2082, accepted on 2026-10-20.

## Location of data
The data required to reproduce all figures in the journal article can be found at The Arctic Data Center: https://doi.org/10.xxxxx. The Jupyter Notebooks and important input and output files used to create each published figure are listed below.

## Abstract of journal article
The Arctic is transitioning towards a seasonally ice-free state over the next few decades, with internal variability
determining precisely when. The phase of the Interdecadal Pacific Oscillation (IPO) has been proposed to reduce internal
variability uncertainty in ice-free predictions. Using eight large ensembles from the Coupled Model Intercomparison Project Phase 5 (CMIP5) and CMIP6, starting from current mean sea ice extent, we find no agreement that the IPO affects ice-free
timing. However, a majority of large ensembles indicate the IPO can affect the rate and spatial distribution of Arctic sea ice
decline over the next two decades.

<br>

## Description of code and data

- **Calculate_IPO.ipynb**: Reads sea surface temperature outputs for the CMIP5 and CMIP6 global climate models (GCMs) stored on `/glade` and the HadISST observational data. Calculates the Henely et al. (2015) Tripolar Index IPO and outputs an IPO time series per ensemble member and observational data set, using Lanczos filtering or 11-year running means.
- **NSIDC_HadISST1_SIC_to_SIA.ipynb**: Calculates sea ice extent (SIE) and sea ice area (SIA) from observational HadISST1 data and outputs a time series from 1870-2025.
- **SIA_SIE_calculations.ipynb**: Compute time series for regional and pan-Arctic SIE and SIA derived from GCM member sea ice concentration (SIC) fields, outputs as one NetCDF per GCM ensemble member.
- **SIC_Composites_by_IPO_phase.ipynb**: Compute the composites of SIC based on each GCM's initially positive and negative IPO members. Outputs NetCDF files of SIC mean and standard deviation per GCM.
- **ERA5_download.ipynb**: Download of ERA5 geopotential heights, no used in final publication analysis
- **Replicate_Screen_and_Deser**: Rough analysis used to produce Figure 1. Uses SIE and IPO calculated previously.
- **Ice-Free_and_IPO_Relationship.ipynb**: Rough analysis used to produce Figures 2 and 3. Uses SIE, IPO and SIC composites calculated previously.

- **Figure_1.ipynb**: Figure 1 is computed using `IPO_11yr_annual_av_TPI_filtered_11yr_Lanczos_all_models.nc` and `All_Model_September_SIE.nc` with the start years defined by the year with SIE closest to 4.7 million square kilometers.
- **Figure_2.ipynb**: Figure 2 a) is computed using `IPO_11yr_annual_av_TPI_all_models.nc` to define positive and negative initially negative IPO ensemble members, for which the SIE trajectories are plotted using `All_Model_September_SIE.nc`. Figure 2 b,c) are computed using `SIC_traj_IPO_neg_start_42_52_sq_km_regrid.nc` and `SIC_traj_IPO_pos_start_42_52_sq_km_regrid.nc` minus the `SIC_traj_ensemble_start_42_52_sq_km_regrid.nc` mean value. With the ice-free regions defined by `SIC_traj_ensemble_start_42_52_sq_km_regrid.nc` and the statistically significant regions defined by `SIC_traj_ensemble_start_42_52_sq_km_regrid.nc` standard deviation vs `SIC_traj_IPO_<pos/neg>_start_42_52_sq_km_regrid.nc` absolute SIC values. The land mask and projection is defined by: `CanESM2_sftlf_regrid_1x1_deg.nc`
- **Figure_3.ipynb**: Figure 3 is computed by finding the ice-free year for each ensemble member in `All_Model_September_SIE.nc`. Then for each ice-free year anomaly relative to the ensemble mean, the correlation is computed for the IPO value for that ensemble member from `IPO_11yr_annual_av_TPI_all_models.nc`

<br>

## Python package versions from NPL 2023b
This code was run on NCAR's Casper/Derecho systems in the
[NCAR Python Library](https://ncar-hpc-docs.readthedocs.io/) environment `npl-2023b`:

| Package        | Version |
|----------------|---------|
| python         | 3.10.12 |
| cartopy        | 0.21.1  |
| cdsapi         | 0.6.1   |
| dask           | 2023.7.0|
| dask-jobqueue  | 0.8.2   |
| matplotlib     | 3.7.3   |
| numpy          | 1.24.4  |
| pandas         | 2.0.3   |
| scipy          | 1.11.1  |
| statsmodels    | 0.14.0  |
| xarray         | 2023.6.0|
