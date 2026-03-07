# Architecture Design

**Version:** 1.0  
**Author:** vanpham

---

# 1. System Overview

The BBC News AI Podcast Transformer is an automated pipeline that converts news articles into short podcast episodes.

The system performs the following tasks:

1. Collect news articles from BBC RSS feeds
2. Summarize the content using AI
3. Generate a podcast script
4. Convert the script into speech
5. Add background music
6. Publish the podcast on a website

The final podcast audio is stored in the repository and served through a **GitHub Pages website**.

---

# 2. High-Level Architecture

The system consists of four main components:

1. News Collection Module  
2. AI Processing Module  
3. Audio Production Module  
4. Website Publishing Module  

These components are connected in a sequential pipeline.

System flow:
BBC RSS Feed
-->
News Collection
-->
AI Processing
(Summarization + Script Generation)
-->
Audio Production
(TTS + Background Music)
-->
Podcast Audio (.mp3)
-->
Website Publishing
(GitHub Pages)

---

# 3. Component Description

## 3.1 News Collection Module

This module retrieves news articles from the **BBC News RSS feed**.

Responsibilities:

- Fetch the RSS feed
- Select the latest 5 articles
- Extract article title, link, and main content

Output:
  List of article texts

Implementation:

- Python
- RSS feed parsing library

---

## 3.2 AI Processing Module

This module processes the collected articles using an AI model.

Responsibilities:

- Summarize the articles
- Generate a podcast script (~5 minutes)

The generated script follows a simple structure:
  Intro → News summaries → Outro

Implementation:

- OpenRouter API
- AI language model

Output:
  Podcast script (text)

---

## 3.3 Audio Production Module

This module converts the podcast script into an audio file.

Responsibilities:

- Convert text to speech (TTS)
- Add random background music
- Export the final podcast audio

Implementation tools:

- Edge-TTS or gTTS
- MoviePy for audio processing

Output:
  Podcast episode (.mp3)

---

## 3.4 Website Publishing Module

This module publishes the generated podcast on a website.

Responsibilities:

- Save the audio file in the repository
- Update the episode list
- Deploy the website

Implementation:

- GitHub repository
- GitHub Pages for hosting

Users can access the website and listen to podcast episodes directly.

---

# 4. System Automation

The system pipeline is automated using **GitHub Actions**.

A scheduled workflow runs the pipeline every day.

Example schedule:
  6:00 AM

The workflow executes:
  python run_pipeline.py

This script triggers the entire system pipeline.

---

# 5. Summary

The architecture is designed as a simple automated pipeline.

Each component performs a specific task:

- News Collection retrieves articles
- AI Processing generates the podcast script
- Audio Production creates the podcast audio
- Website Publishing makes the podcast available online

The system demonstrates how multiple technologies can be integrated to build an **AI-driven content generation pipeline**.
