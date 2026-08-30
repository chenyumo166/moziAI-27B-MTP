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

[English](README.en.md) | [简体中文](README.zh.md) | 繁體中文 | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## 模型簡介

MoziAI-27B-3.8 是由中國財經大V陳雨墨團隊開發的本地開源多模態AI大模型（增強金融領域、支援視覺、工具呼叫、消費級顯卡本地部署）。moziAI-27B-3.8 基於開源底座 Qwen3.8-27B（Dense 27B 架構，MIT 許可），結合陳雨墨團隊自主研發的（金融數據 + 金融領域能力 + 訓練方法 + 動態七維思考體系 + 智能體LOOP反思迭代機制 + 混合量化演算法 MoziSmartBit）開發而成。降低個人與企業的本地部署門檻，授權免費商用。因本地消費級顯卡可部署使用，節約大量雲端token成本，實現7×24小時token自由並且確保本地數據隱私與安全。

**動態七維思考體系 + 智能體LOOP迭代機制**：MoziAI 自研的核心推理模式。智慧判斷任務複雜度，簡單任務啟動二維思考快速回答，中度複雜任務啟用五維思考，高度複雜任務啟用完整七維思考+LOOP反思迭代機制。試圖挑戰比自己體積大幾十倍的萬億級參數模型的複雜任務的有效解決能力，又不失簡單任務的輕快回應。讓本地模型也能養成人類資深專家「先想後做」的能力，這套自研的核心推理模式對比同等體積模型極具特色。

**透過自研的 MoziSmartBit 智能量化技術**，270億參數的密集模型被壓縮至約12.79 GB，比常規的Q4_K_M量化模型（約17 GB）小3.3 GB（約20%）；在精度與大小之間實現了最佳平衡，提供~99%的FP16精度品質。

本模型除了保留AI大模型的通用能力外，還增強了：金融垂直領域應用，金融問答、量化程式編寫、工具呼叫和通用程式編寫，相容各種agent平台呼叫。

模型研發者陳雨墨常把本模型用於本地金融數據分析、量化策略研發、市場調研、任何的文章編寫、整體項目開發推進、通用程式編寫，OpenClaw/Hermes執行256K長上下文的複雜任務。

支援 llama.cpp、Ollama、LM Studio 等主流推理框架免費本地部署

**發佈日期：2026-08-30** | **版本：V3.8**

## 模型特色

- **🧠 動態七維思考體系**：MoziAI 自研的核心推理框架。面對任何任務，模型先輸出 **moziAI-Think** 標記，按任務複雜度動態展開結構化思考——從簡單問答的「理解任務 + 資源需求」兩維速答（Level 0），到分析診斷的五維評估（Level 1），再到複雜開發/策略設計的全七維深度推演（Level 2）：①理解任務 ②複雜度評估 ③依賴關係 ④風險評估 ⑤資源需求 ⑥驗收標準 ⑦執行策略。
- **🧠 智能體LOOP迭代機制**：MoziAI 對於複雜任務，模型自動進入 **moziAI-Loop** 迭代模式：第1輪執行+評估 → 第2輪調整+驗證，確保輸出經過自我校驗後才給出最終答案，而非一次性生成。這意味著模型不只是「回答問題」，而是像資深工程師一樣拆解問題→評估方案→執行→反思→優化，顯著提升複雜任務的準確性和可執行性。簡單問答和任務則自動關閉Loop迭代機制。
- **🧠 MoziSmartBit 智能量化**：MoziAI 自主研發的分層智能量化，在精度與大小之間達到最佳平衡，壓縮至約 12.79 GB，並保持FP16~99% 的精度
- **🧠 金融垂直領域聚焦**：針對金融問答、量化程式編寫和工具呼叫的深度優化。金融領域對於模型幻覺的容忍度極低，也證明了moziAI對比通用模型在垂直領域能力進行深度加強。
- **多語言支援**：支援201種語言和方言，中文能力特別優化，兼顧英語、日語、韓語、德語、法語、西班牙語、葡萄牙語等主流語言
- **通用程式編寫能力**：支援全棧開發、程式碼除錯、架構設計、腳本編寫，覆蓋 Python/JS/TS/Go/Rust 等主流語言
- **文章寫作能力**：支援多體裁高品質寫作，包括研報、分析文章、技術文檔、創意內容等
- **視覺理解**：支援多模態視覺，可本地截圖進入聊天視窗，模型能夠看懂圖片內資訊
- **多框架支援**：兼顧llama.cpp、Ollama、LM Studio、Jan 等主流推理框架
- **多Agent平台支援**：深度適合OpenClaw、Hermes、OpenCode、Cursor、Windsurf、Claude Code、Codex 等國內外主流 AI IDE 與 Agent 框架，原生支援工具呼叫與多輪任務編排，開箱即可

