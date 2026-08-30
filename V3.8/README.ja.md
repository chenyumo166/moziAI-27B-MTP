---
language:
- en
- ja
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

# MoziAI-27B-3.8 - ローカル無料デプロイ可能な小型高性能マルチモーダルAI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | 日本語 | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## モデル概要

MoziAI-27B-3.8は、中国の金融インフルエンサー陳雨墨氏チームが開チームが開発したローカルオープンソース金融AIマルチモーダルLLM（視覚・ツール呼び出し対応）。オープンソースベースモデルQwen3.8-27B（Dense 27Bアーキテクチャ、MITライセンス）を基盤とし、陳雨墨チーム独自開発の（金融データ＋金融ドメイン能力＋トレーニング方法＋七次元思考フレームワーク＋エージェントLOOPメカニズム＋ハイブリッド量子化アルゴリズムMoziSmartBit）を統合。

独自開発のMoziSmartBit知的量子化技術により、270億パラメータのDenseモデルを約12.79 GBに圧縮。通常のQ4_K_M量子化（約17GB）より3.3GB（約20%）小さく、精度とサイズの最適バランスを実現。FP16の**約99%の精度品質**を維持。

金融垂直ドメイン強化、金融Q&A、量化プログラミング、ツール呼び出し、七次元思考能力、LOOPメカニズム、各種エージェントプラットフォーム互換。OpenClaw/Hermesで128Kコンテキストタスクを実行可能。ローカル消費GPUデプロイでクラウドトークンコストを大幅節約、**7×24時間トークンフリー**を実現。

llama.cpp、Ollama、LM Studio等のメインストリーム推論フレームワークをサポート。

**リリース日：2026-08-30** | **バージョン：V3.8**

## モデル特長

- **金融垂直最適化**：金融Q&A、量化プログラミング、ツール呼び出しの強化
- **MoziSmartBit知的量子化**：独自量子化技術、精度**~99%**維持、**~12.79 GB**に圧縮
- **コンシューマGPUデプロイ**：16GB VRAM以上でローカルデプロイ可能、20GB以上で完全な128K長コンテキスト推理
- **MTP推測デコーディング**：内蔵マルチトークン予測レイヤー、推論速度1.5-2倍向上
- **多言語サポート**：201言語・方言対応
- **汎用プログラミング**：Python/JS/TS/Go/Rust等
- **視覚理解**：マルチモーダル対応
- **推論ロジック強化**：チェーン・オブ・スートレーニング
- **マルチフレームワーク**：llama.cpp、Ollama、LM Studio、Jan
- **マルチエージェント**：OpenClaw、Hermes、Cursor等AI IDE対応

## 核心能力

| 能力分野 | 説明 |
|---------|------|
| 市場分析 | マクロ/ミクロ経済解説、A株/HK/US株/商品/暗号通貨 |
| 財務・研報 | 財務指標解説、研報要約、バリュエーション支援 |
| リスク・コンプライアンス | リスク評価、投資助言、金融規制解説 |
| 量化・戦略 | 量化戦略設計、ピラミッド(PEL)量化、バックテスト |
| ツール呼び出し | リアルタイム行情、データベース、研報検索 |

## 技術仕様

| 項目 | 仕様 |
|------|------|
| ベースモデル | Qwen3.8-27B（Dense、ハイブリッドアテンション、MIT） |
| パラメータ | 270億 Dense |
| 量子化 | MoziSmartBit知的量子化 + GGUF標準 |
| コンテキスト長 | 128K（262,144トークン） |
| モデルサイズ | ~12.79 GB |
| 最低VRAM | **16GB+** デプロイ可能（CPUオフロード必要）；**20GB+** 長コンテキスト対応；**24GB+** 完全な128K + ビジョン |
| 推論速度 | MTP有効：R9700 70+ tok/s、MAX+395 CPU 50+ tok/s、MAX+395 GPU 35+ tok/s |

## 量子化フォーマット

| フォーマット | サイズ | 精度 | 説明 |
|-------------|--------|------|------|
| FP16（元） | ~54 GB | 100% | 元16ビット精度 |
| **MoziSmartBit** | **~12.79 GB** | **~99%** | **独自知的量子化** |
| Q4_K_M | ~17 GB | ~98% | GGUF標準4bit |
| Q5_K_M | ~20 GB | ~99% | 高精度 |
| Q6_K | ~23 GB | ~99.5% | 損失無しに近い |
| Q8_0 | ~31 GB | ~100% | 損失なし |

## MTP推測デコーディング

本モデルはMTP推測デコーディングレイヤーを内蔵し、有効にすると推論速度が**1.5-2倍**向上。

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

| パラメータ | 推奨値 | 説明 |
|-----------|--------|------|
| --spec-type | draft-mtp | MTP推測デコーディング有効 |
| --spec-draft-n-max | 2 | 1ステップ最大2トークン予測（~80%受容率） |
| --spec-draft-p-min | 0.75 | 最小受容確率閾値 |

## llama.cpp起動コマンド

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

> 💡 **MTP無効化**：`--spec-type draft-mtp`、`--spec-draft-n-max 2`、`--spec-draft-p-min 0.75`の3行を削除。速度30-50%低下、VRAM使用量減少。

## VRAM構成推奨

| VRAM | コンテキスト | KVキャッシュ | 視覚 | 備考 |
|------|-------------|------------|------|------|
| 20 GB | 128K | q4_0 | 対応 | 推奨構成 |
| 24 GB | 128K | q4_0 | 完全対応 | VRAM余裕あり |
| 32 GB+ | 128K | q4_0 | 完全対応 | 最強構成 |

## ベンチマーク

### コーディング

| ベンチマーク | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 |
| QwenSWEBench | **79.0** | 49.3 | 59.2 |

### エージェント

| ベンチマーク | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 |
| JobBench | **33.4** | 21.8 | 27.6 |
| WebArena-Verified | **64.8** | 48.8 | 55.3 |

## モデルダウンロード

| プラットフォーム | リンク |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## クイックスタート

### 1. ダウンロード

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # メインモデル
├── moziAI-27B-3.8-mmproj-F16.gguf              # 視覚プロジェクション
└── chat-template-moziai-27B-v38.jinja           # チャットテンプレート
```

### 2. 起動

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

### 3. チャット開始

ブラウザで `http://localhost:8080` を開く

## ライセンス

カスタム制限付きライセンス：無料商用利用可能 ✅ | 二次開発禁止 ❌ | 転売禁止 ❌

## 免責事項

本モデルは「現状のまま」提供され、何らかの保証を提供しません。

## お問い合わせ

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 陳雨墨/ chenyumo166. All rights reserved.
