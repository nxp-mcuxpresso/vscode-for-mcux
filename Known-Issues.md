# Known issues in MCUXpresso for VS Code extension

* [MCUXpresso SDK Integration][Multicore] Primary core projects do not build.\
**Workaround**: target_include_directories from CMakeLists.txt of the primary core should include proper directory path to the other cores images.

* [Projects view] For Zephyr projects, the Memory and Components nodes are not showing any data. This will be implemented in a further release.

* [Debug] Zephyr projects cannot be debugged with LinkServer probe. This is due to missing support for LinkServer device names in Zephyr environment. This will be added in a future release of MCUXpresso VS Code extension and Zephyr project.\
**Workaround**: Place the LinkServer device/board/core target names on *Project -> .vscode -> launch.json -> variables -> mcuxDevice and mcuxLinkServerCore*.\
    Example for LPC55S69: `"mcuxDevice": "LPC55S69:LPCXpresso55S69"` and `"mcuxLinkServerCore": "cm33_core0"`.\
    Example for a generic target "X":\
        - go to `<LinkServer_layout>`\
        - issue command: `LinkServer.exe devices -f X`\
        - select the desired `<Device>:<Board>` peer from `Device` and `Board` columns and use it for `mcuxDevice` field\
        - select the desired core from `Cores` column and use it for `mcuxLinkServerCore` field\
        - Note. "primary" can be used for `mcuxLinkServerCore` field as an alias for the primary core.\
    Hint: For more details on LinkServer command usage check the `<LinkServer_layout>/Readme.md`.\

* [Flash Programmer] Flash programmer not working with Zephyr projects on LinkServer debug probes.

* [Debug Semihosting] Semihosting support might not work for older SDK versions. If this is the case, please check mcux_config.cmake file inside your SDK (for standalone SDK in: tools/cmake_toolchain_files, for GitHub SDK in core/tools/cmake_toolchain_files) and replace "${DEBUG_CONSOLE}_CONFIG" with "DEBUG_CONSOLE_CONFIG")

* [Debug Semihosting] In certain situations, going into debug mode might not end up in reaching "main" (but some startup execution point). If this is the case, just issue "Resume" command and the code will stop at "main". This will be fixed in next version.
