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

# MoziAI-27B-3.8 - Modello AI multimodale piccolo ma potente, deployabile localmente gratuitamente

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | Italiano | [Русский](README.ru.md)

## Panoramica del modello

MoziAI-27B-3.8 è un grande modello AI multimodale open-source locale sviluppato dal team dell'influencer finanziario cinese Chen Yumo (potenziato per il dominio finanziario, supporto visione, tool calling, deploy locale su GPU consumer). moziAI-27B-3.8 è basato sul modello base open-source Qwen3.8-27B (architettura Dense 27B, licenza MIT), integrando le tecnologie auto-sviluppate dal team Chen Yumo (dati finanziari + capacità dominio finanziario + metodi di addestramento + Framework di Pensiero Sette-Dimensionale Dinamico + Meccanismo di Iterazione LOOP dell'agente + Algoritmo di quantizzazione ibrida MoziSmartBit). Riduce le barriere del deploy locale per privati e aziende, con licenza commerciale gratuita. Il deploy locale su GPU consumer risparmia significativamente i costi dei token cloud, realizzando la libertà dei token 24/7 garantendo privacy e sicurezza dei dati locali.

**Framework di Pensiero Sette-Dimensionale Dinamico + Meccanismo di Iterazione LOOP dell'agente**: La modalità di ragionamento principale auto-sviluppata da MoziAI. Valuta intelligentemente la complessità dei compiti — compiti semplici attivano il pensiero bidimensionale per risposte rapide, compiti di complessità media utilizzano il pensiero pentadimensionale, compiti altamente complessi attivano il pensiero sette-dimensionale completo con il meccanismo di iterazione LOOP di riflessione.

**Attraverso la tecnologia di quantizzazione intelligente MoziSmartBit auto-sviluppata**, il modello Dense da 27 miliardi di parametri viene compresso a circa 12,79 GB, 3,3 GB (circa 20%) più piccolo dei modelli di quantizzazione Q4_K_M convenzionali (~17 GB); equilibrio ottimale tra precisione e dimensione con ~99% della qualità di precisione FP16.

Oltre a mantenere le capacità generali dei grandi modelli AI, questo modello è stato potenziato per: applicazioni di dominio verticale finanziario, Q&R finanziari, programmazione quantitativa, tool calling e programmazione generale, con compatibilità con varie piattaforme di agenti.

**Data di rilascio: 2026-08-30** | **Versione: V3.8**

## Funzionalità del modello

- **🧠 Framework di Pensiero Sette-Dimensionale Dinamico**: Framework di ragionamento principale auto-sviluppato da MoziAI. Di fronte a qualsiasi compito, il modello emette prima il tag **moziAI-Think**, sviluppando dinamicamente il pensiero strutturato in base alla complessità — da risposta bidimensionale rapida (Level 0) a valutazione pentadimensionale (Level 1) fino al ragionamento profondo sette-dimensionale completo (Level 2): ①Comprensione del compito ②Valutazione della complessità ③Analisi delle dipendenze ④Valutazione dei rischi ⑤Risorse necessarie ⑥Criteri di accettazione ⑦Strategia di esecuzione.
- **🧠 Meccanismo di Iterazione LOOP dell'agente**: Per compiti complessi, MoziAI entra automaticamente in modalità iterativa **moziAI-Loop**: Turno 1 esecuzione + valutazione → Turno 2 aggiustamento + verifica.
- **🧠 Quantizzazione Intelligente MoziSmartBit**: Quantizzazione gerarchica intelligente auto-sviluppata, equilibrio ottimale precisione/dimensione, compresso a ~12,79 GB con FP16 ~99% di precisione.
- **🧠 Focus sul dominio verticale finanziario**: Ottimizzazione profonda per Q&R finanziari, programmazione quantitativa e tool calling.
- **Supporto multilingue**: 201 lingue e dialetti, cinese particolarmente ottimizzato, più inglese, giapponese, coreano, tedesco, francese, spagnolo, portoghese e altri.
- **Capacità di programmazione generale**: Full-stack, debug, architettura, scripting — Python/JS/TS/Go/Rust.
- **Capacità di scrittura**: Scrittura di alta qualità multi-genere — report di ricerca, articoli analitici, documentazione tecnica, contenuti creativi.
- **Comprensione visiva**: Visione multimodale, screenshot incollati nella finestra chat.
- **Supporto multi-framework**: Compatibile con llama.cpp, Ollama, LM Studio, Jan e altri.
- **Supporto multi-piattaforma Agent**: Compatibilità profonda con OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex.

