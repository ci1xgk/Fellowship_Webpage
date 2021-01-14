### Preparing the input data
LISFLOOD uses topographical data, or digital elevation model (DEM), in Esri ASCII raster format. This file contains the first six rows as header information, followed by a space delimited matrix of nrows x ncols (an example snapshot of the file is shown below). This serves as the base computational domain for the hydraulic simulations where the number of rows and columns defines the size of the computational domain.

![image](/Figures/mesh1.PNG)

LISFLOOD reads the DEM by including the keyword `DEMfile` in the `.par` file and following this with the name of the file to be read. To visualize, process or modify the DEM data, it is advised to use QGIS, a geographic information system, which is [freely available to download](https://www.qgis.org/en/site/forusers/download.html). 


#### Viewing a DEM file

---

#### Modifying the resolution of the DEM

---

#### Initial conditions files for ACC/FV1

---

#### DG2-related DEM files

---

#### DG2-related Initial condition files

---

#### Setting up boundary conditions

---

#### Selecting output type




[back](https://www.seamlesswave.com/Merewether.html)
