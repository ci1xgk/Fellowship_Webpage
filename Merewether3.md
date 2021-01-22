### Running the code, outputs and visualization

To run the simulations, user must follow the instructions in section [*"Running LISFLOOD"*](). As an example for running the Merewether test case on windows, user needs to copy paste the LISFLOOD executable file, namely `lisflood.exe`, to the same folder as the input files. Figure below shows the working directory.

![image](/Figures/mer12.png)

By clicking on the *location bar* of Windows Explorer, then entering `cmd` and press *Enter* key, the *Command Prompt Window* will be opened in the folder, as figure below.

![image](/Figures/mer13.png)

To run the simulation, the name of executable must be entered in Command prompt, followed by the name of `.par` file: 
```
lisflood.exe merewether-0p175m.par   
```

When the simulation is finished, a series of files will be generated in a directory named by keyword `dirroot` in `.par` file, as shown below.

![image](/Figures/mer14.png)

[back](/Merewether.md)
