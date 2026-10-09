---
title: "南大 Whisper-Taiwanese Tv0.5"
type: source
tags: [ASR, 台語, 開源模型, 台灣]
created: 2026-10-09
updated: 2026-10-09
sources: ["南大 Whisper-Taiwanese Tv0.5.md"]
---

# 南大 Whisper-Taiwanese Tv0.5

## 後設資料

- **作者 / 機構**：李建興教授（國立台南大學）
- **來源**：1111 人力銀行新聞 — https://www.1111.com.tw/news/jobns/161680
- **類型**：新聞報導（非學術論文）
- **發布**：2024-07-22

## 摘要

國立台南大學李建興教授研究團隊於 2024 年 7 月 22 日發布 Whisper-Taiwanese Tv0.5 開源台語 ASR 模型，基於 OpenAI whisper-large-v3-turbo 微調，訓練資料來自國中教科書內容與 TAIDE 機器人系統的學生互動資料，由國科會支持。未來計畫引入 TAIDE 雙語 AI 系統進行台語與英語教學，保存台語文化資產。

## 主要重點

- **底層模型**：OpenAI whisper-large-v3-turbo 微調版
- **訓練資料**：國中教科書 + TAIDE 機器人學生互動資料
- **合作夥伴**：晨輝出版社、女媧機器人公司、關懷文化基金會
- **資助**：國科會 + 國家高速網路與計算中心 + 文化部
- **⚠️ 注意**：資訊來源為新聞稿，準確率需實測，勿依賴官方宣稱數據

## 介紹的新實體 / 概念

- [[Whisper-Taiwanese]] — 南大釋出的台語 ASR 開源模型

## 與現有頁面的關聯

- [[ASR技術]] — 台灣本土 ASR 模型的代表案例
- [[OpenAI-Whisper]] — 本模型基於 whisper-large-v3-turbo 微調
- [[myVoca]] — 同為台灣本土多語 ASR，可相互比較（商業 vs 開源）
- [[混合語言之語音的語言辨認]] — 台語 ASR 的技術背景

## 個人看法

whisper-large-v3-turbo 是效能與速度均衡的版本，作為台語微調基礎合理。國中教科書作為訓練資料的覆蓋範圍有限（偏書面語、非口語），真實對話場景的準確率可能偏低，需實測驗證。v0.5 版本號暗示仍為早期版本。
