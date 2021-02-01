### Valley flooding following a dam failure

This test case is standard to study and compare the capabilities of 2D hydrodynamic solvers for modelling rapidly-propagating flow over a non-smooth valley ([Ayog et al. 2021](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858); [Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). The 10 m x 10 m resolution DEM and the inflow hydrograph are available from the UK Environment Agency. Coarser resolution DEMs can be produced via QGIS ([recall the "Preparing the input data" section in Merewether case study](/Merewether2.md)).


![Image](/Figures/Fig_7G.jpg)


Flooding occurs from an opening located inside the valley from the southwest side (see the left part in the figure above) where the inflow hydrograph shown in the right part in the figure is applied. This hydrograph is a strong inflow starting at 300 seconds and linearly increase to reach a peak of 3000 cubic meter per second at 600 seconds. The inflow stays at its peak up to 1200 seconds and then linearly decreases to return to zero at 6000 seconds. This causes a flash flood propagation throughout the valley until after 30 hours when the water has ponded near the closed boundary at the eastern edge of the domain. 

To set up this test case, a point source boundary condition is required. This type of boundary condition is defined by specifying the inflow at certain locations inside the domain. Since maximum one point source is allowed per computational cell, the number of point sources depend on the resolution of the grid. 

For the Valley flooding test case, the opening for inflow is located along a line extending from point `(x,y) = (232595, 830480)` to `(x,y) = (232785, 830290)`. By opening the DEM file, namely, `ea5-10m.dem`, in QGIS, it can be observed that the line spans 20 cells inside the domain for the 10m-resolution grid. The locations of these 20 cells along with _Boundary identifier_ (`P` for point source), _Boundary condition type_ (`QVAR` for time-varying inflow) and _Boundary condition time series name_ (here named `test5`) must be provided in `.bci` file, as shown by snapshot below (details in ["Boundary condition type file (.bci)"](https://www.seamlesswave.com/Merewether1-2.html)). 

![image](/Figures/ea5_1.PNG)

If a different grid resolution is to be used, it is necessary to re-check, manually (e.g. using QGIS), which are the cells spanning the length of the inflow opening and list them in `.bci` file. 


When a time-varying inflow is specifified in a `.bdy` file, it should be accompanied with a `.bdy` file that also includes the _Boundary condition time series name_ "test5". In the `.bdy` file, the number of time steps at which the time-varying inflow data is avaiable should be first specified (6 for this case), followed by the list of time to inflow data. Listing of the discharge data should be done based on the unit-width discharge, q = Q/B. 

= 3000/(20 x 10) = 15 square meter per second. Figure below shows a snapshot of `ea5.bdy`, which provides the time series of unit-width discharge, starting from t = 0s, reaching the peak at t = 600s and attenuating at t = 1200 s. 

![image](/Figures/ea5_2.PNG)


_To quantitatively compare and analyse floodplain extents, a post-processing toolkit is available… _ (unfinished)



[back](/LISFLOOD8.0.md)
