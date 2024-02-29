### Using the GPU-MWDG2 solver

To run simulations using the GPU-MWDG2 solver, an NVIDIA GPU and the [CUDA Toolkit](https://developer.nvidia.com/cuda-toolkit) must be installed. The following [Python](https://www.python.org/downloads/) packages must also be installed:

- `pandas`
- `numpy`
- `matplotlib`

#### 1 Running simulations using GPU-MWDG2: building LISFLOOD-FP

To run simulations using the GPU-MWDG2 solver, LISFLOOD-FP must be compiled and built. Only a summary of the steps for compiling and building LISFLOOD-FP is provided in this page, but in case the steps need troubleshooting, more detailed guidance on compiling and building LISFLOOD-FP is available on the SEAMLESS-WAVE website: [here for Windows](/compile_win.md), and [here for Linux](/compile_lin.md). 

##### 1.1 Building on Windows

1. Open the folder `LISFLOOD-FP` in Visual Studio
2. Go to toolbar at the top and select either the `x64-Debug` or `x64-Release` option from the dropdown menu
3. From the toolbar click `Build > Rebuild All`
4. If the `x64-Debug` option was selected, the built executable `lisflood.exe` may be located in `LISFLOOD-FP\out\build\x64-Debug` (`LISFLOOD-FP\out\build\x64-Release` if `x64-Release` was selected).

##### 1.2 Building on Linux*

1. Navigate to the `LISFLOOD-FP` directory
2. Run `cmake -S . -B build` in the command line
3. Run `cmake --build build`
4. The built executable `lisflood` will be located in `LISFLOOD-FP/build`

\* There is a potential issue about building on Linux because the [CUB library](https://nvlabs.github.io/cub/) is not properly detected. This issue be avoided by changing all `#include`s with `cub/` to `../../cub/`.

#### 2 Running simulations using the GPU-MWDG2 solver: preparing the input files

Running simulations using the GPU-MWDG2 solver follows a very similar workflow as previous versions of [LISFLOOD-FP](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) but with some minor differences, explained next. A summary of the LISFLOOD-FP workflow is provided in this readme, but more detailed guidance is available [on the SEAMLESS-WAVE website](/Merewether1.md). The workflow requires preparing several input files, as listed in the table below:

|Input file|File extension|Description|
|----------|--------------|-----------|
|Digital elevation model|`.dem`|ASCII [raster file](https://support.geocue.com/ascii-raster-files-asc/) containing the numerical values of the bathymetric elevation pixel-by-pixel.|
|Initial flow conditions|`.start`<br>`.start.Qx`<br>`.start.Qy`|ASCII raster file containing the numerical values of the initial water depth and discharge pixel-by-pixel.|
|Boundary conditions|`.bci`|Text file specifying where boundary conditions are enforced and what type (fixed versus time-varying).|
|Point source locations|`.bci`|Text file specifying the locations of point sources and what type (fixed versus time-varying).|
|Time series at boundaries and point sources|`.bdy`|Text file containing time series in case time-varying boundary conditions and/or point sources have been specified in the .bci file.|
|Stage and gauge locations|`.stage`<br>`.guage`|Text file containing the locations of virtual stage and gauge points where simulated time histories of the water depth and discharge are recorded.|
|Parameter file|`.par`|Text file containing parameters to access various model features for running a simulation.|

### 2.1 Example: Monai valley

Consider an example of using the GPU-MWDG2 solver to run a simulation of the Monai valley test case in Section 3.3.2 of [Chowdhury et al. 2023](https://iwaponline.com/jh/article/doi/10.2166/hydro.2023.154/95732/GPU-parallelisation-of-Haar-wavelet-based-grid). This test case needs the following input files:

- `monai.par`
- `monai.dem`
- `monai.start`
- `monai.bci`
- `monai.bdy`
- `monai.stage`

Note that unlike the uniform grid DG2 solver, for which the DG2 slope coefficients need to be manually provided by the user in `.dem1x`, `.dem1y`, `.start1x` and `.start1y` files by generating them with the `generateDG2DEM` and `generateDG2start` utilities, GPU-MWDG2 initialises DG2 slope coefficients automatically using only the `.dem` and/or `.start` files.

To prepare the input files listed above and then run simulations of the Monai valley test case, the following steps should be done:

1. Copy the `LISFLOOD-FP\testing\UoS\monai` folder to the same location as the `lisflood.exe` executable, e.g. to `LISFLOOD-FP\out\build\x64-Release`
2. Navigate to `LISFLOOD-FP\out\build\x64-Release\monai`
3. Prepare a stage file `monai.stage` by running `python stage.py` in a command prompt
4. Prepare the raster files `monai.dem` and `monai.start` by running `python raster.py`
5. Prepare the boundary inflow files `monai.bci` and `monai.bdy` by running `python inflow.py`
6. Prepare a parameter file called `monai.par` (parameters needed in file shown below)
7. Run `..\lisflood.exe monai.par` in a command prompt to start running the simulation

**Automated simulations**

Instead of manually running the simulation by doing the steps above, the simulation can be run automatically by opening a command prompt at `LISFLOOD-FP\out\build\x64-Release\monai` and running `python simulate.py`. This will automatically do all the preprocessing for preparing the input files (steps 3 to 6), run several simulations (step 7), and postprocess the results.

Doing steps 1 to 7 will give the following folder tree:

```
-- LISFLOOD-FP
 |
 ...
 |
 | -- out
    |
    ...
    |
    | -- build
        |
        ...
        | -- x64-Release
           |
           ...
           |
           | -- monai
               |
               ...
               | monai.par
               | monai.dem
               | monai.start
               | monai.bci
               | monai.bdy
               | monai.stage
```

#### Parameter (`.par`) file for the Monai valley example 

```
cuda
mwdg2
epsilon       0.001
max_ref_lvl   9
wall_height   0.5
refine_wall
ref_thickness 16
initial_tstep 1
cumulative
raster_out
fpfric        0.01
sim_time      22.5
massint       0.1
saveint       22.5
DEMfile       monai.dem
startfile     monai.start
bcifile       monai.bci
bdyfile       monai.bdy
stagefile     monai.stage
```

### 2.2 What is a parameter file?

A parameter (`.par`) file is a text file that specifies various parameters for running a simulation. Detailed explanations on the parameters and what function they serve have already been provided [here](/Merewether1.md), but they are provided again for reference in the table below, with the extra parameters in LISFLOOD-FP 8.2 *specifically* for running the GPU-MWDG2 solver being highlighted in bold:

| Parameter      | Description |
| -------------- |-------------|
|**`cuda`**          | Boolean keyword instructing the code to use the GPU-parallelised solvers. |
|**`mwdg2`**         | Boolean keyword instructing the code to use the GPU-MWDG2 solver. |
|**`epsilon`**       | Keyword followed by a decimal number. Specifies the error threshold ε used by the model to control the amount of coarsening in the non-uniform grid. A larger value allows a higher amount of coarsening. |
|**`max_ref_lvl`**   | Keyword followed by an integer. Specifies the maximum refinement level L used by the model when setting the $2^L × 2^L$ finest resolution grid. For a test case involving a digital elevation model (DEM) made up of $N × M$ cells, the user must specify the value of L to be such that $2^L ≥ \max(N, M)$. By doing so, two areas emerge in the grid: the actual $N × M$ domain area defined by the DEM, and empty areas beyond the $N × M$ area where no DEM data are available and where no flow should should occur. |
|**`wall_height`**   | Keyword followed by a decimal number. Specifies the height of the wall in metres used by the model to fill the empty areas beyond the domain area. The user must specify a sufficiently high wall height to prevent any flow from exiting past the walls. |
|**`refine_wall`**   | Boolean keyword to prevent the model from excessively coarsening the non-uniform grid around the wall separating the domain area from the void areas. The user can enable this refinement to ensure that very coarse cells around the wall do not lead to unrealistic calculations. |
|**`ref_thickness`** | Keyword followed by an integer. Specifies the number of cells that are to be refined around the wall by the model when the refine_wall keyword is also specified. |
|**`cumulative`**    | Boolean keyword instructing the model to produce a `.cumu` file that contains time series data designed to help in assessing the effect of grid adaptation on the runtime. |
|`DEMfile`           | Keyword followed by text. Specifies the name of the raster file containing the DEM. |
|`startfile`         | Keyword followed by text. Specifies the name of the raster file containing the initial water depths. |
|`bcifile`           | Keyword followed by text. Specifies the name of the boundary condition file. |
|`bdyfile`           | Keyword followed by text. Specifies the name of the file containing the time-varying conditions. |
|`stagefile`         | Keyword followed by text. Specifies the name of the stage file. |
|`sim_time`          | Keyword followed by a decimal number. Specifies the simulation time in seconds. |
|`hwfv1`             | Boolean keyword instructing the code to use the GPU-HWFV1 solver. |
|`initial_t_step`    | Keyword followed by a decimal number. Specifies the initial timestep. |
|`vtk`               | Boolean keyword to enable the output of `.vtk` output files for viewing flow and topography data over a non-uniform grid. |
|`c_prop`            | Boolean keyword to enable the output of discharges; only applicable for quiescent test cases. |
|`raster_out`        | Boolean keyword to enable the output of raster files. |
|`voutput_stage`     | Boolean keyword to also save the velocity time series at the stage locations. |
|`resroot`           | Keyword followed by text. Specifies the prefix of the names of the output files. |
|`dirroot`           | Keyword followed by text. Specifies the name of the folder where the output files are saved. |
|`massint`           | Keyword followed by a decimal number. Specifies the time interval in seconds at which stage or guage data are recorded. |
|`saveint`           | Keyword followed by a decimal number. Specifies the time interval in seconds at which raster or `.vtk` output files are saved. |

The `cumulative` instructs the GPU-MWDG2 solver to produce a `.cumu` file that contains various time series data for assessing the efficiency achieved by dynamic GPU-MWDG2 adaptivity:

| Heading in file    | Description of time series |
|--------------------|-----------------------------|
| `simtime`          | Simulation time in seconds. |
| `runtime_mra`      | Computational effort (measured in seconds) spent by GPU-MWDG2 to perform the MRA process and generate the non-uniform grid up to a given simulation time. |
| `runtime_solver`   | Computational effort (measured in seconds) spent by GPU-MWDG2 to perform the DG2 update for performing the solver computations on the non-uniform grid up to a given simulation time. |
| `runtime_total`    | Sum of the `runtime_mra` and the `runtime_solver` time series, listing the total computational effort spent by GPU-MWDG2 up to a given simulation time. |
| `dt`               | Timestep. |
| `reduction`        | Percentage reduction in the cell count of GPU-MWDG2’s non-uniform grid relative to the cell count of GPU-DG2’s uniform grid. |

These time series data are entensively used to analyse the efficiency of the GPU-MWDG2 solver in [this paper](), which explores the potential speedup achieved by dynamic GPU-MWDG2 adaptivity over the GPU-parallelised uniform-grid DG2 solver released in LISFLOOD-FP 8.0 ([Shaw et al. 2020](https://gmd.copernicus.org/articles/14/3577/2021/)) when simulating a number of test cases of tsunami-induced flooding. The test cases are listed below:

|Test case|Reference|*L*|
|---------|---------|-|
|Monai valley|[Caviedes-Voullième et al., 2020](https://www.sciencedirect.com/science/article/abs/pii/S0309170819309121)|9|
|Seaside, Oregon|[Macías et al., 2020](https://www.sciencedirect.com/science/article/abs/pii/S037838391830351X)|12|
|Tauranga harbour|[Borrero et al., 2015](https://staff.washington.edu/rjl/pubs/Tauranga2015/BorreroLeVequeEtAl2015.pdf)|12|
|Hilo harbour|[Arcos and LeVeque, 2015](https://link.springer.com/article/10.1007/s00024-014-0980-y)|10|

### Example: Seaside, Oregon

[back](/LISFLOOD8.0.md)
