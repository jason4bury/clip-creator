# Changelog

All notable changes to Clip Creator are documented in this file.

## 1.3.0

### Added

- Network-aware Windows Shell folder picker for the Movies Folder.
- Network-aware Windows Shell folder picker for the Output Folder.
- Improved support for mapped network drives used by NAS movie libraries.
- Support for selecting UNC network shares such as `\\Synology\Movies`.
- Fallback to the standard Windows Forms folder picker if Windows Shell browsing is unavailable.

### Changed

- Folder browsing now exposes local folders, This PC, mapped network drives and Windows network locations more reliably.
- Improved usability for movie collections stored on Synology and other NAS devices.
- Application version updated from **1.2.0** to **1.3.0**.
- About window now displays **Version 1.3.0**.
- Recommended executable filename is now `Clip Creator v1.3.0.exe`.


## 1.2.0

### Added

- Self-contained HTML processing report generated after completed runs.
- Colour-coded summary for successful clips, warnings, errors and skipped movies.
- Detailed per-movie report containing output paths and FFmpeg diagnostics.
- Capture of FFmpeg diagnostic output for inclusion in the report.
- Prompt to view the HTML log in the default web browser.
- Timestamped report filenames so separate run reports are retained.

### Changed

- Successfully created clips that also produce FFmpeg diagnostic messages can be identified as warnings.
- Processing diagnostics are retained in a readable web report.
- Application version updated from **1.1.0** to **1.2.0**.
- About window now displays **Version 1.2.0**.
- Recommended executable filename is now `Clip Creator v1.2.0.exe`.


## 1.1.0

### Added

- Preserves the source directory structure beneath the selected Movies Folder.
- Creates a `backdrops` directory inside each generated movie folder.
- Stores generated clips as `backdrops\theme.mp4`.
- Adds path-safety checks so rooted or drive-qualified source paths cannot accidentally be appended to the output folder.

### Fixed

- Fixed invalid output paths that could include a source drive letter such as `V:\` beneath the destination folder.
- Fixed the `GetFullPath()` empty-path error caused by the incorrect `$moviesFolder` variable reference; folder handling now correctly uses `$movieFolder`.

### Changed

- Application version updated from **1.0.0** to **1.1.0**.
- About window now displays **Version 1.1.0**.
- Recommended executable filename is now `Clip Creator v1.1.0.exe`.
- README updated for the new folder and `backdrops` output structure.


## 1.0.0

### Added

-   Modern cinematic Windows Forms interface.
-   One random clip from each movie.
-   MP4 output saved as `theme.mp4`.
-   Separate output folder for each movie.
-   Configurable clip length and start/end avoidance period.
-   Optional recursive subfolder searching.
-   Support for common movie formats.
-   Progress percentage, current movie, time-left estimate and
    clips-created counter.
-   FFmpeg installation check.
-   Existing clip detection with overwrite confirmation.
-   Stop/cancel processing.
-   Open Output Folder control.
-   Completion prompt offering to open the output directory.
-   About dialog with creator, AI-assistance and FFmpeg credits.
-   Application version displayed in the About window.
-   Visual pressed-state feedback on the main GUI buttons.
-   MIT License and GitHub documentation.

### Changed

-   Recommended compiled executable filename is now
    `Clip Creator v1.0.0.exe`.
-   About header now displays
    `Version 1.0.0 • FFmpeg Movie Clip Utility`.
-   About description area was widened so the full description is
    visible.
-   README now includes PS2EXE build instructions and the versioned EXE
    naming convention.

### Fixed

-   Added explicit DPI-awareness handling for the compiled PS2EXE
    version.
-   Disabled Windows Forms automatic scaling to improve consistency
    between the `.ps1` and compiled `.exe`.
-   Improved alignment of the Movies Folder and Output Folder controls.
-   Improved progress percentage positioning and sizing.
-   Improved Current Movie, Time Left and Clips Created layout.
-   Corrected several About-window text and alignment issues.

### Packaging

-   Product: `Clip Creator`
-   Version: `1.0.0`
-   Recommended executable: `Clip Creator v1.0.0.exe`
-   PowerShell source: `clip-creator.ps1`
