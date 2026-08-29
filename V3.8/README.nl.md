---
language:
- en
- nl
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

# MoziAI-27B-3.8 - Gratis lokaal deploybaar klein maar krachtig multimodaal AI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | Nederlands | [Italiano](README.it.md) | [Русский](README.ru.md)

## Modeloverzicht

MoziAI-27B-3.8 is een lokaal open-source financieel AI multimodale LLM (ondersteunt visie en tool calling), ontwikkeld door het team van de Chinese financieel influencer Chen Yumo. Gebaseerd op het open-source basismodel Qwen3.8-27B (Dense 27B architectuur, MIT licentie), met zelfontwikkelde technologieën: (financiële data + financiële domeinvaardigheden + trainingsmethoden + Zeven-Dimensionaal Denken Framework + agent LOOP mechanisme + hybride kwantiseeringsalgoritme MoziSmartBit).

De zelfontwikkelde MoziSmartBit intelligente kwantiseertechnologie comprimeert het 27-miljard parameter Dense model naar ongeveer 12,79 GB, 3,3 GB (~20%) kleiner dan Q4_K_M (~17 GB), met **~99% nauwkeurigheid van FP16**.

Financiële domeinverdieping, financiële Q&A, kwantum programmeren, tool calling, zeven-dimensionaal denken, LOOP mechanisme, multi-agent compatibiliteit. Uitvoering van 256K contexttaken via OpenClaw/Hermes, realisatie van **7x24 tokenvrijheid** met lokale gegevensprivacy.

Ondersteunt llama.cpp, Ollama, LM Studio en andere inferentieframeworks.

**Releasedatum: 2026-08-25** | **Versie: V3.8**

## Modelspecificaties

| Item | Specificatie |
|---|---|
| Basismodel | Qwen3.8-27B (Dense, hybride aandacht, MIT) |
| Parameters | 27 miljard Dense |
| Kwantisatie | MoziSmartBit + GGUF standaard |
| Contextlengte | 256K (262.144 tokens) |
| Modelgrootte | ~12,79 GB |
| Min. VRAM | **16 GB+** bruikbaar (CPU offload)；**20 GB+** vloeiende lange context；**24 GB+** volledige 256K + visie |
| Inferentiesnelheid | MTP: R9700 70+ tok/s, MAX+395 CPU 50+ tok/s |

## Kwantisatieformaten

| Formaat | Grootte | Nauwkeurigheid |
|---|---|---|
| FP16 | ~54 GB | 100% |
| **MoziSmartBit** | **~12,79 GB** | **~99%** |
| Q4_K_M | ~17 GB | ~98% |
| Q5_K_M | ~20 GB | ~99% |

## MTP Speculatieve Decodering

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

> 💡 **MTP uitschakelen**: Verwijder de 3 regels. Snelheid -30-50%, VRAM vermindert.

## llama.cpp Opdracht

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

## Benchmarks

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73,0 | 63,4 | 64,0 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 |
| CoWorkBench | **70,7** | 61,0 | 65,1 |
| IFBench | **79,5** | 69,1 | 79,1 |

## Download

| Platform | Link |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## Snelle start

### 1. Downloaden

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf
├── moziAI-27B-3.8-mmproj-F16.gguf
└── chat-template-moziai-27B-v38.jinja
```

### 2. Starten

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

### 3. Chatten

Open `http://localhost:8080` in de browser

## Licentie

Aangepaste beperkte licentie: Gratis commercieel gebruik ✅ | Secundaire ontwikkeling ❌ | Doorverkoop ❌

## Contact

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. Alle rechten voorbehouden.
