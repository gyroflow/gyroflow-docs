Welcome to the Camera List. To navigate through this section, use the sidebar on the **right**.

At the time of writing, the lists below are not complete and needs further updating. If you know of a certain camera's way of REC triggering, please let us know via:

- Flowshutter [issue](https://github.com/gyroflow/flowshutter/issues/82)
- Gyroflow [Discord](https://discord.gg/WfxZZXjpke)

## Sony Multi-Terminal Protocol

It seems that any camera from Sony that has this Multi-USB port can use this protocol for REC triggering.

[How to make Sony Multi USB connector? Wiring?](wiring.md#sony-multi-usb)

| Camera | Support info | Camera | Support info | Camera | Support info |
| :---: | :---: | :---: | :---: | :---: | :---: |
| A5000 |  yes  |  A7S  |  yes  |  A7R  |  yes  |
| A5100 |  yes  | A7S2  |  yes  | A7R2  |  yes  |
| A6000 |  yes  | A7S3  |  yes  | A7R3  |  yes  |
| A6100 |  yes  |  A7M  |  yes  | A7R4  |  yes  |
| A6300 |  yes  | A7M2  |  yes  |  FX3  |  yes  |
| A6400 |  yes  | A7M3  |  yes  |  FX6  |  yes  |
| A6500 |  yes  | A7M4  |  yes  |  FX9  |  yes  |
| A6600 |  yes  |  A7C  |   no  |  FS5  |  yes  |

## Momentary Ground

As the name implies, momentarily shorting a pin in one of the camera's port(s) to ground triggers REC start/stop. Many cameras support triggering REC using this method.

[Wiring Diagrams](wiring.md#momentary-ground)

| Brand | Model | Support info | Notes | 
| :---: | :---: | :---: | :---: |
| Blackmagic Design | Pocket Cinema Camera 4k | yes | w/[ZITAY recording cable](wiring.md#bmpcc-4k6k6k-pro-recording-cable-zitay) |
| Blackmagic Design | Pocket Cinema Camera 6k | yes | w/[ZITAY recording cable](wiring.md#bmpcc-4k6k6k-pro-recording-cable-zitay) |
| Blackmagic Design | Pocket Cinema Camera 6k pro | yes | w/[ZITAY recording cable](wiring.md#bmpcc-4k6k6k-pro-recording-cable-zitay) |
| Kinefinity | MAVO Edge 6K | yes |
| Kinefinity | MAVO Edge 8K | yes |
| RED | DSMC2 | yes |
| RED | RANGER | yes |
| Panasonic | Lumix DMC-GH1 | yes | w/[Panasonic Custom Trigger Connector](wiring.md#panasonic-lumix-remote-connector) |
| Panasonic | Lumix DMC-GH2 | yes | w/[Panasonic Custom Trigger Connector](wiring.md#panasonic-lumix-remote-connector) |
| Panasonic | Lumix DMC-GH3 | yes | w/[Panasonic Custom Trigger Connector](wiring.md#panasonic-lumix-remote-connector) |
| Panasonic | Lumix DMC-GH4 | yes | w/[Panasonic Custom Trigger Connector](wiring.md#panasonic-lumix-remote-connector) |
| Panasonic | Lumix DMC-GH5 | yes | w/[Panasonic Custom Trigger Connector](wiring.md#panasonic-lumix-remote-connector) |
| Panasonic | Lumix DC-GH5S | yes | w/[Panasonic Custom Trigger Connector](wiring.md#panasonic-lumix-remote-connector) |
| More.. | To Be Appended | |


## 3.3V Schmitt Trigger

Pull a pin of a port to 3.3V level to start REC, and pull it back to 0V to stop REC.

| Brand | Model | Support info |
| :---: | :---: | :---: |
| RED | DSMC | yes |
| RED | DSMC2 | yes |

## TODO