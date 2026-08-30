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

# MoziAI-27B-3.8 - 무료 로컬 배포 가능한 소형 고성능 멀티모달 AI 모델

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | 한국어 | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## 모델 개요

MoziAI-27B-3.8은 중국 금융 인플루언서 첸위모(Chen Yumo) 팀이 개발한 로컬 오픈소스 멀티모달 AI 대규모 모델입니다(금융 분야 강화, 비전 지원, 도구 호출, 컨슈머 GPU 로컬 배포 지원). moziAI-27B-3.8은 오픈소스 베이스 모델 Qwen3.8-27B(Dense 27B 아키텍처, MIT 라이선스)를 기반으로, 첸위모 팀의 독자 개발 기술(금융 데이터 + 금융 도메인 능력 + 학습 방법 + 동적 7차원 사고 프레임워크 + 에이전트 LOOP 반성 반복 메커니즘 + 하이브리드 양자화 알고리즘 MoziSmartBit)을 결합하여 개발되었습니다. 개인과 기업의 로컬 배포 장벽을 낮추고, 무료 상용 사용을 허가합니다. 로컬 컨슈머 GPU에서 배포 가능하여 클라우드 토큰 비용을 대폭 절감하고, 7×24시간 토큰 자유를 실현하면서 로컬 데이터 프라이버시와 보안을 보장합니다.

**동적 7차원 사고 프레임워크 + 에이전트 LOOP 반복 메커니즘**: MoziAI가 독자 개발한 핵심 추론 모드입니다. 작업 복잡도를 지능적으로 판단하여, 간단한 작업은 2차원 사고로 빠르게 답변하고, 중간 복잡도 작업은 5차원 사고를 활성화하며, 고도로 복잡한 작업은 완전한 7차원 사고 + LOOP 반성 반복 메커니즘을 활성화합니다. 자신보다 몇십 배 큰 트릴리언 파라미터 모델의 복잡한 작업 해결 능력에 도전하면서도, 간단한 작업의 가벼운 응답성을 잃지 않습니다. 로컬 모델도 숙련된 인간 전문가의 "먼저 생각하고 행동하는" 능력을 기를 수 있게 하며, 동일 크기의 모델과 비교할 때 이 독자적 핵심 추론 프레임워크는 매우 독창적입니다.

**독자 개발한 MoziSmartBit 지능 양자화 기술을 통해**, 270억 파라미터의 Dense 모델이 약 12.79 GB로 압축되어, 기존 Q4_K_M 양자화 모델(약 17 GB)보다 3.3 GB(약 20%) 작습니다. 정밀도와 크기 간 최적의 균형을 실현하며, FP16의 약 99% 정밀도 품질을 제공합니다.

이 모델은 AI 대규모 모델의 일반적 능력을 유지하면서 다음과 같은 부분이 강화되었습니다: 금융 수직 도메인 애플리케이션, 금융 Q&A, 정량적 프로그래밍, 도구 호출 및 일반 프로그래밍, 다양한 에이전트 플랫폼과의 호환성.

모델 개발자 첸위모는 이 모델을 로컬 금융 데이터 분석, 정량 전략 개발, 시장 조사, 각종 기사 작성, 전체 프로젝트 개발 추진, 일반 프로그래밍, OpenClaw/Hermes의 256K 긴 컨텍스트 복잡한 작업 실행에 자주 사용합니다.

llama.cpp, Ollama, LM Studio 등 주요 추론 프레임워크에서 무료 로컬 배포를 지원합니다.

**출시일: 2026-08-30** | **버전: V3.8**

## 모델 특징

