# Clip Creator v1.5.0

Clip Creator v1.5.0 improves the generated folder structure and adds better handling for partially completed processing runs.

## What's New

### Cleaner Output Structure

Generated clips are now stored directly inside the movie folder's `backdrops` directory.

Previous structure:

```text
Mad Max (1979)
└── Mad Max
    └── backdrops
        └── theme.mp4
```

New structure:

```text
Mad Max (1979)
└── backdrops
    └── theme.mp4
```

### Partial Processing Reports

If processing is stopped before completion, Clip Creator now creates a partial graphical HTML conversion log containing everything processed up to that point.

The user is then given separate options to:

- View the partial HTML conversion log.
- Open the partial output folder containing clips already created.

The partial report clearly identifies that the run was stopped by the user and retains the colour-coded success, warning, error and skipped information.

## Existing Features

- Random FFmpeg movie clip creation.
- Preserved source directory structure.
- `backdrops\theme.mp4` output.
- Existing clip detection with overwrite, continue or stop options.
- Network-aware folder browsing.
- Mapped network drive and Synology/NAS support.
- UNC path support.
- Graphical HTML processing reports.
- FFmpeg diagnostic capture.

## Version

**Clip Creator v1.5.0**

Created by **Jason Rhodes**  
AI assistance: **ChatGPT by OpenAI**  
Video processing: **FFmpeg**