## 核心能力

| 能力領域  | 說明                                         |
| ----- | ------------------------------------------ |
| 市場分析  | 宏觀/微觀經濟解讀、A股/港股/美股/商品/加密貨幣行情與邏輯梳理         |
| 財務與研報| 財報關鍵指標解讀、研報摘要提取、估值與盈利預測輔助                  |
| 風控與合規| 產品風險評估、投資建議合規提示、金融監管政策解讀                   |
| 量化與策略| 量化策略思路設計、金字塔（Pyramid/PEL）量化、回測邏輯、因子構建與工具呼叫 |
| 工具呼叫  | 可接入即時行情、資料庫、研報檢索等金融數據源                    |

## 技術規劃

| 項目     | 參數                                                                                 |
| ------ | ---------------------------------------------------------------------------------- |
| 底座模型   | Qwen3.8-27B（Dense 架構，混合注意力 16 full + 48 linear，MIT 許可證）                         |
| 參數規模   | 270億（27B）Dense 架構                                         |
| 量化方式   | 採用自研 MoziSmartBit 智能量化演算法 + GGUF 標準格式                                               |
| 上下文長度 | 256K（262,144 tokens）                                                             |
| 模型體積   | ~12.79 GB                                                        |
| 最低顯存要求| **16GB+** 可部署（需CPU卸載，如 RTX 4060 Ti 16G）；**20GB+** 可流暢運行長上下文（如 RX 7900 XT 20G）；**24GB+** 支援完整256K + 視覺 |
| 推理框架   | llama.cpp / Ollama / LM Studio / Jan                                               |
| 推理速度   | 開啟MTP推測解碼：AMD R9700顯卡可達 70+ token/s，AMD MAX+395 CPU核顯可達 50+ token/s，AMD MAX+395 GPU可達 35+ token/s，實現本地token自由輸出       |
| 開發團隊   | 陳雨墨團隊                                                                             |

## 量化格式與模型體積

| 量化格式             | 模型體積          | 精度保持      | 說明                |
| ---------------- | ------------- | --------- | ----------------- |
| FP16（原始）         | ~54 GB       | 100%      | 原始 16bit 精度       |
| **MoziSmartBit** | **~12.79 GB** | **~99%**  | **本模型採用自研智能量化方式** |
| Q4_K_M         | ~17 GB      | ~98%     | GGUF 標準 4bit      |
| Q5_K_M         | ~20 GB     | ~99%     | 更高精度              |
| Q6_K            | ~23 GB     | ~99.5%   | 近無損              |
| Q8_0            | ~31 GB     | ~100%    | 無損失              |

> MoziAI V3.8 採用 MoziSmartBit 智能量化方案，在保持約99%精度的同時，將270億參數Dense模型壓縮至約12.79 GB，壓縮比達4.0x，兼顧推理品質與部署門檻，更適合消費級顯卡本地部署

## MoziSmartBit 智能量化技術

傳統量化方案對所有層使用統一精度，而陳雨墨團隊自研的**MoziSmartBit 智能量化**針對 Dense 模型的結構特點，採用智慧差異化量化策略，在體積與精度間取得最優平衡，模型品質高於 Q4_K_M 格式，同時體積僅佔12.79 GB，壓縮比達4.0x，精度保持約99%。

### 壓縮效果

