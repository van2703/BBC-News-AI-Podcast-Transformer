# Requirement Specification
## BBC News AI Podcast Transformer

**Version:** 1.0  
**Author:** vanpham

---

# 1. Project Overview

The **BBC News AI Podcast Transformer** is a system that automatically collects news from BBC News, summarizes the content using AI, generates a short podcast script, converts the script into audio, and publishes the podcast on a website.

Each generated episode is approximately **5 minutes long**.

The final podcast episodes are hosted on a **GitHub Static Pages website**, where users can listen to the audio.

---

# 2. System Pipeline

The system processes data through the following steps:

1. Fetch BBC News articles from RSS feed  
2. Extract article content  
3. Summarize articles using AI  
4. Generate podcast script  
5. Convert script to speech (TTS)  
6. Add random background music  
7. Export podcast audio (.mp3)  
8. Save audio into repository  
9. Update website episode list  
10. Deploy to GitHub Pages  

---

# 3. Core Features

## News Collection

The system collects **5 articles from the BBC News RSS feed** and extracts their main content.

---

## AI Script Generation

The system uses an AI model to:

- summarize the collected articles  
- generate a **short podcast script (~5 minutes)**

The podcast is written as a **single-host monologue** with a simple structure:

Intro → News summaries → Outro

---

## Audio Production

The generated script is converted into speech using **Text-to-Speech (TTS)** tools such as:

- Edge-TTS  
- gTTS  

The system then adds **random background music** and exports the final podcast as an **MP3 file**.

---

# 4. Technical Stack

**Programming Language**

- Python

**AI Engine**

- OpenRouter API (script generation and summarization)

**Audio Processing**

- Edge-TTS or gTTS  
- MoviePy (audio mixing)

**Website**

- GitHub Static Pages

**Storage**

Podcast audio files are stored **directly in the repository**.

No database is required.

---

# 5. System Execution

The system can run in two ways.

## Automatic Execution

The pipeline runs automatically every day using a **GitHub Actions cron job**.

Example schedule:

06:00 every day

---

## Manual Execution

The system can also be run manually:
python run_pipeline.py

This command triggers the full pipeline.

---

# 6. Summary

The project demonstrates how AI can automate the process of turning written news articles into audio podcasts.

The system combines:

- news collection  
- AI-generated scripts  
- text-to-speech audio production  
- automated website publishing
