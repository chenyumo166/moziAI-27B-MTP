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

# MoziAI-27B-3.8 - Kostenfrei lokal deploybares, kleines und leistungsstarkes multimodales AI-Modell

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | Deutsch | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## Modellübersicht

MoziAI-27B-3.8 ist ein lokales Open-Source-Multimodal-AI-Großmodell, das vom Team des chinesischen Finanz-Influencers Chen Yumo entwickelt wurde (mit Verbesserungen im Finanzbereich, Vision-Unterstützung, Tool-Calling und lokalem Deployment auf Verbraucher-GPUs). moziAI-27B-3.8 basiert auf dem Open-Source-Basismodell Qwen3.8-27B (Dense-27B-Architektur, MIT-Lizenz) und integriert die selbst entwickelten Technologien des Chen-Yumo-Teams (Finanzdaten + Finanzdomänenfähigkeiten + Trainingsmethoden + Dynamisches Sieben-Dimensionales-Denk-Framework + Agent-LOOP-Reflexions- und Iterationsmechanismus + Hybrid-Quantisierungsalgorithmus MoziSmartBit). Es senkt die Hürde für das lokale Deployment für Einzelpersonen und Unternehmen und erlaubt die kostenlose kommerzielle Nutzung. Durch die Deployment auf lokalen Verbraucher-GPUs werden Cloud-Token-Kosten erheblich eingespart, 24/7-Token-Freiheit ermöglicht und die lokale Datenprivacy und -sicherheit gewährleistet.

**Dynamisches Sieben-Dimensionales-Denk-Framework + Agent-LOOP-Iterationsmechanismus**: MoziAI's selbst entwickelter Kernrechtsmodus. Bewertet die Aufgabenkomplexität intelligent — einfache Aufgaben aktivieren zweidimensionales Denken für schnelle Antworten, mittelkomplexe Aufgaben nutzen fünfdimensionales Denken, hochkomplexe Aufgaben aktivieren das vollständige sieben-dimensionale Denken mit LOOP-Reflexions- und Iterationsmechanismus. Es zielt darauf ab, die Fähigkeit Billionen-Parameter-Modelle herauszuforden, komplexe Aufgaben effektiv zu lösen, ohne die Leichtigkeit bei einfachen Aufgaben zu verlieren. Dies ermöglicht es lokalen Modellen, die „Zuerst denken, dann handeln"-Fähigkeit erfahrener menschlicher Experten zu entwickeln.

**Durch die selbst entwickelte MoziSmartBit-Intelligent-Quantisierungstechnologie** wird das 27-Milliarden-Parameter Dense-Modell auf etwa 12,79 GB komprimiert, was 3,3 GB (etwa 20%) kleiner als herkömmliche Q4_K_M-Quantisierungsmodelle (~17 GB) ist; optimale Balance zwischen Genauigkeit und Größe mit ~99% FP16-Genauigkeitsqualität.

Das Modell wurde zusätzlich zu den allgemeinen AI-Großmodellfähigkeiten verbessert für: Finanzvertikale Domänenanwendungen, Finanz-Q&A, Quantitatives Programmieren, Tool-Calling und Allgemeines Programmieren, sowie Kompatibilität mit verschiedenen Agent-Plattformen.

Der Modellentwickler Chen Yumo verwendet dieses Modell häufig für lokale Finanzdatenanalyse, Quantitative Strategieentwicklung, Marktforschung, alle Arten von Artikelschreiben, Gesamtprojektentwicklung, Allgemeines Programmieren und OpenClaw/Hermes-Ausführung komplexer Aufgaben mit 256K Langkontext.

Unterstützt kostenfreies lokales Deployment auf Mainstream-Inferenz-Frameworks wie llama.cpp, Ollama, LM Studio und mehr.

**Veröffentlichungsdatum: 2026-08-30** | **Version: V3.8**

## Modellfunktionen

