---
last_modified_at: 2025-04-08 06:25:00
no_link_title:    false
no_excerpt:       false
hide_image:       false
hide_title:       false

layout:           project
cover:            false
sidebar:          false
order:            0

image:
  path:           /assets/img/projects/Raytracer/banner.png
  srcset:
    1920w:        /assets/img/projects/Raytracer/banner.png
    960w:         /assets/img/projects/Raytracer/banner.png
    480w:         /assets/img/projects/Raytracer/banner.png
caption:          WebGL-based Ray-Tracing Renderer

title:            WebGL-based Ray-Tracing Renderer
date:             2024-09-10 11:37:00
description:      WebGL-based Ray-Tracing Renderer
hide_description: true
featured:         false

links:
  - title:        GitHub URL
    url:          https://github.com/youjuice/webgl-raytracer

---

This project was my exploration into ray tracing techniques implemented directly in web browsers using WebGL. 
I built this renderer to deepen my understanding of both real-time graphics programming and GPU-accelerated rendering pipelines.

For more information, please [**check my GitHub repository!**](https://github.com/youjuice/webgl-raytracer)

---
## Project Info

- **Name**: WebGL-based Ray-Tracing Renderer
- **Type**: Personal Study Project
- **Tech Stack**: TypeScript, Babylon.js, WebGL, GLSL
- **Development Period**: September 2024

## Implementation Details

### Ray Tracing Implementation
- Implemented ray-object intersection algorithms
- Created shader-based rendering of shadows and reflections
- Built a complete rendering pipeline using WebGL and GLSL

### Acceleration Structure
- Implemented a Bounding Volume Hierarchy (BVH) for efficient ray casting
- Applied Surface Area Heuristic (SAH) for optimal tree construction
- Used texture-based data structures for GPU-friendly memory access