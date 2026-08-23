# Vision-Based Meeting Room Occupancy Tracker

**Category:** AI/ML  
**Date:** 2026-08-23

---

## Overview

Build a computer vision system that counts people in meeting rooms using a camera feed. Detects occupancy levels, tracks duration of meetings, and provides analytics—all running locally on edge hardware (Raspberry Pi or Jetson Nano) with privacy-preserving on-device processing.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│      Vision-Based Occupancy Tracker                  │
│                                                     │
│  ┌──────────┐    ┌──────────────┐    ┌───────────┐  │
│  │ Camera   │───▶│  Frame       │───▶│  Person   │  │
│  │ (USB/IP) │    │  Capture     │    │  Detection│  │
│  └──────────┘    └──────────────┘    │  (YOLOv8) │  │
│                                      └─────┬─────┘  │
│                                            │         │
│                                    ┌───────▼───────┐  │
│                                    │  Counting &   │  │
│                                    │  Tracking     │  │
│                                    │  (DeepSORT)   │  │
│                                    └───────┬───────┘  │
│                                            │           │
│                                    ┌───────▼───────┐  │
│                                    │  Analytics    │  │
│                                    │  Engine       │  │
│                                    └───────┬───────┘  │
│                                            │           │
│                                    ┌───────▼───────┐  │
│                                    │  Dashboard    │  │
│                                    │  (Flask/     │  │
│                                    │   Grafana)    │  │
│                                    └──────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## Workflow

1. **Capture** video stream from IP camera or USB webcam
2. **Detect** people using YOLOv8 person model
3. **Track** individuals across frames with DeepSORT
4. **Count** unique occupants in defined zones
5. **Estimate** meeting start/end times
6. **Visualize** occupancy trends on dashboard
7. **Alert** when rooms exceed capacity

---

## Tools & Stack

| Component | Technology |
|-----------|-----------|
| Object Detection | YOLOv8 (Ultralytics) |
| Tracking | DeepSORT or ByteTrack |
| Edge Hardware | Raspberry Pi 4 / Jetson Nano |
| Backend | Python (FastAPI/Flask) |
| Database | TimescaleDB or InfluxDB |
| Dashboard | Grafana or Streamlit |
| Processing | OpenCV, PIL |

---

## Learning Goals

- Computer vision basics (object detection)
- Real-time video processing
- Multi-object tracking algorithms
- Edge deployment optimization
- Time-series data visualization
- Privacy-preserving AI design

---

## Build Milestones

| Phase | Deliverable | Timeline |
|-------|-------------|----------|
| 1. Setup | Camera feed + basic detection | Week 1 |
| 2. Model | YOLOv8 inference pipeline | Week 2 |
| 3. Tracking | Object ID assignment across frames | Week 3 |
| 4. Counting | Zone-based occupancy counting | Week 4 |
| 5. Analytics | Meeting duration tracking | Week 5 |
| 6. Dashboard | Real-time visualization | Week 6 |
| 7. Edge | Deploy to Raspberry Pi/Jetson | Week 7 |

---

## Reference Resources

- [YOLOv8 Documentation](https://docs.ultralytics.com/)
- [DeepSORT Paper](https://arxiv.org/abs/1703.07402)
- [OpenCV Python Tutorials](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)
- [Edge AI with Jetson](https://developer.nvidia.com/embedded/learn)
