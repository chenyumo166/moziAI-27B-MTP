---
language:
- es
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

# MoziAI-27B-3.8 — Un modelo de IA multimodal compacto pero potente, de despliegue local gratuito

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | Español | [Português](README.pt.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md) | [Polski](README.pl.md)

**Fecha de publicación: 2026-08-30** · **Versión: V3.8**

---

## 📑 Índice

- [1. Resumen del modelo](#1-resumen-del-modelo)
- [2. Características principales](#2-características-principales) — Pensamiento dinámico de siete dimensiones / LOOP / MoziSmartBit / Enfoque financiero
- [3. Notas de actualización de versión](#3-notas-de-actualización-de-versión)
- [4. Capacidades principales](#4-capacidades-principales)
- [5. Especificaciones técnicas](#5-especificaciones-técnicas)
- [6. ⚡ Inicio rápido](#6--inicio-rápido-3-archivos--100-activación-de-la-mejor-capacidad-de-inferencia) — **descarga de 3 archivos**
- [7. Descarga del modelo](#7-descarga-del-modelo)
- [8. Comandos de ejecución](#8-comandos-de-ejecución)
- [9. Parámetros de inferencia recomendados](#9-parámetros-de-inferencia-recomendados)
- [10. Comparación de formatos de cuantización](#10-comparación-de-formatos-de-cuantización)
- [11. Decodificación especulativa MTP](#11-decodificación-especulativa-mtp-característica-clave-de-aceleración)
- [12. Recomendaciones de configuración de VRAM](#12-recomendaciones-de-configuración-de-vram)
- [13. Métodos de implementación](#13-métodos-de-implementación)
- [14. Benchmarks](#14-benchmarks)
- [15. Licencia](#15-licencia)
- [16. Contacto](#16-contacto)

---

## 1. Resumen del modelo

MoziAI-27B-3.8 es un modelo de IA multimodal de código abierto, implementable localmente, desarrollado por el equipo de Chen Yumo, destacado influencer financiero chino. Construido sobre la base de código abierto **Qwen3.8-27B** (arquitectura Dense 27B, licencia MIT), integra datos financieros propios del equipo + capacidades del dominio financiero + sistema de pensamiento dinámico de siete dimensiones + mecanismo de iteración y reflexión LOOP del agente + algoritmo de cuantización híbrida MoziSmartBit. Este modelo reduce la barrera de implementación local para individuos y empresas, está autorizado para **uso comercial gratuito**, se ejecuta en GPUs de consumo, ahorra costos de tokens en la nube, logra libertad de tokens 7×24 horas y garantiza privacidad y seguridad de datos locales.

---

## 2. Características principales

### 🧠 Sistema de pensamiento dinámico de siete dimensiones

Marco de razonamiento central desarrollado por MoziAI. Ante cualquier tarea, el modelo primero genera la marca **moziAI-Think**, luego expande dinámicamente el pensamiento estructurado según la complejidad:

| Nivel | Escenario | Tareas típicas | Dimensiones expandidas |
| --- | --- | --- | --- |
| **Nivel 0** | Preguntas simples | Explicación de términos, consulta de hechos, traducción, resumen | ①Comprender tarea ⑤Necesidades de recursos (respuesta rápida de 2 dimensiones) |
| **Nivel 1** | Análisis y diagnóstico | Investigación de mercado, redacción, análisis de datos, lectura de informes, evaluación de estrategias | ①②③⑤⑥ Evaluación de cinco dimensiones |
| **Nivel 2** | Desarrollo/estrategia compleja | Desarrollo de código, diseño de arquitectura, estrategias cuantitativas, flujos de trabajo multi-paso, diseño de sistemas | ①②③④⑤⑥⑦ Razonamiento profundo completo de siete dimensiones |

> Siete dimensiones: ①Comprender tarea ②Evaluar complejidad ③Dependencias ④Evaluar riesgos ⑤Necesidades de recursos ⑥Criterios de aceptación ⑦Estrategia de ejecución

### 🔄 Mecanismo de iteración LOOP del agente

Las tareas complejas entran automáticamente en el modo de iteración **moziAI-Loop**: **Ronda 1 ejecución + evaluación → Ronda 2 ajuste + verificación**, garantizando que la salida pase por autoverificación antes de la respuesta final. El modelo actúa como ingeniero senior: «descomponer problema → evaluar solución → ejecutar → reflexionar → optimizar», mejorando significativamente la precisión y viabilidad de tareas complejas. Las preguntas y tareas simples cierran Loop automáticamente.

### 📦 Cuantización inteligente MoziSmartBit

Cuantización inteligente por capas propia: el modelo Dense de 27 mil millones de parámetros se comprime a aproximadamente **13.7 GB**, unos 3.3 GB (~20%) más pequeño que Q4_K_M estándar (~17 GB), manteniendo **~99%** de precisión FP16. La cuantización tradicional aplica precisión uniforme a todas las capas; MoziSmartBit utiliza estrategia de diferenciación inteligente adaptada a la estructura Dense, con precisión superior a Q4_K_M.

### 💰 Enfoque en dominio financiero vertical

Optimización profunda para preguntas financieras, programación cuantitativa y llamadas de herramientas. El dominio financiero tiene tolerancia extremadamente baja a la alucinación del modelo; MoziAI supera significativamente a modelos generales de tamaño similar en este dominio.

### 🌐 Otras características

- **Soporte multilingüe**: 201 idiomas y dialectos, chino optimizado especialmente
- **Programación general**: desarrollo full-stack, depuración, diseño de arquitectura, cubre Python/JS/TS/Go/Rust
- **Redacción**: informes de investigación, artículos analíticos, documentación técnica, contenido creativo
- **Comprensión visual**: visión multimodal, comprensión local de capturas de pantalla
- **Soporte multi-framework**: llama.cpp / Ollama / LM Studio / Jan
- **Soporte multi-Agent**: OpenClaw / Hermes / Cursor / Claude Code / Codex, llamadas nativas de herramientas y orquestación multi-ronda

---

## 3. Notas de actualización de versión

Esta actualización refuerza principalmente: el modo de razonamiento propio de MoziAI «pensamiento dinámico de siete dimensiones + iteración LOOP», permitiendo reconocer la complejidad de las tareas de forma más inteligente, con mayor tasa de finalización de tareas complejas y mejor capacidad de «pensar primero, actuar después».

MoziAI mantiene una frecuencia activa de actualización de versiones, asegurando seguir el desarrollo futuro de la IA y, mediante tecnología propia, hacer que los modelos de IA locales sean más ligeros de implementar y cada vez más capaces.

---

## 4. Capacidades principales

| Área de capacidad | Descripción |
| --- | --- |
| Análisis de mercado | Interpretación macro/microeconómica, análisis de mercados A/HK/US/commodities/criptomonedas |
| Finanzas e informes | Interpretación de indicadores clave de informes financieros, resúmenes de investigación, valoración y proyección de ganancias |
| Riesgo y cumplimiento | Evaluación de riesgo de productos, recordatorios de cumplimiento de consejos de inversión, políticas regulatorias financieras |
| Cuantificación y estrategia | Diseño de estrategias cuantitativas, cuantificación Pyramid (PEL), lógica de backtesting, construcción de factores y llamadas de herramientas |
| Llamadas de herramientas | Conexión a datos de mercado en tiempo real, bases de datos, búsqueda de informes financieros |

---

## 5. Especificaciones técnicas

| Elemento | Especificación |
| --- | --- |
| Modelo base | Qwen3.8-27B (arquitectura Dense, atención híbrida 16 full + 48 linear, licencia MIT) |
| Tamaño de parámetros | 27 mil millones (27B) arquitectura Dense |
| Método de cuantización | Cuantización inteligente MoziSmartBit + formato estándar GGUF |
| Longitud de contexto | 256K (262 144 tokens) |
| Tamaño del modelo | ~13.7 GB |
| VRAM mínima | **16GB+** implementable (descarga CPU); **20GB+** contexto largo fluido; **32GB+** 256K completo + visión |
| Frameworks de inferencia | llama.cpp / Ollama / LM Studio / Jan |
| Velocidad de inferencia | Con decodificación especulativa MTP: R9700 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Equipo de desarrollo | Equipo Chen Yumo |

---

## 6. ⚡ Inicio rápido 3 archivos = 100% activación de la mejor capacidad de inferencia

> ⚠️ **Nota clave**: la mejor capacidad de inferencia de MoziAI requiere **descargar 3 archivos simultáneamente** — modelo principal, proyector de visión, plantilla de chat. La falta de cualquiera pierde la capacidad correspondiente.

### 6.1 Descarga de archivos del modelo

Descargue **todos los archivos del directorio V3.8** desde HuggingFace / ModelScope al mismo directorio local:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Modelo principal (obligatorio, 13.7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Plantilla de chat (obligatoria, con instrucciones de pensamiento+Loop)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Proyector de visión (obligatorio, 927 MB)
```

| Archivo | Tamaño | Necesidad | Función |
| --- | --- | --- | --- |
| Modelo principal `.gguf` | ~13.7 GB | **Obligatorio** | Pesos del modelo, capacidad de inferencia central |
| Proyector de visión `mmproj` | ~927 MB | **Obligatorio** | Comprensión visual multimodal, sin él se pierde capacidad de imagen |
| Plantilla de chat `.jinja` | Mínimo | **Obligatoria** | Inyecta identidad MoziAI + instrucciones de pensamiento de siete dimensiones + mecanismo LOOP |

### 6.2 Inicio y uso

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Abra `http://localhost:8080` en el navegador para iniciar la conversación. Parámetros completos recomendados en la Sección 9.

---

## 7. Descarga del modelo

| Plataforma | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP) |

> 💡 **Usuarios de LM Studio**: busque `moziAI` en [LM Studio](https://lmstudio.ai) para descarga con un clic, sin descargar archivos manualmente.

---

## 8. Comandos de ejecución

### Inicio mínimo (con los 3 archivos)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Inicio completo recomendado

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 262144 -ngl 99 -t 28 \
  --batch-size 1024 --ubatch-size 128 \
  --flash-attn auto \
  --cache-type-k q4_0 --cache-type-v q4_0 --kv-unified \
  --poll 0 \
  --reasoning auto --reasoning-budget 1024 --reasoning-format deepseek-legacy \
  --spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75 \
  --host 0.0.0.0 --port 8080 \
  --temp 0.6 --top-p 0.95 --top-k 20
```

> 💡 Para desactivar MTP: elimine `--spec-type draft-mtp` y parámetros relacionados; velocidad ~30-50% menor, menor uso de VRAM.

---

## 9. Parámetros de inferencia recomendados

Basado en parámetros oficiales recomendados de llama.cpp y optimización local (AMD Radeon AI PRO R9700 32GB):

| Parámetro | Chat general | Codificación/Agent | Notas |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | Equilibrio entre creatividad y precisión |
| top\_p | 0.95 | 0.95 | Umbral de muestreo nuclear |
| top\_k | 20 | 20 | Muestreo truncado |
| repeat\_penalty | 1.05 | 1.05 | Penalización de repetición |
| context\_length | 131072 | 262144 | Chat 128K / Codificación 256K (llama.cpp por defecto 128K) |
| reasoning | auto | auto | Activar cadena de razonamiento (CoT) |
| reasoning\_budget | 400 | 400 | Presupuesto de tokens de razonamiento |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Razonamiento en campo separado |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Decodificación especulativa MTP (ver Sección 11)** |

> 💡 **Modo de pensamiento**: activado con `--reasoning auto` — el modelo razona internamente antes de responder. `reasoning_budget` controla el máximo de tokens de pensamiento (recomendado 400, ajustable 100-1000).

---

## 10. Comparación de formatos de cuantización

| Formato | Tamaño | Precisión | Notas |
| --- | --- | --- | --- |
| FP16 original | ~54 GB | 100% | Sin pérdidas, requiere GPU profesional |
| **MoziSmartBit (este modelo)** | **~13.7 GB** | **~99%** | **Cuantización inteligente propia, mejor precisión por tamaño** |
| Q4_K_M | ~17 GB | ~98% | GGUF estándar 4-bit |
| Q5_K_M | ~20 GB | ~99% | Mayor precisión |
| Q6_K | ~23 GB | ~99.5% | Casi sin pérdidas |
| Q8_0 | ~31 GB | ~100% | Sin pérdidas |

> MoziSmartBit mantiene ~99% de precisión comprimiendo el modelo Dense 27B a 13.7 GB (compresión 3.9x), ~20% más pequeño que Q4_K_M — ideal para GPUs de consumo.

---

## 11. Decodificación especulativa MTP característica clave de aceleración

Este modelo incorpora la capa de decodificación especulativa MTP (Multi-Token Prediction), que aumenta la velocidad de inferencia **1.5-2 veces** al activarse. Es una característica nativa de la arquitectura Qwen3.8; MoziAI conserva los pesos MTP completos.

**Principio**: se entrena un cabezal de predicción ligero (Draft Model) en la arquitectura, que adivina tokens posteriores antes de la verificación del modelo principal, reduciendo las pasadas forward y la latencia. Los errores de predicción son corregidos por el modelo principal, sin impacto negativo en la calidad de salida.

### Parámetros de activación

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parámetro | Valor recomendado | Descripción |
| --- | --- | --- |
| --spec-type | draft-mtp | Activa la decodificación especulativa MTP |
| --spec-draft-n-max | 2 | Máximo 2 tokens adivinados por paso (recomendado, tasa de aceptación ~80%) |
| --spec-draft-p-min | 0.75 | Umbral mínimo de probabilidad de aceptación (0.0-1.0, mayor = más conservador) |

### Ajustes sugeridos

| n-max | Tasa de aceptación | Escenario |
| --- | --- | --- |
| 1 | ~90% | Más conservador, menor ganancia de velocidad |
| **2** | **~80%** | **Recomendado: equilibrio entre velocidad y precisión** |
| 3 | ~71% | Escenario general, mejora notable de velocidad |
| 4-5 | ~60-65% | Escritura creativa, generación de código |
| 6 | ~50-55% | Salida larga de texto puro (requiere ajustar p-min) |

---

## 12. Recomendaciones de configuración de VRAM

| VRAM | Configuración recomendada | Descripción |
| --- | --- | --- |
| 16 GB | Contexto reducido a 64K, requiere descarga CPU | Nivel de entrada, como RTX 4060 Ti |
| **20 GB** | **128K completo, caché KV q4_0** | **Configuración recomendada**, como RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K completo, margen VRAM amplio | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 256K completo, configuración más potente | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 256K completo | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Cuanto más largo el contexto, más VRAM. En OOM reduzca `-c` gradualmente. Use `--fit on` para ajuste automático de capas. Compatible con NVIDIA / AMD / Intel.

---

## 13. Métodos de implementación

### Implementación con Ollama

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

Busque `moziAI` en LM Studio / Jan y seleccione la versión Q4\_K\_M para descargar.

> 💡 El soporte de Ollama para mmproj y chat\_template es limitado; se recomienda llama.cpp para funcionalidad completa.

---

## 14. Benchmarks

MoziAI-27B-3.8 se basa en el ajuste fino de la base Qwen3.8-27B, con el dominio financiero vertical como dirección central de optimización.

### Capacidad de programación

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Capacidad de agente

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Capacidad general

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Capacidad multimodal

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Los datos de los competidores son resultados oficiales publicados. El dominio financiero vertical de MoziAI (interpretación de informes financieros, estrategias cuantitativas, cumplimiento de riesgos, llamadas de herramientas de agentes) supera significativamente a los modelos generales.

---

## 15. Licencia

Este modelo utiliza una **licencia restrictiva personalizada**:

- ✅ **Permitido** — uso comercial gratuito, copia y distribución
- ❌ **Prohibido** — desarrollo posterior, reventa, sublicencia
- 📋 **Requerido** — conservar el aviso de copyright original, acreditar: moziAI-27B

El modelo se proporciona \"tal cual\", sin garantías de ningún tipo. La salida del modelo es solo de referencia y no constituye asesoramiento de inversión. El usuario asume todos los riesgos.

Consulte el archivo [LICENSE](LICENSE) para conocer los términos completos.

---

## 16. Contacto

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
