## Second-order discontinous Galerkin (DG2) flood model

Finite volume flood model formulations are well-established in research and industrial communities (e.g. [CLAWPACK-5](http://www.clawpack.org/) and [TUFLOW](https://www.tuflow.com/) software packages). These formulations have adopted the Godunov-type principle ([Toro and Garcia-Navarro 2007](https://www.tandfonline.com/doi/abs/10.1080/00221686.2007.9521812)) given its advantage to automatically capture all types of water flow transitions: store the flow and terrain data _element-wise_ using a _piecewise-constant approximation_ and evolve flow data by means of inter-elemental spatial flux exchange, by incorporating an [approximate Riemann solver](https://en.wikipedia.org/wiki/Riemann_solver#Approximate_solvers). Formulations that instead use a _piecewise-planar approximation_ are shown to improve flood simulation predictions, such as for modelling applications that are limited to coarse mesh resolution ([Kesserwani and Wang (2014)](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2013WR014906); [Sanders and Schubert 2019](https://www.sciencedirect.com/science/article/pii/S0309170818308698)). 

A second-order discontunuous Galerkin (DG2) approach has been used to augment the finite volume formulation to storing and evolving element-wise _piecewise-planar approximation_. The so-called _slope_decoupled_ DG2 form has been developed ([Kesserwani et al. 2018](https://www.sciencedirect.com/science/article/pii/S004578251830389X)) with a four-fold purpose: 

* simplify the complexity of the caluclation stencil of the general DG2 form to make it compatible with the stencil commonly used in grid-based hydraulic models, while retaining its ability to acheive second-order accurate predictions;

* reduce the number of operations per element from 32 to 12, offering 2.6 times more efficient calculations than the general DG2 form; 

* reliably integrate terrain data and wetting-and-drying using _piecewise-plannar_ data at the level required to simulate real-world flooding scenarios; 

* provide a _reference_ uniform mesh DG2 solver required to develop 2D version of the [Wavelet-based solvers that self-automate grid-resolution size](./MuliWave_Flood_models.md).  


### Ongoing work and code accessibility 
The performance of the robust DG2 flood model is currently being assessed against a range of industry standard flood models, over the [UK Environment Agency benchmark tests](https://consult.environment-agency.gov.uk/engagement/bostonbarriertwao/results/appendix-6---neelz--s.---pender--g.--2013--benchmarking-the-latest-generation-of-2d-hydraulic-modelling-packages.-bristol_environment-agency.pdf), and for real-world case studies. 

The sloped-decoupled DG2 flood model ([Kesserwani et al. 2018](https://www.sciencedirect.com/science/article/pii/S004578251830389X)) has been integrated onto the grid-based [LISFLOOD-FP](http://www.bristol.ac.uk/geography/research/hydrology/models/lisflood/) solver. There is a standard version to run it on multi-core CPU, and a developing CUDA version to also run the DG2 flood model on GPUs. 
