#### Preparing the DG2-related DEM files using `generateDG2DEM` toolkit

The DG2 formulation relies on piecewise-planar representation of data (as opposed to piecewise-constant in FV1 or ACC solvers), in a way that the DEM is composed of an average value plus two slope values in X and Y directions ([Ayog et al., 2021](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858)). LISFLOOD requires each of these three components to be saved in a separate file, with extensions `.dem`, `.dem.1x` and `.dem.1y`. These files can be generated using the toolkit `generateDG2DEM`. To do this, the user should add `.raw` to the extension name of the related DEM files. For example in Merewether test case, the DEM is renamed to  `merewether-0p175m.dem.raw`. 

By running `generateDG2DEM` toolkit, following the explanations in [_"Running `generateDG2DEM`"_](), the files listed below will be generated in the same directory of `merewether-0p175m.dem.raw` file:

1.	`merewether-0p175m.dem`: This is basically a copy of the same `merewether-0p175m.dem.raw`, but overwritten to contain the average DEM vaues for DG2.
2.	`merewether-0p175m.dem.1x`: contains the X-direction slope values of the DEM data.
3.	`merewether-0p175m.dem.1y`: contains the Y-direction slope values of the DEM data.


[back](/Merewether2.md)
