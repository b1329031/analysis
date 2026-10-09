---
title: "Semi-supervised CS-ASR with LLM Filter"
type: source
tags: [ASR, 語碼轉換, LLM, 半監督, 學術論文]
created: 2026-10-09
updated: 2026-10-09
sources: ["Semi-supervised CS-ASR with LLM Filter.md"]
---

# Semi-supervised CS-ASR with LLM Filter

## 後設資料

- **作者**：Yu Xi, Wen Ding, Kai Yu, Junjie Lai
- **來源**：arXiv 2407.04219
- **類型**：學術論文
- **發布**：2024

## 摘要

語碼轉換 ASR 面臨資料稀缺的核心問題。本研究在半監督學習框架中引入 **LLM-Filter**——透過自訂 prompt 讓 LLM 精煉偽標籤、在雜訊學生訓練（Noisy Student Training, NST）期間篩選單語資料，解決資料選擇與標籤修正兩個問題。在 ASRU-CS、AISHELL-2、LibriSpeech 及 AESRC 資料集上，結果超越有監督與半監督基準。

## 主要重點

- LLM-Filter 透過自訂 prompt 進行偽標籤品質精煉與資料篩選
- 在語碼轉換任務上大幅超越有監督與半監督基準
- 英文部分表現甚至超越全監督基準
- 單語資料中的**口音多樣性**在語言相關時帶來額外效益
- 框架通用性高：可整合至任何 Noisy Student Training 流程

## 介紹的新實體 / 概念

- [[語碼轉換ASR]] — 本文的核心應用場景
- [[ASR錯誤修正]] — LLM-Filter 是錯誤修正技術在資料選擇上的延伸應用

## 與現有頁面的關聯

- [[ASR錯誤修正]] — LLM-Filter 展示 LLM 在訓練前端（偽標籤過濾）而非後端（轉錄後修正）的應用
- [[aligning-speech-to-languages]] — 同為語碼轉換 ASR 的改善方法，前者在訓練目標，此篇在資料品質

## 個人看法

LLM-Filter 的設計思路是「用 LLM 的語言知識幫 ASR 篩資料」，而非直接修正輸出。這種「訓練前端介入」的策略與後端修正互補，可同時使用。口音多樣性帶來額外效益的結論，暗示台語口音變異的單語資料也可能對華台語碼轉換 ASR 有所幫助。
