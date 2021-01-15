# Boundary condition type file (`.bci`)

This file specifies boundary conditions not associated with the channel. There can be any number of boundaries on the edge of the domain or at points within the domain itself. There must not be more than one point source per cell.

The file consists of 5 columns, each containng the following informations:

- Column 1: Boundary identifier taking a value of N, E, S, W, F or P and referring to the north, east, south or west boundaries or F referring to a sub-grid channel internal point FREE boundary or P referring to a point source
