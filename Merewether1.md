# Input files and their format
For a typical simulation using either of ACC, FV1 or DG2 solvers, data is input to the model using following file types. Users should note that the file extensions are not mandatory, comments can only be used in the parameter file (.par) and all items are case sensitive. Further details are provided in [LISFLOOD user manual](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view). 

1. Parameter file (`.par`)
   This file contains the information necessary to run the simulation including file names and locations and the main model and run control parameters. The following general    principles apply:
   * All items in the file are case sensitive.
   * Items not recognised are ignored rather than generating an error message.
   * The code expects one item per line only.
   * If a keyword does not appear the model uses the default value specified in the code and (usually) does not generate an error message.
   * The order given below is not fixed.
   * To comment out a line place a # in the first character space.

   The following tables list keywords that are specified in the parameter file. These define parameter values, tell the model to read in specified files, turn model options on and off or tell the model to output specific files.


   | Item name `input` | Description | Applicable solver |
   | :---         | :---      | :--- |
   | DEMfile `filename`   | Digital Elevation Model file name     | ACC, FV1, DG2    |
   | resroot `name`     | Root for naming of results files       | ACC, FV1, DG2     |
   | dirroot `foldername`     | Relative or absolute path for the directory where results files are to be placed       | ACC, FV1, DG2      |
   | saveint `value`     | Interval in seconds at which results files are saved       | ACC, FV1, DG2     |
   | massint `value`     | Interval in seconds at which the .mass file is written     | ACC, FV1, DG2     |
   | sim_time `value`     | Total length of the simulation (sec.)       | ACC, FV1, DG2      |
   | initial_tstep `value`     | Initial guess for the optimum time step and maximum possible time step (sec.)      | ACC, FV1, DG2      |
   | bcifile `filename`     | Name of file identifying floodplain boundary condition types       | ACC, FV1, DG2     |
   | bdyfile `filename`     | Name of file containing information on time varying floodplain boundary conditions       | ACC, FV1, DG2     |
   | fpfric `value`     | Manning’s n value for floodplain if spatially uniform       | ACC, FV1, DG2      |
   | manningfile `filename`     | Name of file containing a grid of floodplain n values       | ACC, FV1, DG2      |
   | acceleration        | Selects the ACC floodplain solver       | ACC      |
   | fv1     | Selects the FV1 floodplain solver       | FV1      |
   | dg2     | Selects the DG2 floodplain solver       | DG2      |
   | cuda    | Run the acceleration, FV1 or DG2 solver on a GPU.       | ACC, FV1, DG2      |
   
   
   Notes: 
     * If both fpfric and manningfile are specified, fpfric will not be used.
     * The file containing Manning's n values should be an ARC ascii raster format with the same dimensions and resolution as the DEMfile. 


What MKS needs to explain? 
`.par`
`.start`
`.dem`

