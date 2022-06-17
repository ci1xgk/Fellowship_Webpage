### Using the non-uniform ACC solver

Things to coverin this section:

Setting up the simulations follows the same conventions as described in [description of the .par file], with the following modifications:
1. The solver is selected by including item “acc_nugrid”
2. The error threshold parameter, epsilon, is selected by including item “epsilon value” where value refers to the values of the error threshold parameter.
3. The maximum resolution level, L, is selected by including the item “L value”, where value refers to an integer for the maximum resolution level
4. The 2D model outputs are generated in two forms: (i) on multiresolution grid as “.vtk” file format [link to description of .vtk files and how to use paraview], and (ii) on uniform grid as the conventional raster files [link to output raster files]. By default both these files are generated at the intervals specified by item “saveint”. However, the generation of the “.vtk” files can be suppressed by including the item “vtkoff”.   



   | Item name `input` | Description | Solver |
   | :---         | :---      | :--- |
   | acc_nugrid     | Selects the non-uniofrm ACC solver       | non-uniform ACC      |
   | cuda    | Run the selected solver on GPU       | All      |


table

   | Test Case | Source | Type | Number of elements (thousands) | Maximum refinements level, L | Resolution, R (m) | Simulation time (hr) |
   | :---         | :---      | :---       | :---         | :---      | :--- |  :--- | 
   | Lower triangle catchment   | [Özgen-Xian et al., 2020](https://iwaponline.com/jh/article/22/5/1059/73853/Wavelet-based-local-mesh-refinement-for-rainfall)              | Pluvial    | 149, 594, 3700 | 10, 11, 12 | 10, 5, 2 | 72 |
   | Upper Lee Catchment   | [Xia and Liang, 2018](https://www.sciencedirect.com/science/article/pii/S0309170818302124#:~:text=A%20new%20implicit%20scheme%20is,in%20the%20shallow%20water%20equations.&text=The%20new%20scheme%20can%20relax%20flow%20velocities%20towards%20the%20correct%20equilibrium%20state.&text=The%20new%20scheme%20is%20numerically,for%20simulating%20very%20shallow%20flows.)              | Pluvial    | 2712 | 12 | 20 | 120 |
   | Eden catchment  | [Xia et al., 2019](https://www.sciencedirect.com/science/article/pii/S030917081930243X) | Fluvial    | 6276 | 13 | 20 | 132 |
   | Glasgow urban area | [Néelz and Pender, 2013](https://consult.environment-agency.gov.uk/engagement/bostonbarriertwao/results/appendix-6---neelz--s.---pender--g.--2013--benchmarking-the-latest-generation-of-2d-hydraulic-modelling-packages.-bristol_environment-agency.pdf) | Pluvial    | 95 | 9 | 2 | 5 |
   | Cockermouth urban area  | [Muthusamy et al., 2021](https://www.sciencedirect.com/science/article/pii/S0022169421001359) | Fluvial    | 2160 | 11 | 1 | 144 |
   
   
   
  Here video tutorials are provided in a step by step manner for setting up the four test cases
   
   
[back](/LISFLOOD8.0.md)
