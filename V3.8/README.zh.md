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
- tool-calling
- vision
- MTP
library_name: llama-cpp
pipeline_tag: text-generation
---

# MoziAI-27B-3.8 — 可免费本地部署的小而强的多模态 AI 模型

[English](README.en.md) | 简体中文 | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

**发布日期：2026-08-30** · **版本：V3.8**

---

## 📑 目录

- [1. 模型概述](#1-模型概述)
- [2. 模型特色](#2-模型特色) — 动态七维思考 / LOOP / MoziSmartBit / 金融聚焦
- [3. 版本升级说明](#3-版本升级说明)
- [4. 核心能力](#4-核心能力)
- [5. 技术规格](#5-技术规格)
- [6. ⚡ 快速开始](#6--快速开始3-个文件--100-激活最佳推理能力) — **三件套下载**
- [7. 模型下载](#7-模型下载)
- [8. 启动命令](#8-启动命令)
- [9. 推荐推理参数](#9-推荐推理参数)
- [10. 量化格式对比](#10-量化格式对比)
- [11. MTP 推测解码](#11-mtp-推测解码重要加速特性)
- [12. 显存配置](#12-显存配置推荐)
- [13. 部署方式](#13-部署方式)
- [14. 基准评测](#14-基准评测)
- [15. 许可证](#15-许可证)
- [16. 联系方式](#16-联系方式)

---

## 1. 模型概述

MoziAI-27B-3.8 是由中国财经大V陈雨墨团队开发的本地开源多模态AI大模型，基于开源底座 **Qwen3.8-27B**（Dense 27B 架构，MIT 许可），结合团队自主研发的金融数据 + 金融领域能力 + 动态七维思考体系 + 智能体LOOP反思迭代机制 + MoziSmartBit混合量化算法开发而成。本模型降低个人与企业的本地部署门槛，授权**免费商用**，在消费级显卡上即可本地部署，节约大量云端 token 成本，实现 7×24 小时 token 自由并确保本地数据隐私与安全。

---

## 2. 模型特色

### 🧠 动态七维思考体系

MoziAI 自研的核心推理框架。面对任何任务，模型先输出 **moziAI-Think** 标记，按任务复杂度动态展开结构化思考：

| 级别 | 适用场景 | 典型任务 | 展开维度 |
| --- | --- | --- | --- |
| **Level 0** | 简单问答 | 术语解释、事实查询、翻译、摘要 | ①理解任务 ⑤资源需求（两维速答） |
| **Level 1** | 分析诊断 | 市场调研、文案编写、数据分析、研报解读、策略评估 | ①②③⑤⑥ 五维评估 |
| **Level 2** | 复杂开发/策略 | 代码开发、架构设计、量化策略开发、多步工作流、系统设计 | ①②③④⑤⑥⑦ 全七维深度推演 |

> 七维：①理解任务 ②复杂度评估 ③依赖关系 ④风险评估 ⑤资源需求 ⑥验收标准 ⑦执行策略

### 🔄 智能体 LOOP 迭代机制

复杂任务自动进入 **moziAI-Loop** 迭代模式：**第 1 轮执行+评估 → 第 2 轮调整+验证**，确保输出经过自我校验后才给出最终答案。模型像资深工程师一样「拆解问题 → 评估方案 → 执行 → 反思 → 优化」，显著提升复杂任务的准确性和可执行性。简单问答和任务则自动关闭 Loop。

### 📦 MoziSmartBit 智能量化

自研分层智能量化，270 亿参数 Dense 模型压缩至约 **13.7 GB**，比常规 Q4_K_M（~17 GB）小约 3.3 GB（~20%），保持 FP16 **~99%** 精度。传统量化对所有层使用统一精度，MoziSmartBit 针对 Dense 模型结构特点采用智能差异化策略，精度优于 Q4_K_M。

### 💰 金融垂直领域聚焦

针对金融问答、量化编程和工具调用的深度优化。金融领域对模型幻觉容忍度极低，MoziAI 在该领域的表现显著优于同等体积的通用模型。

### 🌐 其他特性

- **多语言支持**：201 种语言和方言，中文能力特别优化
- **通用编程**：全栈开发、代码调试、架构设计，覆盖 Python/JS/TS/Go/Rust
- **文章写作**：研报、分析文章、技术文档、创意内容等多体裁高质量写作
- **视觉理解**：多模态视觉，支持本地截图理解图片内容
- **多框架支持**：llama.cpp / Ollama / LM Studio / Jan
- **多 Agent支持**：OpenClaw / Hermes / Cursor / Claude Code / Codex 等，原生工具调用与多轮任务编排

---

## 3. 版本升级说明

本次版本升级主要强化了：moziAI 自研的动态七维思考 + LOOP 迭代的推理模式，使其更加智能识别任务复杂度，复杂任务的完成率更高，提高"先想后做"的能力。

moziAI 会保持活跃的版本升级迭代更新频率，确保紧随未来人工智能的发展，并且不断通过自研技术，让本地 AI 模型可轻量化部署，能力越来越强。

---

## 4. 核心能力

| 能力领域 | 说明 |
| --- | --- |
| 市场分析 | 宏观/微观经济解读、A股/港股/美股/商品/加密货币行情与逻辑梳理 |
| 财务与研报 | 财报关键指标解读、研报摘要提取、估值与盈利预测辅助 |
| 风控与合规 | 产品风险评估、投资建议合规提示、金融监管政策解读 |
| 量化与策略 | 量化策略思路设计、金字塔（Pyramid/PEL）量化、回测逻辑、因子构建与工具调用 |
| 工具调用 | 可接入实时行情、数据库、研报检索等金融数据源 |

---

## 5. 技术规格

| 项目 | 参数 |
| --- | --- |
| 底座模型 | Qwen3.8-27B（Dense 架构，混合注意力 16 full + 48 linear，MIT 许可证） |
| 参数规模 | 270 亿（27B）Dense 架构 |
| 量化方式 | 自研 MoziSmartBit 智能量化 + GGUF 标准格式 |
| 上下文长度 | 128K（262,144 tokens） |
| 模型体积 | ~13.7 GB |
| 最低显存 | **16GB+** 可部署（CPU 卸载）；**20GB+** 流畅长上下文；**24GB+** 完整 128K + 视觉 |
| 推理框架 | llama.cpp / Ollama / LM Studio / Jan |
| 推理速度 | MTP 推测解码下：R9700 达 70+ tok/s，MAX+395 核显达 50+ tok/s，GPU 达 35+ tok/s |
| 开发团队 | 陈雨墨团队 |

---

## 6. ⚡ 快速开始（3 个文件 = 100% 激活最佳推理能力）

> ⚠️ **核心提示**：MoziAI 的最佳推理能力需要**同时下载 3 个文件**——主模型、视觉投影、聊天模板。缺少任何一个都会损失对应能力。

### 6.1 下载模型文件

在 HuggingFace / ModelScope 下载 **V3.8 目录下的所有文件**到本地同一目录：

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf   ← 主模型（必选，13.7 GB）
├── moziAI-27B-3.8-mmproj-F16.gguf            ← 视觉投影（必选，927 MB）
└── chat-template-moziai-27B-v38.jinja         ← 聊天模板（必选，含七维思考+Loop指令）
```

| 文件 | 大小 | 必要性 | 作用 |
| --- | --- | --- | --- |
| 主模型 `.gguf` | ~13.7 GB | **必选** | 模型权重，核心推理能力 |
| 视觉投影 `mmproj` | ~927 MB | **必选** | 多模态视觉理解，不载入则丧失图像能力 |
| 聊天模板 `.jinja` | 微量 | **必选** | 注入 MoziAI 身份 + 七维思考 + LOOP 机制指令 |

### 6.2 启动并使用

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

浏览器打开 `http://localhost:8080` 即可开始对话。完整推荐参数见第 9 节。

---

## 7. 模型下载

| 平台 | 地址 |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main/V3.8) |
| ModelScope（魔搭） | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master/V3.8) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master/V3.8) |

> 💡 **LM Studio 用户**：在 [LM Studio](https://lmstudio.ai) 中搜索 `moziAI` 一键下载，无需手动下载文件。

---

## 8. 启动命令

### 最简启动（含三件套）

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### 完整推荐启动

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 -t 28 \
  --batch-size 1024 --ubatch-size 128 \
  --flash-attn auto \
  --cache-type-k q4_0 --cache-type-v q4_0 --kv-unified \
  --poll 0 \
  --reasoning auto --reasoning-budget 1024 --reasoning-format deepseek-legacy \
  --spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75 \
  --host 0.0.0.0 --port 8080 \
  --temp 0.6 --top-p 0.95 --top-k 20
```

> 💡 关闭 MTP：删除 `--spec-type draft-mtp` 及相关参数，速度降低约 30-50%，显存占用更小。

---

## 9. 推荐推理参数

基于 llama.cpp 官方推荐参数与本地实测优化（AMD Radeon AI PRO R9700 32GB）：

| 参数 | 通用聊天 | 编码/Agent | 说明 |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | 平衡创意与准确性 |
| top\_p | 0.95 | 0.95 | 核采样阈值 |
| top\_k | 20 | 20 | 截断采样 |
| repeat\_penalty | 1.05 | 1.05 | 重复惩罚 |
| context\_length | 262144 | 262144 | 128K 长上下文 |
| reasoning | auto | auto | 开启推理链（思维链） |
| reasoning\_budget | 400 | 400 | 推理预算 token |
| reasoning\_format | deepseek-legacy | deepseek-legacy | 推理输出到独立字段 |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP 推测解码（详见第 11 节）** |

> 💡 **思考模式**：通过 `--reasoning auto` 开启，模型先进行内部推理再输出答案。`reasoning_budget` 控制最大思考 token 数（推荐 400，可调 100-1000）。

---

## 10. 量化格式对比

| 格式 | 体积 | 精度 | 说明 |
| --- | --- | --- | --- |
| FP16 原始 | ~54 GB | 100% | 无损，需专业显卡 |
| **MoziSmartBit（本模型）** | **~13.7 GB** | **~99%** | **自研智能量化，精度最优、体积最小** |
| Q4_K_M | ~17 GB | ~98% | GGUF 标准 4bit |
| Q5_K_M | ~20 GB | ~99% | 更高精度 |
| Q6_K | ~23 GB | ~99.5% | 近无损 |
| Q8_0 | ~31 GB | ~100% | 无损 |

> MoziSmartBit 在保持约 99% 精度的同时，将 27B Dense 模型压缩至 13.7 GB（压缩比 3.9x），比 Q4_K_M 小约 20%，更适合消费级显卡本地部署。

---

## 11. MTP 推测解码（重要加速特性）

本模型内置 MTP（Multi-Token Prediction）推测解码层，开启后推理速度提升 **1.5-2 倍**。这是 Qwen3.8 架构的原生特性，MoziAI 保留了完整 MTP 权重。

**原理**：在模型架构中额外训练了轻量级预测头（Draft Model），用于在主模型验证前预先猜测后续 token，减少 forward 次数，降低推理延迟。猜测错误由主模型纠正，对输出质量无负面影响。

### 开启参数

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| 参数 | 推荐值 | 说明 |
| --- | --- | --- |
| --spec-type | draft-mtp | 启用 MTP 推测解码 |
| --spec-draft-n-max | 2 | 每次最多猜测 2 个 token（推荐值，接受率约 80%） |
| --spec-draft-p-min | 0.75 | 最低接受概率阈值（0.0-1.0，越大越保守） |

### 参数调整建议

| n-max | 接受率 | 适用场景 |
| --- | --- | --- |
| 1 | ~90% | 最保守，速度提升最小 |
| **2** | **~80%** | **推荐：平衡速度与准确率** |
| 3 | ~71% | 通用场景，速度提升明显 |
| 4-5 | ~60-65% | 创意写作、代码生成 |
| 6 | ~50-55% | 纯文本长输出（需配合 p-min 调整） |

---

## 12. 显存配置推荐

| 显存 | 推荐配置 | 说明 |
| --- | --- | --- |
| 16 GB | 上下文降至 64K，需 CPU 卸载 | 入门级，如 RTX 4060 Ti |
| **20 GB** | **128K 满配，q4_0 KV 缓存** | **推荐配置**，如 RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K 满配，显存余量充足 | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K 满配，最强配置 | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB 核显 | 128K 满配 | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 上下文越长，显存占用越多。OOM 时逐步降低 `-c` 参数。使用 `--fit on` 让 llama.cpp 自动调整层数适配显存。支持 NVIDIA / AMD / Intel 全品牌显卡。

---

## 13. 部署方式

### Ollama 部署

```bash
cat > Modelfile << 'EOF'
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf
PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 131072
PARAMETER num_gpu 99
EOF

ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

### LM Studio / Jan

在 LM Studio / Jan 中搜索 `moziAI`，选择 Q4\_K\_M 量化版本下载即可。

> 💡 Ollama 的 mmproj 和 chat\_template 支持有限，建议优先使用 llama.cpp 获得完整功能。

---

## 14. 基准评测

MoziAI-27B-3.8 基于 Qwen3.8-27B 底座微调，金融垂直领域为核心优化方向。

### 编码能力

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Agent 能力

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### 通用能力

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### 多模态能力

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> 竞品数据为官方公开评测结果。MoziAI 金融垂直领域（财报解读、量化策略、风控合规、Agent 工具调用等）表现显著优于通用模型。

---

## 15. 许可证

本模型采用**自定义限制性许可证**：

- ✅ **允许** — 免费商业使用、复制和分发
- ❌ **禁止** — 二次开发、转售售卖、再许可
- 📋 **要求** — 保留原始版权声明，注明来源：moziAI-27B

本模型按「原样」提供，不提供任何形式的保证。模型输出仅供参考，不构成投资建议。使用者需自行承担使用风险。

详细条款请参阅 [LICENSE](LICENSE) 文件。

---

## 16. 联系方式

- **HuggingFace**：[@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**：[@chenyumo166](https://github.com/chenyumo166)
- **微博**：[@rimochen](https://weibo.com/rimochen)
- **E-mail**：263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
