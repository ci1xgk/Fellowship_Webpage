#Efficient and accurate flood simulations using wavelet-based adaptivity

Flood plains are often many square kilometers, but the flow of water in a flood event frequently depends on small-scale topographic features, particularly for urban flood events.  As such, flood simulations must represent many square kilometers with a resolution of a metre or smaller.  Conventional flood simulations are performed on a static, uniform grid, but this becomes computationally prohibitive when the simulation area is very large and the finest resolution is very small since the resultant grid has many millions of cells.  Adaptive flood simulations reduce the computational burden by using dynamic, non-uniform grids to capture the important features of the topography and the flow.  Where the topography or flow are smooth, adaptive methods can coarsen the grid and reduce the total number of cells.

Traditional adaptivity methods can introduce simulation errors through the interpolation of flow data that occurs on the dynamically adaptive mesh ([Caviedes-Voullième and Kesserwani 2015](https://doi.org/10.1016/j.advwatres.2015.09.016)).  These errors can result in inaccurate predictions of flood extent, water depth and flow velocity.  Traditional adaptivity methods typically have several parameters that practitioners must tune for each case study to minimise adaptivity errors.

Wavelet- and multiwavelet-based adaptivity methods offer a number of advantages over traditional methods:

* (multi)wavelet theory provides a strong mathematical foundation
* the adaptive mesh and the flow data are treated as one and dynamically update together
* there is only one user-specified parameter which directly controls adaptivity error

The SEAMLESS-WAVE project uses a (multi)wavelet approach for adaptive flood modelling.  The first-order finite volume model (FV1) is combined with [Haar wavelets](https://en.wikipedia.org/wiki/Haar_wavelet) to produce the Haar-FV1 (HFV1) model.  Similarly, the second-order discontinuous Galerkin model (DG2) is combined with Alpert multiwavelets ([Alpert 1993](https://doi.org/10.1137/0524016)) to produce the multiwavelet-DG2 (MWDG2) model.  The one-dimensional FV1, DG2, HFV1 and MWDG2 hydrodynamic models have been assessed for a range of academic tests and results have been compared against flume experiments (full details will be available in Kesserwani et al. 2019, AWR).  These experiments demonstrate that:

1. the adaptive HFV1 and MWDG2 models preserve the degree of accuracy and robust behaviour of the underlying FV1 and DG2 models;
2. the HFV1 and MWDG2 models are computationally efficient compared to their FV1 and DG2 counterparts on uniform grids, especially when the flow and topography are smooth;
3. the MWDG2 is about 20 times faster than DG2, and MWDG2 can achieve the same high accuracy as DG2 with computation time lower than FV1.

A two-dimensional MWDG2 model is being formulated and testing of this model is already underway.  The two-dimensional MWDG2 model has been measured to be about 50 times faster than DG2 without compromising accuracy or robustness.  Work is ongoing to validate the MWDG2 model for benchmark tests and real-world case studies.
