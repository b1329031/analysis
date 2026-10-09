---
title: "Generative Error Correction for Code-Switching ASR"
source: "https://arxiv.org/abs/2310.13013"
author: "Chen Chen, Yuchen Hu, Chao-Han Huck Yang, Hexin Liu, Sabato Marco Siniscalchi, Eng Siong Chng"
published: "2023（ICASSP 2024）"
created: 2026-10-09
description: "多 ASR N-best + LLM 做語碼轉換場景的生成式錯誤修正"
tags:
  - "clippings"
  - "asr"
  - "llm"
  - "code-switching"
---

## 摘要

語碼轉換（Code-Switching）是指在單一句子中混合使用多種語言，這對自動語音辨識（ASR）系統來說仍是一大挑戰，主要原因是語法結構複雜、訓練資料稀缺。

本研究提出結合大型語言模型（LLM）與多個 ASR 系統輸出的 N-best 候選列表，以改善語碼轉換語音的辨識準確率。作法是先從多個訓練好的 ASR 模型產生 N-best 假設，再透過帶有可訓練低秩適配器（Low-Rank Adapter）的 LLM，學習從 N-best 假設映射到最終正確轉錄結果。

這種生成式錯誤修正方法，相比傳統語言模型重新評分技術，代表了典範的轉移。

## 主要貢獻

- 實證 LLM 能透過降低混合錯誤率（Mixed Error Rate）大幅改善語碼轉換 ASR 的準確率
- 展示 LLM 在假設到轉錄（H2T）學習上有卓越的資料效率，為低資源語言語碼轉換 ASR 的資料稀缺問題提供潛在解法
- 導入生成式方法，取代傳統重新評分流程，開創新典範
- 已投稿 ICASSP 2024
