# MCUXpresso for VS Code Changelog

## Version 25.02

### Zephyr

- Ability to change the board for an existing project.

### Debugger

- Added RTOS DETAILS view for Threads/Tasks monitoring on Zephyr and FreeRTOS.
- Added "instruction stepping mode" source vs. instruction switch option in debug toolbar.
- Variable location is now displayed in tooltip.
- Option to "Show in Memory Inspector" added in variable's context menu.
- Ability to install watchpoints(data breakpoints) by specifying the address range.
- Added support for setting breakpoint type (hardware vs. software).
- Added progress bar for all flash type operations.
- Shorten the file paths displayed in the stack frames so now the file names are visible.

### General

- Integration with MCUXpresso Installer, ability to check and warn (badge notification on extension icon) for missing tools dependencies when starting the extension.
- Added option to open an MCUXpresso Terminal (dedicated Python virtual environment, environment variables, etc.).
- File view mode from Image Info now shows the symbols in a hierarchical file/directory structure (similar to Zephyr's west build -t <ram|rom>_report options).

### Project Management

- "Associate Repository/Toolchain" options indicate current selections.

## Version 24.12

### General

- Added support for Matter (full support for NXP downstream of the Matter repository v1.4.0).
- Added automatic device detection/checks for CMSIS-DAP based debug probes with target information available.

## Version 24.11 Preview

Added preliminary support for [MCUXpresso SDK version 24.12](https://github.com/nxp-mcuxpresso/mcuxsdk-manifests). The SDK will be available in January 2025.

### General

- Added New Project Wizard for Zephyr and MCUXPressso SDK based projects.
- Added Binary Utilities option in Projects view context menu.

### Debugger

- Added Refresh button in Variables, Watch and Live Watch views.
- Added option to set the --override option when invoking LinkServer.
- Memory view has now ASCII option enabled by default.
- Fixed variable support inside debug configuration file (launch.json).
- Fixed unexpected context switch to secondary core once primary core is resumed.

### Zephyr

- Fixed import for existing Zephyr projects.

## Version 24.10

### Debugger

- Migrated from Microsoft C/C++ Debug Adapter to own solution based on the popular Cortex-Debug solution. Existing projects are automatically migrated to the new debug adapter.
- Support for hardware breakpoints.
- Integrated Memory Inspector extension from Eclipse CDT Cloud.
- Fixed run control options on multicore debugging.
- Debugger now stops at main symbol, overcoming the scenario in which additional "Continue" was necessary to reach main().
- Ability to load extra image files or symbol files to a debug session.

### General

- Added "Duplicate" option for build configuration.
- Provide better filtering/searching on Open-CMSIS-Pack remote packs list.

## Version 24.9

### Project Management

- It is now possible to stop the build process ("Cancel" button while building).
- Added "Open CMake presets" button option in "Build Configuration" window for users seeking to add advanced build options.
- Added progress bar when importing projects (useful for large projects).

### MCUXpresso SDK

- Added device "Change package" toolbar entry in Projects View - MCU node.

### Imported Repositories

- Added option to retry west init/update operation in case of repository installation failures.
- Unregister repository ("Remove Repository from Workspace") added in the repository context menu.

### General

- Drag and drop file support from Project View (or VS Code File Explorer) to Image Info.

## Version 24.8 hotfix

### General

- Fixed build errors not appearing in Problems view.

## Version 24.8

### General

- Added file support in Project View.
- CMake presets are no longer duplicated when editing custom build configurations.

### Zephyr

- Added "Associate Repository" option for Zephyr projects.

## Version 24.7

### General

- Extension versioning schema changed to YY.MM.build_number.
- Sped up LinkServer debug probe discovery.
- Improved error handling on Application Code Hub when there is no internet connection.
- Fixed empty shown nodes (instead source file path) for some symbols on Image Info - File section.
- Fixed some scenarios where spaces inside paths produce failures in calling system commands.

### Zephyr

- Sysbuild option is enabled automatically if required by the example.

## Version 1.10.128 hotfix

### General

- Some projects are not successfully converted from CMake kits to CMake presets.

## Version 1.10 (2024.06)

### General

- Added Build Configuration GUI editor.
- Switched from using CMake kits to CMake presets.
- Integration with MCUXpresso Security Provisioning Tool.
- Import repository now notifies the user in case there is not enough space left on the disk.
- Tasks are now used for importing a remote repository; all the commands issued, and their progress are now visible.

### Zephyr

- Support for changing name, build directory, optimization level, and adding extra CMake arguments directly from the new build configuration editor.
- Added support for populating binary blobs from NXP HAL.

### MCUXpresso SDK

- Support for changing name, library type, debug console, floating point, and adding extra CMake arguments directly from the new build configuration editor.

### Eclipse Project Converter

- Implemented conversion for linked libraries and projects without managed linker scripts enabled.

## Version 1.9 (2024.05)

### General

- Added support to work with Python virtual environment.
- Added "Report MCUXpresso for VS Code issue" button in Quickstart Panel view.

### Zephyr

- Fixed overlay file support on Hardware Model v2.
- Improved the data loading speed in DeviceTree viewer.

### Debugger

- Added SWO console for monitoring debug messages transmitted using ITM.

## Version 1.7 (2024.03)

### General

- Added Redlib library support (NXP (non-GNU) ISO C90 standard C library, with some C99 extensions).

>**Note:** Redlib support only works for projects converted from MCUXpresso IDE. For imported SDK examples switching to Redlib is not supported. This will be addressed in a future release.

>**Note:** Redlib is provided by the NXP Toolchain Add-on pack distributed by the MCUXpresso Installer and it comes installed on top of an Arm GNU Toolchain distribution. Be sure you have 12.3.2 or newer version of NXP Toolchain Add-on in order to have Redlib support added. Alternatively, the toolchain provided by MCUXpresso IDE can be used, which already contains Redlib support. Also, MCUXpresso SDK 2.15 or newer has to be used in order to provide integration support of Redlib.

### Zephyr

- Added support for Zephyr Hardware Model v2.
- Added support for Sysbuild (System build).
- Import example wizard now shows better descriptive names for boards and templates lists.
- Support for adding additional overlay files using CMake variables.
- Flash Programmer writes the signed binary file in case it exists (for instance signed binaries for use with the MCUboot bootloader).

### Eclipse Project Converter

- Conversion now supports existing MCUXpresso IDE projects created with Redlib library support.

## Version 1.6 (2024.02)

### General

- List of available toolchains is now sorted from newest to oldest version.
- Location field value is now persisted between VS Code sessions.

### Project Management

- Ability to delete/remove multiple projects at once from Projects view.
- Added the option to not rebuild the project when debugging.
- Reduced the number of absolute paths from the generated JSON files. Only toolchain and repository paths have remained absolute, but they can be overridden using environment variables.

### Zephyr

- Update repository operation now performs a pull from remote before doing `west update`.
- Added support for importing mcuboot as a freestanding/workspace application.
- Reverted change introduced in 1.5 that disabled optimizations by default for debug build configuration as it may result in linker errors and board configuration files being ignored.

### Eclipse Project Converter

- FPU options are no longer added when converting projects for non-FPU devices.

## Version 1.5 (2024.01)

### General

- Integration with [MCUXPresso SDK builder](https://mcuxpresso.nxp.com).
- Ability to import repository using SSH with password protected keys.

### Debugger

- Added online peripherals view.
- Added jtag and speed options for PEmicro debug connection (in launch.json configuration file).

### Project Management

- Switched to VS Code tasks for project build/clean/rebuild (for all type of repositories, except Open-CMSIS-Pack).
- Avoided unnecessary rebuild project when no sources are modified.

### Zephyr

- Compiler optimizations are disabled by default for debug build configuration.

### Analysis Tools

- Image Info now shows additional tree of symbols organized by file.

### Application Code Hub

- Cloned repository is now added to Imported Repositories view. This also offers facility to manage the repository and import available projects. All ACH cloned repositories appear under a single "Application Code Hub" root node.
- MCUXpresso IDE and VS Code options are preselected by default in order to only lists "compatible" projects.

### Eclipse Project Converter

- Added support for Eclipse projects containing Open-CMSIS packs.

## Version 1.4 (2023.11)

### Project Management

- Projects view now indicates origin repository type and version in line with project name.
- Added possibility to change the toolchain for a project (project context menu -> Configure -> Associate Toolchain).
- Paths specified in project settings (i.e. "toolchainPath" and "sdk.path" options from mcuxpresso-tools.json file) can now be defined using variables (userHome, workspaceFolder, workspaceFolderBasename, pathSeparator).
- Changed to CLRF on Windows for ide_overrides.cmake generated file.

### Eclipse Project Converter

- Fixed wrong repository information displayed when no SDK is associated with the project.
- Fixed missing sources in a special case of excluded directories from Eclipse project.

### Zephyr

- Device and core are automatically determined when debugging a Zephyr project with LinkServer debug probe.
- Applications can now be debugged from SDRAM (added SEGGER resetAfterLoad debug option. When this option is not provided, a reset is only sent if it can be determined that the project is in flash).

### MCUXpresso SDK

- Fixed error reported when importing a local archive with very long paths.
- Importing an SDK archive will no longer be removed in case of Git error.

### Analysis Tools

- Image Info now displays sections and symbols in Memory tree even if no map file is available.

### Debugger

- Added offline peripherals view (open by default). SVD files can be loaded and inspected without an active debug session.

## Version 1.3.59 hotfix

### MCUXpresso Installer Integration

- Quickstart Panel -> Open MCUXpresso Installer now prompts you to install the latest version in case your local Installer version is 1.0 or older. This aims to fix an Installer issue when updating to version 1.1.
- Quickstart Panel -> Open MCUXpresso Installer is now able to download and install on macOS and Linux.

### Open-CMSIS-Pack

- Fails to launch debug session on some single-core device targets.

### Zephyr

- Error thrown when you want to create another application type after creating a "Repository Application" using the same template example.

## Version 1.3 (2023.10)

### Project Management

- Added support for importing existing executables (.elf).
- Changed the 'build' icon action.

### Eclipse Project Converter

- Automatically handling MCUXpresso SDK linkage when no default SDK is available at conversion.

### Repository Integration

- Import repository now supports cloning from an HTTPS that requires authentication.

### Zephyr

- Copy the entire project folder when creating a workspace/freestanding application. This prevents build failure due to missing files located outside of the source directory.

### Open-CMSIS-Pack

- Update repository now lists all installed packs that have a newer version available online.
- Properly configure svd file in launch.json (for Peripheral View support).

### MCUXpresso SDK

- Extended display for targets not previously listed for GitHub SDK (FRDM-K64F, LPCXpresso55S36, etc.). In order to benefit on this update, a new clone of GitHub is required.

## Version 1.2 (2023.09)

### General

- Added "Application Code Hub" view, integrating [NXP Application Code Hub](https://mcuxpresso.nxp.com/appcodehub) with support for listing available repositories, filtering, documentation preview and cloning. A project import facility will be added in a future release.
- Local folder prompt selection now defaults to the HOME folder.

### Project Management

- Added "Settings" node in project view that lists all configuration files (.vscode directory content).

### Open-CMSIS-Pack

- Imported project now maintains the origin (ID and version) of the source pack.
- Imported repositories groups all the versions of the same packs under the same entry.
- Pack information can be now be updated via the Refresh button.

### Eclipse Project Converter

- Support importing projects with linked sources.

### Debugger

- Added support for Flash Programmer and multicore for PEmicro probes.
- Added debug option to use JTAG on J-Link probes (debug.segger.interface option in .vscode/mcuxpresso-tools.json).

## Version 1.1 (2023.08)

### General

- User can now directly download MCUXpresso Installer from the extension (in case is not already available).
- Paths specified in project settings (i.e. "toolchainPath" and "sdk.path" options from mcuxpresso-tools.json file) can now be defined using environment variables.

### Eclipse Project Converter

- Support for converting multiple MCUXpresso IDE projects at once.
- Static library projects are now supported by the converter.
- Corrected issues found when the imported project uses flags like `-imacros` or `-static`, or has optimization levels different from O0.
- Solved wrong linker settings handling in case of multiple libraries specified in the Eclipse project.
- Object files are now generated with the .o extension (instead .obj) to be consistent with the Eclipse project linker files.

### Open-CMSIS-Pack

- Import Example from Repository view filters out projects with no available csolution/cproject entries.
- Ability to detect and use already available CMSIS toolbox.
- Support for build configuration management.
- Project view now displays MCU information.
- Import example shows the board image available in the pack (similar with MCUXpresso SDK and Zephyr).

### Repository Integration

- Pre-populate Import Repository -> Local Archive with archive name.
- Import Project view is now refreshed when a new repository is imported while the window is open.
- Creation of git repository changed to optional for newly imported standalone MCUXpresso SDKs.
- Update Repository option in Imported Repository view extended to work for GitHub SDK and Zephyr.
- Fixed displaying progress bar status as complete before finishing the cloning process.
- When git is not installed, the Import Repository -> Revision field is no longer stuck.
- Fixed error thrown after trying to import an example from a new repository.

### Debugger

- Added "Terminate Debug" button option in Projects view for the projects currently being debugged.
- Added "Attach" entry to project context menu.
- Probes view shows projects currently being debugged by each probe.
- Moved probe specific debug options to mcuxpresso-tools.json configuration file.
- Added debug "speed" option for Segger debug probes.

## Version 1.0 (2023.07)

### General

- Added integration with standalone MCUXpresso Config Tools.
- Added Quick Key (Alt-X / ⌘-X) to return to MCUXpresso view.

### Project Management

- Support for importing pure CMake projects.
- Multicore and TrustZone linked projects are now supported by the Eclipse Project Converter.
- "Delete project from disk" deletes the build artifacts for Zephyr Repository projects.
- Rebuild and Clean operations are now invoked for linked projects (i.e. multicore, TrustZone).
- The Import Example from Repository is able to detect and clone source folders located outside example's main directory.
- The "Open in Terminal" command is now aware of Zephyr projects. A terminal session opened from Projects View will have its environment properly set up for interacting with a Zephyr application.
- Added Build and Clean operations for Open-CMSIS projects.

### Repository Integration

- Support for MCUXpresso SDK 2.14.x.
- Added "Refresh" toolbar button in the Imported Repositories view.

### Debugger

- The debugger now prompts when unsure of the target device after automatic detection. This supersedes manual editing of JSON files from previous versions.
- Debugging non-secure project is also flashing the secure image.
- Support debugging project even if there is no associated SDK.
- Ability to use an already started GDB server.
- LinkServer Flash Programmer now accepts binary files.
- In previous versions the debugger occasionally encountered issues starting a LinkServer debug session on macOS or Linux the second time. This has been corrected.
- Debugger now stops at the entry point specified in launch.json (default "main").

### Analysis Tools

- Image Info View now loads data for Open-CMSIS projects.
- Baremetal Heap and Stack facility now detects heap overflow.
- TrustZone projects are now supported by the Baremetal Heap and Stack facility.

## Version 0.9 (2023.06) Pre-release version

 - Initial public version.