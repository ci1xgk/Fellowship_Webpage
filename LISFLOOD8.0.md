
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

#### GitHub for University of Sheffield users 
To get access into the most up to date version version on GitHub, communcate with Jeff from Bristol or with MKS form ou side. It is a cross-platform, so the same download is usable on windows and linux. 


### Compilation   
The downloaded versin is cross-platform... and can be done on personal computers on windows or linux, or via the HPC of the university of Sheffield (link).  

#### On a personal computer
MKS to descrive a process + comments on VS19.  

#### On the University of Sheffield HPC 
link to the HPC, SharC and Bessemer, etc. 


### Case studies 
Why each case study? To demonstrate what?

#### [Merewether urban flooding around building with pieres](./Merewether.md)
One this one, we are clear that GPU solvers are the best option: 0.175m ==> millions of cells. No point of investigation CPU solvers. 
Velocitiy prediction and small eddy capturing. FV1-GPU, ACC-GPU and DG2-GPU. Water levels + velocities + eddies. Other metrics like relevance index.

#### Enviroment Agency Test 5  
Why this case study? 
Underway (MKS management): 10 m, 20 m, 40 m and 80 m for a comparision between ACC-CPU/GPU, FV1-CPU/GPU, DG2-CPU/GPU. Coarse-DG2 does not need GPU! Better velocity prediction. Compare floodplains with metrics H, F and C at t = 3 hours. Downscaling capability. 

#### Carlisle flooding 2005
Why this case study? Should be different than EA5.  
Underway (MKS management): 5 m, 10 m, 20 m and 40 m for a comparision between ACC-CPU/GPU, FV1-CPU/GPU, DG2-CPU/GPU. Coarse-DG2 does not need GPU! Better velocity prediction. Compare floodplains with metrics H, F and C at t = 3 hours. Downscaling capability.

#### Strom Desmond's flooding on the Eden catchement  
Thin water layer and different initial condition 


### Video tutorials  
[1. Download and compile](https://github.com/ci1xgk/Fellowship_Webpage/blob/master/VideoTutorials/Download_and_compile)   
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

