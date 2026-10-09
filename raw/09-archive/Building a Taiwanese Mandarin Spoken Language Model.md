---
title: "Building a Taiwanese Mandarin Spoken Language Model"
source: "https://arxiv.org/pdf/2411.07111"
author: "Chih-Kai Yang, Yu-Kuan Fu, Chen-An Li et al.（李宏毅實驗室，台灣大學）"
published: "2024"
created: 2026-10-09
description: "台灣華語口語語言模型，用 Silero VAD 防 Whisper 幻覺，支援即時語音對話"
tags:
  - "clippings"
  - "asr"
  - "taiwanese"
  - "vad"
---

## 摘要

本研究為台灣華語建立第一個口語語言模型（Spoken Language Model），目標是支援**即時語音對語音的多輪對話**。系統採用 decoder-only Transformer，並整合全雙工（full-duplex）能力，使模型可同時說話與聆聽。

研究涵蓋：使用合成對話資料進行資料準備、針對即時性能的訓練調整，以及自訂評估平台用於量測對話品質。

## 關鍵技術

- **VAD 防幻覺**：使用 Silero VAD 過濾靜音段，避免 Whisper 在空白音訊上產生幻覺輸出
- **全雙工架構**：模型可在聆聽的同時輸出語音，無需明確的輪次切換
- **台灣華語特化**：針對台灣口語習慣與腔調進行訓練

## 主要貢獻

- 端到端口語 LLM 架構，專為台灣華語設計
- 使用合成對話資料的訓練方法
- 評估平台（量測對話流暢度與回應連貫性）
- 為台灣華語口語模型奠定基礎技術
