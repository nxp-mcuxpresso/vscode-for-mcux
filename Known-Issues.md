# Known issues in MCUXpresso for VS Code extension

## Debug

* In the current version, there is no dedicated extra Debug RTOS view, except for the Call Stack thread awareness capability.

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
