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

# MoziAI-27B-3.8 — een klein maar krachtig multimodaal AI-model dat gratis lokaal kan worden ingezet

[English](README.en.md) | [简体中文](README.zh.md) | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | Nederlands | [Italiano](README.it.md) | [Русский](README.ru.md)

**Publicatiedatum: 2026-08-30** · **Versie: V3.8**

---

## 📑 Inhoudsopgave

- [1. Modeloverzicht](#1-modeloverzicht)
- [2. Kenmerken van het model](#2-kenmerken-van-het-model) — Dynamisch zeven-dimensioneel denken / LOOP / MoziSmartBit / Financiële focus
- [3. Versie-upgrade-informatie](#3-versie-upgrade-informatie)
- [4. Kernmogelijkheden](#4-kernmogelijkheden)
- [5. Technische specificaties](#5-technische-specificaties)
- [6. ⚡ Snel starten (3 bestanden = 100% activatie van de beste redeneercapaciteiten)](#6--snel-starten-3-bestanden--100-activatie-van-de-beste-redeneercapaciteiten) — **drie bestanden downloaden**
- [7. Modeldownload](#7-modeldownload)
- [8. Startopdrachten](#8-startopdrachten)
- [9. Aanbevolen inferentieparameters](#9-aanbevolen-inferentieparameters)
- [10. Vergelijking van kwantiseringsformaten](#10-vergelijking-van-kwantiseringsformaten)
- [11. MTP-speculatieve decodering (belangrijke versnellingsfunctie)](#11-mtp-speculatieve-decodering-belangrijke-versnellingsfunctie)
- [12. Aanbevolen VRAM-configuraties](#12-aanbevolen-vram-configuraties)
- [13. Implementatiemethoden](#13-implementatiemethoden)
- [14. Benchmark-evaluaties](#14-benchmark-evaluaties)
- [15. Licentie](#15-licentie)
- [16. Contact](#16-contact)

---

## 1. Modeloverzicht

MoziAI-27B-3.8 is een lokaal open-source multimodaal AI-model van groot formaat, ontwikkeld door het team van de Chinese financiële influencer Chen Yumo, gebaseerd op het open-source basismodel **Qwen3.8-27B** (Dense 27B-architectuur, MIT-licentie), gecombineerd met door het team zelf ontwikkelde financiële data + financiële domeincapaciteiten + een dynamisch zeven-dimensioneel denksysteem + een Agent-LOOP-reflectie- en iteratiemechanisme + het MoziSmartBit hybride kwantiseringsalgoritme. Dit model verlaagt de drempel voor lokale implementatie voor particulieren en bedrijven, is **gratis voor commercieel gebruik**, kan lokaal worden ingezet op consumenten-gpu's, bespaart aanzienlijke cloud-tokenkosten, realiseert 7×24 uur tokenvrijheid en waarborgt de privacy en veiligheid van lokale gegevens.

---

## 2. Kenmerken van het model

### 🧠 Dynamisch zeven-dimensioneel denksysteem

Het door MoziAI zelf ontwikkelde kernredeneerkader. Bij elke taak voert het model eerst de **moziAI-Think**-markering uit en ontvouwt het gestructureerd denken op basis van de taakcomplexiteit:

| Niveau | Toepassingsscenario | Typische taken | Uitgebreide dimensies |
| --- | --- | --- | --- |
| **Level 0** | Eenvoudige vraag-en-antwoord | Termuitleg, feitelijke opzoekingen, vertaling, samenvatting | ①Taakbegrip ⑤Resourcevereisten (tweedimensionaal snel antwoord) |
| **Level 1** | Analyse en diagnose | Marktonderzoek, tekstproductie, data-analyse, interpretatie van onderzoeksrapporten, strategie-evaluatie | ①②③⑤⑥ vijf dimensies evaluatie |
| **Level 2** | Complexe ontwikkeling/strategie | Codeontwikkeling, architectuurontwerp, ontwikkeling van kwantitatieve strategieën, meerstaps workflows, systeemontwerp | ①②③④⑤⑥⑦ volledige zeven dimensies diepgaande afweging |

> Zeven dimensies: ①Taakbegrip ②Complexiteitsbeoordeling ③Afhankelijkheden ④Risicobeoordeling ⑤Resourcevereisten ⑥Acceptatiecriteria ⑦Uitvoeringsstrategie

### 🔄 Agent-LOOP-iteratiemechanisme

Complexe taken gaan automatisch over in de **moziAI-Loop**-iteratiemodus: **ronde 1 uitvoeren + evalueren → ronde 2 aanpassen + verifiëren**, zodat de output pas na zelfcontrole als definitief antwoord wordt gegeven. Het model werkt als een senior ingenieur: 'probleem ontleden → oplossing evalueren → uitvoeren → reflecteren → optimaliseren', wat de nauwkeurigheid en uitvoerbaarheid van complexe taken aanzienlijk verbetert. Voor eenvoudige vragen en taken wordt Loop automatisch uitgeschakeld.

### 📦 MoziSmartBit slimme kwantisering

Zelf ontwikkelde gelaagde slimme kwantisering: het Dense-model met 27 miljard parameters wordt gecomprimeerd tot ongeveer **13,7 GB**, ongeveer 3,3 GB (~20%) kleiner dan reguliere Q4_K_M (~17 GB), met behoud van **~99%** van de FP16-precisie. Traditionele kwantisering gebruikt een uniforme precisie voor alle lagen; MoziSmartBit past een slimme gedifferentieerde strategie toe op basis van de structuurkenmerken van Dense-modellen, met een betere precisie dan Q4_K_M.

### 💰 Focus op het financiële verticale domein

Diepgaande optimalisatie voor financiële vraag-en-antwoord, kwantitatieve programmering en toolaanroepen. Het financiële domein tolereert modelhallucinaties uiterst slecht; MoziAI presteert in dit domein aanzienlijk beter dan algemene modellen van vergelijkbare omvang.

### 🌐 Overige kenmerken

- **Meertalige ondersteuning**: 201 talen en dialecten, met speciale optimalisatie voor het Chinees
- **Algemeen programmeren**: full-stack ontwikkeling, codedebugging, architectuurontwerp, met ondersteuning voor Python/JS/TS/Go/Rust
- **Artikel schrijven**: hoogwaardig schrijven in diverse genres: onderzoeksrapporten, analyses, technische documentatie, creatieve content
- **Visueel begrip**: multimodale visie, ondersteunt lokale schermafbeeldingen voor het begrijpen van beeldinhoud
- **Meerdere frameworks**: llama.cpp / Ollama / LM Studio / Jan
- **Meerdere Agents**: OpenClaw / Hermes / Cursor / Claude Code / Codex en meer, met native toolaanroepen en meerronde taakorkestratie

---

## 3. Versie-upgrade-informatie

Deze versie-upgrade richt zich voornamelijk op het door moziAI zelf ontwikkelde dynamische zeven-dimensionele denken + LOOP-iteratiemodel voor redeneren, waardoor de taakcomplexiteit intelligenter wordt herkend, de voltooiingsgraad van complexe taken hoger ligt en het vermogen om 'eerst te denken, dan te doen' wordt verbeterd.

moziAI blijft actief versie-upgrades en iteraties publiceren om gelijke tred te houden met de toekomstige ontwikkeling van kunstmatige intelligentie, en maakt lokale AI-modellen steeds lichter implementeerbaar en steeds capabeler door voortdurende zelfontwikkelde technologieën.

---

## 4. Kernmogelijkheden

| Capaciteitsdomein | Beschrijving |
| --- | --- |
| Marktanalyse | Macro-/micro-economische interpretatie, overzicht en logica van A-aandelen/HK-aandelen/US-aandelen/grondstoffen/cryptovaluta |
| Financiën en onderzoeksrapporten | Interpretatie van belangrijke financiële kengetallen, extractie van samenvattingen van onderzoeksrapporten, ondersteuning bij waardering en winstprognoses |
| Risicobeheer en compliance | Productrisicobeoordeling, compliancewaarschuwingen bij beleggingsadvies, interpretatie van financiële regelgeving |
| Kwantitatief en strategie | Ontwerp van kwantitatieve strategieën, Pyramid (Pyramid/PEL) kwantitatieve handel, backtestlogica, factorconstructie en toolaanroepen |
| Toolaanroepen | Aansluiting op financiële databronnen zoals realtime marktgegevens, databases en zoekopdrachten in onderzoeksrapporten |

---

## 5. Technische specificaties

| Item | Parameter |
| --- | --- |
| Basismodel | Qwen3.8-27B (Dense-architectuur, hybride aandacht 16 full + 48 linear, MIT-licentie) |
| Parametergrootte | 27 miljard (27B) Dense-architectuur |
| Kwantiseringsmethode | Zelf ontwikkelde MoziSmartBit slimme kwantisering + standaard GGUF-formaat |
| Contextlengte | 128K (262.144 tokens) |
| Modelgrootte | ~13,7 GB |
| Minimale VRAM | **16GB+** implementeerbaar (CPU-offload); **20GB+** soepele lange context; **24GB+** volledige 128K + visie |
| Inferentieframework | llama.cpp / Ollama / LM Studio / Jan |
| Inferentiesnelheid | Met MTP-speculatieve decodering: R9700 bereikt 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Ontwikkelteam | Team Chen Yumo |

---

## 6. ⚡ Snel starten (3 bestanden = 100% activatie van de beste redeneercapaciteiten)

> ⚠️ **Kerntip**: de beste redeneercapaciteiten van MoziAI vereisen het **gelijktijdig downloaden van 3 bestanden** — het hoofdmodel, de visuele projector en de chattemplate. Als er een ontbreekt, gaat de bijbehorende capaciteit verloren.

### 6.1 Download de modelbestanden

Download **alle bestanden in de map V3.8** van HuggingFace / ModelScope naar dezelfde lokale map:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Hoofdmodel (verplicht, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Chattemplate (verplicht, bevat instructies voor zeven-dimensioneel denken + Loop)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf            ← Visuele projector (verplicht, 927 MB)
```

| Bestand | Grootte | Noodzaak | Functie |
| --- | --- | --- | --- |
| Hoofdmodel `.gguf` | ~13,7 GB | **Verplicht** | Modelgewichten, kernredeneercapaciteiten |
| Visuele projector `mmproj` | ~927 MB | **Verplicht** | Multimodaal visueel begrip; zonder dit geen beeldmogelijkheden |
| Chattemplate `.jinja` | Minimaal | **Verplicht** | Injecteert MoziAI-identiteit + zeven-dimensioneel denken + LOOP-mechanisme-instructies |

### 6.2 Start en gebruik

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Open `http://localhost:8080` in uw browser om het gesprek te starten. De volledige aanbevolen parameters vindt u in paragraaf 9.

---

## 7. Modeldownload

| Platform | Adres |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master) |

> 💡 **LM Studio-gebruikers**: zoek in [LM Studio](https://lmstudio.ai) naar `moziAI` en download met één klik, zonder handmatig bestanden te hoeven downloaden.

---

## 8. Startopdrachten

### Minimale start (met de drie bestanden)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Volledige aanbevolen start

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

> 💡 MTP uitschakelen: verwijder `--spec-type draft-mtp` en gerelateerde parameters; de snelheid daalt met ongeveer 30-50%, het VRAM-gebruik wordt kleiner.

---

## 9. Aanbevolen inferentieparameters

Gebaseerd op de officieel aanbevolen parameters van llama.cpp en lokaal gemeten optimalisaties (AMD Radeon AI PRO R9700 32GB):

| Parameter | Algemene chat | Codering/Agent | Beschrijving |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Balans tussen creativiteit en nauwkeurigheid |
| top\_p | 0.95 | 0.95 | Kernmonsterdrempel |
| top\_k | 20 | 20 | Truncated sampling |
| repeat\_penalty | 1.05 | 1.05 | Herhalingsstraf |
| context\_length | 262144 | 262144 | 128K lange context |
| reasoning | auto | auto | Redeneerketen (thought chain) inschakelen |
| reasoning\_budget | 400 | 400 | Redeneerbudget in tokens |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Redenering naar een apart veld uitvoeren |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP-speculatieve decodering (zie paragraaf 11)** |

> 💡 **Denkmodus**: schakel in via `--reasoning auto`; het model redeneert eerst intern voordat het een antwoord geeft. `reasoning_budget` bepaalt het maximale aantal denktokens (aanbevolen 400, instelbaar 100-1000).

---

## 10. Vergelijking van kwantiseringsformaten

| Formaat | Grootte | Precisie | Beschrijving |
| --- | --- | --- | --- |
| FP16 origineel | ~54 GB | 100% | Verliesvrij, vereist een professionele gpu |
| **MoziSmartBit (dit model)** | **~13,7 GB** | **~99%** | **Zelf ontwikkelde slimme kwantisering, beste precisie, kleinste omvang** |
| Q4_K_M | ~17 GB | ~98% | GGUF-standaard 4-bit |
| Q5_K_M | ~20 GB | ~99% | Hogere precisie |
| Q6_K | ~23 GB | ~99,5% | Bijna verliesvrij |
| Q8_0 | ~31 GB | ~100% | Verliesvrij |

> MoziSmartBit comprimeert het 27B Dense-model tot 13,7 GB (compressieverhouding 3,9x) met behoud van ongeveer 99% precisie — ongeveer 20% kleiner dan Q4_K_M, beter geschikt voor lokale implementatie op consumenten-gpu's.

---

## 11. MTP-speculatieve decodering (belangrijke versnellingsfunctie)

Dit model bevat een ingebouwde MTP (Multi-Token Prediction) speculatieve decoderinglaag; na inschakeling stijgt de inferentiesnelheid met **1,5-2x**. Dit is een native functie van de Qwen3.8-architectuur; MoziAI heeft de volledige MTP-gewichten behouden.

**Principe**: in de modelarchitectuur is extra een lichtgewicht voorspellingskop (Draft Model) getraind, die vóór validatie door het hoofdmodel toekomstige tokens vooraf raadt, waardoor het aantal forward-passes afneemt en de inferentielatentie daalt. Fout geraden tokens worden gecorrigeerd door het hoofdmodel; dit heeft geen negatieve invloed op de outputkwaliteit.

### Inschakelparameters

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Aanbevolen waarde | Beschrijving |
| --- | --- | --- |
| --spec-type | draft-mtp | MTP-speculatieve decodering inschakelen |
| --spec-draft-n-max | 2 | Maximaal 2 tokens per keer raden (aanbevolen waarde, acceptatiegraad circa 80%) |
| --spec-draft-p-min | 0.75 | Minimale acceptatiewaarschijnlijkheidsdrempel (0.0-1.0, hoger = conservatiever) |

### Aanbevelingen voor parameteraanpassing

| n-max | Acceptatiegraad | Toepassingsscenario |
| --- | --- | --- |
| 1 | ~90% | Meest conservatief, kleinste snelheidswinst |
| **2** | **~80%** | **Aanbevolen: balans tussen snelheid en nauwkeurigheid** |
| 3 | ~71% | Algemene scenario's, duidelijke snelheidswinst |
| 4-5 | ~60-65% | Creatief schrijven, codegeneratie |
| 6 | ~50-55% | Lange pure-tekstoutput (in combinatie met aanpassing van p-min) |

---

## 12. Aanbevolen VRAM-configuraties

| VRAM | Aanbevolen configuratie | Beschrijving |
| --- | --- | --- |
| 16 GB | Context verlagen naar 64K, CPU-offload nodig | Instapniveau, zoals RTX 4060 Ti |
| **20 GB** | **128K volledig, q4_0 KV-cache** | **Aanbevolen configuratie**, zoals RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K volledig, ruime VRAM-reserve | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K volledig, sterkste configuratie | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 128K volledig | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Hoe langer de context, hoe meer VRAM er wordt gebruikt. Verlaag bij OOM geleidelijk de `-c`-parameter. Gebruik `--fit on` om llama.cpp het aantal lagen automatisch aan het VRAM te laten aanpassen. Ondersteunt gpu's van alle merken: NVIDIA / AMD / Intel.

---

## 13. Implementatiemethoden

### Ollama-implementatie

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

Zoek in LM Studio / Jan naar `moziAI` en download de Q4\_K\_M-kwantiseringsversie.

> 💡 Ollama biedt beperkte ondersteuning voor mmproj en chat\_template; gebruik bij voorkeur llama.cpp voor volledige functionaliteit.

---

## 14. Benchmark-evaluaties

MoziAI-27B-3.8 is gefinetuned op basis van het Qwen3.8-27B-basismodel, met het financiële verticale domein als kernoptimalisatierichting.

### Codeercapaciteiten

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Agent-mogelijkheden

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Algemene mogelijkheden

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Multimodale mogelijkheden

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> De gegevens van concurrenten zijn officieel openbaar gepubliceerde evaluatieresultaten. MoziAI presteert in het financiële verticale domein (interpretatie van financiële rapporten, kwantitatieve strategieën, risicobeheer en compliance, Agent-toolaanroepen, enz.) aanzienlijk beter dan algemene modellen.

---

## 15. Licentie

Dit model wordt geleverd onder een **aangepaste beperkende licentie**:

- ✅ **Toegestaan** — gratis commercieel gebruik, kopiëren en distribueren
- ❌ **Verboden** — herontwikkeling, doorverkoop, sublicentieverlening
- 📋 **Vereist** — behoud van de oorspronkelijke copyrightmelding en bronvermelding: moziAI-27B

Dit model wordt aangeboden 'zoals het is', zonder enige vorm van garantie. De modeloutput is uitsluitend ter referentie en vormt geen beleggingsadvies. Gebruikers dragen zelf het risico van het gebruik.

Raadpleeg het bestand [LICENSE](LICENSE) voor de volledige voorwaarden.

---

## 16. Contact

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. Alle rechten voorbehouden.
