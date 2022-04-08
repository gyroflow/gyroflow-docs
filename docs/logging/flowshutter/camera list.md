The lists below are not complete and needs further updating. If you know of a certain camera's way of REC triggering, please let us know via:

- Flowshutter [issue](https://github.com/gyroflow/flowshutter/issues/82)
- Gyroflow [Discord](https://discord.gg/WfxZZXjpke)

## Sony Multi-Terminal Protocol

It seems that any camera from Sony that has this Multi-USB port can use this protocol for REC triggering.

[How to DIY Sony Multi USB connector?](diy camera jacks.md#sony-multi-usb-connector)

| Camera | Support info | Camera | Support info | Camera | Support info |
| :---: | :---: | :---: | :---: | :---: | :---: |
| A5000 |  yes  |  A7S  |  yes  |  A7R  |  yes  |
| A5100 |  yes  | A7S2  |  yes  | A7R2  |  yes  |
| A6000 |  yes  | A7S3  |  yes  | A7R3  |  yes  |
| A6100 |  yes  |  A7M  |  yes  | A7R4  |  yes  |
| A6300 |  yes  | A7M2  |  yes  | FX3   |  yes  |
| A6400 |  yes  | A7M3  |  yes  | FX6   |  yes  |
| A6500 |  yes  | A7M4  |  yes  | FX9   |  yes  |
| A6600 |  yes  |  A7C  |   no  |

## Momentary Ground

As the name implies, momentarily shorting a pin in one of the camera's port(s) to ground triggers REC start/stop. Many cameras support triggering REC using this method.

| Brand | Model | Support info | Notes | 
| :---: | :---: | :---: | :---: |
| Canon | Almost all(?) | yes | |
| Nikon | Almost all(?) | yes | |
| Blackmagic Design | Pocket Cinema Camera 4k | yes | w/HDMI REC control wire |
| Blackmagic Design | Pocket Cinema Camera 6k | yes | w/HDMI REC control wire |
| Blackmagic Design | Pocket Cinema Camera 6k pro | yes | w/HDMI REC control wire |
| Kinefinity | MAVO Edge 6K | yes |
| Kinefinity | MAVO Edge 8K | yes |
| RED | DSMC2 | yes |
| RED | RANGER | yes |
| More.. | | |


## 3.3V Schmitt Trigger

Pull a pin of a port to 3.3V level to start REC, and pull it back to 0V to stop REC.

| Brand | Model | Support info |
| :---: | :---: | :---: |
| RED | DSMC | yes |
| RED | DSMC2 | yes |

## TODO