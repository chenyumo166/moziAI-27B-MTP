---
language:
- en
- de
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

# MoziAI-27B-3.8 - Kostenlos lokal einsetzbares kleines, leistungsstarkes Multimodal-AI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | Deutsch | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## Modellübersicht

MoziAI-27B-3.8 ist ein lokales Open-Source-Finanz-AI-Multimodales LLM (mit Sicht- und Tool-Calling-Unterstützung), entwickelt vom Team des chinesischen Finanz-Influencers Chen Yumo. Basierend auf dem Open-Source-Grundmodell Qwen3.8-27B (Dense 27B Architektur, MIT-Lizenz), integriert die selbst entwickelten Technologien: (Finanzdaten + Finanzdomänenfähigkeiten + Trainingsmethoden + Sieben-Dimensionales-Denken-Framework + Agent-LOOP-Mechanismus + Hybride Quantisierungsalgorithmus MoziSmartBit).

Durch die selbst entwickelte MoziSmartBit-Intelligenzquantisierungstechnologie wird das 27-Milliarden-Parameter-Dense-Modell auf ca. 12.79 GB komprimiert — ca. 3,3 GB (ca. 20 %) kleiner als die konventionelle Q4_K_M-Quantisierung (ca. 17 GB). Optimales Gleichgewicht zwischen Genauigkeit und Größe mit **ca. 99 % der FP16-Genauigkeit**.

Starke Finanzdomäne: Finanz-Q&A, Quant-Programmierung, Tool-Calling, Sieben-Dimensionales-Denken, LOOP-Mechanismus. Kompatibel mit OpenClaw/Hermes für 128K-Kontextaufgaben. Lokale Consumer-GPU-Implementierung spart Cloud-Token-Kosten und erreicht **7×24-Stunden Token-Freiheit** mit lokalem Datenschutz.

Unterstützt llama.cpp, Ollama, LM Studio und andere Mainstream-Inferenz-Frameworks.

**Erscheinungsdatum: 2026-08-30** | **Version: V3.8**

## Modellmerkmale

- **Finanz-Domäne-Tiefe**: Tiefgreifende Optimierung für Finanz-Q&A, Quant-Programmierung und Tool-Calling
- **MoziSmartBit-Intelligenzquantisierung**: Komprimiert auf ca. **12,79 GB** mit **~99 % Genauigkeit**
- **Consumer-GPU-Einsatz**: 16 GB+ VRAM ermöglicht lokale Bereitstellung, 20 GB+ für vollständigen 128K-Kontext
- **MTP-Spezulative Dekodierung**: Integrierter Multi-Token-Prädiktionslayer, 1,5-2× Inferenzgeschwindigkeit
- **Mehrsprachig**: 201 Sprachen und Dialekte
- **Allgemeine Programmierung**: Python/JS/TS/Go/Rust
- **Visuelle Wahrnehmung**: Multimodal, lokale Bildverarbeitung
- **Erweitertes Denken**: Chain-of-Thought-Training
- **Multi-Framework**: llama.cpp, Ollama, LM Studio, Jan
- **Multi-Agent**: OpenClaw, Hermes, Cursor, Claude Code

## Kerndefinition

| Fähigkeitsbereich | Beschreibung |
|---|---|
| Marktanalyse | Makro-/Mikroökonomie, Aktien, Rohstoffe, Krypto |
| Finanzen & Berichte | Finanzkennzahlen, Research-Zusammenfassungen |
| Risiko & Compliance | Risikobewertung, Anlageempfehlungen, Compliance |
| Quant & Strategie | Quant-Strategien, Pyramid-PEL, Backtesting |
| Tool-Calling | Echtzeitkurse, Datenbanken, Research-Abruf |

## Technische Daten

| Parameter | Wert |
|---|---|
| Grundmodell | Qwen3.8-27B (Dense, Hybrid-Attention, MIT) |
| Parameter | 27 Milliarden Dense |
| Quantisierung | MoziSmartBit + GGUF-Standard |
| Kontextlänge | 128K (262.144 Tokens) |
| Modellgröße | ~12,79 GB |
| Mindest-VRAM | **16 GB+** einsatzbereit (mit CPU-Offload)；**20 GB+** flüssiger Langkontext；**24 GB+** vollständiges 128K + Vision |
| Inferenzgeschwindigkeit | MTP aktiv: R9700 70+ tok/s, MAX+395 CPU 50+ tok/s, MAX+395 GPU 35+ tok/s |

## Quantisierungsformate

| Format | Größe | Genauigkeit | Beschreibung |
|---|---|---|---|
| FP16 | ~54 GB | 100 % | Originalgenauigkeit |
| **MoziSmartBit** | **~12,79 GB** | **~99 %** | **Selbst entwickelte Intelligenzquantisierung** |
| Q4_K_M | ~17 GB | ~98 % | GGUF-Standard 4-Bit |
| Q5_K_M | ~20 GB | ~99 % | Höhere Genauigkeit |
| Q6_K | ~23 GB | ~99,5 % | Nahezu verlustfrei |
| Q8_0 | ~31 GB | ~100 % | Verlustfrei |

## MTP-Spezulative Dekodierung

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

| Parameter | Empfehlung | Beschreibung |
|---|---|---|
| --spec-type | draft-mtp | MTP aktivieren |
| --spec-draft-n-max | 2 | Max. 2 Tokens pro Schritt (~80 % Annahmerate) |
| --spec-draft-p-min | 0,75 | Mindestwahrscheinlichkeit |

> 💡 **MTP deaktivieren**: Entfernen Sie `--spec-type draft-mtp` und die zwei folgenden Zeilen. Geschwindigkeit sinkt ~30-50 %, VRAM wird kleiner.

## llama.cpp Startbefehl

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

## VRAM-Konfiguration

| VRAM | Kontext | KV-Cache | Sicht | Beschreibung |
|---|---|---|---|---|
| 20 GB | 128K | q4_0 | Unterstützt | Empfohlen |
| 24 GB | 128K | q4_0 | Voll | Ausreichend |
| 32 GB+ | 128K | q4_0 | Voll | Beste Konfiguration |

## Benchmarks

### Programmierung

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73,0 | 63,4 | 64,0 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 |
| QwenSWEBench | **79,0** | 49,3 | 59,2 |

### Agent

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| CoWorkBench | **70,7** | 61,0 | 65,1 |
| JobBench | **33,4** | 21,8 | 27,6 |
| WebArena-Verified | **64,8** | 48,8 | 55,3 |

## Modell download

| Plattform | Link |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## Schnellstart

### 1. Herunterladen

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
  -c 131072 -ngl 99
```

### 3. Chat starten

`http://localhost:8080` im Browser öffnen

## Lizenz

Benutzerdefinierte restriktive Lizenz: Freie kommerzielle Nutzung ✅ | Weiterentwicklung ❌ | Weiterverkauf ❌

## Haftungsausschluss

Das Modell wird "wie es ist" bereitgestellt. Keine Garantie.

## Kontakt

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-Mail: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. Alle Rechte vorbehalten.
