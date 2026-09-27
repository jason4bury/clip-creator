# Changelog

All notable changes to Clip Creator are documented in this file.

## 1.0.0

### Latest changes

- Added preservation of the source directory structure beneath the selected Movies Folder.
- Added a `backdrops` directory inside each generated movie folder.
- Moved generated clips to `backdrops\theme.mp4`.
- Fixed invalid output paths that could incorrectly include a source drive letter such as `V:\` beneath the destination folder.
- Fixed the `GetFullPath()` empty-path error caused by an incorrect `$moviesFolder` variable reference; folder handling now correctly uses `$movieFolder`.
- Added path-safety checks so rooted or drive-qualified source paths cannot accidentally be appended to the output folder.

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
