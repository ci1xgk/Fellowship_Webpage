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

![image](/Figures/mer14.png)

The output files are described below:

- **Mass balance output file (`.mass`).** This file gives the following information and is written at the interval specified by the keyword `massint` in the `.par` file:
  - Column 1: `Time`. The time in seconds at which the data was saved.
  - Column 2: `Tstep`. Time step specified by the user (initial time step in the adaptive model) in seconds
  - Column 3: `MinTstep`. Minimum time step used so far during the simulation in seconds
  - Column 4: `NumTsteps`. Number of time steps since the start of the simulation.
  - Column 5: `Area`. Area inundated in m2..
  - Column 6: Vol. Volume of water in the domain in m3.
  - Column 7: Qin. Inflow discharge in m3s-1.
  - Column 8: Hds. Water depth at the downstream exit of the model domain in meters.
  - Column 9: Qout. Calculated outflow discharge at the downstream exit of the model domain in m3s-1.
  - Column 10: Qerror. Volume error per second in m3s-1.
  - Column 11: Verror. Volume error per mass interval (massint variable in the parameter file) m3.
  - Column 12: Rain-Inf+Evap. Cumulative effect of infiltration, evaporation and rainfall over the simulation in 103 m3.
  

[back](/Merewether.md)
