---
title: "SimulStreaming"
type: entity
tags: [ASR, 即時轉錄, Whisper, 開源, 工具]
created: 2026-10-09
updated: 2026-10-09
sources: ["Whisper-Streaming.md"]
free_tier: true
chinese: true
taiwan_made: false
hardware: false
---

# SimulStreaming

SimulStreaming 是查理大學 UFAL 實驗室開發的即時串流語音轉錄系統，為 [[Whisper-Streaming]] 的官方繼任者，速度更快、品質更好，且為主動維護狀態。已整合 Whisper-Streaming 的主要介面，遷移成本低。

## 關鍵屬性

- **開發機構**：查理大學 UFAL（布拉格）
- **性質**：[[Whisper-Streaming]] 的官方繼任者
- **來源**：https://github.com/ufal/SimulStreaming
- **後端**：僅支援 torch（相比 Whisper-Streaming 的 4 種後端選擇較少）
- **維護狀態**：主動維護（Active）
- **授權**：MIT

## 與其他實體的關聯

- [[Whisper-Streaming]] — 前身，已逐漸過時
- [[VoiceStreamAI]] — 同為即時轉錄框架

## 備註

- 2025 年後為即時 Whisper 轉錄的首選，新專案應優先評估此工具
- 僅支援 torch 後端，若需 mlx-whisper（Apple Silicon）等後端，目前仍需使用 Whisper-Streaming
- 內容來自 Whisper-Streaming 文件的說明，尚未有獨立原始文件，後續可補充

## 相關概念

- [[即時串流轉錄]] — SimulStreaming 是此概念的推薦實作
