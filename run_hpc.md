#### Merewether test case on the HPC facilities of the University of Sheffied

LISFLOOD-FP can be compiled on both [ShARC](https://docs.hpc.shef.ac.uk/en/latest/sharc/index.html) and [Bessemer](https://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html) clusters, by following the instructions below.

- **On Bessemer**

First create a directory for your test-case in `testing` directory, and upload the input files. To run the DG2 solver, first the DEM slope files should be created. To do this, in an interactive session, run the following commands (put your bessemer account name in `USER`):

````bash
/home/USER/LISFLOOD-FP/build/generateDG2DEM TESTCASE.par
````

To run on an interactive session, use the following command:

````bash
/home/USER/LISFLOOD-FP/build/lisflood -v -gzip TESTCASE.par
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
