#### Modifying the resolution of the DEM on QGIS

 QGIS can also be used to decrease (upscale) the resolution of the DEM data. For Merewether test case, the original DEM file is at a 0.01 m resolution but another file with a resolution of 0.175 m was produced based on the following procedure:  
-	Load the original DEM following the steps in [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md).
- Right click on the DEM file name in *Layers* window and select *Export - > Save as …*
-	In *Save Raster Layer as …* window, change both the *Horizontal* and *Vertical* resolution to 0.175, and check that the boundaries, or *Extent*, of the 2D domain accommodates the new resolution (for example, *West*: 382232.55, *East*: 382354.35, *North*: 6354664.775, *South*: 6354280.3). Enter a name for the new layer in *File Name* section, namely `merewether-0p175m`, and then click *OK* (see figure below). The newly created layer will be shown in *Layers* window.

![image](/Figures/mer5.png)

- Select the new layer in *Layers* window and go to *Raster - > Conversion - > Translate (Convert Format)...*
-	In *Translate (Convert Format)* window, set *Assign a specified nodata value to output bands* as -9999 and click on *Save to File…* (see figure below).

![image](/Figures/mer6.png)

-	Save the file with `.asc` extension, e.g. `merewether-0p175m.asc`. 
-	Once saved, change the extension of file from `.asc` to `.dem`. 


Hence, `merewether-0p175m.dem` will be the upscaled raw DEM file that will be used to set up LISFLOOD simulations. 


[back](/Merewether2.md)
