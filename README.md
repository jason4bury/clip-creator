# Clip Creator

<p align="center">
  <img src="assets/clip-creator.png" alt="Clip Creator logo" width="300">
</p>

A small PowerShell + Windows Forms front end for
[FFmpeg](https://ffmpeg.org/) that creates one random MP4 clip from each
movie in a folder. Each movie gets its own output folder, with the
generated clip saved as `theme.mp4`.

![Windows](https://img.shields.io/badge/platform-Windows-blue)
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B-5391FE)
![Version](https://img.shields.io/badge/version-1.0.0-00BFFF)
![License](https://img.shields.io/badge/license-MIT-blue)

## Features

-   **One random clip per movie** --- scans the selected movie folder
    and creates a single clip from a random point in each video.
-   **MP4 output** --- every generated clip is saved as `theme.mp4`.
-   **Per-movie folders** --- automatically creates a separate output
    folder named after each movie.
-   **Configurable clip length** --- defaults to 10 seconds but can be
    changed in the GUI.
-   **Avoid start/end** --- can avoid the opening and closing portion of
    each movie when choosing the random clip position.
-   **Existing clip protection** --- if `theme.mp4` already exists, Clip
    Creator asks whether you want to overwrite it or skip that movie.
-   **Subfolder support** --- optionally searches for movies inside
    subfolders.
-   **Multiple video formats** --- supports MKV, MP4, AVI, MOV, M4V,
    WMV, MPG, MPEG, TS, M2TS and WebM.
-   **Live progress** --- shows percentage complete, current movie,
    estimated time left and the number of clips created.
-   **Stop button** --- processing can be cancelled from the GUI.
-   **FFmpeg check** --- verifies that FFmpeg is available before you
    start.
-   **Open Output Folder** --- opens the selected destination directly
    from the GUI.
-   **Completion prompt** --- when processing finishes, asks whether you
    want to open the output folder.
-   **Cinematic interface** --- custom Windows GUI with visual
    button-press feedback and an About dialog.

## Requirements

-   Windows 10 or Windows 11.
-   PowerShell 5.1 or newer.
-   [FFmpeg](https://ffmpeg.org/) and `ffprobe` installed and available
    through your Windows `PATH`.

You can check whether FFmpeg is available from a terminal with:

``` powershell
ffmpeg -version
ffprobe -version
```

Clip Creator also includes a **Check FFmpeg** button in the GUI.

## Usage

Download `clip-creator.ps1` and run it either by right-clicking it and
choosing PowerShell, or from a PowerShell terminal:

``` powershell
.\clip-creator.ps1
```

If your PowerShell execution policy prevents the script from running,
you can launch it for that session with:

``` powershell
powershell -ExecutionPolicy Bypass -File .\clip-creator.ps1
```

Then:

1.  Select your **Movies Folder**.
2.  Select your **Output Folder**.
3.  Set the **Clip Length** and **Avoid Start/End** values.
4.  Choose whether to **Include subfolders**.
5.  Click **Create Random Clips**.
6.  Clip Creator processes each movie and updates the progress display.
7.  When complete, choose whether to open the output folder.

## Output

Given a movie folder such as:

``` text
Movies/
├── Alien.mkv
├── Blade Runner.mp4
└── The Thing.mkv
```

Clip Creator creates:

``` text
Random Clips/
├── Alien/
│   └── theme.mp4
├── Blade Runner/
│   └── theme.mp4
└── The Thing/
    └── theme.mp4
```

If a movie already has a `theme.mp4` in its output folder, you will be
asked whether to overwrite the existing clip.

## Troubleshooting

**The GUI opens but FFmpeg is not detected**

Make sure both `ffmpeg.exe` and `ffprobe.exe` are installed and
available through the Windows `PATH`. Open a new terminal and run
`ffmpeg -version` and `ffprobe -version` to confirm Windows can find
them.

**PowerShell says script execution is disabled**

Your PowerShell execution policy is preventing `.ps1` files from
running. You can run Clip Creator for that session with:

``` powershell
powershell -ExecutionPolicy Bypass -File .\clip-creator.ps1
```

On managed work or college computers, follow your organisation's policy
rather than changing machine-wide execution settings.

**A clip already exists**

Clip Creator checks for an existing `theme.mp4` before processing each
movie. Choose **Yes** to replace it with a new random clip or **No** to
keep the existing file and continue to the next movie.

**The time-left estimate changes while processing**

This is expected. The estimate is calculated from the movies processed
so far, so it becomes more representative as additional movies finish.

## How it works

Clip Creator is a PowerShell Windows Forms application. It scans the
selected folder for supported video files, uses `ffprobe` to determine
each movie's duration, chooses a random position while respecting the
configured start/end avoidance period, and calls FFmpeg to create the
MP4 clip.

The GUI keeps track of the current movie, completion percentage,
estimated time remaining and successfully created clips. Output is
organised automatically into one folder per movie.

## Version

Current release: **1.0.0**

See [CHANGELOG.md](CHANGELOG.md) for release notes.

## Credits

Created by [Jason Rhodes](https://jason4bury.org/).

AI assistance: [ChatGPT by OpenAI](https://openai.com/).

Video processing: [FFmpeg](https://ffmpeg.org/).

## License

MIT --- see [LICENSE](LICENSE).
