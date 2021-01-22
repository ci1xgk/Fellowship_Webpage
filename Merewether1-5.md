#### Water depth and velocity output data file (`.stage`)

This file specifies the locations of points (in X and Y coordinates) where the model generates a time series output of water depth and velocities. 

For each location specified in this file, water depth (in meter) and velocities (in meter per second) values will be written in two files with the extensions of `.stage` and `.velocity`, respectively. These data will be written at each `massint` interval (of time in sec.) specified in `.par` file. The format of such output file(s) is as follows:

- **Line 1.** Number of points at which water depth and velocity output time series are required 

- **Line 2.** X and Y coordinate of 1st point

- **Line 3.** X and Y coordinate of 2nd point

- ...

- **Line i.** X and Y coordinate of ith point


Generating the time series output for the water depth is activated by including the `stagefile` _item name_ in the `.par` file, followed by the name of the `.stage` file to be read. For further activating time series output for the velocities, the extra keyword of `voutput_stage` must be included too. 

Figure below shows an snapshot of the `.stage` file used for the Merewether case study, namely `merewether.stage`, which tells the model to write time series output of water depth values at 4 points inside the domain (the points are listed in the `.stage` file).

![image](/Figures/mer10.png)



[back](/Merewether1.md)
