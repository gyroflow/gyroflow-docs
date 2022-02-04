Due to the flexibility of Gyroflow, the gyro source and the video source can be "mismatched". This means that an action camera with internal gyro logging (e.g. GoPro) can be mounted to a high-end cinema camera acting as a gyro logger. This setup is illustrated below.


![!](img/gopro_logger.jpg){ width="70%" }


The advantages of this setup is the availability of GoPros/Insta360 cameras among filmmakers, meaning no additional hardware other than some fasteners.


With this setup, a number of things should be considered:

* The cinema camera and logger camera should be rigidly attached to each other to avoid mismatching motion data.
* The two should ideally be oriented in the same direction to avoid additional angle corrections.
* Starting recording of the two cameras at almost the same time, or with a small fixed offset (e.g. 10 seconds) makes synchronization easier.

This setup has successfully been used with GoPro Hero 6/8/9, the Insta360 OneR/Go 2 among others. In general, any camera with gyro logging should work, assuming the gyro data is clean and correct.

When using a GoPro hero 8 or newer as a gyro logger, the internally computed orientations (`None` integration method) should not be used, since these orientations only correspond to each frame from the GoPro file.