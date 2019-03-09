## Simulating dynamic human-flood responses

This model is being developed through the PhD project of Mohammad Shirvani (mshirvani1@sheffield.ac.uk) at the University of Sheffield supervised by [Dr Georges Kesserwani](https://www.sheffield.ac.uk/civil/staff/academic/gk) and [Dr Paul Richmond](http://paulrichmond.shef.ac.uk/). It is built upon [FLAME-GPU](http://www.flamegpu.com), which is a computer platform for building and running agent-based simulations on Graphics Processing Units (GPUs). The motivation behind this development is to enable a flexible human-flood modelling framework that captures the complex and bidirectional interactions between flooding and people. 

### About
This model is a tool for simulating flooding events and social behaviour of people in the same modelling framework, where two-way interactions between people and water flows can be analysed dynamically. The modelling framework intertwines two major components: 
* A robust hydraulic solver based on finite volume numerical solution of the two-dimensional shallow water equations, which is capable of simulating complex features including shock formation, wetting and drying processes, etc ([Wang et al. 2011](https://www.tandfonline.com/doi/abs/10.1080/00221686.2011.566248)).
* A pedestrian model for the simulation of a crowd of people walking aimlessly and/or directed towards a goal in a given area ([Richmond and Romano 2008](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.144.734), [Karmakharm et al. 2012](https://diglib.eg.org/handle/10.2312/LocalChapterEvents.TPCG.TPCG12.041-044)).

### Aim and scope
This modelling framework is being developped and progressively validated with a view to: 
* afford real-time flood simulations at urban-to-neighborhood scale (GPU-accelerated),  
* map dynamically the impact of flood water on people states and of people actions to reduce flood risk, and  
* apply this new tool to study realistic scenarios of local community resilience to flood hazard emergencies.   

### Dynamic coupling capability
The modelling framework is able to run for a large crowd of people integrated with flood water simulation in real time, while providing information on the possible changes in individual people states as they get exposed to flooding using morality and vulnerability metrics defined by EA/DEFRA. It is designed to also provide real-time visualisation of both walking humans and flood water propagation, satistics relevant to risk-to-people hazard mapping as time evolves and throughout the spatial flooding domain. 

The dynamic coupling capability of the framework has been validate over a series of hypothetical human-flood interactiong scenarios demonstrating promising capability to:  
* simulate evacuation of people running toward a safe emergency exit, with ‘with’ or ‘without’ early evacuation planning measures
* simulate emergency responders deploying temporary defences and the associated changes in flood water flow reduction
* simulate different inflow conditions without the need for extra compilation and run on any PC/laptop with a graphics

### Functionality 
The modelling framework is entirely agent-based, and requires specification of three different types of agents: flood agents, navigation agents, and pedestrian agents (Shirvani et al. 2019).
- Flood agents: represent computationals cell in a 2D mesh-based grid which discretise the domain for hydraulic solver. Each flood agent stores the information of water flows (i.e. depth and velocity).
- Navigation agents: represent a cell in a grid over which people can walk – they store the textures and features of the area and also the location of entrances and exits, provided for pedestrian agents to follow.
- Pedestrian agents: represent individuals randomly walking  – they store their goal destination for people-to-area interaction, impulsion force variables for people-to-people interactions, and their status variables for people-to-flood interaction.

Since the model does parallel computations, all the above-mentioned agents existing in the domain are evolved at the same time with respect to others’ states within each iteration of the simulations. A single run requires the following: 
1. Generate initial condition for hydraulic model (bed data, water depth, water velocity), and navigation map (defining the area, walls, obstacles, exits) based on the topographic features defined by hydraulic model.
2. Assigning parameters, such as number of people, pedestrian emission rate for exists, size of the flood domain, boundary condition.

### Flooded shopping centre example (hypothetical)  
This is a hypothetical example to demonstrate the dynamic coupling capabibility of the modelling framework. It involves a number of people wandering in a shopping centre, assuming they are moving between a number of malls. Suddenly an unexpected flooding occurs and they start to evacuate the area immediately. Everyone is guided by imaginary police officers directing them towards a safe haven located in northwest corner of the shopping centre. Simulation of this example can be found on a a [YouTube video](https://www.youtube.com/watch?v=NCToADh39dQ) considering 5 different scenarios (1-3 on the response of people to flood water and 4-5 on how people actions can change the course of the flood):
1. Of harmless flood event without any early evacuation planning. People escape to a safe have as a response to instantaneous evacuation order given by imaginary police officers once they observe the flood water propagating. 
2. Of an extreme flood event without any early evacuation planning. People escape once they observe the flood water propagating. Some people get trapped into water and wait for help.
3. Of an early evacuation planning subjected to a flood event. 
4. Of emergency responders making a barrier made of sandbags in front of water flow to obstruct the water flowing towards the escape area. This model runs for a less severe flooding event in which sandbagging can be considered as an effective temporary action. 
5. Sandbagging is demonstrated for an extreme case of flooding. 

There is also a video demo of how the body of people is considered as moving obstacles (showing two-way interactions of water and people at the same time) can be seen [here](https://www.youtube.com/watch?v=qGE5ZNiCLaY).

### Ongoing developments
-	Develop the model to adopt ASCII files as inputs for real-world applications
-	Embedding viability and vulnerability functions
-	Embedding stability and instability functions for people (Jonkman and Vrijling, 2008) and structures (as well as buildings)
-	Defining random height and weight to people based on their ages
-	Defining random walking velocity within a range of average walking and running speed (with respect to peoples’ age)


[back](./)
