### Running the code, outputs and visualisation

After following the instructions within the ["_Compilation_"](/LISFLOOD8.0.md), a LISFLOOD executable file will be obtained. The executable file will have the name `lisflood.exe` on a Windows platform and the name `lisflood` on a linux-based platform. 

For running the `lisflood.exe` of the Merewether test case on windows, bring `lisflood.exe` to the same folder where the input files are located. The figure below shows the file list that should be in the current directory.

![image](/Figures/mer12.png)

By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt Window* will be opened in the folder, as shown in the figure below.

![image](/Figures/mer13.png)

To run the simulation, the name of executable must be entered in *Command prompt*, followed by the name of the `.par` file: 
```
lisflood.exe merewether-0p175m.par   
```

When the simulation is finished, a series of files named according to the keyword `resroot` given in the `.par` file, (i.e. `merewether` for the Merewether test case). These files will be generated in a directory named by the keyword `dirroot` in the `.par` file, as shown in the figure below.

![image](/Figures/mer15.png)



For running `lisflood` from a linux-based platform, different instructions should be followed. See the demo on how to run the Merewether test case on the HPC platform of the University of Sheffied [Name of section](link). 


Running on eiher platforms will produce the following output files:

- [Mass balance output file (`.mass`)](/Merewether3-1.md) 
  
- [Water depth or water surface elevation output files (`-xxxx.wd`, `-xxxx.elev`)](/Merewether3-2.md)

- [Velocity output files (`-xxxx.Vx`, `-xxxx.Vy`)](/Merewether3-3.md)

- [Water depth at stage points output file (`.stage`)](/Merewether3-4.md) 

- [Velocity at stage points output file (`.velocity`)](/Merewether3-5.md) 

- [Maximum water depth (`.max`) and maximum water surface elevation (`.mxe`) output files](/Merewether3-6.md)

- [Time of initial inundation (`.inittm`), time of maximum depth (`.maxtm`) and total time of inundation (`.totaltm`) output files]()

The 2D output rastar maps, can be viewed in QGIS, in the same manner explained in [*"Viewing the DEM data on QGIS"*](/Merewether2-1.md). The text output files, i.e. `.mass`, `.stage` or `.velocity`, can be visualized in any spreadsheet software like MS Excel.



[back](/Merewether.md)
