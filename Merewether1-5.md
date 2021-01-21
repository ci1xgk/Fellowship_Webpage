#### Water depth and velocity output data file (`.stage`)

This file specifies the locations of points (in X and Y coordinates) where the model generates a time series output of water depth and velocity. 
For each location specified in this file, the water depth (in meter) and velocity (in meter per second) values will be written in two files with the extensions of `.stage` and `.velocity`, respectively. These data will be written at each `massint` interval specified in `.par` file. 

The format of the file is as follows:

- Line 1. Number of points at which water depth and velocity output time series are required 

- Line 2. X and Y coordinate of 1st point

- Line 3. X and Y coordinate of 2nd point

- ...

- Line i. X and Y coordinate of nth point


Generating the water depth output is activated by including the `stagefile` keyword in the `.par` file, followed by the name of `.stage` file to be read. For activating the generation of velocity output data, the extra keyword of `voutput_stage` must be included as well. 

Figure below shows an snapshot of the `.stage` file used for the Merewether case study, namely `merewether.stage`, which tells LISFLOOD to write water depth walues at 4 points inside the domain.

![image](/Figures/mer10.png)

[back](/Merewether1.md)
