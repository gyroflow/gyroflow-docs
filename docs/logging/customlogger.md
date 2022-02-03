This page contains an example of how data logging can be implemented.

![!](img/example_axes.png){ width="100%" }

## Hardware
An MEMS Inertial Measurement Unit (MEMS IMU) is a chip containing a gyroscope and an accelerometer. The gyroscope measures the rotational rate, while the accelerometer measures acceleration as the name implies. Gyroflow requires the gyroscope, while the accelerometer is optional and only required if horizon referencing is desired. An example of the acceleration and rotational axes around a camera is illustrated above. Many camera systems already contain such an IMU for electronic image stabilization, so in some cases, it is possible to allow for motion logging through a firmware update.

For a dedicated logger, a simple combination of a memory device (MicroSD/SPI Flash chip etc.), a microcontroller, and an inertial measurement unit suffices. This hardware combination is readily available as low-cost drone flight controllers, which can act as loggers as described on [another page](../betaflight). Dedicated hardware for this task is currently under development as part of the Gyroflow project.

## Software/Firmware
On the software and firmware side, the inertial measurement unit should be configured correctly. Refer to the datasheet of your IMU for information about how to configure this exactly. It has been found that the following IMU settings offer a reasonable starting point.

* logging rate: 500 Hz
* Low pass filter cutoff: 100 Hz
* gyro scaling: 1000 deg/s
* acceleration scaling: +/- 4 g

The minimum logging rate sufficient for stabilization is approximately 100 Hz, but note that such a low logging rate requires excellent filtering in order to avoid data loss and aliasing. Using a 500 Hz logging rate with a 100 Hz cutoff allows for some margin of error in terms of aliasing.

## `.gcsv` gyro log format

!!! warning

    At the time of writing, this format has been designed but not yet fully implemented. This will be done very soon.

What follows is a text-based gyro log format that can easily be implemented in custom hardware/firmware called `.gcsv` (short for gyro csv or gyroflow csv).

Firstly, for a video file called `videofilename.mp4`, the corresponding gyro log file is 'videofilename.gcsv'. This allows for automatic log detection.

The `.gcsv` file contains information about the gyro orientation, scaling, and a unique identifier. For a logger supporting logging of gyro and accelerometer:

```
GYROFLOW IMU LOG
version,1
id,custom_logger_name
orientation,XYZ
note,FIRMWARE_0.1.0
tscale,0.001
gscale,0.0002663161
ascale,0.00059875488
t,gx,gy,gz,ax,ay,az
0,39,86,183,-1137,-15689,-2986
1,56,100,202,-1179,-15694,-2887
2,63,108,218,-1247,-15702,-2794
3,71,108,243,-1308,-15675,-2727
4,83,101,268,-1420,-15662,-2661
5,101,93,294,-1575,-15661,-2629
6,121,95,319,-1677,-15654,-2639
7,143,97,348,-1709,-15673,-2654
8,163,98,362,-1704,-15691,-2685
9,173,93,371,-1678,-15698,-2736
10,181,98,375,-1623,-15697,-2810
11,173,105,365,-1578,-15693,-2929
12,159,111,363,-1555,-15711,-3057
13,157,113,348,-1540,-15747,-3159
14,157,118,327,-1542,-15780,-3246
15,153,123,310,-1595,-15812,-3319
```

Breaking this down:

1. The first line identifies the file as a IMU log. This line should either be `GYROFLOW IMU LOG` or the more neutral `CAMERA IMU LOG`.
2. The second line `version,1` describes the "version" of the .gcsv file. This is equal to `1` for now.
3. The third line contains a unique ID associated with the logger/camera. For instance a high-end camera with internal logging may use `id,potatocam_deluxe_4k_grey_edition`.
4. The forth line contains the orientation string. This corresponds to the `IMU Orientation` field in Gyroflow.
5. The next line is an optional note, and can contain other relevant information, such as the camera/logger firmware version etc.
6. The subsequent lines with `tscale`, `ascale` and `gscale` describe constants used to scale the raw sensor values.
	- Multiplying `tscale` by the raw `t` values should give the time in **seconds**. It can thus be deduced that the file above is logging at 1000 Hz.
	- Multiplying `ascale` by the raw `ax/ay/az` values should give the acceleration in **g**
	- Multiplying `gscale` by the raw `gx/gy/gz` values should give the angular rate in **rad/s**
7. The rest of the file simply consists of a standard CSV header and the raw values. Note that fixed-point integers are used with a scalar in order to avoid excessively large text files. Using floating points here is still valid though.

The header of the `.gcsv` file (for the most part) remains static for a given camera/setup, and can thus be written as a constant string to the file.

Raw sensor values are often represented as 16-bit signed integers, meaning a range between of `+/- 2^15`. If the acceleration range is known to be +/- 4 g as was the case in the example above. Then `ascale = 4/2^15 = 0.00012207031`. Refer to the datasheet for conversion information. Similarly, a gyroscope with a range of `+/- 1000 deg/s` gives `gscale = (1000 * pi / 180)/2^15 = 0.00053263221`. Note that even when configured to a setting such as `+/- 1000 deg/s`, the actual calibration of the sensor may lead to maximum slightly above or below this value. As always, consult the datasheet.

If a magnetometer is present, it's simply:
```
GYROFLOW IMU LOG
version,1
id,custom_logger_name
orientation,XYZ
tscale,0.001
gscale,0.0002663161
ascale,0.00059875488
mscale,
t,gx,gy,gz,ax,ay,az,mx,my,mz
0,39,86,183,-1137,-15689,-2986,123,345,546
1,56,100,202,-1179,-15694,-2887,124,344,560
```
with `mscale` leading to values in **gauss** (Note that `1 tesla = 10000 gauss`). Similarly, if only gyroscope data is used, the `ax,ay,az` columns can be left out.

For a logger/camera implementation, some other things to think about:

* For a camera, the timestamps should be based on the same time source as the video capture. This prevents drift between the two.
* Consider using microseconds for the timestamp if a faster sampling rate if the time source allows. This may improve the timing during the sync process.
* Consider using the data ready interrupts of IMU's instead of polling for more consistent timings.
