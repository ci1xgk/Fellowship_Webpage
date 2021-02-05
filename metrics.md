#### Performance metrics

To measure the performance of the model in predicting the flooding extent, three metrics are commonly used within the hydraulic modeling community, namely Hit Rate (H), False Alarm Ratio (F), and Critical Success Index (C). 

The **Hit Rate (H)**, sometimes referred to as the probability of detection, is a simple measure that tests the proportion of wet benchmark cells that was replicated by
the model, ignoring whether the benchmark flood boundaries were exceeded:

![Image](/Figures/metrics1.PNG)

where Am is the modeled inundated area and Ab in the benchmark inundated area. H ranges from 0 to 1, with a score of 1 indicating that all wet cells in the benchmark data are wet in the model data. The **False Alarm Ratio (F)** is a measure of model overprediction (i.e., ‘‘false alarms’’):

![Image](/Figures/metrics2.PNG)

where scores range from 0 (no false alarms) to 1 (all false alarms). The **Critical Success Index (C)** extends on H and F to create a combined score that penalizes for both underprediction and overprediction:

![Image](/Figures/metrics3.PNG)

where scores range from 0 (no match between model and benchmark) to 1 (perfect match between benchmark and model).

[back](/EnvAcy5.md)
