### Dam-break wave over an urban area

By default, when including the `dg2` item in the `.par` file, LISFLOOD-FP considers running the DG2 solver without local slope limiting. Using the DG2 variant without local slope limiting (DG2-NL) is recommended for flood modelling applications with smooth to gradual flows over terrain with medium to high roughness, i.e. Manning coefficient > 0.02 [(Ayog et al. 2021)](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858). This choice is appropriate to more efficiently simulate shockless flood flows featured in most flood modelling applications, as the localisation procedure for slope limiting doubles runtime cost [(Ayog et al. 2021)](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858). 


For simulations involving either fine-scale spatio-temporal features, flow discontinuities and very smooth terrain surface, the DG2 variant with local slope limiting (DG2-LL) is recommended. It can be activated by adding `limiteslopes` alongside `dg2` in the `.par` file. In the following, the relevance of choosing DG2-LL is demonstrated for the *"Complex dam-break wave interacting with an idealised urban district"* test case reported in [Soares-Frazao and Zech (2008)](https://www.tandfonline.com/doi/abs/10.3826/jhr.2008.3164). Based on the dimensions reported, a DEM file was built, using QGIS, at a resolution of 0.02 m × 0.02 m.

The study area is an experimental flume with a smooth surface (Manning coefficient of 0.01) that is shown in the upper panel of the figure below. It includes twenty-five 0.3 m × 0.3 m square blocks placed with a gap of 0.1 m between each block. The wall barrier with a gate initially separates a water depth of 0.4 m from a water depth of 0.011 m. When the gate is rapidly opened, a dam-break wave is formed and flows swiftly to collide with the blocks. 


![Image](/Figures/Fig6G.jpg)


Both the DEM file and the initially wet dam-break condition were pre-processed to form DG2-related initial conditions, as detailed within the case study of [*"Merewether urban flooding"*](/Merewether.md). DG2-NL and DG2-LL simulations were run up to 10 s. An alternative simulation was run using the well-established MUSCL-FV2 solver, widely used by many research groups and for industrial-scale modelling applications, e.g. [TUFLOW-HPC](https://wiki.tuflow.com/index.php?title=HPC_Introduction).  

The simulated spatial profiles of the water depth and velocity are extracted along the centreline y = 0.2 m (red line in the figure, upper panel) at two output times, 5 s and 6 s, shown in the middle and bottom panel of the figure, respectively. The water depth profiles are located on the left part of the figure, whereas the right side shows the velocity profiles.

DG2-LL shows a closer alignment with the profiles produced by the MUSCL-FV2 solver, both of which show a good agreement with all the observed data. The DG2-NL, though in good agreement with some of the observed data, leads to noisy profiles that in many instances locally diverge from the profiles produced by DG2-LL and MUSCL-FV2.
 


[back](/LISFLOOD8.0.md)
