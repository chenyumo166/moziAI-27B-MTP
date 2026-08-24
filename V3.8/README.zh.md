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

# MoziAI-27B-3.8 - 可免费本地部署的小而强的多模态AI模型

[English](README.en.md) | 简体中文 | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## 模型简介

MoziAI-27B-3.8 是由中国财经大V陈雨墨团队开发的本地开源多模态AI大模型（增强金融领域、支持视觉、工具调用、消费级显卡本地部署）。moziAI-27B-3.8 基于开源底座 Qwen3.8-27B（Dense 27B 架构，MIT 许可），结合陈雨墨团队自主研发的（金融数据 + 金融领域能力 + 训练方法 + 七维思考体系 + 智能体LOOP机制 + 混合量化算法 MoziSmartBit）开发而成。

通过自研的 MoziSmartBit 智能量化技术，将270亿参数 Dense 模型压缩至约 13.7 GB，比常规Q4_K_M量化约17GB的模型体积小了3.3GB（约20%）；在精度与体积间取得最优平衡，实现几乎≈FP16 的 **99%的精度质量**。

本模型除了保留AI大模型的通用能力外，还增强了：金融垂直领域应用，金融问答、量化编程、工具调用和通用编程，模型的七维思考能力、LOOP机制，兼容各种agent平台调用。

模型研发者陈雨墨常把本模型用于本地金融数据分析、量化策略研发、市场调研、任何的文章编写、整体项目推进、通用程序编写，OpenClaw/Hermes执行256K上下文的任务。因本地消费级显卡可部署使用，节约大量云端token成本，实现7×24小时token自由并且确保本地数据隐私与安全。

支持 llama.cpp、Ollama、LM Studio 等主流推理框架

**发布日期：2026-08-25** | **版本：V3.8**

## 模型特色

- **金融垂直深度**：深度加强金融问答、量化程序编写、工具调用能力
- **MoziSmartBit 智能量化**：自研的智能量化技术，精度与体积最佳平衡，模型几乎无损压缩至约 **13.7 GB**，精度保持 **~99%**
- **消费级部署**：20GB显存以上的家用消费级显卡即可本地部署，支持最优256K长上下文推理
- **MTP推测解码**：内置多Token预测层，可开启推测解码，推理速度提升1.5-2倍
- **多语言支持**：支持201种语言和方言，中文能力特别优化，兼顾英语、日语、韓语、德语、法语、西班牙语、葡萄牙语等主流语言
- **通用程序编写能力**：支持全栈开发、代码调试、架构设计、脚本编写，覆盖 Python/JS/TS/Go/Rust 等主流语言
- **文章写作能力**：支持多体裁高质量写作，包括研报、分析文章、技术文档、创意内容等
- **视觉理解**：支持多模态视觉，可本地截图进入聊天窗口，模型能够看懂图片内资讯
- **推理逻辑增强**：配合推理逻辑（思维链）进行训练，进一步提升推理质量
- **多框架支持**：兼顾llama.cpp、Ollama、LM Studio、Jan 等主流推理框架
- **多 Agent 平台支持**：深度适合OpenClaw、Hermes、OpenCode、Cursor、Windsurf、Claude Code、Codex 等国内外主流 AI IDE 与 Agent 框架，原生支持工具调用与多轮任务编排，开箱即可

## 核心能力

| 能力领域  | 说明                                         |
| ----- | ------------------------------------------ |
| 市场分析  | 宏观/微观经济解读、A股/港股/美股/商品/加密货币行情与逻辑梳理         |
| 财务与研报| 财报关键指标解读、研报摘要提取、估值与盈利预测辅助                  |
| 风控与合规| 产品风险评估、投资建议合规提示、金融监管政策解读                   |
| 量化与策略| 量化策略思路设计、金字塔（Pyramid/PEL）量化、回测逻辑、因子构建与工具调用 |
| 工具调用  | 可接入实时行情、数据库、研报检索等金融数据源                    |

