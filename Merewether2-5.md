#### Preparing the DG2-related Initial condition files using `generateDG2start` toolkit

In the same manner as the DEM data, setting up the initial condition for DG2 simulations requires three separate files for either water depth (h) or water surface elevation (h + z), depending on the type of initialisation. These files include the average-coefficient values, the X-directional slope-coefficient values and the Y-directional slope-coefficient values, with extensions of `.start`, `.start1x` and `.start1y`, respectively. 

Files with the the extensions `.start`, `.start1x` and `.start1y` can be generated using the toolkit `generateDG2start` (available in the "preprocess" directory). The toolkit requires the availability of a raw initial condition file in the same folder subject to adding `.raw` to the end of its extension. A demo of how to apply the toolkit is available in [*"Running generateDG2start"*]().


For example, in the Merewether test case, the initial condition file is renamed to  `merewether-0p175m.start.raw`. After running `generateDG2start` toolkit, the files listed below will be generated in the same directory of `merewether-0p175m.start.raw` file:

-	`merewether-0p175m.start` which is a copy of the same `merewether-0p175m.start.raw`, but overwritten to contain the generated average-coefficient values
-	`merewether-0p175m.start1x` which contains the X-directional slope-coefficient values
-	`merewether-0p175m.start1y` which contains the Y-directional slope-coefficient values


[back](/Merewether2.md)
