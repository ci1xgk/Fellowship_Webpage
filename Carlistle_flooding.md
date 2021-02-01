#### Carlistle 2005, urban flooding TBA

Why this case study? Should be different than EA5.  
Underway (MKS management): 5 m, 10 m, 20 m and 40 m for a comparision between ACC-CPU/GPU, FV1-CPU/GPU, DG2-CPU/GPU. Coarse-DG2 does not need GPU! Better velocity prediction. Compare floodplains with metrics H, F and C at t = 3 hours. Downscaling capability.

This test case demonstartes the urban flooding simulations in a real-world study area with multiple point source inflow boundary conditions. The study domain covers about 14.5 square kilometers of the urbanised area of Carlisle, a city in northern England with a population of 70,000. The area was heavily hit by flooding in January 2005, with an estimated return period of 150 years. This resulted in the inundation of 1700 properties, 3000 people being evacuated and two deaths [(Horritt et al. 2010)](https://www.icevirtuallibrary.com/doi/pdf/10.1680/wama.2010.163.6.273). There are three main river channels within the area, i.e. River Eden, Petteril and Caldew, which drive the flood dynamics. Figure below shows the stuudy area.

![Image](/Figures/carl_1.PNG)

To simulate the Carlisle flood events the DEM data and upstream inflow boundary conditions (i.e. flow hydrographs) are required. The DEM data is provided by the School of Geographical Sciences at the University of Bristol, which was created by further processing the LiDAR DEM provided by the UK Environment Agency (EA) by removing the noises and obstacles (e.g. trees and bridges). The DEM has a 5 m spatial resolution. 

The three boundary points are marked in figure above as “Upstream 1” (Easting: 342682, Northing: 557532) located in the North-East of the domain, and “Upstream 2” (Easting: 341362, Northing: 554702) and “Upstream 3” (Easting: 339947, Northing: 554702) located at the south edge of the domain. TBA 

The 15-minute discharge hydrographs obtained through 1D flood routing are available from previous studies ([e.g. Neal et al., 2013; Parkes et al., 2013]()). TBA

[back](/LISFLOOD8.0.md)

