The gyros in both the runcam 5 Orange and gocam PM GR can be sensitive to strong vibrations. You should therefore not rigidly mount it to a source of vibrations (e.g. Drone), but instead use either a TPU mount or similar. The runcam 5 seems to tolerate vibrations decently well, so standard TPU or foam mounts should suffice. From limited testing, the gocam may be more sensitive to motor noise, so see if you can find or 3D print something for better vibration isolation.

## Runcam 5 Orange
Surprise! All along the Runcam 5 Orange had an IMU hidden inside. This was of course previously used for the EIS, but with the newest versions of the firmware, the gyro and accelerometer data can be logged to a CSV file along with the video for post stabilization with Gyroflow. Find the firmware here: https://www.runcam.com/download/runcam5or 

The following have been found to be decent settings for the Runcam 5 Orange, with \* indicating it's important for Gyroflow stabilization.

* Video quality: High
* Resolution\*: Either 4K@30FPS(XV) or 1440p@60fps.
	- The XV resolution is actually the full 4:3 sensor stretched to a 16:9 image (supported by Gyroflow). So this gives the highest resolution and FOV.
	-  Note that the stretching looks bad, so if used without additional processing, linearly squeeze the width to 75% in the video editor to get a 4:3 image.
	- The 1440p option is natively 4:3, so if you want 60fps use this one.
	- You can also use one of the 16:9 resolutions, but this significantly reduces the available FOV for stabilization.
* Volume: You decide
* Shutter\*: Try to get a 90 to 180 degree shutter. So from 1/60 to 1/120 for 30fps and about 1/120 to 1/240 for 60 fps footage. (ND filter may be needed)
* ISO: As low as possible. There seems to be some auto gain regardless of settings.
* Color style: Normal (Flat squeezes the range and doesn’t actually provide more dynamic range)
* Distortion correction\*: Disabled
* Electronic Image Stabilization\*: Disabled
* General settings (there were just found to work decently decently well, but do some testing yourself)
* Saturation: Medium
* Exposure compensation: 0
* Contrast: Low
* Sharpness: Low
* Metering: Average
* White balance: Sunny (change depending on scenario, _don’t_ use auto)
* Low light enhancement: you decide.


### File processing
!!! note

    This was required for the initial gyro logging firmware, and may not be applicable with the latest firmware.

With the initial gyro logging firmware for the Runcam 5, it had an issue with occasionally generating a duplicate frame, which leads to jitter in the stabilized output. This could be fixed by the time you read this, but otherwise there’s a way to solve it. FFmpeg has a command which can detect and remove duplicate frames. I will assume you already have FFmpeg available in the command line, if not, install it from [ffmpeg.org](https://www.ffmpeg.org/).

Duplicate frame detection:
```
Run: ffmpeg -i INPUTVIDEOFILE.mp4 -vf mpdecimate=hi=64:lo=32:frac=0.1 -loglevel debug -f null -
```
After a few seconds, you'll see this:
![!](img/runcam_5_duplicate.png){ width="100%" }


Typically there’s a duplicate frame every 30 seconds. If the input and output frames are the same, then it isn’t an issue. If they are different, we need to get rid of the duplicate frames using the following command:

```
ffmpeg -i RC_0001_210724181232.MP4 -vf mpdecimate=hi=64:lo=32:frac=0.1,setpts=N/FRAME_RATE/TB -c:v libx264 -crf 18 RC_0001_filtered.mp4
```
(replace with your filenames). Lower value for `-crf` means less compression

If using an nvidia GPU (faster processing):

```
ffmpeg -i RC_0001_210724181232.MP4 -vf mpdecimate=hi=64:lo=32:frac=0.1,setpts=N/FRAME_RATE/TB -c:v h264_nvenc -b:v 50M RC_0001_filtered.MP4
```
The 50M means encoding at 50 Mbps, change if needed. Replacing `h264_nvenc` with `h264_amf` should work for AMD systems

In Gyroflow

* If using 4K XV, use the preset: `RunCam/Runcam_5_Orange_4K_30FPS_XV_16by9_stretched.json`
* If using 1440p 60fps use: `RunCam/Runcam_5_Orange_1440p_4by3.json`
* Low pass filter at about `60 Hz` should be fine

## GOCam PM GR
Depending on your setup, you might need to softmount this cam, since the the gyro can be sensitive to motor noise vibrations.

### Settings
First of all, download the latest firmware.

With the initial firmware, the only 4:3 resolution is 1440p 60fps. If you want the full sensor use that. Otherwise use the 4K resolution (works fine if you end up cropping to a cinematic aspect ratio)

### In Gyroflow

* Use either the `RunCam/Runcam_Iflight_Gocam_1440p_4by3.json` preset or the `RunCam/Runcam_Iflight_Gocam_PMGR_4K_16by9.json` preset depending on setting
* A 50 Hz low pass filter setting is a good starting point.