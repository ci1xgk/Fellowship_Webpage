### Running the code, outputs and visualization

To run the simulations, user must follow the instructions in section [*"Running LISFLOOD"*](). As an example for running the Merewether test case on windows, user needs to copy paste the LISFLOOD executable file, namely `lisflood.exe`, to the same folder as the input files. Figure below shows the working directory.

![image](/Figures/mer12.png)

By clicking on the *location bar* of Windows Explorer, then entering `cmd` and press *Enter* key, the *Command Prompt Window* will be opened in the folder, as figure below.

![image](/Figures/mer13.png)

To run the simulation, the name of executable must be entered in *Command prompt*, followed by the name of `.par` file: 
```
lisflood.exe merewether-0p175m.par   
```

When the simulation is finished, a series of files named according to `resroot` convention given in `.par` file (here namely `merewether`) will be generated in a directory named by keyword `dirroot` in `.par` file, as shown below.

![image](/Figures/mer15.png)

The output files are described below:

- [Mass balance output file (`.mass`)](/Merewether3-1) 
  
- **Water depth or water surface elevation output files (`-xxxx.wd`, `-xxxx.elev`).** In these files a grid of water depths (`.wd`) and water surface elevations (`.elev`) values (in meter) will be written in the same ASCII raster format of the DEM input file, with the same resolution and extent, at each save interval, `saveint`, specified in `.par` file. In this naming convention `xxxx` is the `saveint` number. For instance in the example of Merewether test case, since `saveint` is 10 seconds, `merewether-0002.wd` will contain the water depth output at t = 20 seconds. It should be reminded that generation of `.elev` files will be suppressed by including the keyword `.elevoff` in the `.par` file. In case of the DG2 solver two extra files named `-xxxx.wd1x`, `-xxxx.wd1y` or `-xxxx.elev1x`, `-xxxx.elev1y` will be generated that contain the X and Y direction slope coeficients of water depth and water surface elevation, respectively.

- **Velocity output files (`-xxxx.Vx`, `-xxxx.Vy`).** In these files a grid of velocity values in X (`.Vx`) and Y (`.Vy`) direction (in meter per second) will be written in the same ASCII raster format of the DEM input file, with the same resolution and extent, at each save interval, `saveint`, specified in `.par` file. In this naming convention `xxxx` is the `saveint` number.

- **Water depth at stage points output file (`.stage`).** This text file contains the water depth values (in meter) for each stage point specified in the `.stage` input file. The data will be written at each time interval specified by `massint` in the `.par` file.

- **Velocity at stage points output file (`.velocity`).** This text file contains the velocity magnitude (in meter per second) for each stage point specified in the `.stage` input file. The data will be written at each time interval specified by `massint` in the `.par` file.

[back](/Merewether.md)
