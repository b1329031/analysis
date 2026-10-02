---
title: "Better Pseudo-labeling with Multi-ASR Fusion and Error Correction by SpeechLLM"
type: source
tags: [ASR, 偽標籤, SpeechLLM, 多模型融合, 學術論文]
created: 2026-10-02
updated: 2026-10-02
sources: ["Better Pseudo-labeling with Multi-ASR Fusion and Error Correction by SpeechLLM.md"]
---

# Better Pseudo-labeling with Multi-ASR Fusion and Error Correction by SpeechLLM

## 後設資料

- **作者**：Jeena Prakash、Blessingh Kumar、Kadri Hacioglu、Bidisha Sharma 等（Uniphore Systems，印度 & 美國）
- **來源**：arXiv 2506.11089v1
- **類型**：學術論文（半監督 ASR / 偽標籤生成）
- **發布**：2025

## 摘要

本論文探討如何為大量「未轉錄的語音資料」自動產生高品質的偽標籤（pseudo-labels），用於訓練半監督 ASR 模型。傳統做法是用多個 ASR 輸出經多階段處理融合，容易產生錯誤傳遞與資訊損失。作者提出統一的「多 ASR + LLM 後處理」框架，用文字型或語音型 LLM 取代投票／仲裁邏輯。比較三種架構後發現：**語音型 LLM（SpeechLLM）**融合文字假設與聲學證據，產生的轉錄品質最接近人工標註，甚至在部分資料集上超越人工。

## 主要重點

- **三種偽標籤生成架構**：
  1. **多 ASR 集成管線**：融合 Icefall、Nemo Parakeet、OpenAI Whisper 三模型，用字詞層級多數決
  2. **多 ASR + 文字 LLM**（Llama 3.2 1B）：把三模型的混淆網路（confusion network）作為提示，微調後修正
  3. **多 ASR + 語音 LLM**（Qwen2-Audio）：同時納入文字假設與原始聲學證據，效果最佳
- **三個 ASR 模型規模**：Icefall（6,500 萬參數）、Nemo Parakeet（11 億）、Whisper-large-v3（15 億）
- **SpeechLLM 的關鍵優勢**：文字型 LLM 忽略了原始語音的聲學資訊，語音型 LLM 能「再聽一次音訊」來消歧
- **可超越人工標註**：在 DefinedAI 資料集上，用 SpeechLLM 偽標籤訓練的 ASR 比用人工標註訓練的表現更好
- **統一單階段框架**：將偽標籤任務轉為「指令遵循」任務，避免傳統級聯管線的錯誤傳遞與資訊損失
- **參數高效微調**：使用 QLoRA（4-bit），LoRA rank 32

## 介紹的新實體 / 概念

- [[OpenAI Whisper]] — 三個融合 ASR 模型之一
- [[ASR錯誤修正]] — 多 ASR 融合是錯誤修正的延伸應用
- SpeechLLM（語音大模型）— 融合聲學與文字的多模態 LLM

## 與現有頁面的關聯

- [[ASR技術]] 中「多模態融合」為現在 ASR 的發展方向，本文是具體實例
- 與 [[asr-error-correction-llm]] 同屬「LLM 修正 ASR」主題，但本文多了「語音模態」與「偽標籤訓練」角度

## 個人看法

這篇最有啟發的是「SpeechLLM 可超越人工標註」——意味著未來訓練資料可能不再完全依賴昂貴的人工轉錄。對台灣的低資源語言（台語、客語）特別有意義，因為人工標註語料稀缺，若能用多 ASR 融合自動產生高品質偽標籤，將大幅降低在地化 ASR 的開發成本（呼應 [[myVoca]]、[[雅婷逐字稿]] 的在地語料挑戰）。
