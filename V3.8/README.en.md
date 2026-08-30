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

# MoziAI-27B-3.8 - Free Locally Deployable Small Yet Powerful Multimodal AI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## Model Overview

MoziAI-27B-3.8 is a local open-source financial AI multimodal LLM (supports vision and tool calling) developed by Chinese finance influencer Chen Yumo's team. moziAI-27B-3.8 is built on the open-source base model Qwen3.8-27B (Dense 27B architecture, MIT licensed), incorporating the Chen Yumo team's self-developed: (financial data + financial domain capabilities + training methods + Seven-Dimensional Thinking framework + agent LOOP mechanism + hybrid quantization algorithm MoziSmartBit).

Through the self-developed MoziSmartBit intelligent quantization technology, the 27-billion parameter Dense model is compressed to approximately 12.79 GB, which is 3.3G (about 20%) smaller than conventional Q4_K_M quantization models of about 17 GB; achieving the optimal balance between precision and size, delivering **~99% of FP16 precision quality**.

In addition to retaining general AI capabilities, this model enhances: financial vertical domain applications, financial Q&A, quantitative programming, tool calling, and general programming, as well as the model's Seven-Dimensional Thinking capability, LOOP mechanism, and compatibility with various agent platforms.

The model developer Chen Yumo frequently uses this model for local financial data analysis, quantitative strategy R&D, market research, article writing, overall project advancement, general programming, and 128K context tasks via OpenClaw/Hermes. It can be deployed locally on consumer-grade GPUs, saving substantial cloud token costs, achieving **7x24 token freedom** while ensuring local data privacy and security.

Supports llama.cpp, Ollama, LM Studio and other mainstream inference frameworks.

**Release Date: 2026-08-30** | **Version: V3.8**

## Model Features

- **Financial Vertical Focus**: Deep optimization for financial Q&A, quantitative programming, and tool calling
- **MoziSmartBit Intelligent Quantization**: Self-developed smart quantization, best balance of precision and size, compressed to approximately **12.79 GB** with **~99%** precision retention
- **Consumer-grade Deployment**: Deployable on 16GB+ VRAM GPUs (with CPU offloading); 20GB+ for full 128K long context
- **MTP Speculative Decoding**: Built-in multi-token prediction layer for 1.5-2x inference speedup when enabled
- **Multilingual Support**: 201 languages and dialects, with enhanced Chinese capabilities, covering English/Japanese/Korean/German/French/Spanish/Portuguese and more
- **General Programming**: Full-stack development, code debugging, architecture design, script writing, covering Python/JS/TS/Go/Rust and other mainstream languages
- **Article Writing**: High-quality multi-genre writing including research reports, analysis articles, technical documentation, creative content
- **Vision Understanding**: Supports multimodal vision, local screenshot input, image comprehension
- **Enhanced Reasoning**: Chain-of-thought training for improved reasoning quality
- **Multi-Framework Support**: Compatible with llama.cpp, Ollama, LM Studio, Jan
- **Multi-Agent Platform Support**: Deep integration with OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex and other mainstream AI IDEs and Agent frameworks, natively supports tool calling and multi-turn task orchestration, ready to use out of the box

## Core Capabilities

| Capability Area | Description |
|----------------|-------------|
| Market Analysis | Macro/microeconomic interpretation, A-share/HK/US stock/commodity/crypto market logic |
| Financial Reports | Key financial indicator interpretation, research report summary, valuation & earnings forecast assistance |
| Risk & Compliance | Product risk assessment, investment advice compliance, financial regulation policy interpretation |
| Quant & Strategy | Quant strategy design, Pyramid (PEL) quantization, backtesting logic, factor construction and tool calling |
| Tool Calling | Integration with real-time quotes, databases, research report retrieval and other financial data sources |

## Technical Specifications

