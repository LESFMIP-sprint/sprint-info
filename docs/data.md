# Data 

The CANARI-LE has now completed running on ARCHER2. The CANARI-LE consists of 40 ensemble members of both the CMIP6 historical simulation and SSP3-7.0.  Data is stored on tape in JASMIN and priority data in stored on the JASMIN CANARI group workspace (gws).

## Ensemble Details 

Model: HadGEM3-GC1.3-MM, same configuration as used in CMIP6, global configuration version 3.1

Ocean: NEMO3.6

Atmosphere: UM

Sea Ice: CICE

Land: Jules

40 historical (1950-2014) ensemble members

40 future projection, SSP3-7.0 (2015-2100) ensemble members 

More information on the CANARI-LE can be found [here](https://ncas-cms.github.io/canari/).

## Data Access

To access the CANARI-LE data available on JASMIN you need to apply for access to the CANARI gws through the [JASMIN accounts portal](https://accounts.jasmin.ac.uk/) under the my services button.

CANARI-LE data can be found here (/gws/nopw/j04/canari/shared/large-ensemble/priority/).  HIST2 contains the 40 historical ensemble members, 1950-2014, SSP370 the future projection ensemble members, 2015-2100, and HIST1 are the 4 historical ensemble members which were part of CMIP6, 1850-2014.

The list of priority variables are on this [spreadsheet](https://ncas-cms.github.io/canari/metadata/20240229-canari-le-priority-variables.xlsx).  You can find the long names for the variables and the short names used in the netcdf files.  Please pay particular attention to the notes in red.

## Useful Files

For the ocean the mesh_mask and subbasins files can be found in the CANARI gws here /gws/nopw/j04/canari/shared/large-ensemble/ocean

## How to cite

There is no specific paper yet on the large ensemble, so please reference the HadGEM3.1 paper ([Williams et al. 2017](https://agupubs.onlinelibrary.wiley.com/doi/10.1002/2017MS001115)) and acknowledge CANARI and JASMIN.

## HadGEM3-GC3.1-MM Papers

[Williams et al. 2017](https://agupubs.onlinelibrary.wiley.com/doi/10.1002/2017MS001115) The Met Office Global Coupled Model 3.0 and 3.1 (GC3.0 and GC3.1) Configurations

[Menary et al. 2018](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2018MS001495) Preindustrial Control Simulations With HadGEM3-GC3.1 for CMIP6

[Andrews et al. 2020](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2019MS001995) Historical Simulations With HadGEM3-GC3.1 for CMIP6

[Lai et al. 2022](https://journals.ametsoc.org/view/journals/clim/35/4/JCLI-D-21-0281.1.xml) Mechanisms of Internal Atlantic Multidecadal Variability in HadGEM3-GC3.1 at Two Different Resolutions
 