
### Merewether urban flooding
This test case is based on a physical model constructed to simulate the overland flow path in an urban area in Merewether, Newcastle, Australia, during the June 2007 flooding event [(Smith et al. 2017)](https://www.tandfonline.com/doi/abs/10.1080/15715124.2016.1193510). The constructed model was 12.5 m long by 5 m wide, and and was scaled (30:1 horizontal, 9:1 vertical) to the prototype (Figure 1). The physical model experiments were run at steady state with a constant flow rate of 19.7 m3/s, through a section at the bottom boundary of the physical domain (Figure 2).

![image](/Figures/mer1.png)

<img src="https://github.com/ci1xgk/Fellowship_Webpage/blob/master/Figures/mer1.png" width="400" /><figcaption>Figure 1. Study site and physical model domain</figcaption>

<img src="https://github.com/ci1xgk/Fellowship_Webpage/blob/master/Figures/mer2.png" width="400" /><figcaption>Figure 2. Prototype Digital Elevation Model (DEM) and physical model layout.</figcaption>

The model DEM, water level and velocity data were recorded relative to an arbitrary datum (at model scale) and were transformed to prototype scale using known survey points and the Froude scaling relationships. These data files are available for download through the [Water Research Laboratory of University of New South Wales Australia Data Warehouse website](http://datawarehouse.wrl.unsw.edu.au/newcastlefloodmodel/).

The following sections aim to give an overview of LISFLOOD modeling environment and an step-by-step guid to run the Merewether urban flooding test case. 

#### 1. Introduction to LISFLOOD data requirements, input files and file formats

[1.3. title]()


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
