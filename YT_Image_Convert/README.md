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
