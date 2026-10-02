---
title: "ASR Error Correction using Large Language Models"
type: source
tags: [ASR, 錯誤修正, LLM, 學術論文]
created: 2026-10-02
updated: 2026-10-02
sources: ["ASR Error Correction using Large Language Models.md"]
---

# ASR Error Correction using Large Language Models

## 後設資料

- **作者**：Rao Ma、Mengjie Qian、Mark Gales、Kate Knill（劍橋大學）
- **來源**：arXiv 2409.09554v1
- **類型**：學術論文（語音辨識 / 自然語言處理）
- **發布**：2024（IEEE 投稿格式）

## 摘要

本論文研究如何用大型語言模型（LLM）修正自動語音辨識（ASR）的輸出錯誤。錯誤修正（Error Correction, EC）作為 ASR 的後處理步驟，不需存取底層模型權重即可提升黑箱 ASR 系統的表現。作者提出以 ASR 的 **N-best 清單**（而非單一 1-best 假設）作為修正模型的輸入，提供更豐富的上下文；並引入**受限解碼**（constrained decoding）策略，讓修正結果貼近原始語音。研究同時比較了微調（fine-tuning T5）與零樣本（zero-shot ChatGPT）兩種路線。

## 主要重點

- **N-best 清單優於 1-best**：提供多個候選句，含正確轉錄的可能性更高，給修正模型更多線索
- **三種解碼策略**：
  - 無受限解碼（uncon）：自由生成
  - N-best 受限解碼（constr）：只能從 N-best 清單中選
  - N-best 最近解碼（closest）：生成後找 Levenshtein 距離最近的候選
  - 格狀受限解碼（lattice）：擴大到合併路徑的格狀空間
- **微調路線**：T5 模型在 LibriSpeech 上，10-best 相較基線 WER 可降低 7.7%（test\_other）
- **零樣本路線**：GPT-4 在 Transducer 輸出上平均 WERR 達 25.2%，可超越微調的 T5；但在 Whisper 輸出上效果有限（僅 2.6%）
- **Whisper 的 N-best 多樣性低**：因內建反正規化（ITN），多個候選常只有格式差異而非內容差異，限制了修正效益
- **LLM 可作為模型集成工具**：結合不同 ASR 系統的 N-best，GPT-4 可達 32–36% 的 WER 下降
- **資料污染檢測**：用 GPT-4 改寫測試句設計測驗，評估測試資料是否已被 LLM 預訓練看過

## 介紹的新實體 / 概念

- [[OpenAI Whisper]] — 實驗用的大規模 ASR 模型之一
- [[ASR錯誤修正]] — 本論文的核心概念

## 與現有頁面的關聯

- [[ASR技術]] 中「生成式 AI 增強 ASR」的「後處理校正」方式，本文提供深度實證
- [[Good Tape]]、[[雅婷逐字稿]] 等工具的底層辨識品質皆可能受惠於此類後處理技術

## 個人看法

這篇從「黑箱 ASR 也能改善」的角度切入，對實務很有價值——因為多數商業工具（如 [[Otter.ai]]、[[Notta]]）都是 API 黑箱，無法微調底層模型，只能靠後處理。對畢業專題而言，「用 LLM 修正語音輸入錯誤」是可直接套用的技術模組。
