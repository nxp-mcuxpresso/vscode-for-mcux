# NXP MCUXpresso for VS Code extension

The NXP's MCUXpresso for VS Code extension makes NXP devices (based on ARM Cortex-M cores) easy to use right from Microsoft Visual Studio Code environment.

## Overview:

* Support MCUXpresso SDK, Zephyr and Open-CMSIS-Pack software repositories integration.
* Dependency tools and software components can be installed using [MCUXpresso Installer](https://github.com/nxp-mcuxpresso/vscode-for-mcux/wiki/Dependency-Installation)
* Wizard view to import repository from remote or local GitHub or from a standalone archive (MCUXpresso SDK).
* Wizard to import a project example from an installed repository.
* Support for importing all application types for Zephyr (repository, workspace, freestanding).
* Option to import an existing CMake project.
* Project converter from MCUXpresso IDE (Eclipse) to MCUXpresso for VS Code extension. 
* Project view displaying information about: software repository, build configurations, MCU device and memory details.
* Project options to manage components, build, flash and debug.
* Project context options to switch "Floating Point", "C Library", and "Debug Console" types.
* Device tree viewer, Kconfig syntax highlighting for Zephyr support, context options to open interactive Kconfig interface (guiconfig) and integrated terminal for Zephyr based environment.
* Integrated with existing VS Code support for managing files, editing facilities, source control.
* Detailed analysis of an application image structure (Callgraph and Memory details inside Image Info viewer).
* Various binary utilities (to create bin, hex or S-Record type of images, executable information) accessible right from the context menu of executable files.
* Single core [ARM Cortex-M] debug support relying on Microsoft's "C/C++" extension debug support.
* Debug support for J-Link, LinkServer and PEmicro debug probes with detection for available connected devices.
* Support for LPC, Kinetis microcontrollers and i.MX RT crossover processors.
* Dedicated Flash Programmer GUI.
* Baremetal Heap and Stack debug viewer.
* Integration with "Serial Monitor" extension for UART and semihosting console support.
* Quickstart panel view with quick access to various operations, including import project, flash programmer interface, links to documentation.
* Support for Windows, Ubuntu and macOS.

## Changelog

See [Changelog](CHANGELOG.md) section for detailed list.

## Known issues

See [Known issues](Known-Issues.md) section for detailed list.

## License

[NXP Software License Agreement](https://www.nxp.com/docs/en/disclaimer/LA_OPT_NXP_SW.html)