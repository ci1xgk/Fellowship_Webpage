#### Compiling on Linux

To compile LISFLOOD-FP on Linux, the following packages are required:

- [**GCC compiler**](https://gcc.gnu.org/), which is by default installed in most of Linux distributions, like Ubuntu 
- [**CMake**](https://cmake.org/)
- [**libnuma-dev**](https://github.com/numactl/numactl), which is required for NetCDF output and dynamic rainfall support

As an example, on Ubuntu, CMake and libnuma-dev can be installed, by entering the following commands in terminal:

````bash
sudo snap install cmake --classic
sudo apt install libnuma-dev libnetcdf-dev
````

Then open a terminal at in the root `lisflood-fp` directory:

````bash
cmake -S . -B build
cmake --build build
````

The `lisflood` executable is written to the `build` directory.
If `libnuma` is installed in a non-standard location, use

````bash
cmake -S . -B build -DNUMA_ROOT=<path>
cmake --build build

[back](/LISFLOOD8.0.md)
