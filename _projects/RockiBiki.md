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
  path:           /assets/img/projects/RockiBiki/banner.png
  srcset:
    1920w:        /assets/img/projects/RockiBiki/banner.png
    960w:         /assets/img/projects/RockiBiki/banner.png
    480w:         /assets/img/projects/RockiBiki/banner.png
caption:          Motion-based Boxing Game

title:            Rocki Biki
date:             2024-07-10 11:37:00
description:      Motion-based Boxing Game
hide_description: true
featured:         false

links:
  - title:        GitHub URL
    url:          https://github.com/Team-OSI

---

> **Boxing in your browser, moving in real life**

**"Rocki Biki"** is a real-time motion-based boxing game where your physical movements and voice become powerful in-game skills.

We developed a hybrid recognition system that transforms your punches, evasive moves, and voice commands into gameplay, 
creating an immersive interactive boxing experience right in your web browser.

For more information, please [**check our GitHub repository!**](https://github.com/Team-OSI)

---
## Project Info

- **Name**: Rocki Biki
- **Genre**: Motion-based Boxing Game
- **Platform**: Web
- **Tech Stack**: JavaScript, Next.js, Three.js, Node.js, SpringBoot, WebRTC
- **Development Period**: June 2024 - July 2024

## Core Features

- **Motion-Based Gameplay**: Control your character with real physical movements
- **Skill System**: Trigger special skills by performing specific boxing poses
- **Voice Command System**: Read random phrases aloud to activate power-ups with voice similarity scoring
- **Multiplayer Battles**: Challenge friends to boxing matches in real-time with WebRTC
- **Dynamic 3D Environment**: Immersive boxing arena with responsive character animations

## Technical Challenges
- Implemented **Mediapipe-based** pose landmark extraction for accurate motion recognition
- Built multi-threaded environment using **Web Workers** and **SharedArrayBuffer** for parallel processing
- Achieved **8.57x FPS increase** and **708x reduced latency** through performance optimization
- Enhanced motion detection accuracy with **EMA filtering** and **linear interpolation**
- Created a custom **voice similarity algorithm** to evaluate player vocal commands
- Rendered complex 3D scenes efficiently with **Three.js** optimization techniques