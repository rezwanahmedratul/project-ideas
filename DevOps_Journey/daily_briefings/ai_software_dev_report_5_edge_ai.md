# AI Software Dev Report #5 — Edge AI Deployment with Tinkerbell and K3s

**Date:** 2026-08-25
**Category:** AI + DevOps + Edge Computing

---

## Overview

Deploying AI inference workloads to the edge — cameras, IoT gateways, autonomous vehicles — requires lightweight, resilient infrastructure. This report covers how bare-metal provisioning (Tinkerbell), lightweight K8s (K3s), and AI model optimization converge to make edge AI practical.

---

## Key Advancements

### 1. Tinkerbell for Bare-Metal Edge Provisioning

Tinkerbell ([tinkerbell.org](https://tinkerbell.org/)) provides CI/CD-style provisioning for bare-metal servers — critical for edge AI where GPUs must be physically present. Unlike cloud VMs, you get direct hardware access, no virtualization overhead, and predictable latency.

```bash
# Tinkerbell workflow for edge node
tbcli workflow run gpu-inference.yaml \
  --host <edge-node-ip> \
  --image nvidia-jetson:latest
```

- **Reference:** [Tinkerbell Documentation](https://docs.tinkerbell.org/)
- **Reference:** [Tinkerbell GitHub](https://github.com/tinkerbell/tink)

### 2. K3s for Lightweight Cluster Management

K3s (lightweight Kubernetes from Rancher) runs on resources as small as a Raspberry Pi 4. For edge AI, this means you can run a full Kubernetes control plane on the same hardware hosting your inference models. Combined with [k3s-airgapped](https://docs.k3s.io/installation/air-gap) for offline deployments.

- **Reference:** [K3s Official Docs](https://docs.k3s.io/)
- **Reference:** [K3s Air-Gapped Install](https://docs.k3s.io/installation/air-gap)

### 3. NVIDIA Triton + Edge Deployment

NVIDIA Triton Inference Server supports deploying optimized models (TensorRT, ONNX, TorchScript) to edge GPU nodes. Paired with K3s, you get auto-scaling, health checks, and canary deployments for model updates at the edge.

- **Reference:** [NVIDIA Triton Server Docs](https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/index.html)
- **Reference:** [Triton on Kubernetes Guide](https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/docs/frameworks.html)

### 4. Model Quantization for Edge

Edge devices have limited compute. AI-assisted quantization tools auto-optimize models:
- **[TensorRT](https://developer.nvidia.com/tensorrt)** — NVIDIA's optimizer for GPU inference
- **[ONNX Runtime](https://onnxruntime.ai/)** — cross-platform with auto-quantization
- **[GGUF/GGML](https://github.com/ggerganov/ggml)** — for CPU-only edge (RPi, Intel NUC)
- **[MLC LLM](https://llm.mlc.ai/)** — compile LLMs to run on mobile/embedded GPUs

- **Reference:** [MLC LLM Documentation](https://llm.mlc.ai/docs/)
- **Reference:** [GGUF Format Guide](https://github.com/ggerganov/llama.cpp/blob/master/models/README.md)

### 5. Edge AI MLOps with KServe + Tinkerbell

Combining Tinkerbell's bare-metal management with KServe's model serving creates a full edge MLOps stack: provision → serve → monitor → update, all on physical edge hardware without cloud dependency.

- **Reference:** [KServe on Edge](https://kserve.github.io/website/latest/setup//)
- **Reference:** [Edge AI with K8s (AWS Paper)](https://aws.amazon.com/blogs/containers/running-machine-learning-inference-at-the-edge-with-amazon-eks/)

---

## Why It Matters

Edge AI eliminates:
- Cloud latency (critical for real-time inference)
- Bandwidth costs (process locally, send only results)
- Privacy concerns (data never leaves the device)
- Offline capability (works without internet)

---

## Build Exercise

1. Set up a Tinkerbell stack on a local bare-metal server
2. Provision 2 edge nodes (RPis or Intel NUCs) with K3s
3. Deploy an ONNX model via KServe on the K3s cluster
4. Add TensorRT optimization for GPU-accelerated inference
5. Create an automated model update pipeline (new model → Tinkerbell provision → KServe rollout)

---

*References:*
- https://docs.tinkerbell.org/
- https://github.com/tinkerbell/tink
- https://docs.k3s.io/
- https://docs.k3s.io/installation/air-gap
- https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/index.html
- https://onnxruntime.ai/
- https://github.com/ggerganov/llama.cpp
- https://llm.mlc.ai/docs/
- https://kserve.github.io/website/latest/setup/
