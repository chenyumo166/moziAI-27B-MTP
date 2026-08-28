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

# MoziAI-27B-3.8 - 可免費本地部署的小而強的多模態AI模型

[English](README.en.md) | [簡體中文](README.zh.md) | 繁體中文 | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## 模型簡介

MoziAI-27B-3.8 是由中國財經大V陳雨墨團隊開發的本地開源多模態AI大模型（增強金融領域、支持視覺、工具調用、消費級顯卡本地部署）。基於開源底座 Qwen3.8-27B（Dense 27B 架構，MIT 許可），結合陳雨墨團隊自主研發的（金融數據 + 金融領域能力 + 訓練方法 + 七維思考體系 + 智能體LOOP機制 + 混合量化算法 MoziSmartBit）。

通過自研 MoziSmartBit 智能量化技術，將270億參數 Dense 模型壓縮至約 13.7 GB，比常規Q4_K_M量化約17GB的體積小3.3GB（約20%），實現幾乎≈FP16 的 **99%精度質量**。

本模型增強了：金融垂直領域應用、金融問答、量化編程、工具調用、通用編程、七維思考能力、LOOP機制，兼容各種agent平台。可通過 OpenClaw/Hermes 執行256K上下文任務，節約雲端token成本，實現 **7x24 小時 token 自由**，確保本地數據隱私安全。

支持 llama.cpp、Ollama、LM Studio 等主流推理框架。**發布日期：2026-08-25** | **版本：V3.8**

## 模型特色

- **金融垂直深度**：深度加強金融問答、量化編程、工具調用
- **MoziSmartBit 智能量化**：自研量化技術，壓縮至約 **13.7 GB**，精度保持 **~99%**
- **消費級部署**：16GB顯存以上即可本地部署，20GB以上可實現完整256K長上下文推理
- **MTP推測解碼**：內置多Token預測層，推理速度提升1.5-2倍
- **多語言支持**：201種語言，中文能力特別優化
- **通用編程**：Python/JS/TS/Go/Rust 等主流語言
- **文章寫作**：研報、分析文章、技術文檔、創意內容
- **視覺理解**：支持多模態視覺，本地截圖輸入
- **推理邏輯增強**：思維鏈訓練，提升推理質量
- **多框架支持**：llama.cpp、Ollama、LM Studio、Jan
- **多 Agent 支持**：OpenClaw、Hermes、Cursor 等 AI IDE 與 Agent 框架

## 核心能力

| 能力領域 | 說明 |
|---------|------|
| 市場分析 | 宏觀/微觀經濟解讀、A股/港股/美股/商品/加密貨幣行情 |
| 財務與研報 | 財報指標解讀、研報摘要、估值預測輔助 |
| 風控與合規 | 風險評估、投資建議合規、監管政策解讀 |
| 量化與策略 | 量化策略設計、金字塔(PEL)量化、回測邏輯 |
| 工具調用 | 實時行情、數據庫、研報檢索等金融數據源 |

## 技術規劃

| 項目 | 參數 |
|------|------|
| 底座模型 | Qwen3.8-27B（Dense架構，混合注意力，MIT許可） |
| 參數規模 | 270億 Dense |
| 量化方式 | MoziSmartBit 智能量化 + GGUF 標準格式 |
| 上下文長度 | 256K（262,144 tokens） |
| 模型體積 | ~13.7 GB |
| 最低顯存 | **16GB+** 可部署（需CPU卸載）；**20GB+** 可流暢運行長上下文；**24GB+** 完整256K + 視覺 |
| 推理框架 | llama.cpp / Ollama / LM Studio / Jan |
| 推理速度 | MTP啟用：R9700 70+ tok/s，MAX+395 CPU 50+ tok/s，MAX+395 GPU 35+ tok/s |
| 開發團隊 | 陳雨墨團隊 |

## 量化格式與模型體積

| 量化格式 | 體積 | 精度 | 說明 |
|---------|------|------|------|
| FP16 | ~54 GB | 100% | 原始精度 |
| **MoziSmartBit** | **~13.7 GB** | **~99%** | **自研智能量化** |
| Q4_K_M | ~17 GB | ~98% | GGUF 標準 4bit |
| Q5_K_M | ~20 GB | ~99% | 更高精度 |
| Q6_K | ~23 GB | ~99.5% | 近無損 |
| Q8_0 | ~31 GB | ~100% | 無損失 |

## MTP 推測解碼

本模型內置 MTP 推測解碼層，開啟後推理速度提升 **1.5-2 倍**。

### 啟用參數

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

| 參數 | 推薦值 | 說明 |
|------|--------|------|
| --spec-type | draft-mtp | 啟用 MTP |
| --spec-draft-n-max | 2 | 每次猜測 2 token（~80% 接受率） |
| --spec-draft-p-min | 0.75 | 最低接受概率 |

## llama.cpp 啟動命令

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

> 💡 **關閉 MTP**：刪除 `--spec-type draft-mtp`、`--spec-draft-n-max 2`、`--spec-draft-p-min 0.75` 三行即可。關閉後速度降低 30-50%，顯存更小。

## 不同顯存配置推薦

| 顯存 | 上下文 | KV 緩存 | 視覺 | 說明 |
|------|--------|---------|------|------|
| 20 GB | 256K | q4_0 | 支持 | 推薦配置 |
| 24 GB | 256K | q4_0 | 完美 | 顯存充裕 |
| 32 GB+ | 256K | q4_0 | 完美 | 最強配置 |

## 基準評測

### 編碼能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 51.7 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 51.2 | 53.4 |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | -- | 63.8 |

### 代理能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 |
| JobBench | **33.4** | 21.8 | 27.6 |
| WebArena-Verified | **64.8** | 48.8 | 55.3 |

### 通用能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| IFBench | **79.5** | 69.1 | 79.1 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 |

## 模型下載

| 平台 | 連結 |
|------|------|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## 快速開始

### 1. 下載

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # 主模型
├── moziAI-27B-3.8-mmproj-F16.gguf              # 視覺投影
└── chat-template-moziai-27B-v38.jinja           # 聊天模板
```

### 2. 啟動

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

### 3. 對話

瀏覽器打開 `http://localhost:8080` 即可開始

## 許可證

採用**自定義限制性許可證**：免費商業使用 ✅ | 二次開發 ❌ | 轉售 ❌

## 免責聲明

本模型按「原樣」提供，不構成投資建議。使用者自行承擔風險。

## 聯絡方式

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 陳雨墨/ chenyumo166. All rights reserved.
