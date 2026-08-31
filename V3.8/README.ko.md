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

# MoziAI-27B-3.8 — 무료로 로컬 배포할 수 있는 작지만 강력한 멀티모달 AI 모델

[English](README.en.md) | [简体中文](README.zh.md) | [繁体中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

**출시일: 2026-08-30** · **버전: V3.8**

---

## 📑 목차

- [1. 모델 개요](#1-모델-개요)
- [2. 모델 특징](#2-모델-특징) — 동적 7차원 사고 / LOOP / MoziSmartBit / 금융 특화
- [3. 버전 업그레이드 안내](#3-버전-업그레이드-안내)
- [4. 핵심 역량](#4-핵심-역량)
- [5. 기술 사양](#5-기술-사양)
- [6. ⚡ 빠른 시작](#6-빠른-시작-3개-파일-100-최고-추론-능력-활성화) — **3종 세트 다운로드**
- [7. 모델 다운로드](#7-모델-다운로드)
- [8. 시작 명령](#8-시작-명령)
- [9. 권장 추론 매개변수](#9-권장-추론-매개변수)
- [10. 양자화 형식 비교](#10-양자화-형식-비교)
- [11. MTP 추측 디코딩](#11-mtp-추측-디코딩-중요한-가속-기능)
- [12. VRAM 구성 권장](#12-vram-구성-권장)
- [13. 배포 방법](#13-배포-방법)
- [14. 벤치마크 평가](#14-벤치마크-평가)
- [15. 라이선스](#15-라이선스)
- [16. 연락처](#16-연락처)

---

## 1. 모델 개요

MoziAI-27B-3.8은 중국 금융 인플루언서 천위모(陈雨墨) 팀이 개발한 로컬 오픈소스 멀티모달 AI 대형 모델로, 오픈소스 베이스 모델 **Qwen3.8-27B**(Dense 27B 아키텍처, MIT 라이선스)를 기반으로 팀이 자체 개발한 금융 데이터 + 금융 분야 역량 + 동적 7차원 사고 체계 + 에이전트 LOOP 반성·반복 메커니즘 + MoziSmartBit 하이브리드 양자화 알고리즘을 결합하여 개발되었습니다. 본 모델은 개인과 기업의 로컬 배포 장벽을 낮추고 **무료 상업 사용**을 허용하며, 소비자용 그래픽 카드에서도 로컬 배포가 가능합니다. 클라우드 토큰 비용을 크게 절약하고 7×24시간 토큰 자유를 실현하며 로컬 데이터 프라이버시와 보안을 보장합니다.

---

## 2. 모델 특징

### 🧠 동적 7차원 사고 체계

MoziAI가 자체 개발한 핵심 추론 프레임워크입니다. 어떤 작업이든 모델은 먼저 **moziAI-Think** 마커를 출력하고, 작업 복잡도에 따라 구조화된 사고를 동적으로 전개합니다:

| 레벨 | 적용 시나리오 | 대표 작업 | 전개 차원 |
| --- | --- | --- | --- |
| **Level 0** | 단순 Q&A | 용어 설명, 사실 조회, 번역, 요약 | ①작업 이해 ⑤리소스 요구사항(2차원 빠른 응답) |
| **Level 1** | 분석·진단 | 시장 조사, 카피라이팅, 데이터 분석, 리서치 리포트 해석, 전략 평가 | ①②③⑤⑥ 5차원 평가 |
| **Level 2** | 복잡한 개발/전략 | 코드 개발, 아키텍처 설계, 퀀트 전략 개발, 다단계 워크플로우, 시스템 설계 | ①②③④⑤⑥⑦ 전체 7차원 심층 추론 |

> 7차원: ①작업 이해 ②복잡도 평가 ③의존 관계 ④위험 평가 ⑤리소스 요구사항 ⑥수용 기준 ⑦실행 전략

### 🔄 에이전트 LOOP 반복 메커니즘

복잡한 작업은 자동으로 **moziAI-Loop** 반복 모드에 진입합니다: **1차 실행+평가 → 2차 조정+검증**을 통해 출력이 자체 검증을 거친 후에만 최종 답변을 제공합니다. 모델은 베테랑 엔지니어처럼「문제 분해 → 방안 평가 → 실행 → 반성 → 최적화」를 수행하여 복잡한 작업의 정확성과 실행 가능성을 크게 향상시킵니다. 단순 질의응답과 작업에서는 Loop가 자동으로 꺼집니다.

### 📦 MoziSmartBit 스마트 양자화

자체 개발한 계층형 스마트 양자화로, 270억 파라미터 Dense 모델을 약 **13.7 GB**로 압축하여 일반 Q4_K_M(~17 GB)보다 약 3.3 GB(~20%) 작으면서도 FP16 **~99%** 정확도를 유지합니다. 기존 양자화는 모든 레이어에 동일한 정밀도를 사용하지만, MoziSmartBit은 Dense 모델의 구조적 특성에 맞춘 스마트 차별화 전략을 사용하여 Q4_K_M보다 우수한 정확도를 제공합니다.

### 💰 금융 수직 분야 집중

금융 질의응답, 퀀트 프로그래밍 및 도구 호출에 대한 심층 최적화를 수행했습니다. 금융 분야는 모델 환각(할루시네이션)에 대한 허용도가 매우 낮으며, MoziAI는 이 분야에서 동급 규모의 범용 모델보다 훨씬 뛰어난 성능을 보여줍니다.

### 🌐 기타 기능

- **다국어 지원**: 201개 언어 및 방언, 중국어 능력 특별 최적화
- **범용 프로그래밍**: 풀스택 개발, 코드 디버깅, 아키텍처 설계, Python/JS/TS/Go/Rust 지원
- **글쓰기**: 리서치 리포트, 분석 기사, 기술 문서, 창의적 콘텐츠 등 다양한 장르의 고품질 작성
- **시각 이해**: 멀티모달 비전, 로컬 스크린샷을 통한 이미지 내용 이해 지원
- **다중 프레임워크 지원**: llama.cpp / Ollama / LM Studio / Jan
- **다중 Agent 지원**: OpenClaw / Hermes / Cursor / Claude Code / Codex 등, 네이티브 도구 호출 및 다중 턴 작업 오케스트레이션

---

## 3. 버전 업그레이드 안내

이번 버전 업그레이드는 moziAI 자체 개발의 동적 7차원 사고 + LOOP 반복 추론 모드를 강화하여 작업 복잡도를 더욱 지능적으로 인식하고, 복잡한 작업의 완료율을 높이며, '먼저 생각한 후 실행하는' 능력을 향상시켰습니다.

moziAI는 활발한 버전 업그레이드와 반복 업데이트 주기를 유지하여 미래 인공지능 발전에 뒤처지지 않도록 하며, 자체 기술을 통해 로컬 AI 모델의 경량화 배포를 지속적으로 실현하여 성능을 점점 더 강화할 것입니다.

---

## 4. 핵심 역량

| 역량 영역 | 설명 |
| --- | --- |
| 시장 분석 | 거시/미시 경제 해석, A주/홍콩 주식/미국 주식/상품/암호화폐 시세 및 논리 정리 |
| 재무·리서치 리포트 | 재무제표 핵심 지표 해석, 리서치 리포트 요약 추출, 밸류에이션 및 수익 예측 보조 |
| 리스크 관리·컴플라이언스 | 상품 리스크 평가, 투자 조언 컴플라이언스 경고, 금융 규제 정책 해석 |
| 퀀트·전략 | 퀀트 전략 아이디어 설계, 피라미드(Pyramid/PEL) 퀀트, 백테스트 로직, 팩터 구축 및 도구 호출 |
| 도구 호출 | 실시간 시세, 데이터베이스, 리서치 리포트 검색 등 금융 데이터 소스 연동 가능 |

---

## 5. 기술 사양

| 항목 | 사양 |
| --- | --- |
| 베이스 모델 | Qwen3.8-27B(Dense 아키텍처, 하이브리드 어텐션 16 full + 48 linear, MIT 라이선스) |
| 파라미터 규모 | 270억(27B) Dense 아키텍처 |
| 양자화 방식 | 자체 개발 MoziSmartBit 스마트 양자화 + GGUF 표준 형식 |
| 컨텍스트 길이 | 128K(262,144 tokens) |
| 모델 크기 | ~13.7 GB |
| 최소 VRAM | **16GB+** 배포 가능(CPU 오프로드); **20GB+** 원활한 긴 컨텍스트; **24GB+** 전체 128K + 비전 |
| 추론 프레임워크 | llama.cpp / Ollama / LM Studio / Jan |
| 추론 속도 | MTP 추측 디코딩 기준: R9700 70+ tok/s, MAX+395 내장 GPU 50+ tok/s, GPU 35+ tok/s |
| 개발 팀 | 천위모(陈雨墨) 팀 |

---

## 6. ⚡ 빠른 시작（3개 파일 = 최고 추론 능력 100% 활성화）

> ⚠️ **핵심 안내**: MoziAI의 최고 추론 능력을 사용하려면 **파일 3개를 동시에 다운로드**해야 합니다 — 메인 모델, 비전 프로젝터, 채팅 템플릿. 하나라도 빠지면 해당 기능이 손실됩니다.

### 6.1 모델 파일 다운로드

HuggingFace / ModelScope에서 **V3.8 디렉터리의 모든 파일**을 로컬 동일 디렉터리에 다운로드합니다:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← 主模型（必选，13.7 GB）
└── chat-template-moziai-27B-V3.8.jinja         ← 聊天模板（必选，含七维思考+Loop指令）

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf            ← 视觉投影（必选，927 MB）
```

| 파일 | 크기 | 필수 여부 | 역할 |
| --- | --- | --- | --- |
| 메인 모델 `.gguf` | ~13.7 GB | **필수** | 모델 가중치, 핵심 추론 능력 |
| 비전 프로젝터 `mmproj` | ~927 MB | **필수** | 멀티모달 시각 이해, 로드하지 않으면 이미지 기능 상실 |
| 채팅 템플릿 `.jinja` | 아주 작음 | **필수** | MoziAI 정체성 + 7차원 사고 + LOOP 메커니즘 지시 주입 |

### 6.2 실행 및 사용

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

브라우저에서 `http://localhost:8080`을 열면 대화를 시작할 수 있습니다. 전체 권장 매개변수는 9절을 참조하세요.

---

## 7. 모델 다운로드

| 플랫폼 | 주소 |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP/tree/main) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP/tree/master) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP/tree/master) |

> 💡 **LM Studio 사용자**: [LM Studio](https://lmstudio.ai)에서 `moziAI`를 검색하여 원클릭으로 다운로드할 수 있으며, 파일을 수동으로 다운로드할 필요가 없습니다.

---

## 8. 시작 명령

### 최소 실행（3종 세트 포함）

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### 전체 권장 실행

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

> 💡 MTP 끄기: `--spec-type draft-mtp` 및 관련 매개변수를 제거하면 속도가 약 30-50% 낮아지고 VRAM 사용량이 줄어듭니다.

---

## 9. 권장 추론 매개변수

llama.cpp 공식 권장 매개변수와 로컬 실측 최적화를 기반으로 합니다(AMD Radeon AI PRO R9700 32GB):

| 매개변수 | 일반 채팅 | 코딩/Agent | 설명 |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | 창의성과 정확성의 균형 |
| top\_p | 0.95 | 0.95 | 핵 샘플링 임계값 |
| top\_k | 20 | 20 | 절단 샘플링 |
| repeat\_penalty | 1.05 | 1.05 | 반복 페널티 |
| context\_length | 262144 | 262144 | 128K 긴 컨텍스트 |
| reasoning | auto | auto | 추론 체인(사고 체인) 활성화 |
| reasoning\_budget | 400 | 400 | 추론 예산 토큰 |
| reasoning\_format | deepseek-legacy | deepseek-legacy | 추론을 별도 필드로 출력 |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP 추측 디코딩(11절 참조)** |

> 💡 **사고 모드**: `--reasoning auto`로 활성화하면 모델이 답변을 출력하기 전에 내부 추론을 먼저 수행합니다. `reasoning_budget`은 최대 사고 토큰 수를 제어합니다(권장 400, 100-1000 조정 가능).

---

## 10. 양자화 형식 비교

| 형식 | 크기 | 정확도 | 설명 |
| --- | --- | --- | --- |
| FP16 원본 | ~54 GB | 100% | 무손실, 전문가용 그래픽 카드 필요 |
| **MoziSmartBit(본 모델)** | **~13.7 GB** | **~99%** | **자체 개발 스마트 양자화, 최고 정확도·최소 크기** |
| Q4_K_M | ~17 GB | ~98% | GGUF 표준 4bit |
| Q5_K_M | ~20 GB | ~99% | 더 높은 정확도 |
| Q6_K | ~23 GB | ~99.5% | 무손실에 근접 |
| Q8_0 | ~31 GB | ~100% | 무손실 |

> MoziSmartBit은 약 99%의 정확도를 유지하면서 27B Dense 모델을 13.7 GB(압축비 3.9x)로 압축하며, Q4_K_M보다 약 20% 작아 소비자용 그래픽 카드의 로컬 배포에 더 적합합니다.

---

## 11. MTP 추측 디코딩（중요한 가속 기능）

본 모델에는 MTP(Multi-Token Prediction) 추측 디코딩 레이어가 내장되어 있어, 활성화하면 추론 속도가 **1.5-2배** 빨라집니다. 이는 Qwen3.8 아키텍처의 네이티브 기능으로, MoziAI는 완전한 MTP 가중치를 유지하고 있습니다.

**원리**: 모델 아키텍처에 경량 예측 헤드(Draft Model)를 추가로 학습시켜, 메인 모델이 검증하기 전에 후속 토큰을 미리 추측함으로써 forward 횟수를 줄이고 추론 지연 시간을 낮춥니다. 잘못된 추측은 메인 모델이 수정하므로 출력 품질에는 부정적인 영향이 없습니다.

### 활성화 매개변수

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| 매개변수 | 권장값 | 설명 |
| --- | --- | --- |
| --spec-type | draft-mtp | MTP 추측 디코딩 활성화 |
| --spec-draft-n-max | 2 | 매번 최대 2개 토큰 추측(권장값, 수용률 약 80%) |
| --spec-draft-p-min | 0.75 | 최소 수용 확률 임계값(0.0-1.0, 클수록 보수적) |

### 매개변수 조정 권장사항

| n-max | 수용률 | 적용 시나리오 |
| --- | --- | --- |
| 1 | ~90% | 가장 보수적, 속도 향상 최소 |
| **2** | **~80%** | **권장: 속도와 정확도의 균형** |
| 3 | ~71% | 일반 시나리오, 속도 향상이 뚜렷함 |
| 4-5 | ~60-65% | 창의적 글쓰기, 코드 생성 |
| 6 | ~50-55% | 순수 텍스트 긴 출력(p-min 조정 필요) |

---

## 12. VRAM 구성 권장

| VRAM | 권장 구성 | 설명 |
| --- | --- | --- |
| 16 GB | 컨텍스트를 64K로 축소, CPU 오프로드 필요 | 입문급, 예: RTX 4060 Ti |
| **20 GB** | **128K 풀 구성, q4_0 KV 캐시** | **권장 구성**, 예: RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K 풀 구성, VRAM 여유 충분 | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K 풀 구성, 최강 구성 | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB 내장 GPU | 128K 풀 구성 | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 컨텍스트가 길수록 VRAM 사용량이 늘어납니다. OOM 발생 시 `-c` 매개변수를 점진적으로 낮추세요. `--fit on`을 사용하면 llama.cpp가 VRAM에 맞게 레이어 수를 자동으로 조정합니다. NVIDIA / AMD / Intel 전 브랜드 그래픽 카드를 지원합니다.

---

## 13. 배포 방법

### Ollama 배포

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

LM Studio / Jan에서 `moziAI`를 검색하고 Q4\_K\_M 양자화 버전을 선택하여 다운로드하면 됩니다.

> 💡 Ollama의 mmproj 및 chat\_template 지원이 제한적이므로, 완전한 기능을 위해서는 llama.cpp 사용을 권장합니다.

---

## 14. 벤치마크 평가

MoziAI-27B-3.8은 Qwen3.8-27B 베이스 모델을 미세 조정한 모델로, 금융 수직 분야를 핵심 최적화 방향으로 삼고 있습니다.

### 코딩 역량

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Agent 역량

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### 일반 역량

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### 멀티모달 역량

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> 경쟁 모델 데이터는 공식 공개 평가 결과입니다. MoziAI는 금융 수직 분야(재무제표 해석, 퀀트 전략, 리스크 관리·컴플라이언스, Agent 도구 호출 등)에서 범용 모델보다 현저히 우수한 성능을 보여줍니다.

---

## 15. 라이선스

본 모델은 **커스텀 제한적 라이선스**를 사용합니다:

- ✅ **허용** — 무료 상업 사용, 복제 및 배포
- ❌ **금지** — 2차 개발, 재판매, 재라이선스
- 📋 **요구사항** — 원본 저작권 표시 유지, 출처 표기: moziAI-27B

본 모델은 '있는 그대로(as-is)' 제공되며 어떠한 형태의 보증도 제공되지 않습니다. 모델 출력은 참고용일 뿐이며 투자 조언을 구성하지 않습니다. 사용자는 사용에 따른 위험을 스스로 부담해야 합니다.

자세한 약관은 [LICENSE](LICENSE) 파일을 참조하세요.

---

## 16. 연락처

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
