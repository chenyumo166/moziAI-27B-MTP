---
language:
- en
- fr
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

# MoziAI-27B-3.8 - Modèle AI Multimodal Petit mais Puissant, Déploiable Localement et Gratuitement

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | Français | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## Présentation du modèle

MoziAI-27B-3.8 est un LLM multimodal financier open-source local développé par l'équipe de l'influenceur financier chinois Chen Yumo. Basé sur le modèle open-source Qwen3.8-27B (architecture Dense 27B, licence MIT), il intègre les technologies auto-développées : (données financières + capacités du domaine financier + méthodes d'entraînement + cadre de réflexion à sept dimensions + mécanisme LOOP agent + algorithme d'hybridation quantique MoziSmartBit).

La technologie de quantification intelligente MoziSmartBit comprime le modèle Dense de 27 milliards de paramètres à environ 13,7 Go, soit 3,3 Go (~20%) de moins que la quantification Q4_K_M conventionnelle (~17 Go), avec **~99% de la précision FP16**.

Capacités : analyse financière, Q&A financière, programmation quantitative, appel d'outils, réflexion en chaîne, mécanisme LOOP, compatibilité multi-agent. Exécution de tâches sur 256K de contexte via OpenClaw/Hermes, réalisant la **liberté de tokens 7×24** tout en assurant la confidentialité des données locales.

Supporte llama.cpp, Ollama, LM Studio et autres frameworks d'inférence.

**Date de sortie : 2026-08-25** | **Version : V3.8**

## Caractéristiques du modèle

- **Spécialisation financière** : Optimisation approfondie pour Q&A financière, programmation quantitative, appels d'outils
- **Quantification intelligente MoziSmartBit** : Compression à **~12,79 Go** avec **~99% de précision**
- **Déploiement grand public** : 16 Go+ VRAM pour déploiement local, 20 Go+ pour le contexte 256K complet
- **Décodage spéculatif MTP** : Couche multi-token intégrée, vitesse x1.5-2
- **Multilingue** : 201 langues et dialectes
- **Programmation générale** : Python/JS/TS/Go/Rust
- **Compréhension visuelle** : Multimodale
- **Raisonnement avancé** : Entraînement en chaîne de pensée
- **Multi-framework** : llama.cpp, Ollama, LM Studio, Jan
- **Multi-agent** : OpenClaw, Hermes, Cursor, Claude Code

## Capacités clés

| Domaine | Description |
|---|---|
| Analyse de marché | Macro/microéconomie, actions, commodities, crypto |
| Finances & rapports | Indicateurs financiers, synthèses de recherche |
| Risque & conformité | Évaluation des risques, conseil en investissement |
| Quant & stratégie | Stratégies quant, Pyramide PEL, backtesting |
| Appels d'outils | Cours en temps réel, bases de données, recherche |

## Spécifications techniques

| Paramètre | Valeur |
|---|---|
| Modèle de base | Qwen3.8-27B (Dense, attention hybride, MIT) |
| Paramètres | 27 milliards Dense |
| Quantification | MoziSmartBit + format GGUF standard |
| Longueur de contexte | 256K (262 144 tokens) |
| Taille du modèle | ~12,79 Go |
| VRAM min. | **16 Go+** déployable (déchargement CPU nécessaire)；**20 Go+** contexte long fluide；**24 Go+** 256K complet + vision |
| Vitesse d'inférence | MTP : R9700 70+ tok/s, MAX+395 CPU 50+ tok/s, MAX+395 GPU 35+ tok/s |

## Formats de quantification

| Format | Taille | Précision | Description |
|---|---|---|---|
| FP16 (original) | ~54 Go | 100% | Précision 16 bits originale |
| **MoziSmartBit** | **~12,79 Go** | **~99%** | **Quantification intelligente auto-développée** |
| Q4_K_M | ~17 Go | ~98% | GGUF standard 4 bits |
| Q5_K_M | ~20 Go | ~99% | Précision supérieure |
| Q6_K | ~23 Go | ~99,5% | Quasi sans perte |
| Q8_0 | ~31 Go | ~100% | Sans perte |

## Décodage spéculatif MTP

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

| Paramètre | Recommandé | Description |
|---|---|---|
| --spec-type | draft-mtp | Activer MTP |
| --spec-draft-n-max | 2 | Max 2 tokens par étape (~80% taux d'acceptation) |
| --spec-draft-p-min | 0,75 | Seuil minimum de probabilité |

> 💡 **Désactiver MTP** : Supprimez les 3 lignes MTP. Vitesse -30-50%, VRAM réduite.

## Commande de démarrage llama.cpp

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
  --spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0,75 \
  --host 0.0.0.0 --port 8080 \
  --temp 0,6 --top-p 0,95 --top-k 20
```

## Configuration VRAM recommandée

| VRAM | Contexte | KV-cache | Vision | Description |
|---|---|---|---|---|
| 20 Go | 256K | q4_0 | Supportée | Configuration recommandée |
| 24 Go | 256K | q4_0 | Complète | VRAM suffisante |
| 32 Go+ | 256K | q4_0 | Complète | Meilleure configuration |

## Benchmarks

### Programmation

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

## Téléchargement

| Plateforme | Lien |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## Démarrage rapide

### 1. Télécharger

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf
├── moziAI-27B-3.8-mmproj-F16.gguf
└── chat-template-moziai-27B-v38.jinja
```

### 2. Lancer

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

### 3. Discuter

Ouvrir `http://localhost:8080` dans le navigateur

## Licence

Licence restrictive personnalisée : Usage commercial gratuit ✅ | Développement secondaire interdit ❌ | Revente interdite ❌

## Avertissement

Ce modèle est fourni "en l'état", sans garantie d'aucune sorte.

## Contact

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 Chen Yumo / chenyumo166. Tous droits réservés.
