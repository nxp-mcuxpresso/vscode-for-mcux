# Known issues in MCUXpresso for VS Code extension

## General

* Temporary disabled MCUXpresso Installer integration.

* Some users might not see the latest 25.03 SDK version in the REMOTE ARCHIVE viewer when using the Import Repository feature. In this case, if after restarting VS Code the new version is still not visible on the list, please manually remove the cached version by following the next steps:
    - close VS Code
    - remove the content of the directory:
        - Windows: ~\AppData\Roaming\Code\User\globalStorage\nxpsemiconductors.mcuxpresso\file-downloader-downloads
        - macOS: ~/Library/Application Support/Code/User/globalStorage/nxpsemiconductors.mcuxpresso/file-downloader-downloads
        - Ubuntu: ~/.config/Code/User/globalStorage/nxpsemiconductors.mcuxpresso/file-downloader-downloads
    - open VS Code and retry the Import Repository -> REMOTE ARCHIVE viewer

## Debug

* For Zephyr projects, entering debug mode might show the PC cursor in a function called by main() instead of beginning of main(). This occurs because of the inlined calls inside main function. In order to avoid this behavior, set CONFIG_DEBUG_OPTIMIZATIONS=y in Kconfig configuration file and build the project again.
