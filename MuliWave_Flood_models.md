## Smart and flexible multiresolution solvers

Flow of water in a flood event frequently depends on small-scale topographic features, particularly for urban flood events. Flood simulations must represent many square kilometers with a resolution of a metre or smaller. Conventional flood simulations are performed on a static, uniform grid, but this becomes computationally prohibitive when the simulation area is very large and the finest resolution is very small since the resultant grid has many millions of cells.  

Adaptive flood simulators (e.g. [TUFLOW-HPC](https://wiki.tuflow.com/index.php?title=HPC_Introduction) *Quadtree*) reduce the computational burden by using dynamic, non-uniform grids to capture the important features of the topography and the flow.  Where the topography or flow are smooth, adaptive methods can coarsen the grid and reduce the total number of cells.

Conventional mesh-resolution adaptivity methods can introduce simulation errors through heursitic interpolation of flow data that occurs on the dynamically-adaptive mesh ([Caviedes-Voullième and Kesserwani 2015](https://doi.org/10.1016/j.advwatres.2015.09.016)). These errors can result in inaccurate predictions of flood extent, water depth and flow velocity (e.g. see Fig. 14b in [Kesserwani and Liang 2012](https://www.sciencedirect.com/science/article/pii/S0309170811002181)).  Also, these methods are inflexible to practitioners, given the need to tune several parameters for each case study and to alleviate error propagation across different grid-resolution patches.

Multiwavelets bases are naturally compatible with the piecewise-polynomial bases shaping the local solution strucutre wihtin the Discontinuous Galerkin (DG) method, hence also the Finite Volume (FV) method. Multiwavelets' [multiresolution analysis](https://en.wikipedia.org/wiki/Multiresolution_analysis) enables to dynamically form an adaptive solution that overcomes the majority of the above-mentioned shortcomings of conventional adaptive mesh-resolution adaptivity methods ([Kesserwani et al. 2019](https://doi.org/10.1016/j.advwatres.2019.04.019); [Kesserwani and Sharifian 2020](https://www.sciencedirect.com/science/article/pii/S0309170820303079)). Namely, the multiwavelet-based adaptivity offers a solid mathematical foundation to design smart and flexible multiresolution models that: 

* deploy rigorous transforms for inherent encoding/decoding of the modelled data across cascades of resolution scales 

* only need one user-specified parameter to both directly controls adaptivity error and sensibly decide where to refine and where to coarsen 


We have been developping and investigating (multi)wavelet-based adaptive approaches for flood modelling ([Caviedes-Voulliéme and Kesserwani 2015](10.1016/j.jcp.2015.08.030); [Gerhard et al. 2015](10.1016/j.advwatres.2015.09.016)). The first-order finite volume model (FV1) is combined with [Haar wavelets](https://en.wikipedia.org/wiki/Haar_wavelet) to produce the Haar-FV1 (HFV1) model. Similarly, the second-order discontinuous Galerkin model (DG2) is combined with Alpert multiwavelets ([Alpert 1993](https://doi.org/10.1137/0524016)) to produce the multiwavelet-DG2 (MWDG2) model. A complete description of how one-dimensional (1D) hydrodynamic MWDG2/HFV1 solvers can be formulated is found in [Kesserwani et al. (2019)](https://doi.org/10.1016/j.advwatres.2019.04.019), with a diagnostic analysis on its potential for real-world problems and links to access the relevant codes and data. 

To design two-dimensional (2D) hydrodynamic MWDG2/HFV1 solvers that are robust for real-world applications and gain even more efficiency in 2D compared to the 1D case [(Caviedes-Voulliéme et al. 2020)](doi.org/10.1016/j.advwatres.2020.103559), a radical redesign has been proposed [(Kesserwani and Sharifian 2020)](https://www.sciencedirect.com/science/article/pii/S0309170820303079). This redesign adapts multiwavelets theory to fit the setting whereby 2D solvers are efficient and robust for real-world applications, and is significant in demonstrating how multiwavelet-based 2D solvers can be made operational for 2D flood inundation modelling. 


### Ongoing work and code accessibility 
Work is ongoing to explore the potential of different (multi)wavelets types for pre-processing of high resolution DEMs into a multiresolution mesh; and, to explore different numerical solver responses on the multiresolution mesh for real-world case studies with medium- to -large spatial coverages. Work is also ongoing to deliver a fully GPU-resident MWDG2/HFV1 solvers.  

Details on how to access and run educative 1D and 2D codes are documented within [Kesserwani et al. (2019)](https://doi.org/10.1016/j.advwatres.2019.04.019) and [Kesserwani and Sharifian (2020)](https://www.sciencedirect.com/science/article/pii/S0309170820303079). 


[back](./)
