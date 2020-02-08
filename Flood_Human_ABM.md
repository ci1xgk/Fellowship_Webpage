## Agent-based food-pedestrian simulator 

Evacuation simulation models are useful to support flood risk management. Such models were developed for microscopic evacuation analysis of crowds of individuals at urban-scale for various purposes, e.g. emergency response management ([Lumbroso and Tagg 2011](http://eprints.hrwallingford.co.uk/508/)), evacuation route detection ([Bernardini et al. 2017](https://www.sciencedirect.com/science/article/pii/S1876610217346805)), and to assess the number of casualties to dam-break floods ([Lumbroso and Davison 2018](https://onlinelibrary.wiley.com/doi/full/10.1111/jfr3.12230)). Simulators of this type adopt agent-based models (ABM) that allow to analyse the responses of flooding receptor, such as people, cars or socio-economic impacts on the flooded enviroment. Most of existing ABM models are designed for _pre-evacuation_ planning purposes, with little consideration to the accumulated impacts arising from spatiotemproral interactions that could occur _during_ flooding.  

We have been developping a flood-pedestrian simulator that dynamically couples a hydrodynamic ABM to a navigation ABM, including walking pedestrian agents. This simulator is designed to:

* map the interactions occurring between in a crowd of walking individuals under immediate evacuation to realistic flooding conditions, thereby allowing to estimate flood hazard rating in realtime and at a miscroscopic scale; 

* plan pedestrian intervention strategies in reponse to an advanced flood warning, e.g. to decide when and where it is safe to robustly delopy a temorary sandbag barrier. 

The flood-pedestrian simulator is implemented in the [FLAME-GPU](http://www.flamegpu.com) platform for building and efficiently running agent-based simulations on Graphics Processing Units (GPUs). It couples dynamically:

* a fixed grid of flood agents that change their state based on the numerical solution of the two-dimensional shallow water equations ([Wang et al. 2011](https://www.tandfonline.com/doi/abs/10.1080/00221686.2011.566248)), to


* a fixed grid of navigation agents that include continous flow of pedestrian agents driven by a random walk behaviour rules ([Richmond and Romano 2008](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.144.734), [Karmakharm et al. 2012](https://diglib.eg.org/handle/10.2312/LocalChapterEvents.TPCG.TPCG12.041-044)).

The behaviour of the walking pedestrian agents is informed by the spatial and temporal changes in the states of the flood and navigation agents on the coupled grids. 


### Two-way coupling capability
The developing flood-pedestrian simulator ([Shirvani et al. 2019](https://arxiv.org/abs/1908.05232)) is able to run in real time with visualisation, while providing information on the possible changes in the pedestrian states based on the flood-to-people [Hazard Rating (HR) metric defined by the Enironment Agengy and DEFRA](http://randd.defra.gov.uk/Document.aspx?Document=FD2321_3436_TRP.pdf). Outputs of the simulator can also include flooding agent states as they evolve in time and throughout the spatial flooding domain. 

The two-way coupling ability of the simulator has been assessed for a hypothetical case study of a flood shopping centre considering two cases (details in [Shirvani et al. 2019](https://arxiv.org/abs/1908.05232)): 

* an evacuation case involving 1000 pedestrians evacuating toward a safe emergency exit, with _with_/_without_ an advanced flood warning; 

* an intervention case exploring the miminum of _responder_ pedestrians required to safely deploy a temporary defence in response to an advanced warning. 

Simulations exploring the capabilites of the simualtor for five flooding scenarios can be found in this [YouTube video](https://www.youtube.com/watch?v=NCToADh39dQ). Scenarios 1-3 demonstrates how people dynamically response to the emergent flood and scenarios 4-5 demonstrates how people intervention to deploy a temporary barrier can reduce the flood intensity upstream of the emergency exit: 

Scenario 1. Considers a low-risk flood event without any early evacuation planning. People escape to a safe haven as a response to instantaneous evacuation order given by imaginary police officers once they observe the flood water propagating.

Scenario 2. Considers an extreme flood event without any early evacuation planning. People escape once they observe the flood water propagating. Some people get trapped into water and wait for help.

Scenario 3. Considers an early evacuation planning subjected to a flood event. 

Scenario 4. Considers emergency responders making a barrier made of sandbags in front of water flow to obstruct the water flowing towards the escape area. This model runs for a less severe flooding event in which sandbagging can be considered as an effective temporary action. 

Scenario 5. Considers sandbagging during an extreme case of flooding. 


### Ongoing work
The flood-pedestrian simulator has been augmented to incorporate more realistic behaviour rules for the walking pedestrian in flood water. These include rules to account for their variable stability states, variable walking speed states, and different body sizes and height for the pedestrians ([Xia et al. 2014](https://iahr.tandfonline.com/doi/abs/10.1080/00221686.2013.875073); [Postacchini et al. 2018](https://drive.google.com/file/d/1Nhp6heNgwNHdtoEKvMdMvWZFaalTD7FJ/view); [Bernardini et al 2020](https://www.sciencedirect.com/science/article/pii/S0925753519321745)). 

Ongoing work also inclules evaluating the capability of the simulator to plan emergency evacuation and intervension responses for a real study site of a flood-prone area that is often populated by pedestrians. 

### Accessing the simualtor
A project has been approved to port the latest version of the flood-pedestrain simualtor onto [DAFNI](https://www.dafni.ac.uk/projects/), where it will be openly accessible. 


[back](./)
