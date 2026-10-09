---
title: "Generative Error Correction for Code-Switching ASR"
type: source
tags: [ASR, 語碼轉換, LLM, 錯誤修正, 學術論文]
created: 2026-10-09
updated: 2026-10-09
sources: ["Generative Error Correction for Code-Switching ASR.md"]
---

# Generative Error Correction for Code-Switching ASR

## 後設資料

- **作者**：Chen Chen, Yuchen Hu, Chao-Han Huck Yang, Hexin Liu, Sabato Marco Siniscalchi, Eng Siong Chng
- **來源**：arXiv 2310.13013
- **類型**：學術論文（ICASSP 2024）
- **發布**：2023 投稿，ICASSP 2024 發表

## 摘要

語碼轉換語音混合多種語言，使 ASR 面臨語法複雜、訓練資料稀缺的挑戰。本研究提出結合 LLM 與多個 ASR 系統 N-best 候選列表的生成式錯誤修正方法，透過帶 Low-Rank Adapter（LoRA）微調的 LLM，學習從 N-best 假設映射到最終正確轉錄。相較傳統語言模型重新評分，此方法代表典範轉移——LLM 可直接生成 N-best 中不存在的更好答案。

## 主要重點

- LLM 透過降低混合錯誤率（Mixed Error Rate, MER）大幅改善語碼轉換 ASR 準確率
- 展示 LLM 在假設到轉錄（H2T）學習上卓越的資料效率，為低資源語言提供解方
- LoRA 微調使 LLM 高效適應語碼轉換場景，無需全量微調
- 多 ASR 融合的 N-best 提供更豐富的候選，彌補單一 ASR 的語言覆蓋不足

## 介紹的新實體 / 概念

- [[語碼轉換ASR]] — 本文的核心應用場景
- [[ASR錯誤修正]] — 生成式錯誤修正路線的代表論文之一

## 與現有頁面的關聯

- [[ASR錯誤修正]] — 本文與 [[asr-error-correction-llm]] 同屬「N-best + LLM 生成式修正」路線，此篇專注語碼轉換場景
- [[hyporadise]] — HyPoradise 資料集提供 N-best 修正的 benchmark 基礎

## 個人看法

LoRA 使 LLM 修正語碼轉換 ASR 的成本大幅降低，是低資源語言（如台語、客語）的可行路線。Mixed Error Rate 是語碼轉換場景專用指標，與標準 WER 有所不同，需留意評測標準的差異。
