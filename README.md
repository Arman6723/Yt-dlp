# Yt-dlp
YouTube Downloader using Terminal/Shell

Here is a clear, step-by-step guide you can save as a `.txt` file or keep in your notes whenever you need to download or fix a massive YouTube playlist with `yt-dlp`.

---

# Complete `yt-dlp` Playlist Download Guide

This guide covers how to set up a clean, rate-limit-proof playlist download and how to recover missing/skipped songs if YouTube throttles your IP address.

---

## 1. Standard Best-Practice Playlist Command

Use this command to download a full playlist as **`.m4a` audio files**, formatted with clean track numbering, while preventing YouTube rate-limit blocks.

```cmd
yt-dlp -f 140 -x --audio-format m4a --download-archive downloaded.txt --sleep-requests 5 --sleep-interval 5 -o "%(autonumber)04d - %(title)s.%(ext)s" "PLAYLIST_URL"

```

### What Each Flag Does:

* `-f 140 -x --audio-format m4a`: Grabs original M4A audio directly (highest quality without unnecessary re-encoding).
* `--download-archive downloaded.txt`: Creates a local text log of downloaded video IDs so `yt-dlp` never double-downloads a file.
* `--sleep-requests 5 --sleep-interval 5`: Adds a 5-second delay between requests to keep YouTube from flagging your IP as a bot.
* `-o "%(autonumber)04d - %(title)s.%(ext)s"`: Formats file names cleanly as `0001 - Song Title.m4a`, `0002 - Song Title.m4a`, etc.

---

## 2. Fixing Missing / Skipped Tracks

If YouTube rate-limits your IP or hits a network hiccup, `yt-dlp` may skip large chunks of videos (e.g., songs 425 to 999).

### Step-by-Step Recovery Procedure:

1. **Stop the process:** Press `Ctrl + C` in Command Prompt to kill the current run.
2. **Clear the Rate Limit:** Change your network connection (turn on a VPN or connect to a mobile hotspot) to get a fresh IP address.
3. **Run a Targeted Range Command:** Use `--playlist-items` to force `yt-dlp` to hit only the missing range(s). You do **not** need to edit or delete `downloaded.txt`—`yt-dlp` will automatically check your archive and skip anything already saved.

### Single Range Recovery Example:

```cmd
yt-dlp -f 140 -x --audio-format m4a --download-archive downloaded.txt --sleep-requests 5 --sleep-interval 5 -o "%(autonumber)04d - %(title)s.%(ext)s" --playlist-items 425-999 "PLAYLIST_URL"

```

### Multiple Range Recovery Example (Comma-Separated):

```cmd
yt-dlp -f 140 -x --audio-format m4a --download-archive downloaded.txt --sleep-requests 5 --sleep-interval 5 -o "%(autonumber)04d - %(title)s.%(ext)s" --playlist-items 425-999,1001-1191 "PLAYLIST_URL"

```

---

## 3. Quick Reference Troubleshooting Rules

* **Error: `This content isn't available, try again later**`
* **Cause:** YouTube rate-limited your IP address.
* **Fix:** Change your IP address (VPN / Hotspot) and ensure `--sleep-requests 5` is present in your command.


* **Resuming an interrupted download:**
* Just run the standard command again in the exact same folder. As long as `--download-archive downloaded.txt` is present, it will pick up right where it left off.
