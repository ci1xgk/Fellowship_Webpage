# Boundary condition type file (`.bci`)

This file specifies boundary conditions not associated with the channel. There can be any number of boundaries on the edge of the domain or at points within the domain itself. There must not be more than one point source per cell.

The file consists of 5 columns, each containng the following informations:

- Column 1: Boundary identifier taking a value of N, E, S, W, F or P and referring to the north, east, south or west boundaries or F referring to a FREE boundary or P referring to a point source

- Column 2: start of boundary segment (easting or northing in map co-ordinates) for edge boundaries or easting in map co-ordinates for a point source location

- Column 3: End of boundary segment (easting or northing in map co-ordinates) for edge boundaries or northing in map co-ordinates for a point source location

- Column 4: Boundary condition type

- Column 5: Boundary condition value. 

Possible boundary condition types and their associated values are given in Table below:

   | Boundary condition type | Description | Value supplied in column 5 of the `.bci` file |
   | :---         | :---      | :--- |
   | CLOSED   | Zero-flux (default option)     | None  |
   | FREE     | Uniform flow       | None   |
   | HFIX     | Fixed free surface elevation      | Free surface elevation in metres    |
   | HVAR     | Time varying free surface elevation       | Boundary identifier corresponding to data in the user supplied `.bdy` file.   |
   | QFIX     | Fixed flow into domain     | Mass flux per unit width (square meter per second)     |
   | QVAR     | Time varying flow into domain       | Boundary identifier corresponding to data in the user supplied `.bdy` file     |


# TODO: Later decide to put Merwether example here or [here](/Merewether2)

[back](https://www.seamlesswave.com/Merewether1.html)
