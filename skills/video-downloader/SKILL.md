---
name: youtube-downloader
description: Download YouTube videos with customizable quality and format options. Use this skill when the user asks to download, save, or grab YouTube videos. Supports various quality settings (best, 1080p, 720p, 480p, 360p), multiple formats (mp4, webm, mkv), and audio-only downloads as MP3.
---

# YouTube Video Downloader

Download YouTube videos with full control over quality and format settings.
Compatible with Antigravity (agy), Claude Code, OpenAI Codex, and standalone CLI environments.

## Execution

Execute the helper script located in the `scripts/` directory relative to this skill:

```bash
python3 <path-to-skill>/scripts/download_video.py "<YOUTUBE_URL>" [options]
```

When invoked from within the skill's root repository:

```bash
python3 skills/video-downloader/scripts/download_video.py "<YOUTUBE_URL>" [options]
```

## Options

### Quality Settings (`-q`, `--quality`)
Specifies the desired video resolution:
- `best` (default): Highest resolution available
- `1080p`: Full HD (1920x1080)
- `720p`: HD (1280x720)
- `480p`: Standard definition
- `360p`: Lower resolution (faster download, smaller size)
- `worst`: Lowest available video quality

### Format Options (`-f`, `--format`)
Specifies the container/output format (applies to video downloads):
- `mp4` (default): Most compatible across all devices and platforms
- `webm`: Modern open web format
- `mkv`: Matroska container

### Audio Only (`-a`, `--audio-only`)
Extracts and converts only the audio track into high-quality MP3 (320kbps/VBR 0):
```bash
python3 <path-to-skill>/scripts/download_video.py "<YOUTUBE_URL>" -a
```

### Output Directory (`-o`, `--output`)
Specifies the directory where the downloaded file should be saved (defaults to current working directory `.`):
```bash
python3 <path-to-skill>/scripts/download_video.py "<YOUTUBE_URL>" -o "./downloads"
```

## Common Workflows & Examples

1. **Best Quality MP4 (Default)**:
   ```bash
   python3 <path-to-skill>/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID"
   ```

2. **1080p Video to Specific Folder**:
   ```bash
   python3 <path-to-skill>/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID" -q 1080p -o ./downloads
   ```

3. **Audio-Only MP3 Extraction**:
   ```bash
   python3 <path-to-skill>/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID" -a -o ./music
   ```

## Requirements & Fallbacks

- **Python 3.8+**
- **yt-dlp**: Automatically installed via pip if not detected.
- **ffmpeg**: Recommended for audio extraction (`-a`) and merging high-res video/audio streams.
  - macOS: `brew install ffmpeg`
  - Ubuntu/Debian: `sudo apt install ffmpeg`
