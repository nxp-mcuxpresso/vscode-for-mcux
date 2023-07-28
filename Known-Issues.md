# Known issues in MCUXpresso for VS Code extension

## Debug

* For older created projects, due to newest toolchain (12.x) update, starting a debug session might be very slow.\
   **Workaround** Add the following option to your launch.json file:
    ```
    "setupCommands": [
        {
          "text": "set debug-file-directory"
        }
    ]
    ```

* The program execution sometimes stops before main when starting debug session.\
    **Workaround** Resume application, it will then stop at main.

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

* Conversion for MCUXpresso IDE projects built with redlib library type is not supported.\
    **Workaround**: Switch MCUXpresso IDE project to Newlib or Newlib_nano library types then rebuild inside IDE. The project can be then converted.

* Conversion for MCUXpresso IDE projects for static libraries is not supported.

## Views

* [Projects View] For Zephyr projects, the Memory node is not showing any data.