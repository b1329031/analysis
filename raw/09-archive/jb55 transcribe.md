---
title: "jb55/transcribe"
source: "https://github.com/jb55/transcribe"
author: "jb55"
published:
created: 2026-10-09
description: "whisper.cpp + pyannote 語者分離，含聲紋註冊與貪婪配對的命令列轉錄工具"
tags:
  - "clippings"
  - "diarization"
  - "speaker-recognition"
---

## 工具簡介

`transcribe` 是一個命令列工具，輸出帶語者標籤的逐字稿與字幕，可接受任何 ffmpeg 支援的音訊或影片格式。

```
$ transcribe -d interview.mp4 -
[00:00:12] speaker 2: Oh, yeah. So a very common thing in enterprise software is...
[00:00:23] speaker 1: you spend a lot of time and energy using this product, but then...
```

## 工作流程

各工具各司其職：

1. **ffmpeg** 轉換輸入為 16 kHz 單聲道 s16 wav
2. **whisper.cpp** 轉錄成帶時間戳的分段（`-oj` json）
3. **pyannote.audio** 對同一 wav 做語者分離
4. 每個分段取重疊最多的語者，連續同語者分段合併為一行
5. 同一批標注分段生成字幕（不合併）

## 主要指令

```bash
# 基本使用（含語者分離）
transcribe -d interview.mp4

# 指定語者人數
transcribe -d -s 2 meeting.mp4

# 聲紋註冊
transcribe --enroll 小明 --from-speaker 2 "some recording.m4a"

# 後續辨識（自動套用已註冊聲紋）
transcribe -d -m large-v3-turbo "another recording.m4a"
```

## 聲紋命名機制

語者分離只能說「這幾段是同一人」，不知道是誰。透過 `--enroll` 一次性註冊聲紋，之後所有轉錄都會自動套用名字。

- 相似度計算：餘弦相似度，貪婪配對（最強配對優先，每個名字只用一次）
- **未知語者保留編號**，不強行配對
- 實測數據：同一人不同錄音：0.68–0.94；不同人：0.02–0.27
- 預設門檻 0.55（位於中間空白地帶）

## 安裝

```bash
# uv（推薦）
uv venv --python 3.12 .venv
uv pip install -e '.[diarize]'
# whisper-cli 和 ffmpeg 需在 PATH 上
```

## 輸出格式

- `.txt`：逐字稿，每行一個語者輪次
- `.srt` / `.vtt`：字幕（.vtt 支援 `<v 語者名>` 標記）
- `.words.json`：逐字時間戳（需 `--format words`）
