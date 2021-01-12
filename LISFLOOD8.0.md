
## LISFLOOD-FP8.0

The LISFLOOD-FP hydrodynamic model developed by the [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) already includes a local inertia, or ‘gravity wave’, solver, LISFLOOD-ACC, and a diffusive wave, ‘or zero-inertia’, solver, LISFLOOD-ATS. The ACC solver is widely used to simulate floods with gradually-varying, subcritical flow over sufficiently rough surfaces with Manning’s coefficient of at least 0.03. It has a version with CPU-specific optimisations and enhanced with a subgrid channel model ([Neal et al. 2012](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2012WR012514), [2018](https://www.sciencedirect.com/science/article/pii/S1364815217307478)). Please contact [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) for any advice related to the ACC solver.   

### New DG2/FV1 solvers on multi-core CPU 
LISFLOOD-FP 8.0 includes second-order discontinuous Galerkin (DG2) and first-order finite volume (FV1) solvers of the two-dimensional shallow water equations for modelling a wide range of flows, including rapidly-propagating, supercritical flows, shock waves, or flows over very smooth surfaces. The new DG2/FV1 solvers are purely two-dimensional and parallelised for the multi-core CPU architecture, but do not integrate with the subgrid channel model nor with the CPU-specific optimisations ([Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)).

### New GPU solvers  
The new DG2/FV1 solvers are also parallelised within a new Nvidia GPU architecture and can run existing LISFLOOD-FP modelling scenarios without modification. The [user manual of LISFLOOD-FP](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view?usp=sharing) has been updated to further offer guidance about how to parametrise the code to run on the GPU, in particular for the DG2/FV1 solvers. Users interested in knowing more about the mathematical/computational background of the DG2/FV1 solvers and how to run them on LISFLOOD-FP 8.0 are encouraged to start their readings from [Shaw et al. (2021)](https://gmd.copernicus.org/preprints/gmd-2020-340/). 

The rest of this page is devoted to instructing new users on how to download, install and run the code of LISFLOOD-FP 8.0, in particular to use the new hydrodynamic solvers, DG2/FV1. Guidance is provided on preprocessing DG2-related DEM and initial condition files (with slope coefficients), and on posprocessing coarse DG2 output files to downscale them into a floodplain map at finer resolutions. The documented instructions are also covered in video tutorials and through realistic case studies to help identify the capabilities of the different solvers. 


### Download  

#### Zenodo for external users 
We mainly point people to the version on Zenodo where you need to fill a form. Refer to the paper of Shaw et al. (2019). 

#### [University of Sheffield users](./UoS_HPC.md) 


### Compilation   
The downloaded versin is cross-platform... and can be done on personal computers on windows or linux, or via the HPC of the university of Sheffield (link).  

#### On a personal computer
MKS to descrive a process + comments on VS19.  

#### On the University of Sheffield HPC 
link to the HPC, SharC and Bessemer, etc. 


### Case studies 
A selection of case studies are presented to instruct users on how to set up and run the DG2/FV1 solvers for LISFLOOD-FP 8.0. These studies are also useful to gain insights into the potential utility of the DG2 solver. 

#### [1. Pre-processing the initial conditions for DG2 including slope coefficients.](./Merewether.md)
The demonstration is provided for the Mereweher urban flooding across building with pieres [(Smith et al. 2017)](https://www.tandfonline.com/doi/abs/10.1080/15715124.2016.1193510). This test case entails loading an inflow boundary condition and pre-processing initially wet flow conditions with DG2-related slope coefficients for both the initial water level and the raw DEM file.    

#### [ 2. Activation of the local slope limiting for DG2.](./25_Blocks.md) 
By default, when including “dg2” in the “.par” file of LISFLOOD-FP (see the [user manual](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view?usp=sharing)), it considers running the DG2 solver without local slope limiting. This is an appropriate choice to more efficiently and reliably simulate shockless flood flows featured in a wide range of flood modelling applications [(Ayog et al. 2021)](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858). For simulations involving either fine-scale spatial flow features or strong flow discontinuities, there is the option to activate local slope limiting by simply further typing “limiteslopes” alongside “dg2” in the “.par” file. The need for activating local slope limiting for DG2 is demonstrated over a complex dam-break wave interacting with an idealised urban district [(Soares-Frazao and Zech 2008)](https://www.tandfonline.com/doi/abs/10.3826/jhr.2008.3164).

#### [Enviroment Agency Test 5](./EnvAcy5.md)  
#### [Carlisle flooding 2005](./Carlistle_flooding.md)
#### [Eden catchement flooding 2015](./Desmond_Eden2015.md)  


### Video tutorials  
[1. Download and compile](./VideoTutorials/Download_and_compile)   
[2. Introduction to QGIS](The necessary needed to cope with lisflood)
[3. Pre-processing DEM with slope coefficents for the DG2 solver]
[4. Running across different platform](Enviroment Agency Test 5)
[5. Running a test with a point-source inflow](Carlisle 2005 - laoding )
[6. Running with a test with a boundary-source inflow and initially wet areas](Merewether)
[7. Running with a test driven by rainfall](Eden)
[8. Post-processing outputs](Enviroment Agency Test 5, hydrogprahs, floodplain and downscaling-MKS-toolkit, metrics)


### License 


### References 




[back](./)

