Flowshutter has many settings to allow you to use it in different situations. This page contains a short description and guide to each of the settings. Luckily, many of the settings are self-explanatory.

## User Interaction System

There are two or three buttons on the flowshutter:

- two buttons: **Page Down** and **Enter**
- three buttons: **Page Up**, **Enter** and **Page Down**

To use them, you need to press, hold and release, which will trigger the short/long press event depending on the hold time. The threshold for short/long press is 500ms, longer than 50ms and shorter than 500ms will trigger a short press event, and longer than 500ms will trigger a long press event.

## Reboot menu

On homepage, long press the **Enter** button and it will show the reboot menu.

- **Page \***: toggle between different reboot options
- **Enter:**: react to that option

And the reboot options are:

- `Exit`: exit the reboot menu
- `Reboot`: reboot the device

## Battery info

On home page, short press the **Page \*** button and it will show the battery info.

You can short press the **Page \*** button to leave the battery info and back to homepage

## Device menu

On homepage, long press the **Page \*** button and it will show the device menu.

- **Page \***: switch the submenu
- **Enter**: enter the submenu

In each submenu, we have three options:

- `Leave`: leave the submenu and back to overview state
- `Save`: save the settings to the device
- A setting: that can be changed to enable/disable the feature

you can short press the **Page \*** button to switch the option, and short press **Enter** to apply/into that option.

When hovering over a specific setting, you can also short press **Enter** to enter/exit alignment changes, and use **Page \*** to toggle options while making changes.

You can then long press **Page \*** in the overview state of any submenu to return to the homepage.



### Camera protocol

Used to specify how the flowshutter interacts with the camera.

- `NO`: NO interact with the camera
- `MMTRY GND`: [Momentary Ground](clist.md#momentary-ground) on GPIO 25 (TX2)
- `3V3 Schmitt`: [3.3V Schmitt Trigger](clist.md#33v-schmitt-trigger) on GPIO 26 (RX2)
- `Sony MTP`: [Sony Multi-Terminal Port USB Protocol](clist.md#sony-multi-terminal-protocol) on UART2
- `ZCAM`: [ZCAM UART protocol](clist.md#zcam-uart-protocol) on UART2

When you change the camera protocol, please restart when you receive the restart prompt on the OLED to ensure that the relevant hardware devices are properly applied / the microcontroller is properly initialized.

!!! warning "Warning"
    Do not use the wrong camera protocol on devices that do not match. Otherwise, there may be a crash/port burnout/equipment loss of warranty or even fire!

Other protocols/mechenisms are under development.

### Device mode

Used to specify how the flowshutter works with the camera.

- `SLAVE`: The flowshutter is a slave device. It can passively monitor the camera recording state and toggle FC ARM/DISARM correspondingly.
- `MASTER`: The flowshutter is a master device. It can actively trigger camera record/stop and FC ARM/DISARM.
- `MASTER/SLAVE`: The flowshutter is a master/slave device. It can actively trigger camera record/stop and FC ARM/DISARM, or it can passively monitor the camera recording status to trigger FC ARM/DISARM.

### Injection mode

Used to specify whether flowshutter injects sync markers on the camera's audio track. This is so called "Audio Injection" feature.

- `ON`: Inject 25Hz sync marker on one of the audio track.
- `OFF`：No sync marker injection.

### Blackbox erase

Used to erase the blackbox data of the flowshutter.

- `Erase stop`: Stop the erase process.
- `Erasing...`: Start the erase process.

Once you hear a two short beep from the FC, it means the erase process is done.

!!! warning "Warning"

    The erasing process cannot be cancelled and the erased data cannot be retrieved!