## Capacità principali

| Dominio | Descrizione |
| ----- | ------------------------------------------ |
| Analisi di mercato | Interpretazione macro/micro-economica, mercati azionari/commodities/crypto |
| Finanze & Report | Indicatori finanziari, sintesi report, valutazione e previsioni |
| Controllo rischi & Compliance | Valutazione rischi prodotto, conformità consigli investimento, regolamentazione |
| Quantitativo & Strategia | Design strategie quantitative, quantizzazione Pyramid/PEL, backtesting |
| Tool calling | Dati mercato in tempo reale, database, ricerca report |

## Specifiche tecniche

| Elemento | Parametri |
| ------ | ---------------------------------------------------------------------------------- |
| Modello base | Qwen3.8-27B (architettura Dense, attenzione ibrida 16 full + 48 linear, licenza MIT) |
| Scala parametri | 27 miliardi (27B) architettura Dense |
| Metodo di quantizzazione | Algoritmo MoziSmartBit auto-sviluppato + formato standard GGUF |
| Lunghezza contesto | 256K (262.144 token) |
| Dimensione modello | ~12,79 GB |
| VRAM minimo | **16GB+** deployabile (con CPU offloading); **20GB+** contesto lungo fluido; **24GB+** 256K completo + visione |
| Framework inferenza | llama.cpp / Ollama / LM Studio / Jan |
| Velocità inferenza | Con MTP: AMD R9700 GPU 70+ token/s, AMD MAX+395 iGPU 50+ token/s, AMD MAX+395 GPU 35+ token/s |
| Team di sviluppo | Team Chen Yumo |

## Formato quantizzazione e dimensione modello

| Formato | Dimensione | Precisione | Descrizione |
| ---------------- | ------------- | --------- | ----------------- |
| FP16 (Originale) | ~54 GB | 100% | Precisione originale 16 bit |
| **MoziSmartBit** | **~12,79 GB** | **~99%** | **Questo modello utilizza quantizzazione intelligente auto-sviluppata** |
| Q4_K_M | ~17 GB | ~98% | Standard GGUF 4 bit |
| Q5_K_M | ~20 GB | ~99% | Precisione superiore |
| Q6_K | ~23 GB | ~99,5% | Quasi senza perdita |
| Q8_0 | ~31 GB | ~100% | Senza perdita |

## Tecnologia di quantizzazione intelligente MoziSmartBit

I schemi tradizionali applicano precisione uniforme a tutti i livelli. La **MoziSmartBit** adotta una strategia di quantizzazione differenziata intelligente adatta alle caratteristiche strutturali dei modelli Dense.

### Risultati di compressione

- **Perdita di precisione minima**: Guadagno di addestramento > perdita di quantizzazione
- **Compressione 4,0x**: Da FP16 (~54 GB) a ~12,79 GB
- **Deployabile su GPU consumer**: 16 GB VRAM sufficienti, 20 GB+ per contesto lungo 256K completo

### Vantaggi comparativi

**vs Q4_K_M (~17 GB)**: ~20% più piccolo, precisione superiore, soglia VRAM più bassa

**vs FP16 originale (~54 GB)**: Rapporto di compressione ~4,0x, ~99% di precisione mantenuta

## Parametri di inferenza consigliati

