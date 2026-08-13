# Autonomous Security Drone with ArduPilot & YOLOv4-Tiny

## Overview

This project presents the design and development of a low-cost autonomous security drone capable of autonomous waypoint navigation and real-time object detection. The system combines **ArduPilot**, **Raspberry Pi**, and **YOLOv4-Tiny** to detect people and vehicles while logging their GPS coordinates for later analysis.

The primary objective was to demonstrate that reliable autonomous drone solutions can be built using open-source software and affordable hardware.

<img width="957" height="674" alt="image" src="https://github.com/user-attachments/assets/6559d016-aba4-48a8-b4bd-cf735a25e48a" />

---

## Features

* Autonomous waypoint navigation using ArduPilot
* Automatic takeoff and landing
* GPS-based mission execution
* Real-time person and vehicle detection using YOLOv4-Tiny
* MAVLink communication between the flight controller and Raspberry Pi
* Local SQLite database for storing detected objects
* Flight telemetry monitoring
* Modular hardware and software architecture

---

## System Architecture

<img width="1346" height="595" alt="image" src="https://github.com/user-attachments/assets/6c041693-7b92-4ce7-8301-6412d8b2a1ab" />

```
Mission Planner
        │
        ▼
 ArduPilot Flight Controller
        │
   MAVLink (UART)
        │
        ▼
 Raspberry Pi 3B+
        │
 ┌───────────────┐
 │ YOLOv4-Tiny   │
 │ Object Detect │
 └───────────────┘
        │
        ▼
 SQLite Database
```

---

## Hardware

| Component          | Model                             |
| ------------------ | --------------------------------- |
| Frame              | TBS Source Two 5"                 |
| Flight Controller  | SpeedyBee F405                    |
| ESC                | SpeedyBee F405 V4 55A 4-in-1      |
| GPS                | Foxeer M10Q GPS + Compass         |
| Motors             | Velox 2207 1750KV                 |
| Companion Computer | Raspberry Pi 3B+                  |
| Camera             | RunCam Thumb                      |
| Receiver           | TBS Crossfire Nano RX             |
| Radio Controller   | TBS Tango 2                       |
| Battery            | 4S 18650 Li-Ion (Sony VTC Series) |

Several custom mounts (GPS, Raspberry Pi, and camera) were designed and manufactured using 3D printing.

<img width="1322" height="761" alt="image" src="https://github.com/user-attachments/assets/9e0ecfe6-6771-4d6d-a92b-7919f12a35d1" />

---

## Software Stack

### Flight Controller

* ArduPilot
* Mission Planner
* MAVLink communication
* Waypoint navigation
* Automatic takeoff and landing
* Telemetry monitoring

### Companion Computer

* Python
* OpenCV
* YOLOv4-Tiny (ONNX)
* SQLite
* MAVLink (pymavlink)

---

## Object Detection

<img width="900" height="556" alt="image" src="https://github.com/user-attachments/assets/272e761d-f1d9-43ab-9cb4-5325b7adcdba" />


The Raspberry Pi performs lightweight object detection using **YOLOv4-Tiny**, which was selected because it provides a good balance between computational efficiency and detection performance on embedded hardware.

Each detected object generates an event containing:

* Object class (Person / Car)
* Timestamp
* GPS latitude
* GPS longitude

These events are stored locally in an SQLite database.

---

## Flight Test

Test video: https://drive.google.com/file/d/1HQq9gnAjp_7WJZNVXiwGOaoA7TjnvCEy/view?usp=sharing

The autonomous drone successfully completed waypoint missions using ArduPilot.

The integrated object detection pipeline correctly identified people and vehicles, while GPS coordinates and timestamps were recorded into the onboard database.

The project demonstrates the feasibility of combining autonomous flight with onboard computer vision using inexpensive hardware.

---

## Future Work

* Perform object detection during autonomous flight
* Implement object tracking
* Autonomous target following
* Obstacle avoidance
* Live telemetry dashboard
* Remote database synchronization

---

## Technologies

* ArduPilot
* MAVLink
* Python
* OpenCV
* YOLOv4-Tiny
* ONNX
* SQLite
* Raspberry Pi
* Mission Planner

---


## Authors

**Ahmet Yüksel Erkurt**

**Yankı Bora Ayman**
