---
title: "Aligning Speech to Languages"
source: "https://arxiv.org/html/2403.05887v2"
author: "Hexin Liu, Xiangyu Zhang, Haoyang Zhang, Leibny Paola Garcia, Andy W. H. Khong, Eng Siong Chng, Shinji Watanabe"
published: "2024"
created: 2026-10-09
description: "語言對齊損失（LAL）提供幀級語言線索，搭配 LLM 修正語碼轉換 ASR"
tags:
  - "clippings"
  - "asr"
  - "llm"
  - "code-switching"
---

## 摘要

語碼轉換 ASR 的一大挑戰是語言混淆（language confusion）——模型在同一段語音中無法正確區分語言切換的邊界。

本研究提出**語言對齊損失（Language Alignment Loss, LAL）**，在 ASR 訓練期間將聲學特徵對齊至從 ASR 解碼器學到的偽語言標籤，讓模型在不需要逐幀語言標注資料的前提下，學會幀級語言識別能力。

此外，研究結合 LLM 生成式錯誤修正，利用 LAL 輸出的語言線索作為提示，進一步提升雙語場景的表現。在 SEAME 和 ASRU 2019 資料集上測試，效果顯著，且參數幾乎不增加。

## 主要結果

- LAL 在 CTC/Attention 混合模型與 Whisper 模型上均有效
- ASRU 資料集：透過平衡主語言主導資料，獲得 **8.6% 相對改善**
- 搭配 LLM 錯誤修正後：ASRU 測試集 **14.1%** 相對改善，SEAME 測試集 **5.5%** 相對改善
- 計算開銷可忽略不計
