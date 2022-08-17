## `.gcsv` gyro log format

What follows is a text-based gyro log format that can be implemented in custom hardware/firmware called `.gcsv` (short for gyro csv or Gyroflow csv). As a text-based format this is meant to be easily implementable and inspectable (compatible with standard CSV reading software) at the cost of space efficiency.

Firstly, for a video file called `videofilename.mp4`, the corresponding gyro log file is `videofilename.gcsv`, this is a case of the `.gcsv` acting as [sidecar files](https://en.wikipedia.org/wiki/Sidecar_file). This allows for automatic log detection.

The `.gcsv` file contains information about the gyro orientation, scaling, and a unique identifier. The following is an example of a .gcsv file from a logger supporting logging of gyro and accelerometer:

```
GYROFLOW IMU LOG
version,1.2
id,custom_logger_name
orientation,YxZ
note,development_test
fwversion,FIRMWARE_0.1.0
timestamp,1644159993
vendor,potatocam
videofilename,videofilename.mp4
lensprofile,potatocam/potatocam_mark1_prime_7_5mm_4k
frame_readout_time,15.23
frame_readout_direction,0
tscale,0.001
gscale,0.00122173047
ascale,0.00048828125
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
...
```
If a magnetometer is present, some additional fields are present, e.g.:
```
GYROFLOW IMU LOG
version,1.2
id,custom_logger_name
orientation,YxZ
note,development_test
fwversion,FIRMWARE_0.1.0
timestamp,1644159993
vendor,potatocam
videofilename,videofilename.mp4
lensprofile,potatocam_mark1_prime_7_5mm_4k
tscale,0.001
gscale,0.00122173047
ascale,0.00048828125
mscale,0.00059875488
t,gx,gy,gz,ax,ay,az,mx,my,mz
0,39,86,183,-1137,-15689,-2986,123,345,546
1,56,100,202,-1179,-15694,-2887,124,344,560
...
```

### Mandatory fields:

1. The very first line identifies the file as an IMU log. This line should either be `GYROFLOW IMU LOG` or the more neutral `CAMERA IMU LOG`.
2. The second line `version,1.2` describes the "version" of the .gcsv file format. This is equal to `1.2` for now. The versions are backwards compatible, but changes with the addition of new metadata fields.
3. The third line contains a unique ID associated with the logger/camera. For instance a high-end camera with internal logging may use `id,potatocam_deluxe_4k_grey_edition`.
4. The fourth line contains the orientation string. This corresponds to the `IMU Orientation` field in Gyroflow (see the implementation notes below for further details).
5. The next few lines contain optional metadata. These are not strictly required, but may improve workflow and stabilization. Developers are thus encouraged to include all known fields.
6. The subsequent lines with `tscale`, `ascale` and `gscale` describe constants used to scale the raw sensor values.
	- Multiplying `tscale` by the raw `t` values should give the time in **seconds**. It can thus be deduced that the file above is logging at 1000 Hz since each line increments by `1*0.001=0.001 s`, corresponding to a frequency of 1 KHz. The resolution of the timestamps should be 1 ms or better.
	- Multiplying `gscale` by the raw `gx/gy/gz` values should give the angular rate in **rad/s**
	- (If accelerometer data present) Multiplying `ascale` by the raw `ax/ay/az` values should give the acceleration in **g**
	- (If magnetometer data present) Multiplying `mscale` by `mx/my/mz` gives the measurements in **gauss** (Note that `1 tesla = 10000 gauss`).
7. The rest of the file simply consists of a standard CSV header and the raw values. The header and data order should be one of the following: `t,gx,gy,gz`, ``t,gx,gy,gz,ax,ay,az``, or ``t,gx,gy,gz,ax,ay,az,mx,my,mz``. Gyroscope data is the minimum requirement. Acceleration data is required for horizon lock, while magnetometer data improves drift in orientation determination (Not currently of significant importance).
8. For the data itself, fixed-point integers are recommended with a scalar (point 6) in order to avoid excessively large text files. Using floating points here is still valid though. 

### Optional fields:
The following are all optional fields for the metadata block, but developers should include as many known fields as possible.

* `Note` is for other misc. information.
* `fwversion` is the firmware of the logger/camera.
* `timestamp` is the unix timestamp when logging began.
* `vendor` can contain the vendor or developer
* `videofilename` is the name of the corresponding video file. Normally the `.gcsv` file name already matches, but this insures the information is kept if the filename changes.
* `lensprofile` is the unique name of the lens preset and vendor folder. If it matches a lens profile in the [database](https://github.com/gyroflow/gyroflow/tree/master/resources/camera_presets) it is automatically selected during loading.
* `frame_readout_time` is the time in milliseconds it takes to capture a full video frame using rolling shutter. This is used for rolling shutter correction.
* `frame_readout_direction` is the direction of the readout. Most cameras with rolling shutter capture the top of the frame first. Note that Gyroflow currently only supports correcting 0 and 1.
	- 0: Top to bottom
	- 1: Bottom to top
	- 2: Left to right
	- 3: Right to left

### Implementation notes
The required parts of the header of the `.gcsv` file remains static for a given camera/setup, and can thus be written as a constant string to the file.

Raw sensor values are often represented as 16-bit signed integers, meaning a range between of `+/- 2^15`. If the acceleration range is known to be +/- 4 g as was the case in the example above. Then `ascale = 4/2^15 = 0.00012207031`. Refer to the datasheet for conversion information. Similarly, a gyroscope with a range of `+/- 1000 deg/s` gives `gscale = (1000 * pi / 180)/2^15 = 0.00053263221`. Note that even when configured to a setting such as `+/- 1000 deg/s`, the actual calibration of the sensor may lead to a maximum slightly above or below this value. As always, consult the datasheet.

For a logger/camera implementation, some other things to think about:

* For a camera, the timestamps should be based on the same time source as the video capture. This prevents drift between the two.
* Consider using microseconds for the timestamp if a faster sampling rate if the time source allows. This may improve the timing during the sync process.
* Consider using the data ready interrupts of IMU's instead of polling for more consistent timings.
* Ensure proper filtering of the data to meet the Nyquist criteria for the samling frequency. Even more filtering is usually recommended, e.g. setting the builtin hardware low pass filter cutoff at 50 Hz to 100 Hz is a good starting point, even for higher sampling frequencies.

For the IMU Orientation string, the following figure corresponds to `YxZ`.

![!](img/example_axes.png){ width="100%" }

* For the gyroscope, data for an axis correspond to the right-handed rotation rate of the camera body about that axis.
* The accelerometer data correspond to linear acceleration applied in the given direction. Due to the nature of gravity, a stationary object will experience an *upwards* acceleration of 9.81 m/s<sup>2</sup>, while an object in freefall will experience *zero* acceleration.
* The magnetometer data corresponds to the measured magnetic field vector.

In order for orientation determination to work correctly, the data must have the same/aligned coordinate axes. For combined IMU sensors, this is already the case for the raw data. If a rotation is applied to the gyro data before being written, the same rotation should be applied to the accelerometer (and magnetometer). This ensures that the axes stay aligned.

If the gyroscope and accelerometer data come from separate sensors, their axes must similarly be aligned, either physically or by applying a rotation in software.

### Version changelog
* 1.0: Initial version
* 1.1: Add lens profile field
* 1.2: Add rolling shutter information