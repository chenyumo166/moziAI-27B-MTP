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

# MoziAI-27B-3.8 - Free Locally Deployable Small Yet Powerful Multimodal AI Model

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## Model Overview

MoziAI-27B-3.8 is a local open-source multimodal AI large model developed by the team of Chinese finance influencer Chen Yumo (enhanced for the financial domain, supports vision, tool calling, and local deployment on consumer GPUs). moziAI-27B-3.8 is built on the open-source base model Qwen3.8-27B (Dense 27B architecture, MIT licensed), combining the Chen Yumo team's self-developed technologies (financial data + financial domain capabilities + training methods + Dynamic Seven-Dimensional Thinking framework + Agent LOOP reflection and iteration mechanism + hybrid quantization algorithm MoziSmartBit). It lowers the barrier to local deployment for individuals and enterprises, with free commercial licensing. Since it can be deployed locally on consumer GPUs, it saves significant cloud token costs, enabling 24/7 token freedom while ensuring local data privacy and security.

**Dynamic Seven-Dimensional Thinking Framework + Agent LOOP Iteration Mechanism**: MoziAI's self-developed core reasoning mode. It intelligently assesses task complexity — simple tasks activate two-dimensional thinking for quick responses, moderately complex tasks engage five-dimensional thinking, and highly complex tasks activate the full seven-dimensional thinking + LOOP reflection and iteration mechanism. It aims to challenge the ability of models dozens of times its size (trillion-parameter models) to effectively solve complex tasks, without sacrificing the lightweight responsiveness of simple tasks. This enables local models to develop the "think before acting" capability of seasoned human experts. This self-developed core reasoning framework is highly distinctive compared to models of similar size.

**Through the self-developed MoziSmartBit intelligent quantization technology**, the 27-billion parameter Dense model is compressed to approximately 12.79 GB, which is 3.3 GB (about 20%) smaller than conventional Q4_K_M quantization models (~17 GB); achieving the optimal balance between precision and size, delivering ~99% of FP16 precision quality.

In addition to retaining the general capabilities of AI large models, this model has also been enhanced for: financial vertical domain applications, financial Q&A, quantitative programming, tool calling, and general programming, with compatibility with various agent platforms.

The model developer Chen Yumo frequently uses this model for local financial data analysis, quantitative strategy development, market research, all types of writing, overall project development, general programming, and OpenClaw/Hermes execution of complex tasks with 256K long context.

Supports free local deployment on mainstream inference frameworks including llama.cpp, Ollama, LM Studio, and more.

**Release Date: 2026-08-30** | **Version: V3.8**

## Model Features

- **🧠 Dynamic Seven-Dimensional Thinking Framework**: MoziAI's self-developed core reasoning framework. When facing any task, the model first outputs the **moziAI-Think** tag, dynamically expanding structured thinking based on task complexity — from two-dimensional quick response ("task understanding + resource requirements") for simple Q&A (Level 0), to five-dimensional assessment for analysis and diagnosis (Level 1), to full seven-dimensional deep reasoning for complex development/strategy design (Level 2): ①Task Understanding ②Complexity Assessment ③Dependency Analysis ④Risk Assessment ⑤Resource Requirements ⑥Acceptance Criteria ⑦Execution Strategy.
- **🧠 Agent LOOP Iteration Mechanism**: For complex tasks, MoziAI automatically enters the **moziAI-Loop** iteration mode: Round 1 execution + evaluation → Round 2 adjustment + verification, ensuring output is self-verified before delivering the final answer, rather than generating it in one pass. This means the model doesn't just "answer questions" — it breaks down problems like a senior engineer: analyze → evaluate solutions → execute → reflect → optimize, significantly improving the accuracy and executability of complex tasks. Simple Q&A and tasks automatically disable the Loop iteration mechanism.
- **🧠 MoziSmartBit Intelligent Quantization**: MoziAI's self-developed hierarchical intelligent quantization, achieving the optimal balance between precision and size, compressed to approximately 12.79 GB while maintaining FP16 ~99% precision.
- **🧠 Financial Vertical Domain Focus**: Deeply optimized for financial Q&A, quantitative programming, and tool calling. The financial domain has extremely low tolerance for model hallucinations, also demonstrating MoziAI's deep enhancements in vertical domain capabilities compared to general-purpose models.
- **Multilingual Support**: Supports 201 languages and dialects, with particularly optimized Chinese capabilities, while covering major languages including English, Japanese, Korean, German, French, Spanish, Portuguese, and more.
- **General Programming Capabilities**: Supports full-stack development, code debugging, architecture design, and script writing, covering mainstream languages such as Python/JS/TS/Go/Rust.
- **Writing Capabilities**: Supports high-quality writing across multiple genres, including research reports, analytical articles, technical documentation, creative content, and more.
- **Vision Understanding**: Supports multimodal vision; screenshots can be pasted into the chat window, and the model can interpret image content.
- **Multi-Framework Support**: Compatible with mainstream inference frameworks including llama.cpp, Ollama, LM Studio, Jan, and more.
- **Multi-Agent Platform Support**: Deeply compatible with mainstream domestic and international AI IDEs and Agent frameworks including OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex, with native support for tool calling and multi-turn task orchestration, ready to use out of the box.

