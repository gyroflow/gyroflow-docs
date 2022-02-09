
## General recording tips
* Use the settings that give the widest possible field of view. This results in more data to work with. For a lot of cameras, this is using the 4:3 aspect ratio if available.
* If using the main flight controller on a drone for logging, the camera should be rigidly mounted to the drone.
* If using a secondary logger on the camera or internal camera logging, some soft mounting is preferred when used in a high-vibration environment (drones).
* Internal stabilization should be disabled. Furthermore, trying to stabilize footage from a camera with IBIS may result in wobble due to the sensor shifting around.
* In filmmaking, the 180 degree shutter rule is commonly used (shutter speed half of framerate). Depending on your use case and amount of shake, applying Gyroflow stabilization may result in undesired motion blur artifacts. A 90 degree shutter is typically a good compromise between artifacts and pleasing motion blur, and is thus a good starting point. Even higher shutter speeds can make the footage look less "cinematic" due to the lack of motion blur. If you're only concerned about stabilization, a higher shutter speed is generally better.