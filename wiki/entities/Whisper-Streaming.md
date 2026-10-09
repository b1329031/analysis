---
title: "Whisper-Streaming"
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

# Whisper-Streaming

Whisper-Streaming 是查理大學 UFAL 實驗室將批次式 Whisper 模型改造為即時串流轉錄系統的開源工具，採用 Local Agreement Policy 策略，實測約 3.3 秒延遲。2025 年後官方建議改用繼任者 [[SimulStreaming]]。

## 關鍵屬性

- **開發機構**：查理大學 UFAL（布拉格）
- **發表**：IJCNLP-AACL 2023
- **核心策略**：Local Agreement Policy（連續 n 次更新同意某前綴才輸出）
- **延遲**：實測約 3.3 秒
- **維護狀態**：⚠️ 逐漸過時，2025 年後建議改用 [[SimulStreaming]]
- **授權**：MIT

## 支援後端

| 後端 | 特點 |
|---|---|
| faster-whisper | 推薦，需 GPU，速度最快 |
| whisper-timestamped | 較慢但依賴限制少 |
| OpenAI API | 不需 GPU，按使用量付費 |
| mlx-whisper | Apple Silicon 優化 |

## 與其他實體的關聯

- [[SimulStreaming]] — 官方推薦的繼任者，速度品質更好
- [[VoiceStreamAI]] — 同為即時轉錄框架，採用不同的分塊策略
- [[OpenAI-Whisper]] — 底層基礎模型

## 備註

- Local Agreement Policy 的優點：不靠固定視窗，以「多次確認」機制保證輸出穩定性
- 3.3 秒延遲適合會議記錄，但不適合即時對話（< 1 秒需求）
- 已在多語會議現場轉錄服務中驗證穩健性

## 相關概念

- [[即時串流轉錄]] — Whisper-Streaming 是此概念的代表性實作
