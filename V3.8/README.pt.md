---
language:
- pt
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

# MoziAI-27B-3.8 — Um modelo de IA multimodal compacto, porém poderoso, de implantação local gratuita

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | Português | [Español](README.es.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md) | [Polski](README.pl.md)

**Data de publicação: 2026-08-30** · **Versão: V3.8**

---

## 📑 Índice

- [1. Visão geral do modelo](#1-visão-geral-do-modelo)
- [2. Principais recursos](#2-principais-recursos) — Pensamento dinâmico de sete dimensões / LOOP / MoziSmartBit / Foco financeiro
- [3. Notas de atualização de versão](#3-notas-de-atualização-de-versão)
- [4. Capacidades principais](#4-capacidades-principais)
- [5. Especificações técnicas](#5-especificações-técnicas)
- [6. ⚡ Início rápido](#6--início-rápido-3-arquivos--100-de-ativação-da-melhor-capacidade-de-inferência) — **download de 3 arquivos**
- [7. Download do modelo](#7-download-do-modelo)
- [8. Comandos de execução](#8-comandos-de-execução)
- [9. Parâmetros de inferência recomendados](#9-parâmetros-de-inferência-recomendados)
- [10. Comparação de formatos de quantização](#10-comparação-de-formatos-de-quantização)
- [11. Decodificação especulativa MTP](#11-decodificação-especulativa-mtp-recurso-chave-de-aceleração)
- [12. Recomendações de configuração de VRAM](#12-recomendações-de-configuração-de-vram)
- [13. Métodos de implantação](#13-métodos-de-implantação)
- [14. Benchmarks](#14-benchmarks)
- [15. Licença](#15-licença)
- [16. Contato](#16-contato)

---

## 1. Visão geral do modelo

MoziAI-27B-3.8 é um modelo de IA multimodal de código aberto, implantável localmente, desenvolvido pela equipe de Chen Yumo, influenciador financeiro líder da China. Construído sobre a base de código aberto **Qwen3.8-27B** (arquitetura Dense 27B, licença MIT), integra dados financeiros próprios da equipe + capacidades do domínio financeiro + sistema de pensamento dinâmico de sete dimensões + mecanismo de iteração e reflexão LOOP do agente + algoritmo de quantização híbrida MoziSmartBit. Este modelo reduz a barreira de implantação local para indivíduos e empresas, é licenciado para **uso comercial gratuito**, roda em GPUs de consumo, economiza custos de tokens na nuvem, alcança liberdade de tokens 7×24 horas e garante privacidade e segurança dos dados locais.

---

## 2. Principais recursos

### 🧠 Sistema de pensamento dinâmico de sete dimensões

Estrutura de raciocínio central desenvolvida pela MoziAI. Para qualquer tarefa, o modelo primeiro emite a marca **moziAI-Think** e, em seguida, expande dinamicamente o pensamento estruturado conforme a complexidade da tarefa:

| Nível | Cenário | Tarefas típicas | Dimensões expandidas |
| --- | --- | --- | --- |
| **Nível 0** | Perguntas simples | Explicação de termos, consulta de fatos, tradução, resumo | ①Entender tarefa ⑤Necessidades de recursos (resposta rápida de 2 dimensões) |
| **Nível 1** | Análise e diagnóstico | Pesquisa de mercado, redação, análise de dados, leitura de relatórios, avaliação de estratégias | ①②③⑤⑥ Avaliação de cinco dimensões |
| **Nível 2** | Desenvolvimento/estratégia complexos | Desenvolvimento de código, design de arquitetura, estratégias quantitativas, fluxos de trabalho de várias etapas, design de sistemas | ①②③④⑤⑥⑦ Raciocínio profundo completo de sete dimensões |

> Sete dimensões: ①Entender tarefa ②Avaliar complexidade ③Dependências ④Avaliar riscos ⑤Necessidades de recursos ⑥Critérios de aceitação ⑦Estratégia de execução

### 🔄 Mecanismo de iteração LOOP do agente

Tarefas complexas entram automaticamente no modo de iteração **moziAI-Loop**: **Rodada 1 execução + avaliação → Rodada 2 ajuste + verificação**, garantindo que a saída passe por autoverificação antes da resposta final. O modelo age como engenheiro sênior: «decompor problema → avaliar solução → executar → refletir → otimizar», melhorando significativamente a precisão e a viabilidade de tarefas complexas. Perguntas e tarefas simples fecham o Loop automaticamente.

### 📦 Quantização inteligente MoziSmartBit

Quantização inteligente em camadas própria: o modelo Dense de 27 bilhões de parâmetros é comprimido para aproximadamente **13,7 GB**, cerca de 3,3 GB (~20%) menor que o Q4_K_M padrão (~17 GB), mantendo **~99%** da precisão FP16. A quantização tradicional aplica precisão uniforme a todas as camadas; a MoziSmartBit usa estratégia de diferenciação inteligente adaptada à estrutura Dense, com precisão superior ao Q4_K_M.

### 💰 Foco no domínio financeiro vertical

Otimização profunda para perguntas financeiras, programação quantitativa e chamada de ferramentas. O domínio financeiro tem tolerância extremamente baixa à alucinação de modelos, e a MoziAI supera significativamente os modelos gerais de tamanho semelhante neste domínio.

### 🌐 Outros recursos

- **Suporte multilíngue**: 201 idiomas e dialetos, com chinês especialmente otimizado
- **Programação geral**: desenvolvimento full-stack, depuração, design de arquitetura, cobrindo Python/JS/TS/Go/Rust
- **Redação**: relatórios de pesquisa, artigos analíticos, documentação técnica, conteúdo criativo
- **Compreensão visual**: visão multimodal, compreensão local de capturas de tela
- **Suporte multi-framework**: llama.cpp / Ollama / LM Studio / Jan
- **Suporte multi-Agent**: OpenClaw / Hermes / Cursor / Claude Code / Codex, chamada nativa de ferramentas e orquestração de tarefas em várias rodadas

---

## 3. Notas de atualização de versão

Esta atualização reforça principalmente: o modo de raciocínio próprio da MoziAI «pensamento dinâmico de sete dimensões + iteração LOOP», permitindo reconhecer a complexidade das tarefas de forma mais inteligente, com maior taxa de conclusão de tarefas complexas e melhor capacidade de «pensar primeiro, agir depois».

A MoziAI mantém uma cadência ativa de atualizações de versão, garantindo o acompanhamento do desenvolvimento futuro da IA e, por meio de tecnologia própria, tornando os modelos de IA locais mais leves de implantar e cada vez mais capazes.

---

## 4. Capacidades principais

| Área de capacidade | Descrição |
| --- | --- |
| Análise de mercado | Interpretação macro/microeconômica, análise de mercados A/HK/US/commodities/criptomoedas e lógica |
| Finanças e relatórios | Interpretação de indicadores-chave de relatórios financeiros, resumos de pesquisa, avaliação e projeção de lucros |
| Risco e conformidade | Avaliação de risco de produtos, lembretes de conformidade de conselhos de investimento, políticas regulatórias financeiras |
| Quant e estratégia | Design de estratégias quantitativas, quantização Pyramid (PEL), lógica de backtest, construção de fatores e chamada de ferramentas |
| Chamada de ferramentas | Conexão a dados de mercado em tempo real, bancos de dados, busca de relatórios financeiros |

---

## 5. Especificações técnicas

| Item | Especificação |
| --- | --- |
| Modelo base | Qwen3.8-27B (arquitetura Dense, atenção híbrida 16 full + 48 linear, licença MIT) |
| Tamanho de parâmetros | 27 bilhões (27B) arquitetura Dense |
| Método de quantização | Quantização inteligente MoziSmartBit + formato padrão GGUF |
| Comprimento do contexto | 256K (262 144 tokens) |
| Tamanho do modelo | ~13,7 GB |
| VRAM mínima | **16GB+** implantável (offload CPU); **20GB+** contexto longo fluido; **32GB+** 256K completo + visão |
| Frameworks de inferência | llama.cpp / Ollama / LM Studio / Jan |
| Velocidade de inferência | Com decodificação especulativa MTP: R9700 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Equipe de desenvolvimento | Equipe Chen Yumo |

---

## 6. ⚡ Início rápido 3 arquivos = 100% de ativação da melhor capacidade de inferência

> ⚠️ **Nota principal**: a melhor capacidade de inferência da MoziAI requer **download de 3 arquivos simultaneamente** — modelo principal, projetor de visão, template de chat. A falta de qualquer um perde a capacidade correspondente.

### 6.1 Download dos arquivos do modelo

Baixe **todos os arquivos do diretório V3.8** do HuggingFace / ModelScope para o mesmo diretório local:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Modelo principal (obrigatório, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Template de chat (obrigatório, com instruções de pensamento+Loop)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Projetor de visão (obrigatório, 927 MB)
```

| Arquivo | Tamanho | Necessidade | Função |
| --- | --- | --- | --- |
| Modelo principal `.gguf` | ~13,7 GB | **Obrigatório** | Pesos do modelo, capacidade central de inferência |
| Projetor de visão `mmproj` | ~927 MB | **Obrigatório** | Compreensão visual multimodal, sem ele perde a capacidade de imagem |
| Template de chat `.jinja` | Mínimo | **Obrigatório** | Injeta identidade MoziAI + instruções de pensamento de sete dimensões + mecanismo LOOP |

### 6.2 Iniciar e usar

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Abra `http://localhost:8080` no navegador para iniciar a conversa. Parâmetros completos recomendados na Seção 9.

---

## 7. Download do modelo

| Plataforma | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP) |

> 💡 **Usuários do LM Studio**: pesquise `moziAI` no [LM Studio](https://lmstudio.ai) para download com um clique, sem baixar arquivos manualmente.

---

## 8. Comandos de execução

### Início mínimo (com os 3 arquivos)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Início completo recomendado

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

> 💡 Para desativar MTP: remova `--spec-type draft-mtp` e parâmetros relacionados; velocidade ~30-50% menor, uso de VRAM menor.

---

## 9. Parâmetros de inferência recomendados

Baseado nos parâmetros oficiais recomendados do llama.cpp e otimização local (AMD Radeon AI PRO R9700 32GB):

| Parâmetro | Chat geral | Codificação/Agent | Notas |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Equilíbrio entre criatividade e precisão |
| top\_p | 0,95 | 0,95 | Limiar de amostragem nuclear |
| top\_k | 20 | 20 | Amostragem truncada |
| repeat\_penalty | 1,05 | 1,05 | Penalidade de repetição |
| context\_length | 131072 | 262144 | Chat 128K / Codificação 256K (padrão llama.cpp 128K) |
| reasoning | auto | auto | Ativar cadeia de raciocínio (CoT) |
| reasoning\_budget | 400 | 400 | Orçamento de tokens de raciocínio |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Raciocínio em campo separado |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Decodificação especulativa MTP (ver Seção 11)** |

> 💡 **Modo de pensamento**: ativado com `--reasoning auto` — o modelo raciocina internamente antes de responder. `reasoning_budget` controla o máximo de tokens de pensamento (recomendado 400, ajustável 100-1000).

---

## 10. Comparação de formatos de quantização

| Formato | Tamanho | Precisão | Notas |
| --- | --- | --- | --- |
| FP16 original | ~54 GB | 100% | Sem perdas, requer GPU profissional |
| **MoziSmartBit (este modelo)** | **~13,7 GB** | **~99%** | **Quantização inteligente própria, melhor precisão por tamanho** |
| Q4_K_M | ~17 GB | ~98% | GGUF padrão 4-bit |
| Q5_K_M | ~20 GB | ~99% | Maior precisão |
| Q6_K | ~23 GB | ~99,5% | Quase sem perdas |
| Q8_0 | ~31 GB | ~100% | Sem perdas |

> A MoziSmartBit mantém ~99% de precisão comprimindo o modelo Dense 27B para 13,7 GB (compressão 3,9x), ~20% menor que Q4_K_M — ideal para GPUs de consumo.

---

## 11. Decodificação especulativa MTP recurso-chave de aceleração

Este modelo incorpora a camada de decodificação especulativa MTP (Multi-Token Prediction), que aumenta a velocidade de inferência **1,5-2 vezes** quando ativada. É um recurso nativo da arquitetura Qwen3.8; a MoziAI preserva os pesos MTP completos.

**Princípio**: um cabeçalho de predição leve (Draft Model) é treinado na arquitetura para adivinhar tokens subsequentes antes da verificação do modelo principal, reduzindo as passagens forward e a latência. Erros de predição são corrigidos pelo modelo principal, sem impacto negativo na qualidade da saída.

### Parâmetros de ativação

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parâmetro | Valor recomendado | Descrição |
| --- | --- | --- |
| --spec-type | draft-mtp | Ativa a decodificação especulativa MTP |
| --spec-draft-n-max | 2 | Máximo de 2 tokens adivinhados por passo (recomendado, taxa de aceitação ~80%) |
| --spec-draft-p-min | 0,75 | Limiar mínimo de probabilidade de aceitação (0,0-1,0, maior = mais conservador) |

### Ajustes sugeridos

| n-max | Taxa de aceitação | Cenário |
| --- | --- | --- |
| 1 | ~90% | Mais conservador, menor ganho de velocidade |
| **2** | **~80%** | **Recomendado: equilíbrio entre velocidade e precisão** |
| 3 | ~71% | Cenário geral, melhora notável de velocidade |
| 4-5 | ~60-65% | Escrita criativa, geração de código |
| 6 | ~50-55% | Saída longa de texto puro (requer ajuste de p-min) |

---

## 12. Recomendações de configuração de VRAM

| VRAM | Configuração recomendada | Descrição |
| --- | --- | --- |
| 16 GB | Contexto reduzido para 64K, requer offload CPU | Nível de entrada, ex. RTX 4060 Ti |
| **20 GB** | **128K completo, cache KV q4_0** | **Configuração recomendada**, ex. RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K completo, folga de VRAM ampla | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 256K completo, configuração mais potente | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 256K completo | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Quanto mais longo o contexto, mais VRAM é usada. Em OOM, reduza `-c` gradualmente. Use `--fit on` para ajuste automático de camadas. Compatível com NVIDIA / AMD / Intel.

---

## 13. Métodos de implantação

### Implantação com Ollama

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

Pesquise `moziAI` no LM Studio / Jan e selecione a versão de quantização Q4\_K\_M para download.

> 💡 O suporte do Ollama para mmproj e chat\_template é limitado; recomenda-se usar llama.cpp para funcionalidade completa.

---

## 14. Benchmarks

O MoziAI-27B-3.8 baseia-se no fine-tuning da base Qwen3.8-27B, com o domínio financeiro vertical como direção central de otimização.

### Capacidade de codificação

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Capacidade de agente

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Capacidade geral

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Capacidade multimodal

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Os dados dos concorrentes são resultados oficiais publicados. O domínio financeiro vertical da MoziAI (interpretação de relatórios financeiros, estratégias quantitativas, conformidade de riscos, chamadas de ferramentas de agentes) supera significativamente os modelos gerais.

---

## 15. Licença

Este modelo usa uma **licença restritiva personalizada**:

- ✅ **Permitido** — uso comercial gratuito, cópia e distribuição
- ❌ **Proibido** — desenvolvimento posterior, revenda, sublicenciamento
- 📋 **Exigido** — manter o aviso de direitos autorais original, creditar: moziAI-27B

O modelo é fornecido \"como está\", sem garantias de qualquer tipo. A saída do modelo é apenas para referência e não constitui aconselhamento de investimento. O usuário assume todos os riscos.

Consulte o arquivo [LICENSE](LICENSE) para os termos completos.

---

## 16. Contato

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
