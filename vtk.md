#### Non-uniform grid output files (`-xxxx.vtk`)

These files are generated by the non-uniform grid acceleration solver (non-uniform ACC) and involve topography, spatially-varied Manning parameter (if available), 
water depth (in meters) and velocity (in meters per second) on the no-uniform grids at each save interval, `saveint`, as specified in the `.par` file.
The files are written in [VTK format](https://vtk.org/wp-content/uploads/2015/04/file-formats.pdf). Based on this naming convention, `xxxx` is the `saveint` number.

The 2D VTK files can be viewed in [ParaView](https://www.paraview.org/), as explained in [*"Viewing the VTK data on ParaView"*](/paraview.md).

[back](/Merewether3.md)