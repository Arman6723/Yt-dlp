# `yt-dlp` Complete Setup & Usage Guide

## Step 1: Install Required Components via `winget`

Open **Command Prompt (`cmd`)** or **PowerShell** and run:

```cmd
winget install yt-dlp.yt-dlp DirectX.FFmpeg DenoLand.Deno

```

> **Note:** If `winget` asks to accept source agreements, type `Y` and press **Enter**.

---

## Step 2: Create & Navigate to Your Music Folder

Run these commands in `cmd` to set up your directory:

```cmd
mkdir "%USERPROFILE%\Desktop\music transfer\music"
cd /d "%USERPROFILE%\Desktop\music transfer\music"

```

---

## Step 3: Run Download Commands

### Full Playlist Download

```cmd
yt-dlp -f 140 -x --audio-format m4a --download-archive downloaded.txt --sleep-requests 5 --sleep-interval 5 -o "%(autonumber)04d - %(title)s.%(ext)s" "PLAYLIST_URL"

```

### Resume / Range Download (e.g., Tracks 425–999 & 1001–1191)

```cmd
yt-dlp -f 140 -x --audio-format m4a --download-archive downloaded.txt --sleep-requests 5 --sleep-interval 5 -o "%(autonumber)04d - %(title)s.%(ext)s" --playlist-items 425-999,1001-1191 "PLAYLIST_URL"

```

---

## Step 4: Installation Alternatives (Direct Links)

If you prefer downloading `.exe` files manually into your music folder instead of using `winget`:

* **`yt-dlp.exe`**: [Direct Download](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe)
* **`ffmpeg.exe`**: [FFmpeg Releases](https://github.com/BtbN/FFmpeg-Builds/releases) (Extract `ffmpeg.exe` from `bin/`)
* **`deno.exe`**: [Deno Releases](https://github.com/denoland/deno/releases/latest) (Extract `deno.exe` from `.zip`)

---

## Quick Reference

| Flag | Function |
| --- | --- |
| `-f 140 -x --audio-format m4a` | Downloads original M4A audio. |
| `--download-archive downloaded.txt` | Saves log to prevent duplicate downloads. |
| `--sleep-requests 5 --sleep-interval 5` | Prevents YouTube IP blocks/403 errors. |
| `--playlist-items X-Y` | Downloads specific track ranges only. |
