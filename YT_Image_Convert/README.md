# YT: PNG→JPG ≤2MB (HQ) – macOS Automator Quick Action

This Automator **Quick Action** converts PNG images (or other formats) into
**YouTube-ready JPGs** at the highest quality possible while ensuring the
final file size is **≤ 2 MB**. It appends `-yt.jpg` to the filename so you can
quickly identify the optimized thumbnail.

---

## Features

- 📏 **Resizes only if needed** (max 1920×1080, never upscales).
- 🎨 **sRGB color profile** for consistent web/YouTube colors.
- 💾 **File size capped at 2 MB**:
  - Iteratively reduces JPEG quality until ≤ 2 MB.
  - If still too large, gently downscales the image (ImageMagick: 2% steps; sips: 10% step).
- ⚡ **ImageMagick preferred** (best compression/controls).
  - Falls back to macOS `sips` if ImageMagick is not installed.
- 🏷 **Output filename**: `originalname-yt.jpg`.
- 🖱️ Accessible via Finder → **Right-click → Quick Actions**.

---

## Requirements

- macOS (tested on Monterey, Ventura, Sonoma).
- Automator (preinstalled).
- Optional but recommended: [ImageMagick](https://imagemagick.org)  
  Install via [Homebrew](https://brew.sh/):

  ```bash
  brew install imagemagick
  ```

---

## Installation

1. Open **Automator**.
2. Create a **New Document** → **Quick Action**.
3. Configure:
   - **Workflow receives current:** `image files`  
   - **in:** `Finder`
4. Add an action: **Run Shell Script**.
   - **Shell:** `/bin/bash`  
   - **Pass input:** `as arguments`
5. Paste in the contents of `yt_png2jpg.sh` (the script from this repo).
6. Save as: **YT: PNG→JPG ≤2MB (HQ)**.

The Quick Action will now appear in Finder under:  
**Right-click → Quick Actions → YT: PNG→JPG ≤2MB (HQ)**.

---

## Usage

1. In Finder, select one or more PNG (or JPG) files.
2. Right-click → **Quick Actions → YT: PNG→JPG ≤2MB (HQ)**.
3. The optimized JPGs will be created in the same folder, named:
   ```
   mythumbnail.png   →   mythumbnail-yt.jpg
   ```

---

## Notes

- ImageMagick branch: progressive JPEG, 4:2:0 sampling, iterative quality reduction.
- sips branch: uses native macOS tools, finds valid sRGB ICC profile if available.
- Both guarantee the best quality possible at or under 2 MB.

---

## License

MIT License. Use freely for personal or commercial work.
