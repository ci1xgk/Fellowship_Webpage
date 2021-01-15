# Input files and their format
For a typical simulation using either of ACC, FV1 or DG2 solvers, data is input to the model using following file types. Users should note that the file extensions are not mandatory, comments can only be used in the parameter file (.par) and all items are case sensitive. 

1. Parameter file (`.par`)
   This file contains the information necessary to run the simulation including file names and locations and the main model and run control parameters. The following general    principles apply:
   * All items in the file are case sensitive.
   * Items not recognised are ignored rather than generating an error message.
   * The code expects one item per line only.
   * If a keyword does not appear the model uses the default value specified in the code and (usually) does not generate an error message.
   * The order given below is not fixed.
   * To comment out a line place a # in the first character space.

   The following table lists keywords related to ACC, FV1 and DG2 solvers that are specified in the parameter file. These define parameter values, tell the model to read in specified files, turn model options on and off or tell the model to output specific files. The full list of parameters is provided in [LISFLOOD user manual](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view). 


   | Item name `input` | Description | Applicable solver |
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
   
2. Boundary condition type file (`.bci`)
   

   
  



