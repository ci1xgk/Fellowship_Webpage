#### Preparing the initial conditions files for ACC/FV1 on QGIS

The Merewether test case has pond by its end towards to the downstream boundary. The pond is associated with a constant free-surface water elevation of h + z = 17.8 m, which needs to be considered as an initial condition. LISFLOOD expects to read such an initial condition as a raster file, which is made of either free-surface water elevation (h + z) data or water depth (h) data, with the extension of `.start` (see also [_"Input files and their format"_](https://www.seamlesswave.com/Merewether1-6)).  

To generate raster file for the initial free-surface water elevation, the following steps should be applied in QGIS:

-	Load the Merewether DEM raster file, named `merewether-0p175m.dem` in QGIS (explained in [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md)).
-	Go to menu *Raster - > Raster Calculator*
-	In *Raster Calculator* window, enter the following expression in *Raster Calculator Expression*:
```
(merewether-0p175m@1 <= 17.8) * 17.8 + (merewether-0p175m@1 > 17.8) * merewether-0p175m@1
``` 
- Enter a name, e.g. `temp`, for the new layer in the *Output layer* section (see figure below). This puts a value of 17.8 for the free-surface water elevation (h + z) in all areas where the topography (z) value is below 17.8, while the other portions remain unchanged as they are dry areas.

![image](/Figures/mer7.png)

- To convert the newly created `temp` layer into a raster format readable by LISFLOOD, select it in the *Layers* window and go to menu *Raster - > Conversion - > Translate (Convert Format)*.
-	In the *Translate (Convert Format)* window, set *Assign a specified nodata value to output bands* as -9999 and click on *Save to File…*
-	Save the file with `.asc` extension, for example under the same name introduced before, for convenience, i.e. `merewether-0p175m.asc`. 
-	Once saved, change the extension of file from `.asc` to `.start`. 

After applying these steps, the free-surface water elevation raster file, `merewether-0p175m.start` can be read by LISFLOOD (see also [_"Input files and their format"_](https://www.seamlesswave.com/Merewether1-6)).  


---


Generating the initial water depth (h) raster file follows the same steps above, whereby the following expression should be entered in the *Raster Calculator* window:
```
(merewether-0p175m@1 > 17.8) * 0 + (merewether-0p175m@1 <= 17.8) * (17.8 - merewether-0p175m@1)
```
This puts zero values for the water depth (h) in areas where topography is higher than 17.8 (dry areas) and retains the depth value as it otherwise.





[back](/Merewether2.md)
