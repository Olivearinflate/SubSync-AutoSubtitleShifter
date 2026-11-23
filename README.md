<p align="center">
  <img src="https://i.postimg.cc/FsDfVSmP/banner.png" alt="SubSync Subtitle Tool — Batch SRT/ASS Time Shifter, FPS Converter & Encoding Fixer" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Subtitle%20Sync%20%26%20UTF-8-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-subsynctool--v1.2-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# SubSync Subtitle Tool — Batch SRT/ASS Time Shifter, FPS Converter & Encoding Fixer

**Downloaded subtitles appearing 3 seconds too early, drifting out of sync halfway through a movie due to 23.976 vs. 25 FPS mismatch, or showing unreadable symbols instead of Cyrillic/accented letters? Fix any .SRT, .ASS, or .VTT file in one click.**

SubSync Subtitle Tool solves the four most common subtitle headaches on Windows: **shifting all timestamps forward or backward by exact milliseconds, stretching/shrinking timing between `23.976`, `24`, `25`, and `29.97` FPS, repairing Windows-1251/1252 mojibake into clean UTF-8, and stripping `[SDH]` hearing-impaired brackets**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) media collectors, translators, and video editors** managing `.srt`, `.ass`, `.ssa`, and `.vtt` subtitle tracks offline.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Subtitles appear consistently 2–5 seconds early or late | Different intro logo duration between video release and subtitle source | Shift all timestamps by exact `+` or `-` milliseconds (`e.g. +2400 ms`) |
| Subtitles start in sync but drift off by several seconds at the end | Frame-rate mismatch (`23.976 fps` NTSC vs. `25.000 fps` PAL) | Apply linear FPS conversion (`23.976 -> 25.000` or `25.000 -> 23.976`) |
| Subtitles display gibberish (`ÐŸÑ€Ð¸Ð²ÐµÑ‚` or `???`) on TV / player | Legacy ANSI / Windows-1251 encoding instead of UTF-8 | Auto-detect source codepage and convert cleanly to UTF-8 |
| Subtitles cluttered with `[MUSIC PLAYING]` or `[DOOR CREAKS]` | SDH hearing-impaired annotations distract from dialogue | Strip bracketed `[...]` / `(...)` SDH cues and HTML font tags in bulk |

## Download for Windows

[**Download SubSyncTool.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/SubSyncTool.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `SubSyncTool.exe`? (Key features)

- Shifts timestamps by exact seconds/milliseconds (`+` or `-`) across `.srt`, `.ass`, `.ssa`, and `.vtt` files.
- Converts frame-rate drift (`23.976 ↔ 24 ↔ 25 ↔ 29.97 FPS`) with sub-millisecond precision.
- Auto-detects legacy Windows-1251 / Windows-1252 / UTF-16 encodings and converts to clean UTF-8.
- Optional SDH cleaner removes `[sound effects]` and empty lines while re-indexing cue numbers.

### Sample Output

```text
[SubSyncTool] Loaded: Episode_04.srt (618 cues | Detected Encoding: Windows-1251)
[INFO] Applied Ops      : Time Shift +1,850 ms | FPS 23.976 -> 25.000 | Convert to UTF-8
[OK]   Exported File    : Episode_04_synced.srt (618 valid cues | UTF-8 BOM-free)
```

The release ZIP is named `SubSyncTool.zip`; the Windows executable inside is named `SubSyncTool.exe`.

1. Close SubSync Tool before updating or replacing executable files.
2. Click **Download SubSyncTool.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `SubSyncTool.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit).

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `SubSyncTool.exe` runs locally without uploading your files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Gradual drift from 23.976 vs. 25 FPS releases

Simple time-shifting cannot fix progressive drift; linear FPS ratio scaling aligns the entire movie from start to finish.

### Broken Cyrillic and European characters on Smart TVs

Smart TVs and Plex/Kodi clients require UTF-8 encoding; converting legacy ANSI subtitles fixes unreadable symbols immediately.

### Batch fixing entire TV seasons in one drag-and-drop

Drop all 24 `.srt` files of a season and apply the exact same offset or encoding fix in one click.

### 100% local offline processing

Works instantaneously without uploading files.

## Default folders and configuration paths

SubSync Tool saves fixed subtitle files beside your original tracks:

```text
%USERPROFILE%\Videos\
```

Typical directory layout:

```text
Videos\Series\
├── S01E01.mkv
├── S01E01.srt           (Original out-of-sync / ANSI)
└── S01E01_synced.srt    (Synced & UTF-8 — Ready for VLC / MPV / TV)
```

Keep a backup of the original `.srt` before overwriting if you are fine-tuning custom millisecond offsets.

## Quick start guide

Follow these steps to get started:

1. **Extract `SubSyncTool.zip` and launch `SubSyncTool.exe`.** No installation required.
2. **Drag one or multiple `.srt`, `.ass`, or `.vtt` files onto the window.** Preview the first and last subtitle timestamps immediately.
3. **Enter millisecond offset (`+` / `-`), choose FPS conversion, or check **Fix Encoding to UTF-8**.** Optionally enable **Remove [SDH] Tags**.
4. **Click **Save Synced Subtitles** and test in your media player.** Verify dialogue alignment near both the start and end of the video.

### Data safety note

Original subtitle files are preserved with a `_synced` suffix unless overwrite mode is selected.

## What the status summary shows

SubSync Tool reports **cue count, detected character encoding, applied time/FPS shift, and output path**.

## FAQ

**What subtitle formats does SubSync Tool support?**

SubRip (`.srt`), SubStation Alpha (`.ass` / `.ssa`), and WebVTT (`.vtt`).

**How do I fix subtitles that show weird symbols instead of Russian or accented letters?**

Enable 'Convert Encoding to UTF-8'—SubSync automatically detects Windows-1251/1252 and converts to UTF-8.

**Can I process an entire season of episodes at once?**

Yes—drag all episode subtitle files into the window for batch processing.

## Useful reading

- [SubRip (.SRT) Format Specification](https://www.matroska.org/technical/subtitles.html)

## More Windows Desktop Utilities

- [WhisperDesk-OfflineTranscriber](../WhisperDesk-OfflineTranscriber) — Local offline speech-to-text & SRT subtitle generator
- [SnapFormat-BatchMediaConverter](../SnapFormat-BatchMediaConverter) — Offline batch HEIC/WebP/MKV to JPG/PNG/MP4 converter
- [ClipShrink-DiscordCompressor](../ClipShrink-DiscordCompressor) — Compress gameplay clips to exact 10 MB / 50 MB Discord limits
- [BulkRename-RegexFileRenamer](../BulkRename-RegexFileRenamer) — Windows batch file & episode renamer with live preview

*Independent open-source desktop utility for Windows.*
