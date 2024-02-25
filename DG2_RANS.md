### Using the DG2-RANS solver
The DG2-RANS solver is a new solver in LISFLOOD-FP. DG2-RANS is used in a similar way as other solvers in LISFLOOD-FP (i.e., following the guidance described in Section [*"Input files and their format"*](/Merewether1.md)), but several extra parameters are needed to be included in the *.par file, as described in the table below

| Item name `input`  | Description |
| --------- | ----------- |
|turbulent|Boolean keyword instructing LISFLOOD-FP to use turbulent flow simulator|
|laminar|Boolean keyword instructing LISFLOOD-FP to use laminar flow simulator (without turbulence fluctuations)|
|inviscid|Boolean keyword instructing LISFLOOD-FP to use Inviscid flow simulator (without turbulence fluctuations and viscous effects). This is the default flow solver, so if none of `laminar`, `turbulent` and `inviscid` are pointed in *.par file, then the inviscid flow will be considered.|
|DtRatioLimit|Keyword followed by a decimal number. It indirectly sets the upper bound limit for the turbulent (eddy) viscosity $D_t$ = `DtRatioLimit` × $D_m$ The default value is 10,000 which means $D_t$ =0.01.|
|TurbIntensity|Keyword followed by a decimal number. It is the turbulence intensity $I$ and is used in the turbulent inflow boundary condition calculations. It is between 0 to 20%. The default value is 1%. The guidance for its value: <br> Low-turbulence cases: 0%<*I*≤1% <br> Medium-turbulence cases: 1%<*I*≤5% <br> High-turbulence cases: 5%<*I*≤20%|
|TurbViscousityRatio|Keyword followed by a decimal number. It specifies the turbulent viscosity ratio $D_r$ which is used in the turbulent inflow boundary condition calculation. It is usually $D_r$ < 10. Its default value is 0.1. |
|turboutput|Boolean keyword instructing LISFLOOD-FP to write out ASCII raster files of the turbulence-related variables $Hk$, *H*$\varepsilon$ and $D_t$. Their average values will be printed in files with the extensions of *.Hk, *.He and *.Dt. Their slope coefficients will be in files with the extensions of *.Hk1x, *.Hk1y, *.He1x and *.He1y. Without `turboutput`, there will not be any outputs for the turbulence-related variables. |
|startHkHe2d|Boolean keyword instructing LISFLOOD-FP to read initial condition files for *Hk* and *H*$\varepsilon$ in ASCII raster format. It will read files with the extensions of *.Hk, *.Hk1x, *.Hk1y, *.He, *.He1x and *.He1y. Without `startHkHe2d`, $k$ = $k_{tol}$ = $10^{-12}$ and $\varepsilon$ = $\varepsilon\_{tol}$ = $10^{-12}$ will be used.|
|cavity_coarse|Boolean keyword instructing LISFLOOD-FP to simulate "Recirculation flow in sharp building cavities" benchmark test using the coarse grid (0.32 m).|
|cavity_fine|Boolean keyword instructing LISFLOOD-FP to simulate "Recirculation flow in sharp building cavities" benchmark test using the fine grid (0.16 m).|

By default, DG2-RANS will be launched on multicore units. Launching it on GPU needs adding `cuda` input parameter to the *.par file as described in Section [*“Parameter file (.par)”*](/Merewether1-1.md). 

The DG2-RANS solver is described in [this paper](), which explores the performance of DG2-RANS over four vortical shallow water test cases listed below.

|Test case|Reynolds number|Snapshot|
| --------- | ----------- | --------- | 
|Laminar wake(s) past cylinder(s)|200-220|[![array_of_cylinder3d_Dt_2D](/Figures/DG_RANS_array_of_cylinder3d_Dt_2D.png)](https://www.youtube.com/watch?v=JMv3jLEjzp4)|
|Vortex shedding past a conical island|6,210|[![conical_island](/Figures/DG_RANS_conical_island.png)](https://www.youtube.com/watch?v=PByxld06gU4)|
|Recirculation flow in sharp building cavities|112,673|![Many_cavities](/Figures/DG_RANS_Many_cavities.png)|
|Flow past a square block in a diverting T-junction|7,432|[![T_junction](/Figures/DG_RANS_T_junction.png)](https://www.youtube.com/shorts/G43xtVfk_iU)|

[back](/LISFLOOD8.0.md)
