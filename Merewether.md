Description of the test case + 

- DG2 initial condition and topography 
- Fine resolution modelling (0.175m ==> millions of cells)
- Benefit of GPU solvers 
- Velocitiy prediction and small eddy capturing (Water levels + velocities)
- Bug free codes for DG2/FV1 CPU and GPU 
- Other metrics like relevance index.



## Intro
LISFLOOD uses topographical data, or digital elevation model (DEM), in Esri ASCII raster format. This file contains the first six rows as header information, followed by a space delimited matrix of nrows x ncols (an example snapshot of the file is shown below). This serves as the base computational domain for the hydraulic simulations where the number of rows and columns defines the size of the computational domain.

![View of a DEM raster file](https://github.com/ci1xgk/Fellowship_Webpage/blob/master/Figures/mesh1.PNG)

LISFLOOD reads the DEM by including the keyword `DEMfile` in the `.par` file and following this with the name of the file to be read. 

In order to visualize, process or modify the DEM data, it is advised to use QGIS, a geographic information system, which is [freely available to download](https://www.qgis.org/en/site/forusers/download.html). 

In this section the preparation and process of the DEM data is explained for Merewether test case, as an example. The same process could be used for other test cases.









[back](https://www.seamlesswave.com/LISFLOOD8.0.html)
