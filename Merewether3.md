### Running the code, outputs and visualisation

To run the simulations, instructions are available in [*"Running LISFLOOD"*](). An example is given for running the Merewether test case on windows. To do so, copy paste the LISFLOOD executable file, namely `lisflood.exe`, to the same folder as the input files. The figure below shows the file list that should be in the current directory.

![image](/Figures/mer12.png)

By clicking on the *location bar* of the Windows Explorer, then typing `cmd` and pressing *Enter*, the *Command Prompt Window* will be opened in the folder, as shown in the figure below.

![image](/Figures/mer13.png)

To run the simulation, the name of executable must be entered in *Command prompt*, followed by the name of the `.par` file: 
```
lisflood.exe merewether-0p175m.par   
```

When the simulation is finished, a series of files named according to the keyword `resroot` given in the `.par` file, (i.e. `merewether` for the Merewether test case). These files will be generated in a directory named by the keyword `dirroot` in the `.par` file, as shown in the figure below.

![image](/Figures/mer15.png)

The output files are described below:

- [Mass balance output file (`.mass`)](/Merewether3-1.md) 
  
- [Water depth or water surface elevation output files (`-xxxx.wd`, `-xxxx.elev`)](/Merewether3-2.md)

- [Velocity output files (`-xxxx.Vx`, `-xxxx.Vy`)](/Merewether3-3.md)

- [Water depth at stage points output file (`.stage`)](/Merewether3-4.md) 

- [Velocity at stage points output file (`.velocity`)](/Merewether3-5.md) 

- [Maximum water surface elevation (`.mxe`) and maximum water depth (`.max`) output files](/Merewether3-6.md)

- [Time of initial inundation (`.inittm`), time of maximum depth (`.maxtm`) and total time of inundation (`.totaltm`) output files]()



[back](/Merewether.md)
