In collaboration with DJI we created a Gyroflow compatible way to store motion data and more camera information for the stabilization process inside 
video files. To make the experience in Gyroflow as easy and reliable as possible, the video contains the factory lens profile and frame based motion data.
After loading a video, the stabilized preview is ready to export and no sync-points are needed.

##General
In order to record open gyro data for Gyroflow , DJI products use the same concept. The internal image stabilization (EIS), Rocksteady must be disabled
and the WIDE lens profile needs to be selected. 

## DJI Avata
The Avata was the first collaboration with the development team at DJI, and it is the first product from DJI with Gyroflow support out of the box. 

  To record for Gyroflow:
  
    - EIS disabled
    - WIDE lens profile
    - 4K and 2.7K  4:3
    - 4K and 2.7K  16:9
    
## DJI O3 AirUnit
DJI surprised us with the O3 Airunit and the idea of combining a digital-HD FPV stack and an Actioncam with Gyroflow support in one unit. The hardware is
similar to the Action 2 and allows improving the FPV experience for "homemade" DIY drones and all sorts of FPV platforms.
Like the Avata, the O3 Airunit can record motion data :

  To record for Gyroflow:
  
    - EIS disabled
    - WIDE lens profile
    - 4K and 2.7K  4:3
    - 4K and 2.7K  16:9
    
To use the O3 EIS/Rocksteady and in order to record for Gyroflow on drones, it's often necessary to isolate the motion sensor inside the camera module 
from vibrations. Stiff carbon camera plates and ALU camera cages allow vibrations to travel to the camera and to influence the IMU. It's recommended to isolate
the camera using a 3D printed TPU mount to fix the issue in most cases. 
RPM filters in Betaflight should be configured correctly in order to get the best Gyroflow performance and image quality. For certain drone and prop sizes,
it's necessary to set the ESC PWM control frequency to 48 kHz or higher. 

## DJI Action 2 - closed BETA (V 01.04.04100)
Finally, the Action 2 get's it well deserved Gyroflow support and a group of Testers, selected by DJI after registration, is currently testing 
a beta firmware. The experience so far is very positive and we identified a few bugs that will be addressed in the next firmware.
 
  To record for Gyroflow:
  
     - EIS disabled
     - WIDE lens profile
     - 4K 4:3   24-60 fps
     - 4K 16:9  100/120 fps
     
     Not working ( V 01.04.04100 bug )
     - 4K 4:3 50 


## Using DJI open gyro data to stabilize a different camera:
DJI doesn't record RAW IMU data, only Quaternions - "frame based motion data" useable to stabilize other cameras. It's necessary to sync the
external video source and the motion data provided by Action 2 or O3 Airunit. 

    - Use the Integration method: None
    - Right click on timeline -> View mode: Quaternions
    - Make sure to set large enough Sync search size
    

