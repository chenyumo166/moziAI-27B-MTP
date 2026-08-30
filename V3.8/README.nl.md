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

# MoziAI-27B-3.8 - Gratis lokaal deploybaar, klein maar krachtig multimodaal AI-model

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | Nederlands | [Italiano](README.it.md) | [Русский](README.ru.md)

## Modeloverzicht

MoziAI-27B-3.8 is een lokaal open-source multimodaal AI-grootmodel ontwikkeld door het team van de Chinese financiële influencer Chen Yumo (versterkt voor financieel domein, ondersteuning voor visie, tool-calling, lokale deployering op consumenten-GPUs). moziAI-27B-3.8 is gebaseerd op het open-source basismodel Qwen3.8-27B (Dense 27B architectuur, MIT-licentie), met zelfontwikkelde technologieën van het Chen Yumo-team (financiële gegevens + financiële domeincapaciteiten + trainingsmethoden + Dynamisch Zeven-Dimensionaal Denkkader + Agent LOOP Reflectie- en Iteratiemechanisme + Hybride kwantisering-algoritme MoziSmartBit). Het verlaagt de drempel voor lokale deployering voor individuen en bedrijven, met gratis commerciële licentie. Door lokale deployering op consumenten-GPUs worden cloudtokenkosten aanzienlijk bespaard, wordt 24/7 tokenvrijheid gerealiseerd en worden lokale gegevensprivacy en -beveiliging gegarandeerd.

**Dynamisch Zeven-Dimensionaal Denkkader + Agent LOOP Iteratiemechanisme**: MoziAI's zelfontwikkelde kernredeneermodus. Beoordeelt intelligent de taakcomplexiteit — eenvoudige taken activeren tweedimensionaal denken voor snelle antwoorden, matig complexe taken gebruiken vijfdimensionaal denken, zeer complexe taken activeren het volledige zeven-dimensionale denken met LOOP-reflectie- en iteratiemechanisme. Het beoogt de uitdaging van modellen met tientallen keren meer parameters te evenaren bij het effectief oplossen van complexe taken, zonder de lichtheid bij eenvoudige taken te verliezen.

**Door de zelfontwikkelde MoziSmartBit intelligente kwantiseringstechnologie** wordt het 27-miljard parameter Dense-model gecomprimeerd naar ongeveer 12,79 GB, wat 3,3 GB (ongeveer 20%) kleiner is dan conventionele Q4_K_M-kwantiseringmodellen (~17 GB); optimale balans tussen precisie en grootte met ~99% FP16-precisiekwaliteit.

Naast het behouden van de algemene AI-grootmodelcapaciteiten is dit model verbeterd voor: financiële verticale domeintoepassingen, financiële Q&A, kwantitatief programmeren, tool-calling en algemeen programmeren, met compatibiliteit met diverse agent-platforms.

Ondersteunt gratis lokale deployering op mainstrain inferentieframeworks zoals llama.cpp, Ollama, LM Studio en meer.

**Releasedatum: 2026-08-30** | **Versie: V3.8**

## Modelfuncties

