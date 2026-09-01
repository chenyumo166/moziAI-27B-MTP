---
language:
- vi
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

# MoziAI-27B-3.8 — Mô hình AI đa phương thức nhỏ gọn nhưng mạnh mẽ, triển khai cục bộ miễn phí

[English](README.en.md) | [简体中文](README.zh.md) | [繁體中文](README.zh-hant.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [हिन्दी](README.hi.md) | [Deutsch](README.de.md) | [Français](README.fr.md) | [Nederlands](README.nl.md) | [Italiano](README.it.md) | [Русский](README.ru.md) | Tiếng Việt | [Español](README.es.md) | [Português](README.pt.md) | [العربية](README.ar.md) | [Bahasa Indonesia](README.id.md) | [Türkçe](README.tr.md) | [Polski](README.pl.md)

**Ngày phát hành: 2026-08-30** · **Phiên bản: V3.8**

---

## 📑 Mục lục

- [1. Tổng quan mô hình](#1-tổng-quan-mô-hình)
- [2. Tính năng chính](#2-tính-năng-chính) — Tư duy bảy chiều động / LOOP / MoziSmartBit / Trọng tâm tài chính
- [3. Ghi chú nâng cấp phiên bản](#3-ghi-chú-nâng-cấp-phiên-bản)
- [4. Năng lực cốt lõi](#4-năng-lực-cốt-lõi)
- [5. Thông số kỹ thuật](#5-thông-số-kỹ-thuật)
- [6. ⚡ Bắt đầu nhanh](#6--bắt-đầu-nhanh3-tệp--100-kích-hoạt-năng-lực-suy-luận-tốt-nhất) — **tải 3 tệp**
- [7. Tải mô hình](#7-tải-mô-hình)
- [8. Lệnh khởi chạy](#8-lệnh-khởi-chạy)
- [9. Tham số suy luận được khuyến nghị](#9-tham-số-suy-luận-được-khuyến-nghị)
- [10. So sánh định dạng lượng tử hóa](#10-so-sánh-định-dạng-lượng-tử-hóa)
- [11. Giải mã suy đoán MTP](#11-giải-mã-suy-đoán-mtp-tính-năng-tăng-tốc-quan-trọng)
- [12. Khuyến nghị cấu hình VRAM](#12-khuyến-nghị-cấu-hình-vram)
- [13. Phương pháp triển khai](#13-phương-pháp-triển-khai)
- [14. Điểm chuẩn](#14-điểm-chuẩn)
- [15. Giấy phép](#15-giấy-phép)
- [16. Liên hệ](#16-liên-hệ)

---

## 1. Tổng quan mô hình

MoziAI-27B-3.8 là mô hình AI đa phương thức mã nguồn mở có thể triển khai cục bộ, được phát triển bởi đội ngũ của Chen Yumo, nhà ảnh hưởng tài chính hàng đầu Trung Quốc. Được xây dựng trên nền tảng mã nguồn mở **Qwen3.8-27B** (kiến trúc Dense 27B, giấy phép MIT), kết hợp dữ liệu tài chính tự phát triển + năng lực lĩnh vực tài chính + khung tư duy bảy chiều động + cơ chế lặp phản ánh LOOP của agent + thuật toán lượng tử hóa lai MoziSmartBit. Mô hình này giảm rào cản triển khai cục bộ cho cá nhân và doanh nghiệp, được cấp phép **sử dụng thương mại miễn phí**, chạy trên GPU tiêu dùng, tiết kiệm chi phí token đám mây, mang lại tự do token 7×24 giờ và đảm bảo quyền riêng tư cùng bảo mật dữ liệu cục bộ.

---

## 2. Tính năng chính

### 🧠 Khung tư duy bảy chiều động

Khung suy luận cốt lõi do MoziAI tự phát triển. Với bất kỳ nhiệm vụ nào, mô hình trước tiên xuất ra dấu hiệu **moziAI-Think**, sau đó mở rộng tư duy có cấu trúc một cách động theo độ phức tạp của nhiệm vụ:

| Cấp độ | Tình huống | Nhiệm vụ điển hình | Chiều mở rộng |
| --- | --- | --- | --- |
| **Cấp 0** | Hỏi đáp đơn giản | Giải thích thuật ngữ, tra cứu sự kiện, dịch thuật, tóm tắt | ①Hiểu nhiệm vụ ⑤Nhu cầu tài nguyên (trả lời nhanh 2 chiều) |
| **Cấp 1** | Phân tích & chẩn đoán | Nghiên cứu thị trường, viết nội dung, phân tích dữ liệu, đọc báo cáo, đánh giá chiến lược | ①②③⑤⑥ Đánh giá năm chiều |
| **Cấp 2** | Phát triển/chiến lược phức tạp | Phát triển mã, thiết kế kiến trúc, phát triển chiến lược định lượng, quy trình nhiều bước, thiết kế hệ thống | ①②③④⑤⑥⑦ Suy luận sâu đầy đủ bảy chiều |

> Bảy chiều: ①Hiểu nhiệm vụ ②Đánh giá độ phức tạp ③Mối quan hệ phụ thuộc ④Đánh giá rủi ro ⑤Nhu cầu tài nguyên ⑥Tiêu chí nghiệm thu ⑦Chiến lược thực thi

### 🔄 Cơ chế lặp LOOP của Agent

Nhiệm vụ phức tạp tự động vào chế độ lặp **moziAI-Loop**: **Vòng 1 thực thi + đánh giá → Vòng 2 điều chỉnh + xác minh**, đảm bảo đầu ra trải qua tự kiểm chứng trước khi đưa ra câu trả lời cuối cùng. Mô hình hoạt động như kỹ sư cao cấp: «phân rã vấn đề → đánh giá giải pháp → thực thi → phản ánh → tối ưu hóa», nâng cao đáng kể độ chính xác và khả năng thực thi của nhiệm vụ phức tạp. Hỏi đáp và nhiệm vụ đơn giản tự động tắt Loop.

### 📦 Lượng tử hóa thông minh MoziSmartBit

Lượng tử hóa thông minh phân lớp tự phát triển: mô hình Dense 27 tỷ tham số được nén xuống khoảng **13,7 GB**, nhỏ hơn khoảng 3,3 GB (~20%) so với Q4_K_M tiêu chuẩn (~17 GB), duy trì độ chính xác **~99%** FP16. Lượng tử hóa truyền thống áp dụng độ chính xác đồng nhất cho tất cả các lớp; MoziSmartBit sử dụng chiến lược khác biệt thông minh phù hợp với cấu trúc Dense, có độ chính xác tốt hơn Q4_K_M.

### 💰 Trọng tâm lĩnh vực tài chính dọc

Tối ưu sâu cho hỏi đáp tài chính, lập trình định lượng và gọi công cụ. Lĩnh vực tài chính có khả năng chịu đựng rất thấp với ảo giác của mô hình, và MoziAI thể hiện hiệu suất vượt trội so với các mô hình tổng quát cùng kích thước trong lĩnh vực này.

### 🌐 Tính năng khác

- **Hỗ trợ đa ngôn ngữ**: 201 ngôn ngữ và phương ngữ, tiếng Trung được tối ưu đặc biệt
- **Lập trình tổng quát**: phát triển full-stack, gỡ lỗi mã, thiết kế kiến trúc, bao phủ Python/JS/TS/Go/Rust
- **Viết bài**: viết chất lượng cao đa thể loại như báo cáo nghiên cứu, bài phân tích, tài liệu kỹ thuật, nội dung sáng tạo
- **Hiểu thị giác**: thị giác đa phương thức, hỗ trợ hiểu nội dung ảnh qua ảnh chụp màn hình cục bộ
- **Hỗ trợ đa khung**: llama.cpp / Ollama / LM Studio / Jan
- **Hỗ trợ đa Agent**: OpenClaw / Hermes / Cursor / Claude Code / Codex..., gọi công cụ gốc và điều phối nhiệm vụ nhiều vòng

---

## 3. Ghi chú nâng cấp phiên bản

Bản nâng cấp này chủ yếu củng cố: chế độ suy luận «tư duy bảy chiều động + lặp LOOP» do moziAI tự phát triển, giúp nhận diện độ phức tạp nhiệm vụ thông minh hơn, tỷ lệ hoàn thành nhiệm vụ phức tạp cao hơn, nâng cao khả năng «suy nghĩ trước, hành động sau».

moziAI duy trì tần suất nâng cấp phiên bản tích cực, đảm bảo theo kịp sự phát triển AI tương lai, và không ngừng thông qua công nghệ tự phát triển làm cho mô hình AI cục bộ triển khai nhẹ nhàng hơn, năng lực ngày càng mạnh.

---

## 4. Năng lực cốt lõi

| Lĩnh vực năng lực | Mô tả |
| --- | --- |
| Phân tích thị trường | Giải thích kinh tế vĩ mô/vi mô, phân tích thị trường A/HK/US/hàng hóa/tiền mã hóa và logic |
| Tài chính & báo cáo | Giải thích chỉ số chính báo cáo tài chính, trích xuất tóm tắt báo cáo nghiên cứu, hỗ trợ định giá & dự báo lợi nhuận |
| Rủi ro & tuân thủ | Đánh giá rủi ro sản phẩm, nhắc tuân thủ lời khuyên đầu tư, giải thích chính sách quản lý tài chính |
| Định lượng & chiến lược | Thiết kế ý tưởng chiến lược định lượng, lượng tử hóa Pyramid (PEL), logic backtest, xây dựng yếu tố & gọi công cụ |
| Gọi công cụ | Kết nối nguồn dữ liệu thị trường thời gian thực, cơ sở dữ liệu, tìm kiếm báo cáo tài chính |

---

## 5. Thông số kỹ thuật

| Mục | Thông số |
| --- | --- |
| Mô hình nền tảng | Qwen3.8-27B (kiến trúc Dense, chú ý lai 16 full + 48 linear, giấy phép MIT) |
| Quy mô tham số | 27 tỷ (27B) kiến trúc Dense |
| Phương thức lượng tử hóa | Lượng tử hóa thông minh MoziSmartBit + định dạng chuẩn GGUF |
| Độ dài ngữ cảnh | 128K (262.144 token) |
| Kích thước mô hình | ~13,7 GB |
| VRAM tối thiểu | **16GB+** triển khai được (offload CPU); **20GB+** ngữ cảnh dài mượt mà; **24GB+** 128K đầy đủ + thị giác |
| Khung suy luận | llama.cpp / Ollama / LM Studio / Jan |
| Tốc độ suy luận | Với giải mã suy đoán MTP: R9700 70+ tok/s, MAX+395 iGPU 50+ tok/s, GPU 35+ tok/s |
| Đội phát triển | Đội ngũ Chen Yumo |

---

## 6. ⚡ Bắt đầu nhanh (3 tệp = 100% kích hoạt năng lực suy luận tốt nhất)

> ⚠️ **Lưu ý cốt lõi**: Năng lực suy luận tốt nhất của MoziAI yêu cầu **tải đồng thời 3 tệp** — mô hình chính, máy chiếu thị giác, mẫu trò chuyện. Thiếu bất kỳ tệp nào sẽ mất năng lực tương ứng.

### 6.1 Tải tệp mô hình

Tải **tất cả tệp trong thư mục V3.8** từ HuggingFace / ModelScope vào cùng thư mục cục bộ:

```
V3.8/
├── moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf   ← Mô hình chính (bắt buộc, 13,7 GB)
└── chat-template-moziai-27B-V3.8.jinja         ← Mẫu trò chuyện (bắt buộc, chứa hướng dẫn tư duy+Loop)

mmproj/27B/
└── moziAI-27B-mmproj-BF16-V1.0.gguf           ← Máy chiếu thị giác (bắt buộc, 927 MB)
```

| Tệp | Kích thước | Tính cần thiết | Chức năng |
| --- | --- | --- | --- |
| Mô hình chính `.gguf` | ~13,7 GB | **Bắt buộc** | Trọng số mô hình, năng lực suy luận cốt lõi |
| Máy chiếu thị giác `mmproj` | ~927 MB | **Bắt buộc** | Hiểu thị giác đa phương thức, không tải sẽ mất khả năng hình ảnh |
| Mẫu trò chuyện `.jinja` | Rất nhỏ | **Bắt buộc** | Tiêm nhận dạng MoziAI + hướng dẫn tư duy bảy chiều + cơ chế LOOP |

### 6.2 Khởi chạy và sử dụng

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

Mở `http://localhost:8080` trong trình duyệt để bắt đầu trò chuyện. Tham số đầy đủ khuyến nghị ở Mục 9.

---

## 7. Tải mô hình

| Nền tảng | URL |
| --- | --- |
| HuggingFace | [chenyumo/moziAI-27B-MTP](https://huggingface.co/chenyumo/moziAI-27B-MTP) |
| ModelScope | [chenyumo/moziAI-27B-MTP](https://modelscope.cn/models/chenyumo/moziAI-27B-MTP) |
| GitHub | [chenyumo166/moziAI-27B-MTP](https://github.com/chenyumo166/moziAI-27B-MTP) |

> 💡 **Người dùng LM Studio**: tìm `moziAI` trong [LM Studio](https://lmstudio.ai) để tải một chạm, không cần tải tệp thủ công.

---

## 8. Lệnh khởi chạy

### Khởi chạy tối giản (với 3 tệp)

```bash
llama-server \
  -m ./moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf \
  --mmproj mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf \
  --chat-template-file V3.8/chat-template-moziai-27B-V3.8.jinja \
  -c 131072 -ngl 99 \
  --host 0.0.0.0 --port 8080
```

### Khởi chạy đầy đủ khuyến nghị

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

> 💡 Để tắt MTP: xóa `--spec-type draft-mtp` và các tham số liên quan; tốc độ giảm ~30-50%, VRAM sử dụng ít hơn.

---

## 9. Tham số suy luận được khuyến nghị

Dựa trên tham số khuyến nghị chính thức của llama.cpp và tối ưu cục bộ (AMD Radeon AI PRO R9700 32GB):

| Tham số | Chat tổng quát | Coding/Agent | Ghi chú |
| --- | --- | --- | --- |
| temperature | 0,7 | 1,0 | Cân bằng sáng tạo và chính xác |
| top\_p | 0,95 | 0,95 | Ngưỡng lấy mẫu hạt nhân |
| top\_k | 20 | 20 | Lấy mẫu cắt ngắn |
| repeat\_penalty | 1,05 | 1,05 | Phạt lặp lại |
| context\_length | 262144 | 262144 | Ngữ cảnh dài 128K |
| reasoning | auto | auto | Bật chuỗi suy luận (CoT) |
| reasoning\_budget | 400 | 400 | Ngân sách token suy luận |
| reasoning\_format | deepseek-legacy | deepseek-legacy | Xuất suy luận sang trường riêng |
| **spec-type** | **draft-mtp** | **draft-mtp** | **Giải mã suy đoán MTP (xem Mục 11)** |

> 💡 **Chế độ suy nghĩ**: bật qua `--reasoning auto` — mô hình suy luận nội bộ trước khi trả lời. `reasoning_budget` giới hạn số token suy nghĩ tối đa (khuyến nghị 400, điều chỉnh 100-1000).

---

## 10. So sánh định dạng lượng tử hóa

| Định dạng | Kích thước | Độ chính xác | Ghi chú |
| --- | --- | --- | --- |
| FP16 gốc | ~54 GB | 100% | Không mất mát, cần GPU chuyên nghiệp |
| **MoziSmartBit (mô hình này)** | **~13,7 GB** | **~99%** | **Lượng tử hóa thông minh tự phát triển, độ chính xác tốt nhất trên mỗi kích thước** |
| Q4_K_M | ~17 GB | ~98% | GGUF chuẩn 4-bit |
| Q5_K_M | ~20 GB | ~99% | Độ chính xác cao hơn |
| Q6_K | ~23 GB | ~99,5% | Gần như không mất mát |
| Q8_0 | ~31 GB | ~100% | Không mất mát |

> MoziSmartBit giữ ~99% độ chính xác trong khi nén mô hình Dense 27B xuống 13,7 GB (tỷ lệ nén 3,9x), nhỏ hơn ~20% so với Q4_K_M — lý tưởng cho GPU tiêu dùng.

---

## 11. Giải mã suy đoán MTP (Tính năng tăng tốc quan trọng)

Mô hình này có lớp giải mã suy đoán MTP (Multi-Token Prediction), tăng tốc độ suy luận **1,5-2 lần** khi bật. Đây là tính năng gốc của kiến trúc Qwen3.8; MoziAI giữ nguyên trọng số MTP đầy đủ.

**Nguyên lý**: một đầu dự đoán nhẹ (Draft Model) được huấn luyện trong kiến trúc để đoán token tiếp theo trước khi mô hình chính xác minh, giảm số lần forward và độ trễ. Lỗi đoán được mô hình chính sửa, không ảnh hưởng tiêu cực đến chất lượng đầu ra.

### Tham số kích hoạt

```bash
--spec-type draft-mtp \
--spec-draft-n-max 2 \
--spec-draft-p-min 0.75
```

| Tham số | Giá trị khuyến nghị | Mô tả |
| --- | --- | --- |
| --spec-type | draft-mtp | Kích hoạt giải mã suy đoán MTP |
| --spec-draft-n-max | 2 | Tối đa 2 token đoán mỗi bước (khuyến nghị, tỷ lệ chấp nhận ~80%) |
| --spec-draft-p-min | 0,75 | Ngưỡng xác suất chấp nhận tối thiểu (0,0-1,0, lớn hơn = thận trọng hơn) |

### Gợi ý điều chỉnh

| n-max | Tỷ lệ chấp nhận | Tình huống |
| --- | --- | --- |
| 1 | ~90% | Thận trọng nhất, tăng tốc ít nhất |
| **2** | **~80%** | **Khuyến nghị: cân bằng tốc độ và độ chính xác** |
| 3 | ~71% | Tình huống chung, tăng tốc rõ rệt |
| 4-5 | ~60-65% | Viết sáng tạo, tạo mã |
| 6 | ~50-55% | Đầu ra văn bản dài (cần điều chỉnh p-min) |

---

## 12. Khuyến nghị cấu hình VRAM

| VRAM | Cấu hình khuyến nghị | Mô tả |
| --- | --- | --- |
| 16 GB | Ngữ cảnh giảm xuống 64K, cần offload CPU | Cấp nhập môn, ví dụ RTX 4060 Ti |
| **20 GB** | **128K đầy đủ, bộ nhớ đệm KV q4_0** | **Cấu hình khuyến nghị**, ví dụ RX 7900 XT / RTX 5070 Ti |
| 24 GB | 128K đầy đủ, dư VRAM đủ | RTX 4090 / RX 7900 XTX |
| 32 GB+ | 128K đầy đủ, cấu hình mạnh nhất | Radeon AI PRO R9700 / RTX 5090 |
| 128 GB iGPU | 128K đầy đủ | AMD Ryzen AI Max+ 395 / NVIDIA RTX Spark |

> 💡 Ngữ cảnh càng dài, VRAM càng nhiều. Khi OOM giảm `-c` dần. Dùng `--fit on` để llama.cpp tự điều chỉnh số lớp. Hỗ trợ NVIDIA / AMD / Intel.

---

## 13. Phương pháp triển khai

### Triển khai Ollama

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

Tìm `moziAI` trong LM Studio / Jan, chọn phiên bản lượng tử hóa Q4\_K\_M để tải.

> 💡 Hỗ trợ của Ollama cho mmproj và chat\_template còn hạn chế, khuyến nghị ưu tiên llama.cpp để có đầy đủ chức năng.

---

## 14. Điểm chuẩn

MoziAI-27B-3.8 dựa trên tinh chỉnh từ nền tảng Qwen3.8-27B, với lĩnh vực tài chính dọc là hướng tối ưu cốt lõi.

### Năng lực lập trình

| Điểm chuẩn | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| Terminal Bench 2.1 | 73.0 | 63.4 | 64.0 | 78.2 |
| SWE-bench Pro | **61.7** | 53.5 | 57.6 | 53.4 |
| DeepSWE 1.1 | **42.2** | 13.3 | 14.2 | -- |
| QwenSWEBench | **79.0** | 49.3 | 59.2 | 63.8 |

### Năng lực Agent

| Điểm chuẩn | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| CoWorkBench | **70.7** | 61.0 | 65.1 | 68.2 |
| JobBench | **33.4** | 21.8 | 27.6 | -- |
| Agents' Last Exam | **42.9** | 27.3 | 33.6 | -- |
| WebArena-Verified | **64.8** | 48.8 | 55.3 | -- |
| AndroidWorld | **81.9** | 70.3 | 81.0 | 62.0 |

### Năng lực tổng quát

| Điểm chuẩn | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| IFBench | **79.5** | 69.1 | 79.1 | 62.5 |
| GPQA Diamond | 89.2 | 87.8 | 90.3 | **91.3** |

### Năng lực đa phương thức

| Điểm chuẩn | moziAI-27B | Qwen3.6-27B | Qwen3.7-Plus | Opus4.6 Max |
| --- | --- | --- | --- | --- |
| MathVision | **94.6** | 85.1 | 90.3 | 65.5 |
| BabyVision | **85.6** | 28.9 | 70.4 | 12.6 |
| CharXiv RQ | **90.2** | 78.4 | 85.8 | 66.0 |
| Vision2Web | **62.9** | 45.0 | 42.1 | -- |

> Dữ liệu đối thủ là kết quả đánh giá chính thức công bố. Lĩnh vực tài chính dọc của MoziAI (giải thích báo cáo tài chính, chiến lược định lượng, tuân thủ quản lý rủi ro, gọi công cụ agent) vượt trội rõ rệt so với mô hình tổng quát.

---

## 15. Giấy phép

Mô hình này sử dụng **giấy phép hạn chế tùy chỉnh**:

- ✅ **Được phép** — sử dụng thương mại miễn phí, sao chép và phân phối
- ❌ **Bị cấm** — phát triển thêm, bán lại, cấp phép phụ
- 📋 **Yêu cầu** — giữ thông báo bản quyền gốc, ghi nguồn: moziAI-27B

Mô hình được cung cấp \"nguyên trạng\" không kèm bất kỳ bảo hành nào. Đầu ra mô hình chỉ để tham khảo và không cấu thành lời khuyên đầu tư. Người dùng tự chịu mọi rủi ro.

Xem tệp [LICENSE](LICENSE) để biết điều khoản đầy đủ.

---

## 16. Liên hệ

- **HuggingFace**: [@chenyumo](https://huggingface.co/chenyumo)
- **GitHub**: [@chenyumo166](https://github.com/chenyumo166)
- **Weibo**: [@rimochen](https://weibo.com/rimochen)
- **E-mail**: 263515@qq.com

Copyright (c) 2026 陈雨墨 / chenyumo166. All rights reserved.
