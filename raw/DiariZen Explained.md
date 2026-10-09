---
title: "DiariZen Explained"
source: "https://arxiv.org/pdf/2604.21507"
author: "Nikhil Raghav"
published: "2026"
created: 2026-10-09
description: "pyannote 語者分離完整流程的教學論文，分解為 7 個階段含程式碼與張量圖"
tags:
  - "clippings"
  - "diarization"
  - "pyannote"
---

## 摘要

語者分離（Speaker Diarization）的目標是判斷「誰在何時說話」。**DiariZen** 是一個混合系統，結合了剪枝版 WavLM-Large encoder、帶 powerset 分類的 Conformer backend 與 VBx 分群，在開源語者分離系統中達到頂尖效能。

然而，DiariZen 的架構分散於多個程式庫，難以理解與擴充。本教學論文將完整流程拆解為 **7 個連續階段**，每個階段附有概念說明、程式碼參照、張量形狀與視覺化，資料來自 AMI 會議語料庫。

## 7 個處理階段

1. **音訊載入**（Audio Loading）
2. **WavLM 特徵提取**（WavLM Feature Extraction）
3. **Conformer 處理**（Conformer Processing）
4. **分段聚合**（Segmentation Aggregation）
5. **語者 Embedding 提取**（Speaker Embedding Extraction）
6. **VBx 分群 + PLDA 評分**（VBx Clustering with PLDA Scoring）
7. **RTTM 輸出生成**（RTTM Output Generation）

## 主要貢獻

- 完整流程逐步說明（含每階段的輸入/輸出張量形狀）
- 獨立可執行的腳本與 Jupyter Notebook（可重現）
- 中間結果視覺化，方便 debug 與理解
- 開源程式庫，可直接擴充與修改

## 適用對象

想深入理解 pyannote 內部運作、或打算客製化語者分離流程的開發者。