## 技术规划

| 项目     | 参数                                                                                 |
| ------ | ---------------------------------------------------------------------------------- |
| 底座模型   | Qwen3.8-27B（Dense 架构，混合注意力 16 full + 48 linear，MIT 许可证）                         |
| 参数规模   | 270亿（27B）Dense 架构                                         |
| 量化方式   | 采用自研 MoziSmartBit 智能量化算法 + GGUF 标准格式                                               |
| 上下文长度 | 256K（262,144 tokens）                                                             |
| 模型体积   | ~13.7 GB                                                        |
| 最低显存要求| 20GB显存以上的家用消费级显卡（如 RX 7900 XT 20G、RTX 4060 Ti 16G 需搭配 CPU 卸载），推理 24GB（含视觉 + 长上下文） |
| 推理框架   | llama.cpp / Ollama / LM Studio / Jan                                               |
| 推理速度   | 开启MTP推测解码：AMD R9700显卡可达 70+ token/s，AMD MAX+395 CPU核显可达 50+ token/s，AMD MAX+395 GPU可达 35+ token/s，实现本地token自由输出       |
| 开发团队   | 陈雨墨团队                                                                             |

## 量化格式与模型体积

| 量化格式             | 模型体积          | 精度保持      | 说明                |
| ---------------- | ------------- | --------- | ----------------- |
| FP16（原始）         | ~54 GB       | 100%      | 原始 16bit 精度       |
| **MoziSmartBit** | **~13.7 GB** | **~99%**  | **本模型采用自研智能量化方式** |
| Q4_K_M         | ~17 GB      | ~98%     | GGUF 标准 4bit      |
| Q5_K_M         | ~20 GB     | ~99%     | 更高精度              |
| Q6_K            | ~23 GB     | ~99.5%   | 近无损              |
| Q8_0            | ~31 GB     | ~100%    | 无损失              |

> MoziAI V3.8 采用 MoziSmartBit 智能量化方案，在保持约99%精度的同时，将270亿参数Dense模型压缩至约13.7 GB，压缩比达4.0x，兼顾推理质量与部署门槛，更适合消费级显卡本地部署

## MoziSmartBit 智能量化技术

传统量化方案对所有层使用统一精度，而陈雨墨团队自研的**MoziSmartBit 智能量化**针对 Dense 模型的结构特点，采用智能差异化量化策略，在体积与精度间取得最优平衡，模型质量高于 Q4_K_M 格式，同时体积仅占13.7 GB，压缩比达4.0x，精度保持约99%。

### 压缩效果

- **量化精度损失极小**：训练增益 > 量化损失，训练后的MoziAI-27B 在金融领域文本上下PPL 优于训练前的 bf16 底座，降低了同类 AI 模型的幻觉与困惑。
- **模型体积压缩至 4.0 倍**：从 FP16（~54 GB）压缩至 ~13.7 GB，也大幅小于Q4_K_M的~17 GB，大幅降低显存与存储门槛
- **消费级显卡可部署**：原本需要高端显卡的 27B Dense 大模型，现在 20GB 显存即可流畅部署

### 对比优势

**vs Q4_K_M（~17 GB）**：体积减少约 20%（~13.7 GB），精度优于 Q4_K_M（~99% vs ~98%），显存门槛更低，中端消费级显卡（24GB）即可流畅部署

**vs 原始 FP16（~54 GB）**：体积压缩约 4.0 倍，精度保持约99%，从需要专业级显卡降低到消费级显卡即可本地运行256K长上下文

## 推荐推理参数

基于 llama.cpp 官方推荐参数与本地实测优化（AMD Radeon AI PRO R9700 32GB），推荐参数如下：

