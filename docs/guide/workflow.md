# General Workflows

This page contains several common minimal workflows for stabilizing video with Gyroflow.

## Cameras w/ Motion Data 
It is relatively simple to use a camera that can directly output gyro data in the machine, just drag and drop the video file (and gyro log) to gyroflow.

![](img/native_gyro_logging_diagram.png)

## Cameras without Motion Data
The use of the camera that cannot directly output the gyro data in the machine is more flexible. The video file and the gyro log are from different devices, and the two parts need to be manually added to gyroflow.
### Action as logger

![](img/action_as_logger_diagram.png)

### FC as logger

![](img/fc_as_logger_diagram.png)
