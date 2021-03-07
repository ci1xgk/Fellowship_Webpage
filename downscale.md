#### Downscaling coarse-resolution DG2 flood maps

As opposed to piecewise-constant data representation used in first-order methods like FV1, the DG2 solver represents data as piecewise-planar per element defined by three coefficients: an average-coefficient and two slope-coefficients in X and Y directions ([Shaw et al., 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)). When the model is run using the DG2 solver, even though the data are inherently considered as piecewise-planar, the output water depth maps are only generated based on the average-coefficients. This might lead to crude flood maps when using the DG2 solver on coarse grids.  

To improve this crudeness, a post-processing toolkit, named `DG2downscale`, is provided in the `postprocess` directory of `LISFLOOD-FP-trunk` repository, to artificially increase the resolution of the generated flood maps in a process called downscaling.

The left panel in the figure below shows a schematic view of the piecewise-planar representation of the DG2 data (like water depth) over a coarse cell. If four subdivisions are assumed on this coarse cell, using the piecewise-planar representation, it is possible to evaluate the data on the centres of each subdivision. These evaluated data, form the piecewise-constant representation on one level finer resolution, are shown in the right panel in the figure below.

![Image](/Figures/downscale2.svg)

The toolkit is obtained after compiling the LISFLOOD-FP code, following the instructions within [*"Compilation"*](/LISFLOOD8.0.md). It will be generated as an executable file with the name `DG2downscale.exe` on a Windows platform and the name `DG2downscale` on a Linux-based platform, in the same directory where the LISFLOOD-FP executable is generated.

The toolkit requires the availability of the three coarse DG2 water depth or free-surface elevation files: the average-coefficient files `.wd` or `.elev` and the slope-coefficient files `.wd1x` and `.wd1y` or `.elev1x` and `.elev1y`. These files must be placed in the same directory where `DG2downscale` is generated.

In this directory, clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, will open the *Command Prompt* Window. To run the toolkit, the name of the executable must be entered in the *Command prompt*, followed by the name of the coarse DG2 average-coefficient file, i.e. `.wd` or `.elev`:

```
DG2downscale.exe file_name.wd
```
or
```
DG2downscale.exe file_name.elev
```

Note that the slope-coefficient files will be read by the code automatically. After running the `DG2downscale` toolkit, the downscaled water depth or free-surface elevation [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) will be generated within the same directory. This file will be saved with the same name as the coarse DG2 average-coefficient file but with the added extension of `DScaled` (i.e. for example `file_name.wdDScaled` or `file_name.elevDScaled`).

[back](/Desmond_Eden2015.md)
