#### Preparing the DG2-related DEM files using `generateDG2DEM` toolkit

As opposed to piecewise-constant data representation used in FV1 or ACC solvers, the DG2 solver represents data as piecewise-planar per element based on an average-coefficient and two slope-coefficients in X and Y directions ([Shaw et al., 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). 

Hence, setting up DG2 on LISFLOOD requires three separate files including the average-coefficient values, the X-directional slope-coefficient values and the Y-directional slope-coefficient values, with the extensions `.dem`, `.dem1x` and `.dem1y`, respectively. 

Files with the the extensions `.dem`, `.dem1x` and `.dem1y` can be generated using the toolkit `generateDG2DEM` (available in the "_preprocess_" folder). The toolkit requires the availability of a raw DEM file in the same folder subject to adding `.raw` to the end of its extension. A demo of how to apply the toolkit is available in [_"Running `generateDG2DEM`"_](MKS).
 

For example, in the Merewether test case, the DEM is renamed to `merewether-0p175m.dem.raw`. After running `generateDG2DEM` toolkit, the files listed below will be generated in the same directory of `merewether-0p175m.dem.raw` file: 

* `merewether-0p175m.dem` which is a copy of the same `merewether-0p175m.dem.raw`, but overwritten to contain the generated average-coefficient values
* `merewether-0p175m.dem1x` which contains the X-directional slope-coefficient values
* `merewether-0p175m.dem1y` which contains the Y-directional slope-coefficient values



[back](/Merewether2.md)