| 参数 | 通用聊天 | 编码/Agent | 说明 |
| --- | --- | --- | --- |
| temperature | 0.6 | 0.6 | 平衡创意与准确性 |
| top\_p | 0.95 | 0.95 | 核采样阈值 |
| top\_k | 20 | 20 | 截断采样 |
| repeat\_penalty | 1.05 | 1.05 | 重复惩罚 |
| presence\_penalty | 0 | 0 | 无存在惩罚 |
| context\_length | 262144 | 262144 | 256K 长上下文 |
| batch\_size | 2048 | 2048 | 批处理大小 |
| ubatch\_size | 512 | 512 | 微批次大小 |
| flash\_attention | auto | auto | 自动 Flash Attention |
| kv\_cache | q4\_0 | q4\_0 | KV 缓存量化 |
| poll | 0 | 0 | 闲置不轮询GPU，节能低延迟 |
| reasoning | on | on | 开启推理链（思维链） |
| reasoning\_budget | 400 | 400 | 推理预算 token |
| reasoning\_format | deepseek-legacy | deepseek-legacy | 推理格式 |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | 采样器顺序 |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP推测解码（详见下方MTP章节）** |

> 💡 **思考模式说明**：本模型内置 Qwen3.8 Thinking（思维链）能力。通过 `--reasoning on` 开启，模型会先进行内部推理再输出答案。`reasoning_budget` 控制最大思考token数（400为推荐值，可根据任务复杂度调整100-1000）。`reasoning-format deepseek-legacy` 输出思考过程到独立字段，不污染主输出内容。

## MTP 推测解码（重要加速特性）

本模型内置 MTP（Multi-Token Prediction）推测解码层，开启后推理速度可提升 **1.5-2 倍**。这是 Qwen3.8 架构的原生特性，MoziAI 保留了完整的 MTP 权重。

### MTP 原理

MTP 在模型架构中额外训练了一个轻量级的预测头（Draft Model），用于在主模型验证前预先猜测后续 token，从而减少主模型的 forward 次数，大幅降低推理延迟。

### llama.cpp 开启 MTP 的参数

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| 参数 | 推荐值 | 说明 |
| --- | --- | --- |
| --spec-type | draft-mtp | 启用 MTP 推测解码 |
| --spec-draft-n-max | 2 | 每次最多猜测 2 个 token（推荐值，接受率最高约80%） |
| --spec-draft-p-min | 0.75 | 最低接受概率阈值（0.0-1.0，越大越保守） |

### MTP 参数调整建议

| spec-draft-n-max | 接受率 | 适用场景 |
| --- | --- | --- |
| 1 | ~90% | 最保守，速度提升最小但最安全 |
| **2** | **~80%** | **推荐：平衡速度与准确率** |
| 3 | ~71% | 通用场景，速度提升明显 |
| 4-5 | ~60-65% | 创意写作、代码生成 |
| 6 | ~50-55% | 纯文本长输出（需配合 p-min 调整） |

> ⚠️ **注意**：MTP 推测解码对输出质量无负面影响（猜测错误会被主模型纠正），仅影响推理速度。`spec-draft-n-max` 建议从 2 开始，根据实际接受率调整。

## llama.cpp 启动命令

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99 -t 28 \
  --batch-size 2048 --ubatch-size 512 \
  --flash-attn auto \
  --cache-type-k q4_0 --cache-type-v q4_0 --kv-unified \
  --poll 0 \
  --reasoning on --reasoning-budget 400 --reasoning-format deepseek-legacy \
  --spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75 \
  --host 0.0.0.0 --port 8080 \
  --temp 0.6 --top-p 0.95 --top-k 20
