
## LISFLOOD-FP8.0 

Initially developed by the [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/), the LISFLOOD-FP hydrodynamic modelling framework has undergone many developments. It include solvers of the 2D (invicid) shallow water equations with various mathematical and/or numerical complexities for raster-formatted hydraulic simulations. 

The local inertia solver, known as the ACC solver, is widely used to simulate floods with gradually-varying, subcritical flow over sufficiently rough surfaces with Manning’s coefficient of at least 0.03. It has a version with CPU-specific optimisations and enhanced with a subgrid channel model ([Neal et al., 2012](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2012WR012514), [2018](https://www.sciencedirect.com/science/article/pii/S1364815217307478)). 

LISFLOOD-FP8.0 includes second-order discontinuous Galerkin (DG2) and first-order finite volume (FV1) solvers of the 2D (invicid) shallow water equations for modelling a wide range of flows, including rapidly-propagating, supercritical flows, shock waves, or flows over very smooth surfaces. The DG2/FV1 solvers are parallelised for the multi-core CPU architecture, but do not integrate with the subgrid channel model.

To decrease the computational costs, the ACC, FV1 and DG2 solvers have been accelerated using Graphics Processing Units (GPUs) ([Shaw et al., 2021](https://gmd.copernicus.org/preprints/gmd-2020-340/); [Sharifian et al., 2023](https://doi.org/10.5194/gmd-16-2391-2023)). The suitable applications for each of these (invicid) solvers of are summarised in the table below, along with their potential limitations.  

<!--
The LISFLOOD-FP hydrodynamic model developed by the [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) already includes a solver with local inertia, or ‘gravity wave’ formulation, known as the ACC solver, and a solver with the diffusive wave, or ‘zero-inertia’ formulation, known as the ATS solver. The ACC solver is widely used to simulate floods with gradually-varying, subcritical flow over sufficiently rough surfaces with Manning’s coefficient of at least 0.03. It has a version with CPU-specific optimisations and enhanced with a subgrid channel model ([Neal et al., 2012](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2012WR012514), [2018](https://www.sciencedirect.com/science/article/pii/S1364815217307478)). Please contact [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) for any advice related to the ACC solver.   
-->

<!-- 
### New DG2/FV1 (invicid) solvers on multi-core CPU 
The new version, LISFLOOD-FP 8.0, includes second-order discontinuous Galerkin (DG2) and first-order finite volume (FV1) solvers of the two-dimensional shallow water equations (SWE) for modelling a wide range of flows, including rapidly-propagating, supercritical flows, shock waves, or flows over very smooth surfaces. The new DG2/FV1 solvers are purely two-dimensional and parallelised for the multi-core CPU architecture, but do not integrate with the subgrid channel model nor with the CPU-specific optimisations ([Shaw et al., 2021](https://gmd.copernicus.org/articles/14/3577/2021/)).
-->

<!-- 
### New GPU (invicid) solvers 
The new DG2/FV1 solvers are also parallelised within a new Nvidia GPU architecture and can run existing LISFLOOD-FP modelling scenarios without modification. The [user manual of LISFLOOD-FP](https://drive.google.com/file/d/1Yk5txMWWfSqPcPOqjQh30XLSp8Sypy1M/view?usp=sharing) has been updated to further offer guidance about how to parametrise the code to run on the GPU, in particular for the DG2/FV1 solvers. Users interested in knowing more about the mathematical/computational background of the DG2/FV1 solvers and how to run them on LISFLOOD-FP are encouraged to start their readings from [Shaw et al. (2021)](https://gmd.copernicus.org/articles/14/3577/2021/).
 -->

   | Invicid Solver | Suitable applications | Limitations  |
   | :---         | :---      | :--- |
   | ACC   | Fluvial flooding; Pluvial flooding on catchment-scale resolutions      | Not recommended for supercritical flows, e.g., thin flows in pluvial flooding simulations at fine resolution   |
   | FV1     | Fluvial and Pluvial flooding; Dam-breaks       | Might fail in capturing small-scale transients of flows       |
   | DG2     | Fluvial flooding; Dam-breaks; tsunamis; Flows around hydraulic structures       | High computational cost for large-scale applications; Restrictive time-step for applications that involve thin flows    |


### ACC (invicid) solver adapted on a static, non-uniform grid, generated by multiwavelets Galerkin projection of the DEM
LISFLOOD-FP8.1 includes a new GPU-accelerated solver, known as the non-uniform ACC solver. The non-uniform grid is generated by the multiresolution analyses (MRA) of multiwavelets (MWs) to a Galerkin projecion of the digital elevation model (DEM). The ACC solver runs on this non-uniform grid without any grading across resolution levels. The technical background of the non-uniform ACC solver can be found in [Sharifian et al. (2023)](https://gmd.copernicus.org/articles/16/2391/2023/gmd-16-2391-2023.html) and the new parameters required for the non-uniform ACC solver with video tutorials for reproducing real-world catchment- and urban-scale case studies are detailed in this section: [*"Using the non-uniform ACC solver"*](/ACC_NU.md). 

### Adaptive FV1/DG2 (invicid) solvers on dynamic non-uniform grid generated by Haar wavelets (HW)/multiwavelets (MW)

LISFLOOD-FP8.2 include a new GPU-parallelised adaptive FV1/DG2 solvers that run on an adaptive grid generated by the MRA of the HW/MW, respectively, whereby *adaptive grid* refers to a dynamic-in-time non-uniform grid that is generated every timestep. The new solvers, namely the GPU-parallelised MW adaptive DG2 solver, called GPU-MWDG2, is overviewed in a [Chowdhury and Kesserwani (2025)](https://doi.org/10.5194/gmd-2024-152) and the guidance for running GPU-MWDG2 simualtions is available in this section: [*"Using GPU-MWDG2 in LISFLOOD-FP"*](/Adaptive.md).

### DG2-RANS-k-ε solver with GPU acceletation to simulate viscous turbulent shallow vortical flows

A turbulent shallow vortical flow simulator has also been added to LISLFOOD-FP. It adapts the DG2 numerical method to solve Reynolds-Average Navier-Stokes (RANS) Equations close by the two-equation k-ε turbulence model. It can be run on a multicore CPU or on the GPU. See [Kesserwani et al. 2025](https://drive.google.com/file/d/1x_8bgTIGzJzF_qTEDYUzbu82NsGrxpev/view?usp=sharing) for detailed description of the technical underpinning of the "DG2-RANS-k-ε turbulent flow solver" and the "DG2-RANS laminar flow solver". Further guidance as to how to run these solvers on LISFLOOD-FP is available in the section: [*"Using the DG2-RANS-k-ε solver in LISFLOOD-FP"*](DG2_RANS.md).


The rest of this page includes instructions on how to download, install and run the code of LISFLOOD-FP 8.0-8.2, for using the uniform grid invicid DG2-SWE and FV1-SWE solvers. These same instructions will also be needed to set-up the adaptive SWE solvers and the DG2-RANS-k-ε turbulent flow and DG2-RANS laminar flow solvers.  

Guidance is provided on producing the Galerkin polynomial projection of the DEM and initial condition files (with slope-coefficients), and on post-processing the coarse Galerkin polynomial output files to downscale them into a floodplain map at finer resolutions.

The documented instructions are also covered in video tutorials and through realistic case studies.

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
The source code of LISFLOOD-FP8.1 is available under a GNU General Public License v3.0 for any non-commercial use and can be downloaded at 10.5281/zenodo.4073011.

***

### Key references 
G. Kesserwani, J.L. Ayog and D. Bau (2018). [Discontinuous Galerkin formulation for 2D hydrodynamic modelling: trade-offs between theoretical complexity and practical convenience](https://www.sciencedirect.com/science/article/pii/S004578251830389X). Computer Methods in Applied Mechanics and Engineering, 342, 710-741.

J. Ayog, G. Kesserwani, J. Shaw, M.K. Sharifian, and D Bau (2021). [Second-order discontinuous Galerkin flood model: comparison with industry-standard finite volume models](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858). Journal of Hydrology, 594: 125924.

J. Shaw, G. Kesserwani, J. Neal, P. Bates, and M. K. Sharifian (2021). [LISFLOOD-FP 8.0: the new discontinuous Galerkin shallow water solver for multi-core CPUs and GPUs](https://gmd.copernicus.org/articles/14/3577/2021/gmd-14-3577-2021.html). Geoscientific Model Development, 14, 3577–3602.

M. K. Sharifian, G. Kesserwani, A. Chowdhury, J. Neal, and P. Bates (2023). [LISFLOOD-FP 8.1: New GPU accelerated solvers for faster fluvial/pluvial flood simulations](https://doi.org/10.5194/gmd-2022-259). Geoscientific Model Development, 16, 2391–2413.

A. Chowdhury, and G. Kesserwani (2025). [LISFLOOD-FP 8.2: GPU-accelerated multiwavelet discontinuous Galerkin solver with dynamic resolution adaptivity for rapid, multiscale flood simulation](https://doi.org/10.5194/gmd-2024-152).  Geosci. Model Dev. Discuss. 

G. Kesserwani, X. Sun, M. Hajihassanpour, M. K. Sharifian (2025). [Discontinuous Galerkin simulator of shallow vortical flow with turbulence](https://drive.google.com/file/d/1x_8bgTIGzJzF_qTEDYUzbu82NsGrxpev/view?usp=sharing). Advances in Water Resources, [201C, 104986](https://doi.org/10.1016/j.advwatres.2025.104986).
. 

***

### About the Developers 
While the original version of LISFLOOD-FP were set in motion by [University of Bristol](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/), the recent versions 8.0 and 8.1 were mainly developed as part of the SEAMLESS-WAVE project lead by [Georges Kesserwani](https://www.sheffield.ac.uk/civil/people/academic/georges-kesserwani) in University of Sheffield, who is main contact about these versions.   

[Contact Georges](mailto:g.kesserwani@shef.ac.uk)



The main GPU kernels for the FV1 and DG2 solvers were initiated by [James Shaw](https://www.datumedge.co.uk/) during his postdoctoral research, before joining [The Floow](https://www.thefloow.com/) as a senior software engineer. Further developments were mainly carried out by [Mohammad Kazem Sharifian](https://www.linkedin.com/in/mohammad-kazem-sharifian-12b1a440/), including the GPU kernels of the ACC solver for the uniform and non-uniform grids. Mohammad is now a Flood Modeller at [RMS (Moody's Analytics Company)](https://www.rms.com/) and is happy to receive enquiries about the software, bug reports, feature requests, or any relevant matter that needs the community's attention.  

[Contact Mohammad](mailto:mksharifian@gmail.com)




[back](/Developments.md)

