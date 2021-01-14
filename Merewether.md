### Merewether urban flooding
This test case is based on a physical model constructed to simulate the overland flow path in an urban area with building including pieres in Merewether, Newcastle, Australia, during the June 2007 flooding event [(Smith et al. 2017)](https://www.tandfonline.com/doi/abs/10.1080/15715124.2016.1193510). The constructed model was 12.5 m long by 5 m wide, and was scaled (30:1 horizontal, 9:1 vertical) to the prototype shown in the figure below.

![image](/Figures/mer1.png)


The model DEM, water level and velocity data were recorded relative to an arbitrary datum (at model scale) and were transformed to prototype scale using known survey points and the Froude scaling relationships. These data files are available for download through the [Water Research Laboratory of University of New South Wales Australia Data Warehouse website](http://datawarehouse.wrl.unsw.edu.au/newcastlefloodmodel/). An overview of the DEM including the location of buildings and of the inflow (bottom right corner) are shown in the figure below. The physical model experiments were run at steady state with a constant flow rate of 19.7 cubic meters per second.

![image](/Figures/mer2.png)

In the following, an an overview of LISFLOOD modeling environment is provided followed by a step-by-step guid for setting up and running the Merewether urban flooding test case. 


#### 1. Data requirements, input files and their format

#### 2. Title


## Intro
LISFLOOD uses topographical data, or digital elevation model (DEM), in Esri ASCII raster format. This file contains the first six rows as header information, followed by a space delimited matrix of nrows x ncols (an example snapshot of the file is shown below). This serves as the base computational domain for the hydraulic simulations where the number of rows and columns defines the size of the computational domain.

![View of a DEM raster file](https://github.com/ci1xgk/Fellowship_Webpage/blob/master/Figures/mesh1.PNG)

LISFLOOD reads the DEM by including the keyword `DEMfile` in the `.par` file and following this with the name of the file to be read. 

In order to visualize, process or modify the DEM data, it is advised to use QGIS, a geographic information system, which is [freely available to download](https://www.qgis.org/en/site/forusers/download.html). 

In this section the preparation and process of the DEM data is explained for Merewether test case, as an example. The same process could be used for other test cases.









[back](https://www.seamlesswave.com/LISFLOOD8.0.html)
