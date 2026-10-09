---
title: "Whisper-Streaming"
source: "https://github.com/ufal/whisper_streaming"
author: "Dominik Macháček, Raj Dabre, Ondřej Bojar（查理大學 UFAL）"
published: "2023（IJCNLP-AACL 2023）"
created: 2026-10-09
description: "將 Whisper 改造為即時轉錄系統，Local Agreement 策略，實測約 3.3 秒延遲"
tags:
  - "clippings"
  - "asr"
  - "realtime"
  - "whisper"
---

## 重要提醒

> ⚠️ 2025 年 Whisper-Streaming 逐漸過時，官方建議改用 [SimulStreaming](https://github.com/ufal/SimulStreaming)——速度更快、品質更好，且已整合 Whisper-Streaming 的主要介面。

## 摘要

Whisper 原本設計用於最長 30 秒的完整句子音訊，不適合即時串流。本研究在 Whisper 上建構了 **Whisper-Streaming**，使用**本地一致性策略（Local Agreement Policy）**搭配自適應延遲，實現即時語音轉錄與翻譯。

在未分段的長篇語音測試集上，Whisper-Streaming 達到高品質且約 **3.3 秒延遲**，並已在多語會議的現場轉錄服務中驗證其穩健性與實用性。

## 核心原理

- **Local Agreement Policy**：若連續 n 次更新（每次有新音訊）都同意某個前綴轉錄，則確認該前綴輸出
- 不做固定視窗切割，避免在詞語中間斷開
- 使用 init prompt 保持上下文連貫性
- 偵測完整句子後滾動處理緩衝區，保持處理視窗不過長

## 安裝

```bash
pip install librosa soundfile faster-whisper
pip install torch torchaudio  # VAD 用

# Python 模組使用
from whisper_online import FasterWhisperASR, OnlineASRProcessor

asr = FasterWhisperASR("en", "large-v2")
online = OnlineASRProcessor(asr)

while audio_has_not_ended:
    a = # 取得新音訊 chunk
    online.insert_audio_chunk(a)
    o = online.process_iter()
    print(o)  # 部分輸出

o = online.finish()
print(o)
```

## 支援的後端

| 後端 | 特點 |
|---|---|
| faster-whisper | 推薦，需 GPU，速度最快 |
| whisper-timestamped | 較慢但依賴限制少 |
| OpenAI API | 不需 GPU，按使用量付費 |
| mlx-whisper | Apple Silicon 優化 |

## 與 SimulStreaming 比較

| 項目 | Whisper-Streaming | SimulStreaming |
|---|---|---|
| 速度/品質 | 普通 | 更好 |
| 後端選項 | 多（4種） | 僅 torch |
| 授權 | MIT | MIT |
| 維護狀態 | 逐漸停止 | 主動維護 |