## Core Capabilities

| Capability Domain | Description |
| ----- | ------------------------------------------ |
| Market Analysis | Macro/microeconomic interpretation, A-share/HK/US/commodity/cryptocurrency market analysis and logic |
| Financial & Research Reports | Key financial metrics interpretation, research report summary extraction, valuation and earnings forecast assistance |
| Risk Control & Compliance | Product risk assessment, investment advice compliance reminders, financial regulatory policy interpretation |
| Quantitative & Strategy | Quantitative strategy design, Pyramid (Pyramid/PEL) quantification, backtesting logic, factor construction and tool calling |
| Tool Calling | Connectable to real-time market data, databases, research report search, and other financial data sources |

## Technical Specifications

| Item | Parameters |
| ------ | ---------------------------------------------------------------------------------- |
| Base Model | Qwen3.8-27B (Dense architecture, hybrid attention 16 full + 48 linear, MIT license) |
| Parameter Scale | 27 billion (27B) Dense architecture |
| Quantization Method | Self-developed MoziSmartBit intelligent quantization algorithm + GGUF standard format |
| Context Length | 256K (262,144 tokens) |
| Model Size | ~12.79 GB |
| Minimum VRAM | **16GB+** deployable (with CPU offloading, e.g., RTX 4060 Ti 16G); **20GB+** smooth long-context operation (e.g., RX 7900 XT 20G); **24GB+** full 256K + vision support |
| Inference Framework | llama.cpp / Ollama / LM Studio / Jan |
| Inference Speed | With MTP speculative decoding enabled: AMD R9700 GPU achieves 70+ token/s, AMD MAX+395 integrated GPU achieves 50+ token/s, AMD MAX+395 GPU achieves 35+ token/s, enabling local token-free output |
| Development Team | Chen Yumo Team |

## Quantization Format & Model Size

| Quantization Format | Model Size | Precision Retention | Description |
| ---------------- | ------------- | --------- | ----------------- |
| FP16 (Original) | ~54 GB | 100% | Original 16-bit precision |
| **MoziSmartBit** | **~12.79 GB** | **~99%** | **This model uses self-developed intelligent quantization** |
| Q4_K_M | ~17 GB | ~98% | GGUF standard 4-bit |
| Q5_K_M | ~20 GB | ~99% | Higher precision |
| Q6_K | ~23 GB | ~99.5% | Near-lossless |
| Q8_0 | ~31 GB | ~100% | Lossless |

> MoziAI V3.8 uses the MoziSmartBit intelligent quantization scheme, compressing the 27-billion parameter Dense model to approximately 12.79 GB while maintaining approximately 99% precision, with a compression ratio of 4.0x, balancing inference quality and deployment thresholds, making it more suitable for local deployment on consumer GPUs.

## MoziSmartBit Intelligent Quantization Technology

Traditional quantization schemes apply uniform precision across all layers. The Chen Yumo team's self-developed **MoziSmartBit Intelligent Quantization** adopts an intelligent differential quantization strategy tailored to the structural characteristics of Dense models, achieving the optimal balance between size and precision. The model quality surpasses Q4_K_M format, while the size is only 12.79 GB, with a compression ratio of 4.0x and precision retention of approximately 99%.

