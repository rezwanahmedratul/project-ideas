# TinyML Anomaly Detector for Homelab Sensors

**Category:** AI ML  
**Date:** 2026-08-18  
Difficulty: Intermediate

---

## Overview

Train a lightweight anomaly detection model (Isolation Forest or autoencoder) on homelab sensor data (temperature, power draw, network traffic) and deploy it on a Raspberry Pi or small edge device. Alerts when metrics deviate from learned normal behavior — useful for cooling failures or crypto-miner detection.

## Architecture / Structure

```
edge-anomaly/
├── training/
│   ├── collect.py         # Pull Prometheus/InfluxDB history
│   ├── train.py           # IsolationForest / autoencoder
│   └── export.py          # ONNX or TFLite export
├── edge/
│   ├── main.py            # Inference loop
│   ├── ingest.py          # MQTT/serial sensor reader
│   └── alert.py           # Webhook/Telegram
├── models/
│   └── anomaly.onnx
└── docker/
    └── Dockerfile.arm32    # Multi-arch build
```

## Workflow

1. **Collect** 2 weeks of normal sensor data from Prometheus
2. **Train** unsupervised model (no labels needed)
3. **Export** to ONNX/TFLite for edge
4. **Edge** device reads live sensors via MQTT
5. **Infer** → if anomaly score > threshold → alert
6. **Retrain** monthly with new normal data

## Tools

- **Training:** Python, scikit-learn, PyTorch (autoencoder)
- **Export:** ONNX, TensorFlow Lite
- **Edge:** Raspberry Pi (arm32/64), Python or C++
- **Data:** Prometheus, InfluxDB, MQTT (mosquitto)
- **Alerts:** Telegram Bot, webhook

## Learning Goals

- Unsupervised anomaly detection (Isolation Forest, autoencoders)
- Model quantization and edge deployment
- Time-series feature engineering
- MQTT IoT protocols

## Build Milestones

| Milestone | Deliverable | Est. Time |
|-----------|-------------|-----------|
| M1 | Data collection pipeline | 1 day |
| M2 | Train IsolationForest baseline | 1 day |
| M3 | Autoencoder variant + compare | 1.5 days |
| M4 | ONNX export + edge inference | 1.5 days |
| M5 | MQTT ingest + Telegram alerts | 1 day |

---

**Tags:** #tinyml #anomaly-detection #edge #raspberry-pi #iot #prometheus
