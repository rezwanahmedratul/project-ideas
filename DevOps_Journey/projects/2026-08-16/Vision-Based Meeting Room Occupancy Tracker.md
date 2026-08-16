# Vision-Based Meeting Room Occupancy Tracker

## Overview
Use computer vision (YOLOv8 or similar) to detect people in meeting rooms from webcam feeds, tracking occupancy without privacy invasion (no face recognition).

## Architecture
```
Webcam Feed
    ↓
Video Stream Handler
    ↓
Object Detection (YOLOv8)
    ↓
Occupancy Counter
    ↓
Dashboard (Flask/Streamlit)
    ↓
Alert (Telegram when full)
```

## Workflow
1. Set up Raspberry Pi or laptop with webcam
2. Install YOLOv8 and detect person class
3. Track unique individuals using simple ID assignment
4. Count occupancy in real-time
5. Build dashboard showing current/past occupancy
6. Add Telegram notification when room is full

## Tools
- Python (OpenCV, ultralytics)
- YOLOv8 (Ultralytics)
- Flask or Streamlit for dashboard
- Telegram Bot API for alerts
- Raspberry Pi (optional)

## Learning Goals
- Real-time object detection
- Video stream processing
- Privacy-preserving surveillance concepts
- Edge computing for AI

## Build Milestones
- [ ] Set up webcam feed
- [ ] Test YOLOv8 person detection
- [ ] Implement occupancy counting logic
- [ ] Build real-time dashboard
- [ ] Add Telegram notifications
- [ ] Optimize for edge deployment

## References
- https://docs.ultralytics.com/models/yolov8/
- https://github.com/ultralytics/ultralytics
- https://open-vision.github.io/
