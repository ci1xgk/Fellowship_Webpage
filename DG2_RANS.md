### Using the DG2-RANS-k-ε turbluent flow solver (resp. the DG2-RANS laminar flow solver)
The DG2-RANS-k-ε turbulent flow solver (resp. DG2-RANS laminar flow solver) can be set-up and run on [LISFLOOD-FP8.0](https://www.seamlesswave.com/LISFLOOD8.0) in the same way as any other uniform-grid solver (see [*"Input files and their format"*](/Merewether1.md)).

In addition, a number of extra parameters need to be typed and initialised in [LISFLOOD-FP8.0](https://www.seamlesswave.com/LISFLOOD8.0)'s `*.par` file. These extra parameters are described in the Tale below: 

| Item name `input`  | Description |
| --------- | ----------- |
|`turbulent`|Boolean keyword instructing LISFLOOD-FP to use DG2-RANS-k-ε|
|`laminar`|Boolean keyword instructing LISFLOOD-FP to use DG2-RANS|
|`inviscid`|Boolean keyword instructing LISFLOOD-FP to use the inviscid flow solver (DG2-SWE). By default, this flow solver is selected if none of `laminar`, `turbulent` and `inviscid` are pointed in `*.par` file|
|`DtRatioLimit`|Keyword followed by a decimal number. It sets the upper bound limit for the turbulent eddy viscosity $D_t$ = `DtRatioLimit` × $D_m$. The default value is 10,000 which means $D_t$ =0.01|
|`TurbIntensity`|Keyword followed by a decimal number. It is the turbulence intensity \$I$ and is used in the turbulent inflow boundary condition calculations. It is between 0 to 20%. The default value is 1%. The guidance for its value: <br> Low-turbulence cases: 0%<*I*≤1% <br> Medium-turbulence cases: 1%<*I*≤5% <br> High-turbulence cases: 5%<*I*≤20%|
|`TurbViscousityRatio`|Keyword followed by a decimal number. It specifies the turbulent viscosity ratio $D_r$ which is used in the turbulent inflow boundary condition calculation. It is usually $D_r$ < 10. Its default value is 0.1|
|`turboutput`|Boolean keyword instructing LISFLOOD-FP to write out ASCII raster files of the turbulent-flow variables $Hk$, *H*$\varepsilon$ and $D_t$. Their average values will be printed in files with the extensions of `*.Hk`, `*.He` and `*.Dt`. Their slope coefficients will be in files with the extensions of `*.Hk1x`, `*.Hk1y`, `*.He1x` and `*.He1y`. Without `turboutput`, there will not be any outputs for the turbulence-flow variables. |
|`startHkHe2d`|Boolean keyword instructing LISFLOOD-FP to read initial condition files for *Hk* and *H*$\varepsilon$ in ASCII raster format. It will read files with the extensions of `*.Hk`, `*.Hk1x`, `*.Hk1y`, `*.He`, `*.He1x` and `*.He1y`. Without `startHkHe2d`, $k$ = $k_{tol}$ = $10^{-12}$ and $\varepsilon$ = $\varepsilon\_{tol}$ = $10^{-12}$ will be used.|

By default, the DG2-RANS-k-ε turbulent flow solver (resp. DG2-RANS laminar flow solver) will be run on multicore CPU. It is also possible to make the run on the GPU by further typing the item `cuda` in the the `*.par` file (see [*“Parameter file (.par)”*](/Merewether1-1.md)). 

The technicalities underpinning the turbulent flow DG2-RANS-k-ε solver (resp. laminar flow DG2-RANS solver), as well as the simpler (invicid) DG2-SWE solver, are all described in a pre-print [Kesserwani et al. 2025](https://drive.google.com/file/d/1x_8bgTIGzJzF_qTEDYUzbu82NsGrxpev/view?usp=sharing) with validation for turbulent and laminar flow experimental benchmarks involving quasi-steady vortical structures. This is the pre-print accepted for publication in [Advances in Water Resources](https://doi.org/10.1016/j.advwatres.2025.104986). 

Videos demonstrating the turbulent flow DG2-RANS-k-ε solver's (resp. laminar flow DG2-RANS solver's) performance for the most challenging test cases: **a video will start after clicking on a test-case image from the list below**.  

|Test case|Reynolds number|Image |
| --------- | ----------- | --------- | 
|Surface-piercing: Vortex shedding past a conical island (DG2-RANS-k-ε-medium)|5,175|[![conical_island](/Figures/Surface_Piercing.png)](https://youtu.be/AU1Db4y1TkM?si=dGk4zH7JbAyHuRWU)|
|Submerged: Vortex shedding past a conical island (DG2-RANS-k-ε-fine) |6,210|[![conical_island](/Figures/DG_RANS_conical_island.png)](https://www.youtube.com/watch?v=PByxld06gU4)|
|Compoundeddies: Flow past a square block in a diverting T-junction (DG2-RANS-k-ε-fine)|7,432|[![T_junction](/Figures/DG_RANS_T_junction.png)](https://www.youtube.com/shorts/G43xtVfk_iU)|
|Laminar wake interactions past cylinders (DG2-RANS-medium)|220|[![array_of_cylinder3d_Dt_2D](/Figures/DG_RANS_array_of_cylinder3d_Dt_2D.png)](https://www.youtube.com/watch?v=JMv3jLEjzp4)|






#### "Recirculation flow in sharp building cavities"
In contrast to all the other experimental benchmarks, this benchmark involves a skewed (non-uniform distribution of) infow velocity components. Therefore, resolution-specific pre-processing of the inflow boudary was applied and can be activated by further typing these two items. 



| Item name `input`  | Description |
| --------- | ----------- |
|`cavity_coarse`|Boolean keyword instructing LISFLOOD-FP to simulate the "Recirculation flow in sharp building cavities" benchmark test using the coarse grid (0.32 m) -|
|`cavity_fine`|Boolean keyword instructing LISFLOOD-FP to simulate the "Recirculation flow in sharp building cavities" benchmark test using the fine grid (0.16 m) -skewed infow is resolution specific|


![Recirculation flow in sharp building cavities](/Figures/DG_RANS_Many_cavities.png)

[back](/LISFLOOD8.0.md)
