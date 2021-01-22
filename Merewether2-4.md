#### Preparing the DG2-related DEM files using `generateDG2DEM` toolkit

As opposed to piecewise-constant data representation used in FV1 or ACC solvers, the DG2 solver represents data as piecewise-planar per element based on an average-coefficient and two slope-coefficients in X and Y directions ([Shaw et al., 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). Hence, setting up DG2 on LISFLOOD requires three separate files including the average-coefficient values, the X-directional slope-coefficient values and the Y-directional slope-coefficient values, with the extensions `.dem`, `.dem1x` and `.dem1y`, respectively. These files can be generated using the toolkit `generateDG2DEM` (available in the "_preprocess_" folder). To apply `generateDG2DEM`, to a raw DEM file, the `.raw` extension need to be added to the file name. 

For example in Merewether test case, the DEM is renamed to `merewether-0p175m.dem.raw`. After running `generateDG2DEM` toolkit, following the explanations in [_"Running `generateDG2DEM`"_](), the files listed below will be generated in the same directory of `merewether-0p175m.dem.raw` file:

* `merewether-0p175m.dem`: This is basically a copy of the same `merewether-0p175m.dem.raw`, but overwritten to contain the average DEM vaues for DG2.
* `merewether-0p175m.dem1x`: contains the X-directional slope-coefficient values of the DEM data.
* `merewether-0p175m.dem1y`: contains the Y-directional slope-coefficient values of the DEM data.


[back](/Merewether2.md)