- **量化精度損失極小**：訓練增益 > 量化損失，訓練後的MoziAI-27B 在金融領域文本上下PPL 優於訓練前的 bf16 底座，降低了同類 AI 模型的幻覺與困惑。
- **模型體積壓縮至 4.0 倍**：從 FP16（~54 GB）壓縮至 ~12.79 GB，也大幅小於Q4_K_M的~17 GB，大幅降低顯存與存儲門檻
- **消費級顯卡可部署**：原本需要高端顯卡的 27B Dense 大模型，現在 16GB 顯存即可本地部署，20GB 以上顯卡實現完整 256K 長上下文推理

### 對比優勢

**vs Q4_K_M（~17 GB）**：體積減少約 20%（~12.79 GB），精度優於 Q4_K_M，顯存門檻更低，16GB 顯卡即可部署，20GB 以上顯卡即可流暢運行 256K 長上下文

**vs 原始 FP16（~54 GB）**：體積壓縮約 4.0 倍，精度保持約99%，從需要專業級顯卡降低到消費級顯卡即可本地運行256K長上下文

## 推薦推理參數

基於 llama.cpp 官方推薦參數與本地實測優化（AMD Radeon AI PRO R9700 32GB），推薦參數如下：

| 參數 | 通用聊天 | 編碼/Agent | 說明 |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | 平衡創意與準確性 |
| top\_p | 0.95 | 0.95 | 核取樣閾值 |
| top\_k | 20 | 20 | 截斷取樣 |
| repeat\_penalty | 1.05 | 1.05 | 重複懲罰 |
| presence\_penalty | 0 | 0 | 無存在懲罰 |
| context\_length | 262144 | 262144 | 256K 長上下文 |
| batch\_size | 2048 | 2048 | 批次大小 |
| ubatch\_size | 512 | 512 | 微批次大小 |
| flash\_attention | auto | auto | 自動 Flash Attention |
| kv\_cache | q4\_0 | q4\_0 | KV 快取量化 |
| poll | 0 | 0 | 閒置不輪詢GPU，節能低延遲 |
| reasoning | auto | auto | 開啟推理鏈（思維鏈） |
| reasoning\_budget | 400 | 400 | 推理預算 token |
| reasoning\_format | deepseek-legacy | deepseek-legacy | 推理格式 |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | 取樣器順序 |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP推測解碼（詳見下方MTP章節）** |

> 💡 **思考模式說明**：本模型內建 Qwen3.8 Thinking（思維鏈）能力。透過 `--reasoning auto` 開啟，模型會先進行內部推理再輸出答案。`reasoning_budget` 控制最大思考token數（400為推薦值，可根據任務複雜度調整100-1000）。`reasoning-format deepseek-legacy` 將思考過程輸出到獨立欄位，不污染主輸出內容。

## MTP 推測解碼（重要加速特性）

本模型內建 MTP（Multi-Token Prediction）推測解碼層，開啟後推理速度可提升 **1.5-2 倍**。這是 Qwen3.8 架構的原生特性，MoziAI 保留了完整的 MTP 權重。

### MTP 原理

MTP 在模型架構中額外訓練了一個輕量級的預測頭（Draft Model），用於在主模型驗證前預先猜測後續 token，從而減少主模型的 forward 次數，大幅降低推理延遲。

### llama.cpp 開啟 MTP 的參數

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| 參數 | 推薦值 | 說明 |
| --- | --- | --- |
| --spec-type | draft-mtp | 啟用 MTP 推測解碼 |
| --spec-draft-n-max | 2 | 每次最多猜測 2 個 token（推薦值，接受率最高約80%） |
| --spec-draft-p-min | 0.75 | 最低接受機率閾值（0.0-1.0，越大越保守） |

### MTP 參數調整建議

| spec-draft-n-max | 接受率 | 適用場景 |
| --- | --- | --- |
| 1 | ~90% | 最保守，速度提升最小但最安全 |
| **2** | **~80%** | **推薦：平衡速度與準確率** |
| 3 | ~71% | 通用場景，速度提升明顯 |
| 4-5 | ~60-65% | 創意寫作、程式碼生成 |
| 6 | ~50-55% | 純文字長輸出（需配合 p-min 調整） |

