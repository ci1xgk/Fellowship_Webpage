#### Preparing the initial conditions files for ACC/FV1 on QGIS

The Merewether test case has a constant water level of h + z = 17.8 m at the downstream boundary which needs to be set as the initial condition. LISFLOOD can read the initial condition as a raster file of either water level (h + z) or water depth (h), with the extension of `.start` as previously explained in [_"Input files and their format
"_](https://www.seamlesswave.com/Merewether1-6). To generate the initial water level (h + z) raster file using QGIS, the following steps should be applied:

-	Load the Merewether DEM raster file, named `merewether-0p175m.dem` in the QGIS, as explained in [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md).
-	Go to menu *Raster - > Raster Calculator*
-	In *Raster Calculator* window, enter the following expression in *Raster Calculator Expression*:
```
(merewether-0p175m@1 <= 17.8) * 17.8 + (merewether-0p175m@1 > 17.8) * merewether-0p175m@1
``` 
- Enter a name, here e.g. `temp`, for the new layer in the *Output layer* section (see figure below). This puts a value of 17.8 in all areas where topography is less than 17.8 and retains the rest, generating the final initial water level map.

![image](/Figures/mer7.png)

- To convert the newly created `temp` layer into a raster format readable by LISFLOOD-FP, select it in the *Layers* window and go to menu *Raster - > Conversion - > Translate (Convert Format)*.
-	In the *Translate (Convert Format)* window, set *Assign a specified nodata value to output bands* as -9999 and click on *Save to File…*
-	Save the file with `.asc` extension, for example under the same name introduced before, for convenience, i.e. `merewether-0p175m.asc`. 
-	Once saved, change the extension of file from `.asc` to `.start`. 

Generating the initial water depth (h) raster file follows the same steps above but in *Raster Calculator* window, the following expression should be entered:
```
(merewether-0p175m@1 > 17.8) * 0 + (merewether-0p175m@1 <= 17.8) * (17.8 - merewether-0p175m@1)
```
which puts zero values in areas where topography is higher than 17.8 (dry areas) and retains the depth at the rest of the domain, generating the final initial water depth map.



[back](/Merewether2.md)
