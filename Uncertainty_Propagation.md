## Efficient uncertainty quantification for probabilistic flood simulations

Accurately simulating flood events is hard because computer models must be initialised with error-prone data that is derived from real-world measurements of river discharge, topographic elevation and surface roughness properties ([Di Baldassarre and Uhlenbrook 2012](https://doi.org/10.1002/hyp.8226)).  Measurement errors are compounded by data post-processing and model calibration procedures meaning that model inputs are inexact and uncertain.

Deterministic flood models naively assume that input data is exact, leading to misplaced confidence in model predictions that are overly precise.  In contrast, probabilistic flood simulations account for input uncertainties in order to produce a probabilistic solution of the flow.  Probabilistic solutions are normally produced using a Monte Carlo method, such as the [GLUE method](https://doi.org/10.1002/hyp.3360060305), that runs a deterministic model many times with randomised input data.  Monte Carlo simulations typically require many thousands of model runs to adequately capture the range of possible outcomes.  As a result, Monte Carlo simulations are very demanding on computer resources, and many sources of uncertainty must be neglected to make probabilistic simulations feasible ([Neal et al. 2013](https://doi.org/10.1002/hyp.9572)).

Compared to Monte Carlo methods, Polynomial Chaos methods can quantify uncertainty much more efficiently by reducing the number of iterations required.
Existing hydrodynamic modelling studies found that Polynomial Chaos methods are about 50&ndash;100 times faster than Monte Carlo methods ([Ge et al. 2008](https://doi.org/10.1061/(ASCE)0733-9429(2008)134:12(1732)); [El Mo&ccedil;ayd et al. 2018](https://doi.org/10.1007/s10666-017-9582-2)), but these studies have been limited to idealised, one-dimensional flows.
We are working to remove these limitations and move towards increasingly realistic probabilistic models.
So far, we have developed a one-dimensional probabilistic model including the following robust properties:
* a well-balanced mathematical formulation to avoid spurious wave generation over uncertain topography,
* a dynamic wetting-and-drying strategy for representing uncertain regions that may be wet or dry,
* a representation of uncertain surface roughness,
* a robust treatment of subcritical and supercritical flow regimes with uncertain regime transitions

This probabilistic model is based on a so-called _intrusive_ approach which involves a probabilistic reformulation of the underlying equations.
An intrusive approach allows for dynamic optimisations that have the potential for the greatest efficiency gains, but the mathematical reformulation precludes the use of existing deterministic models.

In the near future, we will develop a _nonintrusive_ software toolkit for obtaining probabilistic flood maps from existing deterministic models.
The toolkit will implement modern uncertainty quantification methods ([Bhaduri et al. 2018](https://doi.org/10.1016/j.jcp.2018.06.003)) with the aim of accelerating probabilistic flood models by an order of magnitude.

[back](./)
