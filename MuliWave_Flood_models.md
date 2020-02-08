## Wavelet-based solvers that self-automate grid-resolution size

Flow of water in a flood event frequently depends on small-scale topographic features, particularly for urban flood events.  As such, flood simulations must represent many square kilometers with a resolution of a metre or smaller.  Conventional flood simulations are performed on a static, uniform grid, but this becomes computationally prohibitive when the simulation area is very large and the finest resolution is very small since the resultant grid has many millions of cells.  Adaptive flood simulations reduce the computational burden by using dynamic, non-uniform grids to capture the important features of the topography and the flow.  Where the topography or flow are smooth, adaptive methods can coarsen the grid and reduce the total number of cells.

Traditional adaptivity methods can introduce simulation errors through the interpolation of flow data that occurs on the dynamically adaptive mesh ([Caviedes-Voullième and Kesserwani 2015](https://doi.org/10.1016/j.advwatres.2015.09.016)).  These errors can result in inaccurate predictions of flood extent, water depth and flow velocity.  Also, these methods are inflexible to practitioners, given the need to tune several parameters for each case study and to alliviate error propagation across different grid-resolution patches.

(Multi)wavelet-based adaptivity methods offer a number of advantages over traditional methods:

* they provides rigorous transform for upscaling and downscaling modelled data disperate resolution scales  
* the adaptive mesh and the modelled flow data are treated as one entity
* there is only one user-specified parameter which directly controls adaptivity error

We have been developping (multi)wavelet approaches for adaptive flood modelling.  The first-order finite volume model (FV1) is combined with [Haar wavelets](https://en.wikipedia.org/wiki/Haar_wavelet) to produce the Haar-FV1 (HFV1) model.  Similarly, the second-order discontinuous Galerkin model (DG2) is combined with Alpert multiwavelets ([Alpert 1993](https://doi.org/10.1137/0524016)) to produce the multiwavelet-DG2 (MWDG2) model.  The one-dimensional FV1, DG2, HFV1 and MWDG2 hydrodynamic models have been assessed for a range of academic tests and results have been compared against flume experiments ([Kesserwani et al. 2019](https://doi.org/10.1016/j.advwatres.2019.04.019)).  These numerical experiments demonstrate that: 

* the adaptive HFV1 and MWDG2 models can preserve the same degree of accuracy and robustness of the underlying FV1 and DG2 models; 
* the HFV1 and MWDG2 models boost efficiency compared to their FV1 and DG2 counterparts on uniform grids;
* the MWDG2 allows to achieve the same high-accuracy of the expensive DG2 but at a computational cost that is lower than FV1.

A two-dimensional MWDG2 model is under development and testing, with prelimary results indicating that it offers even more efficiency gain reative to the 1D case ([Kesserwani et al. 2019](https://doi.org/10.1016/j.advwatres.2019.04.019))! Work is also ongoing to validate the 2D-MWDG2 and 2D-HFV1 models for industrial benchmark tests and real-world case studies to assess its real potential for flood modelling applications.



[back](./)
