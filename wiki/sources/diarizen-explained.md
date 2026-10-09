---
title: "DiariZen Explained"
type: source
tags: [語者分離, pyannote, DiariZen, 教學論文]
created: 2026-10-09
updated: 2026-10-09
sources: ["DiariZen Explained.md"]
---

# DiariZen Explained

## 後設資料

- **作者**：Nikhil Raghav
- **來源**：arXiv 2604.21507
- **類型**：教學論文（Tutorial Paper）
- **發布**：2026

## 摘要

本教學論文將 DiariZen 語者分離系統的完整流程拆解為 7 個連續階段，每個階段附有概念說明、程式碼參照、張量形狀與視覺化，資料來自 AMI 會議語料庫。DiariZen 是混合系統，結合剪枝版 WavLM-Large encoder、帶 powerset 分類的 Conformer backend 與 VBx 分群，在開源語者分離系統中達到頂尖效能。

## 主要重點

- **7 個處理階段**：音訊載入 → WavLM 特徵提取 → Conformer 處理 → 分段聚合 → 語者 Embedding 提取 → VBx 分群 + PLDA 評分 → RTTM 輸出
- 每個階段皆有對應的輸入/輸出張量形狀，方便 debug 與理解
- 提供獨立可執行的腳本與 Jupyter Notebook（可重現）
- 適合想深入理解或客製化 pyannote 語者分離流程的開發者

## 介紹的新實體 / 概念

- [[DiariZen]] — 頂尖開源語者分離系統
- [[語者分離與辨識]] — 本文深度說明的技術領域

## 與現有頁面的關聯

- [[語者分離與辨識]] — 完整拆解語者分離技術流程，補充現有概念頁的技術深度
- [[ASR技術]] — 語者分離是 ASR 的延伸技術環節

## 個人看法

對於想理解 pyannote 內部運作或打算在其基礎上開發的工程師，這份教學是目前最系統化的文件之一。VBx + PLDA 分群是語者分離中相對少見的詳細說明對象，值得深入研究。RTTM 格式是語者分離的標準輸出，了解生成過程有助於後處理整合。
