---
title: "HyPoradise"
type: source
tags: [ASR, LLM, 錯誤修正, 資料集, 學術論文]
created: 2026-10-09
updated: 2026-10-09
sources: ["HyPoradise.md"]
---

# HyPoradise

## 後設資料

- **作者**：Chen Chen, Yuchen Hu, Chao-Han Huck Yang, Sabato Marco Siniscalchi, Pin-Yu Chen, Eng Siong Chng
- **來源**：arXiv 2309.15701
- **類型**：學術論文（NeurIPS 2023）
- **發布**：2023

## 摘要

本研究提出利用外部 LLM 進行 ASR 錯誤修正，並建立名為 **HyPoradise（HP）** 的開源 benchmark——包含超過 33 萬筆 N-best 假設與正確轉錄的配對，橫跨多個語音領域。研究展示 LLM 可透過生成式方法突破傳統重新評分（只從 N-best 中選一）的上限，甚至修正 N-best 中根本不存在的 token（幻覺修正），大幅降低 WER。

## 主要重點

- **新資料集**：HyPoradise，33 萬+ 組 N-best 假設與正確轉錄配對，橫跨多個語音領域
- **典範轉移**：從「重新評分（選最好的一個）」到「生成式修正（可生成候選中沒有的答案）」
- **幻覺修正能力**：LLM 可透過有效 prompting 修正 N-best 列表中完全不存在的 token
- **突破性效能**：大幅超越傳統 re-ranking 的理論上限
- **三種修正技術**：評估不同標注資料量下的 LLM 修正方法
- **公開預訓練模型**：建立 ASR 錯誤修正的新評估典範

## 介紹的新實體 / 概念

- [[ASR錯誤修正]] — HyPoradise 是此領域最重要的開源 benchmark

## 與現有頁面的關聯

- [[ASR錯誤修正]] — HyPoradise 為此概念提供最具代表性的資料集與評測框架
- [[generative-ec-cs-asr]] — 同一研究群組，延伸至語碼轉換場景

## 個人看法

「生成式修正可以突破 N-best oracle 上限」是 HyPoradise 最重要的洞見，顛覆了傳統 re-ranking 的思維框架。幻覺修正能力（修正 N-best 中不存在的 token）代表 LLM 帶入的語言知識可以「創造」比任何 ASR 候選都更正確的轉錄。33 萬對配對使其成為訓練與評測的可靠基準。
