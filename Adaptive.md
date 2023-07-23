### Using the GPU-MWDG2 solver

The GPU-MWDG2 solver is a new solver in LISFLOOD-FP. GPU-MWDG2 is used in a similar way as other solvers in LISFLOOD-FP (i.e., following the guidance described in section [*"Input files and their format"*](/Merewether1.md)), but with following changes:

* Six extra parameters need to be included in the `.par` file, as described in the table below.
* The DG2 slope coefficients are automatically initialised by GPU-MWDG2, unlike the uniform grid DG2 solver for which the DG2 slope coefficients need to manually initialised using the `generateDG2DEM` and `generateDG2start` utilities.

| Parameter | Description |
| --------- | ----------- |
| mwdg2 | Boolean keyword instructing LISFLOOD-FP 8.2 to use GPU-MWDG2. |
| cumulative | Boolean keyword instructing GPU-MWDG2 to produce a file called cumulative-data.csv that contains time series data designed to help in assessing the effect of grid adaptation on the time-to-solution delivered by GPU-MWDG2. |
| max_ref_lvl | Keyword followed by an integer. Specifies the maximum refinement level L used by GPU-MWDG2 when setting the finest resolution grid. For a test case involving a DEM made up of N × M cells, the user must specify the value of L to be such that 2L ≥ max(N, M). |
| epsilon | Keyword followed by a decimal number. Specifies the error threshold ε used by GPU-MWDG2 to control the amount of coarsening in the non-uniform grid. A larger value allows a higher amount of coarsening. |
| wall_height | Keyword followed by a decimal number. Specifies the height of the wall in metres used by GPU-MWDG2 to fill the void areas beyond the domain area. The user must specify a sufficiently high wall height to prevent any flow from exiting past the walls. |
| refine_wall | Boolean keyword to prevent GPU-MWDG2 from excessively coarsening the non-uniform grid around the wall separating the domain area from the void areas. The user can enable this refinement to ensure that very coarse cells around the wall do not lead to unrealistic calculations. |
| ref_thickness | Keyword followed by an integer. Specifies the number of cells that are to be refined around the wall by GPU-MWDG2 when the refine_wall keyword is also specified. |

The GPU-MWDG2 solver will be described in [this paper](), which explores the potential speedup of GPU-MWDG2 over the uniform grid GPU-DG2 solver released in LISFLOOD-FP 8.0 over four tsunami-driven flooding test cases, which are listed in the table below.

|Test case|Reference|L|
|---------|---------|-|
|Conical island|Reference|10|
|Okushiri island|Reference|9|
|Seaside, Oregon|Reference|12|
|Tauranga harbour|Reference|12|

The following video shows how to run GPU-MWDG2 for two of the test cases, Okushiri island and Seaside, Oregon, on a personal machine and a high-performance computing cluster respectively: [Running test cases using GPU-MWDG2]().


[back](/LISFLOOD8.0.md)