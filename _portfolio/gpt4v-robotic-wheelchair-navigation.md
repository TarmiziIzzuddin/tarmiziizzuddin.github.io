---
title: "GPT-4V Robotic Wheelchair Navigation"
excerpt: "FYP student integrates OpenAI's GPT-4V with function calling to control a robotic wheelchair using vision and natural language for autonomous navigation.<br/><img src='/images/gpt4v-robotic-wheelchair-thumbnail.jpg'>"
collection: portfolio
---

## Overview

This project was developed by **Phan Zong Xian (Tony)**, my FYP student, under my supervision at **Universiti Teknikal Malaysia Melaka (UTeM)**. The FYP is titled **"Learning to Look and Move: ChatGPT and the Perception Action Loop in Wheelchair Navigation"** — demonstrating how a Vision-Language Model (VLM) with function calling can enable autonomous wheelchair navigation through natural language commands.

## Technical Breakdown

### 🧠 Vision & Reasoning Layer
**OpenAI GPT-4v** serves as the "brain" — it processes camera input to understand the environment, and uses **function calling** to issue structured commands for wheelchair movement.

### 🔗 Middleware
A **Python function** bridges the VLM and hardware, interpreting GPT-4v's function call outputs and translating them into actionable movement commands.

### ⚙️ Execution
Commands are sent via **Serial communication to an Arduino**, which controls the wheelchair's drive motors — completing the perception-action loop.

## System Pipeline

```
Camera Input → GPT-4v (Vision + Reasoning) → Function Call → Python → Serial → Arduino → Wheelchair Motors
```

## Demonstrated Capabilities

From the demo video, the system successfully:

1. **Autonomous navigation to target** — wheelchair responds to a prompt to locate and navigate to an exit door
2. **Vision-guided movement** — GPT-4v processes real-time camera feed to detect and track the destination
3. **Function-calling control** — VLM selectively calls movement functions (forward, turn, stop) based on visual context
4. **End-to-end autonomy** — no manual remote control, pure AI-driven navigation

## Impact

This project demonstrates how **modern VLMs with function calling** can be applied to assistive robotics — enabling individuals with mobility impairments to control a wheelchair through natural language. The integration of perception (vision) and action (motor control) via a single AI model is a significant step toward intelligent, accessible assistive devices.

## Technologies Used

- **VLM:** OpenAI GPT-4v (Vision-Language Model with function calling)
- **Middleware:** Python function call handler
- **Hardware:** Arduino, DC motors, wheelchair chassis
- **Communication:** Serial (UART)
- **Platform:** UTeM

## Acknowledgements

Well done to **Phan Zong Xian (Tony)** for his excellent work on this project — a compelling demonstration of how cutting-edge AI can be applied in assistive technology for real-world impact.

*Posted: February 20, 2025*