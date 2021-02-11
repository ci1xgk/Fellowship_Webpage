#### Eden 2015, fluvial flooding

This test case aims to simulate fluvial flooding resulted from rainfall over a large catchment. It is selected to demonstrate how to set up a simulation based on spatially- and temporally-varying rainfall data. The use of a post-processing toolkit for downscaling coarse-resolution DG2 flood maps is also explained. 

The LISFLOOD-FP is applied to reproduce the flood event caused by the 2015 Storm Desmond, which brought heavy rainfall to the 2500 square kilometers Eden Catchment. Figure below shows a map of the Eden catchment [(Xia et al. 2019)](https://www.sciencedirect.com/science/article/abs/pii/S030917081930243X). There are four major rivers in the catchment, including River Eden and its three tributaries, i.e. River Irthing, River Petteril and River Caldew. River Eden merges with the three tributaries as it passes through Carlisle, whiach was the most flooded city during the Storm Desmond event. 

![Image](/Figures/eden1.png)

For setting up the model the Digital Elevation Mode (DEM) over the whole catchment is required. The 5 m x 5 m resolution DEM data, named `eden-5m.dem`, is provided by [School of Architecture, Building and Civil Engineering at Loughborough University](https://www.lboro.ac.uk/departments/abce/). It was created by further processing the LiDAR DEM provided by the UK Ordnance Survey [(Ordnance Survey, 2018)](https://www.ordnancesurvey.co.uk/business-government/products/terrain-5) and improved by incorporating the locations and heights of flood defences published by the Environmental Agency [(Environment Agency, 2018)](https://data.gov.uk/dataset/8964d3f8-8273-4521-a4b9-3f0a268b6ecf/spatial-flood-defences-with-standardised-attributes). 

The Manning coefficient is assigned according to different land-use types: inside the river channel the value of the coefficint is equal to 0.055 and over floodplain and hillslope equal to 0.075. The Manning coefficient data is provided in a file named `eden-5m.n`(recall [*"Floodplain friction Manning's coefficient file (.n)"*](/Merewether1-7.md).

The spatially- and temporally-varying rainfall data is provided by the [UK Met-Office](https://catalogue.ceda.ac.uk/uuid/82adec1f896af6169112d09cc1174499). The datais at 1 km spatial resolution and 5 min temporal resolution and is provided in a NetCDF file named `eden-5m.nc` (recall [*"Spatially- and temporarily-varying rainfall file (.nc)"*](/Merewether1-8.md)). Figure below shows the time series of the average and median rainfall intensity over the catchment during Storm Desmond. 

![Image](/Figures/eden2.png)


[back](/LISFLOOD8.0.md)
