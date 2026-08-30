---
language:
- en
- zh
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

# MoziAI-27B-3.8 - A Small Yet Powerful Multimodal AI Model for Free Local Deployment

[English](README.en.md) | [简体中文](V3.8/README.zh.md) | [繁體中文](V3.8/README.zh-hant.md) | [日本語](V3.8/README.ja.md) | [한국어](V3.8/README.ko.md) | [हिन्दी](V3.8/README.hi.md) | [Deutsch](V3.8/README.de.md) | [Français](V3.8/README.fr.md) | [Nederlands](V3.8/README.nl.md) | [Italiano](V3.8/README.it.md) | [Русский](V3.8/README.ru.md)

## Overview

MoziAI-27B-3.8 is an open-source local multimodal AI model developed by Chen Yumo's team, featuring enhanced financial domain capabilities, vision support, tool calling, and consumer GPU local deployment. Built on the open-source base Qwen3.8-27B (Dense 27B architecture, MIT license), MoziAI-27B-3.8 integrates Chen Yumo team's self-developed technologies: financial data + financial domain capabilities + training methodology + Dynamic Seven-Dimensional Thinking System + Intelligent Agent LOOP Reflective Iterative Mechanism + MoziSmartBit mixed quantization algorithm. It lowers the barrier to local deployment for individuals and enterprises, with free commercial licensing. Deployable on consumer GPUs, it saves substantial cloud token costs, achieving 24/7 token freedom while ensuring local data privacy and security.

**Dynamic Seven-Dimensional Thinking System + Intelligent Agent LOOP Iterative Mechanism**: MoziAI's self-developed core reasoning paradigm. It intelligently assesses task complexity—simple tasks activate two-dimensional thinking for rapid responses, moderately complex tasks enable five-dimensional thinking, and highly complex tasks engage the full seven-dimensional thinking with LOOP reflective iterative mechanism. This challenges the effective problem-solving capability of trillion-parameter models dozens of times its size, without sacrificing the agile response of simple tasks. It enables local models to cultivate the "think before you act" capability of seasoned human experts, making this self-developed core reasoning paradigm highly distinctive compared to models of similar size.

**Through the self-developed MoziSmartBit intelligent quantization technology**, the 27-billion parameter dense model is compressed to approximately 12.79 GB, approximately 3.3 GB (about 20%) smaller than conventional Q4_K_M quantized models (approximately 17 GB); achieving the optimal balance between precision and size, delivering ~99% FP16 precision quality.

In addition to preserving the general capabilities of AI large models, this model has been enhanced for: financial domain applications, financial Q&A, quantitative programming, tool calling, and general programming, compatible with various agent platform integrations.

Model developer Chen Yumo frequently uses this model for local financial data analysis, quantitative strategy research, market research, article writing, overall project development and advancement, general programming, and executing complex tasks with 256K long context via OpenClaw/Hermes.

Supports free local deployment on mainstream inference frameworks including llama.cpp, Ollama, and LM Studio

**Release Date: 2026-08-30** | **Version: V3.8**

## Model Features

- **🧠 Dynamic Seven-Dimensional Thinking System**: MoziAI's self-developed core reasoning framework. For any task, the model first outputs a **moziAI-Think** marker and dynamically unfolds structured thinking based on task complexity—from a two-dimensional quick answer for simple Q&A (Level 0), to five-dimensional evaluation for analysis and diagnosis (Level 1), to full seven-dimensional deep reasoning for complex development/strategy design (Level 2): ①Task Understanding ②Complexity Assessment ③Dependency Analysis ④Risk Assessment ⑤Resource Requirements ⑥Acceptance Criteria ⑦Execution Strategy.
- **🧠 Intelligent Agent LOOP Iterative Mechanism**: For complex tasks, MoziAI automatically enters **moziAI-Loop** iteration mode: Round 1 execution + evaluation → Round 2 adjustment + verification, ensuring outputs are self-verified before final delivery, rather than generated in a single pass. This means the model doesn't just "answer questions"—it behaves like a senior engineer: decomposing problems → evaluating solutions → executing → reflecting → optimizing, significantly improving accuracy and executability for complex tasks. Simple Q&A and tasks automatically disable the Loop mechanism.
- **🧠 MoziSmartBit Intelligent Quantization**: MoziAI's self-developed layered intelligent quantization achieves the optimal balance between precision and size, compressed to approximately 12.79 GB while maintaining ~99% FP16 precision.
- **🧠 Financial Vertical Domain Focus**: Deep optimization for financial Q&A, quantitative programming, and tool calling. The financial domain has extremely low tolerance for model hallucination, demonstrating MoziAI's significant capability enhancement over general models in vertical domains.
- **Multilingual Support**: Supports 201 languages and dialects, with particularly optimized Chinese capabilities, along with English, Japanese, Korean, German, French, Spanish, Portuguese, and other major languages.
- **General Programming Capability**: Supports full-stack development, code debugging, architecture design, and script writing, covering Python/JS/TS/Go/Rust and other mainstream languages.
- **Article Writing**: Supports high-quality multi-genre writing, including research reports, analysis articles, technical documentation, and creative content.
- **Vision Understanding**: Supports multimodal vision—screenshots can be pasted directly into the chat window, and the model can understand visual content.
- **Multi-Framework Support**: Compatible with mainstream inference frameworks including llama.cpp, Ollama, LM Studio, and Jan.
- **Multi-Agent Platform Support**: Deep integration with OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex, and other mainstream AI IDEs and Agent frameworks, with native support for tool calling and multi-turn task orchestration, ready to use out of the box.

