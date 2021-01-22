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
   | HFIX     | Fixed free-surface elevation      | Free-surface elevation in metres (h+z)   |
   | HVAR     | Time-varying free-surface elevation       | Boundary identifier from data in a user-supplied `.bdy` file   |
   | QFIX     | Fixed flow into domain     | Discharge per unit width in square meter per second (q=Q/B)    |
   | QVAR     | Time-varying flow into domain       | Boundary identifier from data in the user-supplied `.bdy` file     |

For the Merwether test case, the simulation consists of a steady flow rate of Q = 19.7 cubic meter per second, inflowing through an opening at the south edge of the domain with a width B = 38 m ([see *"Merewether urban flooding"*](/Merewether.md)) and leaving through the north edge. The west and east edges of the domain are closed by solid walls.

To set a steady inflow, i.e. specify a unit-width discharge of q = Q/B = 0.5184 in the 5th column, `QFIX` boundary condition type must be selected in the 4rd column. As the inflow located in the south edge (constant Y) the first column has the letter S. The inflow occurs from an opening starting at X = 382300.00 and ending at X = 382338.0, which should be selected in 2nd and 3rd columns.  

To set a free outflow through the northern edge of the domain (constant Y), `FREE` must be selected in the 4th column after selecting N in the 1st column; whereas, the 2nd and 3rd columns has the X coordinates of the north edge. The 5th column can be left blank in this case. 

As closed boundary conditions are set by default, no specifications for the east and west edges are required.     

Hence, the `.bci`file for the Merwether test case, named `merewether.bci`, will be as shown in the snapshot below:

![image](/Figures/mer9.png)

[back](/Merewether1.md)
