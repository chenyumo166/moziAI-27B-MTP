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

# MoziAI-27B-3.8 — A Compact Yet Powerful Multimodal AI Model for Free Local Deployment

[English](README.en.md) | [简体中文](README.zh.md) | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

**Release Date: 2026-08-30** · **Version: V3.8**

---

## 📑 Table of Contents

- [1. Model Overview](#1-model-overview)
- [2. Key Features](#2-key-features) — Dynamic 7-Dimensional Thinking / LOOP / MoziSmartBit / Finance Focus
- [3. Version Upgrade Notes](#3-version-upgrade-notes)
- [4. Core Capabilities](#4-core-capabilities)
- [5. Technical Specifications](#5-technical-specifications)
- [6. ⚡ Quick Start](#6--quick-start3-files--100-activate-best-inference)
- [7. Model Downloads](#7-model-downloads)
- [8. Launch Commands](#8-launch-commands)
- [9. Recommended Inference Parameters](#9-recommended-inference-parameters)
- [10. Quantization Format Comparison](#10-quantization-format-comparison)
- [11. MTP Speculative Decoding](#11-mtp-speculative-decoding)
- [12. VRAM Configuration Recommendations](#12-vram-configuration-recommendations)
- [13. Deployment Methods](#13-deployment-methods)
- [14. Benchmarks](#14-benchmarks)
- [15. License](#15-license)
- [16. Contact](#16-contact)

---

## 1. Model Overview

MoziAI-27B-3.8 is a local open-source multimodal AI large model developed by the team of Chinese finance influencer Chen Yumo. Built on the open-source base **Qwen3.8-27B** (Dense 27B architecture, MIT license), it integrates the team's self-developed financial data + financial domain capabilities + dynamic seven-dimensional thinking framework + agent LOOP reflection and iteration mechanism + MoziSmartBit hybrid quantization algorithm. This model lowers the barrier to local deployment for individuals and enterprises, is licensed for **free commercial use**, can run on consumer GPUs, saves significant cloud token costs, enables 24/7 token freedom, and ensures local data privacy and security.

---

## 2. Key Features

### 🧠 Dynamic Seven-Dimensional Thinking Framework

MoziAI's self-developed core reasoning framework. For any task, the model first outputs a **moziAI-Think** marker, then dynamically unfolds structured thinking based on task complexity:

| Level | Use Case | Typical Tasks | Dimensions Expanded |
| --- | --- | --- | --- |
| **Level 0** | Simple Q&A | Term explanation, fact lookup, translation, summarization | ①Understand task ⑤Resource needs (2-dimension quick answer) |
| **Level 1** | Analysis & Diagnosis | Market research, copywriting, data analysis, report interpretation, strategy evaluation | ①②③⑤⑥ 5-dimension assessment |
| **Level 2** | Complex Dev/Strategy | Code development, architecture design, quant strategy development, multi-step workflows, system design | ①②③④⑤⑥⑦ full 7-dimension deep reasoning |

> Seven dimensions: ①Understand task ②Complexity assessment ③Dependencies ④Risk assessment ⑤Resource needs ⑥Acceptance criteria ⑦Execution strategy

### 🔄 Agent LOOP Iteration Mechanism

Complex tasks automatically enter **moziAI-Loop** iteration mode: **Round 1 execute + evaluate → Round 2 adjust + verify**, ensuring output is self-validated before the final answer. The model works like a senior engineer — "decompose problem → evaluate approach → execute → reflect → optimize" — significantly improving accuracy and executability of complex tasks. For simple Q&A and tasks, Loop is automatically disabled.

### 📦 MoziSmartBit Intelligent Quantization

Self-developed layered intelligent quantization compresses the 27-billion-parameter Dense model to about **13.7 GB** — about 3.3 GB (~20%) smaller than standard Q4_K_M (~17 GB), while maintaining FP16 **~99%** precision. Traditional quantization applies uniform precision across all layers; MoziSmartBit uses an intelligent differentiated strategy tailored to Dense model architecture, achieving better precision than Q4_K_M.

### 💰 Financial Vertical Domain Focus

Deeply optimized for financial Q&A, quantitative programming, and tool calling. The financial domain has extremely low tolerance for model hallucination, and MoziAI significantly outperforms general models of the same size in this domain.

### 🌐 Other Features

- **Multilingual support**: 201 languages and dialects, with specially optimized Chinese capability
- **General programming**: Full-stack development, debugging, architecture design, covering Python/JS/TS/Go/Rust
- **Article writing**: Research reports, analytical articles, technical docs, creative content and other multi-genre high-quality writing
- **Vision understanding**: Multimodal vision, supports understanding image content from local screenshots
- **Multi-framework support**: llama.cpp / Ollama / LM Studio / Jan
- **Multi-Agent support**: OpenClaw / Hermes / Cursor / Claude Code / Codex, native tool calling and multi-turn task orchestration

---

## 3. Version Upgrade Notes

This upgrade mainly strengthens: moziAI's self-developed dynamic seven-dimensional thinking + LOOP iteration reasoning mode, making it smarter at recognizing task complexity, with higher task completion rates for complex tasks, and improving the "think before act" capability.

moziAI will maintain an active version upgrade iteration cadence to stay at the forefront of AI development, and continuously leverage self-developed technology to make local AI models lighter to deploy while becoming more capable.

---

## 4. Core Capabilities

| Capability Domain | Description |
| --- | --- |
| Market Analysis | Macro/micro economic interpretation, A-share/HK/US stocks, commodities, crypto market trends and logic |
| Finance & Reports | Financial report key indicator interpretation, research report summarization, valuation & earnings forecast assistance |
| Risk & Compliance | Product risk assessment, investment advice compliance reminders, financial regulatory policy interpretation |
| Quant & Strategy | Quant strategy design, Pyramid (PEL) quant, backtest logic, factor construction & tool calling |
| Tool Calling | Access to real-time market data, databases, research report retrieval and other financial data sources |

---

## 5. Technical Specifications

| Item | Specification |
| --- | --- |
| Base Model | Qwen3.8-27B (Dense architecture, hybrid attention 16 full + 48 linear, MIT license) |
| Parameters | 27 billion (27B) Dense architecture |
| Quantization | Self-developed MoziSmartBit intelligent quantization + GGUF standard format |
| Context Length | 128K (262,144 tokens) |
| Model Size | ~13.7 GB |
| Min VRAM | **16GB+** deployable (CPU offload); **20GB+** smooth long context; **24GB+** full 128K + vision |
| Inference Frameworks | llama.cpp / Ollama / LM Studio / Jan |
| Inference Speed | With MTP speculative decoding: R9700 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Development Team | Chen Yumo Team |

---

## 6. ⚡ Quick Start (3 Files = 100% Activate Best Inference)

> ⚠️ **Key note**: MoziAI's best inference capability requires **downloading 3 files simultaneously** — main model, vision projector, chat template. Missing any one will lose the corresponding capability.

### 6.1 Download Model Files

Download **all files in the V3.8 directory** from HuggingFace / ModelScope to the same local directory:

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Main model (required, 13.7 GB)
└── chat-template-moziai-27B-v38.jinja         ← Chat template (required, includes 7D thinking + Loop instructions)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Vision projector (required, 927 MB)
```

| File | Size | Required | Purpose |
| --- | --- | --- | --- |
| Main model `.gguf` | ~13.7 GB | **Required** | Model weights, core inference |
| Vision projector `mmproj` | ~927 MB | **Required** | Multimodal vision understanding; image capability lost without it |
| Chat template `.jinja` | Tiny | **Required** | Injects MoziAI identity + 7-dimensional thinking + LOOP instructions |

### 6.2 Launch and Use

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Open `http://localhost:8080` in your browser to start chatting. Full recommended parameters in Section 9.

---

## 7. Model Downloads

| Platform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main/V3.8) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master/V3.8) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master/V3.8) |

> 💡 **LM Studio users**: search `moziAI` in [LM Studio](https://lmstudio.ai) for one-click download, no manual file download needed.

---

## 8. Launch Commands

### Minimal Launch (with Three-Piece Set)

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Full Recommended Launch

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
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

> 💡 Disable MTP: remove `--spec-type draft-mtp` and related parameters; speed drops ~30-50% but VRAM usage is lower.

---

## 9. Recommended Inference Parameters

Based on llama.cpp official recommendations and local testing optimizations (AMD Radeon AI PRO R9700 32GB):

| Parameter | General Chat | Coding/Agent | Description |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Balance creativity and accuracy |
| top\_p | 0.95 | 0.95 | Nucleus sampling threshold |
| top\_k | 20 | 20 | Truncation sampling |
| repeat\_penalty | 1.05 | 1.05 | Repetition penalty |
| context\_length | 262144 | 262144 | 128K long context |
| reasoning | auto | auto | Enable reasoning chain (CoT) |
| reasoning\_budget | 400 | 400 | Reasoning budget tokens |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Reasoning output to separate field |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP speculative decoding (see Section 11)** |

> 💡 **Thinking mode**: enabled via `--reasoning auto`; the model performs internal reasoning before output. `reasoning_budget` controls max thinking tokens (recommended 400, adjustable 100-1000).

---

## 10. Quantization Format Comparison

| Format | Size | Precision | Description |
| --- | --- | --- | --- |
| FP16 original | ~54 GB | 100% | Lossless, needs professional GPU |
| **MoziSmartBit (this model)** | **~13.7 GB** | **~99%** | **Self-developed intelligent quantization, best precision, smallest size** |
| Q4_K_M | ~17 GB | ~98% | GGUF standard 4bit |
| Q5_K_M | ~20 GB | ~99% | Higher precision |
| Q6_K | ~23 GB | ~99.5% | Near lossless |
| Q8_0 | ~31 GB | ~100% | Lossless |

> MoziSmartBit maintains ~99% precision while compressing the 27B Dense model to 13.7 GB (compression ratio 3.9x), ~20% smaller than Q4_K_M, making it better suited for consumer GPU local deployment.

---

## 11. MTP Speculative Decoding (Important Speed Feature)

This model has built-in MTP (Multi-Token Prediction) speculative decoding layers; inference speed improves **1.5-2x** when enabled. This is a native feature of the Qwen3.8 architecture, and MoziAI retains the complete MTP weights.

**Principle**: A lightweight prediction head (Draft Model) is additionally trained in the model architecture to guess subsequent tokens before main model verification, reducing forward passes and lowering inference latency. Wrong guesses are corrected by the main model with no negative impact on output quality.

### Enable Parameters

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Recommended Value | Description |
| --- | --- | --- |
| --spec-type | draft-mtp | Enable MTP speculative decoding |
| --spec-draft-n-max | 2 | Max 2 tokens guessed per step (recommended, ~80% acceptance rate) |
| --spec-draft-p-min | 0.75 | Minimum acceptance probability threshold (0.0-1.0, higher = more conservative) |

### Parameter Tuning Suggestions

| n-max | Acceptance Rate | Use Case |
| --- | --- | --- |
| 1 | ~90% | Most conservative, smallest speed gain |
| **2** | **~80%** | **Recommended: balance speed and accuracy** |
| 3 | ~71% | General use, noticeable speed gain |
| 4-5 | ~60-65% | Creative writing, code generation |
| 6 | ~50-55% | Pure-text long output (adjust p-min accordingly) |

---

## 12. VRAM Configuration Recommendations

| VRAM | Recommended Config | Description |
| --- | --- | --- |
| 16 GB | Lower context to 64K, CPU offload needed | Entry level, e.g. RTX 4060 Ti |
| **20 GB** | **128K full config, q4_0 KV cache** | **Recommended**, e.g. RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K full config, ample VRAM headroom | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K full config, strongest setup | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 128K full config | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Longer context = more VRAM usage. On OOM, gradually lower the `-c` parameter. Use `--fit on` to let llama.cpp auto-adjust layer count to fit VRAM. Supports NVIDIA / AMD / Intel GPUs.

---

## 13. Deployment Methods

### Ollama Deployment

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

Search `moziAI` in LM Studio / Jan and download the Q4\_K\_M quantized version.

> 💡 Ollama's mmproj and chat\_template support is limited; it is recommended to use llama.cpp for full functionality.

---

## 14. Benchmarks

MoziAI-27B-3.8 is fine-tuned on the Qwen3.8-27B base, with the financial vertical domain as the core optimization direction.

### Coding

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Agent Capabilities

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### General Capabilities

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Multimodal Capabilities

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Competitor data from official public benchmark results. MoziAI significantly outperforms general models in financial vertical domains (financial report interpretation, quant strategy, risk & compliance, Agent tool calling, etc.).

---

## 15. License

This model uses a **custom restrictive license**:

- ✅ **Allowed** — Free commercial use, copying and distribution
- ❌ **Prohibited** — Secondary development, resale, re-licensing
- 📋 **Requirements** — Retain original copyright notice, attribute source: moziAI-27B

This model is provided "as is" without warranties of any kind. Model output is for reference only and does not constitute investment advice. Users assume all usage risks.

See the [LICENSE](LICENSE) file for full terms.

---

## 16. Contact

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. All rights reserved.