```

> 💡 **关闭 MTP**：如需关闭 MTP 推测解码，删除启动命令中的 `--spec-type draft-mtp`、`--spec-draft-n-max 2`、`--spec-draft-p-min 0.75` 三行即可。关闭后推理速度会降低约 30-50%，但显存占用更小。

## 不同显存配置推荐

由于使用者显卡配置差异较大，以下为不同显存下的推荐参数：

| 显存 | 推荐上下文 | KV 缓存 | 视觉支持 | 说明 |
| --- | --- | --- | --- | --- |
| 20 GB | 256K 满配 | q4\_0 | 完美支持 | 视觉+256K长上下文，推荐配置（模型+KV约需16GB，显存余量~4GB） |
| 24 GB | 256K 满配 | q4\_0 | 完美支持 | 视觉+256K长上下文，显存余量充足 |
| 32 GB+ | 256K 满配 | q4\_0 | 完美支持 | 视觉+256K长上下文，显存余量充足，最强配置 |

**NVIDIA 显卡参考表**

| 显存 | 显卡型号 |
| --- | --- |
| 16 GB | RTX 4060 Ti（需搭配 CPU 卸载）|
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD 显卡参考表**

| 显存 | 显卡型号 |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel 显卡参考表**

| 显存 | 显卡型号 |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50（需搭配 CPU 卸载）|

**CPU共享内存核显设备参考表**

| 显存 | 处理器型号 |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395（Radeon 8060S 核显） |
| 128 GB | NVIDIA RTX Spark（Blackwell RTX GPU） |

> 💡 **提示**：只要显存满足以上要求即可使用，不限品牌型号，支持NVIDIA / AMD / Intel 各品牌独立显卡，也支持128GB 统一内存的核显 CPU。
> 💡 **提示**：上下文越长，占用显存越多。如果出现显存不足（OOM），请逐步降低 `-c` 参数值。使用 `--fit on` 参数可让 llama.cpp 自动调整层数适配显存。

## Ollama 部署

```bash
# 建立 Modelfile
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf

PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 262144
PARAMETER num_gpu 99

# 载入视觉投影文件（可选，启用视觉能力）
PARAMETER mmproj ./moziAI-27B-3.8-mmproj-F16.gguf

# 载入聊天模板（推荐）
PARAMETER chat_template_file ./chat-template-moziai-27B-v38.jinja

# 建置并运行
ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

> 💡 Ollama 中 `mmproj` 和 `chat_template_file` 参数需确认具体版本支持情况，建议优先使用 llama.cpp 部署以获得完整功能支持

## LM Studio / Jan 部署

直接在 LM Studio / Jan 中搜索 `moziAI`，选择 Q4_K_M 量化版本下载即可

## 基准评测

MoziAI-27B-3.8 基于 Qwen3.8-27B（Dense 27B）底座微调。以下为通用能力基准分数（MoziAI 金融垂直领域为核心优化方向，通用能力基准分数与底座 Qwen3.8-27B 一致）：

### 编码能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73.0 | 63.4 | 64.0 | 51.7 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 51.2 | 53.4 |
| NL2Repo-Bench | 42.3 | 36.2 | 41.1 | -- | 47.6 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | -- | 63.8 |

### 代理能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 | -- | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- | -- |
| Agents' Last Exam (Score) | **42.9** | 27.3 | 33.6 | -- | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | -- | 62.0 |

### 通用能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79.5** | 69.1 | 79.1 | 77.0 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | 83.5 | **91.3** |

### 多模态能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94.6** | 85.1 | 90.3 | -- | 65.5 |
| BabyVision (With CI) | **85.6** | 28.9 | 70.4 | -- | 12.6 |
| CharXiv RQ (With CI) | **90.2** | 78.4 | 85.8 | -- | 66.0 |
| OmniDocBench 1.5 | 91.1 | 89.4 | **91.4** | 75.8 | 86.6 |
| RealWorldQA | 85.9 | 84.1 | **86.9** | -- | 73.9 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- | -- |

> MoziAI-27B-3.8 通用能力基准分数与底座 Qwen3.8-27B 一致。金融垂直领域为 MoziAI 的核心优化方向，在财报解读、量化策略、风控合规、agent管理工具调用等场景下表现显著优于通用模型。Qwen3.6/Qwen3.7/Muse-Glimmer/Opus4.6 数据为官方公开评测结果。