- **🧠 동적 7차원 사고 프레임워크**: MoziAI가 독자 개발한 핵심 추론 프레임워크입니다. 어떤 작업에 직면해도 모델은 먼저 **moziAI-Think** 태그를 출력하고, 작업 복잡도에 따라 구조화된 사고를 동적으로 전개합니다 — 간단한 질문의 "작업 이해 + 리소스 요구사항" 2차원 빠른 응답(Level 0)에서, 분석 진단의 5차원 평가(Level 1), 복잡한 개발/전략 설계의 전체 7차원 심층 추론(Level 2)까지: ①작업 이해 ②복잡도 평가 ③의존성 분석 ④위험 평가 ⑤리소스 요구사항 ⑥인수 기준 ⑦실행 전략.
- **🧠 에이전트 LOOP 반복 메커니즘**: 복잡한 작업에 대해 MoziAI는 자동으로 **moziAI-Loop** 반복 모드로 진입합니다: 1라운드 실행 + 평가 → 2라운드 조정 + 검증. 출력이 자기 검증된 후 최종 답변을 제공하며, 한 번에 생성하지 않습니다. 이는 모델이 단순히 "질문에 답하는" 것이 아니라, 숙련된 엔지니어처럼 문제 분석 → 해결책 평가 → 실행 → 성찰 → 최적화를 수행한다는 것을 의미하여, 복잡한 작업의 정확성과 실행 가능성을 크게 향상시킵니다. 간단한 질문과 작업은 Loop 반복 메커니즘을 자동으로 비활성화합니다.
- **🧠 MoziSmartBit 지능 양자화**: MoziAI가 독자 개발한 계층별 지능 양자화. 정밀도와 크기 간 최적의 균형을 실현하여 약 12.79 GB로 압축하고, FP16 약 99% 정밀도를 유지합니다.
- **🧠 금융 수직 도메인 집중**: 금융 Q&A, 정량적 프로그래밍, 도구 호출에 대한 심층 최적화. 금융 분야는 모델 환각에 대한 관용도가 극히 낮으며, 일반 모델과 비교하여 MoziAI의 수직 도메인 능력 심층 강화를 입증합니다.
- **다국어 지원**: 201개 언어와 방언을 지원하며, 중국어 능력이 특히 최적화되어 있습니다. 영어, 일본어, 한국어, 독일어, 프랑스어, 스페인어, 포르투갈어 등 주요 언어를 모두 포괄합니다.
- **일반 프로그래밍 능력**: 풀스택 개발, 코드 디버깅, 아키텍처 설계, 스크립트 작성을 지원하며, Python/JS/TS/Go/Rust 등 주요 언어를 포괄합니다.
- **기사 작성 능력**: 보고서, 분석 기사, 기술 문서, 창작 콘텐츠 등 다양한 장르의 고품질 작성을 지원합니다.
- **비전 이해**: 멀티모달 비전을 지원하며, 스크린샷을 채팅 창에 붙여넣으면 모델이 이미지 내 정보를 이해할 수 있습니다.
- **멀티 프레임워크 지원**: llama.cpp, Ollama, LM Studio, Jan 등 주요 추론 프레임워크와 호환됩니다.
- **멀티 에이전트 플랫폼 지원**: OpenClaw, Hermes, OpenCode, Cursor, Windsurf, Claude Code, Codex 등 국내외 주요 AI IDE 및 에이전트 프레임워크와 깊은 호환성을 가지며, 도구 호출과 멀티턴 작업 오케스트레이션을 네이티브로 지원합니다.

## 핵심 역량

| 역량 영역 | 설명 |
| ----- | ------------------------------------------ |
| 시장 분석 | 거시/미시 경제 해석, A주/항주/미주/상품/암호화폐 시장 동향 및 논리 분석 |
| 재무 및 리포트 | 재무제표 핵심 지표 해석, 리포트 요약 추출, 밸류에이션 및 실적 전망 지원 |
| 리스크 관리 및 컴플라이언스 | 제품 리스크 평가, 투자 조언 컴플라이언스 주의, 금융 규제 정책 해석 |
| 정량적 및 전략 | 정량 전략 설계, 피라미드(Pyramid/PEL) 양자화, 백테스트 논리, 팩터 구축 및 도구 호출 |
| 도구 호출 | 실시간 시장 데이터, 데이터베이스, 리포트 검색 등 금융 데이터 소스에 접속 가능 |

## 기술 사양

