---
title: "Whisper-Streaming"
type: source
tags: [工具, ASR, 即時轉錄, Whisper, 開源]
created: 2026-10-09
updated: 2026-10-09
sources: ["Whisper-Streaming.md"]
---

# Whisper-Streaming

## 後設資料

- **作者**：Dominik Macháček, Raj Dabre, Ondřej Bojar（查理大學 UFAL）
- **來源**：GitHub — https://github.com/ufal/whisper_streaming
- **類型**：開源工具文件 + 學術論文（IJCNLP-AACL 2023）
- **發布**：2023

## 摘要

Whisper-Streaming 在 Whisper 上建構了**本地一致性策略（Local Agreement Policy）**，將批次模型改造為即時串流轉錄系統，實測延遲約 3.3 秒，已在多語會議現場服務中驗證穩健性。2025 年後官方建議改用繼任者 [[SimulStreaming]]（速度品質更好、主動維護），Whisper-Streaming 逐漸走向過時。

## 主要重點

- **Local Agreement Policy**：連續 n 次更新都同意某前綴後才確認輸出，避免固定視窗切割
- **init prompt 機制**：保持上下文連貫性，避免前後文脈斷裂
- **延遲**：約 3.3 秒（取決於語音和 Local Agreement 設定）
- **4 種後端**：faster-whisper（推薦）、whisper-timestamped、OpenAI API、mlx-whisper
- **⚠️ 已逐漸過時**：2025 年後建議改用 SimulStreaming

## 介紹的新實體 / 概念

- [[Whisper-Streaming]] — 本文的主要說明對象
- [[SimulStreaming]] — 官方推薦的繼任者
- [[即時串流轉錄]] — Local Agreement Policy 是此技術的核心創新

## 與現有頁面的關聯

- [[即時串流轉錄]] — Whisper-Streaming 是此概念的代表性實作
- [[OpenAI-Whisper]] — 底層基礎模型
- [[VoiceStreamAI]] — 同為即時轉錄框架，兩者可互相比較

## 個人看法

Local Agreement Policy 的設計很優雅：不靠固定視窗，而是靠「多次確認」機制輸出穩定結果，兼顧即時性與準確性。3.3 秒延遲對多數會議場景可接受，但對即時對話（< 1 秒）則不足。已有官方繼任者 SimulStreaming，新專案應直接評估後者。
