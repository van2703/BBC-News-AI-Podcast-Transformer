# BBC News AI Podcast Transformer – Architecture Design

1\. High-Level Architecture

System includes: News Fetcher, AI Script Generator(openrouter), Podcast Generator (TTS + Music), Storage (Google Drive), SQLite DB, Streamlit Website, Scheduler.

2\. Component Architecture

\- News Fetcher: extract 5 BBC articles.

\- Script Generator: summarize, style decision, sentiment analysis.

\- Podcast Generator: TTS + music mixing (MoviePy).

\- Storage: upload mp3, cleanup old files.

\- Database: store episodes + logs.

\- Website: display episodes + admin panel.

\- Scheduler: auto-run daily at 06:00.

3\. Data Flow

BBC → Fetcher → openrouter → TTS/Music → Drive + DB → Streamlit UI.

4\. Database Schema

Episodes(id, title, script, bbc\_links, audio\_url, sentiment, created\_at)

Logs(message, level, created\_at)

5\. Non-Functional Requirements

Performance, reliability, fallback, cost optimization, security.

6\. Architecture Decisions

openrouter for text processing, Edge-TTS for low-cost TTS, MoviePy for audio mixing,

Streamlit for simple UI + admin, SQLite DB for lightweight storage.