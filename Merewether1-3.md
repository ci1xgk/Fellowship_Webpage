#### Time varying boundary conditions file (`.bdy`)

This file is needed when selecting `QVAR` or `HVAR` in the `.bci` file. In this case, a hydrograph timeseries needs to be loaded at either a boundary segment (an edge) or a _point source_ (in specifield cells located inside the computational domain). The hydrograph timeseries is either free-surface elevation or unit-width discharge data, aimed to specify time varying-boundary conditions.  

The `.bdy` file is used to specify such a time-varying boundary condition and has the following format:

- **Line 1.** Comment line, ignored by LISFLOOD-FP

- **Line 2.** Boundary identifier (this should be consistent with notation supplied in the `.bci` file)

- **Line 3.** Number of time points at which boundary information is given followed by a keyword for the time units used (either `days`, `hours` or `seconds`)

- **Line 4.** Value1 Time1

- **Line 5.** Value2 Time2

- ...

- **Line i.** Valuei Timei


Note that `Valuei` is the value of the relevant quantity for the given boundary type. That is, for `HVAR` boundary types, `Valuei` is a free-surface water elevation in metres; whereas, ror `QVAR` boundart types, `Valuei` is given as unit-width discharge with units of square meter per second.

In case studies [_"3. Valley flooding following a dam failure"_](/EnvAcy5.md) or [_"4. Carlistle 2005, urban flooding"_](/Carlistle_flooding.md) examples are provided on how to set up `.bdy` file to specify time varying-boundary conditions


[back](/Merewether1.md)
