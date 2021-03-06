#### Metrics for comparing two different flood extent predictions 

To compare two sets of 2D flood extent maps, referred to as the “model” and “benchmark” data, the Hit Rate (H), False Alarm Ratio (F), and Critical Success Index (C) need to be generated ([Wing et al., 2017](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2017WR020917)). The model and benchmark data must have the same grid resolution for the same area of interest.  

To generate the H, F and C metrics, all the cells in the model data and benchmark data are checked one-by-one to flag them as either wet (i.e. contain water depth over 10 cm) or dry (i.e. contain water depth under 10 cm). 

In this sense, M1 denotes a wet model cell, B1 denotes a wet benchmark cell, M0 denotes a dry model cell and B0 denotes a dry benchmark cell. 

At the next step, each cell in the model data is compared to the respective cell in the benchmark data to be flagged as either of the four categories shown in the table below.
  
   |  | **Wet in Benchmark Data (B1)** | **Dry in Benchmark Data (B0)** |
   | :---         | :---      | :--- |
   | **Wet in Model Data (M1)**   | M1B1      | M1B0    |
   | **Dry in Model Data (M0)**   | M0B1      | M0B0    |

M1B1 denotes a cell that is wet in both the benchmark and model data, M0B0 denotes a cell that is dry in both the benchmark and model data, M1B0 denotes a cell that is wet in the model data but dry in the benchmark data, and M0B1 denotes a cell that is dry in the model data but wet in the benchmark data. These are further illustrated in the schematic figure below.

![image](/Figures/metrics4.svg)

Finally, the total number of cells belonging to each of the four categories are summed up and used in the respective formulas to compute H, F and C metrics as follows. 

The Hit Rate (H) indicates how much of the benchmark flood extent is also covered by the model flood extent. It is computed by dividing the total number of cells that are wet in both model and benchmark data by the total number of cells that are wet in the benchmark data:

````
H = ∑M1B1 / (∑M1B1 + ∑M0B1)
````

H ranges from the worst case of 0 (none of the benchmark flood extent is covered by the model flood extent) to the best case of 1 (all of the benchmark flood extent is covered by the model flood extent). Note that H does not consider those areas of the model flood extent that are outside of the benchmark flood extent. 

The False Alarm Ratio (F) measures how much of the model flood extent is outside of the benchmark flood extent. It is computed by dividing the total number of cells that are wet in the model data and dry in the benchmark data by the total number of cells that are wet in the model data:

````
F = ∑M1B0 / (∑M1B0 + ∑M1B1)
````

F ranges from the best case of 0 (none of the model flood extent is outside of the benchmark flood extent) to the worst case of 1 (all of the model flood extent is outside of the benchmark flood extent). 

The Critical Success Index (C) is a composite measure that combines both H and F metrics, and therefore it allows for a more inclusive comparison of the flood extent prediction performance. It is computed by dividing the total number of cells that are wet in both model and benchmark data by the total number of cells that are wet in either model or benchmark data.

````
C = ∑M1B1 / (∑M1B1 + ∑M0B1 + ∑M1B0)
````

C ranges from the worst case of 0, showing no match between the benchmark and model flood extents, to the best case of 1 which shows the perfect match between the benchmark and model flood extents. 

#### Post-processing toolkit to compute the metrics

A Python script, named metrics.py is included in the postprocess directory of LISFLOOD-FP-trunk repository, to compute these metrics. The script requires the GDAL library for reading the data (see [GDAL documentation](https://gdal.org/index.html)). 

To run the script, two [Esri ASCII raster files](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) with the same resolution and extent, one for benchmark data and the other for the model data is required. The model data is the maximum water depth (`.max`) file (recall [*"Running the code, outputs and visualisation"*](/Merewether3.md)) resulted from a simulation. The benchmark data can be the maximum water depth (`.max`) file from another reference simulation or the flood extent observations from a flooding event. For the latter, the flood extent map must be converted to an [Esri ASCII raster file](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/esri-ascii-raster-format.htm) with the same resolution and extent of the model data.

To run the script, first the name of the model and benchmark data files must be entered at lines 138~140 of the script, as shown below:

````
model_fn = "model_data_file_name" 
bench_fn = "benchmark_data_file_name" 
````
After saving the file, it runs with the command:

````
python metrics.py
````

and outputs the metrics on the screen as shown below:

````
Hit rate: ...
False Alarm rate: ...
Critical success index: ...
````

It also saves a contingency map ([Hoch et al., 2017](https://gmd.copernicus.org/articles/10/3913/2017/)) in a file named `map.png`, which visualizes the benchmark and model flood extents. In the map, the green area is the portion of the floodplain that is covered both by the model and benchmark flood extents (i.e. M1B1 cells), the red area is only covered by the benchmark flood extent (i.e. M0B1 cells) and the blue area is only covered by the model flood extent (i.e. M1B0 cells) (see the results of the [*"Carlisle 2005 urban flooding"*](/Carlistle_flooding.md) test case). 

[back](/Carlistle_flooding.md)
