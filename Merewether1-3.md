#### Time varying boundary conditions file (`.bdy`)

This file is needed when selecting `QVAR` or `HVAR` in the `.bci` file. In this case, a timeseries hydrograph needs to be loaded at either a boundary segment (an edge) or a point source. The timeseries hydrograph is either free-surface elevation or unit-width discharge information, aimed to specify time varying boundary conditions.  

The `.bdy` file is used to specify such a time varying boundary condition and has the following format:

- Line 1. Comment line, ignored by LISFLOOD-FP

- Line 2. Boundary identifier (this should be consistent with notation supplied in the `.bci` file)

- Line 3. Number of time points at which boundary information is given followed by a keyword for the time units used (either `days`, `hours` or `seconds`)

- Line 4. Value1 Time1

- Line 5. Value2 Time2

- ...

- Line i. Valuei Timei


Note that `Valuei` is the value of the relevant quantity for the given boundary type. For `HVAR` boundaries `Valuei` is a water surface elevation in metres. ??? However, the units of `Valuei` for `QVAR` boundaries depend on whether the given boundary identifier is specified in the `.bci` file. ?? MKS: WHY TAKING ABOUT QVAR HERE AND LATER? For a `QVAR` boundary specified in the `.bci` file, `Valuei` is given as unit-width discharge with units of square meter per second. ?? NEEDS CLARIFICATION??

In case studies [_"3. Valley flooding following a dam failure"_](https://www.seamlesswave.com/Carlistle_flooding.html) or [_"4. Carlistle 2005, urban flooding"_](https://www.seamlesswave.com/Carlistle_flooding.html) demos are provided of how to set up `.bdy` file for the `.bci` file. 

[back](/Merewether1.md)
