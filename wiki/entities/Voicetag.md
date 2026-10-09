---
title: "Voicetag"
type: entity
tags: [語者分離, pyannote, Python套件, 開源, 工具]
created: 2026-10-09
updated: 2026-10-09
sources: ["voicetag.md"]
free_tier: true
chinese: true
taiwan_made: false
hardware: false
---

# Voicetag

`voicetag` 是結合 pyannote.audio（語者分離）與 resemblyzer（聲紋 embedding）的 Python 套件，提供高階 API 與 CLI，支援聲紋註冊與識別，並可整合多種 STT 後端輸出帶語者標籤的轉錄。

## 關鍵屬性

- **來源**：PyPI — https://pypi.org/project/voicetag/
- **語者分離引擎**：pyannote.audio
- **聲紋 Embedding**：resemblyzer
- **STT 後端**：OpenAI Whisper API / Groq / 本地 Whisper / Deepgram（選配）
- **前置要求**：HuggingFace 帳號 + pyannote 模型授權 + `HF_TOKEN` 環境變數
- **介面**：Python API + CLI

## Python API 範例

```python
vt = VoiceTag()
vt.enroll("小明", ["mingming1.wav"])
result = vt.identify("meeting.wav")
```

## CLI 主要命令

| 命令 | 功能 |
|---|---|
| `voicetag enroll` | 聲紋註冊 |
| `voicetag identify` | 識別語者段落 |
| `voicetag transcribe` | 含轉錄的語者分離 |
| `voicetag profiles` | 管理聲紋庫 |

## 與其他實體的關聯

- [[jb55-Transcribe]] — 同為整合 pyannote 的語者識別工具，jb55 為 CLI 管線，voicetag 為 Python 套件
- [[DiariZen]] — pyannote 生態系的另一語者分離工具

## 備註

- resemblyzer 是相對老舊的 embedding 引擎，效能不如 pyannote/embedding 3.x
- pyannote 授權牆（需到 HuggingFace 確認條款）是部署的初期障礙
- 需注意 [[hf-pyannote-similarity-bug]] 記錄的 pyannote embedding 相似度異常問題

## 相關概念

- [[語者分離與辨識]] — Voicetag 是此技術的 Python 套件封裝
