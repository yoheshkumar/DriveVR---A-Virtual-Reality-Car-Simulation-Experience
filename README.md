## DriveVR: A Controller-Less Virtual Reality Car Simulator

### 📝 Overview

DriveVR is a fully immersive virtual reality driving simulator developed for the Oculus Quest 2. Unlike traditional VR driving games that rely on physical controllers or joysticks, DriveVR is controlled entirely through intuitive hand gestures.

Users can grip a virtual steering wheel in mid-air to steer and use a natural pinch gesture to control acceleration and braking. The project features a realistic physics engine built from scratch using Unity's WheelCollider system, ensuring the car feels grounded and responsive.

### ✨ Key Features

🚫 Controller-Free Input: Uses the Oculus Hand Tracking SDK to map real-time hand movements to vehicle controls.

Right Hand: Pinch to Accelerate/Brake (Analog control based on pinch strength).

Left Hand: Rotate wrist to Steer (Calculates roll angle relative to the horizon).

🏎️ Realistic Physics Engine: Custom-tuned suspension, friction curves, and torque settings to solve common VR physics issues like jitter and ground clipping.

🅿️ Smart Gameplay Loop: Features a complete game cycle with a Start Menu and a "Smart Parking" objective that uses geometric bounds checking to verify precise parking.

🛠️ Optimized for Quest 2: Built with ARM64 architecture and IL2CPP scripting backend for high-performance, standalone VR.

### 🎮 How to Play

<img width="683" height="254" alt="image" src="https://github.com/user-attachments/assets/5fa51e21-7449-43bf-bb6f-05b108f6a433" />

### 📸 Screenshots

#### The Cockpit View

<img width="650" height="296" alt="image" src="https://github.com/user-attachments/assets/c29575f6-98a1-42d0-a965-be872be5f60e" />

#### Hand Tracking in Action

<img width="650" height="296" alt="image" src="https://github.com/user-attachments/assets/15f4dafc-bdb3-4d05-9446-2f01208cad9c" />

#### Task Completion

<img width="650" height="296" alt="image" src="https://github.com/user-attachments/assets/5b782a4b-fbe6-4acb-8950-b6c7cab0e2a0" />

### 🛠️ Technical Implementation

#### Architecture

The project follows a decoupled "Engine vs. Driver" architecture to allow for easy debugging:

CarController.cs: The physics core. Handles torque, steering angle, and visual wheel synchronization. It is agnostic to the input source.

HandInputController.cs: The VR driver. Reads Oculus SDK data and translates it into normalized values (-1 to 1) for the engine.

DesktopCarInput.cs: A debug driver. Allows the car physics to be tested on a PC using keyboard arrow keys.

### Challenges Solved

Physics Jitter: Solved by tuning the WheelCollider dampers to 50,000 to counteract the Rigidbody mass.

Ghost Collisions: Fixed the "car falling through floor" bug by removing conflicting Mesh Colliders from the visual car model.

Android Build Crash: Resolved a startup crash on Quest 2 by enforcing ARM64 architecture and removing the Vulkan graphics API.

Input Calibration: Implemented a self-calibrating steering system that sets the initial hand angle as "zero" to prevent drift and ensure comfortable steering.

### 👨‍💻 Developed Using

Engine: Unity 2022.3 (LTS) / Unity 6

Platform: Oculus Quest 2 (Android)

SDK: Meta XR All-in-One SDK / Oculus Integration

### Thank you for checking out DriveVR!

