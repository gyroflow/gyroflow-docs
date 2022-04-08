Flowshutter has many settings to allow you to use it in different situations. This page contains a short description and guide to each of the settings. Luckily, many of the settings are self-explanatory.

## User Interaction System

There are two buttons on the flowshutter, one is called "PAGE" and another is called "ENTER". There are no difference between long press and short press - once it detects the button pressed, it will react immediately.

- **PAGE**: Navigate between different setting pages.
- **ENTER**: Change the setting, enter the mode.

## Device settings

You can simply use the PAGE keys to cycle through device settings.

- **Idle** => **Battery info** => **[Camera protocol](#camera-protocol)** => **[Device mode](#device-mode)** => **[Injection mode](#injection-mode)** => **Idle**

### Camera protocol

Used to specify how the flowshutter interacts with the camera.

- **Sony MTP**: [Sony Multi-Terminal Port USB Protocol](camera%20list.md#sony-multi-terminal-protocol) on UART2
- **MMTRY GND**: [Momentary Ground](camera%20list.md#momentary-ground) on GPIO 25 (TX2)
- **3V3 Schmitt**: [3.3V Schmitt Trigger](camera%20list.md#33v-schmitt-trigger) on GPIO 26 (RX2)
- **NO**: NO interact with the camera

When you change the camera protocol, please restart when you receive the restart prompt on the OLED to ensure that the relevant hardware devices are properly applied / the microcontroller is properly initialized.

**Do not use the wrong camera protocol on devices that do not match. Otherwise, there may be a crash/port burnout/equipment loss of warranty or even fire!**

Other protocols/mechenisms are under development.

### Device mode

Used to specify how the flowshutter works with the camera.

- **SLAVE**: The flowshutter is a slave device. It can passively monitor the camera recording state and toggle FC ARM/DISARM correspondingly.
- **MASTER**: The flowshutter is a master device. It can actively trigger camera record/stop and FC ARM/DISARM.
- **MASTER/SLAVE**: The flowshutter is a master/slave device. It can actively trigger camera record/stop and FC ARM/DISARM, or it can passively monitor the camera recording status to trigger FC ARM/DISARM.

### Injection mode

Used to specify whether flowshutter injects sync markers on the camera's audio track. This is so called "Audio Injection" feature.

- **ON**: Inject 25Hz sync marker on one of the audio track.
- **OFF**：No sync marker injection.

## Internet settings

Press ENTER on the battery info page to enter the Internet settings.

- **Battery info** =(ENTER)=> **[Internet connection](#internet-connection)** =(failed)=(PAGE)=> **Idle**
- **Battery info** =(ENTER)=> **[Internet connection](#internet-connection)** =(success)=(PAGE)=> **[OTA source](#ota-source)** => **[OTA channel](#ota-channel)** => **[Start OTA update](#start-ota-update)** => **Idle**

### Internet connection

Press ENTER to toggle the internet connection.

Flowshutter will firstly check SSID and password in `wifi.dat` file, if it is not found, it will scan the nearby WiFi APs, later flowshutter will create an AP and host a web server which lists nearby WiFis and allows users to select the WiFi they want to connect to and type password for that.

- **SSID**: `Flowshutter`
- **Password**: `ilovehugo`
- **Wifi selector webpage address**: `192.168.4.1`

Once submitted, flowshutter will connect to the selected WiFi. Then enable `OTA source`, `OTA channel` and `Start OTA update` pages.

### OTA source

OTA is done by pulling the source code from the GitHub repository. For some Chinese users, the access to GitHub's raw content is blocked, so we set up a mirror source of the flowshutter source code on Gitee to facilitate their OTA.

- **GitHub**: `https://raw.githubusercontent.com/gyroflow/flowshutter/*/*.py`
- **Gitee**: `https://gitee.com/dusking1/flowshutter/raw/*/*.py`

### OTA channel

Since our development work lacks automated testing methods to ensure quality, we cannot guarantee that users can perform secure OTA anytime, anywhere, so we have set up three OTA channels.

- **STABLE**: `stable` branch, recommended for general users.
- **BETA**: `beta` branch, recommended for testers.
- **DEV**: `master` branch in flowshutter repository. Only for developers.

### Start OTA update

(WIP)
