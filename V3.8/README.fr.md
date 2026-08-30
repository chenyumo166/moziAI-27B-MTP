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

# MoziAI-27B-3.8 - Modèle AI multimodal petit mais puissant, déployable localement gratuitement

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | Français | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## Présentation du modèle

MoziAI-27B-3.8 est un grand modèle AI multimodal open-source local développé par l'équipe de l'influenceur financier chinois Chen Yumo (amélioré pour le domaine financier, support de la vision, des appels d'outils, déploiement local sur GPU grand public). moziAI-27B-3.8 est construit sur le modèle de base open-source Qwen3.8-27B (architecture Dense 27B, licence MIT), intégrant les technologies auto-développées de l'équipe Chen Yumo (données financières + capacités de domaine financier + méthodes d'entraînement + cadre de réflexion sept dimensionnel dynamique + mécanisme d'itération LOOP de l'agent + algorithme d'hybridation quantification MoziSmartBit). Il réduit les barriers de déploiement local pour les particuliers et les entreprises, avec une licence commerciale gratuite. Le déploiement sur GPU grand public local permet d'économiser considérablement les coûts de tokens cloud, réalisant la liberté de tokens 24/7 tout en garantissant la confidentialité et la sécurité des données locales.

**Cadre de réflexion sept dimensionnel dynamique + Mécanisme d'itération LOOP de l'agent** : Le mode de raisonnement principal auto-développé par MoziAI. Évalue intelligemment la complexité des tâches — les tâches simples activent une réflexion bidimensionnelle pour des réponses rapides, les tâches modérément complexes utilisent une réflexion pentadimensionnelle, et les tâches hautement complexes activent la réflexion sept dimensionnelle complète avec le mécanisme d'itération LOOP de réflexion. Il vise à défier la capacité des modèles à paramètres billions de fois plus grands à résoudre efficacement les tâches complexes, sans sacrifier la réactivité légère des tâches simples.

**Grâce à la technologie de quantification intelligente MoziSmartBit auto-développée**, le modèle Dense de 27 milliards de paramètres est compressé à environ 12,79 GB, soit 3,3 GB (environ 20%) plus petit que les modèles de quantification Q4_K_M conventionnels (~17 GB) ; atteignant l'équilibre optimal entre précision et taille, offrant ~99% de la qualité de précision FP16.

En plus de conserver les capacités générales des grands modèles AI, ce modèle a été amélioré pour : les applications de domaine vertical financier, les Q&R financiers, la programmation quantitative, les appels d'outils et la programmation générale, avec compatibilité avec diverses plateformes d'agents.

Le développeur du modèle Chen Yumo utilise fréquemment ce modèle pour l'analyse de données financières locale, le développement de stratégies quantitatives, la recherche de marché, la rédaction d'articles, le développement de projets globaux, la programmation générale, et l'exécution de tâches complexes à contexte long 256K par OpenClaw/Hermes.

Supporte le déploiement local gratuit sur les frameworks d'inférence mainstream comme llama.cpp, Ollama, LM Studio, et plus.

**Date de sortie : 2026-08-30** | **Version : V3.8**

## Fonctionnalités du modèle

- **🧠 Cadre de réflexion sept dimensionnel dynamique** : Framework de raisonnement principal auto-développé par MoziAI. Face à toute tâche, le modèle produit d'abord le tag **moziAI-Think**, développant dynamiquement la réflexion structurée selon la complexité — de la réponse bidimensionnelle rapide « compréhension de la tâche + exigences de ressources » (Level 0) à l'évaluation pentadimensionnelle (Level 1) jusqu'au raisonnement profond sept dimensionnel complet (Level 2) : ①Compréhension de la tâche ②Évaluation de la complexité ③Analyse des dépendances ④Évaluation des risques ⑤Exigences de ressources ⑥Critères d'acceptation ⑦Stratégie d'exécution.
- **🧠 Mécanisme d'itération LOOP de l'agent** : Pour les tâches complexes, MoziAI entre automatiquement en mode itératif **moziAI-Loop** : Tour 1 exécution + évaluation → Tour 2 ajustement + vérification, assurant que la sortie est auto-vérifiée avant la réponse finale.
- **🧠 Quantification intelligente MoziSmartBit** : Quantification hiérarchique intelligente auto-développée, équilibre optimal précision/taille, compressé à ~12,79 GB avec FP16 ~99% de précision.
- **🧠 Focus sur le domaine vertical financier** : Optimisation profonde pour les Q&R financiers, la programmation quantitative et les appels d'outils.
- **Support multilingue** : 201 langues et dialectes, chinois particulièrement optimisé, couvrant anglais, japonais, coréen, allemand, français, espagnol, portugais, etc.
- **Capacités de programmation générale** : Full-stack, debug, architecture, scripts — Python/JS/TS/Go/Rust.
- **Capacités rédactionnelles** : Rédaction multi-genres de haute qualité — rapports de recherche, articles analytiques, documentation technique, contenu créatif.
- **Compréhension visuelle** : Vision multimodale, screenshots collés dans le chat, le modèle comprend le contenu des images.
- **Support multi-framework** : Compatible llama.cpp, Ollama, LM Studio, Jan, etc.
- **Support multi-plateforme Agent** : Compatibilité profonde avec OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex, support natif des appels d'outils et orchestration de tâches multi-tours.

## Capacités principales

| Domaine | Description |
| ----- | ------------------------------------------ |
| Analyse de marché | Interprétation macro/micro-économique, marchés actions/commodités/crypto |
| Finances & Rapports | Indicateurs financiers, synthèse de rapports, valorisation et prévisions |
| Contrôle des risques & Conformité | Évaluation des risques, conformité des conseils d'investissement, réglementation |
| Quantitatif & Stratégie | Conception de stratégies quantitatives, quantification Pyramid/PEL, backtesting |
| Appels d'outils | Données de marché en temps réel, bases de données, recherche de rapports |

## Spécifications techniques

| Élément | Paramètres |
| ------ | ---------------------------------------------------------------------------------- |
| Modèle de base | Qwen3.8-27B (architecture Dense, attention hybride 16 full + 48 linear, licence MIT) |
| Échelle des paramètres | 27 milliards (27B) architecture Dense |
| Méthode de quantification | Algorithme MoziSmartBit auto-développé + format standard GGUF |
| Longueur du contexte | 256K (262 144 tokens) |
| Taille du modèle | ~12,79 GB |
| VRAM minimum | **16GB+** déployable (avec CPU offloading) ; **20GB+** fonctionnement fluide long contexte ; **24GB+** 256K complet + vision |
| Framework d'inférence | llama.cpp / Ollama / LM Studio / Jan |
| Vitesse d'inférence | Avec MTP : AMD R9700 70+ token/s, AMD MAX+395 iGPU 50+ token/s, AMD MAX+395 GPU 35+ token/s |
| Équipe de développement | Équipe Chen Yumo |

## Format de quantification et taille du modèle

| Format | Taille | Précision | Description |
| ---------------- | ------------- | --------- | ----------------- |
| FP16 (Original) | ~54 GB | 100% | Précision originale 16 bits |
| **MoziSmartBit** | **~12,79 GB** | **~99%** | **Ce modèle utilise la quantification intelligente auto-développée** |
| Q4_K_M | ~17 GB | ~98% | Standard GGUF 4 bits |
| Q5_K_M | ~20 GB | ~99% | Précision supérieure |
| Q6_K | ~23 GB | ~99,5% | Quasi sans perte |
| Q8_0 | ~31 GB | ~100% | Sans perte |

> MoziAI V3.8 utilise le schéma de quantification intelligente MoziSmartBit, compressant le modèle Dense de 27 milliards de paramètres à environ 12,79 GB tout en maintenant ~99% de précision, avec un ratio de compression de 4,0x.

## Technologie de quantification intelligente MoziSmartBit

Les schémas traditionnels appliquent une précision uniforme à toutes les couches. La **quantification intelligente MoziSmartBit** auto-développée adopte une stratégie de quantification différentielle intelligente adaptée aux caractéristiques structurelles des modèles Dense.

### Résultats de compression

- **Perte de précision minimale** : Gain d'entraînement > perte de quantification
- **Compression 4,0x** : De FP16 (~54 GB) à ~12,79 GB
- **Déploiable sur GPU grand public** : 16 GB VRAM suffisent, 20 GB+ pour le contexte long 256K complet

### Avantages comparatifs

**vs Q4_K_M (~17 GB)** : ~20% plus petit, précision supérieure, seuil VRAM plus bas

**vs FP16 original (~54 GB)** : Compression ~4,0x, ~99% de précision maintenue

## Paramètres d'inférence recommandés

Basés sur les recommandations officielles llama.cpp et l'optimisation locale (AMD Radeon AI PRO R9700 32GB) :

| Paramètre | Chat général | Codage/Agent | Description |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Équilibre créativité/précision |
| top\_p | 0,95 | 0,95 | Seuil de sampling noyau |
| top\_k | 20 | 20 | Sampling tronqué |
| repeat\_penalty | 1,05 | 1,05 | Pénalité de répétition |
| presence\_penalty | 0 | 0 | Pas de pénalité de présence |
| context\_length | 262144 | 262144 | Contexte long 256K |
| batch\_size | 2048 | 2048 | Taille de lot |
| ubatch\_size | 512 | 512 | Taille de micro-lot |
| flash\_attention | auto | auto | Flash Attention automatique |
| kv\_cache | q4\_0 | q4\_0 | Quantification du cache KV |
| poll | 0 | 0 | Pas de polling GPU inactif, économie d'énergie |
| reasoning | auto | auto | Chaîne de raisonnement |
| reasoning\_budget | 400 | 400 | Budget tokens de raisonnement |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Format de raisonnement |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | Ordre des échantillonneurs |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Décodage spéculatif MTP** |

> 💡 **Note sur le mode réflexion** : Ce modèle intègre Qwen3.8 Thinking. Activé via `--reasoning auto`, le modèle effectue un raisonnement interne avant de répondre. `reasoning_budget` contrôle le nombre max de tokens de réflexion (400 recommandé, ajustable 100-1000).

## Décodage spéculatif MTP (Fonctionnalité d'accélération importante)

Ce modèle intègre des couches de décodage spéculatif MTP (Multi-Token Prediction). Quand activé, la vitesse d'inférence peut être améliorée de **1,5-2x**.

### Principe du MTP

Le MTP entraîne un tête de prédiction légère (Draft Model) supplémentaire dans l'architecture du modèle pour prédire les tokens suivants avant la validation du modèle principal.

### Paramètres MTP pour llama.cpp

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Paramètre | Valeur recommandée | Description |
| --- | --- | --- |
| --spec-type | draft-mtp | Activer le décodage spéculatif MTP |
| --spec-draft-n-max | 2 | Tokens max devinés par étape (recommandé, taux d'acceptation ~80%) |
| --spec-draft-p-min | 0,75 | Seuil de probabilité minimale d'acceptation |

### Guide d'ajustement des paramètres MTP

| spec-draft-n-max | Taux d'acceptation | Cas d'utilisation |
| --- | --- | --- |
| 1 | ~90% | Le plus conservateur |
| **2** | **~80%** | **Recommandé : équilibre vitesse/précision** |
| 3 | ~71% | Scénarios généraux |
| 4-5 | ~60-65% | Écriture créative, génération de code |
| 6 | ~50-55% | Sortie texte longue |

> ⚠️ **Note** : Le décodage spéculatif MTP n'a aucun impact négatif sur la qualité de sortie.

## Commande de démarrage llama.cpp

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

> 💡 **Désactiver le MTP** : Supprimez les trois lignes `--spec-type draft-mtp`, `--spec-draft-n-max 2` et `--spec-draft-p-min 0.75`. La vitesse diminue d'environ 30-50%.

## Recommandations VRAM

| VRAM | Contexte recommandé | Cache KV | Support Vision | Description |
| --- | --- | --- | --- | --- |
| 20 GB | 256K complet | q4\_0 | Support complet | Vision+256K, configuration recommandée |
| 24 GB | 256K complet | q4\_0 | Support complet | Vision+256K, VRAM suffisant |
| 32 GB+ | 256K complet | q4\_0 | Support complet | Vision+256K, configuration la plus forte |

**GPU NVIDIA**

| VRAM | Modèle GPU |
| --- | --- |
| 16 GB | RTX 4060 Ti (CPU offloading nécessaire) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**GPU AMD**

| VRAM | Modèle GPU |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**GPU Intel**

| VRAM | Modèle GPU |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (CPU offloading nécessaire) |

**CPU avec mémoire partagée / GPU intégré**

| VRAM | Processeur |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395 (Radeon 8060S iGPU) |
| 128 GB | NVIDIA RTX Spark (Blackwell RTX GPU) |

> 💡 **Conseil** : Toute marque et tout modèle sont supportés dès que le VRAM est suffisant.
> 💡 **Conseil** : Plus le contexte est long, plus le VRAM est consommé. En cas d'OOM, réduisez progressivement `-c`. `--fit on` ajuste automatiquement les couches.

## Déploiement Ollama

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

## Déploiement LM Studio / Jan

Recherchez directement `moziAI` dans LM Studio / Jan et téléchargez la version Q4_K_M.

## Évaluation Benchmark

### Capacités de codage

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73,0 | 63,4 | 64,0 | 51,7 | 78,2 |
| SWE-bench Pro | **61,7** | 53,5 | 57,6 | 51,2 | 53,4 |
| NL2Repo-Bench | 42,3 | 36,2 | 41,1 | -- | 47,6 |
| DeepSWE 1.1 | **42,2** | 13,3 | 14,2 | -- | -- |
| QwenSWEBench | **79,0** | 49,3 | 59,2 | -- | 63,8 |

### Capacités Agent

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70,7** | 61,0 | 65,1 | -- | 68,2 |
| JobBench | **33,4** | 21,8 | 27,6 | -- | -- |
| Agents' Last Exam (Score) | **42,9** | 27,3 | 33,6 | -- | -- |
| WebArena-Verified | **64,8** | 48,8 | 55,3 | -- | -- |
| AndroidWorld | **81,9** | 70,3 | 81,0 | -- | 62,0 |

### Capacités générales

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79,5** | 69,1 | 79,1 | 77,0 | 62,5 |
| GPQA Diamond | 89,2 | 87,8 | 90,3 | 83,5 | **91,3** |

### Capacités multimodales

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94,6** | 85,1 | 90,3 | -- | 65,5 |
| BabyVision (With CI) | **85,6** | 28,9 | 70,4 | -- | 12,6 |
| CharXiv RQ (With CI) | **90,2** | 78,4 | 85,8 | -- | 66,0 |
| OmniDocBench 1.5 | 91,1 | 89,4 | **91,4** | 75,8 | 86,6 |
| RealWorldQA | 85,9 | 84,1 | **86,9** | -- | 73,9 |
| Vision2Web | **62,9** | 45,0 | 42,1 | -- | -- |

## Téléchargement du modèle

| Plateforme | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope (魔搭) | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

> 💡 **Utilisateurs LM Studio** : Recherchez directement `moziAI` dans [LM Studio](https://lmstudio.ai) pour un téléchargement en un clic.

⚠️ **Important : La capacité visuelle nécessite le chargement supplémentaire du fichier mmproj**

- **Fichier vision** : `moziAI-27B-3.8-mmproj-F16.gguf` (~927 MB, précision BF16)
- **Emplacement** : Même répertoire que le fichier modèle GGUF
- **Chargement** : Via le paramètre `--mmproj` au démarrage de llama-server

> Sans le fichier vision, la capacité de compréhension d'image est perdue.

## Démarrage rapide

### 1. Télécharger les fichiers du modèle

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # Modèle principal (requis)
├── moziAI-27B-3.8-mmproj-F16.gguf              # Projection vision (optionnel)
└── chat-template-moziai-27B-v38.jinja           # Modèle de chat (recommandé)
```

### 2. Démarrer le service d'inférence

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

### 3. Commencer à utiliser

Ouvrez `http://localhost:8080` dans votre navigateur.

### Structure des répertoires

```
moziAI-27B/
├── README.md              # Ce fichier (documentation chinoise)
├── README.en.md           # Version anglaise
├── LICENSE                # Licence
├── V3.8/                  # Version V3.8
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # Modèle principal
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # Projection vision
│   └── chat-template-moziai-27B-v38.jinja         # Modèle de chat
```

## Mots-clés SEO

Modèle AI financier, modèle open-source local, MoziSmartBit, quantification intelligente, GGUF, Qwen3.8-27B, domaine vertical financier, appels d'outils, Agent, llama.cpp, Ollama, contexte long 256K, multimodal, LLM local, edge AI, self-hosted AI, consumer GPU deployment, intelligent quantization

## Licence (Important)

Ce modèle est distribué sous une **licence restrictive personnalisée** :

✅ **Autorisé** : Utilisation commerciale gratuite, copie et distribution
❌ **Interdit** : Développement secondaire, revente, sous-licence
📋 **Exigences** : Conserver la notice de copyright, attribution : moziAI-27B

## Avertissement

Ce modèle est fourni « en l'état » sans garantie d'aucune sorte.

## Contact

- **HuggingFace** : [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub** : [@chenyumo166](https://github.com/chenyumo166)
- **Weibo** : [@rimochen](https://weibo.com/rimochen)
- **E-mail** : 263515@qq.com

Copyright (c) 2026 陈雨墨/ chenyumo166. All rights reserved.
