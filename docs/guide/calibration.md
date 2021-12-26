## Video guide
<iframe width="560" height="315" src="https://www.youtube.com/embed/f4YD5pGmnxM?start=412" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Getting calibration footage
1. Display the calibration pattern on a flat computer monitor, preferably in full screen. You can also print it out if you're old school.
2. Select the desired camera settings to calibrate for. Most importantly the field of view/focal length and aspect ratio, if applicable. Framerate and resolution doesn't matter, only if the resolution changes the field of view. Too low shutter speed may also cause undesirable motion blur, but it's usually fine.
3. Record your screen from a bunch of different angles and distances in one clip. 10-20 is more than enough. Hold the camera still in each angle to avoid motion blur and make sure the full chessboard is in view. The following angles are recommended for getting distortion information from the full frame:
   * Chessboard filling whole frame
   * Chessboard seen from distance.
   * Chessboard seen at an angle.
   * Each edge of video frame aligned with edge of chessboard.
   * Corner of chessboard aligned with corner of video.


## Creating camera preset
1. Start the Gyroflow tool, preferably the newest version
2. Open the camera calibrator utility.
3. Open calibration video file.
4. Either begin auto calibration or move playhead to clear frames.
5. Click `Add current frame` for each frame.
6. After adding the first couple frames, it can be useful to click `Process loaded frames` and check `Toggle lens correction` to check the undistorted result.
7. If result is totally wrong or the `RMS error` is very high after adding a frame, click `Remove last frame` or reopen file to reset calibration.
8. After all required frames are added and processed, the straight lines should be straight in the undistorted video. RMS error should be under 5 (pixels).
9. Fill in the preset information and export as a JSON file.
10. Feel free to send the file to be included as a default preset. Try to name the file something that uniquely identifies the camera + settings, e.g. `GoPro_Hero_8_4K_4by3_wide.json`.
