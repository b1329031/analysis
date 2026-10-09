---
title: "語碼轉換ASR"
type: concept
tags: [ASR, 語碼轉換, 多語, 低資源語言]
created: 2026-10-09
updated: 2026-10-09
sources: ["Aligning Speech to Languages.md", "Generative Error Correction for Code-Switching ASR.md", "Semi-supervised CS-ASR with LLM Filter.md", "混合語言之語音的語言辨認.md"]
---

# 語碼轉換ASR（Code-Switching ASR, CS-ASR）

**語碼轉換（Code-Switching）**是指說話者在單一句子或對話中混合使用多種語言，例如台灣常見的華台混合語音。**語碼轉換 ASR**是處理此類混合語音的語音辨識技術，核心挑戰是**語言混淆**——模型無法正確辨識語言切換邊界，導致辨識錯誤。

## 詳細說明

### 核心挑戰

1. **語言混淆（Language Confusion）**：切換邊界處模型不確定應使用哪種語言的解碼路徑
2. **訓練資料稀缺**：自然的語碼轉換語音難以蒐集和標注
3. **評測指標特殊**：需使用**混合錯誤率（Mixed Error Rate, MER）**，結合字符錯誤率（CER）與詞錯誤率（WER）

### 改善路線（現代 LLM 方法）

| 方法 | 介入時機 | 代表研究 |
|------|---------|---------|
| 語言對齊損失（LAL） | 訓練期間 | [[aligning-speech-to-languages]] |
| 生成式錯誤修正（GEC） | 推論後處理 | [[generative-ec-cs-asr]]、[[asr-error-correction-llm]] |
| LLM-Filter 半監督 | 訓練資料選擇 | [[semi-supervised-cs-asr-llm]] |

### 語言辨認作為前置任務

在辨識前先判斷每段語音屬於哪種語言，再選用對應的 ASR 模型：
- 早期統計方法：見 [[rocling2007-lid]]（2007 年 ROCLING）
- 現代方法：LAL 以幀級偽語言標籤隱式實現

## 出現場合 / 使用者

- 台灣市場的語音辨識（華語 + 台語 / 台式英語混用）
- 多民族社會的語音助理、字幕生成
- 語言保存計畫的資料標注

## 相關概念

- [[ASR技術]] — 語碼轉換 ASR 是其多語言處理的進階挑戰
- [[ASR錯誤修正]] — 生成式錯誤修正是語碼轉換 ASR 的主要後處理改善手段

## 備註

- Mixed Error Rate (MER) 是語碼轉換場景的專用指標，需區分字符錯誤（中文）與詞錯誤（英文）
- 台語 ASR 工具（[[Whisper-Taiwanese]]、[[myVoca]]）是台灣語碼轉換 ASR 的基礎元件
- 低資源問題是核心瓶頸：真實語碼轉換語音難以標注，LLM 方法（偽標籤精煉）是繞過此問題的可行路線