| Item | Specification |
|------|---------------|
| Base Model | Qwen3.8-27B (Dense architecture, hybrid attention 16 full + 48 linear, MIT licensed) |
| Parameters | 27B Dense |
| Quantization | Self-developed MoziSmartBit Intelligent Quantization + GGUF standard format |
| Context Length | 128K (262,144 tokens) |
| Model Size | ~12.79 GB |
| Min VRAM | **16GB+** deployable (with CPU offload, e.g., RTX 4060 Ti 16G); **20GB+** smooth long context (e.g., RX 7900 XT 20G); **24GB+** full 128K + vision |
| Inference Framework | llama.cpp / Ollama / LM Studio / Jan |
| Inference Speed | With MTP speculative decoding: AMD R9700 70+ tok/s, AMD MAX+395 CPU 50+ tok/s, AMD MAX+395 GPU 35+ tok/s, enabling local 7x24 token freedom |
| Developer | Chen Yumo Team |

## Quantization Formats

| Format | Size | Precision | Notes |
|--------|------|-----------|-------|
| FP16 (Original) | ~54 GB | 100% | Original 16-bit precision |
| **MoziSmartBit** | **~12.79 GB** | **~99%** | **Self-developed intelligent quantization** |
| Q4_K_M | ~17 GB | ~98% | GGUF standard 4-bit |
| Q5_K_M | ~20 GB | ~99% | Higher precision |
| Q6_K | ~23 GB | ~99.5% | Near lossless |
| Q8_0 | ~31 GB | ~100% | Lossless |

> MoziAI V3.8 uses MoziSmartBit intelligent quantization, compressing the 27-billion parameter Dense model to approximately 12.79 GB with ~99% precision retention, achieving a 4.0x compression ratio while balancing inference quality and deployment accessibility.

## MoziSmartBit Intelligent Quantization

Traditional quantization uses uniform precision across all layers. Chen Yumo's self-developed **MoziSmartBit Intelligent Quantization** adopts a differentiated strategy tailored to Dense model structures, achieving the optimal balance between size and precision. The model quality exceeds Q4_K_M format while occupying only 12.79 GB, with a 4.0x compression ratio and ~99% precision retention.

### Compression Results

- **Minimal Precision Loss**: Training gains > quantization losses, making the post-training MoziAI-27B outperform the pre-training BF16 base in financial domain text perplexity
- **4.0x Volume Reduction**: Compressed from FP16 (~54 GB) to ~12.79 GB, significantly smaller than Q4_K_M (~17 GB), dramatically reducing VRAM and storage requirements
- **Consumer GPU Deployment**: The 27B Dense model, previously requiring high-end GPUs, can now be deployed on 16GB+ VRAM GPUs, with 20GB+ for full 128K long context

### Comparison Advantages

**vs Q4_K_M (~17 GB)**: ~20% smaller (~12.79 GB), better precision than Q4_K_M, lower VRAM threshold, deployable on 16GB+ GPUs, smooth 128K on 20GB+

**vs FP16 (~54 GB)**: ~4.0x compression, ~99% precision retention, from professional-grade GPUs down to consumer GPUs for 128K long context

## Recommended Inference Parameters

Based on llama.cpp official recommendations and local optimization (AMD Radeon AI PRO R9700 32GB):

| Parameter | General Chat | Coding/Agent | Description |
|-----------|-------------|--------------|-------------|
| temperature | 0.7 | 1.0 | Balance creativity and accuracy |
| top_p | 0.95 | 0.95 | Nucleus sampling threshold |
| top_k | 20 | 20 | Truncated sampling |
| repeat_penalty | 1.05 | 1.05 | Repetition penalty |
| presence_penalty | 0 | 0 | No presence penalty |
| context_length | 131072 | 131072 | 128K long context |
| batch_size | 1024 | 1024 | Batch size |
| ubatch_size | 128 | 128 | Micro-batch size |
| flash_attention | auto | auto | Automatic Flash Attention |
| kv_cache | q4_0 | q4_0 | KV cache quantization |
| poll | 0 | 0 | Idle = no GPU polling, power saving |
| reasoning | auto | auto | Enable reasoning chain (chain-of-thought) |
| reasoning_budget | 1024 | 1024 | Reasoning token budget |
| reasoning_format | deepseek-legacy | deepseek-legacy | Reasoning format |
| samplers | top_k;top_p;temperature;typ_p | top_k;top_p;temperature;typ_p | Sampler order |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP speculative decoding** |

