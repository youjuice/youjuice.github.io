---
last_modified_at: 2025-04-22 06:25:00
no_link_title:    false
no_excerpt:       false
hide_image:       false
hide_title:       false

layout:           project
cover:            false
sidebar:          false
order:            0

image:
  path:           /assets/img/projects/DJYe/banner.png
  srcset:
    1920w:        /assets/img/projects/DJYe/banner.png
    960w:         /assets/img/projects/DJYe/banner.png
    480w:         /assets/img/projects/DJYe/banner.png
caption:          Discord Music Bot

title:            DJ Ye
date:             2024-09-10 11:37:00
description:      Discord Music Bot
hide_description: true
featured:         false

links:
  - title:        GitHub URL
    url:          https://github.com/youjuice/dj-ye

---

**"DJ Ye"** is a feature-rich Discord music bot that allows users to play and manage music directly 
in voice channels with simple commands and an intuitive interface.

I developed this bot to enhance Discord server experiences with seamless music playback, robust queue management, 
and an interactive user interface that makes controlling music as simple as clicking a button.

For more information:
- [**📎 GitHub Repository**](https://github.com/youjuice/dj-ye)
- [**📔 Dev Diary**](https://ringed-postage-dfc.notion.site/DJ-Ye-03d1b38a49c640bb99b6090c7eb1bb60?pvs=4)

---
## Project Info

- **Name**: DJ Ye
- **Type**: Discord Bot
- **Tech Stack**: Python, Discord.py, YouTube API
- **Current Version**: v1.0.1
- **Development Period**: September 2024

## Key Features

### 🎵 Music Playback
- Song search and playback by title and artist name
- Direct YouTube URL playback support
- Volume control functionality

### 📋 Queue Management
- Adding and removing songs from playlist
- Viewing current playlist
- Skipping to specific tracks
- Shuffle playlist functionality

### 🎧 User Interface
- Intuitive button controls (play/pause, next, previous)
- Automatic relocation of control buttons when new songs play

## Technical Highlights

- **Asynchronous Architecture** using Python's asyncio for efficient resource management
- **Optimized playback engine** with improved recursion handling and exception management
- **Background task processing** for enhanced bot responsiveness