## 模型下载

由于模型文件较大（~13.7 GB），模型权重托管于多个社群平台：

| 平台 | 地址 |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope（魔搭） | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

> 💡 **LM Studio 用户**：可直接在 [LM Studio](https://lmstudio.ai) 中搜索 `moziAI` 并一键下载，无需手动下载文件

> 💡 **下载提示**：请点击上方链接进入 HuggingFace 仓库，在 "Files and versions" 标签下下载 V3.8 目录下的所有文件（主模型、视觉投影、聊天模板），确保三个文件放在同一目录下

⚠️ **重要：视觉能力需要额外载入mmproj 文件**

本模型支持多模态视觉，视觉投影文件（mmproj）已包含在版本目录中

- **视觉文件**：`moziAI-27B-3.8-mmproj-F16.gguf`（约 927 MB，BF16 精度）
- **放置位置**：与 GGUF 模型文件放在同一版本目录下
- **载入方式**：启动 llama-server 时通过 `--mmproj` 参数载入

> 不载入视觉文件将丧失图像理解能力，仅保留纯文本对话能力

## 快速开始

### 1. 下载模型文件

在 HuggingFace / ModelScope 下载 V3.8 目录下的所有文件到本地：

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # 主模型（必选）
├── moziAI-27B-3.8-mmproj-F16.gguf              # 视觉投影（可选）
└── chat-template-moziai-27B-v38.jinja           # 聊天模板（推荐）
```

### 2. 启动推理服务

完整的推荐配置启动命令请参考上方 [llama.cpp 启动命令](#llamacpp-启动命令) 章节

最简启动（仅核心参数）：

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

> 需要视觉能力时加上 `--mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf`

### 3. 开始使用

浏览器打开 `http://localhost:8080` 即可开始对话

### 目录结构

```
moziAI-27B/
├── README.md              # 本文件（中文说明书）
├── README.en.md           # 说明书的英文版本
├── LICENSE                # 许可证
├── V3.8/                  # V3.8 版本
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # 主模型
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # 视觉投影
│   └── chat-template-moziai-27B-v38.jinja         # 聊天模板
```

## SEO 关键词

金融AI大模型、AI大模型、本地开源模型、端侧模型、量化程序编写、MoziSmartBit、智能量化、GGUF量化、Dense模型、本地开源大模型、本地部署、金融AI、工具调用、Agent、llama.cpp、Ollama、GGUF、Q4\_K\_M、Qwen3.8-27B、金融垂直领域、开源模型、MTP推测解码、256K长上下文、多模态、本地LLM、边缘AI、自托管AI、speculative decoding、self-hosted AI、local LLM、edge AI、Chinese financial AI、Qwen3.8 fine-tune、tool-calling、vision model、open-source LLM、consumer GPU deployment、intelligent quantization

## 许可证（重要事项）

本模型采用**自定义限制性许可证**，具体条款如下：

✅ **允许**
- 免费商业使用：可免费整合到您的商业产品或服务中
- 复制和分发：可原样复制、下载、分析

❌ **禁止**
- 二次开发：不得修改、翻译、改编、合并、微调本模型或其任何部分
- 转售售卖：不得将本模型单独或作为产品组成部分进行售卖
- 再许可：不得就本模型授予任何从属许可

📋 **要求**
- 使用时必须保留原始版权声明
- 注明来源：moziAI-27B

详细许可证条款请参阅 [LICENSE](LICENSE) 文件

## 免责声明

本模型按「原样」提供，不提供任何形式的保证。模型输出仅供参考，不构成投资建议。使用者需自行承担使用风险。

## 联系方式

- **HuggingFace**：[@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**：[@chenyumo166](https://github.com/chenyumo166)
- **微博**：[@rimochen](https://weibo.com/rimochen)
- **E-mail**：263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
