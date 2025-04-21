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
  path:           /assets/img/projects/Sorang/banner.png
  srcset:
    1920w:        /assets/img/projects/Sorang/banner.png
    960w:         /assets/img/projects/Sorang/banner.png
    480w:         /assets/img/projects/Sorang/banner.png
caption:          Digital Storytelling Platform

title:            SoRang SoRang
date:             2024-12-10 11:37:00
description:      Digital Storytelling Platform
hide_description: true
featured:         false

links:
  - title:        GitHub URL
    url:          https://github.com/SooNolEum

---

> **Connecting generations through storytelling**

**"SorangSorang"** is a digital storytelling platform that bridges the gap between Jeju Island's elderly population 
and younger generations through interactive stories and cultural exchange.

We developed an innovative voice-to-story system that transforms the oral traditions of Jeju elders into engaging digital content for children, 
preserving cultural heritage while creating meaningful intergenerational connections.

For more information, please [**check our GitHub repository!**](https://github.com/SooNolEum)

---
## Project Info

- **Name**: Sorang Sorang (소랑소랑)
- **Genre**: Digital Storytelling Platform
- **Platform**: Web
- **Tech Stack**: TypeScript, Next.js, Zustand, TailwindCSS
- **Development Period**: December 2024
- **Achievement**: Grand Prize at 12th kakao x goorm Hackathon

## Core Technologies

### 📔 Story Foundation
- Robust form validation with **React Hook Form + Zod**
- Global state management using **Zustand** with **Local Storage** persistence
- Region-specific keyword system for cultural context

### 👵🏻 Voice-to-Story Transformation (Senior's Interface)
- Real-time audio visualization for recording status feedback
- Voice-to-text conversion through **Clova STT API** integration
- **GPT-4 based** fairy tale and educational quiz generation

### 🧒🏻 Interactive Learning Experience (Children's Interface)
- Story-based quiz solving system with engaging interactions
- Region-specific Jeju items as rewards for correct answers
- Interactive UI/UX designed for cultural learning and engagement