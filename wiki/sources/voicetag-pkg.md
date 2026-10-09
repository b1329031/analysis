---
title: "voicetag（Python 套件）"
type: source
tags: [工具, 語者分離, pyannote, Python套件, 開源]
created: 2026-10-09
updated: 2026-10-09
sources: ["voicetag.md"]
---

# voicetag（Python 套件）

## 後設資料

- **來源**：PyPI — https://pypi.org/project/voicetag/
- **類型**：開源 Python 套件文件
- **發布**：不詳

## 摘要

`voicetag` 是結合 pyannote.audio（語者分離）與 resemblyzer（聲紋 embedding）的 Python 套件，自動判斷「誰在說話、從幾點到幾點」。提供 Python API 與 CLI 介面，支援聲紋註冊（enroll）與識別（identify），可搭配 OpenAI Whisper、Groq、Deepgram 等多種 STT 後端進行含轉錄的語者分離。

## 主要重點

- **雙引擎架構**：pyannote 做分離（誰在哪段說話），resemblyzer 做識別（這段是誰）
- **聲紋庫管理**：`enroll` 命令可添加多個音訊樣本，`profiles` 命令管理聲紋庫
- **多 STT 後端**：可選 openai / groq / whisper（本地）/ deepgram，或不含轉錄僅做分離
- **前置要求**：需到 HuggingFace 接受 pyannote 模型授權條款，設定 `HF_TOKEN`
- **適用場景**：Podcast、訪談、會議、法庭、客服中心

## 介紹的新實體 / 概念

- [[Voicetag]] — 本文的主要說明對象

## 與現有頁面的關聯

- [[語者分離與辨識]] — voicetag 是此技術的高階封裝套件
- [[hf-pyannote-similarity-bug]] — 基於 pyannote，需注意 embedding 相似度異常問題
- [[jb55-Transcribe]] — 同為整合 pyannote 的語者分離工具，voicetag 提供更高階 API

## 個人看法

voicetag 的設計目標是「開箱即用」，適合不想深入設定 pyannote 的使用者。resemblyzer 作為聲紋 embedding 引擎是相對老舊的選擇，效能不如 pyannote/embedding 3.x——但後者有已知的相似度異常問題（見 [[hf-pyannote-similarity-bug]]）。pyannote 的授權牆（HuggingFace 條款確認）是部署障礙，需在初始化時處理。
