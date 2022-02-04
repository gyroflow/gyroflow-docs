## Minimum system requirements:
- Windows 10 64-bit (1809 or later)
- macOS 10.14 or later (both Intel and Apple Silicon are supported natively)
- Linux: 
    - `.tar.gz` package (recommended): Debian 10+, Ubuntu 18.10+, CentOS 8.2+, openSUSE 15.3+. Other distros require glibc 2.28+ (`ldd --version` to check)
    - `.AppImage` should work everywhere
    - Make sure you have latest graphics drivers installed
    - Possibly needed packages: `sudo apt install libva2 libvdpau1 libasound2 libxkbcommon0 libpulse0 libc++-dev vdpau-va-driver libvulkan1`
    - GPU specific packages: 
        - NVIDIA: `nvidia-opencl-icd nvidia-vdpau-driver nvidia-egl-icd nvidia-vulkan-icd libnvcuvid1 libnvidia-encode1`
        - Intel: `intel-media-va-driver i965-va-driver beignet-opencl-icd intel-opencl-icd`
        - AMD: `mesa-vdpau-drivers mesa-va-drivers mesa-opencl-icd libegl-mesa0 mesa-vulkan-drivers`
- Android 6+

## Releases
Prebuilt executables are available for Windows, Mac, and Linux. These can be found on the [releases page](https://github.com/gyroflow/gyroflow/releases)


## Build local version

For development purposes, a local version can be built. For instructions, see the [README on GitHub](https://github.com/gyroflow/gyroflow#development):