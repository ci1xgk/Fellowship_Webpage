#### Water depth or free-surface elevation output files (`-xxxx.wd`, `-xxxx.elev`)

In these files, a 2D grid of water depth (`.wd`) and free-surface elevation (`.elev`) values (in metre) will be written. The data will be written with the same [Esri ASCII raster format](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) of the DEM input file at each save interval, `saveint`, as specified in the `.par` file. 

Based on this naming convention, `xxxx` is the `saveint` number. For instance in the example of the Merewether test case, since `saveint` is 10 seconds, `merewether-0002.wd` will contain the water depth output at t = 20 seconds. Note that to disable the generation of `.elev` files, one should include the item `.elevoff` in the `.par` file. In case of the DG2 solver, two extra files named `-xxxx.wd1x`, `-xxxx.wd1y` or `-xxxx.elev1x`, `-xxxx.elev1y` will be generated that contain the X- and Y- directional slope coefficient values of water depth and free-surface elevation, respectively. 


[back](/Merewether3.md)
