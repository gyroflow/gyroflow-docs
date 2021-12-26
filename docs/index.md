# Welcome to the Gyroflow Docs!

This site is currently under construction will eventually house all the info in one place. See http://gyroflow.xyz/ for now.


## Run using python and Poetry:
Note: Try the dev branch for the newest features.

* Install [poetry](https://python-poetry.org/docs/#installation)
* Clone or download the files from this repo
* Navigate to the folder using a commandline and install dependencies using `poetry install`
* Run the application using `poetry run python gyroflow.py`

## Other things to check out:
* [BlackboxToGPMF](https://github.com/Cleric-K/BlackboxToGPMF/tree/gui) by Cleric-K and Attilafustos. Tool for adding GoPro metadata and blackbox data to non-GoPro cameras for use with Reelsteady GO. Initial discussion [here](https://github.com/ElvinC/gyroflow/issues/1).
* [blackbox2gpmf](https://github.com/jaromeyer/blackbox2gpmf) by Jaromeyer. Tool for adding blackbox gyro data to Hero 7 files for Reelsteady Go.
* [Discord server](https://discord.gg/Rs4GBPm) maintained by [Nicecrash](https://www.youtube.com/channel/UCl3M972T7GbxnEucYHzZ05g) for discussion about gyroflow, BlackboxToGPMF, blackbox2gpmf and other related projects.
* [FPV Stabilization Tools Facebook group](https://www.facebook.com/groups/fpvtools) maintained by Attilafustos.


## General recording tips
* Use the settings that give the widest possible field of view (more data to work with). For a lot of cameras, this is in the 4:3 aspect ratio.
* If using the main drone flight controller for logging, the camera should be hardmounted.
* If using a secondary logger on the camera or internal camera logging, some soft mounting is preferred to isolate vibrations.
