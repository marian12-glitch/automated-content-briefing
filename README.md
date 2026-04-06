# 🎬 Automated Content Briefing System

A cost-efficient, fully open-source pipeline that transforms a long-form text article into a structured multimedia briefing video — automatically.

Built as part of the ThinkFlix Machine Learning Engineer technical challenge.

---

## What It Does

Given a text article as input, the system:

1. **Extracts & structures** key ideas into Introduction, Key Points, and Summary sections
2. **Generates spoken audio narration** using free Microsoft Neural TTS
3. **Creates visual slides** for each section
4. **Assembles a final MP4 video** with synced audio and visuals

---

##  Tech Stack

| Tool | Purpose |
|------|---------|
| `sumy` (LSA) | Extractive summarization — no LLM required |
| `edge-tts` | Free Microsoft Neural text-to-speech |
| `matplotlib` | Slide image generation |
| `moviepy 1.0.3` | Video assembly & audio-visual sync |
| `nltk` | Text tokenisation |
| `nest_asyncio` | Async compatibility fix for Windows/Jupyter |

**Total cost to run: $0.00**

---

##  How To Run

### 1. Clone the repo
```bash
git clone https://github.com/YOUR_USERNAME/content-briefing-system.git
cd content-briefing-system
```

### 2. Install dependencies
```bash
pip install sumy edge-tts "moviepy==1.0.3" matplotlib pillow nltk imageio imageio-ffmpeg nest_asyncio
```

### 3. Open the notebook
```bash
jupyter notebook briefing_pipeline.ipynb
```

### 4. Run all cells top to bottom

Your output video will be saved to `output/briefing_final.mp4`

---

## 📁 Output Structure

```
output/
├── narration_00.mp3       # Welcome audio
├── narration_01.mp3       # Section headers & content audio
├── ...
├── full_narration.mp3     # Merged narration track
├── slide_00_title.png     # Title slide
├── slide_01_introduction.png
├── slide_02_key points.png
├── slide_03_summary.png
├── slide_05_end.png
└── briefing_final.mp4     # ✅ Final output video
```

---

## ⚙️ System Architecture

```
[Text Input]
     │
     ▼
[Content Processing]  ← sumy LSA extracts key sentences per section
     │
     ▼
[Audio Generation]    ← edge-tts converts script to MP3 per section
     │
     ▼
[Slide Generation]    ← matplotlib renders dark-themed PNG slides
     │
     ▼
[Video Assembly]      ← moviepy syncs each slide to its audio clip
     │
     ▼
[briefing_final.mp4]
```

---

## 💡 Key Design Decisions

- **No paid APIs** — edge-tts is free, sumy runs locally, no GPU required
- **Extractive summarization** chosen over abstractive to avoid hallucination and remove LLM dependency
- **Dynamic slide duration** — each slide duration is set to match its audio length for perfect sync
- **Runs on any machine** — no GPU needed, completes in under 5 minutes on CPU

---

## 👤 Author

Marian Enam Esi Kushigbor  
ThinkFlix ML Engineer Challenge Submission
