---
language:
- en
- ru
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

# MoziAI-27B-3.8 - Бесплатная локальная установка малой, но мощной мультимодальной AI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | Русский

## Обзор модели

MoziAI-27B-3.8 — локальная open-source финансовая AI мультимодальная LLM (с поддержкой зрения и вызова инструментов), разработанная командой китайского финансового инфлюенсера Чэнь Юймо. Основана на open-source базовой модели Qwen3.8-27B (Dense 27B, MIT лицензия), интегрируя自主研发ные технологии: (финансовые данные + финансовые способности + методы обучения + семимерное мышление + LOOP механизм агента + гибридный алгоритм квантования MoziSmartBit).

Собственная технология интеллектуальной квантации MoziSmartBit сжимает 27-миллиардную Dense модель до ~13.7 ГБ (на 3.3 ГБ / ~20% меньше Q4_K_M), сохраняя **~99% точности FP16**.

Финансовые возможности: Q&A, количественное программирование, вызов инструментов, мышление в 7 измерениях, LOOP механизм, совместимость с агентами. Выполнение 256K контекстных задач через OpenClaw/Hermes, реализация **свободы токенов 7×24** с локальной конфиденциальностью данных.

Поддерживает llama.cpp, Ollama, LM Studio и другие фреймворки вывода.

**Дата релиза: 2026-08-25** | **Версия: V3.8**

## Особенности

- **Финансовая специализация**: Усиление финансового Q&A, количественного программирования, вызова инструментов
- **MoziSmartBit**: Сжатие до **~13.7 ГБ**, сохраняя **~99% точности**
- **Потребительские GPU**: 16 ГБ+ VRAM для локального развертывания, 20 ГБ+ для полного 256K длинного контекста
- **MTP спекулятивная декодация**: Ускорение вывода в 1.5-2 раза
- **Мультиязычность**: 201 языков и диалектов
- **Программирование**: Python/JS/TS/Go/Rust
- **Визуальное восприятие**: Мультимодальное
- **Расширенное мышление**: Обучение цепочкой рассуждений
- **Мульти-фреймворк**: llama.cpp, Ollama, LM Studio, Jan
- **Мульти-агенты**: OpenClaw, Hermes, Cursor, Claude Code

## Ключевые возможности

| Область | Описание |
|---|---|
| Анализ рынка | Макро/микроэкономика, акции, товары, криптовалюта |
| Финансы | Финансовые показатели, резюме исследований |
| Риск и комплаенс | Оценка рисков, инвестиционные рекомендации |
| Кванты и стратегии | Квант-стратегии, Пирамида PEL, бэктестинг |
| Вызов инструментов | Котировки, базы данных, поиск исследований |

## Технические характеристики

| Параметр | Значение |
|---|---|
| Базовая модель | Qwen3.8-27B (Dense, гибридное внимание, MIT) |
| Параметры | 27 млрд Dense |
| Квантование | MoziSmartBit + GGUF формат |
| Контекст | 256K (262,144 токена) |
| Размер модели | ~13.7 ГБ |
| Мин. VRAM | **16 ГБ+** (с CPU offload)；**20 ГБ+** длинный контекст；**24 ГБ+** полный 256K + визуал |
| Скорость | MTP: R9700 70+ tok/s, MAX+395 CPU 50+ tok/s |

## Форматы квантования

| Формат | Размер | Точность |
|---|---|---|
| FP16 | ~54 ГБ | 100% |
| **MoziSmartBit** | **~13.7 ГБ** | **~99%** |
| Q4_K_M | ~17 ГБ | ~98% |
| Q5_K_M | ~20 ГБ | ~99% |
| Q6_K | ~23 ГБ | ~99.5% |
| Q8_0 | ~31 ГБ | ~100% |

## MTP спекулятивная декодация

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

> 💡 **Отключение MTP**: Удалите 3 строки. Скорость снижается ~30-50%, VRAM уменьшается.

## Запуск llama.cpp

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
  --spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75 \
  --host 0.0.0.0 --port 8080 \
  --temp 0.6 --top-p 0.95 --top-k 20
```

## Рекомендуемая VRAM

| VRAM | Контекст | KV-cache | Визия |
|---|---|---|---|
| 20 ГБ | 256K | q4_0 | Поддержка |
| 24 ГБ | 256K | q4_0 | Полная |
| 32 ГБ+ | 256K | q4_0 | Полная |

## Бенчмарки

| Бенчмарк | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 |
| QwenSWEBench | **79.0** | 49.3 | 59.2 |
| CoWorkBench | **70.7** | 61.0 | 65.1 |
| JobBench | **33.4** | 21.8 | 27.6 |

## Скачивание

| Платформа | Ссылка |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## Быстрый старт

### 1. Скачать

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf
├── moziAI-27B-3.8-mmproj-F16.gguf
└── chat-template-moziai-27B-v38.jinja
```

### 2. Запустить

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

### 3. Чат

Откройте `http://localhost:8080` в браузере

## Лицензия

Пользовательская ограниченная лицензия: бесплатное коммерческое использование ✅ | Вторичная разработка запрещена ❌ | Перепродажа запрещена ❌

## Отказ от ответственности

Модель предоставляется "как есть" без каких-либо гарантий.

## Контакты

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 Чэнь Юймо / chenyumo166. Все права защищены.