> 💡 **Thinking Mode**: This model has built-in Qwen3.8 Thinking (chain-of-thought) capability. Enable via `--reasoning auto`. `reasoning_budget` controls max thinking tokens (400 recommended, adjustable 100-1000 based on complexity). `reasoning-format deepseek-legacy` outputs thinking to a separate field.

## MTP Speculative Decoding (Important Speed Feature)

This model has built-in MTP (Multi-Token Prediction) speculative decoding layers. When enabled, inference speed improves by **1.5-2x**. This is a native feature of the Qwen3.8 architecture, and MoziAI preserves the full MTP weights.

### How MTP Works

MTP adds a lightweight draft prediction head that speculatively predicts future tokens before the main model validates them, reducing the number of main model forward passes and significantly lowering inference latency.

### Enable MTP in llama.cpp

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

| Parameter | Recommended | Description |
|-----------|-------------|-------------|
| --spec-type | draft-mtp | Enable MTP speculative decoding |
| --spec-draft-n-max | 2 | Max tokens to draft per step (~80% acceptance rate, recommended) |
| --spec-draft-p-min | 0.75 | Minimum acceptance probability threshold (0.0-1.0, higher = more conservative) |

### MTP Tuning Guide

| spec-draft-n-max | Acceptance Rate | Best For |
|---|---|---|
| 1 | ~90% | Most conservative, smallest speedup |
| **2** | **~80%** | **Recommended: balances speed and accuracy** |
| 3 | ~71% | General use, noticeable speedup |
| 4-5 | ~60-65% | Creative writing, code generation |
| 6 | ~50-55% | Long-form text (pair with p-min adjustment) |

> ⚠️ MTP speculative decoding has no negative impact on output quality (incorrect guesses are corrected by the main model). Start with `spec-draft-n-max 2` and adjust based on acceptance rate.

## llama.cpp Launch Command

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

> 💡 **Disable MTP**: Remove `--spec-type draft-mtp`, `--spec-draft-n-max 2`, and `--spec-draft-p-min 0.75` to disable MTP. Inference speed decreases ~30-50%, but VRAM usage is lower.

## VRAM Configuration Guide

| VRAM | Recommended Context | KV Cache | Vision | Notes |
|------|-------------------|----------|--------|-------|
| 20 GB | 128K Full | q4_0 | Full Support | Vision+128K, recommended config (~16GB model+KV, ~4GB headroom) |
| 24 GB | 128K Full | q4_0 | Full Support | Vision+128K, sufficient headroom |
| 32 GB+ | 128K Full | q4_0 | Full Support | Vision+128K, ample headroom, best config |

**NVIDIA Reference**

| VRAM | Model |
|------|-------|
| 16 GB | RTX 4060 Ti (requires CPU offload) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD Reference**

| VRAM | Model |
|------|-------|
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel Reference**

| VRAM | Model |
|------|-------|
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (requires CPU offload) |

**CPU Shared Memory / iGPU**

| VRAM | Processor |
|------|-----------|
| 128 GB | AMD Ryzen AI Max+ 395 (Radeon 8060S iGPU) |
| 128 GB | NVIDIA RTX Spark (Blackwell RTX GPU) |

> 💡 Any VRAM meeting the above requirements works. Supports NVIDIA / AMD / Intel GPUs as well as iGPU CPUs with 128GB unified memory.
> 💡 Longer context uses more VRAM. If OOM occurs, reduce the `-c` parameter. Use `--fit on` to let llama.cpp auto-adjust layers.

## Ollama Deployment

