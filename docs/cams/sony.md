The following cameras are capable of native gyro data logging: a1, a7c, a7r IV, a7 IV, a7s III, a9 II, FX3, FX6, RX0 II, RX100 VII, ZV1, ZV-E10

This data is designed for use with Sony's [Catalyst Browse](https://www.sonycreativesoftware.com/catalystbrowse) stabilization which cannot stabilize footage shot with third-party lenses. Gyroflow supports reading this metadata natively, thus giving access to more smoothing algorithms and support for third-party lenses.


## General
It has been found that the above mentioned Sony cameras do not record motion data when capturing at **120 fps**.


## Sony a1/a7c/a7r IV/a7 IV/a7s III/a9 II

Since these cameras contain mechanical in-body image stabilization, this should be disabled when using Gyroflow. Even disabled, the sensor may still shift around in the presence of vibrations or strong accelerations. This is unlikely to be an issue with hand-held footage, but your mileage may vary.