- **🧠 Dynamisch Zeven-Dimensionaal Denkkader**: Zelfontwikkeld kernredeneerframework van MoziAI. Geeft bij elke taak eerst het **moziAI-Think**-label uit en ontvouwt gestructureerd denken dynamisch op basis van taakcomplexiteit — van tweedimensionaal snelantwoord (Level 0) via vijfdimensionale beoordeling (Level 1) tot volledig zeven-dimensionaal diep redeneren (Level 2): ①Taakbegrip ②Complexiteitsbeoordeling ③Afhankelijkheidsanalyse ④Risicobeoordeling ⑤Bronbehoeften ⑥Acceptatiecriteria ⑦Uitvoeringsstrategie.
- **🧠 Agent LOOP Iteratiemechanisme**: Bij complexe taken schakelt MoziAI automatisch over op de **moziAI-Loop** iteratiemodus: Ronde 1 uitvoering + beoordeling → Ronde 2 aanpassing + verificatie, waarbij de uitvoer zelf wordt geverifieerd voordat het definitieve antwoord wordt gegeven.
- **🧠 MoziSmartBit Intelligente Kwantisering**: Zelfontwikkelde hiërarchische intelligente kwantisering, optimale balans tussen precisie en grootte, gecomprimeerd naar ~12,79 GB met FP16 ~99% precisie.
- **🧠 Financieel Verticaal Domeinfocus**: Diepe optimalisatie voor financiële Q&A, kwantitatief programmeren en tool-calling.
- **Meertalige ondersteuning**: 201 talen en dialecten, bijzonder geoptimaliseerd Chinees, plus Engels, Japans, Koreaans, Duits, Frans, Spaans, Portugees en meer.
- **Algemene programmeercapaciteiten**: Full-stack ontwikkeling, code-debugging, architectuurontwerp, scriptcreatie — Python/JS/TS/Go/Rust.
- **Schrijfcapaciteiten**: Kwalitatief hoogwaardig schrijven in meerdere genres — onderzoeksrapporten, analytische artikelen, technische documentatie, creatieve inhoud.
- **Visueel begrip**: Multimodale visie, screenshots plakken in het chatvenster, het model begrijpt afbeeldingsinhoud.
- **Multi-frameworkondersteuning**: Compatibel met llama.cpp, Ollama, LM Studio, Jan en meer.
- **Multi-Agent platformondersteuning**: Diepe compatibiliteit met OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex, met native ondersteuning voor tool-calling en multi-turn taakorkestratie.

## Kernmogelijkheden

| Domein | Beschrijving |
| ----- | ------------------------------------------ |
| Marktanalyse | Macro-/micro-economische interpretatie, aandelen/grondstoffen/crypto-markten |
| Financiën & Rapporten | Financiële kerncijfers, rapportagesamenvattingen, waardering en winstprognoses |
| Risicobeheer & Compliance | Productrisicobeoordeling, beleggingsadvies-compliance, financiële regelgeving |
| Kwantitatief & Strategie | Kwantitatieve strategieontwerp, Pyramid/PEL-kwantisering, backtesting, factorconstructie |
| Tool-calling | Realtime marktgegevens, databases, rapportagezoeken |

## Technische specificaties

| Item | Parameters |
| ------ | ---------------------------------------------------------------------------------- |
| Basismodel | Qwen3.8-27B (Dense architectuur, hybride aandacht 16 full + 48 linear, MIT-licentie) |
| Parameterschaal | 27 miljard (27B) Dense architectuur |
| Kwantiseringmethode | Zelfontwikkeld MoziSmartBit-algoritme + GGUF standaardformaat |
| Contextlengte | 256K (262.144 tokens) |
| Modelgrootte | ~12,79 GB |
| Min. VRAM | **16GB+** deploybaar (met CPU offloading); **20GB+** soepele lange context; **24GB+** volledig 256K + visie |
| Inferentie-framework | llama.cpp / Ollama / LM Studio / Jan |
| Inferentiesnelheid | Met MTP: AMD R9700 GPU 70+ token/s, AMD MAX+395 iGPU 50+ token/s, AMD MAX+395 GPU 35+ token/s |
| Ontwikkelingsteam | Chen Yumo Team |

## Kwantiseringformaat en modelgrootte

| Formaat | Grootte | Precisie | Beschrijving |
| ---------------- | ------------- | --------- | ----------------- |
| FP16 (Origineel) | ~54 GB | 100% | Originele 16-bit precisie |
| **MoziSmartBit** | **~12,79 GB** | **~99%** | **Dit model gebruikt zelfontwikkelde intelligente kwantisering** |
| Q4_K_M | ~17 GB | ~98% | GGUF standaard 4-bit |
| Q5_K_M | ~20 GB | ~99% | Hogere precisie |
| Q6_K | ~23 GB | ~99,5% | Bijna verliesvrij |
| Q8_0 | ~31 GB | ~100% | Verliesvrij |

## MoziSmartBit Intelligente Kwantiseringstechnologie

Traditionele kwantiseringsschema's passen eenvormige precisie toe op alle lagen. De zelfontwikkelde **MoziSmartBit** past een intelligente gedifferentieerde kwantiseringstrategie toe die is afgestemd op de structurele kenmerken van Dense-modellen.

### Compressieresultaten

- **Minimale kwantiserverlies**: Trainingwinst > kwantisatieverlies
- **4,0x compressie**: Van FP16 (~54 GB) naar ~12,79 GB
- **Deploybaar op consumenten-GPUs**: 16 GB VRAM volstaat, 20 GB+ voor volledige 256K lange context

