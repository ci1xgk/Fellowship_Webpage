#### Boundary condition type file (`.bci`)

This file is where the boundary conditions for the 2D solvers are specified. The 2D (rectangular) computational domain where a 2D solver is applied can have two types of boundary conditions.

The first type is a boundary condition located at any of the four edges of the rectangular domain. The second type is the so-called *"point source"*, which should be aimed for specifying an inflow located at a point within one computational cell inside the domain (there must not be more than one point source per cell).

The `.bci` file consists of 5 columns, each containing the following items:

- **Column 1.** Boundary identifier taking a value of `N`, `E`, `S`, `W` or `P`, referring to the north, east, south, west or point source boundary 

- **Column 2.** Start of boundary segment for edge boundaries, either easting (X coordinate) or northing (Y coordinate); or, easting (X coordinate) of a point source location

- **Column 3.** End of boundary segment for edge boundaries, either easting (X coordinate) or northing (Y coordinate); or, northing (Y coordinate) of a point source location

- **Column 4.** Boundary condition type (see the "Type" list in the Table below)

- **Column 5.** Boundary condition value or time series name (see the "Item" list in the Table below)

  | Type | Description | Item for column 5 in a `.bci` file |
   | :---         | :---      | :--- |
   | CLOSED   | Zero-flux (default option)     | None  |
   | FREE     | Uniform flow       | None   |
   | HFIX     | Fixed free-surface elevation      | Free-surface elevation in metres (h+z)   |
   | HVAR     | Time-varying free-surface elevation       | Boundary identifier from a user-supplied data file (e.g. a hydrogprah) with a `.bdy` extension |
   | QFIX     | Fixed flow into domain     | Discharge per unit width in square meter per second (q=Q/B)    |
   | QVAR     | Time-varying flow into domain       | Boundary identifier from a user-supplied data file (e.g. a hydrogprah) with a `.bdy` extension     |

For the Merwether test case, the simulation consists of a steady inflow rate of Q = 19.7 cubic meter per second, inflowing through an opening at the south edge along a width of B = 38 m (see [*"Merewether urban flooding"*](/Merewether.md)). The flow leaves the 2D domain through the north edge, whereas the west and east edges of the domain are closed by solid walls.

To set the steady inflow (i.e. specify a unit-width discharge of q = Q/B = 0.5184 in the 5th column), the `QFIX` boundary condition type must be selected in the 4th column. As the inflow is located in the south edge (constant Y) the first column has the letter `S`. The inflow occurs from an opening starting at X = 382300.00 and ending at X = 382338.0, which should be selected in the 2nd and 3rd columns.  

To set the free outflow through the north edge (constant Y), `FREE` must be selected in the 4th column after selecting `N` in the 1st column, while the 2nd and 3rd columns should have the X coordinates of the north edge. The 5th column can be left blank in this case. 

Since `closed` boundary conditions are set by default, no specifications for the east and west edges are required.   

Hence, the `.bci` file for the Merwether test case, named `merewether.bci`, will be as shown in the screenshot below:

![image](/Figures/mer9.png)

[back](/Merewether1.md)
