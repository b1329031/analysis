---
title: "Aligning Speech to Languages"
type: source
tags: [ASR, 語碼轉換, LLM, 語言對齊, 學術論文]
created: 2026-10-09
updated: 2026-10-09
sources: ["Aligning Speech to Languages.md"]
---

# Aligning Speech to Languages

## 後設資料

- **作者**：Hexin Liu, Xiangyu Zhang, Haoyang Zhang, Leibny Paola Garcia, Andy W. H. Khong, Eng Siong Chng, Shinji Watanabe
- **來源**：arXiv 2403.05887v2
- **類型**：學術論文
- **發布**：2024

## 摘要

語碼轉換 ASR 的核心難點是語言混淆——模型無法正確辨識同一語音中的語言切換邊界。本研究提出**語言對齊損失（Language Alignment Loss, LAL）**，在訓練期間讓聲學特徵對齊從 ASR 解碼器學到的偽語言標籤，使模型在無需逐幀語言標注資料的前提下，獲得幀級語言識別能力。結合 LLM 生成式錯誤修正後，ASRU 測試集獲得 14.1% 相對改善、SEAME 測試集 5.5% 相對改善，計算開銷可忽略。

## 主要重點

- LAL 在 CTC/Attention 混合模型與 Whisper 模型上均有效
- ASRU 資料集：平衡主語言主導資料後獲得 8.6% 相對改善
- LAL 輸出的語言線索可作為 LLM 錯誤修正的提示，效果進一步提升
- 不需要任何逐幀語言標注資料（低成本可實施）

## 介紹的新實體 / 概念

- [[語碼轉換ASR]] — 本文的核心應用場景
- [[ASR錯誤修正]] — LAL 與 LLM 錯誤修正的結合

## 與現有頁面的關聯

- [[ASR錯誤修正]] — LAL 作為語言線索提示，是生成式錯誤修正的前置增強
- [[OpenAI-Whisper]] — Whisper 作為實驗模型之一

## 個人看法

LAL 的設計巧妙：以偽標籤作為語言監督信號，不需要昂貴的人工標注，是低資源語碼轉換場景的實用解方。與 [[generative-ec-cs-asr]] 結合可形成完整的兩階段改善流程。
