# Final-Project-Sensor-Fusion-and-Object-Tracking

This project has several task to be performed, divided as follow:
* Step 1
* Step 2
* Step 3
* step 4

## Reference code
[loop_over_dataset.py](loop_over_dataset.py)
<br>
[objdet_pcl.py](objdet_pcl.py)
<br>
[objdet_detect.py](objdet_detect.py)
<br>
[objdet_eval.py](objdet_eval.py)

## Step 1

![pcl6](Pics/pcl6.png "pcl6") *Preceeding vehicles in a X-junction*


```
b = np.array([0, 1e-5, 1e-4, 1e-3, 1e-2, 1e-1, 1, 1e+1, 1e+3, 1e+3, 1e+4, 1e+5, 1e+6, 1e+7])
hist,bins = np.histogram(lidar_pcl_cpy[:,3], bins=b)
print(hist)
```
