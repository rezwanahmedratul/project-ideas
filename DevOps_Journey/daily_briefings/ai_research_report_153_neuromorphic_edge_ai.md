# AI Research Report #153 — Neuromorphic Computing & Spiking Neural Networks for Edge AI

## Overview
As AI workloads migrate from cloud data centers to edge devices, traditional von Neumann architectures face fundamental limits in energy efficiency and latency. Neuromorphic computing — hardware inspired by biological neural structures — offers a radical alternative. Combined with spiking neural networks (SNNs), neuromorphic chips enable always-on AI with microwatt power consumption, opening applications from implantable medical devices to autonomous sensor networks. This report surveys the neuromorphic landscape of 2025.

## Why Neuromorphic? The Efficiency Imperative

### The Power Problem
| Architecture | TOPS/Watt | Example Chip |
|-------------|-----------|--------------|
| GPU (NVIDIA H100) | ~0.5–1 | Data center inference |
| TPU v5 | ~5–10 | Cloud deployment |
| Edge TPU | ~4 | Mobile inference |
| **Neuromorphic (TrueNorth)** | **~70,000** | Event-based processing |
| **Neuromorphic (Loihi 2)** | **~15,000** | Research + edge |
| **Photonic Neuromorphic** | **~100,000+** | Emerging 2025 |

This 4–5 order of magnitude difference makes neuromorphic computing essential for:
- Implantable medical devices (battery lifetime measured in years)
- IoT sensor networks (millions of devices, minimal maintenance)
- Real-time robotics (sub-millisecond reaction times)
- Satellite/aerospace (power constraints, radiation hardening)

## Spiking Neural Networks: The Software Side

### From Rate Coding to Temporal Coding
Traditional ANNs use continuous activation values; SNNs communicate via discrete spikes:

```
Rate-based (ANN):     Activation = 0.73 → Continuous value
                      Weight = 0.45

Spiking (SNN):        Spike at t=10ms → Information in timing
                      Refractory period → Temporal dynamics
```

**Key advantages:**
- **Event-driven computation**: Process only when spikes occur (sparse activity)
- **Temporal encoding**: Precise spike timing carries information
- **Online learning**: Hebbian and STDP rules enable continual adaptation
- **Hardware compatibility**: Direct mapping to membrane potential dynamics

### Learning Algorithms for SNNs
| Method | Accuracy | Training Time | Hardware Support |
|--------|----------|---------------|------------------|
| **Surrogate gradient** | High (~99% ANN parity) | Moderate | Good |
| **STDP** | Moderate | Fast | Native |
| **Reinforcement learning** | Variable | Slow | Good |
| **Temporal backprop** | Emerging | Slow | Limited |

## Hardware Platforms (2025 Landscape)

### Intel Loihi 2
- **Architecture**: 1M neurons, 128M synapses on-chip
- **Features**: Multi-chip interconnect, event-based communication
- **Use cases**: Neuroscience research, edge AI prototyping
- **Access**: Cloud API via Hugging Face and direct lab access

### IBM TrueNorth successor
- Building on 1M neuron foundation with improved programmability
- Focus on commercial applications and embedded deployments

### SpiNNaker 2 (University of Manchester)
- **Scale**: Up to 16M neurons across chips
- **Approach**: ARM cores with event-driven routing fabric
- **Strength**: Large-scale brain simulation, neuroscience

### Photonic Neuromorphic Chips (2025 breakthroughs)
- **Speed**: Optical computing at 100+ Gbps per chip
- **Energy**: Photon-based operations consume femtojoules
- **Companies**: Lightmatter, SiPhotonics, Luminous Computing

### Academic/Startup Ecosystem
- **SynSense / Eyeriss**: Energy-efficient vision processing
- **Berkeley Brain**: Spiking hardware for edge
- **Square Knot Computing**: Neuromorphic chips for autonomous vehicles
- **Mythic Memory**: Analog compute-in-memory for SNNs

## Applications Driving Adoption

### Always-On Sensing
```
Sensor → Neuromorphic chip → Local inference → Only wake host for anomalies
```

Examples:
- Wearable health monitors detecting arrhythmias in real-time
- Industrial vibration analysis predicting equipment failure
- Wildlife monitoring with months-long battery life

### Brain-Computer Interfaces
- Real-time decoding of neural signals for prosthetic control
- Closed-loop stimulation for epilepsy/seizure prediction
- Bidirectional communication with minimal latency

### Autonomous Systems
- Event cameras (neuromorphic vision) provide:
  - Microsecond temporal resolution
  - Gigapixel dynamic range
  - Low bandwidth (only changed pixels transmitted)

Used in: drones, robotics, automotive perception

## Software Toolchains

| Framework | Language | Status | Best For |
|-----------|----------|--------|----------|
| **NEST** | Python/C++ | Mature | Large-scale simulations |
| **Brian2** | Python | Active | Research prototyping |
| **Lava (Intel)** | C++/Python | Production | Loihi programming |
| **Rockpool** | Python/PyTorch | Growing | Hybrid ANN-SNN |
| **Snntorch** | Python/PyTorch | Active | Deep SNN training |

## Challenges & Open Problems

1. **Programming complexity**: SNNs require different mental models than ANNs
2. **Training scalability**: Limited support for large-scale supervised training
3. **Hardware availability**: Neuromorphic chips not yet mass-produced
4. **Ecosystem maturity**: Smaller developer community vs. CUDA/PyTorch
5. **Verification difficulties**: Timing-dependent behavior harder to debug

## Reference Links
- [Intel Loihi 2 Specifications](https://www.intel.com/content/www/us/en/research/loihii2.html)
- [SpiNNaker 2 Project](https://www.spiNNaker.org/)
- [Spiking Neural Network Survey (Nature Reviews, 2025)](https://www.nature.com/natrevneurisci/)
- [Photonic Neuromorphic Computing Landscape](https://www.patsnap.com/resources/blog/articles/photonic-neuromorphic-computing-landscape-2026)
- [Lava Programming Framework](https://lava-nn.readthedocs.io/)

---
*Generated: 2026-09-18 | Source: AI overnight research engine*
