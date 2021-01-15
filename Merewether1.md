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


   | Item name `input` | Description | Applicable model solver |
   | :---         | :---      | :--- |
   | DEMfile `filename`   | Digital Elevation Model file name     | All solvers    |
   | resroot `name`     | Root for naming of results files       | All solvers      |
   | dirroot `foldername`     | Relative or absolute path for the directory where results files are to be placed.       | All solvers      |
   | resroot `name`     | Root for naming of results files       | All solvers      |
   | resroot `name`     | Root for naming of results files       | All solvers      |
   | resroot `name`     | Root for naming of results files       | All solvers      |
   | resroot `name`     | Root for naming of results files       | All solvers      |


What MKS needs to explain? 
`.par`
`.start`
`.dem`

