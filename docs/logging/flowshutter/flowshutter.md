Flowshutter is a custom camera remote. When used in conjunction with readily available hardware, this results in a flexible and reliable external camera motion logger for Gyroflow. It can provide precise synchronization of camera video recording and motion logger (betaflight/emuflight FC) recording.

It was designed to be used with the Gyroflow software to provide you one of the best open source video stabilization experiences.

## Features

- "1-click" - start/stop (1) FC arm (2) camera recording at the same time
- "Audio injection" - inject sync marker to the audio track for precise synchronization between video and gyro data
- OLED display - show the device information and allow user to change settings without hacking the firmware code
- OTA update - (WIP) update the firmware over the air

## Supported Hardware

Currently we are working with a manufacturer that will produce flowshutter hardware. We will disclose more relevant information in the future.

At the same time you can try to DIY your own flowshutter hardware. I have two open sourced designs:

- [Credit card size](https://oshwhub.com/AirFleet/xiang-ji-kong-zhi-ban): build video is [here](https://www.youtube.com/watch?v=ELaQPYE9ncA)

<iframe width="560" height="315" src="https://www.youtube.com/embed/ELaQPYE9ncA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- [FC size](https://oshwhub.com/AirFleet/xiang-ji-kong-zhi-ban_copy_copy): build video is [here](https://youtu.be/ry7Ey54Z7s8)

<iframe width="560" height="315" src="https://www.youtube.com/embed/ry7Ey54Z7s8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Compatible camera protocol/trigger mechanisms

- Sony Multi-Terminal Port USB Protocol
- (WIP) Sony LANC protocol
- (WIP) Canon/Nikon: trigger by short
- (WIP) RED/Kinefinity: trigger by voltage

Check out our [supported camera list](camera list.md) for more details.

### Compatible FC

- Flowbox (highly recommended)
- Modern FC with BMI270 gyro (recommended)
- Any other FC that support CRSF protocol

## More info

- Source code: [https://github.com/gyroflow/flowshutter](https://github.com/gyroflow/flowshutter)
- Development Guide: [https://github.com/gyroflow/flowshutter#development-guide](https://github.com/gyroflow/flowshutter#development-guide)
