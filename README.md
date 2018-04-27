![Image](Fig_1G.jpg)

[1. Rationale](Rationale.md)


### 2. Approach
Multi-Wavelets are augmented forms of wavelets which allow precise, bi-directional, multiscale analysis. Construction of Multi-Wavelets on a mother basis function yields sets of inner bases that have local and nonoverlapping supports at each scale level, but which are globally nested across all scale levels. The power of such multiscale bases lies in their ability to decompose and reconstruct the scales of a given signal relevant to physical and/or statistical modelling data. Although popular in signal and image processing applications, the use of wavelets for flood forecasting is still in its infancy. The idea behind SEAMLESS-WAVE is exploit the versatile properties of Multi-Wavelets, by capitalising on their simultaneous ability to:
- Unambiguously detect and separate localised dominant flow and terrain features on locally nested adaptive grids, thereby providing a tool for intrinsic resolution decision-making; 
- Be adapted as local basis functions, which allows to increase polynomial accuracy in local storage and evolution of the modelling data; 
- Perform multi-scale analysis for accessing, upscaling and downscaling the modelling information across various spectrum of resolution involved in the adaptive grid; 
- Further apply/expand the deterministic model formulation for informing on the statistics of uncertainty propagations due to uncertain inputs in an entirely compatible framework. 


![Image](Fig_3G.jpg)


### 3. Research team and partners
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

The SEAMLESS-WAVE project is undertaken with the awareness and support of relevant industrial and govermental partners, which include: 
- The UK Environment Agency
- BMT-WBM, providers of the “TUFLOW” software
- CH2M, suppliers of the “Flood Modeller Suite”
- Innovyze, providers of the “InfoWorks2D” product
- XP Solutions, providers of the “XPFLOOD” software
- DHI Group, suppliers of the “MIKE FLOOD” software
- Sheffield City Council flood and water management team


### 4. Publications
#### Journal papers
G. Kesserwani, J.L. Ayog and D. Bau (2018). _Discontinuous Galerkin formulation for 2D hydrodynamic modelling:
trade-offs between theoretical complexity and practical convenience_. Computer Methods in Applied Mechanics and Engineering, *under review*. 

M.K. Sharifian, G. Kesserwani and Y. Hassanzadeh (2018). _A discontinuous Galerkin approach for conservative modeling of fully
nonlinear and weakly dispersive wave transformations_. Ocean Modelling, **125**, 61-79.

#### Conference papers
G. Kesserwani, M.K. Sharifian and J. Shaw. _Adaptive multi-scale shallow flow model: a wavelet-based formulation_. 13th International Conference on Hydroinformatics (HIC 2018), July 01-07, Palermo, Italy. 

J.L. Ayog and G. Kesserwani. _A well-balanced second-order discontinuous Galerkin reformulation for shallow water modelling_. 13th International Conference on Hydroinformatics (HIC 2018), July 01-07, Palermo, Italy. 


### 5. Activities
GK to report

### 6. Documentation 
JS to report


### 7. Contact and acknowledgments 
The development of SEAMLESS is currently led by [Georges Kesserwani](https://www.sheffield.ac.uk/civil/staff/academic/gk) supported by an EPSRC Fellowship Scheme. The science and thinking behind the development of SEAMLESS is owed to following research grants: 
- Jan. 2018 - Mar. 2023, EPSRC Fellowship Scheme, “Smart forecasting: joined-up flood forecasting (FF) infrastructure with uncertainties”, funder ID: “EP/R007349/1”. 
- Mar. 2014 - Jul 2015, EPSRC First Grant Scheme, “Unified flood model with optimal zooming and linking at multiple scales”, funder ID: “EP/K031023/1”. 
- Aug. 2013 - Feb. 2014, DAAD Short-Term Grant, “Transforming flood risk modelling: collaborative research schedule with RWTH Aachen”, funder ID: “A1372005”.


![Image](Fig_4G.jpg)
