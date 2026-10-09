---
title: "jb55-Transcribe"
type: entity
tags: [語者分離, 轉錄, CLI, 開源, 工具]
created: 2026-10-09
updated: 2026-10-09
sources: ["jb55 transcribe.md"]
free_tier: true
chinese: true
taiwan_made: false
hardware: false
---

# jb55-Transcribe

`jb55/transcribe` 是命令列工具，整合 whisper.cpp 與 pyannote.audio，輸出帶語者標籤的逐字稿與字幕，支援聲紋註冊命名與跨錄音的語者識別。

## 關鍵屬性

- **作者**：jb55
- **來源**：https://github.com/jb55/transcribe
- **性質**：命令列工具（CLI）
- **語者分離引擎**：pyannote.audio
- **轉錄引擎**：whisper.cpp
- **音訊轉換**：ffmpeg
- **相似度計算**：餘弦相似度（L2 正規化後點積）
- **匹配策略**：貪婪配對（最強配對優先，每個名字只用一次）
- **相似度門檻**：預設 0.55

## 實測相似度分布

| 情境 | 相似度範圍 |
|---|---|
| 同一人不同錄音 | 0.68–0.94 |
| 不同人 | 0.02–0.27 |
| 門檻設定 | 0.55（位於空白地帶） |

## 輸出格式

- `.txt`：逐字稿，每行一個語者輪次，含時間戳
- `.srt` / `.vtt`：字幕（.vtt 支援 `<v 語者名>` 標記）
- `.words.json`：逐字時間戳（需 `--format words`）

## 與其他實體的關聯

- [[Voicetag]] — 同為整合 pyannote 的語者識別工具，voicetag 提供更高階 Python API
- [[OpenAI-Whisper]] — 底層使用 whisper.cpp（Whisper 的 C++ 高效實作）
- [[DiariZen]] — 同為 pyannote 生態系的語者分離工具

## 備註

- 「未知語者保留編號，不強行配對」的保守策略避免錯誤命名
- 管線架構（ffmpeg + whisper.cpp + pyannote 串接）的邊界處理需謹慎
- 安裝推薦使用 uv，需 whisper-cli 和 ffmpeg 在 PATH 上

## 相關概念

- [[語者分離與辨識]] — jb55/transcribe 是此技術的完整命令列實作