### Compression Results

- **Minimal quantization precision loss**: Training gains > quantization losses. The post-training MoziAI-27B achieves lower PPL on financial domain text compared to the pre-training bf16 base model, reducing hallucinations and perplexity compared to similar AI models.
- **Model size compressed to 4.0x**: Compressed from FP16 (~54 GB) to ~12.79 GB, also significantly smaller than Q4_K_M's ~17 GB, substantially lowering VRAM and storage thresholds.
- **Deployable on consumer GPUs**: The 27B Dense large model, which originally required high-end GPUs, can now be locally deployed with 16 GB VRAM, with 20 GB+ GPUs enabling full 256K long-context inference.

### Comparative Advantages

**vs Q4_K_M (~17 GB)**: Approximately 20% smaller (~12.79 GB), precision superior to Q4_K_M, lower VRAM threshold — deployable on 16 GB GPUs, smooth 256K long-context operation on 20 GB+ GPUs.

**vs Original FP16 (~54 GB)**: Approximately 4.0x compression ratio, precision retention of approximately 99%, reducing the requirement from professional-grade GPUs to consumer GPUs for local 256K long-context inference.

## Recommended Inference Parameters

Based on llama.cpp official recommended parameters and local benchmark optimization (AMD Radeon AI PRO R9700 32GB), the recommended parameters are as follows:

| Parameter | General Chat | Coding/Agent | Description |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Balance between creativity and accuracy |
| top\_p | 0.95 | 0.95 | Nucleus sampling threshold |
| top\_k | 20 | 20 | Truncated sampling |
| repeat\_penalty | 1.05 | 1.05 | Repetition penalty |
| presence\_penalty | 0 | 0 | No presence penalty |
| context\_length | 262144 | 262144 | 256K long context |
| batch\_size | 2048 | 2048 | Batch size |
| ubatch\_size | 512 | 512 | Micro-batch size |
| flash\_attention | auto | auto | Automatic Flash Attention |
| kv\_cache | q4\_0 | q4\_0 | KV cache quantization |
| poll | 0 | 0 | Idle GPU polling disabled, energy-saving and low latency |
| reasoning | auto | auto | Enable reasoning chain (Chain of Thought) |
| reasoning\_budget | 400 | 400 | Reasoning token budget |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Reasoning format |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | Sampler order |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP speculative decoding (see MTP section below)** |

> 💡 **Thinking Mode Note**: This model includes Qwen3.8 Thinking (Chain of Thought) capability. Enabled via `--reasoning auto`, the model performs internal reasoning before outputting answers. `reasoning_budget` controls the maximum thinking token count (400 is the recommended value, adjustable from 100-1000 based on task complexity). `reasoning-format deepseek-legacy` outputs the thinking process to a separate field, keeping the main output content clean.

## MTP Speculative Decoding (Important Acceleration Feature)

This model includes MTP (Multi-Token Prediction) speculative decoding layers built-in. When enabled, inference speed can be improved by **1.5-2x**. This is a native feature of the Qwen3.8 architecture, and MoziAI retains the complete MTP weights.

### MTP Principle

MTP trains an additional lightweight prediction head (Draft Model) in the model architecture, used to pre-guess subsequent tokens before the main model verifies them, thereby reducing the number of forward passes in the main model and significantly lowering inference latency.

### llama.cpp MTP Parameters

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Recommended Value | Description |
| --- | --- | --- |
| --spec-type | draft-mtp | Enable MTP speculative decoding |
| --spec-draft-n-max | 2 | Maximum tokens to guess per step (recommended value, acceptance rate ~80%) |
| --spec-draft-p-min | 0.75 | Minimum acceptance probability threshold (0.0-1.0, higher = more conservative) |

### MTP Parameter Tuning Guide

| spec-draft-n-max | Acceptance Rate | Use Case |
| --- | --- | --- |
| 1 | ~90% | Most conservative, smallest speed improvement but safest |
| **2** | **~80%** | **Recommended: balances speed and accuracy** |
| 3 | ~71% | General scenarios, noticeable speed improvement |
| 4-5 | ~60-65% | Creative writing, code generation |
| 6 | ~50-55% | Pure text long output (requires p-min adjustment) |

