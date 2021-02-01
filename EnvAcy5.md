### Valley flooding following a dam failure

This test case is standard to study and compare the capabilities of 2D hydrodynamic solvers for modelling rapidly-propagating flow over a non-smooth valley ([Ayog et al. 2021](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858); [Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). The 10 m x 10 m resolution DEM and the inflow hydrograph are available from the UK Environment Agency. Coarser resolution DEMs can be produced via QGIS ([recall the "_Preparing the input data_" section in Merewether case study](https://www.seamlesswave.com/Merewether2.html)). 


![Image](/Figures/Fig_7G.jpg)


Flooding occurs from a 260-m wide opening located inside the valley from the southwest side (see the left part in the figure above) where the inflow hydrograph shown in the right part in the figure is applied. This hydrograph has a strong inflow peak occurring over a short duration to propagate throughout the valley until after 30 hours when the water has ponded near the closed boundary at the eastern edge of the domain. 

To set up this test case, a point source boundary condition is required. This type of boundary condition is defined by specifying the inflow at certain locations inside the domain. Since maximum one point source is allowed per computational cell, the number of point sources depend on the resolution of the grid. 

For the Valley flooding test case, the opening for inflow is located along a line extending from point `(x,y) = (232595, 830480)` to `(x,y) = (232785, 830290)`. By opening the DEM file, `ea5-10m.dem`, in QGIS, it can be observed that the line spans 20 cells inside the domain for the 10m-resolution grid. The locations of these 20 cells along with Boundary identifier (`P` for point source), Boundary condition type (`QVAR` for time-varying inflow) and Boundary condition time series name (here named `test5`) must be provided in `.bci` file, as shown by snapshot below.

![image](/Figures/ea5_1.PNG)


If a different grid resolution is to be used, it is necessary to re-check, manually (e.g. using QGIS), which are the cells spanning the inflow opening and list them in `.bci` file.

Since a time-varying inflow is used, the hydrograph defining this inflow must be provided in a `.bdy` file.  The figure below shows a snapshot of `ea5.bdy`, which provides the time series of unit-width discharge (q = Q/B = 3000/200 = 15 square meter per second). Note that since 20 cells are specified as point source, the opening width, B, is 200 m. 

![image](/Figures/ea5_2.PNG)




[back](/LISFLOOD8.0.md)