## Core Capabilities

| Capability Area | Description |
| --- | --- |
| Market Analysis | Macro/micro economic interpretation, A-share/HK/US/commodity/crypto market analysis and logic structuring |
| Finance & Research Reports | Key financial indicator interpretation, research report extraction, valuation and earnings forecast assistance |
| Risk Control & Compliance | Product risk assessment, investment advice compliance reminders, financial regulation policy interpretation |
| Quantitative & Strategy | Quantitative strategy design, Pyramid (PEL) quantitative analysis, backtesting logic, factor construction, and tool calling |
| Tool Calling | Integration with real-time market data, databases, research report retrieval, and other financial data sources |

## Technical Specifications

| Item | Parameters |
| --- | --- |
| Base Model | Qwen3.8-27B (Dense architecture, hybrid attention 16 full + 48 linear, MIT license) |
| Parameter Scale | 27 billion (27B) Dense architecture |
| Quantization | Self-developed MoziSmartBit intelligent quantization algorithm + GGUF standard format |
| Context Length | 128K (262,144 tokens) |
| Model Size | ~12.79 GB |
| Minimum VRAM | **16GB+** deployable (with CPU offload, e.g., RTX 4060 Ti 16G); **20GB+** smooth long context (e.g., RX 7900 XT 20G); **24GB+** full 128K + vision |
| Inference Framework | llama.cpp / Ollama / LM Studio / Jan |
| Inference Speed | With MTP speculative decoding: AMD R9700 up to 70+ tokens/s, AMD MAX+395 CPU iGPU up to 50+ tokens/s, AMD MAX+395 GPU up to 35+ tokens/s, achieving local token freedom |
| Development Team | Chen Yumo Team |

## Quantization Formats & Model Size

| Quantization Format | Model Size | Precision Retention | Description |
| --- | --- | --- | --- |
| FP16 (Original) | ~54 GB | 100% | Original 16-bit precision |
| **MoziSmartBit** | **~12.79 GB** | **~99%** | **This model uses self-developed intelligent quantization** |
| Q4_K_M | ~17 GB | ~98% | GGUF standard 4-bit |
| Q5_K_M | ~20 GB | ~99% | Higher precision |
| Q6_K | ~23 GB | ~99.5% | Near-lossless |
| Q8_0 | ~31 GB | ~100% | Lossless |

> MoziAI V3.8 uses the MoziSmartBit intelligent quantization scheme, compressing the 27B Dense model to approximately 12.79 GB while maintaining ~99% precision, with a compression ratio of 4.0x, balancing inference quality and deployment accessibility for consumer GPU local deployment.

## MoziSmartBit Intelligent Quantization Technology

Traditional quantization schemes apply uniform precision across all layers. The Chen Yumo team's self-developed **MoziSmartBit Intelligent Quantization** targets the structural characteristics of Dense models, employing an intelligent differentiated quantization strategy to achieve the optimal balance between size and precision. Model quality exceeds the Q4_K_M format, with a size of only 12.79 GB, a compression ratio of 4.0x, and precision retention of approximately 99%.

### Compression Results

- **Minimal quantization precision loss**: Training gains > quantization losses. The trained MoziAI-27B achieves PPL on financial text superior to the pre-training bf16 base, reducing hallucination and perplexity compared to similar AI models.
- **4.0x model size compression**: From FP16 (~54 GB) compressed to ~12.79 GB, also significantly smaller than Q4_K_M's ~17 GB, substantially reducing VRAM and storage requirements.
- **Consumer GPU deployable**: The 27B Dense model, originally requiring high-end GPUs, can now be deployed locally with 16GB VRAM, with 20GB+ GPUs enabling full 128K long context inference.

### Comparative Advantages

**vs Q4_K_M (~17 GB)**: Approximately 20% smaller (~12.79 GB), precision exceeds Q4_K_M, lower VRAM threshold, deployable on 16GB GPUs, smooth 128K long context on 20GB+ GPUs.

**vs Original FP16 (~54 GB)**: Approximately 4.0x size compression, ~99% precision retention, from requiring professional-grade GPUs down to consumer-grade GPUs for local 128K long context inference.

