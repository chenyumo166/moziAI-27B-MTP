---
language:
- en
- ko
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

# MoziAI-27B-3.8 - 무료 로컬 배포 가능한 소형 고성능 멀티모달 AI

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | 한국어 | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md)

## 모델 개요

MoziAI-27B-3.8은 중국 금융 인플루언서 천위모 팀이 개발한 로컬 오픈소스 금융 AI 멀티모달 LLM입니다. 오픈소스 베이스 모델 Qwen3.8-27B (Dense 27B 아키텍처, MIT 라이선스)를 기반으로, 천위모 팀의 독자 개발 기술을 통합: (금융 데이터 + 금융 영역 능력 + 학습 방법 + 7차원 사고 프레임워크 + 에이전트 LOOP 메커니즘 + 하이브리드 양자화 알고리즘 MoziSmartBit).

독자 개발한 MoziSmartBit 지능형 양자화 기술로 270억 파라미터 Dense 모델을 약 12.79 GB로 압축. 일반 Q4_K_M 양자화(~17GB) 대비 3.3GB(약 20%) 작아지며, 정밀도와 크기의 최적 균형을 달성. FP16의 **약 99% 정밀도 품질**을 유지합니다.

금융 수직 영역 강화, 금융 Q&A, 양자 프로그래밍, 도구 호출, 7차원 사고 능력, LOOP 메커니즘, 다양한 에이전트 플랫폼 호환. OpenClaw/Hermes로 128K 컨텍스트 작업 실행 가능. 로컬 소비자 GPU 배포로 클라우드 토큰 비용 대폭 절감, **7x24 시간 토큰 프리** 달성.

llama.cpp, Ollama, LM Studio 등 메인스트림 추론 프레임워크 지원.

**출시일: 2026-08-30** | **버전: V3.8**

## 모델 특징

- **금융 수직 심화**: 금융 Q&A, 양자 프로그래밍, 도구 호출 강화
- **MoziSmartBit 지능형 양자화**: 독자 양자화 기술, 약 **12.79 GB** 압축, **약 99%** 정밀도 유지
- **소비자 GPU 배포**: 16GB VRAM 이상으로 로컬 배포 가능, 20GB 이상에서 완전한 128K 긴 컨텍스트 추론
- **MTP 추측 디코딩**: 멀티 토큰 예측 레이어 내장, 추론 속도 1.5-2배 향상
- **다국어 지원**: 201개 언어·방언 지원
- **범용 프로그래밍**: Python/JS/TS/Go/Rust 등
- **시각 이해**: 멀티모달 지원
- **추론 논리 강화**: 체인 오브 사고 훈련
- **멀티 프레임워크**: llama.cpp, Ollama, LM Studio, Jan
- **멀티 에이전트**: OpenClaw, Hermes, Cursor 등 AI IDE 지원

## 핵심 역량

| 역량 영역 | 설명 |
|---------|------|
| 시장 분석 | 거시/미시 경제 해석, A/HK/US 주식/원자재/암호화폐 |
| 재무·보고서 | 재무 지표 해석, 리서치 요약, 밸류에이션 지원 |
| 리스크·컴플라이언스 | 리스크 평가, 투자 조언, 규제 정책 해석 |
| 양자·전략 | 양자 전략 설계, 피라미드(PEL) 양자화, 백테스팅 |
| 도구 호출 | 실시간 시세, 데이터베이스, 리서치 검색 등 |

## 기술 사양

| 항목 | 사양 |
|------|------|
| 베이스 모델 | Qwen3.8-27B (Dense, 하이브리드 어텐션, MIT) |
| 파라미터 | 270억 Dense |
| 양자화 | MoziSmartBit 지능형 양자화 + GGUF 표준 |
| 컨텍스트 길이 | 128K (262,144 토큰) |
| 모델 크기 | ~12.79 GB |
| 최소 VRAM | **16GB+** 배포 가능 (CPU 오프로드 필요)；**20GB+** 긴 컨텍스트 지원；**24GB+** 완전한 128K + 비전 |
| 추론 속도 | MTP 시: R9700 70+ tok/s, MAX+395 CPU 50+ tok/s, MAX+395 GPU 35+ tok/s |

