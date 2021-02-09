### Valley flooding following a dam failure

This test case is standard to study and compare the capabilities of 2D hydrodynamic solvers for modelling rapidly-propagating flow over a non-smooth valley ([Ayog et al. 2021](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858); [Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). The 10 m x 10 m resolution DEM and the inflow hydrograph are available from the UK Environment Agency. Coarser resolution DEMs can be produced via QGIS ([recall the "Preparing the input data" section in Merewether case study](/Merewether2.md)).


![Image](/Figures/Fig_7G.jpg)


Flooding occurs from an opening located inside the valley from the southwest side (see the left part in the figure above) where a strong inflow peak occurs (see the right part in the figure). The inflow hydrograph is featured by a discharge of 3000 cubic meter per second occuring during 600 to 1200 seconds. This causes a flash flood propagation throughout the valley until after 30 hours when the water has ponded near the closed boundary at the eastern edge of the domain.

To set up this test case, a point source boundary condition is required. This type of boundary condition is defined by specifying the inflow at certain locations inside the domain. Since maximum one point source is allowed per computational cell, the number of point sources depend on the resolution of the grid. 

For this test, the opening for the inflow is located along a line extending from point `(x,y) = (232595, 830480)` to `(x,y) = (232785, 830290)`. By opening the DEM file, namely, `ea5-10m.dem`, in QGIS, it can be observed that the line spans 20 cells inside the domain for the 10m-resolution grid. The locations of these 20 cells along with _Boundary identifier_ (`P` for point source), _Boundary condition type_ (`QVAR` for time-varying inflow) and _Boundary condition time series name_ (here named `test5`) must be provided in `.bci` file, as shown by snapshot below (details in ["Boundary condition type file (.bci)"](https://www.seamlesswave.com/Merewether1-2.html)). 

![image](/Figures/ea5_1.PNG)

If a different grid resolution is to be used, it is necessary to re-check, manually (e.g. using QGIS), which are the cells spanning the length of the inflow opening and list them in `.bci` file. 


When a time-varying inflow is specifified in a `.bci` file, it should be accompanied with a `.bdy` file that first includes the _Boundary condition time series name_ `test5` in the first row. The second row should include the number of time intervals at which the time-varying (6 for this test) and the unit of time (seconds). The rest of the rows lists the time-varying inflow discharge (first column) alongside its time of occurence (second column). The inflow data between these intervals will be linearly interpolated by LISFLOOD. The inflow (discharge) data must be provided in terms of unit-width discharge, q = Q/B. 


The figure below shows a snapshot of the `.bdy` file for this test, named `ea5.bdy`. It provides the time series of unit-width discharge. Since the inflow starts at 300s, zero discharge is specified during the 0 to 300 seconds interval in the time series. The discharge reaches the peak of 3000 cubic meter per second at 600s and stays at the peak until 1200 seconds. This peak discharge is converted to unit-width discharge based on the discrete length of the opening for the 10m-resolution grid, spanning the 20 cells of length 10 m each, i.e. leading to q = Q/B = 3000/(20 x 10) = 15. At 1200s, the inflow decreases to reach zero at 6000 seconds after which a zero discharge is specified.


![image](/Figures/ea5_2.PNG)

[back](/LISFLOOD8.0.md)
