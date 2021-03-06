# SeaWIFS_MOM6

Collection of Python notebooks for generating a chlorophyll dataset for MOM6 applications.

## Requirements
* dask        >= 2.12.0
* matplotlib  >= 3.1.2
* netcdf4     >= 1.5.3
* numpy       >= 1.19.4
* scipy       >= 1.4.0
* xarray      >= 0.15.0

## Download chlorophyll data

Follow these steps:

1) Register at https://urs.earthdata.nasa.gov/
2) Go to the ncfiles folder and edit get_SeaWiFS_data.sh (replace gustavo.marques with the user name created in 1)
3) Run get_SeaWiFS_data.sh

This should download the necessary chlorophyll data (*L3m_MC_CHL_chlor_a_9km.nc)

## Create SeaWIFS mask

Go to the notebooks folder and execute ```Create_SeaWIFS_Mask.ipynb```. This will generated file ```ncfiles/LandWater_SeaWIFS.nc```

## Combine SeaWIFS data

Go the notebooks folder and execute ```CombineSeaWIFS.ipynb```. This will generated file ```ncfiles/SeaWIFS.L3m_MC_CHL_chlor_a_0.25deg.nc```

## Interpolate and fill SeaWIFS data

First, go to ncfiles folder and generated a netCDF files using the provided *.cdl template:
```
ncgen -o seawifs-clim-1997-2010-tx0.66v1.nc seawifs-clim-1997-2010-tx0.66v1.cdl
```

Then go the notebooks folder and execute ```Interpolate_and_fill_SeaWIFS.ipynb```. This will generated the final file ```ncfiles/seawifs-clim-1997-2010-tx0.66v1.nc```
