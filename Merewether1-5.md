#### Water depth output data file (`.stage`)

This file specifies the locations of points (in X and Y coordinates) where the model generates a time series output of water depth. 
For each location specified in this file, the water depth values will be written in a file with the extension of `.stage`, at each `massint` interval specified in `.par` file. 

The format of the file is as follows:

- Line 1. Number of points at which water depth output time series are required 

- Line 2. X and Y coordinate of 1st point

- Line 3. X and Y coordinate of 2nd point

- ...

- Line i. X and Y coordinate of nth point


Generating the water depth output is activated by including the `stagefile` keyword in the `.par` file, followed by the name of `.stage` file to be read. An example of how to set up the `.stage` file is demonstrated for the Merewether case study in [_"Preparing the input data"_](/Merewether2.md).


[back](/Merewether1.md)
