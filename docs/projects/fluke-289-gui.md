---
title: "Fluke 289 Live GUI"
subtitle: "Real-time capture, freeze-frame triggers (ESP32), plots, and status indicators"
date: 2025-06-15
updated: 2025-10-04
category: "Desktop Tools & GUIs"
role: ["Design", "Implementation"]
stack: ["Python", "CustomTkinter", "Serial", "Matplotlib"]
tags: [python, gui, dmm, serial, esp32]
repo: https://github.com/ghartwell96/fluke-289-gui
cover: assets/fluke-289-gui/cover.jpg
---


!!! abstract "Summary"
    **What:** Desktop GUI for Fluke 289 with live plot, capture, and ESP32 freeze-frame trigger.  
    **Why:** Speeds up captures in calibration/repair workflows.  
    **Role:** Design & implementation.  
    **Stack:** Python, CustomTkinter, Matplotlib, Serial.

#### Problem
Manual captures were slow and error-prone during troubleshooting and verification.

#### Approach
- Serial driver for Fluke 289 (robust timeouts/retries).
- GUI with live plot, capture queue, CSV export.
- ESP32 BLE/TCP trigger to “freeze” and bookmark events.

#### Key Outcomes
- Faster capture workflow (repeatable steps, fewer mis-clicks).
- Clean CSV logs for later analysis.

#### Media
<figure>
  <img src="/assets/fluke-289-gui/cover.jpg" alt="Fluke 289 GUI overview" />
  <figcaption>Live plot, capture controls, and ESP32 trigger status.</figcaption>
</figure>

#### Architecture
```mermaid
flowchart LR
  GUI[CustomTkinter GUI] --> Serial[Fluke 289 Serial]
  GUI --> ESP32[ESP32 Trigger (BLE/TCP)]
  GUI --> CSV[CSV Export]