| 항목 | 파라미터 |
| ------ | ---------------------------------------------------------------------------------- |
| 베이스 모델 | Qwen3.8-27B (Dense 아키텍처, 하이브리드 어텐션 16 full + 48 linear, MIT 라이선스) |
| 파라미터 규모 | 270억 (27B) Dense 아키텍처 |
| 양자화 방식 | 독자 개발 MoziSmartBit 지능 양자화 알고리즘 + GGUF 표준 포맷 |
| 컨텍스트 길이 | 256K (262,144 토큰) |
| 모델 크기 | ~12.79 GB |
| 최소 VRAM 요구사항 | **16GB+** 배포 가능 (CPU 오프로딩 필요, 예: RTX 4060 Ti 16G); **20GB+** 긴 컨텍스트 원활 실행 (예: RX 7900 XT 20G); **24GB+** 완전한 256K + 비전 지원 |
| 추론 프레임워크 | llama.cpp / Ollama / LM Studio / Jan |
| 추론 속도 | MTP 추측 디코딩 활성화 시: AMD R9700 GPU 70+ token/s, AMD MAX+395 내장 GPU 50+ token/s, AMD MAX+395 GPU 35+ token/s, 로컬 토큰 자유 출력 실현 |
| 개발팀 | 첸위모 팀 |

## 양자화 포맷 및 모델 크기

| 양자화 포맷 | 모델 크기 | 정밀도 유지 | 설명 |
| ---------------- | ------------- | --------- | ----------------- |
| FP16 (원본) | ~54 GB | 100% | 원본 16bit 정밀도 |
| **MoziSmartBit** | **~12.79 GB** | **~99%** | **본 모델은 독자 개발 지능 양자화 사용** |
| Q4_K_M | ~17 GB | ~98% | GGUF 표준 4bit |
| Q5_K_M | ~20 GB | ~99% | 더 높은 정밀도 |
| Q6_K | ~23 GB | ~99.5% | 거의 무손실 |
| Q8_0 | ~31 GB | ~100% | 무손실 |

> MoziAI V3.8은 MoziSmartBit 지능 양자화 방식을 채택하여, 약 99% 정밀도를 유지하면서 270억 파라미터 Dense 모델을 약 12.79 GB로 압축합니다. 압축비 4.0x로 추론 품질과 배포 장벽의 균형을 맞추며, 컨슈머 GPU 로컬 배포에 더 적합합니다.

## MoziSmartBit 지능 양자화 기술

기존 양자화 방식은 모든 레이어에 통일 정밀도를 적용하지만, 첸위모 팀의 독자 개발 **MoziSmartBit 지능 양자화**는 Dense 모델의 구조적 특성에 맞춘 지능적 차별화 양자화 전략을 채택하여 크기와 정밀도 간 최적의 균형을 달성합니다. 모델 품질은 Q4_K_M 포맷을 초과하며, 크기는 12.79 GB에 불과하고, 압축비 4.0x, 정밀도 유지율 약 99%입니다.

### 압축 효과

- **양자화 정밀도 손실 극히 작음**: 학습 이득 > 양자화 손실. 학습 후 MoziAI-27B의 금융 분야 텍스트 PPL이 학습 전 bf16 베이스보다 우수하며, 동종 AI 모델 대비 환각과 혼란을 감소시킵니다.
- **모델 크기 4.0배 압축**: FP16(~54 GB)에서 ~12.79 GB로 압축. Q4_K_M의 ~17 GB보다 대폭 작아 VRAM 및 저장소 장벽을 크게 낮춥니다.
- **컨슈머 GPU 배포 가능**: 하이엔드 GPU를 필요로 했던 27B Dense 대규모 모델이 이제 16 GB VRAM으로 로컬 배포 가능하며, 20 GB 이상 GPU에서는 완전한 256K 긴 컨텍스트 추론을 실현합니다.

### 비교 우위

**vs Q4_K_M (~17 GB)**: 약 20% 작음 (~12.79 GB), Q4_K_M보다 우수한 정밀도, 더 낮은 VRAM 장벽 — 16 GB GPU로 배포 가능, 20 GB 이상 GPU에서 256K 긴 컨텍스트 원활 실행.

