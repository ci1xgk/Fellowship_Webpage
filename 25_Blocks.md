As the localisation procedure for slope limiting with DG2 doubles its runtime cost, and we recommend applying DG2 without local slope limiting (DG2-NL) for the majority of flood modelling applications involving gradually varied flows over rough terrain [(Ayog et al. 2021)](https://www.sciencedirect.com/science/article/abs/pii/S0022169420313858). 


The variant of the DG2 with local limiting (DG2-LL) comes in handy when simulating one or multiple shock waves over smooth terrain including sharp obstacles. This is demonstrated for case study of a complex dam-break wave interacting with an idealised urban district. The date for this case study are avaialbe in [Soares-Frazao and Zech (2008)](https://www.tandfonline.com/doi/abs/10.3826/jhr.2008.3164). 


The study area is an experimental flume with smooth surface (Manning coefficient of 0.01) that is shown in the figure below, upper panel. It includes twenty-five 0.3 m × 0.3 m square blocks placed with a gap of 0.1 m between each block. The wall barrier with a gate initially separates two water bodies with a depth of 0.4 m and 0.011 m respectively. When the gate is rapidly opened, a dam-break wave is formed and flows swiftly to collide with the blocks. 


![Image](/Figures/Fig6G.jpg)


DG2-NL and DG2-LL simulations were run up to t = 10 s on a mesh with a grid size of 0.02 m. An alternative simulation was run using the well-established MUSCL-FV2 solver, widely used by many research groups and forms the basis of various hydraulic modelling packages, such as [TUFLOW-HPC](https://wiki.tuflow.com/index.php?title=HPC_Introduction).  


The simulated spatial profiles of the water depth and velocity are extracted along the centreline y = 0.2 m (red line in the figure, upper panel) at two output times, 5 s and 6 s, shown in the middle and bottom panel in the figure, respectively. The water depth profiles are illustrated on the left while the right sides show the velocity profiles.  
DG2-LL shows a closer alignment with the profiles produced by the MUSCL-FV2 solver, both of which showing a good agreement with all the observed data. The DG2-NL, though in good agreement with some of the observed data, leads to noisy profiles that in many instances locally diverge from the profiles produced by DG2-LL and MUSCL-FV2. 


[back](./)
