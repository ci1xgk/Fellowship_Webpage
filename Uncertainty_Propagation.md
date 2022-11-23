## Efficient uncertainty propagation approaches 

Accurately simulating flood events is hard because computer models must be initialised with error-prone data that is derived from real-world measurements of river discharge, topographic elevation and surface roughness properties ([Di Baldassarre and Uhlenbrook 2012](https://doi.org/10.1002/hyp.8226)).  Measurement errors are compounded by data post-processing and model calibration procedures meaning that model inputs are inexact and uncertain.

Deterministic flood models naively assume that input data is exact, leading to misplaced confidence in model predictions that are overly precise.  In contrast, probabilistic flood simulations account for input uncertainties in order to produce a probabilistic solution of the flow.  Probabilistic solutions are normally produced using a Monte Carlo method, such as the [GLUE method](https://doi.org/10.1002/hyp.3360060305), that runs a deterministic model many times with randomised input data.  Monte Carlo simulations typically require many thousands of model runs to adequately capture the range of possible outcomes.  As a result, Monte Carlo simulations are very demanding on computer resources, and many sources of uncertainty must be neglected to make probabilistic simulations feasible ([Neal et al. 2013](https://doi.org/10.1002/hyp.9572)).

Compared to Monte Carlo methods, Polynomial Chaos methods can quantify uncertainty much more efficiently by reducing the number of iterations required. Existing hydrodynamic modelling studies found that Polynomial Chaos methods are about 50&ndash;100 times faster than Monte Carlo methods ([Ge et al. 2008](https://doi.org/10.1061/(ASCE)0733-9429(2008)134:12(1732)); [El Mo&ccedil;ayd et al. 2018](https://doi.org/10.1007/s10666-017-9582-2)), but these studies were limited to idealised cases (e.g. smooth topography, frictionless flows in fully-wet domains).

We have been developing probabilistic finite volume formulations based on _intrusive_ and _nonintrusive_ stochastic approaches ([Xiu 2009](http://sci.utah.edu/publications/xiu09/Xiu_CiCP2009.pdf)), with the aim to make them robust for hydraulic modelling applications ([Shaw and Kesserwani 2020](https://ascelibrary.org/doi/10.1061/%28ASCE%29HY.1943-7900.0001705); [Shaw et al. 2020](https://www.sciencedirect.com/science/article/abs/pii/S0309170819306281)). A intrusive/nonintrusive approach extends/samples a deterministic hydrodynamic solver to directly/iteratively propagate forward input uncertainties. Multiscale wavelet functions are used to span multidimensional uncertainty space, enabling to transfer the validity of robustness treatments from the underlying deterministic solver and to improve capturing of fine-scale variations in joint probability distributions. 

The _wavelet-based nonintrusive approach_ is found to be more flexible for use with existing deterministic solver, for propagating _multiple uncertainties in practical hydrodynamic modelling applications_. 


### Sampling-based methods, with code accessiblity 
Nonintrusive software toolkits for obtaining probabilistic flood maps from existing deterministic models have been developed. The toolkits implement modern uncertainty quantification methods (e.g. [Bhaduri et al. 2018](https://doi.org/10.1016/j.jcp.2018.06.003)) with the aim of accelerating probabilistic flood models by using alternatives to the Standard Monte Carlo method (SMC).

The alternatives consider Latin Hypercube Sampling (LHS), Adaptive Stratified Sampling (ASS), Quasi Monte Carlo (QMC) and Haar Wavelet Expansion (HWE) as they can capture all types of histogram distributions. The code to test and run these alternatives for three realistic case studies with many uncertain inputs can be found on [Zenodo](https://zenodo.org/record/7050213).


[back](./)
