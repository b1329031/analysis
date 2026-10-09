---
title: "voicetag"
source: "https://pypi.org/project/voicetag/"
author:
published:
created: 2026-10-09
description: "pyannote + resemblyzer 實作的語者分離與命名識別 Python 套件"
tags:
  - "clippings"
  - "diarization"
  - "pyannote"
---

## 套件簡介

`voicetag` 是一個 Python 語者分離與命名識別函式庫，結合 **pyannote.audio**（語者分離）與 **resemblyzer**（聲紋 embedding），讓使用者能自動判斷「誰在說話、從幾點到幾點」。

適用場景：Podcast、訪談、會議錄音、法庭紀錄、客服中心、媒體監控。

## 安裝

```bash
pip install voicetag
# 選擇性：搭配轉錄提供者
pip install voicetag[openai]    # OpenAI Whisper API
pip install voicetag[groq]      # Groq（快速 Whisper）
pip install voicetag[whisper]   # 本地 Whisper
pip install voicetag[deepgram]  # Deepgram
pip install voicetag[all-stt]   # 全部提供者
```

**前置作業**：需到 HuggingFace 接受 pyannote 模型授權條款，取得 token 後設定 `HF_TOKEN` 環境變數。

## 使用範例

### Python API

```python
from voicetag import VoiceTag

vt = VoiceTag()
vt.enroll("小明", ["mingming1.wav", "mingming2.wav"])
vt.enroll("小華", ["xiaohua1.wav"])

result = vt.identify("meeting.wav")
for segment in result.segments:
    print(f"{segment.speaker}: {segment.start:.1f}s - {segment.end:.1f}s")
```

### CLI 指令

```bash
# 聲紋註冊
voicetag enroll "小明" mingming1.wav mingming2.wav

# 識別
voicetag identify meeting.wav --threshold 0.8

# 含轉錄
voicetag transcribe meeting.wav --provider openai --language zh

# 管理聲紋庫
voicetag profiles list
voicetag profiles remove "小明"
```
