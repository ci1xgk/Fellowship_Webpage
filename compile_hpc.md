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

Go to `libnuma-dev` directory and install it (specify `<PATH>` as the directory to install libnuma):

````bash
./autogen.sh
./configure
make
make install DESTDIR=<PATH>
````

Load CMake:

````bash
module load CMake/3.13.3-GCCcore-8.2.0
````

To use dynamic rainfall, e.g. for Eden flooding test case, NetCDF must be loaded:

````bash
module load netCDF/4.6.2-gompi-2019a
````

To run LISFLOOD-FP on GPU, the CUDA toolkit should also be loaded:

````bash
module load CUDA/10.1.105-GCC-8.2.0-2.31.1 
````

Go to `LISFLOOD-FP` directory and run `cmake`, by pointing to libnuma install directory (denoted by `<PATH>`):

````bash
cmake -S . -B build -DNUMA_ROOT=<PATH>
cmake --build build
````

By doing so, the `lisflood` executable will be generated in the `build` directory.

- **On ShARC**

Compiling on ShARC follows the same procedure as Bessemer. The only difference is the NetCDF module, which is not available on ShARC and must be installed manually.

Launch an interactive session on a worker node using the command:

````bash
qrsh
````

Clone the repository: 

````bash
git clone https://github.com/SEAMLESS-WAVE/LISFLOOD-FP.git
````

Clone libnuma package:

````bash
git clone https://github.com/numactl/numactl.git
````

Go to `libnuma-dev` directory and install it (specify `<PATH>` as the directory to install libnuma):

````bash
./autogen.sh
./configure
make
make install DESTDIR=<PATH>
````

Load CMake:

````bash
module load dev/cmake/3.17.1/gcc-8.2
````

To use dynamic rainfall, e.g. for Eden flooding test case, NetCDF library is required. 

````bash
module load netCDF/4.6.2-gompi-2019a
````

To run LISFLOOD-FP on GPU, the CUDA toolkit should also be loaded:

````bash
module load libs/CUDA/10.1.243/binary 
````

Go to `LISFLOOD-FP` directory and run `cmake`, by pointing to libnuma install directory (denoted by `<PATH>`):

````bash
cmake -S . -B build -DNUMA_ROOT=<PATH>
cmake --build build
````

By doing so, the `lisflood` executable will be generated in the `build` directory.

[back](/LISFLOOD8.0.md)
