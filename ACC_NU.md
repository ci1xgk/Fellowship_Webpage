### Using the non-uniform ACC solver

The non-uniform ACC solver is distributed as a new solver in the LISFLOOD-FP ecosystem and follows the same standard usage with a few updates to input/output components. Setting up the simulations for using the new non-uniform ACC solver follows the same conventions of LISFLOOD-FP as described in section [*"Input files and their format"*](/Merewether1.md), with a few updates to the `.par` file:
* The non-uniform ACC solver is selected by including item `acc_nugrid`.
* The error threshold, $\varepsilon$, is selected by including item `epsilon`, followed by a float number refering to the value of $\varepsilon$.
* The maximum refinement level, *L*, is selected by including the item `L`, followed by an integer refering to the value of *L*.
* The 2D model outputs are generated in two forms: 
   1. Multiresolution grid as `.vtk` file format (see section [*"Non-uniform grid output files (-xxxx.vtk)"*](/vtk.md) for further information about `.vtk` files and how to visualise them).
   2. Standards uniform grid of LISFLOOD-FP as conventional raster files (Recall section [*"Water depth or free-surface elevation output files (-xxxx.wd, -xxxx.elev)"*](/Merewether3-2.md)). 
   
   By default both of these files are generated at the intervals specified by item `saveint`. However, the generation of the `.vtk` files can be suppressed (to save disk space) by including the item `vtkoff`.

These modifications to the `.par` files are summarised in the table below.

   | Item name `input` | Description | Solver |
   | :---         | :---      | :--- |
   | acc_nugrid     | Selects the non-uniofrm ACC solver       | non-uniform ACC      |
   | cuda    | Run the selected solver on GPU       | All      |
   | epsilon     | The choice of error threshold, $\varepsilon$       | non-uniform ACC      |   
   | L     | The maximum refinement levels, *L*      | non-uniform ACC      |   
   | vtkoff     | Suppress production of 2D multiresolution map files (`*.vtk`)     | non-uniform ACC      |   

The mathematical/computational background of the MW-based grid generation, the adaptation of the ACC solver on the resulting grids and the idea behind the GPU parallelisation are explained in [HESS manuscript](https://www.hydrology-and-earth-system-sciences.net/). In the latter, the non-uniform ACC solvers were applied to reproduce five real-world fluvial/pluvial case studies, including three catchment-scale scenarios and two urban flooding cases on city-scale. The case studies are summarised in table below. 

   | Test Case | Source | Type | Number of elements (thousands) | *L* | *R* (m) | Simulation time (hr) |
   | :---         | :---      | :---       | :---         | :---      | :--- |  :--- | 
   | Lower triangle catchment   | [Özgen-Xian et al., 2020](https://iwaponline.com/jh/article/22/5/1059/73853/Wavelet-based-local-mesh-refinement-for-rainfall)              | Pluvial    | 149, 594, 3700 | 10, 11, 12 | 10, 5, 2 | 72 |
   | Upper Lee Catchment   | [Xia and Liang, 2018](https://www.sciencedirect.com/science/article/pii/S0309170818302124#:~:text=A%20new%20implicit%20scheme%20is,in%20the%20shallow%20water%20equations.&text=The%20new%20scheme%20can%20relax%20flow%20velocities%20towards%20the%20correct%20equilibrium%20state.&text=The%20new%20scheme%20is%20numerically,for%20simulating%20very%20shallow%20flows.)              | Pluvial    | 2712 | 12 | 20 | 120 |
   | Eden catchment  | [Xia et al., 2019](https://www.sciencedirect.com/science/article/pii/S030917081930243X) | Fluvial    | 6276 | 13 | 20 | 132 |
   | Glasgow urban area | [Néelz and Pender, 2013](https://consult.environment-agency.gov.uk/engagement/bostonbarriertwao/results/appendix-6---neelz--s.---pender--g.--2013--benchmarking-the-latest-generation-of-2d-hydraulic-modelling-packages.-bristol_environment-agency.pdf) | Pluvial    | 95 | 9 | 2 | 5 |
   | Cockermouth urban area  | [Muthusamy et al., 2021](https://www.sciencedirect.com/science/article/pii/S0022169421001359) | Fluvial    | 2160 | 11 | 1 | 144 |
    
The step by step instructions on how to download and install the code, along with instructions on simulating two of the case studies are given in the videos linked below. Only two case studies are selected as both involve specific features of the setup process and the rest of them follow the same process.  

1. [Download and installation](https://youtu.be/jJDRMBkPyr8)

2. [Upper Lee catchment case study](https://youtu.be/IQBr9kxI-0k)

3. [Glasgow urban area case study](https://youtu.be/8yKIa7-mcg8)
   
   
[back](/LISFLOOD8.0.md)
