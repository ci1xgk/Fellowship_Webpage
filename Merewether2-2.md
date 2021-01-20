#### Modifying the resolution of the DEM on QGIS

The QGIS also provides a way to decrease (upscale) the resolution of the DEM data based on the modeling requirements. For Merewether test case, the original 0.01 m resolution of the DEM was decreased to 0.175 m according to the following procedure:  
-	Load the original DEM following the steps in [_"Viewing the DEM data on QGIS"_](/Merewether2-1.md).
- Right click on the DEM file name in *Layers* window and select *Export - > Save as …*
-	In *Save Raster Layer as …* window, change both the *Horizontal* and *Vertical* Resolution to 0.175, and check that the boundaries, or *Extent*, of the domain accommodates the new resolution (for example, *West*: 382232.55, *East*: 382354.35, *North*: 6354664.775, *South*: 6354280.3). Enter a name for the new layer in *File Name* section, namely `merewether-0p175m`, and then click *OK* (See figure below). The newly created layer will be shown in *Layers* window.

![image](/Figures/mer5.png)

[back](/Merewether2.md)
