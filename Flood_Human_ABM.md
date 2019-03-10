## Simulating dynamic human-flood responses

This model is being developed through the PhD project of Mohammad Shirvani (mshirvani1@sheffield.ac.uk) at the University of Sheffield supervised by [Dr Georges Kesserwani](https://www.sheffield.ac.uk/civil/staff/academic/gk) and [Dr Paul Richmond](http://paulrichmond.shef.ac.uk/). It is built upon [FLAME-GPU](http://www.flamegpu.com), which is a computer platform for building and running agent-based simulations on Graphics Processing Units (GPUs). The motivation behind this development is to enable a flexible human-flood modelling framework that captures the complex and bidirectional interactions between flooding and people. 

### About
This model is a tool for simulating flooding events and social behaviour of people in the same modelling framework, where two-way interactions between people and water flows can be analysed dynamically. The modelling framework intertwines two major components: 
* A robust hydraulic solver based on finite volume numerical solution of the two-dimensional shallow water equations, which is capable of simulating complex features including shock formation, wetting and drying processes, etc ([Wang et al. 2011](https://www.tandfonline.com/doi/abs/10.1080/00221686.2011.566248)).
* A pedestrian model for the simulation of a crowd of people walking aimlessly and/or directed towards a goal in a given area ([Richmond and Romano 2008](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.144.734), [Karmakharm et al. 2012](https://diglib.eg.org/handle/10.2312/LocalChapterEvents.TPCG.TPCG12.041-044)).

### Aim and scope
This modelling framework is being developped and progressively validated aiming to: 
* afford real-time flood simulations at urban-to-neighborhood scale (GPU-accelerated),  
* map dynamically the impact of flood water on people states and of people actions to reduce flood risk, and  
* apply this new tool to study realistic scenarios of local community resilience to flood hazard emergencies.   

### Dynamic coupling capability
The modelling framework is able to run for a large crowd of people integrated with flood water simulation in real time, while providing information on the possible changes in individual people states as they get exposed to flooding using flood-to-people hazard rating metrics defined by EA/DEFRA. It is designed to also provide real-time visualisation of both walking humans and flood water propagation, satistics relevant to risk-to-people hazard mapping as time evolves and throughout the spatial flooding domain. 

The dynamic coupling of the framework has been assessed by a series of hypothetical flooding scenarios involving human-flood interactions demonstrating promising capability to:  
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
