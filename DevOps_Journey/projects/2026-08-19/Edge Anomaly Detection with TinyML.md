# Edge Anomaly Detection with TinyML

**Category:** AI / ML  
**Date:** 2026-08-19  
**Difficulty:** Advanced  

## Overview
Train a **tiny machine-learning model** to detect anomalies in time-series sensor data (CPU temp, network traffic, vibration) and deploy it to an edge device (Raspberry Pi + NPU HAT, or an ESP32). The model runs on-device, flagging abnormal patterns in real time without sending raw data to the cloud. Directly applies the 2026 Edge AI trend from today's research report.

## Architecture / Structure
```
edge-anomaly/
├── data/                 # sample sensor CSVs
├── train.py              # autoencoder / IsolationForest training
├── quantize.py           # convert to TFLite / INT8
├── device/
│   ├── main.py           # inference loop on Pi
│   └── requirements.txt
├── eval.py              # precision/recall on labeled anomalies
└── README.md
```

## Workflow
1. Collect or synthesize normal sensor readings.
2. Train an autoencoder; anomaly = high reconstruction error.
3. Quantize the model to TFLite INT8 for the edge.
4. Deploy to the device; it scores live readings and raises an alert on threshold breach.
5. Evaluate on labeled anomaly windows; tune threshold.

## Tools
- Python, scikit-learn / PyTorch (autoencoder)
- TensorFlow Lite / Edge Impulse for deployment
- Raspberry Pi (or ESP32), optional NPU HAT
- Prometheus (optional) to graph scores

## Learning Goals
- Unsupervised anomaly detection (autoencoders, Isolation Forest).
- Model quantization and edge deployment.
- Real-time inference on constrained hardware.
- Balancing false positives vs. detection rate.

## Build Milestones
1. Generate/collect a sensor dataset and train a baseline autoencoder.
2. Define anomaly scoring + threshold; evaluate on synthetic faults.
3. Convert the model to TFLite INT8 and validate accuracy loss.
4. Run inference on a Raspberry Pi over a live sensor feed.
5. Add alerting (local LED / notifier service) and a small dashboard.
