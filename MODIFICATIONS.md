# Modifications Notice / 修改声明

本文件依据 **Apache License, Version 2.0 第 4(b) 条** 的要求发布：
分发衍生作品时，必须使任何被修改的文件带有显著声明，说明该文件已被修改。

This file is published to satisfy **Apache License, Version 2.0,
Section 4(b)**, which requires that any modified files carry prominent
notices stating that they were changed.

---

## 1. 原始作品 / Original work

| 项目 | 内容 |
|---|---|
| 上游基底模型 | Qwen3.8-27B（Dense） |
| 上游许可 | Apache License, Version 2.0 |
| 本作品 | MoziAI-27B-MTP（moziAI-27B-V3.8） |
| 修改人 | Chen Yumo / 陈雨墨 / chenyumo166 |
| 修改时间 | 2026-08-10 ~ 2026-09-01 |

---

## 2. 修改内容 / What was changed

MoziAI 团队对原始作品进行了以下修改：

The MoziAI team made the following changes to the original work:

1. **继续训练 / 微调** — 在金融领域数据上进行继续预训练与监督微调
   **Continued training / fine-tuning** — continued pre-training and
   supervised fine-tuning on financial-domain data.
2. **重新量化** — 使用自研 MoziSmartBit 智能量化算法对权重重新量化
   （Q4_K_M 级别，GGUF 格式）
   **Requantization** of the weights with the MoziAI-developed
   MoziSmartBit smart quantization algorithm (Q4_K_M class, GGUF).
3. **保留 MTP 权重** — 完整保留 Qwen3.8 架构原生 MTP
   （Multi-Token Prediction）推测解码层
   **MTP weights preserved** — the native MTP (Multi-Token Prediction)
   speculative decoding layer of the Qwen3.8 architecture is fully
   preserved.
4. **对话模板** — 新增自定义 chat template，注入 MoziAI 身份标识、
   动态七维思考指令与 LOOP 迭代指令
   **Chat template** — added a custom chat template injecting the MoziAI
   identity marker, seven-dimensional thinking instructions and LOOP
   iteration instructions.
5. **视觉投影器** — 新增 mmproj 视觉投影器文件
   **Vision projector** — added mmproj projector artifacts.
6. **文档与脚手架** — 新增/改写 README、docs、发布脚本
   **Documentation and scaffolding** — added/rewrote README, docs and
   release scripts.

---

## 3. 被修改 / 新增的文件清单 / Modified & added files

| 文件 | 状态 |
|---|---|
| `moziAI-27B-MTP-V3.8-Q4_K_M-Qwen3.8-27B.gguf` | 由上游权重**修改**（继续训练 + 重新量化） |
| `mmproj/27B/moziAI-27B-mmproj-BF16-V1.0.gguf` | **新增** |
| `V3.8/chat-template-moziai-27B-V3.8.jinja` | **新增** |
| `README.md`、`README.modelscope.md`、`V3.8/README.*.md` | **新增/改写** |
| `LICENSE.md`、`LICENSE-APACHE`、`NOTICE` | **新增/改写** |

---

## 4. 未修改的上游权利 / Upstream rights not modified

本声明仅记录 MoziAI 团队的修改行为，**不改变**任何上游组件的许可状态。
继承自 Qwen 的组件持续受 **Apache License, Version 2.0** 约束，
见 `LICENSE-APACHE`；上游版权与归属声明见 `NOTICE`。

This statement only records the MoziAI team's modifications. It does
**not** alter the license status of any upstream component. The
inherited Qwen components remain governed by **Apache License,
Version 2.0** — see `LICENSE-APACHE`. Upstream copyright and
attribution notices are in `NOTICE`.

---

## 5. 上游文件名的保留 / Retention of upstream notices

原始上游作品中的版权、专利、商标与归属声明（Apache License 2.0
第 4(c) 条要求保留的部分）均未被移除或隐藏。

No copyright, patent, trademark or attribution notice from the
original upstream work (as required to be retained by Apache License
2.0, Section 4(c)) has been removed or obscured.

---

*本文件最后更新：2026-09-12 / Last updated: 2026-09-12*
