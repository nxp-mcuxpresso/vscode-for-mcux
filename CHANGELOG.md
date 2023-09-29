# MCUXpresso for VS Code Changelog

## Version 1.2 (2023.09)

<h3>General</h3>

- Added "Application Code Hub" view, integrating [NXP Application Code Hub](https://mcuxpresso.nxp.com/appcodehub) with support for listing available repositories, filtering, documentation preview and cloning. A project import facility will be added in a future release.
- Local folder prompt selection now defaults to the HOME folder.

<h3>Project Management</h3>

- Added "Settings" node in project view that lists all configuration files (.vscode directory content).

<h3>Open-CMSIS-Pack</h3>

- Imported project now maintains the origin (ID and version) of the source pack.
- Installed repositories groups all the versions of the same packs under the same entry.
- Pack information can be now be updated via the Refresh button.

<h3>Eclipse Project Converter</h3>

- Support importing projects with linked sources.

<h3>Debugger</h3>

- Added support for Flash Programmer and multicore for PEmicro probes.
- Added debug option to use JTAG on J-Link probes (debug.segger.interface option in .vscode/mcuxpresso-tools.json).

## Version 1.1 (2023.08)

<h3>General</h3>

- User can now directly download MCUXpresso Installer from the extension (in case is not already available).
- Paths specified in project settings (i.e. "toolchainPath" and "sdk.path" options from mcuxpresso-tools.json file) can now be defined using environment variables.

<h3>Eclipse Project Converter</h3>

- Support for converting multiple MCUXpresso IDE projects at once.
- Static library projects are now supported by the converter.
- Corrected issues found when the imported project uses flags like “-imacros” or “-static”, or has optimization levels different from O0.
- Solved wrong linker settings handling in case of multiple libraries specified in the Eclipse project.
- Object files are now generated with the .o extension (instead .obj) to be consistent with the Eclipse project linker files.

<h3>Open-CMSIS-Pack</h3>

- Import Example from Repository view filters out projects with no available csolution/cproject entries.
- Ability to detect and use already available CMSIS toolbox.
- Support for build configuration management.
- Project view now displays MCU information.
- Import example shows the board image available in the pack (similar with MCUXpresso SDK and Zephyr).

<h3>Repository Integration</h3>

- Pre-populate Import Repository -> Local Archive with archive name.
- Import Project view is now refreshed when a new repository is imported while the window is open.
- Creation of git repository changed to optional for newly imported standalone MCUXpresso SDKs.
- Update Repository option in Installed Repository view extended to work for GitHub SDK and Zephyr.
- Fixed displaying progress bar status as complete before finishing the cloning process.
- When git is not installed, the Import Repository -> Revision field is no longer stuck.
- Fixed error thrown after trying to import an example from a new repository.

<h3>Debugger</h3>

- Added "Terminate Debug" button option in Projects view for the projects currently being debugged.
- Added "Attach" entry to project context menu.
- Probes view shows projects currently being debugged by each probe.
- Moved probe specific debug options to mcuxpresso-tools.json configuration file.
- Added debug "speed" option for Segger debug probes.

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