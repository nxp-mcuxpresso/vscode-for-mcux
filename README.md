# NXP MCUXpresso for VS Code extension

The NXP's MCUXpresso for VS Code extension makes NXP devices (based on ARM Cortex-M cores) easy to use right from Microsoft Visual Studio Code environment.

For complete details follow the [wiki](https://github.com/nxp-mcuxpresso/vscode-for-mcux/wiki) section.

## Overview:

* Support MCUXpresso SDK, Zephyr and Open-CMSIS-Pack software repositories integration.
* Integration with [MCUXPresso SDK builder](https://mcuxpresso.nxp.com).
* Dependency tools and software components can be installed using [MCUXpresso Installer](https://github.com/nxp-mcuxpresso/vscode-for-mcux/wiki/Dependency-Installation)
* Wizard view to import repository from remote or local GitHub or from a standalone archive (MCUXpresso SDK).
* Wizard to import a project example from an installed repository.
* Support for importing all application types for Zephyr (repository, workspace, freestanding).
* Integration with standalone MCUXpresso Config Tools and MCUXpresso SEC Security Tool.
* Option to import an existing CMake project.
* Support for importing existing executables.
* Project converter from MCUXpresso IDE (Eclipse) to MCUXpresso for VS Code extension. 
* Project view displaying information about: software repository, build configurations, MCU device and memory details.
* Project options to manage components, build, flash and debug.
* Build configuration GUI editor.
* Device Tree viewer, Kconfig syntax highlighting for Zephyr support, context options to open interactive Kconfig interface (guiconfig) and integrated terminal for Zephyr based environment.
* Integrated with existing VS Code support for managing files, editing facilities, source control.
* Detailed analysis of an application image structure (Callgraph and Memory details inside Image Info viewer).
* Various binary utilities (to create bin, hex or S-Record type of images, executable information) accessible right from the context menu of executable files.
* Single/multi core [ARM Cortex-M] debug support relying on Microsoft's "C/C++" extension.
* Debug support for J-Link, LinkServer and PEmicro probes with detection for available connected devices.
* Support for LPC, Kinetis microcontrollers and i.MX RT crossover processors.
* Dedicated Flash Programmer GUI.
* Baremetal Heap and Stack debug viewer.
* Integration with "Serial Monitor" extension for UART and semihosting console support.
* SWO console for monitoring debug messages transmitted using ITM.
* Online and offline Peripherals viewer.
* Quickstart panel view with quick access to various operations, including import project, flash programmer interface, links to documentation.
* Integration with NXP Application Code Hub.
* Support for Windows, Ubuntu and macOS.

## Known issues

See [Known issues](https://github.com/nxp-mcuxpresso/vscode-for-mcux/blob/main/Known-Issues.md) section for detailed list.

## License

[NXP Software License Agreement](https://www.nxp.com/docs/en/disclaimer/LA_OPT_NXP_SW.html)

## Telemetry

MCUXpresso for VS Code extension uses Microsoft telemetry. This allows us to collect usage data and continuously improve the extension and user experience. Storage mechanism follows the VS Code telemetry enablement ("telemetry.telemetryLevel" setting option). Read [Microsoft Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement) for more details.
