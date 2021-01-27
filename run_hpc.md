#### Running the Merewether test case on the HPC facilities of the University of Sheffied

Once the `lisflood` executable is generated, following the instructions within the ["_Compiling on The University of Sheffield HPC facilities_"](/compile_hpc.md), 
the model can be run on both [ShARC](https://docs.hpc.shef.ac.uk/en/latest/sharc/index.html) and [Bessemer](https://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html) clusters, by following the instructions below.

- **On Bessemer**

Create a directory for your test-case, here for example `merewether`, and place the input files of the Merewether test case in it. To run on interactive mode, first open an interactive seesion:

````bash
srun --pty bash -i
````

Then enter the following commands (`<USER>` is the Bessemer account name):

````bash
/home/USER/LISFLOOD-FP/build/lisflood merewether-0p175m.par
````

To run in a batch mode, create a shell file, and run it as:

````bash
sbatch shell_file.sh
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