**vs 원본 FP16 (~54 GB)**: 약 4.0배 압축비, 약 99% 정밀도 유지. 프로페셔널급 GPU에서 컨슈머 GPU로降低了, 로컬 256K 긴 컨텍스트 추론이 가능합니다.

## 권장 추론 파라미터

llama.cpp 공식 권장 파라미터와 로컬 벤치마크 최적화(AMD Radeon AI PRO R9700 32GB)를 기반으로 한 권장 파라미터입니다:

| 파라미터 | 일반 채팅 | 코딩/Agent | 설명 |
| --- | --- | --- | --- |
| temperature | 0.7 | 1.0 | 창의성과 정확성의 균형 |
| top\_p | 0.95 | 0.95 | 뉴클리어스 샘플링 임계값 |
| top\_k | 20 | 20 | 절단 샘플링 |
| repeat\_penalty | 1.05 | 1.05 | 반복 페널티 |
| presence\_penalty | 0 | 0 | 프레즌스 페널티 없음 |
| context\_length | 262144 | 262144 | 256K 긴 컨텍스트 |
| batch\_size | 2048 | 2048 | 배치 크기 |
| ubatch\_size | 512 | 512 | 마이크로배치 크기 |
| flash\_attention | auto | auto | 자동 Flash Attention |
| kv\_cache | q4\_0 | q4\_0 | KV 캐시 양자화 |
| poll | 0 | 0 | 유휴 시 GPU 폴링 비활성화, 절전 및 저지연 |
| reasoning | auto | auto | 추론 체인(사고 체인) 활성화 |
| reasoning\_budget | 400 | 400 | 추론 토큰 예산 |
| reasoning\_format | deepseek-legacy | deepseek-legacy | 추론 포맷 |
| samplers | top\_k;top\_p;temperature;typ\_p | top\_k;top\_p;temperature;typ\_p | 샘플러 순서 |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP 추측 디코딩(하단 MTP 섹션 참조)** |

> 💡 **사고 모드 설명**: 본 모델에는 Qwen3.8 Thinking(사고 체인) 기능이 내장되어 있습니다. `--reasoning auto`로 활성화하면, 모델은 답변을 출력하기 전에 내부 추론을 수행합니다. `reasoning_budget`은 최대 사고 토큰 수를 제어합니다(400이 권장 값, 작업 복잡도에 따라 100-1000으로 조정 가능). `reasoning-format deepseek-legacy`는 사고 과정을 별도 필드로 출력하여 메인 출력 콘텐츠를 오염시키지 않습니다.

## MTP 추측 디코딩 (중요 가속 기능)

본 모델에는 MTP(Multi-Token Prediction) 추측 디코딩 레이어가 내장되어 있습니다. 활성화 시 추론 속도가 **1.5-2배** 향상됩니다. 이는 Qwen3.8 아키텍처의 네이티브 기능이며, MoziAI는 완전한 MTP 가중치를 보유하고 있습니다.

### MTP 원리

MTP는 모델 아키텍처에 경량 예측 헤드(Draft Model)를 추가 학습하여, 메인 모델 검증 전에 후속 토큰을 미리 추측합니다. 이를 통해 메인 모델의 forward 횟수를 줄이고 추론 지연 시간을 크게 낮춥니다.

### llama.cpp MTP 활성화 파라미터

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| 파라미터 | 권장 값 | 설명 |
| --- | --- | --- |
| --spec-type | draft-mtp | MTP 추측 디코딩 활성화 |
| --spec-draft-n-max | 2 | 스텝당 최대 추측 토큰 수 (권장 값, 수용률 약 80%) |
| --spec-draft-p-min | 0.75 | 최소 수용 확률 임계값 (0.0-1.0, 높을수록 보수적) |

### MTP 파라미터 조정 가이드

| spec-draft-n-max | 수용률 | 적용 시나리오 |
| --- | --- | --- |
| 1 | ~90% | 가장 보수적, 속도 향상 최소이지만 가장 안전 |
| **2** | **~80%** | **권장: 속도와 정확성의 균형** |
| 3 | ~71% | 범용 시나리오, 눈에 띄는 속도 향상 |
| 4-5 | ~60-65% | 창작 글쓰기, 코드 생성 |
| 6 | ~50-55% | 순수 텍스트 긴 출력 (p-min 조정 필요) |

