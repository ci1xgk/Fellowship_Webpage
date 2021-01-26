#### Compiling on Linux

To compile LISFLOOD-FP on Linux, the following packages are required:

- [**GCC compiler**](https://gcc.gnu.org/), which is by default installed in most of Linux distributions, like Ubuntu 
- [**CMake**](https://cmake.org/)
- [**libnuma**](https://github.com/numactl/numactl) 
- [**libnetcdf**](https://www.unidata.ucar.edu/software/netcdf/), which is required for NetCDF output and dynamic rainfall support

As an example, on Ubuntu, CMake, libnuma and libnetcdf can be installed, by entering the following commands in terminal:

````bash
sudo snap install cmake --classic
sudo apt install libnuma-dev libnetcdf-dev
````

After installing the packages, open a terminal in `LISFLOOD-FP-trunk` directory, and enter the following commands:

````bash
cmake -S . -B build
cmake --build build
````

If libnuma is installed in a non-standard location, the following commands must be used, in which `<path>` denotes the installation directory of libnuma:

````bash
cmake -S . -B build -DNUMA_ROOT=<path>
cmake --build build
````
By doing so, the `lisflood` executable will be generated in the `build` sub-directory.

[back](/LISFLOOD8.0.md)
