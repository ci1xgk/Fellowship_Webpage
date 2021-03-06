#### Preparing the initial conditions files for ACC/FV1 on QGIS

The Merewether test case has a pond at its end near the downstream boundary. The pond is associated with a constant free-surface elevation of h + z = 17.8 m, which needs to be considered as an initial condition. LISFLOOD-FP expects to read such an initial condition as an [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm), which is made of either free-surface elevation (h + z) or water depth (h) data, with the extension of `.start` (recall [_"Input files and their format"_](https://www.seamlesswave.com/Merewether1-6)).  

To generate the raster file for the initial free-surface elevation, the following steps must be applied in QGIS:

-	Load the Merewether DEM raster file, named `merewether-0p175m.dem` in QGIS (recall [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md)).
-	Go to the menu *Raster - > Raster Calculator*
-	In the *Raster Calculator* window, enter the following expression in *Raster Calculator Expression*:
```
(merewether-0p175m@1 <= 17.8) * 17.8 + (merewether-0p175m@1 > 17.8) * merewether-0p175m@1
``` 
- Enter a name, e.g. `temp`, for the new layer in the *Output layer* section (see figure below). This puts a value of 17.8 for the free-surface elevation (h + z) in all areas where the topography (z) value is below 17.8, while the other portions remain unchanged as they are dry areas.

![image](/Figures/mer7.png)

- To convert the newly created `temp` layer into a raster format readable by LISFLOOD-FP, select it in the *Layers* window and go to menu *Raster - > Conversion - > Translate (Convert Format)*.
-	In the *Translate (Convert Format)* window, set *Assign a specified nodata value to output bands* as -9999 and click on *Save to File…*
-	Save the file with `.asc` extension, for example under the same name introduced before, for convenience, i.e. `merewether-0p175m.asc`. 
-	Once saved, change the extension of file from `.asc` to `.start`. 

After applying these steps, the free-surface elevation raster file, `merewether-0p175m.start` can be read by LISFLOOD-FP (recall [_"Input files and their format"_](https://www.seamlesswave.com/Merewether1-6)).  


---


Generating the initial water depth (h) raster file follows the same steps above, whereby the following expression should be entered in the *Raster Calculator* window:
```
(merewether-0p175m@1 > 17.8) * 0 + (merewether-0p175m@1 <= 17.8) * (17.8 - merewether-0p175m@1)
```
This puts zero values for the water depth (h) in areas where the topography is higher than 17.8 (dry areas) and retains the depth value as it is, otherwise.





[back](/Merewether2.md)
