# General

Welcome to Camera and Gyro Logging Guide!

This page contains some useful information about camera settings and supported gyro data formats. For more details, please refer to the left navigation bar.

## Camera Recording Tips

- **Use the settings that give the widest possible field of view.** This results in more data to work with. For a lot of cameras, this is using the 4:3 aspect ratio if available.
* If using the main flight controller on a drone for logging, the camera should be rigidly mounted to the drone.
* If using a secondary logger on the camera or internal camera logging, some soft mounting is preferred when used in a high-vibration environment (drones).
- **Internal stabilization should be disabled.** Furthermore, trying to stabilize footage from a camera with IBIS may result in wobble due to the sensor shifting around.
* **A 90 degree shutter is typically a good compromise between artifacts and pleasing motion blur, and is thus a good starting point.** In filmmaking, the 180 degree shutter rule is commonly used (shutter speed half of framerate). Depending on your use case and amount of shake, applying Gyroflow stabilization may result in undesired motion blur artifacts. Note that even higher shutter speeds can make the footage look less "cinematic" due to the lack of motion blur. If you're only concerned about stabilization, a higher shutter speed is generally better.


## Supported gyro formats

Gyroflow needs a source of gyroscope data (and optionally accelerometer data) to operate. Currently, Gyroflow supports the following gyro log types:

- GoPro (All models with gyro metadata, starting with HERO 5)
- Sony (a1, a7c, a7r IV, a7 IV, a7s III, a9 II, FX3, FX6, RX0 II, RX100 VII, ZV1, ZV-E10)
- Insta360 (OneR, SMO 4k, GO2)
- DJI (Avata, O3 Airunit, ...)
- Betaflight blackbox (CSV and binary)
- Runcam CSV (Runcam 5 Orange, iFlight GOCam GR)
- Hawkeye Firefly X Lite CSV
- WitMotion (WT901SDCL binary and *.txt - devices unreliable)
- Mobile apps: `Sensor Logger`, `G-Field Recorder`, `Gyro`
- Gyroflow [.gcsv log](https://docs.gyroflow.xyz/logging/gcsv/)
- ArduPilot VideoStabilization logging (*.log)
- **(TODO)** DJI flight logs (*.dat, *.txt)
