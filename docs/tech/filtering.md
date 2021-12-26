## Logging rate

For video stabilization, logging rates of at least 100 Hz of _clean_ data has shown to work, with _clean_ being the keyword. The data should:
1. Be clear of aliasing
2. Match the camera orientation

For number one, adequite filtering should be applied before the saving step in order to satisfy the [Nyquist–Shannon sampling theorem](https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem). This may sound fancy, but just means the frequencies in the signal should be limited to at most, half the sampling frequency. For a 200 Hz logging rate, a low pass/decimation filter with a cutoff of about 100 Hz should be applied. Most MEMS gyroscopes contain onboard options for low pass filtering, but depending on the exact chip, this may not be adequite for handling harsh vibration-heavy environments on a drone.

In the second case, the physical gyro should match the motion of the camera, meaning no or minimal play should be present between the two.