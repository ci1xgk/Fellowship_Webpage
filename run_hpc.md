#### Running the Merewether test case on the HPC facilities of the University of Sheffied

Once the `lisflood` executable is generated, following the instructions within the ["_Compiling on The University of Sheffield HPC facilities_"](/compile_hpc.md), 
the model can be run on both [ShARC](https://docs.hpc.shef.ac.uk/en/latest/sharc/index.html) and [Bessemer](https://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html) clusters, by following the instructions below.

- **On Bessemer**

Create a directory for your test-case, here for example `merewether`, and place the input files of the Merewether test case in it. To run on interactive mode, first open an interactive seesion:

````bash
srun --pty bash -i
````

Go to `merewether` directory and enter the following commands (`<USER>` is the Bessemer account name):

````bash
/home/USER/LISFLOOD-FP/build/lisflood merewether-0p175m.par
````
By doing so, the simulation will start to run. 

It should be noted that in an interactive mode, the simulation stops once the session is closed. For long simulations, batch mode is a better option, using which the simulation will continue irrespective of disconnecting from the cluster.

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
##module load netCDF/4.6.2-iimpi-2019a

##env

##export LD_LIBRARY_PATH=$HOME/netcdf_build_gcc/release/lib:$LD_LIBRARY_PATH

##export LD_LIBRARY_PATH=/usr/local/packages/live/eb/netCDF/4.6.2-gompi-2019a/lib64/libnetcdf.so.13:$LD_LIBRARY_PATH

##srun --export=ALL ../../build/lisflood -v -gzip eden_5m.par 

/home/ci1ms/LISFLOOD-FP/build/lisflood -v carlisle_run1.par
````

To run the script go to `merewether` directory and enter the following command:

````bash
sbatch merewether.sh
````

To check the status of the batch runs, you can use the following commands:

````bash
squeue
squeue --user=USER --start
````

and to remove the jobs from queue:

````bash
scancel "JOB_ID"
````

[back](/Merewether3.md)
