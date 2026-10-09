---
title: "HyPoradise"
source: "https://arxiv.org/abs/2309.15701"
author: "Chen Chen, Yuchen Hu, Chao-Han Huck Yang, Sabato Marco Siniscalchi, Pin-Yu Chen, Eng Siong Chng"
published: "2023（NeurIPS 2023）"
created: 2026-10-09
description: "LLM 修正 ASR 的開源 benchmark，提供 33 萬對 N-best 假設與正確轉錄"
tags:
  - "clippings"
  - "asr"
  - "llm"
---

## 摘要

ASR 系統在處理雜訊音訊時仍有明顯限制。本研究提出利用外部 LLM 的語言知識進行 ASR 錯誤修正，並建立名為 **HyPoradise（HP）** 的開源 benchmark——包含超過 **33 萬筆** N-best 假設與正確轉錄的配對，橫跨多個語音領域。

## 主要貢獻

- **新資料集**：HyPoradise，33 萬+ 組 N-best 假設與正確轉錄配對
- **典範轉移**：從傳統語言模型重新評分（只選候選之一）轉向生成式修正（可從 N-best 中萃取並生成更好的答案）
- **三種錯誤修正技術**：評估不同數量標注資料下的 LLM 修正方法
- **突破性效能**：大幅降低詞錯誤率（WER），超越傳統 re-ranking 的上限
- **生成能力**：LLM 可透過有效 prompting 修正 N-best 列表中根本不存在的 token（幻覺修正）
- **可重現性**：公開預訓練模型，建立 ASR 錯誤修正的新評估典範
