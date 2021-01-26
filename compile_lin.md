#### Compiling on Linux

To compile LISFLOOD-FP on Linux, the following packages are required:

- [**GCC compiler**](https://gcc.gnu.org/): This is by default installed in most of Linux distributions, like Ubuntu 
- **CMake**, which can be installedd following the instructions [here](https://cmake.org/install/)

Ensure a recent version of CMake is installed.
Also ensure `libnuma-dev` is installed and, for NetCDF output and dynamic rainfall support, ensure `libnetcdf-dev` is also installed.  On Ubuntu:

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
