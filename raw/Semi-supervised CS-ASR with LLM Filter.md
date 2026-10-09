---
title: "Semi-supervised CS-ASR with LLM Filter"
source: "https://arxiv.org/pdf/2407.04219"
author: "Yu Xi, Wen Ding, Kai Yu, Junjie Lai"
published: "2024"
created: 2026-10-09
description: "用 LLM 過濾偽標籤，半監督訓練語碼轉換 ASR，純 prompt 修正效果評估"
tags:
  - "clippings"
  - "asr"
  - "llm"
  - "code-switching"
---

## 摘要

語碼轉換（CS）ASR 系統的建構面臨資料稀缺的核心問題。本研究提出在半監督學習框架中使用無標注的單語語音資料，並引入 **LLM-Filter**——透過自訂 prompt 讓 LLM 精煉偽標籤、在雜訊學生訓練（Noisy Student Training）期間篩選單語資料。

在 ASRU-CS、AISHELL-2、LibriSpeech 及 AESRC 多個資料集上測試，結果優於基準方法。

## 主要結果

- 在語碼轉換任務上大幅超越有監督與半監督基準
- 英文部分的表現甚至超越全監督基準
- 單語資料中的口音多樣性在語言相關時帶來額外效益
- LLM-Filter 成功利用大型語言模型能力進行資料精煉與選擇

## 貢獻

建立了一套通用框架，透過整合 LLM 過濾機制，將雜訊學生訓練應用於語碼轉換 ASR——同時處理資料選擇與標籤修正兩個問題。
