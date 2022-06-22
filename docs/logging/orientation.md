In order to find the IMU orientation, the following approach can be used. Essentially, by moving the system in a known order, the observed gyro/accelerometer signal can be compared to teh `correct` one.


Firstly, the "standard" Gyroflow input orientation is defined as follows. Suppose a camera is pointed with the lens forwards in a horizontal orientation. The z vector is then pointed backwards, the x vector pointed upwards, and the y vector pointed to the left. This is illustrated in the figure below.


The measured accelerations and angular rates are assumed to be aligned.



## Find orientation for existing footage
If you have captured footage with an unknown orientation, it is also possible to deduce the correct orientation based on the video and gyro data. 