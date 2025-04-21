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
  path:           /assets/img/projects/PintOS/banner.png
  srcset:
    1920w:        /assets/img/projects/PintOS/banner.png
    960w:         /assets/img/projects/PintOS/banner.png
    480w:         /assets/img/projects/PintOS/banner.png
caption:          Operating System Implementation

title:            PintOS Project
date:             2023-03-10 11:37:00
description:      Operating System Implementation
hide_description: true
featured:         false

links:
  - title:        More Info
    url:          https://github.com/youjuice/PintOS

---

**"PintOS"** is an educational operating system project where I implemented core OS functionalities to deepen 
my understanding of system architecture.

I built essential components of a functioning operating system, gaining hands-on experience 
with low-level systems programming while developing practical skills in memory management and concurrency control.

For more information:
- [**📎 GitHub Repository**](https://github.com/youjuice/PintOS)
- [**📔 Dev Diary**](https://ringed-postage-dfc.notion.site/PintOS-e7be8de4a7944308bba8bd79cb3465bf?pvs=4)

---
## Project Info

- **Name**: PintOS Project
- **Genre**: Operating System Implementation
- **Type**: Individual Project
- **Tech Stack**: C
- **Development Period**: May 2024 - June 2024

## Core Components Implemented

### 🧵 Project 1: THREADS
- Priority-based scheduling with **multilevel feedback queue**
- **Semaphore implementation** for synchronization primitives
- **Priority donation** mechanism to solve priority inversion problems

### 🔄 Project 2: USER PROGRAM
- Comprehensive system call handlers for process management
- File operation system calls including **read, write, open, and close**
- Memory allocation system calls with proper validation

### 💾 Project 3: VIRTUAL MEMORY
- **Page replacement algorithm** implementation (Second-Chance)
- **Swap mechanism** for efficient memory utilization
- **Copy-on-Write** optimization for process forking
- **Memory-mapped files** for efficient I/O operations