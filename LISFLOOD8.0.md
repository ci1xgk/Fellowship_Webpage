
## LISFLOOD-FP8.2 

The LISFLOOD-FP is a raster-based hydrodynamic model that has been developed by the [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/). LISFLOOD-FP has undergone extensive development since conception and includes a collection of numerical schemes implemented to solve a variety of mathematical approximations of the 2D shallow water equations of different complexity. The local inertia solver, known as the ACC solver, is widely used to simulate floods with gradually-varying, subcritical flow over sufficiently rough surfaces with Manning’s coefficient of at least 0.03. It has a version with CPU-specific optimisations and enhanced with a subgrid channel model ([Neal et al., 2012](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2012WR012514), [2018](https://www.sciencedirect.com/science/article/pii/S1364815217307478)).



, ranging from a simple diffusive wave model to shock-capturing Godunov-type schemes based on Finite Volume (FV) and discontinuous Galerkin (DG) methods which solve the full shallow-water equations.





already includes a solver with local inertia, or ‘gravity wave’ formulation, known as the ACC solver, and a solver with the diffusive wave, or ‘zero-inertia’ formulation, known as the ATS solver. The ACC solver is widely used to simulate floods with gradually-varying, subcritical flow over sufficiently rough surfaces with Manning’s coefficient of at least 0.03. It has a version with CPU-specific optimisations and enhanced with a subgrid channel model ([Neal et al., 2012](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2012WR012514), [2018](https://www.sciencedirect.com/science/article/pii/S1364815217307478)). Please contact [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) for any advice related to the ACC solver.   

%### New DG2/FV1 solvers on multi-core CPU 
The new version, LISFLOOD-FP 8.0, includes second-order discontinuous Galerkin (DG2) and first-order finite volume (FV1) solvers of the two-dimensional shallow water equations for modelling a wide range of flows, including rapidly-propagating, supercritical flows, shock waves, or flows over very smooth surfaces. The new DG2/FV1 solvers are purely two-dimensional and parallelised for the multi-core CPU architecture, but do not integrate with the subgrid channel model nor with the CPU-specific optimisations ([Shaw et al., 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/)).


%### New GPU solvers  
The new DG2/FV1 solvers are also parallelised within a new Nvidia GPU architecture and can run existing LISFLOOD-FP modelling scenarios without modification. The [user manual of LISFLOOD-FP](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view?usp=sharing) has been updated to further offer guidance about how to parametrise the code to run on the GPU, in particular for the DG2/FV1 solvers. Users interested in knowing more about the mathematical/computational background of the DG2/FV1 solvers and how to run them on LISFLOOD-FP are encouraged to start their readings from [Shaw et al. (2021)](https://gmd.copernicus.org/preprints/gmd-2020-340/). 

The rest of this page is devoted to instructing new users on how to download, install and run the code of LISFLOOD-FP 8.0, in particular to use the new hydrodynamic solvers, DG2/FV1. Guidance is provided on preprocessing DG2-related Digital Elevation Model (DEM) and initial condition files (with slope-coefficients), and on posprocessing the coarse DG2 output files to downscale them into a floodplain map at finer resolutions. The documented instructions are also covered in video tutorials and through realistic case studies. 



   | Solver | Suitable applications | Limitations  |
   | :---         | :---      | :--- |
   | ACC   | Fluvial flooding; Pluvial flooding with catchment-scale resolutions      | Not recommended for supercritical flows, e.g., thin flows in pluvial flooding simulations    |
   | FV1     | Fluvial and Pluvial flooding; Dam-breaks       | Higher cost     |
   | DG2     | Fluvial flooding; Dam-breaks; Flows around hydraulic structures       | High computational cost for large-scale applications; Restrictive time-step for applications that involve thin flows    |

***

### Download  

#### [Zenodo for external users](./Zenodo.md)


#### [University of Sheffield users](./UoS_HPC.md) 


***


### Compilation   
LISFLOOD-FP 8.0 is cross-platform and can be compiled on Windows or Linux using [CMake](https://cmake.org/) version 3.13 or above. University of Sheffield users can also compile and run it on the [HPC Computing Facilities](https://www.sheffield.ac.uk/it-services/research/hpc-facilities). The compilation process on each of the platforms is explained below.

- [Windows](/compile_win.md)
  

- [Linux](/compile_lin.md)


- [The University of Sheffield HPC facilities](/compile_hpc.md) 

***


### Case studies 
Case studies are presented to instruct users on how to set up and run the DG2/FV1/ACC solvers of LISFLOOD-FP. These studies are also useful to identify the most optimal DG2 configuration for the targeted application.


#### [1. Merewether urban flooding](./Merewether.md)
This case study [(Smith et al., 2017)](https://www.tandfonline.com/doi/abs/10.1080/15715124.2016.1193510) is used to explain how to set up and run LISFLOOD-FP for beginners using any of the DG2, FV1 and ACC two-dimensional hydrodynamic solvers on the CPU or the GPU.  


#### [2. Dam-break wave over an urban area](./25_Blocks.md) 
This case study [(Soares-Frazao and Zech, 2008)](https://www.tandfonline.com/doi/abs/10.3826/jhr.2008.3164) is aimed to demonstrate when local slope limiting with DG2 should be applied. 


#### [3. Valley flooding following a dam failure](./EnvAcy5.md)  
This case study [(Néelz and Pender, 2013)](https://consult.environment-agency.gov.uk/engagement/bostonbarriertwao/results/appendix-6---neelz--s.---pender--g.--2013--benchmarking-the-latest-generation-of-2d-hydraulic-modelling-packages.-bristol_environment-agency.pdf) is aimed to demonstrate how to handle an inflow boundary condition located inside the computational area, at source point(s).


#### [4. Carlisle 2005 urban flooding](./Carlistle_flooding.md)
This case study [(Horritt et al., 2010)](https://www.icevirtuallibrary.com/doi/pdf/10.1680/wama.2010.163.6.273) is particularly aimed to demonstrate how to handle multiple inflow boundary conditions from different source point(s). It is also used to demonstrate a new postprocessing toolkit for producing metrics to evaluate the floodplain extent predictions when comparing the simulation outcomes of two different hydrodynamic solvers.


#### [5. Eden 2015 fluvial flooding](./Desmond_Eden2015.md)  
This case study [(Xia et al., 2019)](https://www.sciencedirect.com/science/article/abs/pii/S030917081930243X) involves overland flow driven by spatially- and temporally-varying rainfall data over a 2500 kilometre square catchment. It is aimed to demonstrate how to use spatially-varying Manning coefficients provided in an input file, along with the new rain-on-grid option of LISFLOOD-FP 8.0. It is also used to demonstrate a new postprocessing toolkit for downscaling coarse-resolution planar DG2 flood maps.


***

### Video tutorials

1. [Downloading Lisflood](https://youtu.be/qHbt2eNhDgo)

2. [Compiling on Windows](https://youtu.be/cNpeCDQXHCs)

3. [How to set up and run a simulation in Lisflood](https://youtu.be/QENBvUGzoEk)

4. [Running a dam break test with slope limiting](https://youtu.be/p_fuxHsManM)

5. [Running a test with a point-source inflow](https://youtu.be/T21Can8f4Zg)

6. [Running a test with multiple inflows](https://youtu.be/Im7k70E1jLY)

7. [Running a test with spatially and/or temporally varying Manning coefficient rainfall](https://youtu.be/eOA4Vgsf9bY)

***

### License 
The source code of LISFLOOD-FP8.0 is available under a GNU General Public License v3.0 for any non-commercial use and can be downloaded at 10.5281/zenodo.4073011.

***

### Key references 
G. Kesserwani, J.L. Ayog and D. Bau (2018). Discontinuous Galerkin formulation for 2D hydrodynamic modelling: trade-offs between theoretical complexity and practical convenience. Computer Methods in Applied Mechanics and Engineering, 342, 710-741.

J. Ayog, G. Kesserwani, J. Shaw, M.K. Sharifian, and D Bau (2021). Second-order discontinuous Galerkin flood model: comparison with industry-standard finite volume models. Journal of Hydrology, 594: 125924.

J. Shaw, G. Kesserwani, J. Neal, P. Bates, and M. K. Sharifian (2021). LISFLOOD-FP 8.0: the new discontinuous Galerkin shallow water solver for multi-core CPUs and GPUs. Development and technical paper submitted to Geoscientific Model Development, in review.




[back](/Developments.md)

