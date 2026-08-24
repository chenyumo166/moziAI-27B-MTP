---
language:
- en
- it
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

# MoziAI-27B-3.8 - AI Multimodale Piccola ma Potente, Distribuibile Gratuitamente in Locale

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | Italiano | [Русский](README.ru.md)

## Panoramica del modello

MoziAI-27B-3.8 è un LLM multimodale finanziario open-source locale sviluppato dal team dell'influencer finanziario cinese Chen Yumo. Basato sul modello open-source Qwen3.8-27B (architettura Dense 27B, licenza MIT), integra le tecnologie sviluppate internamente: (dati finanziari + capacità del dominio finanziario + metodi di addestramento + framework di ragionamento a sette dimensioni + meccanismo LOOP agente + algoritmo di quantizzazione ibrida MoziSmartBit).

La tecnologia di quantizzazione intelligente MoziSmartBit comprime il modello Dense da 27 miliardi di parametri a circa 13,7 GB, circa 3,3 GB (~20%) più piccolo della quantizzazione Q4_K_M convenzionale (~17 GB), con **~99% della precisione FP16**.

Capacità: Q&A finanziaria, programmazione quantitativa, chiamata strumenti, ragionamento in 7 dimensioni, meccanismo LOOP, compatibilità multi-agente. Esecuzione di task con 256K di contesto via OpenClaw/Hermes, realizzando la **libertà dei token 7×24** con privacy locale.

Supporta llama.cpp, Ollama, LM Studio e altri framework di inferenza.

**Data di rilascio: 2026-08-25** | **Versione: V3.8**

## Caratteristiche

- **Verticalità finanziaria**: Ottimizzazione profonda per Q&A finanziaria, programmazione quantitativa, chiamata strumenti
- **Quantizzazione intelligente MoziSmartBit**: Compressione a **~13,7 GB** con **~99% di precisione**
- **Deploy su GPU consumer**: 20 GB VRAM+, contesto 256K
- **Decodifica speculativa MTP**: Layer multi-token integrato, velocità x1.5-2
- **Multilingua**: 201 lingue e dialetti
- **Programmazione generale**: Python/JS/TS/Go/Rust
- **Comprensione visiva**: Multimodale
- **Ragionamento avanzato**: Addestramento chain-of-thought
- **Multi-framework**: llama.cpp, Ollama, LM Studio, Jan
- **Multi-agente**: OpenClaw, Hermes, Cursor, Claude Code

## Specifiche tecniche

| Parametro | Valore |
|---|---|
| Modello base | Qwen3.8-27B (Dense, attention ibrida, MIT) |
| Parametri | 27 miliardi Dense |
| Quantizzazione | MoziSmartBit + formato GGUF |
| Lunghezza contesto | 256K (262.144 token) |
| Dimensione modello | ~13,7 GB |
| VRAM min. | 20 GB+ (RTX 4060 Ti 16G: CPU offload) |
| Velocità inferenza | MTP: R9700 70+ tok/s, MAX+395 CPU 50+ tok/s |

## Formati di quantizzazione

| Formato | Dimensione | Precisione |
|---|---|---|
| FP16 | ~54 GB | 100% |
| **MoziSmartBit** | **~13,7 GB** | **~99%** |
| Q4_K_M | ~17 GB | ~98% |
| Q5_K_M | ~20 GB | ~99% |
| Q6_K | ~23 GB | ~99,5% |
| Q8_0 | ~31 GB | ~100% |

## MTP Decodifica Speculativa

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

> 💡 **Disabilitare MTP**: Rimuovere le 3 righe. Velocità -30-50%, VRAM ridotta.

## Comando di avvio llama.cpp

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

## Benchmark

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73,0 | 63,4 | 64,0 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 |
| CoWorkBench | **70,7** | 61,0 | 65,1 |
| IFBench | **79,5** | 69,1 | 79,1 |
| GPQA Diamond | 89,2 | 87,8 | 90,3 |

## Download

| Piattaforma | Link |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## Avvio rapido

### 1. Scaricare

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf
├── moziAI-27B-3.8-mmproj-F16.gguf
└── chat-template-moziai-27B-v38.jinja
```

### 2. Avviare

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

### 3. Chat

Aprire `http://localhost:8080` nel browser

## Licenza

Licenza restrittiva personalizzata: Uso commerciale gratuito ✅ | Sviluppo secondario proibito ❌ | Rivendita proibita ❌

## Contatti

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. Tutti i diritti riservati.
