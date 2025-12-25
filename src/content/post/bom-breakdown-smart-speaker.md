---
title: "BOM Breakdown: Voice-Controlled Smart Speaker"
description: "Where the money actually goes in a $50 voice device. A line-by-line analysis of component costs."
publishDate: "2024-12-24"
tags: ["bom breakdown", "cost analysis", "manufacturing"]
pinned: true
---

## The $15 BOM Target

Building a voice-controlled device for under $50 retail means your Bill of Materials (BOM) needs to hit ~$15. Here is how we achieve that with the Tau Labs reference architecture.

### Core Compute & Connectivity (~$4.50)

The heart of the system. We choose the ESP32-S3 for its balance of AI performance and cost.

| Component | Part Number | Cost (10k qty) | Notes |
| :--- | :--- | :--- | :--- |
| SoC | ESP32-S3-WROOM-1 | $2.10 | Dual-core Xtensa, AI instructions |
| Flash | 16MB SPI Flash | $0.80 | Required for large voice models |
| PSRAM | 8MB Octal PSRAM | $1.60 | Essential for audio buffering |

### Audio Front End (~$3.20)

Clean audio is non-negotiable. We use a dual-mic topology.

| Component | Part Number | Cost (10k qty) | Notes |
| :--- | :--- | :--- | :--- |
| Mics | MEMS Analog Mic (x2) | $0.90 | 65mm spacing for beamforming |
| ADC | ES7210 | $1.10 | 4-channel ADC for mic array |
| Amp | MAX98357A | $1.20 | 3W Class-D Amplifier |

### Power & Mechanical (~$5.50)

Often overlooked, but critical for "feel".

| Component | Part Number | Cost (10k qty) | Notes |
| :--- | :--- | :--- | :--- |
| PCB | 4-layer FR4 | $1.50 | Impedance controlled |
| Battery | 2000mAh Li-Po | $2.50 | Certified cell |
| Plastics | Injection Molded ABS | $1.50 | Tooling amortized separately |

### Assembly & Packaging (~$1.80)

| Item | Cost |
| :--- | :--- |
| SMT Assembly | $0.80 |
| Final Assembly | $0.60 |
| Box & Manual | $0.40 |

### Total: $15.00

This leaves margin for logistics, marketing, and software development. By choosing the ESP32-S3 over a Linux-based Cortex-A solution, we save ~$8 per unit, making the product viable at retail.