> ⚠️ **주의**: MTP 추측 디코딩은 출력 품질에 부정적 영향이 없습니다(잘못된 추측은 메인 모델에 의해 수정됨). 추론 속도에만 영향을 미칩니다. `spec-draft-n-max`는 2에서 시작하여 실제 수용률에 따라 조정하는 것을 권장합니다.

## llama.cpp 시작 명령어

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

> 💡 **MTP 비활성화**: MTP 추측 디코딩을 비활성화하려면, 시작 명령어에서 `--spec-type draft-mtp`, `--spec-draft-n-max 2`, `--spec-draft-p-min 0.75` 세 줄을 삭제하면 됩니다. 비활성화 시 추론 속도는 약 30-50% 감소하지만 VRAM 사용량이 줄어듭니다.

## VRAM별 구성 권장

사용자 GPU 구성의 차이가 크므로, 다음은 다양한 VRAM 레벨별 권장 파라미터입니다:

| VRAM | 권장 컨텍스트 | KV 캐시 | 비전 지원 | 설명 |
| --- | --- | --- | --- | --- |
| 20 GB | 256K 풀 | q4\_0 | 완전 지원 | 비전+256K 긴 컨텍스트, 권장 구성 (모델+KV 약 16GB 필요, VRAM 여유 ~4GB) |
| 24 GB | 256K 풀 | q4\_0 | 완전 지원 | 비전+256K 긴 컨텍스트, 충분한 VRAM 여유 |
| 32 GB+ | 256K 풀 | q4\_0 | 완전 지원 | 비전+256K 긴 컨텍스트, 충분한 VRAM 여유, 최강 구성 |

**NVIDIA GPU 참고표**

| VRAM | GPU 모델 |
| --- | --- |
| 16 GB | RTX 4060 Ti (CPU 오프로딩 필요) |
| 20 GB | RTX 5070 Ti |
| 24 GB | RTX 4090 / RTX 3090 Ti |
| 32 GB | RTX 5090 |

**AMD GPU 참고표**

| VRAM | GPU 모델 |
| --- | --- |
| 20 GB | RX 7900 XT |
| 24 GB | RX 7900 XTX |
| 32 GB | Radeon AI PRO R9700 |

**Intel GPU 참고표**

| VRAM | GPU 모델 |
| --- | --- |
| 24 GB | Arc Pro B60 |
| 16 GB | Arc Pro B50 (CPU 오프로딩 필요) |

**CPU 공유 메모리 내장 GPU 장치 참고표**

| VRAM | 프로세서 모델 |
| --- | --- |
| 128 GB | AMD Ryzen AI Max+ 395 (Radeon 8060S 내장 GPU) |
| 128 GB | NVIDIA RTX Spark (Blackwell RTX GPU) |

> 💡 **팁**: VRAM이 위의 요구사항을 충족하면 브랜드와 모델에 관계없이 사용 가능합니다. NVIDIA / AMD / Intel 각 브랜드 범용 GPU와 128GB 통합 메모리 내장 GPU CPU도 지원합니다.
> 💡 **팁**: 컨텍스트가 길수록 VRAM 사용량이 증가합니다. VRAM 부족(OOM)이 발생하면 `-c` 파라미터 값을 단계적으로 낮추세요. `--fit on` 파라미터를 사용하면 llama.cpp가 사용 가능한 VRAM에 맞춰 레이어 수를 자동 조정합니다.

## Ollama 배포

```bash
# Modelfile 생성
FROM ./moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf

PARAMETER temperature 0.6
PARAMETER top_p 0.95
PARAMETER top_k 20
PARAMETER num_ctx 262144
PARAMETER num_gpu 99

# 비전 투영 파일 로드 (선택사항, 비전 기능 활성화)
PARAMETER mmproj ./moziAI-27B-3.8-mmproj-F16.gguf

# 채팅 템플릿 로드 (권장)
PARAMETER chat_template_file ./chat-template-moziai-27B-v38.jinja

# 빌드 및 실행
ollama create moziAI-27B -f Modelfile
ollama run moziAI-27B
```

