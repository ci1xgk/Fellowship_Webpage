## Agent-based food-pedestrian model 

Evacuation simulation models are useful to support flood risk management. Such models were developed for microscopic evacuation analysis of crowds of individuals at urban-scale for various purposes, such as emergency response management ([Lumbroso and Tagg 2011](http://eprints.hrwallingford.co.uk/508/)), evacuation route finding ([Bernardini et al. 2017](https://www.sciencedirect.com/science/article/pii/S1876610217346805)), and assessing the number of casualties to violent flood types ([Lumbroso and Davison 2018](https://onlinelibrary.wiley.com/doi/full/10.1111/jfr3.12230)). Simulators of this type adopt agent-based models (ABM) to dynamically map the responses of flooding receptor, such as people or cars, in an urban enviroment. However, most of existing ABM models are designed for _pre-evacuation_ planning purposes and thus ignore the implications from dynamic spatiotemproral interactions that could have occured _during_ flooding.  

We have been developping a flood-pedestrian simulator that dynamically couples a hydrodynamic ABM to a navigation ABM, including walking pedestrian agents. This simulator is designed to:

* dynamically map the interactions occurring between in a crowd of walking individuals under immediate evacuation under mild and realistic flooding energency conditions, thereby allowing to estimate flood hazard rating in realtime and at a miscroscopic scale; 

* plan pedestrian intervention strategies if an advanced flood warning is issued, e.g. to decide when and where it is possible to safely and robustly delopy a temorary flood barrier. 

The flood-pedestrian simulator is implemented in the open source [FLAME-GPU](http://www.flamegpu.com) platform, ideal for building and efficiently running agent-based simulations on Graphics Processing Units (GPUs). It couples dynamically:

* a fixed grid of flood agents that change their state based on the numerical solution of the two-dimensional shallow water equations ([Wang et al. 2011](https://www.tandfonline.com/doi/abs/10.1080/00221686.2011.566248)), to


* a fixed grid of navigation agents that include continous flow of pedestrian agents driven by a random walk behaviour rules ([Richmond and Romano 2008](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.144.734), [Karmakharm et al. 2012](https://diglib.eg.org/handle/10.2312/LocalChapterEvents.TPCG.TPCG12.041-044)).

The behaviour of the walking pedestrian agents is informed by the spatial and temporal changes in the agent states on the coupled navigation and hydrodynamic grids. 


### Dynamic coupling capability
The modelling framework is able to run for a large crowd of people integrated with flood water simulation in real time, while providing information on the possible changes in individual people states as they get exposed to flooding using flood-to-people hazard rating metrics defined by EA/DEFRA. It is designed to also provide real-time visualisation of both walking humans and flood water propagation, satistics relevant to risk-to-people hazard mapping as time evolves and throughout the spatial flooding domain. 

The dynamic coupling of the framework has been assessed by a series of hypothetical flooding scenarios involving human-flood interactions demonstrating promising capability to (see the Illustrative example Section below):  
* simulate evacuation of people running toward a safe emergency exit, with ‘with’ or ‘without’ early evacuation planning measures
* simulate emergency responders deploying temporary defences and the associated changes in flood water flow reduction
* simulate different inflow conditions without the need for extra compilation and run on any PC/laptop with a graphics

### Functionality 
The modelling framework is entirely agent-based, and requires specification of three different types of agents: flood agents, navigation agents, and pedestrian agents (Shirvani et al. 2019).
- Flood agents represent computationals cell in a 2D mesh-based grid which discretise the domain for hydraulic solver. Each flood agent stores the information of water flows (i.e. depth and velocity).
- Navigation agents represent a cell in a grid over which people can walk – they store the textures and features of the area and also the location of entrances and exits, provided for pedestrian agents to follow.
- Pedestrian agents represent individuals randomly walking  – they store their goal destination for people-to-area interaction, impulsion force variables for people-to-people interactions, and their status variables for people-to-flood interaction.

Since the model does parallel computations, all the above-mentioned agents existing in the domain are evolved at the same time during a simulation. A single run requires defining: the initial condition for the hydraulic model (bed data, water depth, water velocity), the navigation map relative topographic features defined by hydraulic model (defining the area, walls, obstacles, exits), and parameters including the number of people, pedestrian emission rate for exists, size of the flood domain, boundary condition.

### Illustrative example (hypothetical shopping centre)  
This example aims to demonstrate the dynamic coupling capabibility of the modelling framework. It assumes a shopping centre inside which people are wandering, and then an unexpected flooding occurs and they start to evacuate immediately. People are assumed to be guided by imaginary police officers directing them towards a safe haven located in northwest corner of the shopping centre. Simulations illustrating people-flooding interactions for five different scenarios can be found in this [YouTube video](https://www.youtube.com/watch?v=NCToADh39dQ), where scenarios 1.-3. demonstrates how people dynamically response to the emergent flood and scenarios 4.-5. demonstrates how people actions can reduce the flood intensity in a desired area: 

1. Considers a low-risk flood event without any early evacuation planning. People escape to a safe haven as a response to instantaneous evacuation order given by imaginary police officers once they observe the flood water propagating.

2. Considers an extreme flood event without any early evacuation planning. People escape once they observe the flood water propagating. Some people get trapped into water and wait for help.

3. Considers an early evacuation planning subjected to a flood event. 

4. Considers emergency responders making a barrier made of sandbags in front of water flow to obstruct the water flowing towards the escape area. This model runs for a less severe flooding event in which sandbagging can be considered as an effective temporary action. 

5. Considers sandbagging during an extreme case of flooding. 

There is also a video demo of how the body of people is considered as moving obstacles (showing two-way interactions of water and people at the same time) can be seen [here](https://www.youtube.com/watch?v=qGE5ZNiCLaY).

### Ongoing developments
The human-flood modelling framework is being suported with the necessary developments to enable its applicability for real study sites to support flood resilience studies considering community responses. 



[back](./)
