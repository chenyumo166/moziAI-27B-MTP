---
language:
- id
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

# MoziAI-27B-3.8 — Model AI Multimodal Kecil tapi Hebat, Bisa Dijalankan Lokal Secara Gratis

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | Bahasa Indonesia | [Español](README.es.md) | [Português](README.pt.md) | [العربية](README.ar.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md) | [Polski](README.pl.md)

**Tanggal Rilis: 2026-08-30** · **Versi: V3.8**

---

## 📑 Daftar Isi

- [1. Ikhtisar Model](#1-ikhtisar-model)
- [2. Fitur Utama](#2-fitur-utama) — Pemikiran Tujuh Dimensi Dinamis / LOOP / MoziSmartBit / Fokus Finansial
- [3. Catatan Upgrade Versi](#3-catatan-upgrade-versi)
- [4. Kemampuan Inti](#4-kemampuan-inti)
- [5. Spesifikasi Teknis](#5-spesifikasi-teknis)
- [6. ⚡ Mulai Cepat](#6--mulai-cepat3-file--100-aktifkan-kemampuan-inferensi-terbaik) — **unduh 3 file**
- [7. Unduh Model](#7-unduh-model)
- [8. Perintah Menjalankan](#8-perintah-menjalankan)
- [9. Parameter Inferensi yang Direkomendasikan](#9-parameter-inferensi-yang-direkomendasikan)
- [10. Perbandingan Format Kuantisasi](#10-perbandingan-format-kuantisasi)
- [11. Decoding Spekulatif MTP](#11-decoding-spekulatif-mtp-fitur-akselerasi-penting)
- [12. Rekomendasi Konfigurasi VRAM](#12-rekomendasi-konfigurasi-vram)
- [13. Metode Deployment](#13-metode-deployment)
- [14. Benchmark](#14-benchmark)
- [15. Lisensi](#15-lisensi)
- [16. Kontak](#16-kontak)

---

## 1. Ikhtisar Model

MoziAI-27B-3.8 adalah model AI multimodal open-source yang dapat di-deploy secara lokal, dikembangkan oleh tim Chen Yumo, influencer keuangan ternama China. Dibangun di atas basis open-source **Qwen3.8-27B** (arsitektur Dense 27B, lisensi MIT), menggabungkan data finansial yang dikembangkan sendiri + kemampuan domain finansial + kerangka pemikiran tujuh dimensi dinamis + mekanisme iterasi refleksi LOOP agen + algoritma kuantisasi hibrida MoziSmartBit. Model ini menurunkan hambatan deployment lokal bagi individu dan perusahaan, dilisensikan untuk **penggunaan komersial gratis**, berjalan di GPU konsumen, menghemat biaya token cloud, mewujudkan kebebasan token 7×24 jam dan menjamin privasi serta keamanan data lokal.

---

## 2. Fitur Utama

### 🧠 Kerangka Pemikiran Tujuh Dimensi Dinamis

Kerangka penalaran inti yang dikembangkan sendiri oleh MoziAI. Untuk tugas apa pun, model pertama-tama mengeluarkan penanda **moziAI-Think**, kemudian mengembangkan pemikiran terstruktur secara dinamis berdasarkan kompleksitas tugas:

| Level | Skenario | Tugas Khas | Dimensi yang Dibuka |
| --- | --- | --- | --- |
| **Level 0** | Tanya jawab sederhana | Penjelasan istilah, pencarian fakta, terjemahan, ringkasan | ①Memahami tugas ⑤Kebutuhan sumber daya (jawaban cepat 2 dimensi) |
| **Level 1** | Analisis & diagnosis | Riset pasar, penulisan konten, analisis data, membaca laporan, evaluasi strategi | ①②③⑤⑥ Evaluasi lima dimensi |
| **Level 2** | Pengembangan/strategi kompleks | Pengembangan kode, desain arsitektur, strategi kuant, alur kerja multi-langkah, desain sistem | ①②③④⑤⑥⑦ Penalaran mendalam penuh tujuh dimensi |

> Tujuh dimensi: ①Memahami tugas ②Menilai kompleksitas ③Hubungan ketergantungan ④Menilai risiko ⑤Kebutuhan sumber daya ⑥Kriteria penerimaan ⑦Strategi eksekusi

### 🔄 Mekanisme Iterasi LOOP Agen

Tugas kompleks otomatis masuk ke mode iterasi **moziAI-Loop**: **Putaran 1 eksekusi + evaluasi → Putaran 2 penyesuaian + verifikasi**, memastikan output melewati validasi mandiri sebelum memberikan jawaban akhir. Model bekerja seperti insinyur senior: «memecah masalah → mengevaluasi solusi → mengeksekusi → merefleksi → mengoptimalkan», meningkatkan akurasi dan keterlaksanaan tugas kompleks secara signifikan. Tanya jawab dan tugas sederhana otomatis menonaktifkan Loop.

### 📦 Kuantisasi Cerdas MoziSmartBit

Kuantisasi berlapis cerdas yang dikembangkan sendiri: model Dense 27 miliar parameter dikompresi menjadi sekitar **13,7 GB**, sekitar 3,3 GB (~20%) lebih kecil dari Q4_K_M standar (~17 GB), dengan mempertahankan akurasi **~99%** FP16. Kuantisasi tradisional menerapkan presisi seragam ke semua lapisan; MoziSmartBit menggunakan strategi diferensiasi cerdas yang disesuaikan dengan struktur Dense, dengan akurasi lebih baik dari Q4_K_M.

### 💰 Fokus Domain Finansial Vertikal

Optimasi mendalam untuk tanya jawab finansial, pemrograman kuantitatif, dan pemanggilan alat. Domain finansial memiliki toleransi sangat rendah terhadap halusinasi model, dan MoziAI menunjukkan kinerja jauh lebih baik daripada model umum berukuran sama di domain ini.

### 🌐 Fitur Lainnya

- **Dukungan multibahasa**: 201 bahasa dan dialek, dengan optimasi khusus untuk bahasa Mandarin
- **Pemrograman umum**: pengembangan full-stack, debugging kode, desain arsitektur, mencakup Python/JS/TS/Go/Rust
- **Penulisan artikel**: penulisan berkualitas tinggi multi-genre seperti laporan riset, artikel analisis, dokumen teknis, konten kreatif
- **Pemahaman visual**: visi multimodal, mendukung pemahaman konten gambar dari screenshot lokal
- **Dukungan multi-framework**: llama.cpp / Ollama / LM Studio / Jan
- **Dukungan multi-Agent**: OpenClaw / Hermes / Cursor / Claude Code / Codex, dengan pemanggilan alat native dan orkestrasi tugas multi-putaran

---

## 3. Catatan Upgrade Versi

Upgrade ini terutama memperkuat: mode penalaran «pemikiran tujuh dimensi dinamis + iterasi LOOP» yang dikembangkan sendiri oleh moziAI, membuatnya lebih cerdas mengenali kompleksitas tugas, tingkat penyelesaian tugas kompleks lebih tinggi, meningkatkan kemampuan «berpikir dulu, baru bertindak».

moziAI akan menjaga frekuensi pembaruan versi yang aktif, memastikan mengikuti perkembangan AI masa depan, dan terus melalui teknologi sendiri membuat model AI lokal lebih ringan untuk di-deploy dan semakin mampu.

---

## 4. Kemampuan Inti

| Bidang Kemampuan | Deskripsi |
| --- | --- |
| Analisis Pasar | Interpretasi ekonomi makro/mikro, analisis pasar A/HK/US/komoditas/kripto dan logikanya |
| Keuangan & Laporan | Interpretasi indikator kunci laporan keuangan, ekstraksi ringkasan riset, bantuan valuasi & proyeksi laba |
| Risiko & Kepatuhan | Penilaian risiko produk, pengingat kepatuhan saran investasi, interpretasi kebijakan regulasi finansial |
| Kuant & Strategi | Desain ide strategi kuantitatif, kuantisasi Pyramid (PEL), logika backtest, konstruksi faktor & pemanggilan alat |
| Pemanggilan Alat | Terhubung ke sumber data pasar real-time, database, pencarian riset finansial |

---

## 5. Spesifikasi Teknis

| Item | Spesifikasi |
| --- | --- |
| Model Dasar | Qwen3.8-27B (arsitektur Dense, perhatian hibrida 16 full + 48 linear, lisensi MIT) |
| Ukuran Parameter | 27 miliar (27B) arsitektur Dense |
| Metode Kuantisasi | Kuantisasi cerdas MoziSmartBit + format standar GGUF |
| Panjang Konteks | 128K (262.144 token) |
| Ukuran Model | ~13,7 GB |
| VRAM Minimum | **16GB+** dapat di-deploy (offload CPU); **20GB+** konteks panjang lancar; **24GB+** 128K penuh + visi |
| Framework Inferensi | llama.cpp / Ollama / LM Studio / Jan |
| Kecepatan Inferensi | Dengan decoding spekulatif MTP: R9700 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Tim Pengembang | Tim Chen Yumo |

---

## 6. ⚡ Mulai Cepat (3 File = 100% Aktivasi Kemampuan Inferensi Terbaik)

> ⚠️ **Poin Penting**: Kemampuan inferensi terbaik MoziAI memerlukan **unduh 3 file sekaligus** — model utama, proyektor visi, template chat. Kehilangan salah satu akan mengurangi kemampuan terkait.

### 6.1 Unduh File Model

Unduh **semua file di direktori V3.8** dari HuggingFace / ModelScope ke direktori lokal yang sama:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Model utama (wajib, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Template chat (wajib, berisi instruksi pemikiran + Loop)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Proyektor visi (wajib, 927 MB)
```

| File | Ukuran | Kebutuhan | Fungsi |
| --- | --- | --- | --- |
| Model utama `.gguf` | ~13,7 GB | **Wajib** | Bobot model, kemampuan inferensi inti |
| Proyektor visi `mmproj` | ~927 MB | **Wajib** | Pemahaman visual multimodal, tanpa ini kehilangan kemampuan gambar |
| Template chat `.jinja` | Sangat kecil | **Wajib** | Menyuntikkan identitas MoziAI + instruksi pemikiran tujuh dimensi + mekanisme LOOP |

### 6.2 Menjalankan dan Menggunakan

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Buka `http://localhost:8080` di browser untuk memulai percakapan. Parameter lengkap yang direkomendasikan ada di Bagian 9.

---

## 7. Unduh Model

| Platform | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP) |

> 💡 **Pengguna LM Studio**: cari `moziAI` di [LM Studio](https://lmstudio.ai) untuk unduh sekali klik, tanpa perlu mengunduh file manual.

---

## 8. Perintah Menjalankan

### Menjalankan Paling Sederhana (dengan 3 file)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Menjalankan Penuh yang Direkomendasikan

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

> 💡 Untuk menonaktifkan MTP: hapus `--spec-type draft-mtp` dan parameter terkait; kecepatan ~30-50% lebih lambat, penggunaan VRAM lebih kecil.

---

## 9. Parameter Inferensi yang Direkomendasikan

Berdasarkan parameter resmi llama.cpp dan optimasi lokal (AMD Radeon AI PRO R9700 32GB):

| Parameter | Chat umum | Coding/Agent | Keterangan |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Keseimbangan kreativitas dan akurasi |
| top\_p | 0,95 | 0,95 | Ambang sampling nukleus |
| top\_k | 20 | 20 | Sampling terpotong |
| repeat\_penalty | 1,05 | 1,05 | Penalti pengulangan |
| context\_length | 262144 | 262144 | Konteks panjang 128K |
| reasoning | auto | auto | Aktifkan rantai penalaran (CoT) |
| reasoning\_budget | 400 | 400 | Anggaran token penalaran |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Output penalaran ke field terpisah |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Decoding spekulatif MTP (lihat Bagian 11)** |

> 💡 **Mode berpikir**: diaktifkan via `--reasoning auto` — model menalar secara internal sebelum menjawab. `reasoning_budget` membatasi token berpikir maksimum (disarankan 400, dapat disesuaikan 100-1000).

---

## 10. Perbandingan Format Kuantisasi

| Format | Ukuran | Akurasi | Keterangan |
| --- | --- | --- | --- |
| FP16 asli | ~54 GB | 100% | Tanpa loss, butuh GPU profesional |
| **MoziSmartBit (model ini)** | **~13,7 GB** | **~99%** | **Kuantisasi cerdas buatan sendiri, akurasi terbaik per ukuran** |
| Q4_K_M | ~17 GB | ~98% | GGUF standar 4-bit |
| Q5_K_M | ~20 GB | ~99% | Akurasi lebih tinggi |
| Q6_K | ~23 GB | ~99,5% | Hampir tanpa loss |
| Q8_0 | ~31 GB | ~100% | Tanpa loss |

> MoziSmartBit mempertahankan akurasi ~99% sambil mengompresi model Dense 27B menjadi 13,7 GB (rasio kompresi 3,9x), ~20% lebih kecil dari Q4_K_M — ideal untuk GPU konsumen.

---

## 11. Decoding Spekulatif MTP (Fitur Akselerasi Penting)

Model ini memiliki lapisan decoding spekulatif MTP (Multi-Token Prediction), yang meningkatkan kecepatan inferensi **1,5-2 kali** saat diaktifkan. Ini adalah fitur asli arsitektur Qwen3.8; MoziAI mempertahankan bobot MTP lengkap.

**Prinsip**: kepala prediksi ringan (Draft Model) dilatih dalam arsitektur untuk menebak token berikutnya sebelum verifikasi model utama, mengurangi forward pass dan latensi. Kesalahan tebakan dikoreksi oleh model utama, tanpa dampak negatif pada kualitas output.

### Parameter Aktivasi

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Parameter | Nilai yang Direkomendasikan | Keterangan |
| --- | --- | --- |
| --spec-type | draft-mtp | Mengaktifkan decoding spekulatif MTP |
| --spec-draft-n-max | 2 | Maksimal 2 token ditebak per langkah (disarankan, tingkat penerimaan ~80%) |
| --spec-draft-p-min | 0,75 | Ambang probabilitas penerimaan minimum (0,0-1,0, lebih besar = lebih konservatif) |

### Saran Penyesuaian

| n-max | Tingkat Penerimaan | Skenario |
| --- | --- | --- |
| 1 | ~90% | Paling konservatif, peningkatan kecepatan terkecil |
| **2** | **~80%** | **Disarankan: keseimbangan kecepatan dan akurasi** |
| 3 | ~71% | Skenario umum, peningkatan kecepatan nyata |
| 4-5 | ~60-65% | Penulisan kreatif, generasi kode |
| 6 | ~50-55% | Output teks panjang (perlu penyesuaian p-min) |

---

## 12. Rekomendasi Konfigurasi VRAM

| VRAM | Konfigurasi yang Direkomendasikan | Keterangan |
| --- | --- | --- |
| 16 GB | Konteks turun ke 64K, perlu offload CPU | Level pemula, mis. RTX 4060 Ti |
| **20 GB** | **128K penuh, cache KV q4_0** | **Konfigurasi yang direkomendasikan**, mis. RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K penuh, sisa VRAM cukup | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K penuh, konfigurasi terkuat | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 128K penuh | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Semakin panjang konteks, semakin banyak VRAM yang digunakan. Saat OOM turunkan `-c` bertahap. Gunakan `--fit on` agar llama.cpp menyesuaikan jumlah lapisan otomatis. Mendukung semua kartu NVIDIA / AMD / Intel.

---

## 13. Metode Deployment

### Deployment Ollama

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

Cari `moziAI` di LM Studio / Jan, pilih versi kuantisasi Q4\_K\_M untuk diunduh.

> 💡 Dukungan Ollama untuk mmproj dan chat\_template terbatas, disarankan menggunakan llama.cpp terlebih dahulu untuk fungsionalitas lengkap.

---

## 14. Benchmark

MoziAI-27B-3.8 didasarkan pada fine-tuning dari basis Qwen3.8-27B, dengan domain finansial vertikal sebagai arah optimasi inti.

### Kemampuan Coding

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Kemampuan Agen

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Kemampuan Umum

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Kemampuan Multimodal

| Benchmark | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Data pesaing adalah hasil evaluasi resmi yang dipublikasikan. Domain finansial vertikal MoziAI (interpretasi laporan keuangan, strategi kuant, kepatuhan manajemen risiko, pemanggilan alat agen) jauh lebih unggul daripada model umum.

---

## 15. Lisensi

Model ini menggunakan **lisensi restriktif kustom**:

- ✅ **Diizinkan** — penggunaan komersial gratis, menyalin dan mendistribusikan
- ❌ **Dilarang** — pengembangan lanjutan, penjualan ulang, sub-lisensi
- 📋 **Diwajibkan** — mempertahankan pemberitahuan hak cipta asli, mencantumkan sumber: moziAI-27B

Model disediakan "sebagaimana adanya" tanpa jaminan apa pun. Output model hanya untuk referensi dan tidak merupakan saran investasi. Pengguna menanggung semua risiko.

Lihat file [LICENSE](LICENSE) untuk ketentuan lengkap.

---

## 16. Kontak

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
