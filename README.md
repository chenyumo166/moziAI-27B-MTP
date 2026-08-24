---
language:
- zh
- en
license: other
tags:
- gguf
- Dense
- financial-llm
- MoziSmartBit
- qwen3.8
- MoziAI
- 工具调用
- 视觉
- MTP
库名称: llama-cpp
pipeline_tag: 文本生成
---

# MoziAI-27B-3.8 - 免费本地部署的小而强大的多模态AI

[English](V3.8/README.en.md) | [简体中文](V3.8/README.zh.md) | [繁體中文](V3.8/README.zh-hant.md) | [日本語](V3.8/README.ja.md) | [한국어](V3.8/README.ko.md) | [हिन्दी](V3.8/README.hi.md) | [Deutsch](V3.8/README.de.md) | [Français](V3.8/README.fr.md) | [Nederlands](V3.8/README.nl.md) | [Italiano](V3.8/README.it.md) | [Русский](V3.8/README.ru.md)

## 模型概述

MoziAI-27B-3.8 是由中国金融KOL陈宇墨团队开发的一款本地开源金融AI多模态大语言模型（支持视觉和工具调用）。moziAI-27B-3.8 基于开源基础模型Qwen3.8-27B（密集27B架构，MIT许可），整合了陈雨墨团队自主研发的：(金融数据 + 金融领域能力 + 训练方法 + 七维思维框架 + Agent LOOP机制 + 混合量化算法MoziSmartBit)。

通过自主研发的MoziSmartBit智能量化技术，270亿参数的密集模型被压缩至约13.7 GB，比常规的Q4_K_M量化模型（约17 GB）小3.3 GB（约20%）；在精度与大小之间实现了最佳平衡，提供**~99%的FP16精度质量**。

除了保留通用人工智能能力外，该模型还增强了：金融垂直领域应用、金融问答、量化编程、工具调用和通用编程，以及模型的七维思维能力、LOOP机制和对各种智能体平台的兼容性。

## 快速开始

请查看 [详细文档](V3.8/README.zh.md) 了解完整功能、硬件要求和部署指南。

## 下载

| 文件 | 大小 | 说明 |
|------|------|------|
| moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf | ~13.7 GB | 主模型（Q4Q3-hybrid 混合量化） |
| moziAI-27B-MTP-V3.8-mmproj-F16.gguf | ~885 MB | 视觉投影器 |
| chat-template-moziai-27B-V3.8.jinja | ~8.7 KB | 聊天模板 |

## 许可证

本模型采用 **Custom Restrictive License**，详见 [LICENSE](LICENSE)。

## 联系方式

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **E-mail**: 263515@qq.com

---

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
