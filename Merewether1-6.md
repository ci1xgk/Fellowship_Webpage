#### Velocity output data file (`.gauge`)

This file specifies the locations of points (in X and Y coordinates) where the model generates a time series output of velocity. 
For each location specified in this file, the velocity values (in meter per second) will be written in a file with the extension of `.velocity`, at each `massint` interval specified in `.par` file. 

The format of the file is as follows:

- Line 1. Number of points at which velocity output time series are required 

- Line 2. X and Y coordinate of 1st point

- Line 3. X and Y coordinate of 2nd point

- ...

- Line i. X and Y coordinate of nth point


Generating the velocity output is activated by including the keyword `voutput_stage`, and the keyword `gaugefile` followed by the name of `.gauge` file to be read, in the `.par` file. An example of how to set up the `.gauge` file is demonstrated for the Merewether case study in [_"Preparing the input data"_](/Merewether2.md).


[back](/Merewether1.md)
