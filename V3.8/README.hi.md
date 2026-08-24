---
language:
- en
- hi
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

# MoziAI-27B-3.8 - मुफ्त में स्थानीय रूप से तैनात करने योग्य छोटा लेकिन शक्तिशाली बहुमोडल AI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | हिन्दी | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## मॉडल अवलोकन

MoziAI-27B-3.8 चीनी वित्तीय प्रभावकर्ता चेन युमो की टीम द्वारा विकसित एक स्थानीय ओपन-सोर्स वित्तीय AI बहुमोडल LLM है (दृष्टि और टूल कॉलिंग समर्थन)। ओपन-सोर्स बेस मॉडल Qwen3.8-27B (Dense 27B आर्किटेक्चर, MIT लाइसेंस) पर आधारित, स्व-विकसित प्रौद्योगिकियों का एकीकरण: (वित्तीय डेटा + वित्तीय डोमेन क्षमताएं + प्रशिक्षण विधियां + सात-आयामी सोच फ्रेमवर्क + एजेंट LOOP मैकेनिज्म + हाइब्रिड क्वांटाइजेशन एल्गोरिदम MoziSmartBit)।

MoziSmartBit बुद्धिमान क्वांटाइजेशन तकनीक 27 अरब पैरामीटर Dense मॉडल को ~13.7 GB तक संपीड़ित करती है, जो Q4_K_M से ~20% छोटा है और FP16 की **~99% सटीकता** बनाए रखता है।

वित्तीय डोमेन गहन अनुकूलन, वित्तीय Q&A, क्वांटम प्रोग्रामिंग, टूल कॉलिंग, सात-आयामी सोच, LOOP मैकेनिज्म। OpenClaw/Hermes के माध्यम से 256K संदर्भ कार्य, **7×24 टोकन स्वतंत्रता**।

llama.cpp, Ollama, LM Studio समर्थित।

**रिलीज़ दिनांक: 2026-08-25** | **संस्करण: V3.8**

## मॉडल विशेषताएं

- **वित्तीय गहनता**: वित्तीय Q&A, क्वांटम प्रोग्रामिंग, टूल कॉलिंग
- **MoziSmartBit**: ~13.7 GB तक संपीड़न, **~99% सटीकता**
- **उपभोक्ता GPU**: 20GB+ VRAM, 256K लंबा संदर्भ
- **MTP सटीक डीकोडिंग**: 1.5-2x गति वृद्धि
- **बहुभाषी**: 201 भाषाएं
- **सामान्य प्रोग्रामिंग**: Python/JS/TS/Go/Rust
- **दृश्य समझ**: बहुमोडल

## तकनीकी विशिष्टताएं

| आइटम | मान |
|---|---|
| बेस मॉडल | Qwen3.8-27B (Dense, MIT) |
| पैरामीटर | 27 अरब Dense |
| क्वांटाइजेशन | MoziSmartBit + GGUF |
| संदर्भ लंबाई | 256K (262,144 टोकन) |
| मॉडल आकार | ~13.7 GB |
| न्यूनतम VRAM | 20GB+ |

## MTP सटीक डीकोडिंग

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

> 💡 MTP बंद करने के लिए: ये 3 पंक्तियां हटाएं। गति -30-50%, VRAM कम।

## llama.cpp कमांड

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

## बेंचमार्क

| बेंचमार्क | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 |
| CoWorkBench | **70.7** | 61.0 | 65.1 |
| IFBench | **79.5** | 69.1 | 79.1 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 |

## डाउनलोड

| प्लेटफ़ॉर्म | लिंक |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## त्वरित शुरुआत

### 1. डाउनलोड

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf
├── moziAI-27B-3.8-mmproj-F16.gguf
└── chat-template-moziai-27B-v38.jinja
```

### 2. प्रारंभ

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 262144 -ngl 99
```

### 3. चैट शुरू करें

ब्राउज़र में `http://localhost:8080` खोलें

## लाइसेंस

कस्टम प्रतिबंधित लाइसेंस: मुफ्त वाणिज्यिक उपयोग ✅ | द्वितीयक विकास वर्जित ❌ | पुनर्विक्रय वर्जित ❌

## संपर्क

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 चेन युमो / chenyumo166. सर्वाधिकार सुरक्षित।