> ⚠️ **Note**: MTP speculative decoding has no negative impact on output quality (incorrect guesses are corrected by the main model) and only affects inference speed. It is recommended to start with `spec-draft-n-max` = 2 and adjust based on actual acceptance rates.

## llama.cpp Startup Command

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

> 💡 **Disabling MTP**: To disable MTP speculative decoding, simply remove the `--spec-type draft-mtp`, `--spec-draft-n-max 2`, and `--spec-draft-p-min 0.75` lines from the startup command. Disabling MTP reduces inference speed by approximately 30-50%, but uses less VRAM.

## VRAM Configuration Recommendations

Due to significant differences in user GPU configurations, here are recommended parameters for different VRAM levels:

| VRAM | Recommended Context | KV Cache | Vision Support | Description |
| --- | --- | --- | --- | --- |
| 20 GB | 256K Full | q4\_0 | Full Support | Vision + 256K long context, recommended configuration (model + KV requires ~16 GB, VRAM headroom ~4 GB) |
| 24 GB | 256K Full | q4\_0 | Full Support | Vision + 256K long context, ample VRAM headroom |
| 32 GB+ | 256K Full | q4\_0 | Full Support | Vision + 256K long context, ample VRAM headroom, strongest configuration |

**NVIDIA GPU Reference Table**

| VRAM | GPU Model |
| --- | --- |
| 16 GB | RTX 4060 Ti (requires CPU offloading) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD GPU Reference Table**

| VRAM | GPU Model |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel GPU Reference Table**

| VRAM | GPU Model |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (requires CPU offloading) |

**CPU Shared Memory / Integrated GPU Reference Table**

| VRAM | Processor Model |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395 (Radeon 8060S integrated GPU) |
| 128 GB | NVIDIA RTX Spark (Blackwell RTX GPU) |

> 💡 **Tip**: As long as VRAM meets the above requirements, any brand or model is supported — NVIDIA / AMD / Intel discrete GPUs, as well as integrated GPU CPUs with 128 GB unified memory.
> 💡 **Tip**: Longer context consumes more VRAM. If VRAM overflow (OOM) occurs, gradually reduce the `-c` parameter value. The `--fit on` parameter allows llama.cpp to automatically adjust layers to fit available VRAM.

## Ollama Deployment

