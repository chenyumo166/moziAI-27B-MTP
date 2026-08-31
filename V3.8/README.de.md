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

# MoziAI-27B-3.8 — Ein kleines, aber leistungsstarkes multimodales KI-Modell für die kostenlose lokale Bereitstellung

[English](README.en.md) | [简体中文](README.zh.md) | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

**Veröffentlichungsdatum: 2026-08-30** · **Version: V3.8**

---

## 📑 Inhaltsverzeichnis

- [1. Modellübersicht](#1-modellübersicht)
- [2. Besonderheiten des Modells](#2-besonderheiten-des-modells) — dynamisches siebendimensionales Denken / LOOP / MoziSmartBit / Finanzfokus
- [3. Versionshinweise](#3-versionshinweise)
- [4. Kernfunktionen](#4-kernfunktionen)
- [5. Technische Spezifikationen](#5-technische-spezifikationen)
- [6. ⚡ Schnellstart](#6--schnellstart-3-dateien--100--aktivierte-beste-inferenzfähigkeit) — **Download des Drei-Dateien-Pakets**
- [7. Modell-Download](#7-modell-download)
- [8. Startbefehle](#8-startbefehle)
- [9. Empfohlene Inferenzparameter](#9-empfohlene-inferenzparameter)
- [10. Vergleich der Quantisierungsformate](#10-vergleich-der-quantisierungsformate)
- [11. MTP-Spekulationsdecodierung (wichtiges Beschleunigungsmerkmal)](#11-mtp-spekulationsdecodierung-wichtiges-beschleunigungsmerkmal)
- [12. Empfohlene VRAM-Konfiguration](#12-empfohlene-vram-konfiguration)
- [13. Bereitstellungsmethoden](#13-bereitstellungsmethoden)
- [14. Benchmark-Bewertung](#14-benchmark-bewertung)
- [15. Lizenz](#15-lizenz)
- [16. Kontakt](#16-kontakt)

---

## 1. Modellübersicht

MoziAI-27B-3.8 ist ein lokal bereitstellbares Open-Source-Multimodales-KI-Modell, das vom Team des chinesischen Finanzexperten 陈雨墨 (Chen Yumo) entwickelt wurde. Es basiert auf dem Open-Source-Basismodell **Qwen3.8-27B** (Dense-27B-Architektur, MIT-Lizenz) und kombiniert selbst entwickelte Finanzdaten, Finanzbereichs-Kompetenzen, das dynamische siebendimensionale Denksystem, den Agenten-LOOP-Reflexions- und Iterationsmechanismus sowie den MoziSmartBit-Hybridquantisierungsalgorithmus. Dieses Modell senkt die Hürde für die lokale Bereitstellung für Einzelpersonen und Unternehmen. Es ist für die **kostenlose kommerzielle Nutzung** lizenziert, kann auf Consumer-Grafikkarten lokal bereitgestellt werden, spart erhebliche Cloud-Token-Kosten, ermöglicht 7×24 Stunden Token-Freiheit und gewährleistet die Privatsphäre und Sicherheit lokaler Daten.

---

## 2. Besonderheiten des Modells

### 🧠 Dynamisches siebendimensionales Denksystem

Das von MoziAI selbst entwickelte Kern-Inferenzframework. Bei jeder Aufgabe gibt das Modell zunächst das **moziAI-Think**-Tag aus und entfaltet je nach Aufgabenkomplexität dynamisch strukturiertes Denken:

| Stufe | Anwendungsbereich | Typische Aufgaben | Entfaltete Dimensionen |
| --- | --- | --- | --- |
| **Level 0** | Einfache Fragen & Antworten | Begriffserklärungen, Faktenabfragen, Übersetzung, Zusammenfassung | ① Aufgabenverständnis ⑤ Ressourcenbedarf (zweidimensionale Schnellantwort) |
| **Level 1** | Analyse & Diagnose | Marktforschung, Textverfassung, Datenanalyse, Interpretation von Research-Berichten, Strategiebewertung | ①②③⑤⑥ Fünf-Dimensionen-Bewertung |
| **Level 2** | Komplexe Entwicklung/Strategie | Codeentwicklung, Architekturdesign, Entwicklung quantitativer Strategien, mehrstufige Workflows, Systemdesign | ①②③④⑤⑥⑦ Tiefe Ableitung über alle sieben Dimensionen |

> Sieben Dimensionen: ① Aufgabenverständnis ② Komplexitätsbewertung ③ Abhängigkeiten ④ Risikobewertung ⑤ Ressourcenbedarf ⑥ Abnahmekriterien ⑦ Ausführungsstrategie

### 🔄 Agenten-LOOP-Iterationsmechanismus

Komplexe Aufgaben wechseln automatisch in den **moziAI-Loop**-Iterationsmodus: **Runde 1: Ausführung + Bewertung → Runde 2: Anpassung + Verifizierung**. Dadurch wird sichergestellt, dass die Ausgabe erst nach einer Selbstprüfung als endgültige Antwort geliefert wird. Wie ein erfahrener Ingenieur zerlegt das Modell Probleme → bewertet Lösungen → führt aus → reflektiert → optimiert, wodurch Genauigkeit und Ausführbarkeit bei komplexen Aufgaben deutlich verbessert werden. Bei einfachen Fragen und Aufgaben wird der Loop automatisch deaktiviert.

### 📦 MoziSmartBit Intelligente Quantisierung

Selbst entwickelte hierarchische intelligente Quantisierung: Das Dense-Modell mit 27 Milliarden Parametern wird auf etwa **13,7 GB** komprimiert – etwa 3,3 GB (~20 %) kleiner als herkömmliches Q4_K_M (~17 GB) – bei Erhalt von etwa **99 %** der FP16-Präzision. Herkömmliche Quantisierung verwendet für alle Schichten eine einheitliche Präzision; MoziSmartBit setzt stattdessen eine intelligente differenzierte Strategie um, die auf die strukturellen Merkmale des Dense-Modells abgestimmt ist, und übertrifft Q4_K_M an Präzision.

### 💰 Fokus auf den Finanzvertikalbereich

Tiefe Optimierung für Finanz-Fragen & Antworten, quantitative Programmierung und Tool-Aufrufe. Im Finanzbereich ist die Toleranz gegenüber Halluzinationen extrem gering; MoziAI schneidet in diesem Bereich deutlich besser ab als vergleichbar große allgemeine Modelle.

### 🌐 Weitere Merkmale

- **Mehrsprachigkeit**: 201 Sprachen und Dialekte, mit besonders optimierten Chinesisch-Fähigkeiten
- **Allgemeine Programmierung**: Full-Stack-Entwicklung, Code-Debugging, Architekturdesign – Abdeckung von Python/JS/TS/Go/Rust
- **Artikelverfassen**: Hochwertiges Schreiben in mehreren Genres, z. B. Research-Berichte, Analyseartikel, technische Dokumentation, kreative Inhalte
- **Visuelles Verständnis**: multimodales Sehen; unterstützt das lokale Verständnis von Bildinhalten über Screenshots
- **Multi-Framework-Unterstützung**: llama.cpp / Ollama / LM Studio / Jan
- **Multi-Agent-Unterstützung**: OpenClaw / Hermes / Cursor / Claude Code / Codex usw. – natives Tool-Calling und mehrstufige Aufgabenorchestrierung

---

## 3. Versionshinweise

Diese Versionsaktualisierung stärkt vor allem die von moziAI selbst entwickelten Inferenzmodi „dynamisches siebendimensionales Denken + LOOP-Iteration": Sie erkennen die Aufgabenkomplexität intelligenter, erhöhen die Abschlussquote komplexer Aufgaben und verbessern die Fähigkeit, „erst zu denken, dann zu handeln".

moziAI bleibt mit einer aktiven, hohen Frequenz von Versionsupdates und Iterationen am Puls der künftigen KI-Entwicklung und macht lokale KI-Modelle durch kontinuierlich selbst entwickelte Technologien immer leichter bereitstellbar und immer leistungsfähiger.

---

## 4. Kernfunktionen

| Kompetenzbereich | Beschreibung |
| --- | --- |
| Marktanalyse | Makro-/mikroökonomische Einordnung, Aufbereitung von Kursentwicklungen und -logik für A-Aktien, Hongkong, USA, Rohstoffe und Kryptowährungen |
| Finanzen & Research-Berichte | Interpretation wichtiger Bilanzkennzahlen, Extraktion von Research-Zusammenfassungen, Unterstützung bei Bewertung und Gewinnprognosen |
| Risikomanagement & Compliance | Risikobewertung von Produkten, Compliance-Hinweise zu Anlageempfehlungen, Interpretation der Finanzregulierungspolitik |
| Quantitativ & Strategie | Design quantitativer Strategieansätze, Pyramid-Quantifizierung (Pyramid/PEL), Backtest-Logik, Faktorkonstruktion und Tool-Aufrufe |
| Tool-Aufrufe | Anbindung an Finanzdatenquellen wie Echtzeit-Kursdaten, Datenbanken und Research-Suche |

---

## 5. Technische Spezifikationen

| Eigenschaft | Wert |
| --- | --- |
| Basismodell | Qwen3.8-27B (Dense-Architektur, gemischte Aufmerksamkeit: 16 full + 48 linear, MIT-Lizenz) |
| Parameterumfang | 27 Milliarden (27B) Dense-Architektur |
| Quantisierungsmethode | Selbst entwickelte MoziSmartBit-Intelligentquantisierung + GGUF-Standardformat |
| Kontextlänge | 128K (262.144 Tokens) |
| Modellgröße | ~13,7 GB |
| Minimaler VRAM | **16 GB+** bereitstellbar (CPU-Offload); **20 GB+** flüssige lange Kontexte; **24 GB+** volle 128K + Vision |
| Inferenz-Framework | llama.cpp / Ollama / LM Studio / Jan |
| Inferenzgeschwindigkeit | Mit MTP-Spekulationsdecodierung: R9700 erreicht 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Entwicklungsteam | Team 陈雨墨 (Chen Yumo) |

---

## 6. ⚡ Schnellstart (3 Dateien = 100 % aktivierte beste Inferenzfähigkeit)

> ⚠️ **Wichtiger Hinweis**: Für die beste Inferenzfähigkeit von MoziAI müssen **3 Dateien gleichzeitig heruntergeladen werden** – Hauptmodell, visuelles Projektionsmodul und Chat-Template. Fehlt eine davon, geht die entsprechende Fähigkeit verloren.

### 6.1 Modelldateien herunterladen

Laden Sie auf HuggingFace / ModelScope **alle Dateien im Verzeichnis V3.8** in dasselbe lokale Verzeichnis herunter:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Hauptmodell (erforderlich, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Chat-Template (erforderlich, enthält siebendimensionale Denk- und Loop-Anweisungen)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf            ← visuelles Projektionsmodul (erforderlich, 927 MB)
```

| Datei | Größe | Notwendigkeit | Funktion |
| --- | --- | --- | --- |
| Hauptmodell `.gguf` | ~13,7 GB | **erforderlich** | Modellgewichte, Kern-Inferenzfähigkeit |
| Visuelles Projektionsmodul `mmproj` | ~927 MB | **erforderlich** | multimodales visuelles Verständnis; ohne Einbindung gehen die Bildfähigkeiten verloren |
| Chat-Template `.jinja` | minimal | **erforderlich** | injiziert die Anweisungen für MoziAI-Identität + siebendimensionales Denken + LOOP-Mechanismus |

### 6.2 Starten und verwenden

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Öffnen Sie im Browser `http://localhost:8080`, um das Gespräch zu beginnen. Die vollständigen empfohlenen Parameter finden Sie in Abschnitt 9.

---

## 7. Modell-Download

| Plattform | Adresse |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master) |

> 💡 **LM-Studio-Nutzer**: Suchen Sie in [LM Studio](https://lmstudio.ai) nach `moziAI` und laden Sie es mit einem Klick herunter – kein manuelles Herunterladen von Dateien erforderlich.

---

## 8. Startbefehle

### Minimalstart (mit dem Drei-Dateien-Paket)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Vollständig empfohlener Start

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

> 💡 MTP deaktivieren: Entfernen Sie `--spec-type draft-mtp` und die zugehörigen Parameter; die Geschwindigkeit sinkt um etwa 30–50 %, der VRAM-Verbrauch ist geringer.

---

## 9. Empfohlene Inferenzparameter

Basierend auf den offiziell empfohlenen Parametern von llama.cpp und lokalen Praxistests (AMD Radeon AI PRO R9700 32 GB):

| Parameter | Allgemeiner Chat | Codierung/Agent | Beschreibung |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Balance zwischen Kreativität und Genauigkeit |
| top\_p | 0.95 | 0.95 | Kern-Sampling-Schwellenwert |
| top\_k | 20 | 20 | Truncated Sampling |
| repeat\_penalty | 1.05 | 1.05 | Wiederholungsstrafe |
| context\_length | 262144 | 262144 | 128K langer Kontext |
| reasoning | auto | auto | Reasoning-Kette (Chain of Thought) aktivieren |
| reasoning\_budget | 400 | 400 | Reasoning-Budget-Tokens |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Reasoning in ein separates Feld ausgeben |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP-Spekulationsdecodierung (siehe Abschnitt 11)** |

> 💡 **Denkmodus**: Aktivieren Sie ihn über `--reasoning auto`; das Modell führt zuerst eine interne Überlegung durch, bevor es die Antwort ausgibt. `reasoning_budget` steuert die maximale Anzahl von Denk-Tokens (empfohlen 400, einstellbar 100–1000).

---

## 10. Vergleich der Quantisierungsformate

| Format | Größe | Präzision | Beschreibung |
| --- | --- | --- | --- |
| FP16 Original | ~54 GB | 100 % | verlustfrei, benötigt professionelle Grafikkarten |
| **MoziSmartBit (dieses Modell)** | **~13,7 GB** | **~99 %** | **selbst entwickelte intelligente Quantisierung: beste Präzision, kleinste Größe** |
| Q4_K_M | ~17 GB | ~98 % | GGUF-Standard 4-Bit |
| Q5_K_M | ~20 GB | ~99 % | höhere Präzision |
| Q6_K | ~23 GB | ~99,5 % | nahezu verlustfrei |
| Q8_0 | ~31 GB | ~100 % | verlustfrei |

> MoziSmartBit komprimiert das 27B-Dense-Modell bei Erhalt von etwa 99 % Präzision auf 13,7 GB (Kompressionsverhältnis 3,9×) – etwa 20 % kleiner als Q4_K_M und damit besser für die lokale Bereitstellung auf Consumer-Grafikkarten geeignet.

---

## 11. MTP-Spekulationsdecodierung (wichtiges Beschleunigungsmerkmal)

Dieses Modell enthält eine integrierte MTP-Spekulationsdecodierungsschicht (Multi-Token-Prediction). Nach der Aktivierung erhöht sich die Inferenzgeschwindigkeit um das **1,5- bis 2-Fache**. Dies ist ein natives Merkmal der Qwen3.8-Architektur; MoziAI hat die vollständigen MTP-Gewichte beibehalten.

**Prinzip**: In der Modellarchitektur wurde zusätzlich ein leichtgewichtiger Vorhersagekopf (Draft-Modell) trainiert, der nachfolgende Tokens vor der Verifikation durch das Hauptmodell vorhersagt. Dadurch werden die Anzahl der Forward-Pässe und die Inferenzlatenz reduziert. Falsche Vorhersagen werden vom Hauptmodell korrigiert – ohne negative Auswirkungen auf die Ausgabequalität.

### Aktivierungsparameter

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Empfohlener Wert | Beschreibung |
| --- | --- | --- |
| --spec-type | draft-mtp | aktiviert die MTP-Spekulationsdecodierung |
| --spec-draft-n-max | 2 | maximal 2 vorhergesagte Tokens pro Schritt (empfohlener Wert, Akzeptanzrate ca. 80 %) |
| --spec-draft-p-min | 0.75 | Mindestschwelle der Akzeptanzwahrscheinlichkeit (0.0–1.0; je größer, desto konservativer) |

### Empfehlungen zur Parameteranpassung

| n-max | Akzeptanzrate | Anwendungsbereich |
| --- | --- | --- |
| 1 | ~90 % | am konservativsten, geringste Geschwindigkeitssteigerung |
| **2** | **~80 %** | **empfohlen: Balance zwischen Geschwindigkeit und Genauigkeit** |
| 3 | ~71 % | allgemeine Szenarien, deutliche Geschwindigkeitssteigerung |
| 4–5 | ~60–65 % | kreatives Schreiben, Codegenerierung |
| 6 | ~50–55 % | lange reine Textausgaben (in Kombination mit der p-min-Anpassung) |

---

## 12. Empfohlene VRAM-Konfiguration

| VRAM | Empfohlene Konfiguration | Beschreibung |
| --- | --- | --- |
| 16 GB | Kontext auf 64K reduzieren, CPU-Offload erforderlich | Einstiegsklasse, z. B. RTX 4060 Ti |
| **20 GB** | **volle 128K, q4_0-KV-Cache** | **empfohlene Konfiguration**, z. B. RX 7900 XT / RTX 5070 Ti |
| 24 GB | volle 128K, ausreichende VRAM-Reserve | RTX 4090 / RX 7900 XTX |
| 32 GB+ | volle 128K, stärkste Konfiguration | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | volle 128K | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Je länger der Kontext, desto mehr VRAM wird benötigt. Bei OOM reduzieren Sie den Parameter `-c` schrittweise. Mit `--fit on` passt llama.cpp die Anzahl der Schichten automatisch an den VRAM an. Unterstützt Grafikkarten aller Marken: NVIDIA / AMD / Intel.

---

## 13. Bereitstellungsmethoden

### Ollama-Bereitstellung

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

Suchen Sie in LM Studio / Jan nach `moziAI` und laden Sie die Q4\_K\_M-Quantisierungsversion herunter.

> 💡 Ollama unterstützt mmproj und chat\_template nur eingeschränkt; für den vollen Funktionsumfang wird empfohlen, llama.cpp zu verwenden.

---

## 14. Benchmark-Bewertung

MoziAI-27B-3.8 basiert auf dem Basismodell Qwen3.8-27B und ist mit dem Finanzvertikalbereich als Kernoptimierungsrichtung feinabgestimmt.

### Codierungsfähigkeiten

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Agent-Fähigkeiten

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Allgemeine Fähigkeiten

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Multimodale Fähigkeiten

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Die Daten der Wettbewerber sind offiziell veröffentlichte Benchmark-Ergebnisse. MoziAI übertrifft allgemeine Modelle deutlich in Finanzvertikalbereichen (Bilanzinterpretation, quantitative Strategien, Risikomanagement & Compliance, Agent-Tool-Aufrufe usw.).

---

## 15. Lizenz

Dieses Modell verwendet eine **benutzerdefinierte restriktive Lizenz**:

- ✅ **Erlaubt** — kostenlose kommerzielle Nutzung, Vervielfältigung und Verbreitung
- ❌ **Verboten** — Weiterentwicklung, Weiterverkauf, Unterlizenzierung
- 📋 **Erforderlich** — Original-Urheberrechtshinweis beibehalten und Quelle angeben: moziAI-27B

Dieses Modell wird „wie besehen" ohne jegliche Gewährleistung bereitgestellt. Die Modellausgaben dienen ausschließlich der Information und stellen keine Anlageberatung dar. Die Nutzung erfolgt auf eigenes Risiko.

Detaillierte Bedingungen finden Sie in der Datei [LICENSE](LICENSE).

---

## 16. Kontakt

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-Mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. Alle Rechte vorbehalten.
