
## LISFLOOD-FP8.0 with DG2 and GPU solvers

The LISFLOOD-FP hydrodynamic model developed by the [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) already includes a local inertia, or ‘gravity wave’, solver, LISFLOOD-ACC, and a diffusive wave, ‘or zero-inertia’, solver, LISFLOOD-ATS. The ACC solver is widely used to simulate floods with gradually-varying, subcritical flow over sufficiently rough surfaces with Manning’s coefficient of at least 0.03. It has a version with CPU-specific optimisations and enhanced with a subgrid channel model ([Neal et al. 2012](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2012WR012514), [2018](https://www.sciencedirect.com/science/article/pii/S1364815217307478)). Please contact [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) for any advice related to the ACC solver.   

### New DG2/FV1 solvers on multi-core CPU 
LISFLOOD-FP 8.0 includes second-order discontinuous Galerkin (DG2) and first-order finite volume (FV1) solvers of the two-dimensional shallow water equations for modelling a wide range of flows, including rapidly-propagating, supercritical flows, shock waves, or flows over very smooth surfaces. The new DG2/FV1 solvers are purely two-dimensional and parallelised for the multi-core CPU architecture, but do not integrate with the subgrid channel model nor with the CPU-specific optimisations ([Shaw et al. 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)).


### New GPU solvers  
The new DG2/FV1 solvers are also parallelised within a new Nvidia GPU architecture and can run existing LISFLOOD-FP modelling scenarios without modification. The [user manual of LISFLOOD-FP](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view?usp=sharing) has been updated to further offer guidance about how to parametrise the code to run on the GPU, in particular for the DG2/FV1 solvers. Users interested in knowing more about the mathematical/computational background of the DG2/FV1 solvers and how to run them on LISFLOOD-FP 8.0 are encouraged to start their readings from [Shaw et al. (2021)](https://gmd.copernicus.org/preprints/gmd-2020-340/). 

The rest of this page is devoted to instructing new users on how to download, install and run the code of LISFLOOD-FP 8.0, in particular to use the new hydrodynamic solvers, DG2/FV1. Guidance is provided on preprocessing DG2-related DEM and initial condition files (with slope coefficients), and on posprocessing coarse DG2 output files to downscale them into a floodplain map at finer resolutions. The documented instructions are also covered in video tutorials and through realistic case studies. 

***

### Download  

#### Zenodo for external users 
We mainly point people to the version on Zenodo where you need to fill a form. Refer to the paper of Shaw et al. (2019). 


#### [University of Sheffield users](./UoS_HPC.md) 


***


### Compilation   
The downloaded version is cross-platform and can be compiled on Windows or Linux. University of Sheffield users can also compile and run the code on the [HPC Computing Facilities provide by IT Services](https://www.sheffield.ac.uk/it-services/research/hpc-facilities). The compilation process is explained for each platform as followed.

- [Windows](/compile_win.md)
  

- [Linux](/compile_lin.md)


- [The University of Sheffield HPC](/compile_hpc.md) 

***


### Case studies 
Case studies are presented to instruct users how to set up and run the DG2/FV1/ACC solvers for LISFLOOD-FP8.0. These studies are also useful to identify the most optimal DG2 configuration for the targetted application. 


#### [1. Merewether, urban flooding](./Merewether.md)
This case study [(Smith et al. 2017)](https://www.tandfonline.com/doi/abs/10.1080/15715124.2016.1193510) is used to explain how to set up and run LISFLOOD-FP for beginners using any of the DG2, FV1 and ACC two-dimensional hydrodynamic solvers on the CPU or the GPU.  


#### [2. Dam-break wave over an urban area](./25_Blocks.md) 
This case study [(Soares-Frazao and Zech 2008)](https://www.tandfonline.com/doi/abs/10.3826/jhr.2008.3164) is aimed to demonstrate when local slope limiting with DG2 should be applied. 


#### [3. Valley flooding following a dam failure](./EnvAcy5.md)  
This case study [(Néelz and Pender 2013)](https://consult.environment-agency.gov.uk/engagement/bostonbarriertwao/results/appendix-6---neelz--s.---pender--g.--2013--benchmarking-the-latest-generation-of-2d-hydraulic-modelling-packages.-bristol_environment-agency.pdf) is aimed to demonstrate how to handle an inflow boundary condition located inside the computational area, at source point(s). This test is also used to demonstrate a new post-processing toolkit for producing metrics to quantify floodplain extent prediction capabilities when comparing the outcomes predicted by different hydrodynamic solvers.


#### [4. Carlistle 2005, urban flooding](./Carlistle_flooding.md)
This case study [(Horritt et al. 2010)](https://www.icevirtuallibrary.com/doi/pdf/10.1680/wama.2010.163.6.273) is particularly aimed to demonstrate how to handle multiple inflow boundary conditions from different source point(s).


#### [5. Eden 2015, fluvial flooding](./Desmond_Eden2015.md)  
This case study [(Xia et al. 2019)](https://www.sciencedirect.com/science/article/abs/pii/S030917081930243X) involves overland flow driven by spatially- and temporally-varying rainfall data over a 2500 kilometer square catchment. It is aimed to demonstrate how to use the new rain-on-grid capabilities in LISFLOOD-FP8.0. This test is also used to demonstrate a new post-processing toolkit for downscaling coarse-resolution DG2 flood maps.

***

### Video tutorials  
[1. Download and compile](./VideoTutorials/Download_and_compile)   
[2. Introduction to QGIS](The necessary needed to cope with lisflood)
[3. Pre-processing DEM with slope coefficents for the DG2 solver]
[4. Running across different platform](Enviroment Agency Test 5)
[5. Running a test with a point-source inflow](Carlisle 2005 - laoding )
[6. Running with a test with a boundary-source inflow and initially wet areas](Merewether)
[7. Running with a test driven by rainfall](Eden)
[8. Post-processing outputs](Enviroment Agency Test 5, hydrogprahs, floodplain and downscaling-MKS-toolkit, metrics)

***

### License 

***

### References 




[back](/Developments.md)

