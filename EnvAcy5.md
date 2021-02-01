### Valley flooding following a dam failure

This test case is standard to study and compare the capabilities of 2D hydrodynamic solvers for modelling rapidly-propagating flow over a non-smooth valley ([Ayog et al. 2021](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858); [Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). The 10 m x 10 m resolution DEM and the inflow hydrograph are available from the UK Environment Agency. Coarser resolution DEMs can be produced via QGIS. 


![Image](/Figures/Fig_7G.jpg)


Flooding occurs from an opening located inside the valley from the southwest side (left part in the figure) where the inflow hydrograph is applied (right part in the figure). This hydrograph has a strong inflow peak of 3000 cubic meter per second occurring over a short duration to propagate throughout the valley until after 30 hours when the water has ponded near the closed boundary at the eastern edge of the domain. 

To set up this test case, a point source boundary condition is required. This type of boundary condition is defined by specifying the inflow at certain locations inside the domain. Since maximum one point source is allowed per computational cell, the number of point sources depend on the resolution of the grid. 

For the Valley flooding test case, the opening for inflow is located along a line extending from point `(x,y) = (232595, 830480)` to `(x,y) = (232785, 830290)`. By opening the DEM file, namely, `ea5-10m.dem`, in QGIS, it can be observed that the line passes 20 cells inside the domain. The locations of these 20 cells along with Boundary identifier (`P` for point source), Boundary condition type (`QVAR` for time-varying inflow) and Boundary condition time series name (here named `test5`) must be provided in `.bci` file, as shown by snapshot below.

![image](/Figures/ea5_1.PNG)

It should be noted tht if different grid resolution is to be used, the user is required to manually check (e.g. using QGIS) which cells are paassed by the inflow opening and list them in `.bci` file. 

Since time-varying inflow is used, the respective hydrograph must be provided in a `.bdy` file. Since 20 cells are specified as point source, the peak discharge of 3000 cubic meter per second will be converted to unit-width discharge as q = Q/B = 3000/(20 x 10) = 15 square meter per second. Figure below shows a snapshot of `ea5.bdy`, which provides the time series of unit-width discharge, starting from t = 0s, reaching the peak at t = 600s and attenuating at t = 1200 s. 

![image](/Figures/ea5_2.PNG)


_To quantitatively compare and analyse floodplain extents, a post-processing toolkit is available… _ (unfinished)



[back](/LISFLOOD8.0.md)
