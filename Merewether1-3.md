# Time varying boundary conditions file (`.bdy`)

This file is used to specify time varying boundary conditions (keywords `QVAR` or `HVAR` in the or `.bci` file) associated with a boundary segment or point source. For each time varying boundary condition the format for the file is as follows:

- Line 1: Comment line, ignored by LISFLOOD-FP.

- Line 2: Boundary identifier (this should be consistent with notation supplied in the `.bci` file).

- Line 3: Number of time points at which boundary information is given followed by a keyword for the time units used (either `days`, `hours` or `seconds`).

- Line 4: Value1 Time1

- Line 5: Value2 Time2

- ...

- Line i: Valuei Timei

Where `Valuei` is the value of the relevant quantity for the given boundary type. 

**Notes:**
- For all `HVAR` boundaries `Valuei` is a water surface elevation in metres. However, the units of `Valuei` for `QVAR` boundaries depend on whether the given boundary identifier is specified in the `.bci` file. 
- For a `QVAR` boundary specified in the `.bci` file `Valuei` is given as mass flux per unit width with units of square meter per second.


[back](https://www.seamlesswave.com/Merewether1.html)
