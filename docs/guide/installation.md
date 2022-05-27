# Installation

## Minimum system requirements:

Here are the Gyroflow minimum requirements:

- Windows 10 64-bit (1809 or later)
    - Windows "N" versions: Install the "Media Feature Pack", go to Settings -> Apps -> Optional features -> Add a feature -> Select "Media Feature Pack" -> Click Install
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

## Official Releases

Prebuilt executables are available for Windows, Mac, and Linux. These can be found on the [GitHub Releases](https://github.com/gyroflow/gyroflow/releases)


## Nightly builds

In some cases you may need to [download the latest nightly build](https://gyroflow.xyz/devbuild/?autodownload):

- For example, a known bug was fixed in the nightly build and you need to use it urgently.
- Or, you want to see how the latest committed translation actually works in the app, Whether the translation needs to be fine-tuned to match the overall translation style.

In general, however, we discourage casually trying nightly builds unless you know what you're doing!


## Build local version

For development purposes, a local version can be built. For the building instructions, see the [development section on GitHub](https://github.com/gyroflow/gyroflow#development):
