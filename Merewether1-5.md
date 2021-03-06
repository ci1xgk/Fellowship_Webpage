#### Input file including the positions where water depth and velocity histories are to be extracted (`.stage`)

This file specifies the locations of points (in X and Y coordinates) where LISFLOOD-FP generates a time series output of water depth and velocities. 

For each location specified in this file, water depth (in metre) and velocities (in metre per second) values will be written in two files with the extensions of `.stage` and `.velocity`, respectively. 

These data will be written at each massint interval (of time in sec.) specified in the `.par` file. The format of a `.stage` input file is as follows:

- **Line 1.** Number of points at which water depth and velocity output time series are required

- **Line 2.** X and Y coordinate of 1st point

- **Line 3.** X and Y coordinate of 2nd point

- ...

- **Line n.** X and Y coordinate of ith point


Generating the time series output for the water depth is activated by including the `stagefile` item in the `.par` file, followed by the name of the `.stage` file to be read. For further activating time series output for the velocities, the extra item of `voutput_stage` must be included as well.

The figure below shows a screenshot of the `.stage` file used for the Merewether case study, namely `merewether.stage`, which tells LISFLOOD-FP to write time series output of the water depth values at 4 points inside the domain.

![image](/Figures/mer10.png)



[back](/Merewether1.md)
