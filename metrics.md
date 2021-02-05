#### Performance metrics

To measure the performance of the model in predicting the flooding extent, three metrics are commonly used within the hydraulic modeling community, namely Hit Rate (H), False Alarm Ratio (F), and Critical Success Index (C). 


These metrics compare the benchmark data vs modeled data in a binary (wet or dry) manner and sum up them as four states shown in table below.

   |  | **Wet in Benchmark Data** | **Dry in Benchmark Data** |
   | :---         | :---      | :--- |
   | **Wet in Modeled Data**   | M1B1      | M1B0    |
   | **Dry in Modeled Data**     | M0B1       | M0B0    |

In this sense, e.g. M1B1 denotes the total number of cells that are both wet in benchmark and modeled data.

The **Hit Rate (H)**, sometimes referred to as the probability of detection, is a simple measure that tests the proportion of wet benchmark cells that was replicated by
the model, ignoring whether the benchmark flood boundaries were exceeded:

````
H = M1B1 / (M1B1 + M0B1)
````

H ranges from 0 (none of the wet benchmark cells are wet in the modeled data) to 1 (all wet benchmark cells are wet in the modeled data), examining the model’s tendency toward underprediction of the flood hazard.

The **False Alarm Ratio (F)** indicates the proportion of wet modeled cells that are not wet in the benchmark data:

````
F = M1B0 / (M1B0 + M1B1)
````

This metric gives an idea of whether the model has the tendency to overpredict flood extent and can range from 0 (no false alarms) to 1 (all false alarms). 

The **Critical Success Index (C)** extends on both H and F to create a combined score that accounts for both underprediction and overprediction:

````
C = M1B1 / (M1B1 + M0B1 + M1B0)
````

where scores range from 0 (no match between benchmark and modeled data) to 1 (perfect match between benchmark and modeled data).

#### Python script to compute the performance metrics

A simple Python script, named `metrics.py` is included in the post-processing directory, to compute these statistical metrics.  

[back](/EnvAcy5.md)