> 💡 Ollama에서 `mmproj`와 `chat_template_file` 파라미터는 구체적인 버전 지원 여부를 확인해야 합니다. 완전한 기능 지원을 위해 llama.cpp 배포를 우선 사용하는 것을 권장합니다.

## LM Studio / Jan 배포

LM Studio / Jan에서 `moziAI`를 직접 검색하고 Q4_K_M 양자화 버전을 선택하여 다운로드하세요.

## 벤치마크 평가

MoziAI-27B-3.8은 Qwen3.8-27B (Dense 27B) 베이스 모델을 파인튜닝한 것입니다. 다음은 일반 능력 벤치마크 점수입니다(MoziAI의 핵심 최적화 방향은 금융 수직 도메인이며, 일반 능력 벤치마크 점수는 베이스 Qwen3.8-27B와 일치합니다):

### 코딩 능력

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| Terminal Bench 2.1 (Terminus) | 73.0 | 63.4 | 64.0 | 51.7 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 51.2 | 53.4 |
| NL2Repo-Bench | 42.3 | 36.2 | 41.1 | -- | 47.6 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | -- | 63.8 |

### 에이전트 능력

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 | -- | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- | -- |
| Agents' Last Exam (Score) | **42.9** | 27.3 | 33.6 | -- | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | -- | 62.0 |

### 일반 능력

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| IFBench | **79.5** | 69.1 | 79.1 | 77.0 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | 83.5 | **91.3** |

### 멀티모달 능력

| Benchmark | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus | Muse Glimmer-30B | Opus4.6 Max |
|---|---|---|---|---|---|
| MathVision (With CI) | **94.6** | 85.1 | 90.3 | -- | 65.5 |
| BabyVision (With CI) | **85.6** | 28.9 | 70.4 | -- | 12.6 |
| CharXiv RQ (With CI) | **90.2** | 78.4 | 85.8 | -- | 66.0 |
| OmniDocBench 1.5 | 91.1 | 89.4 | **91.4** | 75.8 | 86.6 |
| RealWorldQA | 85.9 | 84.1 | **86.9** | -- | 73.9 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- | -- |

> MoziAI-27B-3.8의 일반 능력 벤치마크 점수는 베이스 모델 Qwen3.8-27B와 일치합니다. 금융 수직 도메인은 MoziAI의 핵심 최적화 방향이며, 재무제표 해석, 정량 전략, 리스크 관리 컴플라이언스, 에이전트 관리 도구 호출 등의 시나리오에서 일반 모델보다 현저히 뛰어난 성능을 보여줍니다. Qwen3.6/Qwen3.7/Muse-Glimmer/Opus4.6 데이터는 공식 공개 벤치마크 결과입니다.

## 모델 다운로드

모델 파일이 크기 때문에(~12.79 GB), 모델 가중치는 여러 커뮤니티 플랫폼에서 호스팅됩니다:

| 플랫폼 | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| ModelScope (魔搭) | [chenyumo/moziAI-27B-3.8-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-Q4_K_M) |