- **🧠 Dynamisches Sieben-Dimensionales-Denk-Framework**: MoziAI's selbst entwickeltes Kernrechts-Framework. Bei jeder Aufgabe gibt das Modell zunächst den **moziAI-Think**-Tag aus und entfaltet strukturiertes Denken dynamisch basierend auf der Aufgabenkomplexität — von zweidimensionaler Schnellantwort (Level 0) über fünfdimensionale Bewertung (Level 1) bis hin zur vollständigen sieben-dimensionalen Tiefenableitung (Level 2): ①Aufgabenverständnis ②Komplexitätsbewertung ③Abhängigkeitsanalyse ④Risikobewertung ⑤Ressourcenanforderungen ⑥Abnahmekriterien ⑦Ausführungsstrategie.
- **🧠 Agent-LOOP-Iterationsmechanismus**: Bei komplexen Aufgaben wechselt MoziAI automatisch in den **moziAI-Loop**-Iterationsmodus: Runde 1 Ausführung + Bewertung → Runde 2 Anpassung + Verifizierung, stellt sicher, dass die Ausgabe vor der endgültigen Antwort selbstverifiziert wird. Das Modell beantwortet nicht nur Fragen — es zerlegt Probleme wie ein erfahrener Ingenieur: Analysieren → Lösung bewerten → Ausführen → Reflektieren → Optimieren.
- **🧠 MoziSmartBit Intelligent-Quantisierung**: MoziAI's selbst entwickelte hierarchische intelligente Quantisierung, optimale Balance zwischen Genauigkeit und Größe, komprimiert auf ~12,79 GB bei FP16 ~99% Genauigkeit.
- **🧠 Finanzvertikale Domänenfokus**: Tiefgehende Optimierung für Finanz-Q&A, Quantitatives Programmieren und Tool-Calling. Der Finanzbereich hat extrem niedrige Toleranz für Modellhalluzinationen.
- **Mehrsprachige Unterstützung**: Unterstützt 201 Sprachen und Dialekte, mit besonders optimierten Chinesisch-Fähigkeiten, sowie Englisch, Japanisch, Koreanisch, Deutsch, Französisch, Spanisch, Portugiesisch und weitere.
- **Allgemeine Programmierfähigkeiten**: Unterstützt Full-Stack-Entwicklung, Code-Debugging, Architekturdesign und Skripterstellung über Python/JS/TS/Go/Rust.
- **Artikelschreibfähigkeiten**: Unterstützt hochwertiges Schreiben in mehreren Genres, einschließlich Forschungsberichte, Analyseartikel, technische Dokumentation und kreative Inhalte.
- **Visuelles Verständnis**: Unterstützt multimodales Sehen; Screenshots können in das Chat-Fenster eingefügt werden und das Modell kann Bildinhalte verstehen.
- **Multi-Framework-Unterstützung**: Kompatibel mit Mainstream-Inferenz-Frameworks wie llama.cpp, Ollama, LM Studio, Jan und mehr.
- **Multi-Agent-Plattform-Unterstützung**: Tiefgehende Kompatibilität mit Hauptnationalen und internationalen AI-IDEs und Agent-Frameworks wie OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex, mit nativer Unterstützung für Tool-Calling und Multi-Turn-Aufgabenorchestrierung.

## Kernfähigkeiten

| Fähigkeitsbereich | Beschreibung |
| ----- | ------------------------------------------ |
| Marktanalyse | Makro-/Mikroökonomische Interpretation, A-Aktien/Hongkong/Aktien/Waren/Kryptowährungsmärkte |
| Finanzen & Berichte | Finanzkennzahlen-Interpretation, Berichtszusammenfassung, Bewertung und Ergebnisprognose |
| Risikomanagement & Compliance | Produkt-Risikobewertung, Anlageberatung-Compliance, Finanzaufsichtspolitik |
| Quantitativ & Strategie | Quantitative Strategiedesign, Pyramid (Pyramid/PEL) Quantisierung, Backtesting, Faktorconstruction |
| Tool-Calling | Anbindung an Echtzeitmarktdaten, Datenbanken, Berichtsuche |

## Technische Spezifikation

| Artikel | Parameter |
| ------ | ---------------------------------------------------------------------------------- |
| Basismodell | Qwen3.8-27B (Dense-Architektur, Hybrid-Attention 16 full + 48 linear, MIT-Lizenz) |
| Parameterskalierung | 27 Milliarden (27B) Dense-Architektur |
| Quantisierungsmethode | Selbst entwickelter MoziSmartBit-Intelligent-Quantisierungsalgorithmus + GGUF-Standardformat |
| Kontextlänge | 256K (262.144 Tokens) |
| Modellgröße | ~12,79 GB |
| Mindest-VRAM | **16GB+** deploybar (mit CPU-Offloading, z.B. RTX 4060 Ti 16G); **20GB+** flüssiger Langkontext (z.B. RX 7900 XT 20G); **24GB+** vollständiges 256K + Vision |
| Inferenz-Framework | llama.cpp / Ollama / LM Studio / Jan |
| Inferenzgeschwindigkeit | Mit MTP-Spekulative-Decoding: AMD R9700 GPU 70+ token/s, AMD MAX+395 integrierte GPU 50+ token/s, AMD MAX+395 GPU 35+ token/s |
| Entwicklungsteam | Chen Yumo Team |

