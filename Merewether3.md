### Running the code, outputs and visualisation

After following the instructions within ["_Compilation_"](/LISFLOOD8.0.md), a LISFLOOD-FP executable file will be obtained. The executable file will have the name `lisflood.exe` on a Windows platform and the name `lisflood` on a Linux-based platform.

For running the `lisflood.exe` of the Merewether test case on Windows, create a directory for the test case, for example named `merewether`, inside the same directory where `lisflood.exe` is located. Then place the input files (available in the `testing\UoS\T04` directory of `LISFLOOD-FP-trunk` repository) inside the `merewether` directory as shown in the figure below.

![image](/Figures/mer12.png)

By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt* window will be opened in the folder, as shown in the figure below.

![image](/Figures/mer13.png)

To run the simulation, the name of the executable must be entered in *Command prompt*, followed by the name of the `.par` file: 
```
..\lisflood.exe merewether-0p175m.par   
```

When the simulation is finished, a series of files, named according to the item `resroot` given in the `.par` file, (i.e. `merewether` for the Merewether test case) will be generated. These files will be located in a directory named by the item `dirroot` in the `.par` file, as shown in the figure below.

![image](/Figures/mer15.png)



For running `lisflood` from a linux-based platform, different instructions must be followed (see the demo on [how to run the Merewether test case on the HPC platform of the University of Sheffied](/run_hpc.md). 


Running on eiher platform will produce the following output files:

- [Mass balance output file (`.mass`)](/Merewether3-1.md) 
  
- [Water depth or free-surface elevation output files (`-xxxx.wd`, `-xxxx.elev`)](/Merewether3-2.md)

- [Velocity output files (`-xxxx.Vx`, `-xxxx.Vy`)](/Merewether3-3.md)

- [Water depth at stage points output file (`.stage`)](/Merewether3-4.md) 

- [Velocity at stage points output file (`.velocity`)](/Merewether3-5.md) 

- [Maximum water depth (`.max`) and maximum free-surface elevation (`.mxe`) output files](/Merewether3-6.md)

- [Time of initial inundation (`.inittm`), time of maximum depth (`.maxtm`) and total time of inundation (`.totaltm`) output files](/Merewether3-7.md)

The 2D output raster files can be viewed in QGIS, in the same manner explained in [*"Viewing the DEM data on QGIS"*](/Merewether2-1.md). The text output files, i.e. `.mass`, `.stage` or `.velocity`, can be visualized in any spreadsheet software like MS Excel.



[back](/Merewether.md)