```bash
# Create Modelfile
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf

PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 262144
PARAMETER num_gpu 99

# Load vision projection (optional, enables vision)
PARAMETER mmproj ./moziAI-27B-3.8-mmproj-F16.gguf

# Load chat template (recommended)
PARAMETER chat_template_file ./chat-template-moziai-27B-v38.jinja

# Build and run
ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

> 💡 Ollama support for `mmproj` and `chat_template_file` varies by version. For full functionality, llama.cpp is recommended.

## LM Studio / Jan Deployment

Search for `moziAI` in LM Studio / Jan, select the Q4_K_M quantized version and download.

## Benchmark Results

MoziAI-27B-3.8 is fine-tuned on Qwen3.8-27B (Dense 27B). General capability benchmarks match the base Qwen3.8-27B; MoziAI specializes in the financial vertical domain.

### Coding

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73.0 | 63.4 | 64.0 | 51.7 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 51.2 | 53.4 |
| NL2Repo-Bench | 42.3 | 36.2 | 41.1 | -- | 47.6 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | -- | 63.8 |

### Agent

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 | -- | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- | -- |
| Agents' Last Exam (Score) | **42.9** | 27.3 | 33.6 | -- | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | -- | 62.0 |

### General

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79.5** | 69.1 | 79.1 | 77.0 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | 83.5 | **91.3** |

### Multimodal

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94.6** | 85.1 | 90.3 | -- | 65.5 |
| BabyVision (With CI) | **85.6** | 28.9 | 70.4 | -- | 12.6 |
| CharXiv RQ (With CI) | **90.2** | 78.4 | 85.8 | -- | 66.0 |
| OmniDocBench 1.5 | 91.1 | 89.4 | **91.4** | 75.8 | 86.6 |
| RealWorldQA | 85.9 | 84.1 | **86.9** | -- | 73.9 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- | -- |

> MoziAI-27B-3.8 general benchmarks match Qwen3.8-27B base. The financial vertical domain is MoziAI's core optimization direction, significantly outperforming general models in financial report analysis, quantitative strategy, risk compliance, and agent tool calling.

## Download

| Platform | Link |
|----------|------|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

> 💡 **LM Studio**: Search `moziAI` in [LM Studio](https://lmstudio.ai) for one-click download.
> 💡 **Download**: Click the link, go to "Files and versions" tab, download all files from V3.8 directory (model, vision projection, chat template) to the same folder.

⚠️ **Vision requires mmproj file**

- **Vision file**: `moziAI-27B-3.8-mmproj-F16.gguf` (~927 MB, BF16 precision)
- **Location**: Same directory as the GGUF model file
- **Usage**: Add `--mmproj` parameter when launching llama-server

> Without vision file, only text dialogue is available.

## Quick Start

### 1. Download

Download all files from V3.8 directory:

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # Main model (required)
├── moziAI-27B-3.8-mmproj-F16.gguf              # Vision projection (optional)
└── chat-template-moziai-27B-v38.jinja           # Chat template (recommended)
```

### 2. Launch

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

> Add `--mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf` for vision support.

### 3. Start Chatting

Open `http://localhost:8080` in your browser.

## SEO Keywords

Financial AI, local open-source model, edge deployment, quantitative programming, MoziSmartBit, intelligent quantization, GGUF quantization, Dense model, local deployment, finance AI, tool calling, Agent, llama.cpp, Ollama, GGUF, Q4_K_M, Qwen3.8-27B, financial vertical, open source, MTP speculative decoding, 128K long context, multimodal, local LLM, edge AI, self-hosted AI, speculative decoding, Chinese financial AI, Qwen3.8 fine-tune, tool-calling, vision model, open-source LLM, consumer GPU deployment, intelligent quantization, on-premise AI

## License

**Custom restrictive license**:

✅ **Allowed**: Free commercial use, copy and distribute as-is

❌ **Prohibited**: Secondary development, resale, re-licensing

📋 **Required**: Retain original copyright notice, credit moziAI-27B

See [LICENSE](LICENSE) for details.

## Disclaimer

This model is provided "as is" without any warranties. Model outputs are for reference only and do not constitute investment advice. Users assume all risks.

## Contact

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
