---
language:
- tr
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

# MoziAI-27B-3.8 — Küçük ama Güçlü, Yerel Olarak Ücretsiz Dağıtılabilen Çok Modlu AI Modeli

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | Türkçe | [Español](README.es.md) | [Português](README.pt.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Tiếng Việt](README.vi.md) | [Polski](README.pl.md)

**Yayın Tarihi: 2026-08-30** · **Sürüm: V3.8**

---

## 📑 İçindekiler

- [1. Modele Genel Bakış](#1-modele-genel-bakış)
- [2. Temel Özellikler](#2-temel-özellikler) — Dinamik Yedi Boyutlu Düşünme / LOOP / MoziSmartBit / Finans Odağı
- [3. Sürüm Yükseltme Notları](#3-sürüm-yükseltme-notları)
- [4. Temel Yetenekler](#4-temel-yetenekler)
- [5. Teknik Özellikler](#5-teknik-özellikler)
- [6. ⚡ Hızlı Başlangıç](#6--hızlı-başlangıç-3-dosya--100-en-i̇yi-çıkarım-yeteneğini-etkinleştirin) — **3 dosya indirme**
- [7. Model İndirme](#7-model-i̇ndirme)
- [8. Çalıştırma Komutları](#8-çalıştırma-komutları)
- [9. Önerilen Çıkarım Parametreleri](#9-önerilen-çıkarım-parametreleri)
- [10. Kuantizasyon Formatı Karşılaştırması](#10-kuantizasyon-formatı-karşılaştırması)
- [11. MTP Spekülatif Kod Çözme](#11-mtp-spekülatif-kod-çözme-önemli-hızlandırma-özelliği)
- [12. VRAM Yapılandırma Önerileri](#12-vram-yapılandırma-önerileri)
- [13. Dağıtım Yöntemleri](#13-dağıtım-yöntemleri)
- [14. Kıyaslamalar](#14-kıyaslamalar)
- [15. Lisans](#15-lisans)
- [16. İletişim](#16-i̇letişim)

---

## 1. Modele Genel Bakış

MoziAI-27B-3.8, Çin'in önde gelen finans fenomeni Chen Yumo'nun ekibi tarafından geliştirilen, yerel olarak dağıtılabilir açık kaynak çok modlu AI modelidir. Açık kaynak taban **Qwen3.8-27B** (Dense 27B mimarisi, MIT lisansı) üzerine inşa edilmiş olup, ekibin kendi geliştirdiği finansal veri + finansal alan yetenekleri + dinamik yedi boyutlu düşünme çerçevesi + ajan LOOP yansıtma ve yineleme mekanizması + MoziSmartBit hibrit kuantizasyon algoritmasını birleştirir. Bu model, bireyler ve işletmeler için yerel dağıtım engelini azaltır, **ücretsiz ticari kullanım** için lisanslıdır, tüketici GPU'larında çalışır, bulut token maliyetlerinden tasarruf sağlar, 7×24 saat token özgürlüğü sunar ve yerel veri gizliliği ile güvenliğini garanti eder.

---

## 2. Temel Özellikler

### 🧠 Dinamik Yedi Boyutlu Düşünme Çerçevesi

MoziAI'nin kendi geliştirdiği temel akıl yürütme çerçevesi. Herhangi bir görevde model önce **moziAI-Think** işaretini çıkarır, ardından görev karmaşıklığına göre yapılandırılmış düşünmeyi dinamik olarak genişletir:

| Seviye | Senaryo | Tipik Görevler | Genişletilen Boyutlar |
| --- | --- | --- | --- |
| **Seviye 0** | Basit soru-cevap | Terim açıklama, bilgi arama, çeviri, özetleme | ①Görevi anlama ⑤Kaynak ihtiyaçları (iki boyutlu hızlı yanıt) |
| **Seviye 1** | Analiz ve teşhis | Pazar araştırması, metin yazarlığı, veri analizi, rapor okuma, strateji değerlendirme | ①②③⑤⑥ Beş boyutlu değerlendirme |
| **Seviye 2** | Karmaşık geliştirme/strateji | Kod geliştirme, mimari tasarım, kant strateji geliştirme, çok adımlı iş akışları, sistem tasarımı | ①②③④⑤⑥⑦ Tam yedi boyutlu derin akıl yürütme |

> Yedi boyut: ①Görevi anlama ②Karmaşıklık değerlendirmesi ③Bağımlılıklar ④Risk değerlendirmesi ⑤Kaynak ihtiyaçları ⑥Kabul kriterleri ⑦Yürütme stratejisi

### 🔄 Ajan LOOP Yineleme Mekanizması

Karmaşık görevler otomatik olarak **moziAI-Loop** yineleme moduna girer: **1. Tur yürütme + değerlendirme → 2. Tur ayarlama + doğrulama**, nihai yanıt verilmeden önce çıktının öz doğrulamadan geçmesini sağlar. Model kıdemli bir mühendis gibi çalışır: «sorunu parçala → çözümü değerlendir → yürüt → yansıt → optimize et», karmaşık görevlerin doğruluğunu ve uygulanabilirliğini önemli ölçüde artırır. Basit soru-cevap ve görevlerde Loop otomatik kapanır.

### 📦 MoziSmartBit Akıllı Kuantizasyon

Kendi geliştirilen katmanlı akıllı kuantizasyon: Dense 27 milyar parametreli model yaklaşık **13,7 GB**'a sıkıştırılır, standart Q4_K_M'den (~17 GB) yaklaşık 3,3 GB (~%20) daha küçüktür ve FP16 **~%99** doğruluğunu korur. Geleneksel kuantizasyon tüm katmanlara tek tip hassasiyet uygular; MoziSmartBit, Dense yapısına uygun akıllı farklılaştırma stratejisi kullanır ve Q4_K_M'den daha iyi doğruluk sağlar.

### 💰 Finansal Dikey Alan Odağı

Finansal soru-cevap, kantitatif programlama ve araç çağrısı için derin optimizasyon. Finans alanı model halüsinasyonlarına karşı son derece düşük toleransa sahiptir ve MoziAI bu alanda aynı boyuttaki genel modellerden belirgin şekilde daha iyi performans gösterir.

### 🌐 Diğer Özellikler

- **Çok dilli destek**: 201 dil ve lehçe, Çince yetenekleri özel olarak optimize edilmiş
- **Genel programlama**: full-stack geliştirme, kod hata ayıklama, mimari tasarım, Python/JS/TS/Go/Rust kapsar
- **Makale yazımı**: araştırma raporları, analiz makaleleri, teknik belgeler, yaratıcı içerik gibi çok türde yüksek kaliteli yazım
- **Görsel anlama**: çok modlu görüş, yerel ekran görüntüsü ile görüntü içeriğini anlama
- **Çoklu çerçeve desteği**: llama.cpp / Ollama / LM Studio / Jan
- **Çoklu Ajan desteği**: OpenClaw / Hermes / Cursor / Claude Code / Codex vb., yerel araç çağrısı ve çok turlu görev orkestrasyonu

---

## 3. Sürüm Yükseltme Notları

Bu yükseltme esas olarak şunları güçlendirir: moziAI'nin kendi geliştirdiği «dinamik yedi boyutlu düşünme + LOOP yineleme» akıl yürütme modunu, görev karmaşıklığını daha akıllı tanımasını, karmaşık görev tamamlama oranının yükselmesini ve «önce düşün, sonra yap» yeteneğinin gelişmesini sağlar.

moziAI, gelecekteki yapay zeka gelişimini takip etmek için aktif sürüm yükseltme sıklığını korur ve kendi teknolojileriyle yerel AI modellerini daha hafif dağıtılabilir ve giderek daha yetenekli hale getirir.

---

## 4. Temel Yetenekler

| Yetenek Alanı | Açıklama |
| --- | --- |
| Pazar Analizi | Makro/mikro ekonomik yorum, A/HK/ABD/hisse senedi/emtia/kripto piyasa ve mantık analizi |
| Finans ve Raporlar | Finansal rapor temel göstergeleri yorumlama, araştırma raporu özet çıkarma, değerleme ve kazanç tahmini desteği |
| Risk ve Uyum | Ürün risk değerlendirmesi, yatırım tavsiyesi uyum hatırlatmaları, finansal düzenleme politikaları yorumlama |
| Kant ve Strateji | Kantitatif strateji fikir tasarımı, Pyramid (PEL) kuantizasyonu, geri test mantığı, faktör oluşturma ve araç çağrısı |
| Araç Çağrısı | Gerçek zamanlı piyasa verileri, veritabanları, araştırma raporu arama gibi finansal veri kaynaklarına bağlanma |

---

## 5. Teknik Özellikler

| Öğe | Özellik |
| --- | --- |
| Taban Model | Qwen3.8-27B (Dense mimarisi, hibrit dikkat 16 full + 48 linear, MIT lisansı) |
| Parametre Boyutu | 27 milyar (27B) Dense mimarisi |
| Kuantizasyon Yöntemi | Kendi geliştirilen MoziSmartBit akıllı kuantizasyon + GGUF standart formatı |
| Bağlam Uzunluğu | 256K (262.144 token) |
| Model Boyutu | ~13,7 GB |
| Minimum VRAM | **16GB+** dağıtılabilir (CPU offload); **20GB+** akıcı uzun bağlam; **32GB+** tam 256K + görüş |
| Çıkarım Çerçeveleri | llama.cpp / Ollama / LM Studio / Jan |
| Çıkarım Hızı | MTP spekülatif kod çözme ile: R9700 70+ tok/sn, MAX+395 iGPU 50+ tok/sn, GPU 35+ tok/sn |
| Geliştirme Ekibi | Chen Yumo Ekibi |

---

## 6. ⚡ Hızlı Başlangıç 3 Dosya = %100 En İyi Çıkarım Yeteneğini Etkinleştirin

> ⚠️ **Temel Not**: MoziAI'nin en iyi çıkarım yeteneği için **3 dosyayı birlikte indirmeniz** gerekir — ana model, görüş projektörü, sohbet şablonu. Herhangi birinin eksik olması ilgili yeteneği kaybettirir.

### 6.1 Model Dosyalarını İndirme

HuggingFace / ModelScope'tan **V3.8 dizinindeki tüm dosyaları** aynı yerel dizine indirin:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Ana model (zorunlu, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Sohbet şablonu (zorunlu, düşünme+Loop talimatları içerir)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Görüş projektörü (zorunlu, 927 MB)
```

| Dosya | Boyut | Gereklilik | İşlev |
| --- | --- | --- | --- |
| Ana model `.gguf` | ~13,7 GB | **Zorunlu** | Model ağırlıkları, temel çıkarım yeteneği |
| Görüş projektörü `mmproj` | ~927 MB | **Zorunlu** | Çok modlu görsel anlama, yüklenmezse görüntü yeteneği kaybolur |
| Sohbet şablonu `.jinja` | Çok küçük | **Zorunlu** | MoziAI kimliği + yedi boyutlu düşünme + LOOP mekanizma talimatlarını enjekte eder |

### 6.2 Başlatma ve Kullanım

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Tarayıcıda `http://localhost:8080` adresini açarak sohbete başlayın. Tam önerilen parametreler Bölüm 9'da.

---

## 7. Model İndirme

| Platform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP) |

> 💡 **LM Studio kullanıcıları**: [LM Studio](https://lmstudio.ai)'da `moziAI` arayarak tek tıkla indirin, dosyaları manuel indirmenize gerek yok.

---

## 8. Çalıştırma Komutları

### En Basit Başlatma (3 dosya ile)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Tam Önerilen Başlatma

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

> 💡 MTP'yi kapatmak için: `--spec-type draft-mtp` ve ilgili parametreleri silin; hız ~%30-50 düşer, VRAM kullanımı azalır.

---

## 9. Önerilen Çıkarım Parametreleri

llama.cpp resmi önerilen parametreleri ve yerel optimizasyona dayanır (AMD Radeon AI PRO R9700 32GB):

| Parametre | Genel sohbet | Kodlama/Agent | Notlar |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Yaratıcılık ve doğruluk dengesi |
| top\_p | 0,95 | 0,95 | Çekirdek örnekleme eşiği |
| top\_k | 20 | 20 | Kesilmiş örnekleme |
| repeat\_penalty | 1,05 | 1,05 | Tekrar cezası |
| context\_length | 131072 | 262144 | Sohbet 128K / Kodlama 256K (llama.cpp varsayılan 128K) |
| reasoning | auto | auto | Akıl yürütme zincirini etkinleştir (CoT) |
| reasoning\_budget | 400 | 400 | Akıl yürütme bütçe tokenleri |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Akıl yürütmeyi ayrı alanda çıkar |
| **spec-type** | **draft-mtp** | **draft-mtp** | **MTP spekülatif kod çözme (bkz. Bölüm 11)** |

> 💡 **Düşünme modu**: `--reasoning auto` ile etkinleştirilir — model yanıtlamadan önce dahili olarak akıl yürütür. `reasoning_budget` maksimum düşünme tokenlerini sınırlar (önerilen 400, 100-1000 arası ayarlanabilir).

---

## 10. Kuantizasyon Formatı Karşılaştırması

| Format | Boyut | Doğruluk | Notlar |
| --- | --- | --- | --- |
| FP16 orijinal | ~54 GB | %100 | Kayıpsız, profesyonel GPU gerekir |
| **MoziSmartBit (bu model)** | **~13,7 GB** | **~%99** | **Kendi geliştirilen akıllı kuantizasyon, boyut başına en iyi doğruluk** |
| Q4_K_M | ~17 GB | ~%98 | Standart GGUF 4-bit |
| Q5_K_M | ~20 GB | ~%99 | Daha yüksek doğruluk |
| Q6_K | ~23 GB | ~%99,5 | Neredeyse kayıpsız |
| Q8_0 | ~31 GB | ~%100 | Kayıpsız |

> MoziSmartBit, Dense 27B modelini 13,7 GB'a sıkıştırırken ~%99 doğruluğu korur (3,9x sıkıştırma), Q4_K_M'den ~%20 daha küçük — tüketici GPU'ları için ideal.

---

## 11. MTP Spekülatif Kod Çözme Önemli Hızlandırma Özelliği

Bu model, etkinleştirildiğinde çıkarım hızını **1,5-2 kat** artıran MTP (Multi-Token Prediction) spekülatif kod çözme katmanına sahiptir. Bu, Qwen3.8 mimarisinin yerel bir özelliğidir; MoziAI tam MTP ağırlıklarını korur.

**İlke**: mimaride, ana model doğrulamasından önce sonraki tokenleri tahmin eden hafif bir tahmin başlığı (Draft Model) eğitilir, forward geçişlerini ve gecikmeyi azaltır. Tahmin hataları ana model tarafından düzeltilir, çıktı kalitesine olumsuz etkisi yoktur.

### Etkinleştirme Parametreleri

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parametre | Önerilen Değer | Açıklama |
| --- | --- | --- |
| --spec-type | draft-mtp | MTP spekülatif kod çözmeyi etkinleştirir |
| --spec-draft-n-max | 2 | Adım başına en fazla 2 token tahmini (önerilen, kabul oranı ~%80) |
| --spec-draft-p-min | 0,75 | Minimum kabul olasılık eşiği (0,0-1,0, büyük = daha muhafazakâr) |

### Ayar Önerileri

| n-max | Kabul Oranı | Senaryo |
| --- | --- | --- |
| 1 | ~%90 | En muhafazakâr, en az hız artışı |
| **2** | **~%80** | **Önerilen: hız ve doğruluk dengesi** |
| 3 | ~%71 | Genel senaryo, belirgin hız artışı |
| 4-5 | ~%60-65 | Yaratıcı yazım, kod üretimi |
| 6 | ~%50-55 | Uzun saf metin çıktısı (p-min ayarı gerekir) |

---

## 12. VRAM Yapılandırma Önerileri

| VRAM | Önerilen Yapılandırma | Açıklama |
| --- | --- | --- |
| 16 GB | Bağlam 64K'ya düşürülür, CPU offload gerekir | Giriş seviyesi, ör. RTX 4060 Ti |
| **20 GB** | **128K tam, q4_0 KV önbelleği** | **Önerilen yapılandırma**, ör. RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K tam, yeterli VRAM boşluğu | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 256K tam, en güçlü yapılandırma | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 256K tam | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Bağlam ne kadar uzunsa VRAM kullanımı o kadar artar. OOM durumunda `-c`'yi kademeli düşürün. llama.cpp'nin katman sayısını otomatik ayarlaması için `--fit on` kullanın. NVIDIA / AMD / Intel destekler.

---

## 13. Dağıtım Yöntemleri

### Ollama Dağıtımı

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

LM Studio / Jan'da `moziAI` arayın ve Q4\_K\_M kuantizasyon sürümünü seçip indirin.

> 💡 Ollama'nın mmproj ve chat\_template desteği sınırlıdır, tam işlevsellik için öncelikle llama.cpp kullanmanız önerilir.

---

## 14. Kıyaslamalar

MoziAI-27B-3.8, Qwen3.8-27B tabanının ince ayarına dayanır; finansal dikey alan çekirdek optimizasyon yönüdür.

### Kodlama Yeteneği

| Kıyaslama | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Ajan Yeteneği

| Kıyaslama | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Genel Yetenek

| Kıyaslama | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Çok Modlu Yetenek

| Kıyaslama | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Rakip verileri resmi yayınlanmış değerlendirme sonuçlarıdır. MoziAI'nin finansal dikey alanı (finansal rapor yorumlama, kantitatif strateji, risk yönetimi uyumu, ajan araç çağrısı) genel modellerden belirgin şekilde üstündür.

---

## 15. Lisans

Bu model **özel kısıtlayıcı lisans** kullanır:

- ✅ **İzin verilir** — ücretsiz ticari kullanım, kopyalama ve dağıtım
- ❌ **Yasaktır** — daha fazla geliştirme, yeniden satış, alt lisanslama
- 📋 **Gerekli** — orijinal telif hakkı bildirimini koruyun, kaynak belirtin: moziAI-27B

Model "olduğu gibi", herhangi bir garanti olmadan sağlanır. Model çıktısı yalnızca referans içindir ve yatırım tavsiyesi oluşturmaz. Kullanıcılar tüm riskleri üstlenir.

Tam koşullar için [LICENSE](LICENSE) dosyasına bakın.

---

## 16. İletişim

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-posta**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
