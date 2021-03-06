#### Mass balance output file (`.mass`)

This is a tabular text file in which each line is written at the interval specified by the item massint in the `.par` file. Each line has 12 columns that contain the following information: 

  - **Column 1.** `Time` The time in seconds at which the data was saved
  - **Column 2.** `Tstep` Time step specified in seconds, either by the user or automatically selected
  - **Column 3.** `MinTstep` Minimum time step used so far during the simulation in seconds
  - **Column 4.** `NumTsteps` Number of time steps since the start of the simulation
  - **Column 5.** `Area` Area inundated in square meter
  - **Column 6.** `Vol` Volume of water in the domain in cubic meter
  - **Column 7.** `Qin` Inflow discharge in cubic meter per second (from the open domain edges)
  - ****Column 8.** `Hds` Water depth at the downstream exit of the model domain in meter
  - **Column 9.** `Qout` Calculated outflow discharge at the downstream exit of the model domain in cubic meter per second
  - **Column 10.** `Qerror` Volume error per second in cubic meter per second
  - **Column 11.** `Verror` Volume error per mass interval (`massint` variable in the `.par` file) in cubic meter
  - **Column 12.** `Rain-(Inf+Evap)` Cumulative effect of infiltration, evaporation and rainfall over the simulation in 1000 cubic meters (not active in 2D simulations)
  
  
  [back](/Merewether3.md)
