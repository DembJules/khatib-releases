# Khatīb — Oral Heritage to Academic Book

### Local AI Audio Transcription, Multi-Source Media Downloader & Academic Book Publisher

A high-performance, private, 100% offline-capable AI speech recognition, multilingual transcription, and academic publication suite powered by **`whisper.cpp`** and **`llama.cpp`**. Designed to turn hours of spoken oral heritage, academic lectures, and religious discourse into beautifully formatted, vocalized, and structured Word documents (`.docx`) and books.

---

## 🌟 Key Features & Architecture

### 1. Trilingual Localization Engine (English, Français, العربية)
- **Full Application Coverage**: All 7 tabs, modal dialogs, context menus, settings panels, and live consoles are fully localized in **English**, **French (Français)**, and **Arabic (العربية)**.
- **Dynamic 1-Click Language Switcher**: Switch languages instantly from the top bar (`🌐 Language / Langue / اللغة`). All active windows, modal dialogs, and notebook tabs update dynamically in real time without requiring an application restart.
- **Bi-Directional Alignment**: Comprehensive right-to-left (RTL) typographic handling for Arabic text and annotations.

### 2. Multi-Source Audio & Video Pipeline (Tab 1)
Streamline ingestion from any audio/video source into a structured, unified workflow:
- **📁 Local Folders**: Batch-transcribe `.mp3`, `.mp4`, `.wav`, `.m4a`, `.aac`, `.mkv`, `.ogg`, `.flac`, and `.webm` files. Includes recursive subfolder discovery and incremental processing (skips already-transcribed files).
- **📺 YouTube (`YoutubeDownload.py`)**: Download single videos, Shorts, or complete playlists with automated archive tracking (`downloaded.txt`), 1-click archive rebuilding, and automatic cleanup of transient `.webm` files.
- **💾 Google Drive (`GDriveDownload.py`)**:
  - Full support for shared folders (including massive archives with **3,000+ audio files**) and direct file links.
  - **Sequential Streaming ("Low Disk Space Mode")**: Downloads one file, transcribes it, appends it to Word, and optionally deletes the audio before fetching the next lesson.
  - **Folder Inspector**: Inspect and preview files in any remote Drive folder, auto-detect subjects from filenames, and selectively process items.
- **✈️ Telegram (`TelegramDownload.py`)**:
  - Fetch voice notes, audio lectures, and videos from public Telegram channels or post links with **zero API key or phone login required**.
  - Supports both Batch mode and Low Disk Space sequential processing with keyword filtering.

### 3. Models & Agents Hub (Whisper, Custom Hugging Face & LLaMA GGUF)
- **Curated Speech Models**: 1-click downloads for official Whisper models (`large-v3`, `large-v3-turbo`, `large-v3-q5_0`, `medium`, `small`, `base`).
- **Custom Hugging Face Whisper Models**: Directly browse, search, and download fine-tuned community Whisper models (e.g. `akashmjn/whisper-large-v3-arabic-ggml`, `bofenghuang/whisper-large-v3-french-ggml`, `distil-whisper/distil-large-v3-ggml`).
- **Live Hugging Face Search**: Search Hugging Face directly within the app for any custom `.bin` model file with automatic destination routing to `models/`.
- **Local GGUF LLMs**: Download and manage local models (Qwen 2.5 3B/7B, LLaMA 3.1, Mistral) for chapter titling and offline AI chat.
- **175+ Specialized Agents**: Install specialized offline agent personas with workspace retrieval-augmented generation (RAG) and persistent memory.

### 4. Academic Book Publisher Engine (Tab 7 & Tab 1 Integration)
- **Dawrah 2023 Academic Cover Page**: Generates formal book covers with classical Arabic calligraphy, Latin titles, volume subtitles, teacher/author credits, and decorative academic borders.
- **Arabic Tashkeel & Auto-Vocalization**: Automatic vocalization and diacritic placement for Arabic titles (`[ 🪄 Auto-Vocalize ]`).
- **Multi-Level Table of Contents (Levels 1–3)**: Generates hierarchical Word TOCs displaying the Book Title (H1), Lectures/Chapters (H2), and Thematic Subsections (H3) with calculated page numbers.
- **Flexible Layout Modes**: Choose between `CONTINUOUS` (academic treaty style) and `DIALOGUE` (Q&A / question-and-answer format).
- **Academic Footnotes & Transliteration**: Automatic transliteration indexing, verse adornment (`﴿ ... ﴾`), and standardized honorifics (ﷺ, ﷻ, ؓ, ؑ).
- **Instant Word Document Opener**: Direct top-bar button (`📄 Open Last Word Doc`) with optimized fast loading for documents spanning 2,000+ pages.

