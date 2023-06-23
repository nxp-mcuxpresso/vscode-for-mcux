# Known issues in MCUXpresso for VS Code extension

## Debug

* The program execution does not stop at main when entering into debug mode.

* Debugging and flashing Zephyr projects with LinkServer or PEmicro probes requires manual modifications of the .vscode/mcuxpresso-tools.json file. This is due to missing support for LinkServer device names in Zephyr environment.
    
    LinkServer: 
    ```
    Update device/core target names in "Project -> .vscode -> mcuxpresso-tools.json -> debug -> linkserver" using the following steps for a generic target "X":
        - go to `<LinkServer_layout>`
        - issue command: `LinkServer.exe devices -f X`
        - select the desired `<Device>:<Board>` peer from `Device` and `Board` columns and use it for `device` field
        - select the desired core from `Cores` column and use it for `core` field
        - Note. "primary" can be used for `core` field as an alias for the primary core.
    Hint: For more details on LinkServer command usage check the `<LinkServer_layout>/Readme.md`.

    Example for LPC55S69: `"device": "LPC55S69:LPCXpresso55S69"` and `"core": "cm33_core0"`.
    ```
    PEmicro:
    ```
    Update device/core target names in "Project -> .vscode -> mcuxpresso-tools.json -> debug -> pemicro" using the following steps:
        - go to `<PEmicro_layout>`
        - issue command: `pegdbserver_console.exe -deviceList`
        - select the desired device and use it for `device` field
    ```

* [macOS | Linux] Unable to start debug session on consecutive quick attempts using LinkServer debug probe.\
    **Workaround**: wait for ~1 min (connection socket timeout) and retry.

* Semihosting support might not work for older SDK versions. If this is the case, please check mcux_config.cmake file inside your SDK (for standalone SDK in: tools/cmake_toolchain_files, for GitHub SDK in core/tools/cmake_toolchain_files) and:
    - remove --specs=rdimon.specs (remove _"set(SPECS "--specs=rdimon.specs" PARENT_SCOPE)"_ line)
    - replace "${DEBUG_CONSOLE}_CONFIG" with "DEBUG_CONSOLE_CONFIG"
    
    Before:
    ```
    if(${DEBUG_CONSOLE} MATCHES "SEMIHOST")
        set(SPECS "--specs=rdimon.specs" PARENT_SCOPE)
        set(${DEBUG_CONSOLE}_CONFIG "-DSDK_DEBUGCONSOLE=0" PARENT_SCOPE)
    else()
        set(SPECS "--specs=nano.specs --specs=nosys.specs" PARENT_SCOPE)
        set(${DEBUG_CONSOLE}_CONFIG "-DSDK_DEBUGCONSOLE=1" PARENT_SCOPE)
    endif()
    ```
    After:
    ```
    if(${DEBUG_CONSOLE} MATCHES "SEMIHOST")
        set(DEBUG_CONSOLE_CONFIG "-DSDK_DEBUGCONSOLE=0" PARENT_SCOPE)
    else()
        set(SPECS "--specs=nano.specs --specs=nosys.specs" PARENT_SCOPE)
        set(DEBUG_CONSOLE_CONFIG "-DSDK_DEBUGCONSOLE=1" PARENT_SCOPE)
    endif()
    ```

## Project Importer

* MCUXpresso IDE projects built with redlib library type will not be converted.\
    **Workaround**: Switch MCUXpresso IDE project to Newlib or Newlib_nano library types then rebuild inside IDE. The project can be then converted.

* Import does not work for standalone multicore or trustzone example projects downloaded from mcuxpresso.nxp.com.

* Some projects imported from MCUXpresso SDKs might not build. This is due to missing component sources that are located outside example directory, so these are not cloned.

## Views

* [Projects View] For Zephyr projects, the Memory node is not showing any data.
