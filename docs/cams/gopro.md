From the GoPro Hero 5 and onwards, the [GPMF](https://github.com/gopro/gpmf-parser) metadata has contained useful motion data supported by Gyroflow. Unfortunately not all cameras work equally well:

## General
All GoPros use 4:3 sensors and allow for different field of views. For Gyroflow stabilization, the best resolutions are 4:3 resolutions with the `wide` field of view. This gives Gyroflow the most image data to work with.

## Hero 8/9/10
These cameras all contain pre-computed camera orientations for every single frame, meaning the synchronisation step can be skipped when using the `None` integration method. Footage from these cameras are essentially "plug and play" when it comes to Gyroflow stabilization, since Gyroflow contains built-in lens profiles for all these cameras. Furthermore, since these cameras do internal rolling shutter processing, additional rolling shutter correction is not required.

Finally, the GPMF metadata also contains transformed orientation information when hypersmooth is enabled, meaning further stabilization in Gyroflow is possible.

## Hero 7
The Hero 7 is a bit of an outlier. For drone footage, the gyro data from the Hero 7 have been found to be lackluster to say the least. High amounts of noise and aliasing means Gyroflow stabilization using the internal data is likely to give bad results. For this reason, the Hero 7 is not recommended for cinematic FPV footage. One workaround is to use external gyro logging, for instance using the drone blackbox. Another workaround is the use of vibration-dampening mount, which can be a hassle compared to other GoPros.

The Hero 7 doesn't compute per-frame orientations, meaning synchronization is required. For handheld footage, the mentioned noise issues shouldn't be a problem.

## Hero 6
The Hero 6 contains gyroscope and accelerometer data, and can thus be used with Gyroflow out of the box. Due to the lack of per-frame orientations, the synchronization step is still required. The Hero 6 doesn't exhibit the noise issues of the Hero 7, and works well for drone footage. Compared to Hero 8/9/10, no internal rolling shutter processing is performed, meaning fast motion can cause warping, if no rolling shutter correction is applied in Gyroflow.

## Hero 5
The Hero 5 exhibits similar noise problems to the Hero 7, and is thus not suitable for drone footage out of the box. It should still work for handheld footage.