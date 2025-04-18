## Food-pedestrian simulator 

The flood-pedestrian simulator is implementend within [FLAMEGPU](http://www.flamegpu.com), a computational platform for the simulation of multiple agent interactions on CUDA Cores for parallel processing on Graphical Processing Units (GPUs). It involves dynamic and bidirectional coupling across pedestrian-agents and flood-agents ([Shirvani et al. 2021](https://onlinelibrary.wiley.com/doi/10.1111/jfr3.12695)). 

Pedestrian-agents are continuous so they can change their coordinates and their population. Their walking patterns are based on the social force model that accounts for the movements of each individual and by modelling the interaction between individuals to derive forces that avoid collisions with neighbours. The motion of pedestrian-agents is also governed by a global path planning model represented by a grid of discrete agents, navigation-agents, forming a navigation map. The navigation map encodes the features of the walkable area necessary for the individuals’ way-finding decision, e.g. terrain obstacles and walls that need to be avoided as the individuals navigate and vector fields providing navigation to key destinations. Multiple pedestrian agents can be present at the same time over one mutual navigation agent as they are of continuous type ([Shirvani et al. 2021](https://onlinelibrary.wiley.com/doi/10.1111/jfr3.12695)). 

Flood-agents are discrete agents that are coincident with the grid of navigation agents. Each flood-agent stores its position, terrain properties in terms of height and Manning’s roughness parameter, and the states of the floodwater variables in terms of water depth and velocity components. A non-sequential computation for a hydrodynamic model is used to allow all flood-agents to dynamically updates the states of floodwater variables at the same time. The information stored in the pedestrian-agents and in the flood-agents is dynamically passed between them through the navigation-agents that act as shared communication interfaces (see Section 2.5 in [Shirvani et al. 2021](https://onlinelibrary.wiley.com/doi/10.1111/jfr3.12695)).


### Verification of the simualtor's two-way coupling capability
The two-way coupling ability of the simulator has been evaluated for a hypothetical case study of a flooded shopping centre ([Shirvani et al. 2021](https://onlinelibrary.wiley.com/doi/10.1111/jfr3.12695)), for an evacuation scenario of 1000 pedestrians to a safe emergency exit, with _with_/_without_ an advanced flood warning; and an intervention scenario to find out the miminum _responder_ pedestrians and height of a flood-fighting barrier for safe and robust deployment. 

In addition to the demonstration provided in [Shirvani et al. (2021)](https://onlinelibrary.wiley.com/doi/10.1111/jfr3.12695), simulation demos are provided in this [video](https://www.youtube.com/watch?v=NCToADh39dQ) for five modelling cases. 'Model 1' to 'Model 3' simulate people evacuating during a flood; whereas, 'Model 4' and 'Model 5' simulate people intervening to deploy a flood-fighting barrier upstream of the emergency exit. More specifically:  

* 'Model 1' covers a low-risk flood event without any early evacuation planning. People escape to the emergency exit, in response to an order given by an authority onsite as soon as they observe the flooding propagation.

* 'Model 2' covers an extreme flood event without an early evacuation plan. People escape once they observe the flooding propagation, while some people get trapped in floodwater and wait for help.

* 'Model 3' illustrates an early evacuation planning assuming a prior knowledge of flooding propagation.  

* 'Model 4' shows emergency responders deploying a sandbag-barrier prior to a low-risk flooding to obstruct water flow from reaching the espcape area. 

* 'Model 5' study the feasiblity of the the sandbaging process for an extreme flooding case.


### Pedestrian-agent rules 
The flood-pedestrian simulator has been augmented to consider an enhanced level of heterogeneity for individual pedestrian-agent characteristics (e.g. such as age, gender, weight [Shirvani et al. 2020](https://iwaponline.com/jh/article-abstract/22/5/1078/75432/Agent-based-modelling-of-pedestrian-responses?redirectedFrom=fulltext)), to incorporate empirically based variable movement speeds and stability patterns, and to become applicable for flood emergency evacuation planning in **outdoor spaces** where individuals' destination choice and individual risk perception have great influence on the simulation outcomes ([Shirvani and Kesserwani 2021](https://nhess.copernicus.org/articles/21/3175/2021/nhess-21-3175-2021.html)). 

The performance of the simulator was demonstrated for an indoor shopping centre (synthetic case study) and for a flood-prone urban site in the city of Sheffield, near a football stadium ofen congested by pedestrians (see the video in [Shirvani 2021](https://av.tib.eu/media/51547). 

The simulator was also demonstrated over a public engagement activity ([Festival of the Mind, 2020](http://staging-festivalofthemind.kinsta.cloud/2020/futurecade/planning-for-the-next-great-flood/)), through a dynamic 4D visulaisation tool. 


### Accessibility and users' run guide
The first version of the flood-pedestrian simualtor is available on the UK compute facility of [DAFNI](https://dafni.ac.uk/project/flood-people-simulator/), where it can be used from a user-friendly graphical interface. We are very grateful for the portability support provided by DAFNI to make the simulator available to the wider community and easy-to-use by non-experts. The project of porting the simulator to DAFNI was smooth, timely and stress-free. Also, upon project completion, DAFNI provided us with a demonstration of how the simulator can be run from their user-friendly graphical interface. Thanks DAFNI! 

The latest version of the simuator ([Shirvani and Kesserwani 2021](https://nhess.copernicus.org/articles/21/3175/2021/nhess-21-3175-2021.html)), including a detailed run guide is openly available on [GitHub](https://github.com/SahebSh/flood-pedestrian-simulator/tree/v1.3.0) and can also be accessed from [Zenodo](https://zenodo.org/record/4564288#.Yh9QMOjP25d). Thanks Saheb for the great work, leading to your PhD award! 


[back](https://www.seamlesswave.com/Developments.html)
