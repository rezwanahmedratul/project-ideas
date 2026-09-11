# TensorFlow Lite 移动端图像分类 App

## 概述
训练一个轻量级图像分类模型并使用 TensorFlow Lite 部署到 Android/iOS 设备。

## 架构/结构
```
┌─────────────────────────────────────────────────────────┐
│               Mobile Image Classification                │
├──────────────┬──────────────┬──────────────┬────────────┤
│  训练阶段    │  优化阶段    │  部署阶段    │  推理阶段  │
├──────────────┼──────────────┼──────────────┼────────────┤
│ • 数据集准备 │ • Quantization│ • TFLite    │ • 摄像头   │
│ • Model 训练 │ • Pruning    │   Conversion│   输入     │
│ • 验证调优   │ • Format转换 │ • App 打包  │ • 模型推理 │
│              │              │ • 分发测试   │ • 结果展示 │
└──────────────┴──────────────┴──────────────┴────────────┘
```

## 工作流
1. 收集并标注图像数据集
2. 使用 TensorFlow/Keras 训练分类模型
3. 应用量化压缩至 TFLite 格式
4. 集成到 Flutter/React Native App
5. 部署到真机测试

## 工具
- Python + TensorFlow/Keras
- TensorFlow Lite Converter
- Flutter / React Native
- LabelImg（数据标注）

## 学习目标
- 深度学习模型训练
- 模型压缩与优化
- 移动端 ML 部署
- Flutter 跨平台开发

## 构建里程碑
- [ ] 周 1：数据集准备与标注
- [ ] 周 2：模型训练与调优
- [ ] 周 3：TFLite 转换与量化
- [ ] 周 4：移动端 App 开发
- [ ] 周 5：性能测试与发布