### 5. Acoustic Tuning & Vocabulary Training Studio (Tab 5)
- **Instant Phonetic Correction Rules**: Add acoustic misrecognition pairs (e.g. French *"doigts"* ➔ *"dou'as"*, *"rondo"* ➔ *"woudou"*, *"khoutba"* ➔ *"khoutbah"*) that immediately update `learned_corrections.json` and apply to future and existing transcripts.
- **Whisper Neural Prompt Conditioning (`--prompt`)**: Injects targeted vocabulary into Whisper's neural decoder before audio processing to bias phoneme recognition toward correct terminology.
- **Automated Differential Learning**: Diffs raw transcripts against human-revised `.docx` manuscripts to automatically extract vocabulary rules and misheard phrases.
- **Direct Word Document Correction Pass**: Runs full dictionary replacement passes across existing Word documents without re-transcribing audio files.

### 6. Local LLM Titling, Chat & Offline Personal Agent (Tabs 3 & 4)
- **Tab 3 — LLaMA Chat & Safe Web Research**: Local chat powered by `llama-server` with optional keyless HTTPS DuckDuckGo & Wikipedia search.
- **Tab 4 — 100% Offline Personal Agent**: Isolated workspace assistant with RAG across `.docx`, `.txt`, and `.srt` files, persistent memory (`agent_memory.json`), and custom agent creation tools.

### 7. Hardware-Adaptive GPU Acceleration (CUDA / Vulkan / Metal / CPU)
- **NVIDIA GPU (CUDA 11.7 – 13.5)**: Automated GPU detection and portable runtime downloader (`DownloadCudaDLLs.bat` / `download_cuda_dlls.py`). Uses isolated portable runtime DLLs (`cublas64`, `cudart64`, `cublasLt64`) without requiring a complete NVIDIA CUDA Toolkit installation.
- **AMD Radeon GPU (Vulkan)**: High-speed GPU acceleration via `ggml-vulkan.dll` and Vulkan runtime.
- **Apple Silicon Mac (Metal)**: Zero-copy unified memory acceleration across M1/M2/M3/M4 Apple Silicon.
- **Multi-Core CPU Fallback**: Optimized multi-threaded execution for systems without a dedicated GPU.

---

## 🚀 Quick Start Guide

### Windows (10 / 11)

1. **Automated Setup & Verification**:
   Double-click `Install.bat` to verify hardware, Python packages (`python-docx`, `yt-dlp`, `gdown`), FFmpeg media decoder, and CUDA runtime libraries.
2. **NVIDIA CUDA GPU Acceleration (Optional but Recommended)**:
   Double-click `DownloadCudaDLLs.bat` to automatically detect your NVIDIA driver and download the matching portable CUDA runtime DLLs.
3. **Launch the Native Desktop App**:
   Double-click `01_START_DESKTOP_UI.bat` to launch the native GUI (with trilingual language switcher).
4. **Launch the Web Browser Interface**:
   Double-click `02_START_WEB_UI.bat` to open the web studio at `http://127.0.0.1:7860`.

---

### macOS (Apple Silicon & Intel)

1. **Automated Setup**:
   Open Terminal in the directory and run:
   ```bash
   ./install.sh
   ```
2. **Launch Desktop App**:
   ```bash
   ./01_START_DESKTOP_UI.sh
   ```
3. **Launch Web Studio**:
   ```bash
   ./02_START_WEB_UI.sh
   ```

---

### Linux / Headless Servers

1. **Install Python Dependencies**:
   ```bash
   pip install -r requirements.txt || pip install python-docx yt-dlp gdown
   ```
2. **Run System Verifier**:
   ```bash
   python install.py
   ```
3. **Launch Web Server**:
   ```bash
   ./02_START_WEB_UI.sh
   ```

---

## 🔒 Security & Privacy Architecture

- **Strict Localhost Binding**: Binds exclusively to `127.0.0.1` and enforces strict `Host` and `Origin` validation to protect against CSRF and DNS rebinding.
- **Path Traversal & Shell-Free Execution**: Subprocesses are invoked as argument vectors without shell interpolation (`shell=False`). Input paths are sanitized and strictly validated against directory traversal patterns.
- **100% Air-Gapped Capable**: All transcription, chapter titling, book compilation, and agent memory operations run entirely on local offline compute.

---

## 📄 License & Attribution

Powered by [whisper.cpp](https://github.com/ggerganov/whisper.cpp) and [llama.cpp](https://github.com/ggerganov/llama.cpp) under the MIT License.
Academic book publishing engine and Khatīb studio components developed for local offline preservation and publication of spoken heritage.
