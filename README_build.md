# KenBurns v3.2 – Build Windows .exe

This is your working copy prepared for distribution.

## Files
- `KenBurns_v3_2_dist.py` – updated script that auto-detects ffmpeg.exe when bundled
- `build.bat` – one-click build script for Windows

## Requirements on build machine (Windows 10/11)
1. Python 3.10+ (check "Add to PATH" during install)
2. FFmpeg: download ffmpeg-release-essentials.zip from https://www.gyan.dev/ffmpeg/builds/
   - Extract `ffmpeg.exe` (from bin folder)
3. PyInstaller:
   ```
   pip install pyinstaller
   ```

## Quick build – single .exe (requires ffmpeg installed on user PCs)
```bat
pyinstaller --onefile --windowed --name KenBurns_v3_2 KenBurns_v3_2_dist.py
```
Output: `dist\KenBurns_v3_2.exe`
Users must have ffmpeg in PATH, or place ffmpeg.exe next to the exe.

## Recommended – bundle ffmpeg inside
1. Put `ffmpeg.exe` in same folder as the .py file
2. Run:
```bat
pyinstaller --onefile --windowed --name KenBurns_v3_2 --add-binary "ffmpeg.exe;." KenBurns_v3_2_dist.py
```
This creates a true standalone exe (~25-30 MB). No install needed.

## Using build.bat
Double-click `build.bat` – it will detect ffmpeg.exe and choose the right mode automatically.

## Distribution folder structure
```
KenBurns_v3_2/
  KenBurns_v3_2.exe
  README.txt
  (optional) ffmpeg.exe  <-- if not bundled
```

## Notes
- The app uses Tkinter (built-in) – no extra Python packages needed
- Output video is 1920x1080, 25fps, H.264
- First run may be slow as Windows Defender scans the onefile exe
- If you get "ffmpeg not found", ensure ffmpeg.exe is either bundled or in same folder
