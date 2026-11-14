# ESP32 CONTROLLER + 128x64 DISPLAY (OLEDMIRROR) - ᴇɴ

Mirroring the PC screen to a 128×64 OLED display connected to an ESP32 via USB.

```
┌───────────────────────────────┐
│           Desktop             │
│   Monitor / Window / Region   │
└──────────────┬────────────────┘
               │ USB-C (specific protocol with CRC)
               ▼
        ┌─────────────┐
        │    ESP32    │
        └──────┬──────┘
               │ I2C (or SPI)
               ▼
        ┌─────────────┐
        │ OLED 128×64 │
        └─────────────┘
```

The panel displays a real-time, monochrome version of what is on the screen.
It is not a CPU/RAM information panel—it is visual mirroring.

## Before you start: what to expect from the result

It is worth noting this before you build the circuit. A 1920×1080 screen has **2,073,600 pixels**.
The panel has **8,192**, and each one can only be on or off. Mirroring discards **99.6%** of the information.
**What you can see:** window layout, movement, whether a video is playing, the general shape of the content, the moving cursor.
**What you cannot see:** any text. A line of 1080p text occupies less than half a pixel on the panel.
**For a truly useful result:** mirror a **region** (e.g., 512×256) or a **small window** instead of the entire monitor.
The downscaling factor drops from 15× to 4×, making the content legible. The application supports all three modes for this reason.

by caiothedev<br/>
#esp32 #display #csharp #controller #text-mirror