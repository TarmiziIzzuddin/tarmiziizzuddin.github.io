---
title: "Natural Language Robot Control with Gemini API & ROS2-MCP"
excerpt: "Undergraduate AI students developed a system to command a Yahboom Micro-ROS Robot through natural language, bridging LLMs and physical hardware using Gemini API and ROS2-MCP servers.<br/><img src='/images/llm-robot-demo-thumbnail.jpg'>"
collection: portfolio
---

## Overview

This project was developed by Undergraduate AI students in the **Faculty of Artificial Intelligence and Cybersecurity (FAIX)**, UTeM, as part of their **BAXU 3923: Workshop 2** course. The team successfully built a system that commands a **Yahboom Micro-ROS Robot** through natural language, bridging the gap between Large Language Models and physical hardware.

🔗 **GitHub Repository:** [Project Source Code](https://github.com/TarmiziIzzuddin/llm-ros2-micro-robot) *(link to be confirmed)*

## Technical Breakdown

### 🧠 Reasoning Layer
**Gemini 1.5 Flash** serves as the primary "brain," interpreting complex human intent and translating it into actionable instructions for the robot.

### 🔗 Middleware
By implementing **Model Context Protocol (MCP)** servers, the team created a standardized bridge that allows the LLM to call specific robot services dynamically — enabling flexible and extensible command handling.

### ⚙️ Execution
Commands are processed via **ROS2 Humble** and executed on an **ESP32-based mobile platform** (Yahboom Micro-ROS Robot), ensuring low-latency communication between the AI and motor controllers.

## Demonstrated Capabilities

From the demo video, the system successfully performed:

1. **Natural Navigation** — "Robot, go to the bedroom" → robot navigates to exact destination
2. **Multi-Room Movement** — "Robot, go to the living room" → robot repositions accurately
3. **Visual Understanding** — "Robot, what do you see?" → camera captures scene and Gemini analyzes it (correctly identifies objects like a remote controller)
4. **Home Return** — "Robot, go back home" → robot returns to starting position

## Impact

This project is a fantastic example of how modern generative AI can be integrated into robust robotics frameworks. It demonstrates the practical application of LLMs beyond text generation — enabling physical-world interaction through natural language interfaces.

## Technologies Used

- **LLM:** Google Gemini 1.5 Flash
- **Protocol:** Model Context Protocol (MCP)
- **Framework:** ROS2 Humble
- **Hardware:** Yahboom Micro-ROS Robot (ESP32-based)
- **Platform:** FAIX, Universiti Teknikal Malaysia Melaka (UTeM)

## Acknowledgements

Special thanks to **Wei Hong Soon** and the dedicated team of undergraduate AI students for their excellent work on this technical milestone.

*Posted: May 2, 2026*
