# TinyML Anomaly Detection for Homelab Sensors

**Date:** 2026-08-27
**Category:** AI/ML
**Tags:** tinyml, edge-ai, anomaly-detection, raspberry-pi, mqtt

---

## Overview

Deploy a micro-ML model on a Raspberry Pi or ESP32 to detect anomalies in homelab sensor data (temperature, power, network latency). The model runs entirely on-device, learning normal patterns and flagging deviations in real-time.

## Architecture

```
┌──────────────────────────────────────────────────────────┐
│                  Homelab Sensors                          │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌──────────────┐   │
│  │ Temp    │ │ Power   │ │ Network │ │ CPU/Memory   │   │
│  │ Sensor  │ │ Meter   │ │ Latency │ │ Monitor      │   │
│  └────┬────┘ └────┬────┘ └────┬────┘ └──────┬───────┘   │
│       │            │            │              │          │
│       └────────────┴────────────┴──────────────┘          │
│                            │ MQTT                         │
│                            ▼                              │
│              ┌───────────────────────┐                     │
│              │  Edge Device (Pi/ESP32)│                     │
│              │  ┌─────────────────┐   │                     │
│              │  │  TinyML Model   │   │                     │
│              │  │  (TensorFlow Lite│   │                     │
│              │  │   / ONNX Runtime)│   │                     │
│              │  └─────────────────┘   │                     │
│              │  ┌─────────────────┐   │                     │
│              │  │  Anomaly Alert  │   │                     │
│              │  │  (Local display │   │                     │
│              │  │   + Notification)│   │                     │
│              │  └─────────────────┘   │                     │
│              └───────────────────────┘                     │
│                            │                               │
│                            ▼ (occasional sync)             │
│              ┌───────────────────────┐                     │
│              │  Central Dashboard    │                     │
│              │  (Grafana/Prometheus) │                     │
│              └───────────────────────┘                     │
└──────────────────────────────────────────────────────────┘
```

## Sensor Data & Features

| Sensor | Raw Data | Features Extracted |
|--------|----------|-------------------|
| Temperature | °C readings | Rolling mean, std, rate of change |
| Power (kWh) | Wattage samples | Peak detection, usage patterns |
| Network latency | RTT ms | Jitter, packet loss ratio |
| CPU load | % utilization | Burst detection, sustained load |

## ML Model

### Approach: Isolation Forest or Autoencoder
- **Isolation Forest** — Good for high-dimensional anomaly detection, interpretable
- **Autoencoder** — Reconstructs normal patterns; high reconstruction error = anomaly
- **LSTM-based** — Captures temporal dependencies in sensor time series

### Model Size Target
- <5MB for microcontroller deployment
- <50MB for Raspberry Pi
- Quantized to INT8 for efficiency

### Training Pipeline
1. Collect 2–4 weeks of normal sensor data
2. Feature engineering (rolling windows, derivatives)
3. Train model on "normal" data only (unsupervised)
4. Validate on held-out normal period
5. Deploy quantized model to edge device

## Inference Pipeline (Edge)

```
MQTT Message → Buffer Window → Feature Extraction → Model Inference
                                                   │
                                           Score > threshold?
                                          /           \
                                        Yes            No
                                        │              │
                                    Alert!         Log normally
                                    (Local +      (Forward to
                                     Push)         central)
```

## Alert Channels
- Local buzzer/LED on device
- MQTT publish to homelab alarm topic
- Optional: Telegram/WhatsApp notification
- Grafana panel with anomaly timeline

## Tools

- **Python** (model training on laptop/server)
- **TensorFlow Lite** or **ONNX Runtime** (edge inference)
- **scikit-learn** (Isolation Forest baseline)
- **MQTT** (sensor data transport)
- **Raspberry Pi 4** or **ESP32-S3** (edge hardware)
- **Grafana** (visualization)

## Learning Goals

- Time series anomaly detection algorithms
- Model quantization (FP32 → INT8 → QAT)
- Edge deployment patterns
- MQTT messaging protocols
- Sensor data feature engineering

## Build Milestones

1. [ ] Set up sensor data collection (MQTT broker + simulated sensors)
2. [ ] Collect and label normal operating data (2+ weeks)
3. [ ] Train baseline Isolation Forest model
4. [ ] Implement feature extraction pipeline
5. [ ] Deploy model to Raspberry Pi with TFLite
6. [ ] Add real-time inference and alerting
7. [ ] Build Grafana dashboard with anomaly overlay
8. [ ] Add periodic model retraining from aggregated data

---
*Generated: 2026-08-27*
