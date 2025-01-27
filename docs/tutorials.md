# Tutorials

Some simple tutorials to get you started analysing the CANARI-LE.

- [Git Setup and Basics](github.md)

- [Configuring and Using the JASMIN Notebooks Service](jasmin_notebook_service.md)
  
- [Creating and Using your Own Conda/Mamba Enviroment](creating_your_own_conda_env.md)

- [Running on Sci Servers, installing Micromamba and running your own JupyterLab](running_on_sci_servers.md)

- [Using the Dask gateway](using_the_dask_gateway.md)

- [Computing indices with cf-python](cf_python.md)

- [CDFTOOLS](https://github.com/CANARI-sprint/CDFTOOLS):  a diagnostic package written in fortran 90 for the analysis of NEMO model output, initialized in the frame of the DRAKKAR project (https://www.drakkar-ocean.eu/)

- **Data Analysis Guides:** Access our data analysis guides hosted on the [tutorials repository](https://github.com/CANARI-sprint/tutorials).

- [Github collaborative working tutorial](git_tutorial.md)

To try these tutorials independently, clone the repository in JASMIN with the following commands:

```
git clone https://github.com/CANARI-sprint/tutorials.git
cd tutorials
```
`!IMPORTANT:` You need to have access to the CANARI gws.

Here's a catalog of the available notebooks.  The first 8 tutorials refer to the [COAsT python package](https://british-oceanographic-data-centre.github.io/COAsT/#about).

1) **[Basic Data Manipulation](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/1_basic_manipulation.ipynb):** Introduction to data handling using the COAsT package.

2) **[Exporting to NetCDF](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/2_export_to_netcdf.ipynb):** Guide on exporting outputs to netCDF format for future use or analysis.

3) **[Climatology Tutorial](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/3_climatology_tutorial.ipynb):** Demonstrates calculating climatological means and multi-year climatologies.

4) **[Calculating EOFs](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/4_calculate_eof.ipynb):** How to utilize COAsT for computing Empirical Orthogonal Functions (EOFs).

5) **[Potential Energy Analysis](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/5_potential_energy.ipynb):** Tutorial on calculating Potential Energy Anomaly and applying regional masking..

6) **[Pycnocline Diagnostics](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/6_pycnocline.ipynb):** Exploration of pycnocline depth and thickness diagnostics.

7) **[Seasonal Decomposition](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/7_seasonal_decomp.ipynb):** Techniques for decomposing time series into trend, seasonal, and residual components.

8) **[Transect Calculations](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/8_transect_calculation.ipynb):** Methods for creating data transects.

9) **[Basic Plots and Analysis](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/9_basic_plots_and_analysis.ipynb):** Utilizing CANARI-LE historical data for Sea Surface Temperature (SST) visualization.

10) **[UK Precipitation Plots](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/0_UK_Precipitation_with_iris.ipynb):** Making plots of UK precipitation using the iris python package, curtesy of Ben Harvey.

11) **[Box Profile Development](https://github.com/CANARI-sprint/tutorials/blob/main/notebooks/11_compute_and_plot_an_ocean_profile_using_lotus.ipynb):** Computing ocean profiles with selected variables making use of the lotus queue on JASMIN.