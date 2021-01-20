#### Preparing the DG2-related Initial condition files using `generateDG2start` toolkit

In this same manner as the DEM data, the initial condition for DG2 simulations should be provided in three files with extensions of `.start`, `.start.1x` and `.start.1y`, for either water depth (h) or water elevation (h + z) initialization. These files can be generated using the function generateDG2init. To do this, the user should add .raw to the extension name of the related initial condition. For example in this case, the initial condition file is renamed to  merewether-0p175m.start.raw. 

By running generateDG2init function (see section with link) the following files will be generated in the same directory: 
4.	merewether-0p175m.start: This is basically a copy of the same merewether-0p175m.start.raw, but overwritten to contain the average flow coefficients (h or h + z, depending on the type of initialization) for DG2.
5.	merewether-0p175m.start.1x: contains the x-direction slope values of initial condition.
6.	merewether-0p175m.start.1y: contains the y-direction slope values of initial condition.


[back](/Merewether2.md)
