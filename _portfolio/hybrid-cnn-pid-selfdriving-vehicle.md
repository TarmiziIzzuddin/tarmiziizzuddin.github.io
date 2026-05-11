---
title: "Hybrid CNN-PID Self-Driving Vehicle"
excerpt: "A regression-based PilotNet-style CNN predicts steering angles, stabilized by a tuned PID controller on an Arduino — bridging high-level vision and low-level control.<br/><img src='/images/hybrid-cnn-pid-selfdriving-thumbnail.jpg'>"
collection: portfolio
---

## Overview

This project was developed by **Muhammad Aiman Razali**, my FYP student, under my supervision at **Universiti Teknikal Malaysia Melaka (UTeM)**. The work implements a **Hybrid CNN-PID Approach for Steering Angle Prediction and Control** in a self-driving RC vehicle — successfully bridging the gap between high-level computer vision and low-level hardware control.

🔗 **GitHub Repository:** [CNN-self-driving-rc](https://github.com/DaisukeRich/CNN-self-driving-rc)

## Technical Breakdown

### 🧠 Vision & Inference
A **front-facing USB camera** feeds real-time RGB images to a **regression-based CNN (PilotNet-style architecture)** running on a laptop. The model predicts steering angles in normalized form (-1 to 1).

### 🔗 Communication
Normalized steering values are transmitted via **Serial communication** from the laptop to an **Arduino Uno**.

### ⚙️ Execution & Control
The Arduino runs a **tuned closed-loop PID controller** that manages the DC steering motor using **potentiometer feedback**, minimizing overshoot and ensuring smooth steering response.

## System Pipeline

```
Camera → CNN Model (Laptop) → Serial Communication → Arduino PID Controller → Steering Motor
```

## Demonstrated Capabilities

From the demo video, the system successfully:

1. **Real-time steering prediction** — CNN processes live camera feed at inference speed
2. **PID-stabilized control** — Three PID parameter sets were tested; Set 1 selected for best stability and lowest overshoot
3. **End-to-end autonomous driving** — Camera image directly determines steering, no manual intervention

## Technologies Used

- **Deep Learning:** PilotNet-style regression CNN (Keras/TensorFlow)
- **Control:** Closed-loop PID controller with potentiometer feedback
- **Hardware:** Arduino Uno, USB Camera, DC steering motor, motor driver
- **Communication:** Serial (UART) between laptop and Arduino
- **Platform:** UTeM

## Acknowledgements

Well done to **Muhammad Aiman Razali** for his excellent work on this hardware-software integration project, demonstrating how modern deep learning can be paired with classical control theory for real-world autonomous systems.

*Posted: February 5, 2026*