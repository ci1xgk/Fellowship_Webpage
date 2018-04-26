![Image](Fig_1G.jpg)





### 1. Contact and acknowledgments 
The development of SEAMLESS is currently led by [Georges Kesserwani](https://www.sheffield.ac.uk/civil/staff/academic/gk) supported by an EPSRC Fellowship Scheme. The science and thinking behind the development of SEAMLESS is owed to following research grants: 
- Jan. 2018 - Mar. 2023, EPSRC Fellowship Scheme, “Smart forecasting: joined-up flood forecasting (FF) infrastructure with uncertainties”, funder ID: “EP/R007349/1”. 
- Mar. 2014 - Jul 2015, EPSRC First Grant Scheme, “Unified flood model with optimal zooming and linking at multiple scales”, funder ID: “EP/K031023/1”. 
- Aug. 2013 - Feb. 2014, DAAD Short-Term Grant, “Transforming flood risk modelling: collaborative research schedule with RWTH Aachen”, funder ID: “A1372005”.





![Image](Fig_2G.jpg)


### 2. Rationale
The need to better forecast and model flooding is of strategic importance to society and science. Policy-makers continue to desire more accurate and comprehensive flood warning maps to issue for public protection against flood events. Hydraulic consultancy and software industry firms still aspire to achieve significantly greater intelligence, reliability, coverage and functionality in their next-generation of hydraulic models, which can particularly obviate manual labour for excessive user iterations in building and running flood models, better control scaling effects due to inter-regional dependencies and more efficiently forecast uncertainty propagation. Aligned with these needs, scientists and engineers across many research communities still seek to develop a modelling framework that is “intelligent” and “holistic”, in the sense of being:
- Adaptable (able to embed and self-select a cascade of scales) 
- Reliable and efficient (to ensure a high-quality answer, in as rapid a time as possible)
- Versatile (applicable to solve a wide/compound range of physical scales and/or domains)
- Comprehensive (inform on numerical-model error and/or physical uncertainty propagation)


![Image](Fig_3G.jpg)



### 3. Approach
Multi-Wavelets are augmented forms of wavelets which allow precise, bi-directional, multiscale analysis. Construction of Multi-Wavelets on a mother basis function yields sets of inner bases that have local and nonoverlapping supports at each scale level, but which are globally nested across all scale levels. The power of such multiscale bases lies in their ability to decompose and reconstruct the scales of a given signal relevant to physical and/or statistical modelling data. Although popular in signal and image processing applications, the use of wavelets for flood forecasting is still in its infancy. The idea behind SEAMLESS-WAVE is exploit the versatile properties of Multi-Wavelets, by capitalising on their simultaneous ability to:
- Unambiguously detect and separate localised dominant flow and terrain features on locally nested adaptive grids, thereby providing a tool for intrinsic resolution decision-making; 
- Be adapted as local basis functions, which allows to increase polynomial accuracy in local storage and evolution of the modelling data; 
- Perform multi-scale analysis for accessing, upscaling and downscaling the modelling information across various spectrum of resolution involved in the adaptive grid; 
- Further apply/expand the deterministic model formulation for informing on the statistics of uncertainty propagations due to uncertain inputs in an entirely compatible framework. 


### 4. The team and collaborators 
The current team involves researchers working at the interface between applied mathematics, hydraulic modelling and science fields, which include the following people: 
- Georges Kesserwani, Research Fellow at the University of Sheffield 
- James Shaw, Research Associate at the University of Sheffield
- Mohammad Kazem Sharifian, PhD student at the University of Tabriz 
- Janice Lynn Agoy, PhD student at the University of Sheffield
- Mohammad Shirvani, PhD student at the University of Sheffield

We are happy that the following scientists have agreed to serve on our steering committee and to provide scientific guidance:
- Jennifer Ryan, University of East Anglia
- Chris Keylock, Loughborough University
- Paul Bates, University of Bristol
- Onno Bokhove, University of Leeds
- Domenico Bau, University of Sheffield 


### 5. Publications
#### Journal papers
G. Kesserwani, J.L. Ayog and D. Bau (2018). _Discontinuous Galerkin formulation for 2D hydrodynamic modelling:
trade-offs between theoretical complexity and practical convenience_. Computer Methods in Applied Mechanics and Engineering, *under review*. 

M.K. Sharifian, G. Kesserwani and Y. Hassanzadeh (2018). _A discontinuous Galerkin approach for conservative modeling of fully
nonlinear and weakly dispersive wave transformations_. Ocean Modelling, **125**, 61-79.

#### Conference papers
G. Kesserwani, M.K. Sharifian and J. Shaw. _Adaptive multi-scale shallow flow model: a wavelet-based formulation_. 13th International Conference on Hydroinformatics (HIC 2018), July 01-07, Palermo, Italy. 

J.L. Ayog and G. Kesserwani. _A well-balanced second-order discontinuous Galerkin reformulation for shallow water modelling_. 13th International Conference on Hydroinformatics (HIC 2018), July 01-07, Palermo, Italy. 


### 6. Activities

### 7. Documentation and downloads 




![Image](Fig_4G.jpg)

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column



