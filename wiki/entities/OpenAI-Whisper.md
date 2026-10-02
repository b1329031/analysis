---
title: "OpenAI Whisper"
type: entity
tags: [ASR, 開源模型, OpenAI, 語音辨識]
created: 2026-10-02
updated: 2026-10-02
sources: ["ASR Error Correction using Large Language Models.md", "Better Pseudo-labeling with Multi-ASR Fusion and Error Correction by SpeechLLM.md", "Who Said What, and Will It Be Remembered? Evaluating Persistent Speaker Attribution Across Meetings.md"]
free_tier: true
chinese: true
taiwan_made: false
hardware: false
---

# OpenAI Whisper

OpenAI Whisper 是 OpenAI 推出的大規模開源 ASR（語音辨識）模型，以海量弱監督與多語言資料訓練，成為許多商業與學術語音工具的底層基礎，也是台語工具常見的技術來源。

## 關鍵屬性

- **開發商**：OpenAI
- **性質**：開源模型（可自行部署）
- **模型規模**：提供 base / small / medium / large 等多種尺寸；large-v3 約 15 億參數
- **訓練資料**：約 68 萬小時多語言音訊（含弱標籤與偽標籤）
- **語言**：多語言（含中文、英文），台語需透過提示詞輔助
- **特點**：
  - 內建反正規化（ITN）：自動加標點、大小寫、去除贅字
  - 可離線部署，無 API 費用
  - 成為眾多下游工具的辨識引擎

## 在研究中的角色

- **錯誤修正研究**（[[asr-error-correction-llm]]）：作為被修正的 ASR 系統之一；其 N-best 多樣性較低（候選常只差格式），限制了 N-best 修正效益
- **多 ASR 融合**（[[multi-asr-fusion-speechllm]]）：與 Icefall、Nemo Parakeet 並列為三個融合模型之一（Whisper-large-v3）
- **語者歸屬評測**（[[persistent-speaker-attribution]]）：WhisperX 以 Whisper large-v2 為辨識核心

## 與其他實體的關聯

- 基於 Whisper 的工具：[[Good Tape]]（Tinrec 文章指出其台語能力基於 Whisper）
- 相關辨識模型：[[myVoca]]（台灣在地四語 ASR）
- 串流版本：[[ASR技術]] 提到的「串流 Whisper」（Bloomberg、CPU 下低於 500 毫秒）

## 備註

- Whisper 是「免費但需自行部署」的選項，與商業黑箱 API（[[Otter.ai]]、[[Notta]]）形成對比
- 對台語等低資源語言，Whisper 準確率中上但需提示詞輔助（見 [[tinrec-taiwanese-asr]]）
- 其 ITN 特性雖提升可讀性，卻降低 N-best 多樣性，對後處理錯誤修正不利
