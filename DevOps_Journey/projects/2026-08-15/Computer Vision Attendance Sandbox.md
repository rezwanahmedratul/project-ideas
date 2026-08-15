# Computer Vision Attendance Sandbox

## Overview
A computer vision application for face recognition-based attendance tracking with privacy-focused local processing.

## Architecture
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Camera    │     │  CV Engine  │     │   Database  │
│   Capture   │◄───▶│ (OpenCV)    │◄───▶│  (SQLite)   │
└─────────────┘     └─────────────┘     └─────────────┘
        │                │
   ┌─────────┐     ┌───────────┐
   │  Face   │     │  Recognition│
   │  Detection│   │  Model     │
   └─────────┘     └───────────┘
```

## Workflow
1. **Capture**: Get frame from camera or video stream
2. **Detect**: Find faces using Haar cascades or MTCNN
3. **Recognize**: Match faces against enrolled database
4. **Record**: Log attendance with timestamp
5. **Report**: Generate attendance reports

## Tools
- Python with OpenCV
- face_recognition library or InsightFace
- SQLite for storage
- Flask or FastAPI for API
- Streamlit for dashboard

## Learning Goals
- Learn computer vision fundamentals
- Practice face recognition systems
- Understand privacy considerations
- Build real-time processing pipelines

## Build Milestones
1. **M1**: Basic face detection and recognition
2. **M2**: Add person enrollment system
3. **M3**: Implement attendance logging
4. **M4**: Create web dashboard for reports
5. **M5**: Add multi-camera support
6. **M6**: Implement privacy features (on-device processing)
