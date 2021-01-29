### Valley flooding following a dam failure

This test case is standard to study and compare the capabilities of 2D hydrodynamic solvers for modelling rapidly-propagating flow over a non-smooth valley ([Ayog et al. 2021](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858); [Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). The 10 m x 10 m resolution DEM and the inflow hydrograph are available from the UK Environment Agency. Coarser resolution DEMs can be produced via QGIS. 


![Image](/Figures/Fig_7G.jpg)


Flooding occurs from a 200-m wide opening located inside the valley from the southwest side (left part in the figure) where the inflow hydrograph is applied (right part in the figure). This hydrograph has a strong inflow peak occurring over a short duration to propagate throughout the valley until after 30 hours when the water has ponded near the closed boundary at the eastern edge of the domain. 

To set up this simulation on LISFLOOD-FP8.0, a point source boundary condition is required. This type of boundary condition is defined by specifying the inflow at certain locations inside the domain. Since maximum one point source is allowed per computational cell, the number of point sources depend on the resolution of the grid. 

For the Valley flooding test case, since the grid resolution is 10 m, the 200 m opening inside the valley is specified through a number of 20 cells. If a coarser grid resolution of 50 m is deployed, the opening will be specified through 4 cells. 

The figure below shows an snapshot of the `.bci` file used for Valley flooding test case.

![image](/Figures/ea5_1.PNG)



… MKS … What is this? What the user specificies? File names? The number of points is dependent on the resolution of the grid … right MKS? To be continued_ (unfinished)


_To quantitatively compare and analyse floodplain extents, a post-processing toolkit is available… _ (unfinished)



[back](/LISFLOOD8.0.md)
