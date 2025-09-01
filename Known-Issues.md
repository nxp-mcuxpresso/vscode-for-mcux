# Known issues in MCUXpresso for VS Code extension

## General

* The build process may fail if any file paths involved exceed 260 characters. To avoid this limitation, shorten the project's directory path to ensure all file paths remain within the limit.
Build Failure Due to Spaces in File Paths

* The build process may encounter issues if any paths involved contain spaces. Avoid using spaces in project or repository paths.

* After upgrading to GNU Arm Toolchain 14.x, some projects, compatible with GNU Arm Toolchain 13.x, might fail to build. Please use GNU Arm Toolchain 13.2.Rel1 component available in MCUXpresso Installer for this purpose.

* Some users might not see the latest 25.03 SDK version in the REMOTE ARCHIVE viewer when using the Import Repository feature. In this case, if after restarting VS Code the new version is still not visible in the list, please manually remove the cached version by following the next steps:
    * Close VS Code
    * Remove the content of the directory:
        * Windows: %homepath%\AppData\Roaming\Code\User\globalStorage\nxpsemiconductors.mcuxpresso\file-downloader-downloads
        * macOS: ~/Library/Application Support/Code/User/globalStorage/nxpsemiconductors.mcuxpresso/file-downloader-downloads
        * Ubuntu: ~/.config/Code/User/globalStorage/nxpsemiconductors.mcuxpresso/file-downloader-downloads
    * Open VS Code and retry the Import Repository -> REMOTE ARCHIVE viewer

## Debug

* For Zephyr projects, entering debug mode might show the PC cursor in a function called by main() instead of beginning of main(). This occurs because of the inlined calls inside main function. In order to avoid this behavior, set CONFIG_DEBUG_OPTIMIZATIONS=y in Kconfig configuration file and build the project again.
