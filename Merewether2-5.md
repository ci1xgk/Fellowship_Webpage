#### Preparing the DG2-related Initial condition files using `generateDG2start` toolkit

In this same manner as the DEM data, the initial condition for DG2 simulations should be provided in three files with extensions of `.start`, `.start1x` and `.start1y`, for either water depth (h) or water elevation (h + z) initialization. These files can be generated using the `generateDG2start` toolkit. To do this, the user should add `.raw` to the extension name of the related initial condition. For example in Merewether test case, the initial condition file is renamed to  `merewether-0p175m.start.raw`. 

By running `generateDG2start` toolkit , following the explanations in [_"Running `generateDG2start`"_](), the files listed below will be generated in the same directory of `merewether-0p175m.start.raw` file: 
1.	`merewether-0p175m.start`: This is basically a copy of the same `merewether-0p175m.start.raw`, but overwritten to contain the average values of water depth or water elevation (depending on the type of initialization) for DG2.
2.	`merewether-0p175m.start1x`: contains the X-direction slope values of water depth or water elevation.
3.	`merewether-0p175m.start1y`: contains the y-direction slope values of water depth or water elevation.


[back](/Merewether2.md)
