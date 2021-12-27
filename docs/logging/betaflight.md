Betaflight/Cleanflight/Inav/Emuflight/etc form a popular family of flight control firmware for high-performance multicopters. By using the built-in blackbox logging feature, gyro data for use with Gyroflow video stabilization can be collected. This was in fact one of the initial goals of the project! Betaflight, Cleanflight, Inav, Emuflight etc. all use more or less the same structure for handling blackbox data logging, so this page covers all of these.


## Hardware
As you may already know, the above mentioned flight firmwares can all run on the same type of hardware. A flight controller supporting this family of flight firmwares typically contain:

* STMicroelectronics 32 bit microcontroller (F4, F7, H7)
* MEMS inertial measurement unit (MPU6000, BHI160, ICM2xxxx, ICM4xxxx etc.)

Some flight controllers have an onboard magnetometer. In general, this is not required for video stabilization purposes unless absolute orientation is desired.

Different gyros exhibit different behaviors in terms of data quality, noise, etc. In general, if the IMU is capable of providing clean data for the drone control loop, the same data is suitable for video stabilization purposes.

For blackbox data logging, the hardware typically either contains an onboard SPI Flash chip, or a slot for an SD card. If neither of these are available, additional hardware solutions can be connected to the flight controller in order to enable blackbox logging. This can be using:

* [The Openlager](https://github.com/d-ronin/openlager) - A open source and commercially available board containing an STM32f4 and a MicroSD slot for logging high rate data through a spare serial port.
* [Tiny Blackbox](https://github.com/alexeystn/tiny-blackbox) - An open source ultra-light logger containing a 16 MB flash chip.
* <del>[SparkFun OpenLog](https://github.com/sparkfun/OpenLog)</del> - A serial-based logger similar to the Openlager. This is no longer officially supported by Betaflight etc. due to data rate limitations. 


## Betaflight/(Cleanflight/Emuflight?)

Required software:

* Betaflight/Cleanflight/Emuflight configurator
* Betaflight blackbox explorer

The following should be a decent starting point for the blackbox configuration

* 500 Hz logging rate
* Debug mode: `None`

If you're running Betaflight 4.3 or newer, it is possible to deselect specific elements of the data logging in order to save precious recording space. From the CLI:
```
set blackbox_disable_pids = ON
set blackbox_disable_rc = ON
set blackbox_disable_setpoint = ON
set blackbox_disable_bat = ON
set blackbox_disable_mag = ON
set blackbox_disable_alt = ON
set blackbox_disable_rssi = ON
set blackbox_disable_debug = ON
set blackbox_disable_motors = ON
set blackbox_disable_gps = ON
```

![!Betaflight configurator blackbox tab](img/config-blackbox.jpg){ width="100%" }