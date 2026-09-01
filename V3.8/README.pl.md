---
language:
- pl
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

# MoziAI-27B-3.8 — Kompaktowy, ale potężny multimodalny model AI do darmowego wdrożenia lokalnego

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | Polski | [Español](README.es.md) | [Português](README.pt.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

**Data wydania: 2026-08-30** · **Wersja: V3.8**

---

## 📑 Spis treści

- [1. Przegląd modelu](#1-przegląd-modelu)
- [2. Kluczowe funkcje](#2-kluczowe-funkcje) — Dynamiczne myślenie siedmiowymiarowe / LOOP / MoziSmartBit / Fokus finansowy
- [3. Notatki o aktualizacji wersji](#3-notatki-o-aktualizacji-wersji)
- [4. Kluczowe możliwości](#4-kluczowe-możliwości)
- [5. Specyfikacja techniczna](#5-specyfikacja-techniczna)
- [6. ⚡ Szybki start](#6--szybki-start3-pliki--100-aktywacja-najlepszych-możliwości-wnioskowania) — **pobierz 3 pliki**
- [7. Pobieranie modelu](#7-pobieranie-modelu)
- [8. Polecenia uruchamiania](#8-polecenia-uruchamiania)
- [9. Zalecane parametry wnioskowania](#9-zalecane-parametry-wnioskowania)
- [10. Porównanie formatów kwantyzacji](#10-porównanie-formatów-kwantyzacji)
- [11. Dekodowanie spekulacyjne MTP](#11-dekodowanie-spekulacyjne-mtp-kluczowa-funkcja-przyspieszająca)
- [12. Zalecenia konfiguracji VRAM](#12-zalecenia-konfiguracji-vram)
- [13. Metody wdrożenia](#13-metody-wdrożenia)
- [14. Benchmarki](#14-benchmarki)
- [15. Licencja](#15-licencja)
- [16. Kontakt](#16-kontakt)

---

## 1. Przegląd modelu

MoziAI-27B-3.8 to lokalnie wdrażalny, otwartoźródłowy multimodalny model AI opracowany przez zespół Chen Yumo, czołowego chińskiego influencera finansowego. Zbudowany na otwartej bazie **Qwen3.8-27B** (architektura Dense 27B, licencja MIT), integruje własne dane finansowe zespołu + możliwości domeny finansowej + dynamiczny siedmiowymiarowy system myślenia + mechanizm iteracyjnej refleksji LOOP agenta + hybrydowy algorytm kwantyzacji MoziSmartBit. Model obniża barierę wdrożenia lokalnego dla osób i firm, jest licencjonowany do **darmowego użytku komercyjnego**, działa na kartach konsumenckich, oszczędza koszty tokenów chmurowych, zapewnia wolność tokenów 7×24 godziny oraz gwarantuje prywatność i bezpieczeństwo danych lokalnych.

---

## 2. Kluczowe funkcje

### 🧠 Dynamiczny siedmiowymiarowy system myślenia

Autorski system wnioskowania MoziAI. Dla dowolnego zadania model najpierw generuje znacznik **moziAI-Think**, a następnie dynamicznie rozwija ustrukturyzowane myślenie w zależności od złożoności zadania:

| Poziom | Scenariusz | Typowe zadania | Rozwijane wymiary |
| --- | --- | --- | --- |
| **Poziom 0** | Proste pytania i odpowiedzi | Wyjaśnianie terminów, wyszukiwanie faktów, tłumaczenie, streszczanie | ①Zrozumienie zadania ⑤Potrzeby zasobów (szybka odpowiedź 2-wymiarowa) |
| **Poziom 1** | Analiza i diagnoza | Badania rynku, copywriting, analiza danych, czytanie raportów, ocena strategii | ①②③⑤⑥ Ocena pięciowymiarowa |
| **Poziom 2** | Złożony rozwój/strategia | Rozwój kodu, projektowanie architektury, rozwój strategii kwant, wieloetapowe przepływy pracy, projektowanie systemów | ①②③④⑤⑥⑦ Pełne siedmiowymiarowe głębokie wnioskowanie |

> Siedem wymiarów: ①Zrozumienie zadania ②Ocena złożoności ③Zależności ④Ocena ryzyka ⑤Potrzeby zasobów ⑥Kryteria akceptacji ⑦Strategia wykonania

### 🔄 Mechanizm iteracji LOOP agenta

Złożone zadania automatycznie wchodzą w tryb iteracji **moziAI-Loop**: **Runda 1 wykonanie + ocena → Runda 2 dostosowanie + weryfikacja**, co zapewnia, że wyniki przechodzą samoweryfikację przed udzieleniem ostatecznej odpowiedzi. Model działa jak doświadczony inżynier: «dekompozycja problemu → ocena rozwiązania → wykonanie → refleksja → optymalizacja», znacząco zwiększając dokładność i wykonalność złożonych zadań. Proste pytania i zadania automatycznie wyłączają Loop.

### 📦 Inteligentna kwantyzacja MoziSmartBit

Autorska warstwowa inteligentna kwantyzacja: model Dense o 27 mld parametrów kompresowany do około **13,7 GB**, około 3,3 GB (~20%) mniejszy niż standardowy Q4_K_M (~17 GB), przy zachowaniu **~99%** dokładności FP16. Tradycyjna kwantyzacja stosuje jednolitą precyzję do wszystkich warstw; MoziSmartBit stosuje inteligentną strategię zróżnicowania dopasowaną do struktury Dense, z dokładnością lepszą niż Q4_K_M.

### 💰 Fokus na pionowej domenie finansowej

Głęboka optymalizacja pod pytania finansowe, programowanie ilościowe i wywoływanie narzędzi. Domena finansowa ma bardzo niską tolerancję na halucynacje modelu, a MoziAI wypada znacznie lepiej niż modele ogólne o podobnym rozmiarze w tej dziedzinie.

### 🌐 Inne funkcje

- **Wsparcie wielojęzyczne**: 201 języków i dialektów, z szczególną optymalizacją chińskiego
- **Programowanie ogólne**: rozwój full-stack, debugowanie kodu, projektowanie architektury, obejmuje Python/JS/TS/Go/Rust
- **Pisanie artykułów**: wysokiej jakości pisanie w wielu gatunkach — raporty, artykuły analityczne, dokumentacja techniczna, treści kreatywne
- **Rozumienie wizualne**: multimodalne widzenie, wsparcie rozumienia obrazów ze zrzutów ekranu lokalnie
- **Wsparcie wielu frameworków**: llama.cpp / Ollama / LM Studio / Jan
- **Wsparcie wielu Agentów**: OpenClaw / Hermes / Cursor / Claude Code / Codex itd., natywne wywoływanie narzędzi i wieloetapowa orkiestracja zadań

---

## 3. Notatki o aktualizacji wersji

Ta aktualizacja wzmacnia głównie: autorski tryb wnioskowania «dynamiczne siedmiowymiarowe myślenie + iteracja LOOP», inteligentniejsze rozpoznawanie złożoności zadań, wyższy wskaźnik ukończenia złożonych zadań oraz lepszą zdolność «najpierw pomyśl, potem działaj».

moziAI utrzymuje aktywną częstotliwość aktualizacji wersji, aby nadążać za przyszłym rozwojem AI, i nieustannie poprzez własne technologie sprawia, że lokalne modele AI są lżejsze we wdrożeniu i coraz bardziej zdolne.

---

## 4. Kluczowe możliwości

| Obszar możliwości | Opis |
| --- | --- |
| Analiza rynku | Interpretacja makro/mikroekonomiczna, analiza rynków A/HK/US/towarów/kryptowalut i ich logiki |
| Finanse i raporty | Interpretacja kluczowych wskaźników raportów finansowych, ekstrakcja streszczeń raportów, wsparcie wyceny i prognoz zysków |
| Ryzyko i zgodność | Ocena ryzyka produktów, przypomnienia o zgodności porad inwestycyjnych, interpretacja polityk regulacji finansowych |
| Kwant i strategia | Projektowanie pomysłów na strategie ilościowe, kwantyzacja Pyramid (PEL), logika backtestów, budowa czynników i wywoływanie narzędzi |
| Wywoływanie narzędzi | Łączenie z danymi rynkowymi w czasie rzeczywistym, bazami danych, wyszukiwaniem raportów finansowych |

---

## 5. Specyfikacja techniczna

| Element | Specyfikacja |
| --- | --- |
| Model bazowy | Qwen3.8-27B (architektura Dense, uwaga hybrydowa 16 full + 48 linear, licencja MIT) |
| Rozmiar parametrów | 27 mld (27B) architektura Dense |
| Metoda kwantyzacji | Autorska inteligentna kwantyzacja MoziSmartBit + standardowy format GGUF |
| Długość kontekstu | 128K (262 144 tokenów) |
| Rozmiar modelu | ~13,7 GB |
| Minimalne VRAM | **16GB+** wdrażalny (offload CPU); **20GB+** płynny długi kontekst; **24GB+** pełne 128K + widzenie |
| Frameworki wnioskowania | llama.cpp / Ollama / LM Studio / Jan |
| Szybkość wnioskowania | Z dekodowaniem spekulacyjnym MTP: R9700 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Zespół deweloperski | Zespół Chen Yumo |

---

## 6. ⚡ Szybki start (3 pliki = 100% aktywacji najlepszych możliwości wnioskowania)

> ⚠️ **Kluczowa uwaga**: Najlepsze możliwości wnioskowania MoziAI wymagają **pobrania 3 plików jednocześnie** — modelu głównego, projektora wizyjnego, szablonu czatu. Brak któregokolwiek spowoduje utratę odpowiednich możliwości.

### 6.1 Pobieranie plików modelu

Pobierz **wszystkie pliki z katalogu V3.8** z HuggingFace / ModelScope do tego samego katalogu lokalnego:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Model główny (wymagany, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Szablon czatu (wymagany, zawiera instrukcje myślenia+Loop)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Projektor wizyjny (wymagany, 927 MB)
```

| Plik | Rozmiar | Wymóg | Funkcja |
| --- | --- | --- | --- |
| Model główny `.gguf` | ~13,7 GB | **Wymagany** | Wagi modelu, podstawowe możliwości wnioskowania |
| Projektor wizyjny `mmproj` | ~927 MB | **Wymagany** | Multimodalne rozumienie wizualne, bez niego utrata możliwości obrazowych |
| Szablon czatu `.jinja` | Minimalny | **Wymagany** | Wstrzykuje tożsamość MoziAI + instrukcje siedmiowymiarowego myślenia + mechanizm LOOP |

### 6.2 Uruchamianie i użytkowanie

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Otwórz `http://localhost:8080` w przeglądarce, aby rozpocząć rozmowę. Pełne zalecane parametry w Sekcji 9.

---

## 7. Pobieranie modelu

| Platforma | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP) |

> 💡 **Użytkownicy LM Studio**: wyszukaj `moziAI` w [LM Studio](https://lmstudio.ai), aby pobrać jednym kliknięciem, bez ręcznego pobierania plików.

---

## 8. Polecenia uruchamiania

### Najprostsze uruchomienie (z 3 plikami)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Pełne zalecane uruchomienie

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

> 💡 Aby wyłączyć MTP: usuń `--spec-type draft-mtp` i powiązane parametry; prędkość ~30-50% niższa, mniejsze użycie VRAM.

---

## 9. Zalecane parametry wnioskowania

Na podstawie oficjalnych zaleceń llama.cpp i optymalizacji lokalnej (AMD Radeon AI PRO R9700 32GB):

| Parametr | Ogólny czat | Kodowanie/Agent | Uwagi |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Równowaga kreatywności i dokładności |
| top\_p | 0,95 | 0,95 | Próg próbkowania jądrowego |
| top\_k | 20 | 20 | Próbkowanie ucięte |
| repeat\_penalty | 1,05 | 1,05 | Kara za powtarzanie |
| context\_length | 262144 | 262144 | Długi kontekst 128K |
| reasoning | auto | auto | Włącz łańcuch wnioskowania (CoT) |
| reasoning\_budget | 400 | 400 | Budżet tokenów wnioskowania |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Wnioskowanie w osobnym polu |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Dekodowanie spekulacyjne MTP (patrz Sekcja 11)** |

> 💡 **Tryb myślenia**: włączany przez `--reasoning auto` — model wnioskuje wewnętrznie przed odpowiedzią. `reasoning_budget` ogranicza maksymalną liczbę tokenów myślenia (zalecane 400, regulowane 100-1000).

---

## 10. Porównanie formatów kwantyzacji

| Format | Rozmiar | Dokładność | Uwagi |
| --- | --- | --- | --- |
| FP16 oryginalny | ~54 GB | 100% | Bezstratny, wymaga profesjonalnego GPU |
| **MoziSmartBit (ten model)** | **~13,7 GB** | **~99%** | **Autorska inteligentna kwantyzacja, najlepsza dokładność na rozmiar** |
| Q4_K_M | ~17 GB | ~98% | Standardowe GGUF 4-bit |
| Q5_K_M | ~20 GB | ~99% | Wyższa dokładność |
| Q6_K | ~23 GB | ~99,5% | Prawie bezstratny |
| Q8_0 | ~31 GB | ~100% | Bezstratny |

> MoziSmartBit zachowuje ~99% dokładności, kompresując model Dense 27B do 13,7 GB (współczynnik 3,9x), ~20% mniejszy niż Q4_K_M — idealny dla kart konsumenckich.

---

## 11. Dekodowanie spekulacyjne MTP (kluczowa funkcja przyspieszająca)

Model zawiera warstwę dekodowania spekulacyjnego MTP (Multi-Token Prediction), która zwiększa szybkość wnioskowania **1,5-2 razy** po włączeniu. To natywna funkcja architektury Qwen3.8; MoziAI zachowuje pełne wagi MTP.

**Zasada**: w architekturze trenowany jest lekki nagłówek predykcyjny (Draft Model) do przewidywania kolejnych tokenów przed weryfikacją przez model główny, co zmniejsza liczbę przejść forward i opóźnienia. Błędy predykcji są korygowane przez model główny, bez negatywnego wpływu na jakość wyników.

### Parametry aktywacji

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parametr | Zalecana wartość | Opis |
| --- | --- | --- |
| --spec-type | draft-mtp | Włącza dekodowanie spekulacyjne MTP |
| --spec-draft-n-max | 2 | Maksymalnie 2 tokeny przewidywane na krok (zalecane, wskaźnik akceptacji ~80%) |
| --spec-draft-p-min | 0,75 | Minimalny próg prawdopodobieństwa akceptacji (0,0-1,0, większy = bardziej konserwatywny) |

### Sugestie dostrajania

| n-max | Wskaźnik akceptacji | Scenariusz |
| --- | --- | --- |
| 1 | ~90% | Najbardziej konserwatywny, najmniejszy wzrost prędkości |
| **2** | **~80%** | **Zalecany: równowaga prędkości i dokładności** |
| 3 | ~71% | Scenariusz ogólny, wyraźny wzrost prędkości |
| 4-5 | ~60-65% | Pisanie kreatywne, generowanie kodu |
| 6 | ~50-55% | Długie czyste teksty (wymaga dostrojenia p-min) |

---

## 12. Zalecenia konfiguracji VRAM

| VRAM | Zalecana konfiguracja | Opis |
| --- | --- | --- |
| 16 GB | Kontekst zmniejszony do 64K, wymaga offload CPU | Poziom wejściowy, np. RTX 4060 Ti |
| **20 GB** | **Pełne 128K, pamięć KV q4_0** | **Zalecana konfiguracja**, np. RX 7900 XT / RTX 5070 Ti |
| 24 GB | Pełne 128K, wystarczający zapas VRAM | RTX 4090 / RX 7900 XTX |
| 32 GB+ | Pełne 128K, najsilniejsza konfiguracja | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | Pełne 128K | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Im dłuższy kontekst, tym więcej VRAM. Przy OOM stopniowo obniżaj `-c`. Użyj `--fit on`, aby llama.cpp automatycznie dostosował liczbę warstw. Wspiera NVIDIA / AMD / Intel.

---

## 13. Metody wdrożenia

### Wdrożenie Ollama

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

Wyszukaj `moziAI` w LM Studio / Jan i wybierz wersję kwantyzacji Q4\_K\_M do pobrania.

> 💡 Wsparcie Ollama dla mmproj i chat\_template jest ograniczone; zaleca się najpierw użycie llama.cpp dla pełnej funkcjonalności.

---

## 14. Benchmarki

MoziAI-27B-3.8 opiera się na fine-tuningu bazy Qwen3.8-27B, z pionową domeną finansową jako głównym kierunkiem optymalizacji.

### Zdolność kodowania

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Zdolność agentów

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Zdolność ogólna

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Zdolność multimodalna

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Dane konkurencji to oficjalnie opublikowane wyniki ewaluacji. Pionowa domena finansowa MoziAI (interpretacja raportów finansowych, strategie ilościowe, zgodność zarządzania ryzykiem, wywoływanie narzędzi agentów) znacznie przewyższa modele ogólne.

---

## 15. Licencja

Model używa **niestandardowej licencji ograniczającej**:

- ✅ **Dozwolone** — darmowe użytkowanie komercyjne, kopiowanie i dystrybucja
- ❌ **Zabronione** — dalszy rozwój, odsprzedaż, sublicencjonowanie
- 📋 **Wymagane** — zachowanie oryginalnego powiadomienia o prawach autorskich, podanie źródła: moziAI-27B

Model jest dostarczany „tak jak jest", bez żadnych gwarancji. Wyniki modelu służą wyłącznie celom informacyjnym i nie stanowią porady inwestycyjnej. Użytkownik ponosi całe ryzyko.

Pełne warunki w pliku [LICENSE](LICENSE).

---

## 16. Kontakt

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
