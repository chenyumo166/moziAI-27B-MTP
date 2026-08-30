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

# MoziAI-27B-3.8 — 可免費本地部署的小而強的多模態 AI 模型

[English](README.en.md) | [简体中文](README.zh.md) | 繁體中文 | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

**發布日期：2026-08-30** · **版本：V3.8**

---

## 📑 目錄

- [1. 模型概述](#1-模型概述)
- [2. 模型特色](#2-模型特色) — 動態七維思考 / LOOP / MoziSmartBit / 金融聚焦
- [3. 版本升級說明](#3-版本升級說明)
- [4. 核心能力](#4-核心能力)
- [5. 技術規格](#5-技術規格)
- [6. ⚡ 快速開始](#6--快速開始3-個檔案--100-啟用最佳推理能力) — **三件套下載**
- [7. 模型下載](#7-模型下載)
- [8. 啟動命令](#8-啟動命令)
- [9. 推薦推理參數](#9-推薦推理參數)
- [10. 量化格式對比](#10-量化格式對比)
- [11. MTP 推測解碼](#11-mtp-推測解碼重要加速特性)
- [12. 顯存配置推薦](#12-顯存配置推薦)
- [13. 部署方式](#13-部署方式)
- [14. 基準評測](#14-基準評測)
- [15. 許可證](#15-許可證)
- [16. 聯絡方式](#16-聯絡方式)

---

## 1. 模型概述

MoziAI-27B-3.8 是由中國財經大V陳雨墨團隊開發的本地開源多模態AI大模型，基於開源底座 **Qwen3.8-27B**（Dense 27B 架構，MIT 許可），結合團隊自主研發的金融資料 + 金融領域能力 + 動態七維思考體系 + 智慧體LOOP反思迭代機制 + MoziSmartBit混合量化演算法開發而成。本模型降低個人與企業的本地部署門檻，授權**免費商用**，在消費級顯示卡上即可本地部署，節約大量雲端 token 成本，實現 7×24 小時 token 自由並確保本地資料隱私與安全。

---

## 2. 模型特色

### 🧠 動態七維思考體系

MoziAI 自研的核心推理框架。面對任何任務，模型先輸出 **moziAI-Think** 標記，依任務複雜度動態展開結構化思考：

| 級別 | 適用場景 | 典型任務 | 展開維度 |
| --- | --- | --- | --- |
| **Level 0** | 簡單問答 | 術語解釋、事實查詢、翻譯、摘要 | ①理解任務 ⑤資源需求（兩維速答） |
| **Level 1** | 分析診斷 | 市場調研、文案編寫、資料分析、研報解讀、策略評估 | ①②③⑤⑥ 五維評估 |
| **Level 2** | 複雜開發/策略 | 程式碼開發、架構設計、量化策略開發、多步工作流、系統設計 | ①②③④⑤⑥⑦ 全七維深度推演 |

> 七維：①理解任務 ②複雜度評估 ③依賴關係 ④風險評估 ⑤資源需求 ⑥驗收標準 ⑦執行策略

### 🔄 智慧體 LOOP 迭代機制

複雜任務自動進入 **moziAI-Loop** 迭代模式：**第 1 輪執行+評估 → 第 2 輪調整+驗證**，確保輸出經過自我校驗後才給出最終答案。模型像資深工程師一樣「拆解問題 → 評估方案 → 執行 → 反思 → 優化」，顯著提升複雜任務的準確性與可執行性。簡單問答和任務則自動關閉 Loop。

### 📦 MoziSmartBit 智慧量化

自研分層智慧量化，270 億參數 Dense 模型壓縮至約 **13.7 GB**，比常規 Q4_K_M（~17 GB）小約 3.3 GB（~20%），保持 FP16 **~99%** 精度。傳統量化對所有層使用統一精度，MoziSmartBit 針對 Dense 模型結構特點採用智慧差異化策略，精度優於 Q4_K_M。

### 💰 金融垂直領域聚焦

針對金融問答、量化程式設計和工具呼叫的深度最佳化。金融領域對模型幻覺容忍度極低，MoziAI 在該領域的表現顯著優於同等體積的通用模型。

### 🌐 其他特性

- **多語言支援**：201 種語言和方言，中文能力特別最佳化
- **通用程式設計**：全端開發、程式碼除錯、架構設計，涵蓋 Python/JS/TS/Go/Rust
- **文章寫作**：研報、分析文章、技術文件、創意內容等多體裁高品質寫作
- **視覺理解**：多模態視覺，支援本地截圖理解圖片內容
- **多框架支援**：llama.cpp / Ollama / LM Studio / Jan
- **多 Agent 支援**：OpenClaw / Hermes / Cursor / Claude Code / Codex 等，原生工具呼叫與多輪任務編排

---

## 3. 版本升級說明

本次版本升級主要強化了：moziAI 自研的動態七維思考 + LOOP 迭代的推理模式，使其更智慧地識別任務複雜度，複雜任務的完成率更高，提升"先想後做"的能力。

moziAI 會保持活躍的版本升級迭代更新頻率，確保緊隨未來人工智慧的發展，並不斷透過自研技術，讓本地 AI 模型可輕量化部署，能力越來越強。

---

## 4. 核心能力

| 能力領域 | 說明 |
| --- | --- |
| 市場分析 | 宏觀/微觀經濟解讀、A股/港股/美股/商品/加密貨幣行情與邏輯梳理 |
| 財務與研報 | 財報關鍵指標解讀、研報摘要提取、估值與盈利預測輔助 |
| 風控與合規 | 產品風險評估、投資建議合規提示、金融監管政策解讀 |
| 量化與策略 | 量化策略思路設計、金字塔（Pyramid/PEL）量化、回測邏輯、因子建構與工具呼叫 |
| 工具呼叫 | 可接入即時行情、資料庫、研報檢索等金融資料來源 |

---

## 5. 技術規格

| 項目 | 參數 |
| --- | --- |
| 底座模型 | Qwen3.8-27B（Dense 架構，混合注意力 16 full + 48 linear，MIT 許可證） |
| 參數規模 | 270 億（27B）Dense 架構 |
| 量化方式 | 自研 MoziSmartBit 智慧量化 + GGUF 標準格式 |
| 上下文長度 | 128K（262,144 tokens） |
| 模型體積 | ~13.7 GB |
| 最低顯存 | **16GB+** 可部署（CPU 卸載）；**20GB+** 流暢長上下文；**24GB+** 完整 128K + 視覺 |
| 推理框架 | llama.cpp / Ollama / LM Studio / Jan |
| 推理速度 | MTP 推測解碼下：R9700 達 70+ tok/s，MAX+395 內顯達 50+ tok/s，GPU 達 35+ tok/s |
| 開發團隊 | 陳雨墨團隊 |

---

## 6. ⚡ 快速開始（3 個檔案 = 100% 啟用最佳推理能力）

> ⚠️ **核心提示**：MoziAI 的最佳推理能力需要**同時下載 3 個檔案**——主模型、視覺投影、聊天模板。缺少任何一個都會損失對應能力。

### 6.1 下載模型檔案

在 HuggingFace / ModelScope 下載 **V3.8 目錄下的所有檔案**到本地同一目錄：

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf   ← 主模型（必選，13.7 GB）
├── moziAI-27B-3.8-mmproj-F16.gguf            ← 視覺投影（必選，927 MB）
└── chat-template-moziai-27B-v38.jinja         ← 聊天模板（必選，含七維思考+Loop指令）
```

| 檔案 | 大小 | 必要性 | 作用 |
| --- | --- | --- | --- |
| 主模型 `.gguf` | ~13.7 GB | **必選** | 模型權重，核心推理能力 |
| 視覺投影 `mmproj` | ~927 MB | **必選** | 多模態視覺理解，不載入則喪失圖像能力 |
| 聊天模板 `.jinja` | 微量 | **必選** | 注入 MoziAI 身份 + 七維思考 + LOOP 機制指令 |

### 6.2 啟動並使用

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

瀏覽器開啟 `http://localhost:8080` 即可開始對話。完整推薦參數見第 9 節。

---

## 7. 模型下載

| 平台 | 地址 |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main/V3.8) |
| ModelScope（魔搭） | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master/V3.8) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master/V3.8) |

> 💡 **LM Studio 使用者**：在 [LM Studio](https://lmstudio.ai) 中搜尋 `moziAI` 一鍵下載，無需手動下載檔案。

---

## 8. 啟動命令

### 最簡啟動（含三件套）

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### 完整推薦啟動

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

> 💡 關閉 MTP：刪除 `--spec-type draft-mtp` 及相關參數，速度降低約 30-50%，顯存占用更小。

---

## 9. 推薦推理參數

基於 llama.cpp 官方推薦參數與本地實測最佳化（AMD Radeon AI PRO R9700 32GB）：

| 參數 | 通用聊天 | 編碼/Agent | 說明 |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | 平衡創意與準確性 |
| top\_p | 0.95 | 0.95 | 核取樣閾值 |
| top\_k | 20 | 20 | 截斷取樣 |
| repeat\_penalty | 1.05 | 1.05 | 重複懲罰 |
| context\_length | 262144 | 262144 | 128K 長上下文 |
| reasoning | auto | auto | 開啟推理鏈（思維鏈） |
| reasoning\_budget | 400 | 400 | 推理預算 token |
| reasoning\_format | deepseek-legacy | deepseek-legacy | 推理輸出到獨立欄位 |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP 推測解碼（詳見第 11 節）** |

> 💡 **思考模式**：透過 `--reasoning auto` 開啟，模型先進行內部推理再輸出答案。`reasoning_budget` 控制最大思考 token 數（推薦 400，可調 100-1000）。

---

## 10. 量化格式對比

| 格式 | 體積 | 精度 | 說明 |
| --- | --- | --- | --- |
| FP16 原始 | ~54 GB | 100% | 無損，需專業顯示卡 |
| **MoziSmartBit（本模型）** | **~13.7 GB** | **~99%** | **自研智慧量化，精度最優、體積最小** |
| Q4_K_M | ~17 GB | ~98% | GGUF 標準 4bit |
| Q5_K_M | ~20 GB | ~99% | 更高精度 |
| Q6_K | ~23 GB | ~99.5% | 近無損 |
| Q8_0 | ~31 GB | ~100% | 無損 |

> MoziSmartBit 在保持約 99% 精度的同時，將 27B Dense 模型壓縮至 13.7 GB（壓縮比 3.9x），比 Q4_K_M 小約 20%，更適合消費級顯示卡本地部署。

---

## 11. MTP 推測解碼（重要加速特性）

本模型內建 MTP（Multi-Token Prediction）推測解碼層，開啟後推理速度提升 **1.5-2 倍**。這是 Qwen3.8 架構的原生特性，MoziAI 保留了完整 MTP 權重。

**原理**：在模型架構中額外訓練了輕量級預測頭（Draft Model），用於在主模型驗證前預先猜測後續 token，減少 forward 次數，降低推理延遲。猜測錯誤由主模型糾正，對輸出品質無負面影響。

### 開啟參數

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| 參數 | 推薦值 | 說明 |
| --- | --- | --- |
| --spec-type | draft-mtp | 啟用 MTP 推測解碼 |
| --spec-draft-n-max | 2 | 每次最多猜測 2 個 token（推薦值，接受率約 80%） |
| --spec-draft-p-min | 0.75 | 最低接受機率閾值（0.0-1.0，越大越保守） |

### 參數調整建議

| n-max | 接受率 | 適用場景 |
| --- | --- | --- |
| 1 | ~90% | 最保守，速度提升最小 |
| **2** | **~80%** | **推薦：平衡速度與準確率** |
| 3 | ~71% | 通用場景，速度提升明顯 |
| 4-5 | ~60-65% | 創意寫作、程式碼生成 |
| 6 | ~50-55% | 純文字長輸出（需配合 p-min 調整） |

---

## 12. 顯存配置推薦

| 顯存 | 推薦配置 | 說明 |
| --- | --- | --- |
| 16 GB | 上下文降至 64K，需 CPU 卸載 | 入門級，如 RTX 4060 Ti |
| **20 GB** | **128K 滿配，q4_0 KV 快取** | **推薦配置**，如 RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K 滿配，顯存餘量充足 | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K 滿配，最強配置 | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB 內顯 | 128K 滿配 | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 上下文越長，顯存占用越多。OOM 時逐步降低 `-c` 參數。使用 `--fit on` 讓 llama.cpp 自動調整層數以適配顯存。支援 NVIDIA / AMD / Intel 全品牌顯示卡。

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

在 LM Studio / Jan 中搜尋 `moziAI`，選擇 Q4\_K\_M 量化版本下載即可。

> 💡 Ollama 的 mmproj 和 chat\_template 支援有限，建議優先使用 llama.cpp 以獲得完整功能。

---

## 14. 基準評測

MoziAI-27B-3.8 基於 Qwen3.8-27B 底座微調，金融垂直領域為核心最佳化方向。

### 編碼能力

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

### 多模態能力

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> 競品資料為官方公開評測結果。MoziAI 金融垂直領域（財報解讀、量化策略、風控合規、Agent 工具呼叫等）表現顯著優於通用模型。

---

## 15. 許可證

本模型採用**自訂限制性許可證**：

- ✅ **允許** — 免費商業使用、複製和散佈
- ❌ **禁止** — 二次開發、轉售販賣、再授權
- 📋 **要求** — 保留原始版權聲明，註明來源：moziAI-27B

本模型按「原樣」提供，不提供任何形式的保證。模型輸出僅供參考，不構成投資建議。使用者需自行承擔使用風險。

詳細條款請參閱 [LICENSE](LICENSE) 檔案。

---

## 16. 聯絡方式

- **HuggingFace**：[@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**：[@chenyumo166](https://github.com/chenyumo166)
- **微博**：[@rimochen](https://weibo.com/rimochen)
- **E-mail**：263515@qq.com

Copyright (c) 2026 陳雨墨 / chenyumo166. All rights reserved.