## Quantisierungsformat & Modellgröße

| Quantisierungsformat | Modellgröße | Genauigkeitsbeibehaltung | Beschreibung |
| ---------------- | ------------- | --------- | ----------------- |
| FP16 (Original) | ~54 GB | 100% | Original 16-Bit-Genauigkeit |
| **MoziSmartBit** | **~12,79 GB** | **~99%** | **Dieses Modell verwendet selbst entwickelte intelligente Quantisierung** |
| Q4_K_M | ~17 GB | ~98% | GGUF-Standard 4-Bit |
| Q5_K_M | ~20 GB | ~99% | Höhere Genauigkeit |
| Q6_K | ~23 GB | ~99,5% | Nahezu verlustfrei |
| Q8_0 | ~31 GB | ~100% | Verlustfrei |

> MoziAI V3.8 verwendet das MoziSmartBit-Intelligent-Quantisierungsverfahren und komprimiert das 27-Milliarden-Parameter Dense-Modell auf etwa 12,79 GB bei Beibehaltung von etwa 99% Genauigkeit mit einem Kompressionsverhältnis von 4,0x.

## MoziSmartBit Intelligent-Quantisierungstechnologie

Herkömmliche Quantisierungsverfahren wenden einheitliche Genauigkeit auf alle Schichten an. Das selbst entwickelte **MoziSmartBit-Intelligent-Quantisierung** des Chen-Yumo-Teams adoptiert eine intelligente differenzierte Quantisierungsstrategie, die auf die strukturellen Merkmale von Dense-Modellen zugeschnitten ist und die optimale Balance zwischen Größe und Genauigkeit erreicht.

### Kompressionsergebnisse

- **Minimaler Quantisierungsgenauigkeitsverlust**: Trainingsgewinn > Quantisierungsverlust
- **Modellgröße auf 4,0x komprimiert**: Von FP16 (~54 GB) auf ~12,79 GB
- **Auf Verbraucher-GPUs deploybar**: 16 GB VRAM reichen für Deployment, 20 GB+ für vollständigen 256K-Langkontext

### Vergleichsvorteile

**vs Q4_K_M (~17 GB)**: Etwa 20% kleiner (~12,79 GB), höhere Genauigkeit, niedrigere VRAM-Schwelle, auf 16 GB GPUs deploybar

**vs Original FP16 (~54 GB)**: Etwa 4,0x Kompressionsverhältnis, ~99% Genauigkeitsbeibehaltung, von Profi-GPUs auf Verbraucher-GPUs reduziert

## Empfohlene Inferenzparameter

Basierend auf llama.cpp-Offiziellen Empfehlungen und lokaler Benchmark-Optimierung (AMD Radeon AI PRO R9700 32GB):

| Parameter | Allgemeiner Chat | Coding/Agent | Beschreibung |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Balance zwischen Kreativität und Genauigkeit |
| top\_p | 0.95 | 0,95 | Nucleus-Sampling-Schwelle |
| top\_k | 20 | 20 | Abgeschnittenes Sampling |
| repeat\_penalty | 1,05 | 1,05 | Wiederholungsstrafe |
| presence\_penalty | 0 | 0 | Keine Anwesenheitsstrafe |
| context\_length | 262144 | 262144 | 256K Langkontext |
| batch\_size | 2048 | 2048 | Stapelgröße |
| ubatch\_size | 512 | 512 | Mikro-Stapelgröße |
| flash\_attention | auto | auto | Automatisches Flash Attention |
| kv\_cache | q4\_0 | q4\_0 | KV-Cache-Quantisierung |
| poll | 0 | 0 | Keine GPU-Polling im Leerlauf, sparsam und niedrige Latenz |
| reasoning | auto | auto | Reasoning-Chain (Thought-Chain) aktivieren |
| reasoning\_budget | 400 | 400 | Reasoning-Token-Budget |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Reasoning-Format |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | Sampler-Reihenfolge |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP-Spekulative-Decoding (siehe unten)** |

