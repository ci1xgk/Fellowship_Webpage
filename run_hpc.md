#### Running the Merewether test case on the HPC facilities of the University of Sheffied

Once the `lisflood` executable is generated, following the instructions within the ["_Compiling on The University of Sheffield HPC facilities_"](/compile_hpc.md), 
the model can be run on both [ShARC](https://docs.hpc.shef.ac.uk/en/latest/sharc/index.html) and [Bessemer](https://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html) clusters, by following the instructions below.

- **On Bessemer**

Create a directory for your test-case, here for example `merewether`, and place the input files of the Merewether test case in it. To run on interactive mode, first open an interactive session:

````bash
srun --pty bash -i
````

Go to `merewether` directory and enter the following commands (`<USER>` is the Bessemer account name):

````bash
/home/USER/LISFLOOD-FP/build/lisflood merewether-0p175m.par
````
By doing so, the simulation will start to run. 

It should be noted that in an interactive mode, the simulation stops once the session is closed or connection to cluster is lost. For long simulations, batch mode is a better option, using which the simulation will continue irrespective of disconnecting from the cluster.

To run in a batch mode, create a shell script in `merewether` directory, for example named `merewether.sh`, and put the following lines in it:

````bash
#!/bin/bash
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=16
#SBATCH --mem=8G
#SBATCH --time=6000
#SBATCH --job-name=carlisle5m
#SBATCH --mail-user=m.sharifian@sheffield.ac.uk

module load netCDF/4.6.2-gompi-2019a

/home/ci1ms/LISFLOOD-FP/build/lisflood merewether-0p175m.par
````

The different options to use in the shell script are explained [here](https://docs.hpc.shef.ac.uk/en/latest/bessemer/slurm.html).


Once the shell script is edited, to run the script go to `merewether` directory and enter the following command:

````bash
sbatch merewether.sh
````

After submitting the job, to check the status of the batch runs, the following commands can be used:

````bash
squeue --user=<USER> --start
````

where `<USER>` is the user name used to connect to Bessemer. 

- **On ShARC**

TBA

[back](/Merewether3.md)