### Vergelijkingsvoordelen

**vs Q4_K_M (~17 GB)**: ~20% kleiner, hogere precisie, lagere VRAM-drempel

**vs FP16 origineel (~54 GB)**: ~4,0x compressieverhouding, ~99% precisie behouden

## Aanbevolen inferentieparameters

Gebaseerd op llama.cpp-officiële aanbevelingen en lokale optimalisatie (AMD Radeon AI PRO R9700 32GB):

| Parameter | Algemene chat | Coding/Agent | Beschrijving |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Balans tussen creativiteit en nauwkeurigheid |
| top\_p | 0,95 | 0,95 | Nucleus sampling drempel |
| top\_k | 20 | 20 | Afgeknot sampling |
| repeat\_penalty | 1,05 | 1,05 | Herhalingsstraf |
| presence\_penalty | 0 | 0 | Geen aanwezigheidsstraf |
| context\_length | 262144 | 262144 | 256K lange context |
| batch\_size | 2048 | 2048 | Batchgrootte |
| ubatch\_size | 512 | 512 | Micro-batchgrootte |
| flash\_attention | auto | auto | Automatisch Flash Attention |
| kv\_cache | q4\_0 | q4\_0 | KV-cache kwantisering |
| poll | 0 | 0 | Geen GPU-polling in rust, energiebesparend |
| reasoning | auto | auto | Redeneerketen (denkketen) activeren |
| reasoning\_budget | 400 | 400 | Redeneer tokenbudget |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Redeneerformaat |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | Sampler volgorde |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP-speculatieve decoding** |

> 💡 **Denkmodus**: Dit model bevat Qwen3.8 Thinking (denkketen). Geactiveerd via `--reasoning auto`.

## MTP-speculatieve decoding (Belangrijk kenmerk)

Dit model bevat ingebouwde MTP (Multi-Token Prediction) speculatieve decoding-lagen. Bij activering kan de inferentiesnelheid met **1,5-2x** worden verbeterd.

### MTP-principe

MTP traint een extra lichtgewicht voorspellingshoofd (Draft Model) dat volgende tokens voorspelt voordat het hoofdmodel ze verifieert.

### llama.cpp MTP-parameters

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Aanbevolen waarde | Beschrijving |
| --- | --- | --- |
| --spec-type | draft-mtp | MTP-speculatieve decoding activeren |
| --spec-draft-n-max | 2 | Max tokens geraden per stap (aanbevolen, acceptatiegraad ~80%) |
| --spec-draft-p-min | 0,75 | Minimale acceptatiekansdrempel |

### MTP-parameteraanbevelingen

| spec-draft-n-max | Acceptatiegraad | Gebruiksscenario |
| --- | --- | --- |
| 1 | ~90% | Meest conservatief |
| **2** | **~80%** | **Aanbevolen: balans snelheid/nauwkeurigheid** |
| 3 | ~71% | Algemene scenario's |
| 4-5 | ~60-65% | Creatief schrijven, codegeneratie |
| 6 | ~50-55% | Zuivere tekst-lange output |

## llama.cpp Opstartcommando

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

## VRAM-configuratie-aanbevelingen

| VRAM | Aanbevolen context | KV-cache | Visie-ondersteuning | Beschrijving |
| --- | --- | --- | --- | --- |
| 20 GB | 256K volledig | q4\_0 | Volledig | Visie+256K, aanbevolen configuratie |
| 24 GB | 256K volledig | q4\_0 | Volledig | Visie+256K, voldoende VRAM |
| 32 GB+ | 256K volledig | q4\_0 | Volledig | Visie+256K, sterkste configuratie |

**NVIDIA GPU**

| VRAM | GPU-model |
| --- | --- |
| 16 GB | RTX 4060 Ti (CPU offloading nodig) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD GPU**

| VRAM | GPU-model |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel GPU**

| VRAM | GPU-model |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (CPU offloading nodig) |

**CPU gedeeld geheugen / geïntegreerde GPU**

| VRAM | Processor |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395 (Radeon 8060S iGPU) |
| 128 GB | NVIDIA RTX Spark (Blackwell RTX GPU) |