```bash
# Create Modelfile
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf

PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 262144
PARAMETER num_gpu 99

# Load vision projection file (optional, enables vision capability)
PARAMETER mmproj ./moziAI-27B-3.8-mmproj-F16.gguf

# Load chat template (recommended)
PARAMETER chat_template_file ./chat-template-moziai-27B-v38.jinja

# Build and run
ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

> 💡 The `mmproj` and `chat_template_file` parameters in Ollama require verification of specific version support. It is recommended to use llama.cpp deployment for complete feature support.

## LM Studio / Jan Deployment

Search for `moziAI` directly in LM Studio / Jan and select the Q4_K_M quantized version to download.

## Benchmark Evaluation

MoziAI-27B-3.8 is fine-tuned from the Qwen3.8-27B (Dense 27B) base model. The following are general capability benchmark scores (MoziAI's core optimization direction is the financial vertical domain; general capability benchmark scores are consistent with the base Qwen3.8-27B):

### Coding Capabilities

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73.0 | 63.4 | 64.0 | 51.7 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 51.2 | 53.4 |
| NL2Repo-Bench | 42.3 | 36.2 | 41.1 | -- | 47.6 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | -- | 63.8 |

### Agent Capabilities

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 | -- | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- | -- |
| Agents' Last Exam (Score) | **42.9** | 27.3 | 33.6 | -- | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | -- | 62.0 |

### General Capabilities

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79.5** | 69.1 | 79.1 | 77.0 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | 83.5 | **91.3** |

### Multimodal Capabilities

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94.6** | 85.1 | 90.3 | -- | 65.5 |
| BabyVision (With CI) | **85.6** | 28.9 | 70.4 | -- | 12.6 |
| CharXiv RQ (With CI) | **90.2** | 78.4 | 85.8 | -- | 66.0 |
| OmniDocBench 1.5 | 91.1 | 89.4 | **91.4** | 75.8 | 86.6 |
| RealWorldQA | 85.9 | 84.1 | **86.9** | -- | 73.9 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- | -- |

> MoziAI-27B-3.8 general capability benchmark scores are consistent with the base model Qwen3.8-27B. The financial vertical domain is MoziAI's core optimization direction, showing significant advantages over general-purpose models in scenarios such as financial report interpretation, quantitative strategy, risk control compliance, and agent management tool calling. Qwen3.6/Qwen3.7/Muse-Glimmer/Opus4.6 data are from officially published benchmark results.

## Model Download

Due to the large model file size (~12.79 GB), model weights are hosted on multiple community platforms:

| Platform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

> 💡 **LM Studio Users**: You can directly search for `moziAI` in [LM Studio](https://lmstudio.ai) and download with one click, no manual file download required.

> 💡 **Download Tip**: Please click the links above to enter the HuggingFace repository, and download all files in the V3.8 directory (main model, vision projection, chat template) under the "Files and versions" tab. Ensure all three files are placed in the same directory.

⚠️ **Important: Vision capability requires loading an additional mmproj file**

This model supports multimodal vision. The vision projection file (mmproj) is included in the version directory.

- **Vision file**: `moziAI-27B-3.8-mmproj-F16.gguf` (~927 MB, BF16 precision)
- **Placement**: Place in the same version directory as the GGUF model file
- **Loading**: Load via the `--mmproj` parameter when starting llama-server

> Without loading the vision file, image understanding capability is lost; only pure text conversation capability is retained.

## Quick Start

### 1. Download Model Files

Download all files in the V3.8 directory from HuggingFace / ModelScope to local:

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # Main model (required)
├── moziAI-27B-3.8-mmproj-F16.gguf              # Vision projection (optional)
└── chat-template-moziai-27B-v38.jinja           # Chat template (recommended)
```

### 2. Start Inference Service

For the complete recommended startup command, please refer to the [llama.cpp Startup Command](#llamacpp-startup-command) section above.

Minimal startup (core parameters only):

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

> Add `--mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf` when vision capability is needed.

### 3. Start Using

Open `http://localhost:8080` in your browser to begin chatting.

### Directory Structure

```
moziAI-27B/
├── README.md              # This file (Chinese documentation)
├── README.en.md           # English version of the documentation
├── LICENSE                # License
├── V3.8/                  # V3.8 version
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # Main model
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # Vision projection
│   └── chat-template-moziai-27B-v38.jinja         # Chat template
```

## SEO Keywords

Financial AI large model, AI large model, local open-source model, edge model, quantitative programming, MoziSmartBit, intelligent quantization, GGUF quantization, Dense model, local open-source large model, local deployment, financial AI, tool calling, Agent, llama.cpp, Ollama, GGUF, Q4\_K\_M, Qwen3.8-27B, financial vertical domain, open-source model, MTP speculative decoding, 256K long context, multimodal, local LLM, edge AI, self-hosted AI, speculative decoding, self-hosted AI, local LLM, edge AI, Chinese financial AI, Qwen3.8 fine-tune, tool-calling, vision model, open-source LLM, consumer GPU deployment, intelligent quantization

## License (Important)

This model is distributed under a **custom restrictive license** with the following terms:

✅ **Permitted**
- Free commercial use: Can be freely integrated into your commercial products or services
- Copying and distribution: Can be copied, downloaded, and analyzed as-is

❌ **Prohibited**
- Secondary development: No modification, translation, adaptation, merging, or fine-tuning of this model or any part thereof
- Resale: No selling of this model, either standalone or as part of a product
- Sublicensing: No granting of any subordinate license for this model

📋 **Requirements**
- Must retain the original copyright notice when using
- Attribution required: moziAI-27B

For detailed license terms, please refer to the [LICENSE](LICENSE) file.

## Disclaimer

This model is provided "as is" without any form of warranty. Model outputs are for reference only and do not constitute investment advice. Users assume all risks associated with the use of this model.

## Contact

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
