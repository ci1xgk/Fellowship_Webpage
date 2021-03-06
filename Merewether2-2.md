#### Modifying the resolution of the DEM on QGIS

QGIS can also be used to decrease (upscale) the resolution of the DEM data. For the Merewether test case, the original DEM file was at a 0.01 m x 0.01 m resolution but another file with a resolution of 0.175 m x 0.175 m is produced based on the following procedure:  
-	Load the original DEM following the steps in [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md).
- Right-click on the DEM file name in *Layers* window and select *Export - > Save as …*
-	In *Save Raster Layer as …* window, change both the *Horizontal* and *Vertical* resolution to 0.175, and check that the boundaries, or *Extent*, of the 2D domain accommodates the new resolution (in this example it must be: *West*: 382232.55, *East*: 382354.35, *North*: 6354664.775, *South*: 6354280.3). Enter a name for the new layer in the *File Name* section, namely `merewether-0p175m`, and then click *OK* (see figure below). The newly created layer will be shown in the *Layers* window.

![image](/Figures/mer5.png)

- Select the new layer in the *Layers* window and go to *Raster - > Conversion - > Translate (Convert Format)...*
-	In the *Translate (Convert Format)* window, set *Assign a specified nodata value to output bands* as -9999 and click on *Save to File…* (see figure below).

![image](/Figures/mer6.png)

-	Save the file with `.asc` extension, e.g. `merewether-0p175m.asc`. 
-	Once saved, change the extension of the file from `.asc` to `.dem`. 


Hence, `merewether-0p175m.dem` will be the upscaled raw DEM file that will be used to set up LISFLOOD-FP simulations.


[back](/Merewether2.md)
