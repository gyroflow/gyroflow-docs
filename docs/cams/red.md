!!! warning

	While most RED cameras have the required hardware for gyro logging, not all of them have this feature enabled.

Some cameras from RED cinema save motion data, either on a per-frame basis, or asynchronously (faster sample rate). This data is supported by Gyroflow.

Footage from the following cameras are known to contain per-frame motion data:

* RED RAVEN
* ???

Footage from the following cameras contain asynchronous motion data:

* RED V-RAPTOR
* RED KOMODO
* ??

Make sure the camera firmware is updated, since older firmware versions may not have gyro logging enabled.

## Stabilize RED footage with Gyroflow
In order to get the most out of RED footage, the following workflow is recommended:

1. Transcode from R3D to ProRes. The resulting file can be loaded in Gyroflow as the video file
2. Load the original .R3D in the "Motion data" section.
3. Load the correct lens profile and do autosync.
4. You can then render as ProRes or export a project file and open it in DaVinci Resolve with Gyroflow-OFX plugin and the original .R3D file to have full color control and stabilization inside Resolve without any quality loss

Tips for KOMODO specifically:
* Estimate gyro bias: Find a place where camera is not moving at all, right click on timeline and **Estimate gyro bias here** to calibrate the gyroscope
* Enable rolling shutter correction and set frame readout time to 0.01ms (global shutter)
* Do autosync, or better find 2-3 points on the timeline with significant motion and right click -> Autosync here
* If it's shaky, remove the sync point and try in a different place


## View RED metadata manually
If you wish to view the RED metadata without using Gyroflow, you can use REDline, a command-line utility bundled with REDCINE-X PRO ([Windows](https://www.red.com/download/redcine-x-pro-win), [MacOS](https://www.red.com/download/redcine-x-pro-mac)) or standalone program ([Linux](https://www.red.com/download/redline-linux-beta)). See how to install and launch REDline based on your operating system in this [guide](http://docs.red.com/955-0004/REDCINE-XProOperationGuide/Content/11_REDLINE/LaunchRedline.htm).


In order to view the per-frame metadata for a video file, run:

```
REDline --i video.R3D --printMeta 5
```

Assuming `REDline` is in the PATH, or e.g. `"C:\Program Files\REDCINE-X PRO 64-bit\REDline" --i video.R3D --printMeta 5` on a Windows installation of REDCINE-X PRO.

For a clip from a RED RAVEN, this yields:

```
FrameNo,Timecode,Timestamp,Aperture,Focus Distance,Focal Length,Acceleration X,Acceleration Y,Acceleration Z,Rotation X,Rotation Y,Rotation Z,Cooke Metadata
0,20:47:06:03,,4.500000,455,10,0.087000,-0.019000,1.022000,0.189000,-0.001000,-2.253000,
1,20:47:06:04,,4.500000,455,10,0.102000,-0.019000,1.007000,2.438000,-2.250000,-4.502000,
2,20:47:06:05,,4.500000,455,10,0.102000,-0.019000,1.022000,2.438000,-0.001000,-2.253000,
3,20:47:06:06,,4.500000,455,10,0.102000,-0.019000,1.007000,2.446000,-0.001000,-4.502000,
4,20:47:06:07,,4.500000,455,10,0.087000,-0.003000,1.007000,2.446000,0.007000,-4.502000,
5,20:47:06:08,,4.500000,455,10,0.087000,-0.019000,1.007000,2.446000,0.007000,-2.253000,
6,20:47:06:09,,4.500000,455,10,0.087000,-0.019000,1.007000,2.438000,-0.001000,-0.004000,
7,20:47:06:10,,4.500000,455,10,0.102000,-0.019000,1.007000,2.438000,-0.001000,-0.004000,
8,20:47:06:11,,4.500000,455,10,0.102000,-0.019000,0.991000,2.438000,-0.001000,-0.004000,
...
```

In order to view the asynchronous metadata, run:

```
REDline --i video.R3D --printMeta 7
```

This yields the following for a clip without this data:

```
[02-07-22-24-33-066]<69f4> Clip does not have async IMU data
```

