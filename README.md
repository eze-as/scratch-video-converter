# 🎬 Scratch Video Converter (HTML5 + Delta Encoding)

A lightweight, in-browser preprocessor designed to convert MP4 video clips into highly compressed alphanumeric data streams for real-time rendering in **Scratch 3.0** via the **Pen** extension.
 
🔗 **Live Web Converter:** [https://tu-usuario.github.io/tu-repo/](https://tu-usuario.github.io/tu-repo/)  
🕹️ **Scratch Project:** [Link to your Scratch project here]

---

## ⚡ How It Works

Playing video in Scratch usually requires uploading hundreds of individual costume frames, which quickly hits project size limits and creates massive memory lag. This project tackles the challenge through client-side stream processing:

1. **Downscaling & Sampling:** The browser captures video frames at **10 FPS** on an HTML5 `<canvas>` sized to **$64 \times 48$ pixels** (3,072 pixels per frame).
2. **Color Quantization (64 Colors):** Each RGB pixel is mapped to the nearest color in a carefully calibrated 64-color palette using weighted Euclidean color distance.
3. **Scratch-Safe Collision Encoding:** Scratch list lookup blocks are case-insensitive (`a == A`). To prevent color corruption, the palette utilizes 26 uppercase letters (`A-Z`) and 38 unique symbols (`!`, `$`, `%`, `*`, etc.).
4. **Delta Encoding Compression:** Instead of redrawing the entire canvas each frame, the engine only tracks and outputs pixels that changed relative to the previous frame (`[skip][color]#[skip][color]...`). This cuts output payload sizes by **60% to 80%** and enables smooth real-time playback.

---

## 🚀 Quick Start

1. Open the [Web Converter](https://tu-usuario.github.io/tu-repo/).
2. Select any `.mp4` video (short clips under 20 seconds are recommended).
3. Click **Process Video (64 Colors + Delta)**.
4. Click **Copy to Clipboard**.
5. In the Scratch project, click the **Green Flag**, paste the payload into the prompt, and press Enter.

> 💡 **Tip:** Enable **Turbo Mode** in Scratch (`Shift + Click on Green Flag`) for silky-smooth 10 FPS playback.

---

## 🛠️ Tech Stack

* **Frontend:** Vanilla JavaScript, HTML5 Canvas API, File & Video APIs.
* **Rendering Engine:** Scratch 3.0 with the Pen Extension.
* **License:** MIT
