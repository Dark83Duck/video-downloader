# 🎬 Video Downloader (Multi-Agent Skill & Plugin)

[![Compatible with Antigravity](https://img.shields.io/badge/Antigravity-Compatible-4285F4)](https://github.com)
[![Compatible with Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-D97706)](https://github.com)
[![Compatible with OpenAI Codex](https://img.shields.io/badge/Codex-Compatible-10A37F)](https://github.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A multi-agent skill and plugin that allows AI coding assistants (**Antigravity / agy**, **Claude Code**, and **OpenAI Codex**) to download YouTube videos and extract audio tracks with full control over quality and formats.

---

## ✨ Features

- **Multi-Agent Compatibility**: Works seamlessly with **Antigravity (AGY)**, **Claude Code**, and **Codex**.
- **Quality Control**: Download at `best`, `1080p`, `720p`, `480p`, `360p`, or `worst`.
- **Format Options**: Output as `mp4` (default), `webm`, or `mkv`.
- **Audio Extraction**: Download high-quality audio directly as `mp3` with a single option (`-a`).
- **Self-Healing Dependencies**: Automatically detects and installs `yt-dlp` if missing.
- **Standalone CLI**: Can be executed directly from terminal without an agent.

---

## 📋 Prerequisites

1. **Python 3.8+**
2. **ffmpeg** (Recommended for audio extraction & stream merging):
   - **macOS**: `brew install ffmpeg`
   - **Ubuntu/Debian**: `sudo apt update && sudo apt install -y ffmpeg`
   - **Windows**: `winget install Gyan.FFmpeg`

---

## 🚀 Installation

### 1. Antigravity (agy)

**Global Installation (All projects):**
```bash
git clone https://github.com/Dark83Duck/video-downloder.git ~/.gemini/config/plugins/video-downloader
```

**Project-Specific Installation:**
```bash
mkdir -p .agents/plugins
git clone https://github.com/Dark83Duck/video-downloder.git .agents/plugins/video-downloader
```

---

### 2. Claude Code

**Global Installation:**
```bash
# Clone into Claude plugins directory:
git clone https://github.com/Dark83Duck/video-downloder.git ~/.claude/plugins/video-downloader

# Or link the skill directly:
ln -s "$(pwd)/video-downloader/skills/video-downloader" ~/.claude/skills/video-downloader
```

**Project-Specific Installation:**
```bash
mkdir -p .claude/skills
ln -s "$(pwd)/video-downloader/skills/video-downloader" .claude/skills/video-downloader
```

---

### 3. OpenAI Codex

**Global Installation:**
```bash
git clone https://github.com/Dark83Duck/video-downloder.git ~/.codex/skills/video-downloader
```

**Project-Specific Installation:**
Place in your repository's `.agents/skills/` or `skills/` directory.

---

## 🤖 Prompting Your AI Assistant

Once installed, you can simply ask your agent in plain language:

- *"Download this YouTube video in 1080p MP4: `https://www.youtube.com/watch?v=...`"*
- *"Extract the audio from this video as MP3 and save it to ./music: `https://www.youtube.com/watch?v=...`"*
- *"이 유튜브 영상 720p로 다운로드해서 downloads 폴더에 저장해줘: `https://www.youtube.com/watch?v=...`"*

---

## 💻 Standalone CLI Usage

You can also run the script directly from your terminal:

```bash
# Basic download (best quality MP4)
python3 skills/video-downloader/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID"

# 1080p MP4 saved to a custom folder
python3 skills/video-downloader/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID" -q 1080p -o ./downloads

# Extract audio only as MP3
python3 skills/video-downloader/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID" -a -o ./music

# 720p WebM
python3 skills/video-downloader/scripts/download_video.py "https://www.youtube.com/watch?v=VIDEO_ID" -q 720p -f webm
```

### CLI Arguments

| Option | Shorthand | Default | Description | Choices |
| :--- | :--- | :--- | :--- | :--- |
| `--quality` | `-q` | `best` | Video resolution | `best`, `1080p`, `720p`, `480p`, `360p`, `worst` |
| `--format` | `-f` | `mp4` | Container format | `mp4`, `webm`, `mkv` |
| `--audio-only`| `-a` | `false` | Extract MP3 audio | Flag (no value needed) |
| `--output` | `-o` | `.` | Target directory | Path string |

---

## 📂 Project Structure

```text
video-downloader/
├── README.md                          # Documentation & multi-agent guide
├── LICENSE                            # MIT License
├── .gitignore                         # Ignores temp, venv, and downloaded media
├── plugin.json                        # Root plugin manifest (Antigravity & agents)
├── gemini-extension.json              # Gemini CLI extension manifest
├── .claude-plugin/
│   └── plugin.json                    # Claude Code plugin manifest
├── .codex-plugin/
│   └── plugin.json                    # OpenAI Codex plugin manifest
└── skills/
    └── video-downloader/
        ├── SKILL.md                   # Skill instructions with frontmatter
        └── scripts/
            └── download_video.py      # Core download engine
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