> 💡 **Tip**: Elk merk en model wordt ondersteund zolang het VRAM voldoet.
> 💡 **Tip**: Langere context verbruikt meer VRAM. Bij OOM, verlaag `-c` geleidelijk. `--fit on` past automatisch aan.

## Ollama-deployering

```bash
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

## LM Studio / Jan deployering

Zoek direct naar `moziAI` in LM Studio / Jan en download de Q4_K_M-versie.

## Benchmark-evaluatie

### Programmeercapaciteiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73,0 | 63,4 | 64,0 | 51,7 | 78,2 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 | 51,2 | 53,4 |
| NL2Repo-Bench | 42,3 | 36,2 | 41,1 | -- | 47,6 |
| DeepSWE 1.1 | **42,2** | 13,3 | 14,2 | -- | -- |
| QwenSWEBench | **79,0** | 49,3 | 59,2 | -- | 63,8 |

### Agentcapaciteiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70,7** | 61,0 | 65,1 | -- | 68,2 |
| JobBench | **33,4** | 21,8 | 27,6 | -- | -- |
| Agents' Last Exam (Score) | **42,9** | 27,3 | 33,6 | -- | -- |
| WebArena-Verified | **64,8** | 48,8 | 55,3 | -- | -- |
| AndroidWorld | **81,9** | 70,3 | 81,0 | -- | 62,0 |

### Algemene capaciteiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79,5** | 69,1 | 79,1 | 77,0 | 62,5 |
| GPQA Diamond | 89,2 | 87,8 | 90,3 | 83,5 | **91,3** |

### Multimodale capaciteiten

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94,6** | 85,1 | 90,3 | -- | 65,5 |
| BabyVision (With CI) | **85,6** | 28,9 | 70,4 | -- | 12,6 |
| CharXiv RQ (With CI) | **90,2** | 78,4 | 85,8 | -- | 66,0 |
| OmniDocBench 1.5 | 91,1 | 89,4 | **91,4** | 75,8 | 86,6 |
| RealWorldQA | 85,9 | 84,1 | **86,9** | -- | 73,9 |
| Vision2Web | **62,9** | 45,0 | 42,1 | -- | -- |

## Modeldownload

| Platform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope (魔搭) | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

⚠️ **Belangrijk: Visievermogen vereist extra mmproj-bestand**

- **Visiebestand**: `moziAI-27B-3.8-mmproj-F16.gguf` (~927 MB, BF16 precisie)
- **Locatie**: In dezelfde versiemap als het GGUF-modelbestand
- **Laden**: Via `--mmproj` parameter bij het starten van llama-server

> Zonder het visiebestand gaat het afbeeldingsvermogen verloren.

## Snelstart

### 1. Modelbestanden downloaden

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # Hoofdmodel (vereist)
├── moziAI-27B-3.8-mmproj-F16.gguf              # Visieprojectie (optioneel)
└── chat-template-moziai-27B-v38.jinja           # Chattemplate (aanbevolen)
```

### 2. Inferentieservice starten

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

### 3. Gebruiken

Open `http://localhost:8080` in uw browser.

### Mappenstructuur

```
moziAI-27B/
├── README.md              # Dit bestand (Chinese documentatie)
├── README.en.md           # Engelse versie
├── LICENSE                # Licentie
├── V3.8/                  # V3.8 versie
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # Hoofdmodel
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # Visieprojectie
│   └── chat-template-moziai-27B-v38.jinja         # Chattemplate
```

## SEO-trefwoorden

Financieel AI-grootmodel, lokaal open-source model, MoziSmartBit, intelligente kwantisering, GGUF, Qwen3.8-27B, financieel verticaal domein, tool-calling, Agent, llama.cpp, Ollama, 256K lange context, multimodaal, lokaal LLM, edge AI, self-hosted AI, consumer GPU deployment, intelligent quantization

## Licentie (Belangrijk)

✅ **Toegestaan**: Gratis commercieel gebruik, kopiëren en verspreiden
❌ **Verboden**: Secundaire ontwikkeling, wederverkoop, sublicentiëren
📋 **Vereisten**: Auteursrechtvermelding behouden, bron: moziAI-27B

## Disclaimer

Dit model wordt "as is" geleverd zonder enige vorm van garantie.

## Contact

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
