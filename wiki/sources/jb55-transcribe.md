---
title: "jb55/transcribe"
type: source
tags: [工具, 語者分離, 轉錄, CLI, 開源]
created: 2026-10-09
updated: 2026-10-09
sources: ["jb55 transcribe.md"]
---

# jb55/transcribe

## 後設資料

- **作者**：jb55
- **來源**：GitHub — https://github.com/jb55/transcribe
- **類型**：開源工具文件
- **發布**：不詳

## 摘要

`transcribe` 是命令列工具，整合 whisper.cpp 與 pyannote.audio，輸出帶語者標籤的逐字稿（txt）與字幕（srt/vtt）。流程：ffmpeg 轉換格式 → whisper.cpp 轉錄 → pyannote 語者分離 → 貪婪配對（最強匹配優先）。支援 `--enroll` 聲紋註冊，後續轉錄自動套用名字；未知語者保留編號，不強行配對。

## 主要重點

- **管線架構**：每個工具各司其職，ffmpeg + whisper.cpp + pyannote 串接
- **貪婪配對**：餘弦相似度最強配對優先，每個名字只用一次
- **實測相似度分布**：同人 0.68–0.94，不同人 0.02–0.27，門檻設定 0.55
- **輸出格式**：txt（逐字稿）、srt（字幕）、vtt（支援 `<v 語者名>` 標記）、words.json（逐字時間戳）
- **安裝**：推薦使用 uv，需 whisper-cli 和 ffmpeg 在 PATH 上

## 介紹的新實體 / 概念

- [[jb55-Transcribe]] — 本文的主要說明對象

## 與現有頁面的關聯

- [[語者分離與辨識]] — 實作貪婪配對的語者分離與命名機制
- [[OpenAI-Whisper]] — 底層使用 whisper.cpp（Whisper 的 C++ 實作）
- [[hf-pyannote-similarity-bug]] — 使用 pyannote 做語者分離，相似度門檻設定需謹慎

## 個人看法

相似度門檻 0.55 設在同人（0.68–0.94）與不同人（0.02–0.27）之間的空白地帶，設計合理。「未知語者保留編號、不強行配對」的策略保守但正確，避免錯誤命名比匿名更糟的情況。管線架構的優點是可獨立替換任一元件，缺點是兩條時間軸（whisper 的分段 vs pyannote 的分段）需要對齊，邊界處理需小心。
