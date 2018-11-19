## Interactive and dynamic agent-based flood model on FLAME-GPU for studying human-flood systems


This project is carried by Mohammad Shirvani as a part of his PhD studentship at the University of Sheffield supervised by [Dr Georges Kesserwani](https://www.sheffield.ac.uk/civil/staff/academic/gk) and [Dr Paul Richmond](http://paulrichmond.shef.ac.uk/)

The motivation of this research is grounded on demonstrating the merit of using a new technology for creating an agent-based hydraulic model and its inherent capability to capture complex interactions with other types of agents in flood-related researches.

The current model is built upon [FLAME-GPU](http://www.flamegpu.com), which is a computer modelling framework for building and running agent-based simulations on Graphics Processing Units (GPUs).

Please contact Mohammad Shirvani (mshirvani1@sheffield.ac.uk) for further details. 

### What is it?

This model is a tool for simulating flooding events and social behaviour of people in one unified shared modelling framework in which two-way interactions between people and water flows can be analysed dynamically at the level of individuals.

This model is developed by combining two major components: 
1.	A well-established hydraulic model (Liang et al., 2007) based on Finite Volume (FV) solution of the two-dimensional Shallow               Water Equations (SWEs) capable of simulating complex features of water flows over an initially dried and/or wet area with bed             friction contribution.
      
 2.	A pedestrian model, created by Richmond and Romano (2008) and developed by Karmakharm et al (2012) on FLAME-GPU and capable of             producing a simulation of a crowd of people walking aimlessly and/or directed towards a goal in a given area.

### What is the aim?

The aim of this model is to: 

1. Provide fast flood simulations respectful to physics of water flows 
2. Provide an alive flood water simulation which can be modified dynamically by the actions of emergency responders 
3. Eliminate the need of employing external hydraulic software packages to obtain hydrodynamic datasets for feeding ABMs so as to map between water flow characteristics and real-world systems, e.g. social behaviour

All of which above reinforce a greater goal for enabling end-users to conduct real-time spatio-temporal evaluation of human-flood systems from a synaptic perspective, such as assessing the efficiency of implementing temporary flood defence measures or evacuation planning strategies at individual level.

### What does it can do? (so far)

It can:
-	run for large crowd of people integrated with flood water simulation in real time 
-	dynamically change the status of people exposed to water flows by modifying their walking velocities and showing whether they are alive, dead, or trapped with respect to water depth and velocity, which is which based on morality and vulnerability functions defined by EA/DEFRA
-	simulate evacuation of people running toward a safe haven/emergency exit
-	provide a possibility to expose people to flood water under ‘with’ or ‘without’ early evacuation planning measures
-	simulate emergency responders deploying temporary defences
-	optionally observe the effect of human body on water flows
-	run for different scenarios with different inputs and initial conditions without the need for further compilation 
-	run on any PC/laptop with a graphics card

#### What are the outputs?
-	Real-time visualisation of both walking humans and water propagation
-	Statistics and numerical outputs relevant to people and water flow status and characteristics can be customised and outputted after each iteration, both as text files and/or on console command screen (for real-time statistics)

Note 1: in current model, the information of people and hydrodynamic data as well as structural measures is outputted on console command window.

Note 2: any customised outputting form required further compilation after changing to the desirable format

### How does it work?

The model is inherently agent based, created on specification of three different types of agents: flood agents, navigation agents, and pedestrian agents.

- Flood agent: is the representative of a computational cell in a 2D mesh-based grid which discretise the domain for solving SWE with the aim of FV method – they store the information of water flows (i.e. depth and velocity)

- Navigation agent: is the representative of a cell in a grid over which people can walk – they store the textures and features of the area and also the location of entrances and exits, provided for pedestrian agents to follow

- Pedestrian agent: is the representative of an individual based on random walk behaviour – they store their goal destination for people-to-area interaction, impulsion force variables for people-to-people interactions, and their status variables for people-to-flood interaction

Since the model aims parallel computations, all the above-mentioned agents existing in the domain are evolved at the same time with respect to others’ states within each iteration of the simulations

### How to use it?
1.	Generating initial condition for hydraulic model (bed data, water depth, water velocity), and navigation map (defining the area, walls, obstacles, exits) based on the topographic features defined by hydraulic model.

2.	Assigning parameters, such as number of people, pedestrian emission rate for exists, size of the flood domain, boundary condition, etc. 

3.	Run

### An example

This example is based on simulation of a number of people wandering in a shopping centre, assuming they are moving between a number of malls. Suddenly an unexpected flooding occurs and they start to evacuate the area immediately. Everyone is guided by imaginary police officers directing them towards a hypothetical safe haven located in northwest corner of the shopping centre. 

Watch a demo of the model on YouTube for 5 different scenarios: [CLICK](https://www.youtube.com/watch?v=NCToADh39dQ)

•	First, to demonstrate the response of people to flood water, response of people to a harmless and a very dangerous flash floods with and without early evacuation planning is simulated

Model 1: shows a harmless flood event without any early evacuation planning. People escape to a safe have as a response to instantaneous evacuation order given by imaginary police officers once they observe the flood water propagating. 

Model 2: shows a very extreme flood event without any early evacuation planning. People escape once they observe the flood water propagating. Some people get trapped into water and wait for help.

Model 3: simulates an early evacuation planning in this hypothetical shopping centre subjected to a flood event. 

•	Second, to demonstrate potential influences of individual’s actions with the purpose of mitigating the extent of flooding or obstructing flowing water, it is assumed that a number of emergency responders build up a sandbag barrier in front of water flows to protect the area where the safe haven is located.

Model 4: emergency responders make a barrier made of sandbags in front of water flow to obstruct the water flowing towards a safe zone (escape area). This model runs for a less severe flooding event in which sandbagging can be considered as an effective temporary action. 

Model 5: Sandbagging is demonstrated for an extreme case of flooding. 
Also, a demo of how the body of people is considered as moving obstacles (showing two-way interactions of water and people at the same time) can be seen [here](https://www.youtube.com/watch?v=qGE5ZNiCLaY).

### To whom it may benefit most?
All practitioners in flood-related researches, particularly in the field of flood-risk management, flood resilience, evacuation planning, emergency responses, flood mitigation measures.

### Further developments in near future

-	Develop the model to adopt ASCII files as inputs for real-world applications
-	Embedding viability and vulnerability functions
-	Embedding stability and instability functions for people (Jonkman and Vrijling, 2008) and structures (as well as buildings)
-	Defining random height and weight to people based on their ages
-	Defining random walking velocity within a range of average walking and running speed (with respect to peoples’ age)

### References

Richmond Paul, Romano Daniela(2008), Agent Based GPU, a Real-time 3D Simulation and Interactive Visualisation Framework for Massive Agent Based Modelling on the GPU, Proceedings of International Workshop on Supervisualisation 2008 (IWSV08), Part of ICS08), Kos Island, Greece. June 2008.

Karmakharm Twin, Richmond Paul (2012), "Large Scale Pedestrian Multi-Simulation for a Decision Support Tool", in Proc. of Theory and Practice of Computer Graphics (TPCG) 2012, 13-14th September 2012, Rutherford Appleton Laboratory, UK

Liang, Q., Zang, J., Borthwick, A.G.L, Taylor, P.H. (2007) Shallow flow simulation on dynamically adaptive cut cell quadtree grids, International Journal for Numerical Methods in Fluids , 53(12): 1777-1799

Jonkman, S. N. and Vrijling, J. K. (2008), Loss of life due to floods, J. Flood Risk Management, 1: 43-56.




[back](./)