## Recommended Inference Parameters

Based on llama.cpp official recommended parameters and local optimization testing (AMD Radeon AI PRO R9700 32GB):

| Parameter | General Chat | Coding/Agent | Description |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Balance creativity and accuracy |
| top_p | 0.95 | 0.95 | Nucleus sampling threshold |
| top_k | 20 | 20 | Truncation sampling |
| repeat_penalty | 1.05 | 1.05 | Repetition penalty |
| presence_penalty | 0 | 0 | No presence penalty |
| context_length | 262144 | 262144 | 128K long context |
| batch_size | 2048 | 2048 | Batch size |
| ubatch_size | 512 | 512 | Micro-batch size |
| flash_attention | auto | auto | Automatic Flash Attention |
| kv_cache | q4_0 | q4_0 | KV cache quantization |
| poll | 0 | 0 | No GPU polling when idle, energy-saving |
| reasoning | auto | auto | Enable reasoning chain (thinking) |
| reasoning_budget | 400 | 400 | Reasoning token budget |
| reasoning_format | deepseek-legacy | deepseek-legacy | Reasoning output format |
| samplers | top_k;top_p;temperature;typ_p | top_k;top_p;temperature;typ_p | Sampler ordering |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP speculative decoding (see MTP section below)** |

> 💡 **Thinking Mode**: This model has built-in Qwen3.8 Thinking (chain-of-thought) capability. Enabled via `--reasoning auto`, the model performs internal reasoning before outputting answers. `reasoning_budget` controls maximum thinking tokens (400 recommended, adjustable 100-1000 based on task complexity). `reasoning-format deepseek-legacy` outputs the thinking process to a separate field without polluting the main output.

## MTP Speculative Decoding (Important Acceleration Feature)

This model includes a built-in MTP (Multi-Token Prediction) speculative decoding layer that can accelerate inference speed by **1.5-2x** when enabled. This is a native feature of the Qwen3.8 architecture, and MoziAI retains the complete MTP weights.

### MTP Principle

MTP trains an additional lightweight prediction head (Draft Model) in the model architecture, used to pre-guess subsequent tokens before the main model's verification, reducing the main model's forward passes and significantly lowering inference latency.

### Enabling MTP in llama.cpp

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Recommended Value | Description |
| --- | --- | --- |
| --spec-type | draft-mtp | Enable MTP speculative decoding |
| --spec-draft-n-max | 2 | Maximum 2 tokens guessed per step (recommended, ~80% acceptance rate) |
| --spec-draft-p-min | 0.75 | Minimum acceptance probability threshold (0.0-1.0, higher = more conservative) |

### MTP Parameter Tuning Guide

| spec-draft-n-max | Acceptance Rate | Use Case |
| --- | --- | --- |
| 1 | ~90% | Most conservative, minimal speed improvement but safest |
| **2** | **~80%** | **Recommended: balances speed and accuracy** |
| 3 | ~71% | General use, noticeable speed improvement |
| 4-5 | ~60-65% | Creative writing, code generation |
| 6 | ~50-55% | Long text output (requires p-min adjustment) |

> ⚠️ **Note**: MTP speculative decoding has no negative impact on output quality (incorrect guesses are corrected by the main model) and only affects inference speed. Start with `spec-draft-n-max` of 2 and adjust based on actual acceptance rate.

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

> 💡 **Disabling MTP**: To disable MTP speculative decoding, remove the three lines containing `--spec-type draft-mtp`, `--spec-draft-n-max 2`, and `--spec-draft-p-min 0.75` from the launch command. Inference speed will decrease by approximately 30-50%, but VRAM usage will be lower.

## VRAM Configuration Guide

| VRAM | Recommended Context | KV Cache | Vision Support | Description |
| --- | --- | --- | --- | --- |
| 20 GB | 128K Full | q4_0 | Full Support | Vision+128K long context, recommended config (~16GB model+KV, ~4GB headroom) |
| 24 GB | 128K Full | q4_0 | Full Support | Vision+128K long context, ample headroom |
| 32 GB+ | 128K Full | q4_0 | Full Support | Vision+128K long context, ample headroom, best configuration |

## Model Download

| Platform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

## License (Important)

This model uses a **custom restrictive license**:

✅ **Allowed**
- Free commercial use: integrate into commercial products or services
- Copy and distribute: copy, download, and analyze as-is

❌ **Prohibited**
- Secondary development: no modification, translation, adaptation, merging, or fine-tuning of the model
- Resale: no selling the model standalone or as part of a product
- Sub-licensing: no granting of any sub-licenses

📋 **Requirements**
- Must retain original copyright notice
- Attribution required: moziAI-27B

See [LICENSE](V3.8/LICENSE) for full terms.

## Disclaimer

This model is provided "as is" without any warranty. Model outputs are for reference only and do not constitute investment advice. Users assume all risks.

## Contact

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