> 💡 **LM Studio 사용자**: [LM Studio](https://lmstudio.ai)에서 `moziAI`를 직접 검색하고 원클릭으로 다운로드할 수 있으며, 수동 파일 다운로드가 필요하지 않습니다.

> 💡 **다운로드 팁**: 위의 링크를 클릭하여 HuggingFace 리포지토리에 들어가 "Files and versions" 탭에서 V3.8 디렉토리의 모든 파일(메인 모델, 비전 투영, 채팅 템플릿)을 다운로드하세요. 세 파일을 동일한 디렉토리에 배치해야 합니다.

⚠️ **중요: 비전 기능에는 추가 mmproj 파일 로드가 필요합니다**

본 모델은 멀티모달 비전을 지원합니다. 비전 투영 파일(mmproj)은 버전 디렉토리에 포함되어 있습니다.

- **비전 파일**: `moziAI-27B-3.8-mmproj-F16.gguf` (약 927 MB, BF16 정밀도)
- **배치 위치**: GGUF 모델 파일과 동일한 버전 디렉토리에 배치
- **로드 방법**: llama-server 시작 시 `--mmproj` 파라미터로 로드

> 비전 파일을 로드하지 않으면 이미지 이해 능력이 상실되며, 순수 텍스트 대화 능력만 유지됩니다.

## 빠른 시작

### 1. 모델 파일 다운로드

HuggingFace / ModelScope에서 V3.8 디렉토리의 모든 파일을 로컬로 다운로드:

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # 메인 모델 (필수)
├── moziAI-27B-3.8-mmproj-F16.gguf              # 비전 투영 (선택사항)
└── chat-template-moziai-27B-v38.jinja           # 채팅 템플릿 (권장)
```

### 2. 추론 서비스 시작

완전한 권장 구성 시작 명령어는 위의 [llama.cpp 시작 명령어](#llamacpp-시작-명령어) 섹션을 참조하세요.

최소 시작 (핵심 파라미터만):

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

> 비전 기능이 필요한 경우 `--mmproj V3.8/moziAI-27B-3.8-mmproj-F16.gguf`를 추가하세요.

### 3. 사용 시작

브라우저에서 `http://localhost:8080`을 열면 채팅을 시작할 수 있습니다.

### 디렉토리 구조

```
moziAI-27B/
├── README.md              # 본 파일 (중국어 설명서)
├── README.en.md           # 영어 설명서
├── LICENSE                # 라이선스
├── V3.8/                  # V3.8 버전
│   ├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf    # 메인 모델
│   ├── moziAI-27B-3.8-mmproj-F16.gguf            # 비전 투영
│   └── chat-template-moziai-27B-v38.jinja         # 채팅 템플릿
```

## SEO 키워드

금융 AI 대규모 모델, AI 대규모 모델, 로컬 오픈소스 모델, 엣지 모델, 정량적 프로그래밍, MoziSmartBit, 지능 양자화, GGUF 양자화, Dense 모델, 로컬 오픈소스 대규모 모델, 로컬 배포, 금융 AI, 도구 호출, Agent, llama.cpp, Ollama, GGUF, Q4\_K\_M, Qwen3.8-27B, 금융 수직 도메인, 오픈소스 모델, MTP 추측 디코딩, 256K 긴 컨텍스트, 멀티모달, 로컬 LLM, 엣지 AI, 셀프호스트 AI, speculative decoding, self-hosted AI, local LLM, edge AI, Chinese financial AI, Qwen3.8 fine-tune, tool-calling, vision model, open-source LLM, consumer GPU deployment, intelligent quantization

## 라이선스 (중요 사항)

본 모델은 **커스텀 제한 라이선스**에 따라 제공되며, 구체적 조건은 다음과 같습니다:

✅ **허용**
- 무료 상용 사용: 귀하의 상용 제품이나 서비스에 무료로 통합 가능
- 복사 및 배포: 그대로 복사, 다운로드, 분석 가능

❌ **금지**
- 2차 개발: 본 모델 또는 그 어떤 부분도 수정, 번역, 개조, 병합, 파인튜닝 금지
- 재판매: 본 모델을 단독으로 또는 제품의 일부로 판매 금지
- 재라이선스: 본 모델에 대한 어떤 종속 라이선스도 부여 금지

📋 **요구사항**
- 사용 시 원본 저작권 표시를 유지해야 합니다
- 출처 표시: moziAI-27B

자세한 라이선스 조건은 [LICENSE](LICENSE) 파일을 참조하세요.

## 면책 조항

본 모델은 "있는 그대로" 제공되며, 어떤 형태의 보증도 제공하지 않습니다. 모델 출력은 참고용일 뿐이며, 투자 조언을 구성하지 않습니다. 사용자는 본 모델 사용에 따른 모든 위험을自行承担합니다.

## 연락처

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陳雨墨/ chenyumo166. All rights reserved.