Basati sulle raccomandazioni ufficiali llama.cpp e ottimizzazione locale (AMD Radeon AI PRO R9700 32GB):

| Parametro | Chat generale | Codifica/Agent | Descrizione |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Equilibrio creatività/precisione |
| top\_p | 0,95 | 0,95 | Soglia nucleus sampling |
| top\_k | 20 | 20 | Sampling troncato |
| repeat\_penalty | 1,05 | 1,05 | Penalità ripetizione |
| presence\_penalty | 0 | 0 | Nessuna penalità presenza |
| context\_length | 262144 | 262144 | Contesto lungo 256K |
| batch\_size | 2048 | 2048 | Dimensione batch |
| ubatch\_size | 512 | 512 | Dimensione micro-batch |
| flash\_attention | auto | auto | Flash Attention automatico |
| kv\_cache | q4\_0 | q4\_0 | Quantizzazione cache KV |
| poll | 0 | 0 | Nessun polling GPU inattivo, risparmio energetico |
| reasoning | auto | auto | Catena di ragionamento |
| reasoning\_budget | 400 | 400 | Budget token ragionamento |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Formato ragionamento |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | Ordine samplers |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Decodifica speculativa MTP** |

> 💡 **Nota modalità pensiero**: Questo modello include Qwen3.8 Thinking (catena di pensiero). Attivato via `--reasoning auto`.

## Decodifica speculativa MTP (Funzionalità di accelerazione importante)

Questo modello include strati di decodifica speculativa MTP (Multi-Token Prediction) integrati. Quando attivata, la velocità di inferenza può migliorare di **1,5-2x**.

### Principio MTP

MTP addestra una testa di predizione leggera (Draft Model) aggiuntiva che predice i token successivi prima della validazione del modello principale.

### Parametri MTP per llama.cpp

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parametro | Valore consigliato | Descrizione |
| --- | --- | --- |
| --spec-type | draft-mtp | Abilita decodifica speculativa MTP |
| --spec-draft-n-max | 2 | Max token indovinati per passo (consigliato, tasso accettazione ~80%) |
| --spec-draft-p-min | 0,75 | Soglia probabilità minima accettazione |

### Guida parametri MTP

| spec-draft-n-max | Tasso accettazione | Caso d'uso |
| --- | --- | --- |
| 1 | ~90% | Più conservativo |
| **2** | **~80%** | **Consigliato: equilibrio velocità/precisione** |
| 3 | ~71% | Scenari generali |
| 4-5 | ~60-65% | Scrittura creativa, generazione codice |
| 6 | ~50-55% | Output testo lungo puro |

## Comando di avvio llama.cpp

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

## Raccomandazioni configurazione VRAM

| VRAM | Contesto consigliato | KV cache | Supporto visione | Descrizione |
| --- | --- | --- | --- | --- |
| 20 GB | 256K completo | q4\_0 | Supporto completo | Visione+256K, configurazione consigliata |
| 24 GB | 256K completo | q4\_0 | Supporto completo | Visione+256K, VRAM sufficiente |
| 32 GB+ | 256K completo | q4\_0 | Supporto completo | Visione+256K, configurazione più potente |

**GPU NVIDIA**

| VRAM | Modello GPU |
| --- | --- |
| 16 GB | RTX 4060 Ti (CPU offloading necessario) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**GPU AMD**

| VRAM | Modello GPU |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**GPU Intel**

| VRAM | Modello GPU |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (CPU offloading necessario) |

**CPU con memoria condivisa / GPU integrata**

| VRAM | Processore |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395 (Radeon 8060S iGPU) |
| 128 GB | NVIDIA RTX Spark (Blackwell RTX GPU) |

> 💡 **Suggerimento**: Qualsiasi marca e modello è supportato se il VRAM è sufficiente.
> 💡 **Suggerimento**: Contesti più lunghi consumano più VRAM. In caso di OOM, ridurre gradualmente `-c`. `--fit on` regola automaticamente i livelli.

