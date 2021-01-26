#### Compiling on Windows

To compile LISFLOOD-FP on Windows, [Microsoft Visual Studio](https://visualstudio.microsoft.com/) and [CMake](https://cmake.org/) are required. By default, CMake is installed as part of the **Desktop development with C++** workloads, in the process of installing Visual studio. 

To compile the code either of MSVC (the default C++ compiler of Visual Studio) or [Intel C++ compilers](https://software.intel.com/content/www/us/en/develop/tools/oneapi/components/dpc-compiler.html) can be used, as explained below.

- **Using the MSVC compiler**

Launch Visual Studio and open `LISFLOOD-FP-trunk` as a local folder:

![image](/Figures/comp_win_1.png)
![image](/Figures/comp_win_2.png)

From *Configuration* drop-down list, choose the `msvc-x64-Debug` or `msvc-x64-Release`:

![image](/Figures/comp_win_3.png)

From *Build* menu click on *Rebuild All*:

![image](/Figures/comp_win_4.png)

After the compiling is finished a executable file, namely `lisflood.exe` will be generated in `\LISFLOOD-FP-trunk\out\build\msvc-x64-Debug` or `\LISFLOOD-FP-trunk\out\build\msvc-x64-Release` sub-directories (depending on the configuration used above). 


[back](/LISFLOOD8.0.md)