## 양자화 포맷

| 포맷 | 크기 | 정밀도 | 설명 |
|------|------|--------|------|
| FP16 (원본) | ~54 GB | 100% | 원본 16비트 정밀도 |
| **MoziSmartBit** | **~12.79 GB** | **약 99%** | **독자 지능형 양자화** |
| Q4_K_M | ~17 GB | ~98% | GGUF 표준 4bit |
| Q5_K_M | ~20 GB | ~99% | 더 높은 정밀도 |
| Q6_K | ~23 GB | ~99.5% | 거의 무손실 |
| Q8_0 | ~31 GB | ~100% | 무손실 |

## MTP 추측 디코딩

본 모델은 MTP 추측 디코딩 레이어를 내장하고 있어 활성화 시 추론 속도가 **1.5-2배** 향상됩니다.

```bash
--spec-type draft-mtp --spec-draft-n-max 2 --spec-draft-p-min 0.75
```

| 파라미터 | 권장값 | 설명 |
|----------|--------|------|
| --spec-type | draft-mtp | MTP 추측 디코딩 활성화 |
| --spec-draft-n-max | 2 | 스텝당 최대 2토큰 추측 (~80% 수용율) |
| --spec-draft-p-min | 0.75 | 최소 수용 확률 |

## llama.cpp 실행 명령어

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

> 💡 **MTP 비활성화**: `--spec-type draft-mtp`, `--spec-draft-n-max 2`, `--spec-draft-p-min 0.75` 세 줄 삭제. 속도 30-50% 감소, VRAM 사용량 감소.

## VRAM 구성 권장

| VRAM | 컨텍스트 | KV캐시 | 비전 | 설명 |
|------|---------|--------|------|------|
| 20 GB | 128K | q4_0 | 지원 | 권장 구성 |
| 24 GB | 128K | q4_0 | 완전 지원 | VRAM 여유 |
| 32 GB+ | 128K | q4_0 | 완전 지원 | 최강 구성 |

## 벤치마크

### 코딩

| 벤치마크 | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 |
| QwenSWEBench | **79.0** | 49.3 | 59.2 |

### 에이전트

| 벤치마크 | moziAI-27B-3.8 | Qwen3.6-27B | Qwen3.7-Plus |
|---|---|---|---|
| CoWorkBench | **70.7** | 61.0 | 65.1 |
| JobBench | **33.4** | 21.8 | 27.6 |
| WebArena-Verified | **64.8** | 48.8 | 55.3 |

## 모델 다운로드

| 플랫폼 | 링크 |
|---|---|
| HuggingFace | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://huggingface.co/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| ModelScope | [chenyumo/moziAI-27B-3.8-MTP-Q4_K_M](https://modelscope.cn/models/chenyumo/moziAI-27B-3.8-MTP-Q4_K_M) |
| GitHub | [chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M](https://github.com/chenyumo166/moziAI-27B-3.8-MTP-Q4_K_M) |

## 빠른 시작

### 1. 다운로드

```
V3.8/
├── moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf      # 메인 모델
├── moziAI-27B-3.8-mmproj-F16.gguf              # 비전 프로젝션
└── chat-template-moziai-27B-v38.jinja           # 채팅 템플릿
```

### 2. 실행

```bash
llama-server \
  -m V3.8/moziAI-27B-3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-v38.jinja \
  -c 131072 -ngl 99
```

### 3. 채팅 시작

브라우저에서 `http://localhost:8080` 열기

## 라이선스

커스텀 제한 라이선스: 무료 상업 사용 가능 ✅ | 2차 개발 불가 ❌ | 재판매 불가 ❌

## 면책 조항

본 모델은 "있는 그대로" 제공되며, 어떤 보증도 하지 않습니다.

## 연락처

- HuggingFace: [@chenyumo](https://huggingface.co/chenyumo)
- GitHub: [@chenyumo166](https://github.com/chenyumo166)
- E-mail: 263515@qq.com

Copyright (c) 2026 천위모/ chenyumo166. All rights reserved.
