#### Carlistle 2005, urban flooding TBA

<!---Why this case study? Should be different than EA5.  
Underway (MKS management): 5 m, 10 m, 20 m and 40 m for a comparision between ACC-CPU/GPU, FV1-CPU/GPU, DG2-CPU/GPU. Coarse-DG2 does not need GPU! Better velocity prediction. Compare floodplains with metrics H, F and C at t = 3 hours. Downscaling capability.--->

This test case demonstartes the urban flooding simulations in a real-world study area with multiple point source inflow boundary conditions. The study domain covers about 14.5 square kilometers of the urbanised area of Carlisle, a city in northern England with a population of 70,000. The area was heavily hit by flooding in January 2005, with an estimated return period of 150 years [(Horritt et al. 2010)](https://www.icevirtuallibrary.com/doi/pdf/10.1680/wama.2010.163.6.273). There are three main river channels within the area, i.e. River Eden, Petteril and Caldew, which drive the flood dynamics. Figure below shows the stuudy area.

![Image](/Figures/carl_1.PNG)

To simulate the Carlisle flood event the DEM data and upstream inflow boundary conditions (i.e. flow hydrographs) are required. The 5 m x 5 m resolution DEM data, namely `carlisle-5m.dem`, is provided by the School of Geographical Sciences at the University of Bristol, which was created by further processing the LiDAR DEM provided by the UK Environment Agency (EA) by removing the noises and obstacles (e.g. trees and bridges). 

Flood inflow enters from rivers Eden, Petteril and Caldew marked in figure above as *Upstream 1*, *Upstream 2* and *Upstream 3*, respectively. The discharge hydrographs (in 15-minute intervals) obtained through 1D flood routing are available from previous studies (e.g. [Neal et al., 2013](https://onlinelibrary.wiley.com/doi/10.1002/hyp.9572)), as shown in figure below.

![Image](/Figures/carl_2.PNG)

To set up this test case, th three river inflows are specified as point sources in the `carlisle-5m.bci`, while western edge of the domain is set as free outflow to allow the water to exit the domain. Figure below shows an snapshot of the `carlisle-5m.bci` file.

![Image](/Figures/carl_3.PNG)

In the first row, the western boundary is set as `FREE` boundary condition. The rest of the rows specify a series of points sources (identifier `P`), defined as the time-varying inflow (type `QVAR`) with names `upstream1`, `upstream2`, `upstream3` refering to respective time series specified in the `.bdy` file. The *Upstream 1*, which is the section of River Eden from point `(x,y) = (342662, 557552)` to `(x,y) = (342707, 557503)`, is spanned by 11 cells and is named `upstream1`. The *Upstream 2*, which is the section of River Petteril from point `(x,y) = (341352, 554702)` to `(x,y) = (341377, 554702)`, is spanned by 6 cells and is named `upstream2`. The *Upstream 3*, which is the section of River Caldew from point `(x,y) = (339937, 554702)` to `(x,y) = (339962, 554702)`, is spanned by 6 cells and is named `upstream3`

Since time-varying inflow is specifified in a `carlisle-5m.bci` file, it is accompanied with a time series file named `carlisle.bdy` file. The layout of the `carlisle.bdy` file follows the same structure explained for [*"Valley flooding"*](/EnvAcy5.md) test case. However, here three time series are written consecutively: The first row specifies the first time series name, `upstream1`, followed by the the number of time intervals, and the lists of the time-varying inflow discharge alongside its time of occurence; After all data of time series `upstream1` is written, the data for `upstream2` and then `upstream3` will be listed with the same order. 


[back](/LISFLOOD8.0.md)

