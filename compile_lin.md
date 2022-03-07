#### Compiling on Linux

To compile LISFLOOD-FP on Linux, the following packages are required:

- [**GCC compiler**](https://gcc.gnu.org/), which is by default installed in most Linux distributions, like Ubuntu 
- [**CMake**](https://cmake.org/)
- [**libnuma**](https://github.com/numactl/numactl) 
- [**libnetcdf**](https://www.unidata.ucar.edu/software/netcdf/), which is required for NetCDF output and dynamic rainfall support
- [**CUDA toolkit**](https://developer.nvidia.com/cuda-toolkit), required to run GPU-accelerated solvers

As an example, on Ubuntu, CMake, libnuma and libnetcdf can be installed, by entering the following commands in the terminal:

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

#### Updates on compiling for RedHat linux distribution (Thanks to [Justin R. Davis](https://vivo.ufl.edu/display/n8101) from UFL)
While the compilation process explained above has been tested on Debian-based distributions like Ubuntu, a few ammendment might be required for compiling on RedHat-based distributions, notably, on old versions like [RHEL7](https://access.redhat.com/products/red-hat-enterprise-linux): 
- As RHEL7 only supports old versions of CMake and GCC, the following commands can be used to prepare the libraries and compile the CPU solvers 

````bash
yum -y install numactl-devel numactl-libs netcdf-devel cmake3 devtoolset-11
wget https://zenodo.org/record/4073011/files/LISFLOOD-FP-8.zip
unzip LISFLOOD-FP-8.zip
cd LISFLOOD-FP-trunk/
scl enable devtoolset-11 'cmake3 -S . -B build'
scl enable devtoolset-11 'cmake3 --build build'
````


[back](/LISFLOOD8.0.md)
