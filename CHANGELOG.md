# MCUXpresso for VS Code Changelog

## Version 1.0 (2023.07)

<h3>General</h3>

- Added integration with standalone MCUXpresso Config Tools.
- Added Quick Key (Alt-X / ⌘-X) to return to MCUXpresso view.

<h3>Project Management</h3>

- Support for importing pure CMake projects.
- Multicore and TrustZone linked projects are now supported by the Eclipse Project Converter.
- "Delete project from disk" deletes the build artifacts for Zephyr Repository projects.
- Rebuild and Clean operations are now invoked for linked projects (i.e. multicore, TrustZone).
- The Import Example from Repository is able to detect and clone source folders located outside example's main directory.
- The "Open in Terminal" command is now aware of Zephyr projects. A terminal session opened from Projects View will have its environment properly set up for interacting with a Zephyr application.
- Added Build and Clean operations for Open-CMSIS projects.

<h3>Repository Integration</h3>

- Support for MCUXpresso SDK 2.14.x.
- Added "Refresh" toolbar button in the Installed Repositories view.

<h3>Debugger</h3>

- The debugger now prompts when unsure of the target device after automatic detection. This supersedes manual editing of JSON files from previous versions.
- Debugging non-secure project is also flashing the secure image.
- Support debugging project even if there is no associated SDK.
- Ability to use an already started GDB server.
- LinkServer Flash Programmer now accepts binary files.
- In previous versions the debugger occasionally encountered issues starting a LinkServer debug session on macOS or Linux the second time. This has been corrected.
- Debugger now stops at the entry point specified in launch.json (default "main").

<h3>Analysis Tools</h3>

- Image Info View now loads data for Open-CMSIS projects.
- Baremetal Heap and Stack facility now detects heap overflow.
- TrustZone projects are now supported by the Baremetal Heap and Stack facility.

## Version 0.9 (2023.06) Pre-release version

 - Initial public version.