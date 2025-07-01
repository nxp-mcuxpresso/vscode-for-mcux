# Known issues in MCUXpresso for VS Code extension

## General

* After upgrading to GNU Arm Toolchain 14.x, some projects, compatible with GNU Arm Toolchain 13.x, might fail to build. As a temporary solution, until we'll upgrade our MCUXpresso Installer to handle various versions of toolchains, please manually install a GNU Arm Toolchain 13.x version plus our compatible GNU Arm Toolchain add-on on top in order to work with:
    * MCUXpreso SDK older than v25.06
    * Projects from Application Code Hub compatible with MCUXpresso SDK older than v25.06
    * Matter 1.4.0.2

   To obtain a working version of this toolchain set, please:
    * Download and install GNU Arm Toolchain 13.2.Rel1, AArch32 bare-metal target (arm-none-eabi), from: https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads/13-2-rel1
    * Download and unzip our GNU Arm Toolchain addon for your preferred host operating system in the same location from one of the sources listed below:
        * https://www.nxp.com/lgfiles/updates/mcuxpresso/AdditionalCLibs-13.2.4-060924-win32.zip
        * https://www.nxp.com/lgfiles/updates/mcuxpresso/AdditionalCLibs-13.2.4-060924-linux.tar.xz
        * https://www.nxp.com/lgfiles/updates/mcuxpresso/AdditionalCLibs-13.2.4-060924-mac.tar.xz
        * https://www.nxp.com/lgfiles/updates/mcuxpresso/AdditionalCLibs-13.2.4-060924-mac.tar.xz


* Some users might not see the latest 25.03 SDK version in the REMOTE ARCHIVE viewer when using the Import Repository feature. In this case, if after restarting VS Code the new version is still not visible in the list, please manually remove the cached version by following the next steps:
    * Close VS Code
    * Remove the content of the directory:
        * Windows: %homepath%\AppData\Roaming\Code\User\globalStorage\nxpsemiconductors.mcuxpresso\file-downloader-downloads
        * macOS: ~/Library/Application Support/Code/User/globalStorage/nxpsemiconductors.mcuxpresso/file-downloader-downloads
        * Ubuntu: ~/.config/Code/User/globalStorage/nxpsemiconductors.mcuxpresso/file-downloader-downloads
    * Open VS Code and retry the Import Repository -> REMOTE ARCHIVE viewer

## Debug

* For Zephyr projects, entering debug mode might show the PC cursor in a function called by main() instead of beginning of main(). This occurs because of the inlined calls inside main function. In order to avoid this behavior, set CONFIG_DEBUG_OPTIMIZATIONS=y in Kconfig configuration file and build the project again.
