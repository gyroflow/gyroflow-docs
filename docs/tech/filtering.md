For video stabilization, logging rates of at least 100 Hz of _clean_ data has shown to work, with _clean_ being the keyword. This page contains some info about the quality of the gyro data.

## Aliasing
For number one, adequate filtering should be applied before the saving step in order to satisfy the [Nyquist–Shannon sampling theorem](https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem). This may sound fancy, but just means the frequencies in the signal should be limited to at most, half the sampling frequency. For a 200 Hz logging rate, a low pass/decimation filter with a cutoff of about 100 Hz should be applied. Most MEMS gyroscopes contain on-board options for low pass filtering, but depending on the exact chip, this may not be adequate for handling harsh vibration-heavy environments on a drone.


## Gyro-camera coupling
The physical gyro should match the motion of the camera, meaning no or minimal play should be present between the two. This is not a problem for builtin gyro logging.

## Filtering
If no aliasing is present, the gyro data can be further filtered, assuming the sampling rate is sufficiently high. Roughly speaking, the frequencies of camera shake lie below 50 Hz. Frequencies above this could either be noise or high frequency signals resulting from high frequency, but low amplitude vibrations. 