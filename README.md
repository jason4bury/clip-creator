# Clip Creator

<p align="center">
  <img src="assets/clip-creator.png" alt="Clip Creator logo" width="300" height="300">
</p>

A small PowerShell + Windows Forms front end for
[FFmpeg](https://ffmpeg.org/) that creates one random MP4 clip from each
movie in a folder. Each movie gets its own output folder, with the
generated clip saved as `theme.mp4`.

![Platform](https://img.shields.io/badge/platform-Windows-blue)
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-5391FE)
![Version](https://img.shields.io/badge/version-1.5.0-00BFFF)
![License](https://img.shields.io/badge/license-MIT-blue)

## What's New in v1.5.0

- **Cleaner output structure** — generated clips are now stored directly in the source movie folder structure as `backdrops\theme.mp4`, without creating an unnecessary extra folder based on the video filename.
- **Partial HTML conversion log** — if processing is stopped, Clip Creator creates a graphical HTML report containing everything processed up to the point of cancellation.
- **Partial output access** — after cancellation, Clip Creator can open the output folder containing clips that were successfully created before processing stopped.
- **Separate cancellation prompts** — users can choose whether to view the partial HTML conversion log and whether to open the partial output folder.
- **Cancellation summary** — the partial report clearly identifies that processing was stopped and shows how many clips were created before cancellation.
- **Version update** — Clip Creator is now **1.5.0**.

## Features

- **Partial HTML conversion log** — creates a colour-coded report when a run is stopped early.
- **Partial output access** — optionally opens clips created before cancellation.
- **Cleaner backdrops structure** — outputs directly to `Movie Folder\backdrops\theme.mp4`.

- **Stop remaining creations** — cancel the rest of a run directly from the existing-clip overwrite prompt.

- **Network-aware folder browsing** — browse mapped network drives and Windows network locations.
- **UNC share support** — use NAS paths such as `\\Synology\Movies`.

-   **One random clip per movie** --- chooses a random point in each
    movie and creates one clip.
-   **MP4 output** --- clips are exported as `theme.mp4`.
-   **Per-movie folders** --- each movie gets its own named output
    folder.
-   **Configurable clip length** --- 10 seconds by default.
-   **Avoid start/end** --- avoids the opening and closing portion of a
    movie where possible.
-   **Existing clip protection** --- asks whether to overwrite an
    existing `theme.mp4`.
-   **Subfolder support** --- optionally scans movie folders
    recursively.
-   **Multiple video formats** --- supports MKV, MP4, AVI, MOV, M4V,
    WMV, MPG, MPEG, TS, M2TS and WebM.
-   **Improved progress display** --- shows percentage complete, current
    movie, time left and clips created.
-   **Stop processing** --- processing can be cancelled from the GUI.
-   **FFmpeg check** --- verifies that FFmpeg is available.
-   **Open Output Folder** --- opens the destination directly from the
    application.
-   **Completion prompt** --- asks whether to open the output directory
    when processing finishes.
-   **Modern cinematic interface** --- includes visual pressed-state
    feedback on the main buttons.
-   **About window** --- displays the application version and project
    credits.
-   **EXE-friendly DPI handling** --- improves layout consistency when
    the script is compiled with PS2EXE.

## Requirements

-   Windows 10 or Windows 11
-   PowerShell 5.1 or newer
-   [FFmpeg](https://ffmpeg.org/) and `ffprobe` installed and available
    through the Windows `PATH`

Check FFmpeg from PowerShell with:

``` powershell
ffmpeg -version
ffprobe -version
```

Clip Creator also includes a **Check FFmpeg** button.

## Output Folder Structure

Clip Creator preserves the directory structure below the selected Movies Folder. It no longer creates an additional folder based on the video filename.

For example, this source:

```text
V:\Movies\Mad Max (1979)\Mad Max.mkv
```

produces:

```text
D:\Random Clips\Mad Max (1979)\backdrops\theme.mp4
```

If processing is stopped early, clips that were already completed remain in the output folder.

## Network and NAS Storage

Clip Creator supports movie libraries stored on network storage such as a Synology NAS.

The **Movies Folder** and **Output Folder** Browse buttons use the Windows Shell folder picker, making mapped network drives and Windows network locations available alongside local folders.

You can use either a mapped drive:

```text
V:\Movies
```

or a UNC network path:

```text
\\Synology\Movies
```

Clip Creator preserves the directory structure beneath the selected Movies Folder when creating the output structure.

If a mapped drive is visible in File Explorer but not in Clip Creator, make sure Clip Creator is running under the same Windows user/security context that created the drive mapping. Clip Creator does not normally need to be run as Administrator.

## Usage

Run the PowerShell version with:

``` powershell
.\clip-creator.ps1
```

If script execution is blocked for the current session:

``` powershell
powershell -ExecutionPolicy Bypass -File .\clip-creator.ps1
```

Then:

1.  Select the **Movies Folder**.
2.  Select the **Output Folder**.
3.  Set **Clip Length** and **Avoid Start/End**.
4.  Choose whether to **Include subfolders**.
5.  Click **Create Random Clips**.
6.  Follow the progress display while the movies are processed.
7.  When complete, choose whether to open the output folder.

## Output

Clip Creator preserves the folder structure **below the selected Movies Folder**.

For example, if the selected Movies Folder is `V:\Documentary` and contains:

```text
V:\Documentary
└── Doctor Who Am I (2022)
    └── Doctor Who Am I.mkv
```

with the output folder set to `D:\Random Clips`, Clip Creator creates:

```text
D:\Random Clips
└── Doctor Who Am I (2022)
    └── Doctor Who Am I
        └── backdrops
            └── theme.mp4
```

The source drive letter and selected root folder are not copied into the output. Only directories beneath the selected Movies Folder are recreated.

If `backdrops\theme.mp4` already exists, Clip Creator asks whether it should be overwritten.

## Creating the EXE

Clip Creator can be packaged with the PowerShell `ps2exe` module:

``` powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
Install-Module -Name ps2exe -Scope CurrentUser -Force
Import-Module ps2exe

Invoke-ps2exe -inputFile .\clip-creator.ps1 -outputFile ".\Clip Creator v1.5.0.exe" `
    -STA -noConsole `
    -iconFile .\clip-creator.ico `
    -title "Clip Creator" `
    -version "1.5.0" `
    -product "Clip Creator" `
    -company "Jason Rhodes" `
    -copyright "Copyright © 2026 Jason Rhodes"
```

The recommended executable filename is:

``` text
Clip Creator v1.5.0.exe
```

## Processing Report

After a completed run, Clip Creator writes a timestamped HTML report into the selected output folder, for example:

```text
Clip-Creator-Log-20260928-095800.html
```

The self-contained web page includes summary cards for **Successful**, **Warnings**, **Errors** and **Skipped**, plus a detailed table showing each movie, its output path and any FFmpeg diagnostic messages.

Clip Creator asks whether you want to view the report immediately after processing. Errors are highlighted in red and warnings in yellow.

## Compiled EXE Notes

Clip Creator v1.5.0 includes a compatibility fix specifically for the PS2EXE-compiled application. FFmpeg and FFprobe are launched using .NET process handling rather than PowerShell stream redirection. This prevents the repeated `Path` error dialogs seen in v1.3.0 while retaining captured FFmpeg diagnostics for the HTML report.

## Troubleshooting

**The compiled EXE layout looks different from the PowerShell version**

The current script includes explicit DPI-awareness handling and disables
Windows Forms automatic scaling to help the compiled PS2EXE interface
retain the intended layout. Rebuild the EXE from the latest
`clip-creator.ps1`.

**FFmpeg is not detected**

Make sure `ffmpeg.exe` and `ffprobe.exe` are installed and available
through the Windows `PATH`. Open a new PowerShell window and run
`ffmpeg -version` and `ffprobe -version`.

**PowerShell says script execution is disabled**

Run the script with a process-only execution-policy bypass as shown in
the Usage section. On managed computers, follow your organisation's
policies.

**A clip already exists**

Choose **Yes** to replace the existing `theme.mp4`, or **No** to keep it
and continue to the next movie.

**The time-left estimate changes**

This is expected. The estimate is based on processing completed so far
and can change as more movies finish.

## How it works

Clip Creator scans the selected folder for supported video files. It
uses `ffprobe` to determine each movie's duration, selects a random
position while respecting the configured start/end avoidance period, and
uses FFmpeg to create the MP4 clip.

The GUI tracks the current movie, completion percentage, estimated time
left and number of clips created. Output is organised automatically into
one folder per movie.

## Version

Current release: **1.5.0**

See [CHANGELOG.md](CHANGELOG.md) for release notes.

## Credits

Created by [Jason Rhodes](https://jason4bury.org/).

AI assistance: [ChatGPT by OpenAI](https://openai.com/).

Video processing: [FFmpeg](https://ffmpeg.org/).

## License

Clip Creator is released under the **MIT License**. See
[LICENSE](LICENSE).
