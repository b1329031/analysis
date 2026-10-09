---
title: "VoiceStreamAI"
type: entity
tags: [ASR, 即時轉錄, WebSocket, 開源, 工具]
created: 2026-10-09
updated: 2026-10-09
sources: ["VoiceStreamAI.md"]
free_tier: true
chinese: true
taiwan_made: false
hardware: false
---

# VoiceStreamAI

VoiceStreamAI 是 Python 伺服器 + JavaScript 客戶端透過 WebSocket 實現近即時音訊串流與轉錄的開源框架，預設使用 HuggingFace VAD 與 faster-whisper，採用模組化工廠/策略模式設計。

## 關鍵屬性

- **作者**：Alessandro Saccoia
- **來源**：https://github.com/alesaccoia/VoiceStreamAI
- **架構**：Python 伺服器 + JavaScript 客戶端
- **傳輸**：WebSocket（支援 SSL）
- **預設 VAD**：Silero VAD（無需 token）/ pyannote（需 HuggingFace token）
- **預設 ASR**：faster-whisper
- **分塊策略**：5 秒分塊 + 靜音等待（SilenceAtEndOfChunk）
- **授權**：不詳

## 架構說明

| 元件 | 職責 |
|---|---|
| Python Server | WebSocket 連線管理、VAD 偵測、ASR 轉錄 |
| JavaScript Client | 瀏覽器端錄音、WebSocket 傳輸 |
| VAD | 語音活動偵測，減少無效音訊傳輸 |
| faster-whisper | ASR 引擎，比原版 Whisper 快 |

## 與其他實體的關聯

- [[Whisper-Streaming]] / [[SimulStreaming]] — 同為即時轉錄框架，不同架構
- [[OpenAI-Whisper]] — 底層辨識引擎（faster-whisper 為其加速實作）

## 備註

- 靜音等待策略在密集語音段會增加延遲，直到偵測到停頓才輸出
- 模組化設計讓替換 VAD 或 ASR 後端相對容易
- 需注意 pyannote VAD 的授權門檻（需 HuggingFace token）

## 相關概念

- [[即時串流轉錄]] — VoiceStreamAI 是此概念的 WebSocket 架構實作
