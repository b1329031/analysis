---
title: "VoiceStreamAI"
source: "https://github.com/alesaccoia/VoiceStreamAI"
author: "Alessandro Saccoia"
published:
created: 2026-10-09
description: "WebSocket + VAD + Whisper 即時語音轉文字框架，Python 伺服器 + JavaScript 客戶端"
tags:
  - "clippings"
  - "asr"
  - "realtime"
  - "websocket"
---

## 簡介

**VoiceStreamAI** 是一個 Python 3 伺服器 + JavaScript 客戶端的解決方案，透過 WebSocket 實現近即時音訊串流與轉錄。

系統使用 HuggingFace 的 VAD（語音活動偵測）和 OpenAI Whisper（預設使用 faster-whisper）進行語音辨識。

## 主要功能

- WebSocket 即時音訊串流
- 模組化設計，易於整合不同 VAD 和 ASR 技術
- 工廠模式與策略模式，元件管理彈性
- 可自訂音訊分塊處理策略
- 多語言轉錄支援
- 支援 SSL 安全連線

## 快速啟動

```bash
# 無需 token 的 Silero VAD + 小型 Whisper
python3 -m src.main --host 0.0.0.0 --port 6006 \
  --asr-args '{"model_size": "tiny"}'

# 使用 Pyannote VAD（需 HuggingFace token）
python3 -m src.main --vad-type pyannote \
  --vad-args '{"auth_token": "your_token_here"}'
```

## 主要設定參數

| 參數 | 說明 | 預設值 |
|---|---|---|
| `--vad-type` | VAD 類型（`silero`、`pyannote`、`none`） | `silero` |
| `--asr-type` | ASR 類型 | `faster_whisper` |
| `--host` | WebSocket 伺服器主機 | `127.0.0.1` |
| `--port` | 監聽埠號 | `8765` |

## 客戶端使用

1. 開啟 `client/index.html`
2. 輸入 WebSocket 位址（預設 `ws://localhost:8765`）
3. 設定音訊分塊長度與偏移量
4. 選擇轉錄語言
5. 點「Connect」→「Start Streaming」

## VAD 緩衝策略（SilenceAtEndOfChunk）

- 預設分塊長度 5 秒
- 等待靜音後才處理，避免詞語被切斷
- 這會在密集語音段引入額外延遲，直到偵測到停頓才轉錄

## 架構說明

- **Python Server**：管理 WebSocket 連線、處理音訊串流、執行 VAD 和轉錄
- **faster-whisper**：預設 ASR 後端，速度比原版 Whisper 快很多
- **VAD 目的**：減少計算負擔、提升準確率、優化網路頻寬（只傳語音段）
