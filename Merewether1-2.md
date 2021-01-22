#### Boundary condition type file (`.bci`)

This file is where the boundary conditions for the 2D solvers are specified. The 2D computational domain (rectangular) where a 2D solver is applied can have two types of boundary conditions. The first type is a boundary condition located at any of the four edges of a rectangular domain. The second type boundary condition is _"point source"_: it is needed for specifing an inflow located at a point within one computational cell inside the domain (there must not be more than one point source per cell).

The `.bci` file consists of 5 columns, each containng the following items:

- **Column 1.** Boundary identifier taking a value of `N`, `E`, `S`, `W`, `F` or `P`, referring to the north, east, south, west, free or point source boundary 

- **Column 2.** Start of boundary segment for edge boundaries, either easting (X coordinate) or northing (Y coordinate); or, easting (X coordinate) of a point source location

- **Column 3.** End of boundary segment for edge boundaries, either easting (X coordinate) or northing (Y coordinate); or, northing (Y coordinate) of a point source location

- **Column 4.** Boundary condition type (see the "Type" list in the Table below)

- **Column 5.** Boundary condition value or file (see the "Item" list in the Table below)

  | Type | Description | Item for column 5 in a `.bci` file |
   | :---         | :---      | :--- |
   | CLOSED   | Zero-flux (default option)     | None  |
   | FREE     | Uniform flow       | None   |
   | HFIX     | Fixed free surface elevation      | Free surface elevation in metres    |
   | HVAR     | Time varying free surface elevation       | Boundary identifier from data in a user supplied `.bdy` file   |
   | QFIX     | Fixed flow into domain     | Discharge per unit width (square meter per second)     |
   | QVAR     | Time varying flow into domain       | Boundary identifier from data in the user supplied `.bdy` file     |

For Merwether test case, the simulation consists of a steady flow rate of 19.7 cubic meter per second, incoming through a 38 m opening at the south edge of the domain ([see *"Merewether urban flooding"*](/Merewether.md)) and going out through the north edge, while west and east edgees are closed. To set this type of inflow, `HFIX` boundary condition type must be selected. Dividing 19.7 by 38 (length of opening) gives a discharge per unit width of 0.5184 (square meter per second). Accordingly, the `.bci`file for this test case, namely `merewether.bci` will be set as figure below.

![image](/Figures/mer9.png)

[back](/Merewether1.md)
