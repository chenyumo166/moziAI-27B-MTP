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

# MoziAI-27B-3.8 — Un modèle d'IA multimodal compact et puissant, déployable localement gratuitement

[English](README.en.md) | [简体中文](README.zh.md) | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | [Español](README.es.md) | [Português](README.pt.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md) | [Polski](README.pl.md)

**Date de sortie : 2026-08-30** · **Version : V3.8**

---

## 📑 Table des matières

- [1. Présentation du modèle](#1-présentation-du-modèle)
- [2. Caractéristiques du modèle](#2-caractéristiques-du-modèle) — Pensée dynamique en sept dimensions / LOOP / MoziSmartBit / Focus finance
- [3. Notes de version](#3-notes-de-version)
- [4. Capacités principales](#4-capacités-principales)
- [5. Spécifications techniques](#5-spécifications-techniques)
- [6. ⚡ Démarrage rapide](#6-démarrage-rapide-3-fichiers--100-dactivation-du-raisonnement-optimal) — **Téléchargement des trois fichiers**
- [7. Téléchargement du modèle](#7-téléchargement-du-modèle)
- [8. Commandes de démarrage](#8-commandes-de-démarrage)
- [9. Paramètres de raisonnement recommandés](#9-paramètres-de-raisonnement-recommandés)
- [10. Comparaison des formats de quantification](#10-comparaison-des-formats-de-quantification)
- [11. Décodage spéculatif MTP](#11-décodage-spéculatif-mtp-accélération-majeure)
- [12. Configuration VRAM](#12-configuration-vram-recommandée)
- [13. Options de déploiement](#13-options-de-déploiement)
- [14. Évaluations de référence](#14-évaluations-de-référence)
- [15. Licence](#15-licence)
- [16. Contact](#16-contact)

---

## 1. Présentation du modèle

MoziAI-27B-3.8 est un modèle d'IA multimodal open source local, développé par l'équipe de Chen Yumo, grand influenceur financier chinois. Il repose sur la base open source **Qwen3.8-27B** (architecture Dense 27B, licence MIT), combinée aux technologies développées en interne par l'équipe : données financières + compétences en finance + système de pensée dynamique en sept dimensions + mécanisme de réflexion itérative LOOP pour agents + algorithme de quantification hybride MoziSmartBit. Ce modèle abaisse le seuil de déploiement local pour les particuliers et les entreprises, avec une autorisation d'**utilisation commerciale gratuite**. Il peut être déployé localement sur des cartes graphiques grand public, réduisant considérablement les coûts de tokens cloud, offrant une liberté de tokens 7×24 heures et garantissant la confidentialité et la sécurité des données locales.

---

## 2. Caractéristiques du modèle

### 🧠 Système de pensée dynamique en sept dimensions

Cadre de raisonnement central développé par MoziAI. Face à toute tâche, le modèle émet d'abord le marqueur **moziAI-Think**, puis déploie dynamiquement une réflexion structurée en fonction de la complexité de la tâche :

| Niveau | Cas d'usage | Tâches typiques | Dimensions déployées |
| --- | --- | --- | --- |
| **Level 0** | Questions-réponses simples | Explication de termes, recherche factuelle, traduction, résumé | ①Compréhension de la tâche ⑤Besoins en ressources (réponse rapide sur 2 dimensions) |
| **Level 1** | Analyse et diagnostic | Étude de marché, rédaction de contenu, analyse de données, interprétation de rapports de recherche, évaluation de stratégies | ①②③⑤⑥ Évaluation sur 5 dimensions |
| **Level 2** | Développement/stratégies complexes | Développement de code, conception d'architecture, développement de stratégies quantitatives, workflows multi-étapes, conception de systèmes | ①②③④⑤⑥⑦ Déduction approfondie sur les 7 dimensions |

> Les sept dimensions : ①Compréhension de la tâche ②Évaluation de la complexité ③Dépendances ④Évaluation des risques ⑤Besoins en ressources ⑥Critères d'acceptation ⑦Stratégie d'exécution

### 🔄 Mécanisme d'itération LOOP pour agents

Les tâches complexes entrent automatiquement en mode itératif **moziAI-Loop** : **1er tour exécution + évaluation → 2e tour ajustement + validation**, garantissant que la sortie est auto-vérifiée avant de fournir la réponse finale. Comme un ingénieur expérimenté, le modèle « décompose le problème → évalue la solution → exécute → réfléchit → optimise », améliorant considérablement la précision et l'exécutabilité des tâches complexes. Le Loop est automatiquement désactivé pour les questions et tâches simples.

### 📦 Quantification intelligente MoziSmartBit

Quantification intelligente stratifiée développée en interne : le modèle Dense de 27 milliards de paramètres est compressé à environ **13,7 Go**, soit environ 3,3 Go (~20 %) de moins que le Q4_K_M standard (~17 Go), tout en conservant **~99 %** de la précision FP16. La quantification traditionnelle applique une précision uniforme à toutes les couches ; MoziSmartBit adopte une stratégie de différenciation intelligente adaptée à la structure des modèles Dense, avec une précision supérieure à celle du Q4_K_M.

### 💰 Focalisation sur le secteur financier vertical

Optimisation approfondie pour les questions-réponses financières, la programmation quantitative et l'appel d'outils. Le secteur financier tolère extrêmement mal les hallucinations des modèles ; MoziAI y surpasse nettement les modèles généralistes de taille équivalente.

### 🌐 Autres caractéristiques

- **Prise en charge multilingue** : 201 langues et dialectes, capacités en chinois particulièrement optimisées
- **Programmation générale** : développement full-stack, débogage de code, conception d'architecture, couvrant Python/JS/TS/Go/Rust
- **Rédaction d'articles** : rapports de recherche, articles d'analyse, documentation technique, contenu créatif — rédaction de haute qualité tous genres confondus
- **Compréhension visuelle** : vision multimodale, compréhension du contenu des images via captures d'écran locales
- **Prise en charge multi-frameworks** : llama.cpp / Ollama / LM Studio / Jan
- **Prise en charge multi-agents** : OpenClaw / Hermes / Cursor / Claude Code / Codex, etc. — appel d'outils natif et orchestration de tâches multi-tours

---

## 3. Notes de version

Cette mise à jour renforce principalement : le mode de raisonnement dynamique en sept dimensions + l'itération LOOP développés par moziAI, lui permettant de reconnaître plus intelligemment la complexité des tâches, d'atteindre un taux d'achèvement plus élevé sur les tâches complexes et d'améliorer sa capacité à « réfléchir avant d'agir ».

moziAI maintiendra un rythme actif de mises à jour itératives afin de suivre de près l'évolution future de l'intelligence artificielle, et continuera, grâce à ses technologies propriétaires, à rendre le déploiement des modèles d'IA locaux plus léger et leurs capacités toujours plus puissantes.

---

## 4. Capacités principales

| Domaine de compétence | Description |
| --- | --- |
| Analyse de marché | Interprétation macro/micro-économique, analyse des cours et de la logique des actions A / actions de Hong Kong / actions américaines / matières premières / cryptomonnaies |
| Finance et rapports de recherche | Interprétation des indicateurs clés des rapports financiers, extraction de résumés de rapports de recherche, aide à l'évaluation et aux prévisions de bénéfices |
| Gestion des risques et conformité | Évaluation des risques des produits, alertes de conformité pour les conseils en investissement, interprétation des politiques de réglementation financière |
| Quantitatif et stratégies | Conception d'idées de stratégies quantitatives, quantification Pyramid (PEL), logique de backtest, construction de facteurs et appel d'outils |
| Appel d'outils | Connexion aux sources de données financières telles que les cotations en temps réel, les bases de données et la recherche de rapports |

---

## 5. Spécifications techniques

| Élément | Paramètre |
| --- | --- |
| Modèle de base | Qwen3.8-27B (architecture Dense, attention mixte 16 full + 48 linear, licence MIT) |
| Nombre de paramètres | 27 milliards (27B), architecture Dense |
| Méthode de quantification | Quantification intelligente MoziSmartBit propriétaire + format standard GGUF |
| Longueur du contexte | 128K (262 144 tokens) |
| Taille du modèle | ~13,7 Go |
| VRAM minimale | **16 Go+** déployable (déchargement CPU) ; **20 Go+** long contexte fluide ; **24 Go+** 128K complet + vision |
| Framework d'inférence | llama.cpp / Ollama / LM Studio / Jan |
| Vitesse d'inférence | Avec décodage spéculatif MTP : 70+ tok/s sur R9700, 50+ tok/s sur iGPU MAX+395, 35+ tok/s sur GPU |
| Équipe de développement | Équipe de Chen Yumo |

---

## 6. ⚡ Démarrage rapide (3 fichiers = 100 % d'activation du raisonnement optimal)

> ⚠️ **Point essentiel** : les capacités de raisonnement optimales de MoziAI nécessitent le **téléchargement simultané de 3 fichiers** — le modèle principal, la projection visuelle et le modèle de chat. L'absence de l'un d'entre eux entraîne la perte de la capacité correspondante.

### 6.1 Téléchargement des fichiers du modèle

Téléchargez **tous les fichiers du répertoire V3.8** depuis HuggingFace / ModelScope dans le même répertoire local :

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← 主模型（必选，13.7 GB）
└── chat-template-moziai-27B-V3.8.jinja         ← 聊天模板（必选，含七维思考+Loop指令）

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf            ← 视觉投影（必选，927 MB）
```

| Fichier | Taille | Nécessité | Rôle |
| --- | --- | --- | --- |
| Modèle principal `.gguf` | ~13,7 Go | **Obligatoire** | Poids du modèle, capacité de raisonnement principale |
| Projection visuelle `mmproj` | ~927 Mo | **Obligatoire** | Compréhension visuelle multimodale ; sans chargement, les capacités d'image sont perdues |
| Modèle de chat `.jinja` | Minimal | **Obligatoire** | Injecte l'identité MoziAI + les instructions du système de pensée en sept dimensions + du mécanisme LOOP |

### 6.2 Démarrage et utilisation

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Ouvrez `http://localhost:8080` dans votre navigateur pour commencer la conversation. Les paramètres complets recommandés figurent à la section 9.

---

## 7. Téléchargement du modèle

| Plateforme | Adresse |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main) |
| ModelScope (Módā) | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master) |

> 💡 **Utilisateurs de LM Studio** : recherchez `moziAI` dans [LM Studio](https://lmstudio.ai) pour un téléchargement en un clic, sans téléchargement manuel des fichiers.

---

## 8. Commandes de démarrage

### Démarrage minimal (avec les trois fichiers)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Démarrage complet recommandé

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

> 💡 Pour désactiver MTP : supprimez `--spec-type draft-mtp` et les paramètres associés ; la vitesse diminue d'environ 30 à 50 % mais l'utilisation de la VRAM est réduite.

---

## 9. Paramètres de raisonnement recommandés

Basés sur les paramètres recommandés officiellement par llama.cpp et optimisés par des tests locaux (AMD Radeon AI PRO R9700 32 Go) :

| Paramètre | Chat général | Codage/Agent | Description |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Équilibre entre créativité et précision |
| top\_p | 0.95 | 0.95 | Seuil d'échantillonnage par noyau (nucleus sampling) |
| top\_k | 20 | 20 | Échantillonnage par troncature |
| repeat\_penalty | 1.05 | 1.05 | Pénalité de répétition |
| context\_length | 262144 | 262144 | Contexte long de 128K |
| reasoning | auto | auto | Active la chaîne de raisonnement (chaîne de pensée) |
| reasoning\_budget | 400 | 400 | Budget de tokens de raisonnement |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Sortie du raisonnement dans un champ séparé |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Décodage spéculatif MTP (voir section 11)** |

> 💡 **Mode réflexion** : activé via `--reasoning auto`, le modèle effectue d'abord un raisonnement interne avant de fournir la réponse. `reasoning_budget` contrôle le nombre maximal de tokens de réflexion (400 recommandé, réglable de 100 à 1000).

---

## 10. Comparaison des formats de quantification

| Format | Taille | Précision | Description |
| --- | --- | --- | --- |
| FP16 original | ~54 Go | 100 % | Sans perte, nécessite une carte graphique professionnelle |
| **MoziSmartBit (ce modèle)** | **~13,7 Go** | **~99 %** | **Quantification intelligente propriétaire, précision optimale, taille minimale** |
| Q4_K_M | ~17 Go | ~98 % | GGUF 4 bits standard |
| Q5_K_M | ~20 Go | ~99 % | Précision supérieure |
| Q6_K | ~23 Go | ~99,5 % | Quasi sans perte |
| Q8_0 | ~31 Go | ~100 % | Sans perte |

> MoziSmartBit compresse le modèle Dense 27B à 13,7 Go (taux de compression 3,9x) tout en conservant environ 99 % de précision, soit environ 20 % de moins que le Q4_K_M, ce qui le rend plus adapté au déploiement local sur des cartes graphiques grand public.

---

## 11. Décodage spéculatif MTP (accélération majeure)

Ce modèle intègre une couche de décodage spéculatif MTP (Multi-Token Prediction). Une fois activée, la vitesse d'inférence est multipliée par **1,5 à 2**. Il s'agit d'une fonctionnalité native de l'architecture Qwen3.8 ; MoziAI a conservé l'intégralité des poids MTP.

**Principe** : une tête de prédiction légère (modèle de draft) est entraînée en plus dans l'architecture du modèle. Elle devine à l'avance les tokens suivants avant la validation par le modèle principal, réduisant le nombre de passes forward et la latence d'inférence. Les erreurs de prédiction sont corrigées par le modèle principal, sans impact négatif sur la qualité de la sortie.

### Paramètres d'activation

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Paramètre | Valeur recommandée | Description |
| --- | --- | --- |
| --spec-type | draft-mtp | Active le décodage spéculatif MTP |
| --spec-draft-n-max | 2 | Devine au maximum 2 tokens à la fois (valeur recommandée, taux d'acceptation d'environ 80 %) |
| --spec-draft-p-min | 0.75 | Seuil minimal de probabilité d'acceptation (0,0-1,0 ; plus il est élevé, plus c'est conservateur) |

### Conseils de réglage des paramètres

| n-max | Taux d'acceptation | Cas d'usage |
| --- | --- | --- |
| 1 | ~90 % | Le plus conservateur, gain de vitesse minimal |
| **2** | **~80 %** | **Recommandé : équilibre entre vitesse et précision** |
| 3 | ~71 % | Scénarios généraux, gain de vitesse notable |
| 4-5 | ~60-65 % | Rédaction créative, génération de code |
| 6 | ~50-55 % | Sorties longues en texte pur (à ajuster avec p-min) |

---

## 12. Configuration VRAM recommandée

| VRAM | Configuration recommandée | Description |
| --- | --- | --- |
| 16 Go | Contexte réduit à 64K, déchargement CPU requis | Niveau d'entrée, par ex. RTX 4060 Ti |
| **20 Go** | **128K complet, cache KV q4_0** | **Configuration recommandée**, par ex. RX 7900 XT / RTX 5070 Ti |
| 24 Go | 128K complet, marge VRAM confortable | RTX 4090 / RX 7900 XTX |
| 32 Go et plus | 128K complet, configuration la plus puissante | Radeon AI PRO R9700 / RTX 5090 |
| 128 Go iGPU | 128K complet | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Plus le contexte est long, plus la VRAM utilisée est importante. En cas d'OOM, réduisez progressivement le paramètre `-c`. Utilisez `--fit on` pour laisser llama.cpp ajuster automatiquement le nombre de couches en fonction de la VRAM. Compatible avec toutes les cartes graphiques NVIDIA / AMD / Intel.

---

## 13. Options de déploiement

### Déploiement avec Ollama

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

Recherchez `moziAI` dans LM Studio / Jan et téléchargez la version quantifiée Q4\_K\_M.

> 💡 La prise en charge de mmproj et du chat\_template par Ollama est limitée ; il est recommandé d'utiliser llama.cpp en priorité pour bénéficier de toutes les fonctionnalités.

---

## 14. Évaluations de référence

MoziAI-27B-3.8 est un modèle affiné (fine-tuning) à partir de la base Qwen3.8-27B, avec le secteur financier vertical comme direction d'optimisation principale.

### Capacités de codage

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Capacités d'agent

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Capacités générales

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Capacités multimodales

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Les données des concurrents proviennent de résultats d'évaluation officiellement publiés. Dans le secteur financier vertical (interprétation des rapports financiers, stratégies quantitatives, gestion des risques et conformité, appel d'outils par agents, etc.), MoziAI surpasse nettement les modèles généralistes.

---

## 15. Licence

Ce modèle est distribué sous une **licence restrictive personnalisée** :

- ✅ **Autorisé** — utilisation commerciale gratuite, copie et distribution
- ❌ **Interdit** — développement dérivé, revente, sous-licenciement
- 📋 **Exigé** — conserver la mention de copyright d'origine et indiquer la source : moziAI-27B

Ce modèle est fourni « en l'état », sans garantie d'aucune sorte. Les sorties du modèle sont fournies à titre informatif uniquement et ne constituent pas des conseils en investissement. L'utilisateur assume l'ensemble des risques liés à son utilisation.

Veuillez consulter le fichier [LICENSE](LICENSE) pour les conditions détaillées.

---

## 16. Contact

- **HuggingFace** : [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub** : [@chenyumo166](https://github.com/chenyumo166)
- **Weibo** : [@rimochen](https://weibo.com/rimochen)
- **E-mail** : 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. Tous droits réservés.
