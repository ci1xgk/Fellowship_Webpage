## Agent-based food-pedestrian simulator 

The flood-pedestrian simulator is implementend within [FLAMEGPU](http://www.flamegpu.com), a computational platform for the simulation of multiple agent interactions on CUDA Cores for parallel processing on Graphical Processing Units (GPUs). It involves dynamic and bidirectional coupling across pedestrian-agents and flood-agents ([Shirvani et al. 2020](https://arxiv.org/abs/1908.05232)). 

Pedestrian-agents are continuous so they can change their coordinates and their population. Their walking patterns are based on the social force model that accounts for the movements of each individual and by modelling the interaction between individuals to derive forces that avoid collisions with neighbours. The motion of pedestrian-agents is also governed by by a global path planning model represented by a grid of discrete agents, navigation-agents, forming a navigation map. The navigation map encodes the features of the walkable area necessary for the individuals’ way-finding decision, e.g. terrain obstacles and walls that need to be avoided as the individuals navigate and vector fields providing navigation to key destinations. Multiple pedestrian agents can be present at the same time over one mutual navigation agent as they are of continuous type ([Shirvani et al. 2020](https://arxiv.org/abs/1908.05232)). 

Flood-agents are discrete agents that are coincident with the grid of navigation agents. Each flood-agent stores its position, terrain properties in terms of height and Manning’s roughness parameter, and the states of the floodwater variables in terms of water depth and velocity components. A non-sequential computation for a hydrodynamic model is used to allow all flood-agents to dynamically updates the states of floodwater variables at the same time (i.e. in parallel). The information stored in the pedestrian-agents and in the flood-agents is dynamically passed between them through the navigation-agents that act as shared communication interfaces (see Section 2.5 in [Shirvani et al. 2020](https://arxiv.org/abs/1908.05232)).


### Verification of the simualtor's two-way coupling capability
The two-way coupling ability of the simulator has been assessed for a hypothetical case study of a flood shopping centre considering two cases (details in [Shirvani et al. 2020](https://arxiv.org/abs/1908.05232)): 

* an evacuation case involving 1000 pedestrians evacuating toward a safe emergency exit, with _with_/_without_ an advanced flood warning; 

* an intervention case exploring the miminum of _responder_ pedestrians required to safely deploy a temporary defence in response to an advanced warning. 

Simulations illustrating the capabilites of the simualtor for five flooding scenarios can be found in this [YouTube video](https://www.youtube.com/watch?v=NCToADh39dQ). Scenarios 1-3 demonstrates how people dynamically response to the emergent flood and scenarios 4-5 demonstrates how people intervention to deploy a temporary barrier can reduce the flood intensity upstream of the emergency exit: 

Scenario 1. Considers a low-risk flood event without any early evacuation planning. People escape to a safe haven as a response to instantaneous evacuation order given by imaginary police officers once they observe the flood water propagating.

Scenario 2. Considers an extreme flood event without any early evacuation planning. People escape once they observe the flood water propagating. Some people get trapped into water and wait for help.

Scenario 3. Considers an early evacuation planning subjected to a flood event. 

Scenario 4. Considers emergency responders making a barrier made of sandbags in front of water flow to obstruct the water flowing towards the escape area. This model runs for a less severe flooding event in which sandbagging can be considered as an effective temporary action. 

Scenario 5. Considers sandbagging during an extreme case of flooding. 


### Ongoing work
The flood-pedestrian simulator has been augmented with more sophisticated behaviour rules for governing pedestrians' variable walking speeds and instability states in floodwater, and considering difference age, gender and body sizes ([Shirvani et al 2020](https://iwaponline.com/jh/article-abstract/22/5/1078/75432/Agent-based-modelling-of-pedestrian-responses?redirectedFrom=fulltext)). Work is also ongoing to set up and apply the simulator for a real case study of a flood-prone and congested urban area to more realistically explore its potential in planning evacuation and interventions.  


### Accessing the simualtor
The flood-pedestrain simualtor has been ported to the compute facility of [DAFNI](https://dafni.ac.uk/project/flood-people-simulator/), where it can be used from a user-friendly graphical interface and informed by a detailed user guide. We are very grateful for the portability support provided by DAFNI to make the simulator available to the wider community and easy-to-use by non-experts. The project of porting the simulator to DAFNI was smooth, timely and stress-free! Also, upon project completion, we were provided with a demonstration of how the simulator can be run from the user-friendly graphical interface of DAFNI. Thanks DAFNI! 


[back](./)
