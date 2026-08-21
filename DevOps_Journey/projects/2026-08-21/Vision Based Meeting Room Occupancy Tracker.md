# Vision-Based Meeting Room Occupancy Tracker

## Overview
A privacy-preserving computer vision system that counts occupants in meeting rooms using edge AI, without storing identifiable images.

## Architecture
```
┌─────────────────────────────────────────────────┐
│           Camera / Webcam Feed                  │
│                  (RTSP/HTTP)                    │
└──────────────────────┬──────────────────────────┘
                       │
          ┌────────────▼────────────┐
          │  Edge Inference         │
          │  (YOLOv8 on Jetson/PC)  │
          │  - Person detection     │
          │  - Counting             │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  Occupancy Counter      │
          │  (real-time count)      │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  Privacy Filter         │
          │  (blur faces, no save)  │
          └────────────┬────────────┘
                       │
          ┌────────────▼────────────┐
          │  Dashboard / Alerts     │
          │  - Current count        │
          │  - Historical trends    │
          │  - Overcrowding alert   │
          └─────────────────────────┘
```

## Workflow
1. Camera feed captured at edge device
2. YOLOv8 detects and counts people
3. Count published to MQTT/Redis
4. Dashboard shows real-time occupancy
5. Alert triggers if room exceeds capacity
6. No images stored — only counts and metadata

## Tools
- **YOLOv8** (Ultralytics) for person detection
- **OpenCV** for video processing
- **MQTT** or **Redis** for pub/sub
- **FastAPI** for REST API
- **Grafana** for visualization
- **Raspberry Pi 4** or **Jetson Nano** for edge

## Learning Goals
- Computer vision fundamentals
- Edge AI deployment
- Real-time streaming architectures
- Privacy-by-design principles

## Build Milestones
1. [ ] Person detection model setup
2. [ ] Video stream processing pipeline
3. [ ] Real-time counting logic
4. [ ] Privacy filter (face blur/no storage)
5. [ ] MQTT publishing
6. [ ] Dashboard with historical charts
7. [ ] Alert system (email/Telegram webhook)