## Deploy Ollama

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

## Deploy LM Studio / Jan

Cerca direttamente `moziAI` in LM Studio / Jan e scarica la versione Q4_K_M.

## Valutazione Benchmark

### Capacità di codifica

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73,0 | 63,4 | 64,0 | 51,7 | 78,2 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 | 51,2 | 53,4 |
| NL2Repo-Bench | 42,3 | 36,2 | 41,1 | -- | 47,6 |
| DeepSWE 1.1 | **42,2** | 13,3 | 14,2 | -- | -- |
| QwenSWEBench | **79,0** | 49,3 | 59,2 | -- | 63,8 |

### Capacità Agent

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70,7** | 61,0 | 65,1 | -- | 68,2 |
| JobBench | **33,4** | 21,8 | 27,6 | -- | -- |
| Agents' Last Exam (Score) | **42,9** | 27,3 | 33,6 | -- | -- |
| WebArena-Verified | **64,8** | 48,8 | 55,3 | -- | -- |
| AndroidWorld | **81,9** | 70,3 | 81,0 | -- | 62,0 |

### Capacità generali

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79,5** | 69,1 | 79,1 | 77,0 | 62,5 |
| GPQA Diamond | 89,2 | 87,8 | 90,3 | 83,5 | **91,3** |

### Capacità multimodali

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94,6** | 85,1 | 90,3 | -- | 65,5 |
| BabyVision (With CI) | **85,6** | 28,9 | 70,4 | -- | 12,6 |
| CharXiv RQ (With CI) | **90,2** | 78,4 | 85,8 | -- | 66,0 |
| OmniDocBench 1.5 | 91,1 | 89,4 | **91,4** | 75,8 | 86,6 |
| RealWorldQA | 85,9 | 84,1 | **86,9** | -- | 73,9 |
| Vision2Web | **62,9** | 45,0 | 42,1 | -- | -- |

## Download del modello

| Piattaforma | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope (魔搭) | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

⚠️ **Importante: La capacità visiva richiede il caricamento aggiuntivo del file mmproj**

- **File visione**: `moziAI-27B-3.8-mmproj-F16.gguf` (~927 MB, precisione BF16)
- **Posizione**: Nella stessa directory di versione del file modello GGUF
- **Caricamento**: Tramite parametro `--mmproj` all'avvio di llama-server

> Senza caricare il file visione si perde la capacità di comprensione delle immagini.

## Inizio rapido

### 1. Scarica i file del modello

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # Modello principale (obbligatorio)
├── moziAI-27B-3.8-mmproj-F16.gguf              # Proiezione visione (opzionale)
└── chat-template-moziai-27B-v38.jinja           # Template chat (consigliato)
```

### 2. Avvia il servizio di inferenza

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

### 3. Inizia a usare

Apri `http://localhost:8080` nel browser.

### Struttura directory

```
moziAI-27B/
├── README.md              # Questo file (documentazione cinese)
├── README.en.md           # Versione inglese
├── LICENSE                # Licenza
├── V3.8/                  # Versione V3.8
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # Modello principale
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # Proiezione visione
│   └── chat-template-moziai-27B-v38.jinja         # Template chat
```

## Parole chiave SEO

Modello AI finanziario, modello open-source locale, MoziSmartBit, quantizzazione intelligente, GGUF, Qwen3.8-27B, dominio verticale finanziario, tool calling, Agent, llama.cpp, Ollama, contesto lungo 256K, multimodale, LLM locale, edge AI, self-hosted AI, consumer GPU deployment, intelligent quantization

## Licenza (Importante)

✅ **Consentito**: Uso commerciale gratuito, copia e distribuzione
❌ **Proibito**: Sviluppo secondario, rivendita, sotto-licenza
📋 **Requisiti**: Mantenere la nota copyright, attribuzione: moziAI-27B

## Disclaimer

Questo modello è fornito "così com'è" senza alcuna garanzia.

## Contatti

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
