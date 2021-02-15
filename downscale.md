#### Downscaling coarse-resolution DG2 flood maps

As opposed to piecewise-constant data representation used in first order methods like, FV1, the DG2 solver represents data as piecewise-planar per element defined by three coefficients: an average-coefficient and two slope-coefficients in X and Y directions ([Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). When the model is run using the DG2 solver, eventhough inside the model the data are considered as piece-wise planar, the output flood maps are only generated based on the average coefficients. This might lead to very crude flood maps when using the model on coarse grids.  

To improve this crudeness to some extent, a toolkit is provided in the post-processing directory that artificially increase the resolution of the generated flood maps in a process called **downscaling**.

The left panel in the figure below, shows an schematic view of the planar represantion of the DG2-generated data (like water depth or water surface elevation) over a coarse cell. If the cell is devided into four subcells, using this planar representation, it is possible to evaluate the data on the centers of each 4 subcells. Thi   

![Image](/Figures/downscale2.svg)

[back](/Desmond_Eden2015.md)