> 💡 **Thinking-Modus-Hinweis**: Dieses Modell enthält Qwen3.8 Thinking (Thought-Chain) Fähigkeit. Über `--reasoning auto` aktiviert, führt das Modell vor der Antwort eine interne Reasoning durch. `reasoning_budget` steuert die maximale Thinking-Token-Anzahl (400 ist empfohlen, anpassbar 100-1000).

## MTP-Spekulative-Decoding (Wichtige Beschleunigungsfunktion)

Dieses Modell enthält eingebaute MTP (Multi-Token Prediction) Spekulative-Decoding-Schichten. Bei Aktivierung kann die Inferenzgeschwindigkeit um **1,5-2x** verbessert werden.

### MTP-Prinzip

MTP trainiert einen zusätzlichen leichtgewichtigen Vorhersagekopf (Draft Model) in der Modellarchitektur zur vorläufigen Vorhersage nachfolgender Tokens vor der Hauptmodellvalidierung.

### llama.cpp MTP-Parameter

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Empfohlener Wert | Beschreibung |
| --- | --- | --- |
| --spec-type | draft-mtp | MTP-Spekulative-Decoding aktivieren |
| --spec-draft-n-max | 2 | Maximal pro Schritt erratene Tokens (empfohlen, Annahmequote ~80%) |
| --spec-draft-p-min | 0,75 | Mindestannahmewahrscheinlichkeitsschwelle (0,0-1,0) |

### MTP-Parameteranpassungsleitfaden

| spec-draft-n-max | Annahmequote | Anwendungsfall |
| --- | --- | --- |
| 1 | ~90% | Am konservativsten |
| **2** | **~80%** | **Empfohlen: Balance Geschwindigkeit und Genauigkeit** |
| 3 | ~71% | Allgemeine Szenarien |
| 4-5 | ~60-65% | Kreatives Schreiben, Code-Generierung |
| 6 | ~50-55% | Reiner Text-Langoutput |

> ⚠️ **Hinweis**: MTP-Spekulative-Decoding hat keinen negativen Einfluss auf die Ausgabequalität.

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

> 💡 **MTP deaktivieren**: Entfernen Sie die drei Zeilen `--spec-type draft-mtp`, `--spec-draft-n-max 2` und `--spec-draft-p-min 0.75` aus dem Startbefehl. Die Geschwindigkeit sinkt dann um ca. 30-50%.

## VRAM-Konfigurationsempfehlungen

| VRAM | Empfohlener Kontext | KV-Cache | Vision-Unterstützung | Beschreibung |
| --- | --- | --- | --- | --- |
| 20 GB | 256K Voll | q4\_0 | Volle Unterstützung | Vision+256K Langkontext, empfohlene Konfiguration |
| 24 GB | 256K Voll | q4\_0 | Volle Unterstützung | Vision+256K Langkontext,充足的 VRAM |
| 32 GB+ | 256K Voll | q4\_0 | Volle Unterstützung | Vision+256K Langkontext, stärkste Konfiguration |

**NVIDIA GPU Referenztabelle**

| VRAM | GPU-Modell |
| --- | --- |
| 16 GB | RTX 4060 Ti (CPU-Offloading erforderlich) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD GPU Referenztabelle**

| VRAM | GPU-Modell |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel GPU Referenztabelle**

| VRAM | GPU-Modell |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (CPU-Offloading erforderlich) |

> 💡 **Tipp**: Solange das VRAM die Anforderungen erfüllt, ist jede Marke und jedes Modell unterstützt.
> 💡 **Tipp**: Längere Kontexte verbrauchen mehr VRAM. Bei VRAM-Überlauf (OOM) `-c`-Parameter schrittweise reduzieren. `--fit on` lässt llama.cpp die Schichten automatisch anpassen.

## Ollama-Deployment

