---
title: "Building a Taiwanese Mandarin Spoken Language Model"
type: source
tags: [ASR, 台灣華語, 口語LM, VAD, 全雙工, 學術論文]
created: 2026-10-09
updated: 2026-10-09
sources: ["Building a Taiwanese Mandarin Spoken Language Model.md"]
---

# Building a Taiwanese Mandarin Spoken Language Model

## 後設資料

- **作者**：Chih-Kai Yang, Yu-Kuan Fu, Chen-An Li 等（台灣大學 / 李宏毅實驗室）
- **來源**：arXiv 2411.07111
- **類型**：學術論文
- **發布**：2024

## 摘要

台大李宏毅實驗室為台灣華語建立第一個口語語言模型（Spoken Language Model），支援即時語音對語音的多輪對話，採用 decoder-only Transformer 並整合**全雙工（full-duplex）**能力，使模型可同時說話與聆聽。關鍵技術包括：Silero VAD 過濾靜音段以防止 Whisper 在空白音訊上產生幻覺輸出、合成對話資料訓練、以及自訂評估平台量測對話流暢度。

## 主要重點

- **VAD 防幻覺**：Silero VAD 偵測靜音段，避免 Whisper 在無語音片段輸出亂碼
- **全雙工架構**：無需明確輪次切換，模型可在聆聽的同時輸出語音
- **台灣華語特化**：針對台灣口語習慣與腔調進行訓練
- **合成資料訓練**：解決真實口語對話資料稀缺問題

## 介紹的新實體 / 概念

- 台大口語語言模型（研究原型，非公開產品）

## 與現有頁面的關聯

- [[ASR技術]] — 台灣本土口語 LM 研究，代表 ASR 與對話 AI 的融合趨勢
- [[OpenAI-Whisper]] — 系統中用於轉錄的基礎模型，VAD 防幻覺策略針對 Whisper 特性設計
- [[語碼轉換ASR]] — 台灣華語本質上常混合台語、閩南語等，口語 LM 需應對此挑戰

## 個人看法

全雙工口語 LM 代表了「語音 AI 對話」的下一代架構。Silero VAD 防幻覺的做法是即時轉錄系統的實用技巧，在 [[即時串流轉錄]] 場景中可直接採用。台灣華語缺乏大量口語訓練資料，合成資料的路徑值得借鑒。
