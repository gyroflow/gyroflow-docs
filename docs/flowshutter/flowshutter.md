![](img/flowshutter.png)

Flowshutter is a custom camera remote. When used in conjunction with readily available hardware, this results in a flexible and reliable external camera motion logger for Gyroflow. It can provide precise synchronization of camera video recording and motion logger (betaflight/emuflight FC) recording.

It was designed to be used with the Gyroflow software to provide you one of the best open source video stabilization experiences.


## Features

- **"1-click"** - synchronously start/stop (1) FC arm (2) camera recording
- **"Audio injection"** - inject sync marker to the audio track for precise synchronization between video and gyro data
- **OLED Display** - show the device information and allow user to change settings without hacking the firmware code
- Blackbox Erasion - erase all blackbox data without connecting to the computer
- OTA Update - (WIP) update the firmware over the air


## Supported Hardware

Currently we are working NeutronRC for a small range of sales in China. Subsequent versions are in production, please stay tuned.

![](img/nerc_sdb_pic.jpg)

For more info about list of supported hardware, please check [Supported Hardware](hardware.md).


### Compatible camera protocol/trigger mechanisms

- Sony Multi-Terminal Port USB Protocol
- Momentary Ground
- 3.3V Schmitt Trigger
- (WIP) 5V Schmitt Trigger
- (WIP) Sony LANC protocol
- (WIP) HDMI CEC protocol

Check out our list of [Supported Camera](clist.md) for more details.

### Compatible FC

- Flowbox (highly recommended)
- Modern FC with BMI270 gyro (recommended)
- Any other FC that support CRSF protocol

## More info

- Source code: [https://github.com/gyroflow/flowshutter](https://github.com/gyroflow/flowshutter)
- Development Guide: [https://github.com/gyroflow/flowshutter#development-guide](https://github.com/gyroflow/flowshutter#development-guide)
