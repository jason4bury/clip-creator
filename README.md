# Clip Creator

---

<p align="center">
  <img src="assets/clip-creator.png" alt="Clip Creator" width="300" height="300">
</p>

A modern PowerShell GUI for creating random MP4 clips from your movie collection using **FFmpeg**. Clip Creator creates one configurable random clip per movie and saves it as `theme.mp4` inside a movie-named output folder.

![Platform](https://img.shields.io/badge/platform-Windows-0078D4)
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-5391FE)
![Version](https://img.shields.io/badge/version-1.0.0-00BFFF)
![License](https://img.shields.io/badge/license-MIT-blue)

**Clip Creator** is a Windows PowerShell GUI for creating one random
video clip from each movie in a folder using FFmpeg.

Each generated clip is saved as an MP4 named `theme.mp4` inside its own
movie-named output folder.

## Features

-   Modern cinematic Windows GUI
-   Creates one random clip per movie
-   Default clip length of 10 seconds
-   Avoids the beginning and end of movies where possible
-   Exports clips as MP4
-   Creates a separate output folder for each movie
-   Saves each clip as `theme.mp4`
-   Supports subfolders
-   Supports common formats including MKV, MP4, AVI, MOV, M4V, WMV, MPG,
    MPEG, TS, M2TS and WebM
-   Shows processing progress, current movie, time left and clips
    created
-   Checks whether FFmpeg is available
-   Detects an existing `theme.mp4` and asks before overwriting it
-   Can open the output directory after processing
-   Stop/cancel processing button
-   Built-in About window

## Requirements

-   Windows 10 or Windows 11
-   PowerShell 5.1 or newer
-   FFmpeg and FFprobe available on the system

The easiest setup is to have `ffmpeg.exe` and `ffprobe.exe` available
through your Windows `PATH`.

## Running Clip Creator

1.  Download or clone this repository.
2.  Make sure FFmpeg is installed.
3.  Right-click `clip-creator.ps1` and run it with PowerShell, or open
    PowerShell in the project directory and run:

``` powershell
.\clip-creator.ps1
```

If Windows prevents local PowerShell scripts from running, review your
organisation's PowerShell execution policy before changing it.

## How to use

1.  Select your **Movies Folder**.
2.  Select the **Output Folder**.
3.  Choose the clip length and the amount of time to avoid at the
    start/end.
4.  Leave **Include subfolders** enabled if your movies are organised in
    folders.
5.  Click **Create Random Clips**.
6.  Clip Creator chooses a random position in each movie and creates one
    MP4 clip.
7.  When processing finishes, you can choose to open the output folder.

## Output structure

For movies such as:

``` text
Movies/
├── Alien.mkv
├── Blade Runner.mp4
└── The Thing.mkv
```

Clip Creator produces:

``` text
Random Clips/
├── Alien/
│   └── theme.mp4
├── Blade Runner/
│   └── theme.mp4
└── The Thing/
    └── theme.mp4
```

If `theme.mp4` already exists for a movie, Clip Creator asks whether you
want to overwrite it.

## Version

Current version: **1.0.0**

See [CHANGELOG.md](CHANGELOG.md) for release notes.

## Credits

Created by **Jason Rhodes**.

AI assistance: **ChatGPT by OpenAI**.

Video processing: **FFmpeg**.

## Links

-   Jason Rhodes: https://jason4bury.org
-   OpenAI: https://openai.com
-   FFmpeg: https://ffmpeg.org

## Licence

Copyright © Jason Rhodes. See [LICENSE](LICENSE) for the repository
licence.
