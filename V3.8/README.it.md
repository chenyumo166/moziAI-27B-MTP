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

# MoziAI-27B-3.8 — Un modello AI multimodale compatto e potente, distribuibile localmente gratuitamente

[English](README.en.md) | [简体中文](README.zh.md) | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | Italiano | [Русский](README.ru.md) | [Español](README.es.md) | [Português](README.pt.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md) | [Polski](README.pl.md)

**Data di rilascio: 2026-08-30** · **Versione: V3.8**

---

## 📑 Indice

- [1. Panoramica del modello](#1-panoramica-del-modello)
- [2. Caratteristiche del modello](#2-caratteristiche-del-modello) — Pensiero dinamico a sette dimensioni / LOOP / MoziSmartBit / Focus finanziario
- [3. Note sull'aggiornamento della versione](#3-note-sullaggiornamento-della-versione)
- [4. Capacità principali](#4-capacità-principali)
- [5. Specifiche tecniche](#5-specifiche-tecniche)
- [6. ⚡ Avvio rapido](#6--avvio-rapido-3-file--100-delle-migliori-capacità-di-ragionamento) — **Download del trio di file**
- [7. Download del modello](#7-download-del-modello)
- [8. Comandi di avvio](#8-comandi-di-avvio)
- [9. Parametri di inferenza consigliati](#9-parametri-di-inferenza-consigliati)
- [10. Confronto dei formati di quantizzazione](#10-confronto-dei-formati-di-quantizzazione)
- [11. Decodifica speculativa MTP](#11-decodifica-speculativa-mtp-importante-funzionalità-di-accelerazione)
- [12. Configurazione VRAM](#12-configurazione-vram-consigliata)
- [13. Modalità di distribuzione](#13-modalità-di-distribuzione)
- [14. Benchmark](#14-benchmark)
- [15. Licenza](#15-licenza)
- [16. Contatti](#16-contatti)

---

## 1. Panoramica del modello

MoziAI-27B-3.8 è un modello AI multimodale open source sviluppato dal team di Chen Yumo, noto opinionista finanziario cinese, basato sul modello open source **Qwen3.8-27B** (architettura Dense 27B, licenza MIT) e combinato con dati finanziari sviluppati in proprio dal team, capacità nel settore finanziario, sistema di pensiero dinamico a sette dimensioni, meccanismo di riflessione e iterazione LOOP dell'agente e algoritmo di quantizzazione ibrida MoziSmartBit. Questo modello abbassa la soglia di distribuzione locale per privati e aziende, è autorizzato all'**uso commerciale gratuito**, può essere distribuito localmente su schede grafiche consumer, riducendo notevolmente i costi dei token cloud, garantendo 7×24 ore di libertà sui token e assicurando la privacy e la sicurezza dei dati locali.

---

## 2. Caratteristiche del modello

### 🧠 Sistema di pensiero dinamico a sette dimensioni

Il framework di ragionamento principale sviluppato da MoziAI. Di fronte a qualsiasi compito, il modello emette prima il marcatore **moziAI-Think** ed espande dinamicamente il pensiero strutturato in base alla complessità del compito:

| Livello | Scenari di utilizzo | Compiti tipici | Dimensioni di espansione |
| --- | --- | --- | --- |
| **Level 0** | Domande e risposte semplici | Spiegazione di termini, ricerche di fatti, traduzione, riassunti | ①Comprendere il compito ⑤Fabbisogno di risorse (risposta rapida a due dimensioni) |
| **Level 1** | Analisi e diagnosi | Ricerche di mercato, redazione di testi, analisi dei dati, interpretazione di report, valutazione di strategie | ①②③⑤⑥ Valutazione a cinque dimensioni |
| **Level 2** | Sviluppo/strategie complesse | Sviluppo di codice, progettazione di architetture, sviluppo di strategie quantitative, flussi di lavoro multi-step, progettazione di sistemi | ①②③④⑤⑥⑦ Deduzione profonda completa a sette dimensioni |

> Le sette dimensioni: ①Comprendere il compito ②Valutazione della complessità ③Relazioni di dipendenza ④Valutazione del rischio ⑤Fabbisogno di risorse ⑥Criteri di accettazione ⑦Strategia di esecuzione

### 🔄 Meccanismo di iterazione LOOP dell'agente

I compiti complessi entrano automaticamente nella modalità di iterazione **moziAI-Loop**: **1º ciclo esecuzione + valutazione → 2º ciclo regolazione + verifica**, garantendo che l'output venga sottoposto ad auto-verifica prima di fornire la risposta finale. Come un ingegnere esperto, il modello "scompone il problema → valuta la soluzione → esegue → riflette → ottimizza", migliorando significativamente l'accuratezza e l'eseguibilità dei compiti complessi. Per domande e compiti semplici, invece, il Loop viene disattivato automaticamente.

### 📦 Quantizzazione intelligente MoziSmartBit

Quantizzazione intelligente a strati sviluppata in proprio: il modello Dense da 27 miliardi di parametri viene compresso a circa **13.7 GB**, circa 3.3 GB (~20%) in meno rispetto al Q4_K_M standard (~17 GB), mantenendo una precisione FP16 di circa **~99%**. La quantizzazione tradizionale applica una precisione uniforme a tutti i layer; MoziSmartBit adotta invece una strategia intelligente e differenziata in base alle caratteristiche strutturali dei modelli Dense, con una precisione superiore al Q4_K_M.

### 💰 Focus sul settore verticale finanziario

Ottimizzazione profonda per domande e risposte finanziarie, programmazione quantitativa e chiamate a strumenti. Il settore finanziario ha una tolleranza estremamente bassa per le allucinazioni dei modelli; in questo ambito, MoziAI supera nettamente i modelli generici di pari dimensione.

### 🌐 Altre caratteristiche

- **Supporto multilingue**: 201 lingue e dialetti, con capacità in cinese particolarmente ottimizzate
- **Programmazione generica**: sviluppo full-stack, debug del codice, progettazione di architetture; copre Python/JS/TS/Go/Rust
- **Scrittura di articoli**: scrittura di alta qualità in più generi, tra cui report di ricerca, articoli di analisi, documentazione tecnica e contenuti creativi
- **Comprensione visiva**: visione multimodale, supporta la comprensione dei contenuti delle immagini tramite screenshot locali
- **Supporto multi-framework**: llama.cpp / Ollama / LM Studio / Jan
- **Supporto multi-Agent**: OpenClaw / Hermes / Cursor / Claude Code / Codex, ecc., con chiamate a strumenti native e orchestrazione di attività multi-turno

---

## 3. Note sull'aggiornamento della versione

Questo aggiornamento della versione potenzia principalmente: la modalità di ragionamento a pensiero dinamico a sette dimensioni + iterazione LOOP sviluppata da moziAI, che ora riconosce in modo più intelligente la complessità dei compiti, aumenta il tasso di completamento dei compiti complessi e migliora la capacità di "pensare prima di agire".

moziAI manterrà un ritmo attivo di aggiornamenti e iterazioni delle versioni, per stare al passo con l'evoluzione futura dell'intelligenza artificiale e, grazie alle tecnologie sviluppate internamente, rendere i modelli AI locali sempre più leggeri da distribuire e sempre più capaci.

---

## 4. Capacità principali

| Ambito di capacità | Descrizione |
| --- | --- |
| Analisi di mercato | Interpretazione macro/microeconomica, analisi dei mercati e della logica di A-shares/Hong Kong/USA/commodity/criptovalute |
| Finanza e report di ricerca | Interpretazione degli indicatori chiave dei bilanci, estrazione di sintesi dai report, supporto alla valutazione e alle previsioni degli utili |
| Gestione del rischio e conformità | Valutazione del rischio dei prodotti, avvisi di conformità per i consigli di investimento, interpretazione delle politiche di regolamentazione finanziaria |
| Quantitativo e strategie | Progettazione di idee per strategie quantitative, quantitativo con Pyramid (PEL), logica di backtest, costruzione di fattori e chiamate a strumenti |
| Chiamate a strumenti | Può collegarsi a fonti di dati finanziari come quotazioni in tempo reale, database e ricerca di report |

---

## 5. Specifiche tecniche

| Voce | Parametro |
| --- | --- |
| Modello base | Qwen3.8-27B (architettura Dense, attenzione ibrida 16 full + 48 linear, licenza MIT) |
| Dimensione dei parametri | 27 miliardi (27B), architettura Dense |
| Metodo di quantizzazione | Quantizzazione intelligente MoziSmartBit sviluppata in proprio + formato standard GGUF |
| Lunghezza del contesto | 128K (262,144 tokens) |
| Dimensioni del modello | ~13.7 GB |
| VRAM minima | **16GB+** distribuibile (offload CPU); **20GB+** per contesto lungo fluido; **24GB+** per 128K completo + visione |
| Framework di inferenza | llama.cpp / Ollama / LM Studio / Jan |
| Velocità di inferenza | Con decodifica speculativa MTP: R9700 fino a 70+ tok/s, iGPU MAX+395 fino a 50+ tok/s, GPU fino a 35+ tok/s |
| Team di sviluppo | Team di Chen Yumo |

---

## 6. ⚡ Avvio rapido (3 file = attivazione al 100% delle migliori capacità di ragionamento)

> ⚠️ **Nota fondamentale**: le migliori capacità di ragionamento di MoziAI richiedono il download **simultaneo di 3 file** — modello principale, proiezione visiva e template di chat. La mancanza di uno qualsiasi comporta la perdita della capacità corrispondente.

### 6.1 Download dei file del modello

Scarica **tutti i file nella directory V3.8** da HuggingFace / ModelScope nella stessa directory locale:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← 主模型（必选，13.7 GB）
└── chat-template-moziai-27B-V3.8.jinja         ← 聊天模板（必选，含七维思考+Loop指令）

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf            ← 视觉投影（必选，927 MB）
```

| File | Dimensioni | Necessità | Funzione |
| --- | --- | --- | --- |
| Modello principale `.gguf` | ~13.7 GB | **Obbligatorio** | Pesi del modello, capacità di ragionamento principale |
| Proiezione visiva `mmproj` | ~927 MB | **Obbligatorio** | Comprensione visiva multimodale; senza il caricamento si perde la capacità di elaborazione delle immagini |
| Template di chat `.jinja` | Minimo | **Obbligatorio** | Inietta le istruzioni di identità MoziAI + pensiero a sette dimensioni + meccanismo LOOP |

### 6.2 Avvio e utilizzo

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Apri `http://localhost:8080` nel browser per iniziare la conversazione. Per i parametri consigliati completi, vedere la sezione 9.

---

## 7. Download del modello

| Piattaforma | Indirizzo |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master) |

> 💡 **Utenti LM Studio**: cercate `moziAI` in [LM Studio](https://lmstudio.ai) per scaricare con un clic, senza dover scaricare manualmente i file.

---

## 8. Comandi di avvio

### Avvio minimale (con il trio di file)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Avvio consigliato completo

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
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

> 💡 Disattivazione di MTP: rimuovete `--spec-type draft-mtp` e i parametri correlati; la velocità diminuisce di circa il 30-50%, ma l'occupazione di VRAM è inferiore.

---

## 9. Parametri di inferenza consigliati

Basati sui parametri consigliati ufficiali di llama.cpp e su ottimizzazioni testate localmente (AMD Radeon AI PRO R9700 32GB):

| Parametro | Chat generica | Coding/Agent | Descrizione |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Bilancia creatività e accuratezza |
| top\_p | 0.95 | 0.95 | Soglia del campionamento nucleare (top-p) |
| top\_k | 20 | 20 | Campionamento con troncamento |
| repeat\_penalty | 1.05 | 1.05 | Penalità di ripetizione |
| context\_length | 262144 | 262144 | Contesto lungo 128K |
| reasoning | auto | auto | Attiva la catena di ragionamento (chain of thought) |
| reasoning\_budget | 400 | 400 | Budget di token per il ragionamento |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Output del ragionamento in un campo separato |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Decodifica speculativa MTP (vedi sezione 11)** |

> 💡 **Modalità di pensiero**: si attiva con `--reasoning auto`; il modello svolge prima il ragionamento interno e poi emette la risposta. `reasoning_budget` controlla il numero massimo di token di pensiero (consigliato 400, regolabile da 100 a 1000).

---

## 10. Confronto dei formati di quantizzazione

| Formato | Dimensioni | Precisione | Descrizione |
| --- | --- | --- | --- |
| FP16 originale | ~54 GB | 100% | Senza perdite, richiede schede grafiche professionali |
| **MoziSmartBit (questo modello)** | **~13.7 GB** | **~99%** | **Quantizzazione intelligente proprietaria, precisione ottimale e dimensioni minime** |
| Q4_K_M | ~17 GB | ~98% | 4bit standard GGUF |
| Q5_K_M | ~20 GB | ~99% | Precisione superiore |
| Q6_K | ~23 GB | ~99.5% | Quasi senza perdite |
| Q8_0 | ~31 GB | ~100% | Senza perdite |

> MoziSmartBit comprime il modello Dense 27B a 13.7 GB (rapporto di compressione 3.9x) mantenendo circa il 99% di precisione, risultando circa il 20% più piccolo del Q4_K_M e più adatto alla distribuzione locale su schede grafiche consumer.

---

## 11. Decodifica speculativa MTP (importante funzionalità di accelerazione)

Questo modello integra il livello di decodifica speculativa MTP (Multi-Token Prediction); una volta attivato, la velocità di inferenza aumenta di **1.5-2 volte**. Si tratta di una funzionalità nativa dell'architettura Qwen3.8 e MoziAI ha conservato tutti i pesi MTP.

**Principio**: nell'architettura del modello è stato addestrato un ulteriore head di previsione leggero (Draft Model) che anticipa i token successivi prima della verifica da parte del modello principale, riducendo il numero di passate forward e la latenza di inferenza. Gli errori di previsione vengono corretti dal modello principale, senza effetti negativi sulla qualità dell'output.

### Parametri di attivazione

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parametro | Valore consigliato | Descrizione |
| --- | --- | --- |
| --spec-type | draft-mtp | Abilita la decodifica speculativa MTP |
| --spec-draft-n-max | 2 | Massimo 2 token previsti per volta (valore consigliato, tasso di accettazione ~80%) |
| --spec-draft-p-min | 0.75 | Soglia minima di probabilità di accettazione (0.0-1.0, più alto è più conservativo) |

### Suggerimenti per la regolazione dei parametri

| n-max | Tasso di accettazione | Scenari di utilizzo |
| --- | --- | --- |
| 1 | ~90% | Il più conservativo, miglioramento minimo della velocità |
| **2** | **~80%** | **Consigliato: equilibrio tra velocità e accuratezza** |
| 3 | ~71% | Scenari generici, miglioramento evidente della velocità |
| 4-5 | ~60-65% | Scrittura creativa, generazione di codice |
| 6 | ~50-55% | Output lunghi di solo testo (da regolare insieme a p-min) |

---

## 12. Configurazione VRAM consigliata

| VRAM | Configurazione consigliata | Descrizione |
| --- | --- | --- |
| 16 GB | Contesto ridotto a 64K, richiede offload CPU | Livello base, ad es. RTX 4060 Ti |
| **20 GB** | **128K completo, cache KV q4_0** | **Configurazione consigliata**, ad es. RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K completo, ampio margine di VRAM | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K completo, configurazione più potente | Radeon AI PRO R9700 / RTX 5090 |
| iGPU 128 GB | 128K completo | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Più lungo è il contesto, maggiore è l'occupazione di VRAM. In caso di OOM, riducete gradualmente il parametro `-c`. Usate `--fit on` per far adattare automaticamente a llama.cpp il numero di layer in base alla VRAM disponibile. Supporta schede grafiche di tutti i marchi: NVIDIA / AMD / Intel.

---

## 13. Modalità di distribuzione

### Distribuzione con Ollama

```bash
cat > Modelfile << 'EOF'
FROM ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf
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

Cercate `moziAI` in LM Studio / Jan e scaricate la versione quantizzata Q4\_K\_M.

> 💡 Il supporto di Ollama per mmproj e chat\_template è limitato; si consiglia di usare preferibilmente llama.cpp per disporre di tutte le funzionalità.

---

## 14. Benchmark

MoziAI-27B-3.8 è un fine-tuning basato sul modello base Qwen3.8-27B, con il settore verticale finanziario come direzione di ottimizzazione principale.

### Capacità di coding

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Capacità Agent

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Capacità generali

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Capacità multimodali

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> I dati dei modelli concorrenti provengono dai risultati di benchmark ufficialmente pubblicati. Nel settore verticale finanziario (interpretazione dei bilanci, strategie quantitative, gestione del rischio e conformità, chiamate a strumenti Agent, ecc.) MoziAI supera nettamente i modelli generici.

---

## 15. Licenza

Questo modello è rilasciato con una **licenza restrittiva personalizzata**:

- ✅ **Consentito** — uso commerciale gratuito, copia e distribuzione
- ❌ **Vietato** — sviluppo derivato, rivendita, sub-licenza
- 📋 **Richiesto** — conservare l'avviso di copyright originale e indicare la fonte: moziAI-27B

Questo modello è fornito "così com'è", senza garanzie di alcun tipo. Gli output del modello sono solo a scopo informativo e non costituiscono consigli di investimento. L'utente si assume tutti i rischi derivanti dall'utilizzo.

Per i termini completi, fare riferimento al file [LICENSE](LICENSE).

---

## 16. Contatti

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. Tutti i diritti riservati.