```bash
# Modelfile erstellen
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf

PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 262144
PARAMETER num_gpu 99

PARAMETER mmproj ./moziAI-27B-3.8-mmproj-F16.gguf
PARAMETER chat_template_file ./chat-template-moziai-27B-v38.jinja

ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

## LM Studio / Jan Deployment

Suchen Sie direkt nach `moziAI` in LM Studio / Jan und wählen Sie die Q4_K_M-Version zum Download.

## Benchmark-Bewertung

MoziAI-27B-3.8 basiert auf dem Qwen3.8-27B (Dense 27B) Basismodell:

### Coding-Fähigkeiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73,0 | 63,4 | 64,0 | 51,7 | 78,2 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 | 51,2 | 53,4 |
| NL2Repo-Bench | 42,3 | 36,2 | 41,1 | -- | 47,6 |
| DeepSWE 1.1 | **42,2** | 13,3 | 14,2 | -- | -- |
| QwenSWEBench | **79,0** | 49,3 | 59,2 | -- | 63,8 |

### Agent-Fähigkeiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70,7** | 61,0 | 65,1 | -- | 68,2 |
| JobBench | **33,4** | 21,8 | 27,6 | -- | -- |
| Agents' Last Exam (Score) | **42,9** | 27,3 | 33,6 | -- | -- |
| WebArena-Verified | **64,8** | 48,8 | 55,3 | -- | -- |
| AndroidWorld | **81,9** | 70,3 | 81,0 | -- | 62,0 |

### Allgemeine Fähigkeiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79,5** | 69,1 | 79,1 | 77,0 | 62,5 |
| GPQA Diamond | 89,2 | 87,8 | 90,3 | 83,5 | **91,3** |

### Multimodale Fähigkeiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94,6** | 85,1 | 90,3 | -- | 65,5 |
| BabyVision (With CI) | **85,6** | 28,9 | 70,4 | -- | 12,6 |
| CharXiv RQ (With CI) | **90,2** | 78,4 | 85,8 | -- | 66,0 |
| OmniDocBench 1.5 | 91,1 | 89,4 | **91,4** | 75,8 | 86,6 |
| RealWorldQA | 85,9 | 84,1 | **86,9** | -- | 73,9 |
| Vision2Web | **62,9** | 45,0 | 42,1 | -- | -- |

## Modell-Download

| Plattform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope (魔搭) | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

⚠️ **Wichtig: Vision-Fähigkeit erfordert zusätzliches Laden der mmproj-Datei**

- **Vision-Datei**: `moziAI-27B-3.8-mmproj-F16.gguf` (~927 MB, BF16-Genauigkeit)
- **Ablageort**: Im selben Versionsverzeichnis wie die GGUF-Modelldatei
- **Laden**: Über den `--mmproj`-Parameter beim Starten von llama-server

## Schnellstart

### 1. Modelldateien herunterladen

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # Hauptmodell (erforderlich)
├── moziAI-27B-3.8-mmproj-F16.gguf              # Vision-Projektion (optional)
└── chat-template-moziai-27B-v38.jinja           # Chat-Template (empfohlen)
```

### 2. Inferenzdienst starten

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

### 3. Nutzung starten

Öffnen Sie `http://localhost:8080` im Browser.

### Verzeichnisstruktur

```
moziAI-27B/
├── README.md              # Diese Datei (chinesische Dokumentation)
├── README.en.md           # Englische Version
├── LICENSE                # Lizenz
├── V3.8/                  # V3.8-Version
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # Hauptmodell
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # Vision-Projektion
│   └── chat-template-moziai-27B-v38.jinja         # Chat-Template
```

## SEO-Schlüsselwörter

Finanz-AI-Großmodell, lokales Open-Source-Modell, MoziSmartBit, GGUF-Quantisierung, Qwen3.8-27B, Finanzvertikale Domäne, Tool-Calling, Agent, llama.cpp, Ollama, 256K Langkontext, multimodal, lokales LLM, edge AI, self-hosted AI, consumer GPU deployment, intelligent quantization

## Lizenz (Wichtig)

Dieses Modell wird unter einer **benutzerdefinierten eingeschränkten Lizenz** bereitgestellt:

✅ **Erlaubt**: Kostenlose kommerzielle Nutzung, Kopie und Vertrieb
❌ **Verboten**: Sekundäre Entwicklung, Weiterverkauf, Unterlizenzierung
📋 **Anforderungen**: Urheberrechtshinweis beibehalten, Quelle: moziAI-27B

## Haftungsausschluss

Dieses Modell wird „wie es ist" ohne jegliche Form von Garantie bereitgestellt.

## Kontakt

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