> ⚠️ **注意**：MTP 推測解碼對輸出品質無負面影響（猜測錯誤會被主模型糾正），僅影響推理速度。`spec-draft-n-max` 建議從 2 開始，根據實際接受率調整。

## llama.cpp 啟動指令

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

> 💡 **關閉 MTP**：如需關閉 MTP 推測解碼，刪除啟動指令中的 `--spec-type draft-mtp`、`--spec-draft-n-max 2`、`--spec-draft-p-min 0.75` 三行即可。關閉後推理速度會降低約 30-50%，但顯存佔用更小。

## 不同顯存配置推薦

由於使用者顯卡配置差異較大，以下為不同顯存下的推薦參數：

| 顯存 | 推薦上下文 | KV 快取 | 視覺支援 | 說明 |
| --- | --- | --- | --- | --- |
| 20 GB | 256K 滿配 | q4\_0 | 完美支援 | 視覺+256K長上下文，推薦配置（模型+KV約需16GB，顯存餘量~4GB） |
| 24 GB | 256K 滿配 | q4\_0 | 完美支援 | 視覺+256K長上下文，顯存餘量充足 |
| 32 GB+ | 256K 滿配 | q4\_0 | 完美支援 | 視覺+256K長上下文，顯存餘量充足，最強配置 |

**NVIDIA 顯卡參考表**

| 顯存 | 顯卡型號 |
| --- | --- |
| 16 GB | RTX 4060 Ti（需搭配 CPU 卸載）|
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD 顯卡參考表**

| 顯存 | 顯卡型號 |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel 顯卡參考表**

| 顯存 | 顯卡型號 |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50（需搭配 CPU 卸載）|

**CPU共享記憶體核顯設備參考表**

| 顯存 | 處理器型號 |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395（Radeon 8060S 核顯） |
| 128 GB | NVIDIA RTX Spark（Blackwell RTX GPU） |

> 💡 **提示**：只要顯存滿足以上要求即可使用，不限品牌型號，支援NVIDIA / AMD / Intel 各品牌獨立顯卡，也支援128GB 統一記憶體的核顯CPU。
> 💡 **提示**：上下文越長，佔用顯存越多。如果出現顯存不足（OOM），請逐步降低 `-c` 參數值。使用 `--fit on` 參數可讓 llama.cpp 自動調整層數適配顯存。

## Ollama 部署

```bash
# 建立 Modelfile
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf

PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 262144
PARAMETER num_gpu 99

# 載入視覺投影片（可選，啟用視覺能力）
PARAMETER mmproj ./moziAI-27B-3.8-mmproj-F16.gguf

# 載入聊天模板（推薦）
PARAMETER chat_template_file ./chat-template-moziai-27B-v38.jinja

# 建置並執行
ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

> 💡 Ollama 中 `mmproj` 和 `chat_template_file` 參數需確認具體版本支援情況，建議優先使用 llama.cpp 部署以獲得完整功能支援

## LM Studio / Jan 部署

直接在 LM Studio / Jan 中搜尋 `moziAI`，選擇 Q4_K_M 量化版本下載即可

## 基準評測

MoziAI-27B-3.8 基於 Qwen3.8-27B（Dense 27B）底座微調。以下為通用能力基準分數（MoziAI 金融垂直領域為核心優化方向，通用能力基準分數與底座 Qwen3.8-27B 一致）：

### 編碼能力

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

### 多模態能力

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94.6** | 85.1 | 90.3 | -- | 65.5 |
| BabyVision (With CI) | **85.6** | 28.9 | 70.4 | -- | 12.6 |
| CharXiv RQ (With CI) | **90.2** | 78.4 | 85.8 | -- | 66.0 |
| OmniDocBench 1.5 | 91.1 | 89.4 | **91.4** | 75.8 | 86.6 |
| RealWorldQA | 85.9 | 84.1 | **86.9** | -- | 73.9 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- | -- |

> MoziAI-27B-3.8 通用能力基準分數與底座 Qwen3.8-27B 一致。金融垂直領域為 MoziAI 的核心優化方向，在財報解讀、量化策略、風控合規、agent管理工具呼叫等場景下表現顯著優於通用模型。Qwen3.6/Qwen3.7/Muse-Glimmer/Opus4.6 數據為官方公開評測結果。

## 模型下載

由於模型檔案較大（~12.79 GB），模型權重託管於多個社群平台：

| 平台 | 地址 |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope（魔搭） | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

> 💡 **LM Studio 使用者**：可直接在 [LM Studio](https://lmstudio.ai) 中搜尋 `moziAI` 並一鍵下載，無需手動下載檔案

> 💡 **下載提示**：請點擊上方連結進入 HuggingFace 倉庫，在「Files and versions」標籤下下載 V3.8 目錄下的所有檔案（主模型、視覺投影片、聊天模板），確保三個檔案放在同一目錄下

⚠️ **重要：視覺能力需要額外載入mmproj 檔案**

本模型支援多模態視覺，視覺投影片（mmproj）已包含在版本目錄中

- **視覺檔案**：`moziAI-27B-3.8-mmproj-F16.gguf`（約 927 MB，BF16 精度）
- **放置位置**：與 GGUF 模型檔案放在同一版本目錄下
- **載入方式**：啟動 llama-server 時透過 `--mmproj` 參數載入

> 不載入視覺檔案將喪失影像理解能力，僅保留純文字對話能力

## 快速開始

### 1. 下載模型檔案

在 HuggingFace / ModelScope 下載 V3.8 目錄下的所有檔案到本地：

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # 主模型（必選）
├── moziAI-27B-3.8-mmproj-F16.gguf              # 視覺投影片（可選）
└── chat-template-moziai-27B-v38.jinja           # 聊天模板（推薦）
```

