# YouTube Downloader

Download single videos or entire playlists to Google Drive.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/WhoisMonesh/Colab-Youtube-Downloader/blob/main/Colab-Youtube-Downloader.ipynb)

---

## Quick Start

1. **Open in Colab** (click badge above)
2. **Mount Drive** when prompted
3. **Paste your URL** in the `URL` field in section 3
4. **Run all cells**

Your files will appear in your Google Drive under `YouTubeDownloader/`.

---

## Features

| Feature | Description |
|---|---|
| **Single & Playlist** | Paste any YouTube URL — single video or playlist, auto-detected |
| **Playlist Progress** | Shows per-video index (3/15), download speed, and percentage |
| **Limit Videos** | `MAX_VIDEOS` caps how many videos to grab from a playlist |
| **Audio Only** | Toggle `AUDIO_ONLY = True` to download as MP3 |
| **Sync-safe** | Downloads locally first, then moves to Drive (avoids FUSE errors) |
| **Keep-Alive** | JavaScript prevents Colab timeout during long downloads |
| **Auto-Zip** | If multiple files are downloaded, they are zipped automatically |

---

## Where to Put the URL

In section **3. Configuration**, find this line and paste your URL:

```python
URL = ''  # <-- paste your YouTube link between the quotes
```

### Examples

| What to download | What to paste |
|---|---|
| Single video | `URL = 'https://youtube.com/watch?v=dQw4w9WgXcQ'` |
| Short link | `URL = 'https://youtu.be/dQw4w9WgXcQ'` |
| Playlist | `URL = 'https://youtube.com/playlist?list=PL...'` |
| Video in playlist | `URL = 'https://youtube.com/watch?v=...&list=PL...'` |

The notebook automatically detects whether the URL points to a single video or a playlist.

### Playlist Limit

To download only the first N videos from a playlist:

```python
MAX_VIDEOS = 5  # downloads first 5 videos only (0 = all)
```

---

## All Configuration Options

| Variable | Default | Description |
|---|---|---|
| `SAVE_PATH` | `/content/downloads/YouTubeDownloader/` | Local temp directory |
| `DRIVE_PATH` | `/content/drive/My Drive/YouTubeDownloader/` | Final Drive destination |
| `URL` | `''` | YouTube video or playlist URL |
| `FORMAT` | `'bestvideo+bestaudio/best'` | Quality / format selection |
| `AUDIO_ONLY` | `False` | Set `True` to extract audio as MP3 |
| `MAX_VIDEOS` | `0` | Max videos for playlists (`0` = all) |
| `KEEP_ALIVE` | `True` | Prevent Colab timeout |

### Format Examples

| FORMAT | Result |
|---|---|
| `bestvideo+bestaudio/best` | Best available quality |
| `bestvideo[height<=1080]+bestaudio/best[height<=1080]` | Max 1080p |
| `bestvideo[height<=720]+bestaudio/best[height<=720]` | Max 720p |
| `bestaudio/best` | Audio only |

---

## Technical Details

- Uses [yt-dlp](https://github.com/yt-dlp/yt-dlp) with [ffmpeg](https://ffmpeg.org/) for merging
- Downloads to `/content/downloads/` first, then `shutil.move` to Drive (avoids FUSE sync conflicts)
- Playlist detection via `extract_flat` (fast, no download)
- Live progress via `IPython.display` HTML with `display_id`
- JavaScript keep-alive prevents Colab session timeout
- Automatic ZIP when multiple files are downloaded

---

## Fair Use & Legal Notice

This tool downloads publicly available YouTube videos for **personal, non-commercial use only**.

**You agree to:**
- Only download content you have the legal right to access
- Respect YouTube's Terms of Service
- Not redistribute, re-upload, or monetize downloaded content
- Use downloaded content for personal offline access, education, or fair-use purposes

**You may NOT use this tool to:**
- Download videos protected by paywalls or DRM
- Mass-download content for commercial purposes
- Circumvent regional restrictions (geo-blocking)
- Violate any applicable copyright laws

**Disclaimer:** The authors are not responsible for how you use this software. You assume all legal responsibility for the content you download. This tool is provided for educational purposes only.

---

## License

MIT
