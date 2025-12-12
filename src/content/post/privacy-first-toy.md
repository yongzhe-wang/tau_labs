---
title: "Case Study: Designing a Privacy-First Voice Toy"
description: "Balancing local processing and cloud intelligence for a kid-safe interactive experience."
publishDate: "2023-11-20"
tags: ["case-study", "privacy", "hardware"]
---

Parents are rightfully worried about "spy toys." When a leading educational brand approached us to build a voice-interactive storytelling companion, their #1 requirement was privacy. They wanted the magic of ChatGPT without the risk of sending a child's bedroom conversations to a random server.

## The Hybrid Architecture

We designed a "Privacy Sandwich" architecture:

1.  **Layer 1: Local Wake Word & Command (On-Device)**
    The device listens *only* for a specific wake word ("Hey Tau"). This detection happens entirely on a low-power microcontroller (MCU). No audio leaves the buffer until this triggers.

2.  **Layer 2: Local Intent Classification (On-Device)**
    Once awake, the audio is processed by a small, local model to determine *intent*.
    - "Turn on the light" -> Handled locally.
    - "Tell me a story about a dragon" -> Flagged for generation.

3.  **Layer 3: Anonymized Cloud Request (Cloud)**
    If the request requires creative generation, we convert the speech to text *locally*. We then send *only the text prompt* to the cloud LLM. We strip all metadata. The cloud returns text, which is converted to speech *locally* on the device.

## Hardware Implementation

To support this, we built a custom PCB featuring:
- **Dual Microphone Array:** With hardware beamforming to isolate the child's voice from background TV noise.
- **Hardware Mute Switch:** A physical switch that electrically disconnects the microphones, giving parents absolute peace of mind.
- **Secure Element:** To store cryptographic keys, ensuring the device cannot be hijacked.

## Outcome

The product launched in time for the holiday season. It achieved COPPA compliance and won a "Best of CES" award for its innovative approach to privacy. It proved that you don't have to sacrifice safety to build a magical, AI-powered product.
