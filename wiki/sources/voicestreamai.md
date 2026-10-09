---
title: "VoiceStreamAI"
type: source
tags: [工具, ASR, 即時轉錄, WebSocket, VAD, 開源]
created: 2026-10-09
updated: 2026-10-09
sources: ["VoiceStreamAI.md"]
---

# VoiceStreamAI

## 後設資料

- **作者**：Alessandro Saccoia
- **來源**：GitHub — https://github.com/alesaccoia/VoiceStreamAI
- **類型**：開源工具文件
- **發布**：不詳

## 摘要

VoiceStreamAI 是 Python 伺服器 + JavaScript 客戶端的即時語音轉錄框架，透過 WebSocket 傳輸音訊串流，預設使用 HuggingFace VAD（Silero 或 pyannote）與 faster-whisper。模組化設計採用工廠模式與策略模式，可替換 VAD 和 ASR 元件，預設 5 秒分塊加靜音等待策略（SilenceAtEndOfChunk），在密集語音段可能引入額外延遲。

## 主要重點

- **雙端架構**：Python 伺服器管理 WebSocket 連線與 ASR，JavaScript 客戶端負責收音
- **VAD 類型**：支援 Silero（無需 token）、pyannote（需 HuggingFace token）、none
- **ASR 後端**：預設 faster-whisper，比原版 Whisper 快很多
- **分塊策略**：5 秒分塊 + 靜音等待，避免詞語被切斷
- **SSL 支援**：支援安全 WebSocket 連線（wss://）
- **延遲問題**：靜音等待策略在密集語音時會引入額外等待

## 介紹的新實體 / 概念

- [[VoiceStreamAI]] — 本文的主要說明對象
- [[即時串流轉錄]] — 本工具實作的核心技術

## 與現有頁面的關聯

- [[即時串流轉錄]] — VoiceStreamAI 是即時串流轉錄的具體開源實作
- [[ASR技術]] — 即時 ASR 應用案例，展示 WebSocket + VAD + ASR 的整合架構
- [[OpenAI-Whisper]] — faster-whisper 是 Whisper 的加速版本，為底層辨識引擎

## 個人看法

VoiceStreamAI 的架構清晰，適合作為自建即時轉錄服務的起點。VAD 在串流場景中的核心作用是「知道什麼時候說完了」，避免在語音中間斷開送給 ASR，這是 5 秒靜音等待策略背後的邏輯。與 [[Whisper-Streaming]] 的 Local Agreement Policy 相比，此方案更直接但延遲控制較粗糙。
