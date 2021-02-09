#### Performance metrics for flood extent prediction 

Different metrics are used to evaluated different aspects of a flood model's performance, compared to the reference or benchmark data [(Hoch and Trigg, 2019)](https://iopscience.iop.org/article/10.1088/1748-9326/aaf3d3). For example, when the focus of comparison is the surface water elevation at a certain location, the RMSE (root-mean-square error) or the bias (mean difference between water levels) is usually used to compare water elevations predicted by the model (or **model data**) to in-situ water elevation measurments (or **benchmark data**). 

To validate the performance of a flood model in predicting the flood extent, three metrics are commonly used within the hydraulic modeling community, namely Hit Rate (H), False Alarm Ratio (F), and Critical Success Index (C) [(Wing et al. 2017)](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2017WR020917). In the process of comuting these metrics, model data is the flood extent predicted by the model, while benchmark data refers to either surveyed extent of the flooding event or the flood extent from a reference flood modeling simulation.  

These metrics compare the benchmark data cells _vs._ model data cells one by one, in a binary (wet or dry) manner, and sum up them as four states shown in the table and schematic figure below.  

   |  | **Wet in Benchmark Data (B1)** | **Dry in Benchmark Data (B0)** |
   | :---         | :---      | :--- |
   | **Wet in Model Data (M1)**   | M1B1      | M1B0    |
   | **Dry in Model Data (M0)**   | M0B1      | M0B0    |

![image](/Figures/metrics4.svg)

M1B1 denotes the total number of cells that are wet in both of the benchmark and model data, M0B0 denotes the total number of cells that are dry in both of the benchmark and model data, M1B0 denotes the total number of cells that are wet in the model data but dry in the benchmark data, and M0B1 denotes the total number of cells that are dry in the model data but wet in the benchmark data. 


The **Hit Rate (H)** is a simple measure that assess the proportion of wet benchmark data cells that was also predicted as wet by the model:

````
H = M1B1 / (M1B1 + M0B1)
````

H ranges from 0 (none of the wet benchmark data cells are wet in the model data) to 1 (all wet benchmark data cells are wet in the model data). Since this metric only considers the area with wet benchmark data cells, it only examines the model’s tendency toward underprediction of the flood extent.

The **False Alarm Ratio (F)** indicates the proportion of wet model data cells that are not wet in the benchmark data:

````
F = M1B0 / (M1B0 + M1B1)
````

This metric gives an idea of whether the model has the tendency to overpredict flood extent. In this sense, a cell that is wet in model data but dry in benchmark data is regarded as *false alarm*. Therefore, F can range from 0 (none of the model data cells are false alarms) to 1 (all of the model data cells are false alarms). 

The **Critical Success Index (C)** extends on both H and F to create a combined criteria that accounts for both underprediction and overprediction:

````
C = M1B1 / (M1B1 + M0B1 + M1B0)
````

where scores range from 0, showing no match between benchmark and model data, to 1 , which shows the perfect match between benchmark and model data.

#### Python script to compute the metrics

A simple Python script, named `metrics.py` is included in the post-processing directory, to compute these statistical metrics. The script requres GDAL package for reading the data. The process of computing the metrics is here described as an example for the Carlistle 2005, urban flooding test case.

To run the script, two ASCII rastar files with the same resolution and extent, one for benchmark data and the other for the model data. The model data is the Maximum water depth (`.max`) file (recall [Running the code, outputs and visualisation](/Merewether3.md)) that is generated at the end of simulation, namely `carlisle-5m.max`. The benchmark data is a ASCII raster file, provided as `carlisle-5m.dat`, which contains the serveyed extent of the flooding. Figure below shows the maps of model and benchmark data.

![image](/Figures/metrics5.svg)

To run the script, the name of these two files must be entered at lines 138~140 as below:

````
model_fn = "carlisle-5m.max" 
bench_fn = "carlisle-5m.dat" 
````
After saving the file, it runs with command:

````
python metrics.py
````

and shows the metrics on the screen.

[back](/Carlistle_flooding.md)
