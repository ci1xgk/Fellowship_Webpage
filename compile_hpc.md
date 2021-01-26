#### Compiling on The University of Sheffield HPC facilities

LISFLOOD-FP can be compiled on both [ShARC](https://docs.hpc.shef.ac.uk/en/latest/sharc/index.html) and [Bessemer](https://docs.hpc.shef.ac.uk/en/latest/bessemer/index.html) clusters, by following the instructions below.

- **On Bessemer**

Launch an interactive session on a worker node using the command:

````bash
srun --pty bash -i
````

Clone the repository: 

````bash
git clone https://github.com/SEAMLESS-WAVE/LISFLOOD-FP.git
````

Clone libnuma package:

````bash
git clone https://github.com/numactl/numactl.git
````

Go to `libnuma-dev` directory and install it:

````bash
./autogen.sh
./configure
make
make install DESTDIR=/path/to/install/libnuma/directory
````

Load CMake:

````bash
module load CMake/3.13.3-GCCcore-8.2.0
````

Load NetCDF:

````bash
module load netCDF/4.6.2-gompi-2019a
````

To run LISFLOOD-FP on GPU, the CUDA toolkit should also be loaded:

````bash
module load CUDA/10.1.105-GCC-8.2.0-2.31.1 
````

Go to `LISFLOOD-FP` directory and run `cmake`, by pointing to libnuma install directory:

````bash
cmake -S . -B build -DNUMA_ROOT=/home/USER/libnuma/usr/local
cmake --build build
````

By doing so, the `lisflood` executable will be generated in the `build` directory.

[back](/LISFLOOD8.0.md)