### 2. 啟動推理服務

完整的推薦配置啟動指令請參考上方 [llama.cpp 啟動指令](#llamacpp-啟動指令) 章節

最簡啟動（僅核心參數）：

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

> 需要視覺能力時加上 `--mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf`

### 3. 開始使用

瀏覽器開啟 `http://localhost:8080` 即可開始對話

### 目錄結構

```
moziAI-27B/
├── README.md              # 本檔案（中文說明書）
├── README.en.md           # 說明書的英文版本
├── LICENSE                # 許可證
├── V3.8/                  # V3.8 版本
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # 主模型
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # 視覺投影片
│   └── chat-template-moziai-27B-v38.jinja         # 聊天模板
```

## SEO 關鍵詞

金融AI大模型、AI大模型、本地開源模型、端側模型、量化程式編寫、MoziSmartBit、智能量化、GGUF量化、Dense模型、本地開源大模型、本地部署、金融AI、工具呼叫、Agent、llama.cpp、Ollama、GGUF、Q4\_K\_M、Qwen3.8-27B、金融垂直領域、開源模型、MTP推測解碼、256K長上下文、多模態、本地LLM、邊緣AI、自託管AI、speculative decoding、self-hosted AI、local LLM、edge AI、Chinese financial AI、Qwen3.8 fine-tune、tool-calling、vision model、open-source LLM、consumer GPU deployment、intelligent quantization

## 許可證（重要事項）

本模型採用**自訂限制性許可證**，具體條款如下：

✅ **允許**
- 免費商業使用：可免費整合到您的商業產品或服務中
- 複製和分發：可原樣複製、下載、分析

❌ **禁止**
- 二次開發：不得修改、翻譯、改編、合併、微調本模型或其任何部分
- 轉售售賣：不得將本模型單獨或作為產品組成部分進行售賣
- 再許可：不得就本模型授予任何從屬許可

📋 **要求**
- 使用時必須保留原始版權聲明
- 註明來源：moziAI-27B

詳細許可證條款請參閱 [LICENSE](LICENSE) 檔案

## 免責聲明

本模型按「原樣」提供，不提供任何形式的保證。模型輸出僅供參考，不構成投資建議。使用者需自行承擔使用風險。

## 聯繫方式

- **HuggingFace**：[@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**：[@chenyumo166](https://github.com/chenyumo166)
- **微博**：[@rimochen](https://weibo.com/rimochen)
- **E-mail**：263515@qq.com

Copyright (c) 2026 陳雨墨/ chenyumo166. All rights reserved.
