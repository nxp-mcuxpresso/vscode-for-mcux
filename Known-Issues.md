# Known issues in MCUXpresso for VS Code extension

## General

* Temporary disabled MCUXpresso Installer integration.

## Debug

* For Zephyr projects, entering debug mode might show the PC cursor in a function called by main() instead of beginning of main(). This occurs because of the inlined calls inside main function. In order to avoid this behavior, set CONFIG_DEBUG_OPTIMIZATIONS=y in Kconfig configuration file and build the project again.
