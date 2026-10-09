---
title: "Whisper-Taiwanese"
type: entity
tags: [ASR, 台語, 開源模型, 台灣, 微調]
created: 2026-10-09
updated: 2026-10-09
sources: ["南大 Whisper-Taiwanese Tv0.5.md"]
free_tier: true
chinese: false
taiwan_made: true
hardware: false
---

# Whisper-Taiwanese

Whisper-Taiwanese（Tv0.5）是國立台南大學李建興教授研究團隊於 2024 年發布的開源台語 ASR 模型，基於 OpenAI whisper-large-v3-turbo 微調，由國科會支持，為台語文化保存計畫的一部分。

## 關鍵屬性

- **開發機構**：國立台南大學 / 李建興教授實驗室
- **版本**：Tv0.5（候選版本）
- **底層模型**：OpenAI whisper-large-v3-turbo（微調版）
- **訓練資料**：國中教科書內容 + TAIDE 機器人學生互動資料
- **目標語言**：台灣台語（閩南語）
- **資助**：國科會 + 國家高速網路與計算中心 + 文化部
- **性質**：開源

## 合作夥伴

- 晨輝出版社（教科書內容）
- 女媧機器人公司（硬體支援）
- 關懷文化基金會

## 與其他實體的關聯

- [[OpenAI-Whisper]] — 底層基礎模型（whisper-large-v3-turbo）
- [[myVoca]] — 同為台灣本土語音 ASR，但 myVoca 為商業產品（國台英客四語），Whisper-Taiwanese 為開源（台語專用）

## 備註

- v0.5 暗示仍為早期版本，穩定性與準確率有待驗證
- 訓練資料偏書面語（國中教科書），口語對話場景準確率可能偏低
- 資訊來源為新聞稿，官方宣稱數據需實測驗證
- 預計後續版本（v1.0+）將引入 TAIDE 雙語系統，增加教學用途

## 相關概念

- [[ASR技術]] — 台灣本土 ASR 模型的開源代表
- [[語碼轉換ASR]] — 台語常與華語混用，台語 ASR 是語碼轉換研究的基礎元件
