#### Boundary condition type file (`.bci`)

This file is where the boundary conditions for the 2D solvers are specified. The 2D computational domain (rectangular) where a 2D solver is applied can have two types of boundary conditions. The first type is a boundary condition located at any of four edges of a rectangular domain. The second type boundary condition is _"point source"_: it is needed for specifing an inflow located at a point within one computational cell inside the domain (there must not be more than one point source per cell).

The `.bci` file consists of 5 columns, each containng the following items:

- Column 1: Boundary identifier taking a value of N, E, S, W, F or P, referring to the north, east, south, west, free or point source boundary 

- Column 2: Start of boundary segment, easting (x) or northing (y) in map co-ordinates, for edge boundaries or easting in map co-ordinates for a point source location

- Column 3: End of boundary segment (easting or northing in map co-ordinates) for edge boundaries or northing in map co-ordinates for a point source location

- Column 4: Boundary condition type (see Table below)

- Column 5: Boundary condition value (see Table below)

  | BC type | Description | Item in column 5 within `.bci` file |
   | :---         | :---      | :--- |
   | CLOSED   | Zero-flux (default option)     | None  |
   | FREE     | Uniform flow       | None   |
   | HFIX     | Fixed free surface elevation      | Free surface elevation in metres    |
   | HVAR     | Time varying free surface elevation       | Boundary identifier corresponding to data in the user supplied `.bdy` file.   |
   | QFIX     | Fixed flow into domain     | Mass flux per unit width (square meter per second)     |
   | QVAR     | Time varying flow into domain       | Boundary identifier corresponding to data in the user supplied `.bdy` file     |


# TODO: Later decide to put Merwether example here or [here](/Merewether2)

[back](/Merewether1.md)
