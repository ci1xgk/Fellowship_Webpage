# Parameter file (`.par`)

This is the starting file that a user should refer to for setting up and running any simulation. Inside this file, the user should enter parameters including the names and location of files of relevance for the case study under condideration. While putting entries or items in the `.par` file, the following rules apply:  

   * Only the items listed in [LISFLOOD user manual](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view) should be typed. Any other item will be ignored. 
   
   * There should only be one item per line. Items can be entered in no particualr order. To comment out a line place add a `#` in the first character space.

   * If a keyword does not appear, the model uses the default value specified wihtout generating an error message.
   
To run the 2D ACC, FV1 and DG2 solvers, the following list of items need to be specified in the `.par` file. 


   | Item name `input` | Description | Solver |
   | :---         | :---      | :--- |
   | DEMfile `filename`   | Digital Elevation Model file name     | All solvers    |
   | resroot `name`     | Root for naming of results files       | All solvers    |
   | dirroot `foldername`     | Relative or absolute path for the directory where results files are to be placed       | All solvers     |
   | saveint `value`     | Interval in seconds at which results files are saved       | All solvers    |
   | massint `value`     | Interval in seconds at which the .mass file is written     | All solvers     |
   | sim_time `value`     | Total length of the simulation (sec.)       | All solvers     |
   | initial_tstep `value`     | Initial guess for the optimum time step and maximum possible time step (sec.)      | All solvers     |
   | bcifile `filename`     | Name of file identifying floodplain boundary condition types       | All solvers    |
   | bdyfile `filename`     | Name of file containing information on time varying floodplain boundary conditions       | All solvers     |
   | fpfric `value`     | Manning’s n value for floodplain if spatially uniform       | All solvers      |
   | manningfile `filename`     | Name of file containing a grid of floodplain n values       | All solvers     |
   | acceleration        | Selects the ACC floodplain solver       | ACC      |
   | fv1     | Selects the FV1 floodplain solver       | FV1      |
   | dg2     | Selects the DG2 floodplain solver       | DG2      |
   | cuda    | Run the acceleration, FV1 or DG2 solver on a GPU.       | All solvers      |
   | dynamicrainfile `filename`   | Name of spatially- and temporally-varying rainfall data (NetCDF)     | All solvers    |
   | nodata_elevation `value`     | Terrain elevation value that replaces NODATA values in the DEMfile      | All solvers    |
   | drain_nodata     | Enable to remove water in cells with NODATA elevation       | All solvers    |
   | startfile `filename`     | Name of initial conditions file with water depth in ARC ascii raster format     | All solvers    |
   | startelev `filename`     | Similar to startfile but with water surface elevation rather than depth    | All solvers    |
   | limitslopes     | Enable the DG2 minmod slope limiter      | DG2   |
   | krivodonovathresh     | Control the localisation of the DG2 slope limiter (Default: 10.0)       | DG2   |
   
   
   [back](/Merewether1.md)
