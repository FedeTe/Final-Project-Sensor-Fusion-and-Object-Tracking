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
In this step I've implemented EKF for Lidar data only; in order to do so I've derived the equations and adapted the code from the previous excercise to fit input dimensions, which is 6D.

```
F = np.matrix([[1, 0, 0, dt, 0, 0],
               [0, 1, 0, 0, dt, 0],
               [0, 0, 1, 0, 0, dt],
               [0, 0, 0, 1, 0, 0],
               [0, 0, 0, 0, 1, 0],
               [0, 0, 0, 0, 0, 1]])
```
The formula used to calculate Q is the following one:
![Q](Pic/Q.png "Q")
```
Q = 0, 0, 0, 0, 0, 0
    0, 0, 0, 0, 0, 0
    0, 0, 0, 0, 0, 0
    0, 0, 0, q, 0, 0
    0, 0, 0, 0, q, 0
    0, 0, 0, 0, 0, q
```
Using the already calculated F and Q, the resulting Q(t) is:
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
The resulting EFK mean RMSE is 0.32, which is lower than the request.

<p align="center">
  <img src="Pic/step1.png"/>
</p>

<p align="center">
  <img src="Pic/rmse.png"/>
</p>

## Step 2
The aim of the step is to initialize, update (score and or state) and delete tracks. RMSE of the step is shown in the chart below:
<p align="center">
  <img src="Pic/rmse_2.png"/>
</p>

![step1](Pic/step1.png "step1")
<br>
![rmse](Pic/rmse.png "rmse")
