# Final-Project-Sensor-Fusion-and-Object-Tracking

This project has several task to be performed, divided as follow:
* Step 1
* Step 2
* Step 3
* step 4

## Reference code
[filter.py](filter.py)
<br>
[trackmanagement.py](trackmanagement.py)
<br>
[association.py](association.py)
<br>
[measurements.py](measurements.py)

## Step 1
In this step I've implemented EKF for a 6D input; in order to do so I've derived the equations and adapted the code from the previous excercise to fit input dimensions.

```
F = np.matrix([[1, 0, 0, dt, 0, 0],
               [0, 1, 0, 0, dt, 0],
               [0, 0, 1, 0, 0, dt],
               [0, 0, 0, 1, 0, 0],
               [0, 0, 0, 0, 1, 0],
               [0, 0, 0, 0, 0, 1]])
```

```
q = params.q
dt = params.dt
q1 = ((dt**3)/3) * q 
q2 = ((dt**2)/2) * q 
q3 = dt * q 
Q = np.matrix([[q1, 0, 0, q2, 0, 0],
               [0, q1, 0, 0, q2, 0],
               [0, 0, q1, 0, 0, q2],
               [q2, 0, 0, q3, 0, 0],
               [0, q2, 0, 0, q3, 0],
               [0, 0, q2, 0, 0, q3]])
```
The resulting EFK has RMSE is 0.32, which is lower than the request.

![step1](Pic/step1.png "step1")
<br>
![rmse](Pic/rmse.png "rmse")


```
b = np.array([0, 1e-5, 1e-4, 1e-3, 1e-2, 1e-1, 1, 1e+1, 1e+3, 1e+3, 1e+4, 1e+5, 1e+6, 1e+7])
hist,bins = np.histogram(lidar_pcl_cpy[:,3], bins=b)
print(hist)
```
