---
title: "DiariZen"
type: entity
tags: [語者分離, pyannote, 開源, 深度學習]
created: 2026-10-09
updated: 2026-10-09
sources: ["DiariZen Explained.md"]
free_tier: true
chinese: false
taiwan_made: false
hardware: false
---

# DiariZen

DiariZen 是一個混合架構的開源語者分離系統，結合剪枝版 WavLM-Large encoder、帶 powerset 分類的 Conformer backend 與 VBx 分群，在開源語者分離系統中達到頂尖效能。

## 關鍵屬性

- **架構**：WavLM-Large（剪枝）+ Conformer（powerset 分類）+ VBx（分群）
- **分群方法**：VBx + PLDA 評分
- **輸出格式**：RTTM（Rich Transcription Time Marked）
- **訓練資料**：AMI 會議語料庫等
- **性質**：開源（可自行部署）
- **生態系**：pyannote.audio 生態系的頂尖模型之一

## 技術流程（7 階段）

1. 音訊載入
2. WavLM 特徵提取
3. Conformer 處理
4. 分段聚合
5. 語者 Embedding 提取
6. VBx 分群 + PLDA 評分
7. RTTM 輸出生成

詳見 [[diarizen-explained]]（完整拆解含程式碼與張量圖）

## 與其他實體的關聯

- [[Voicetag]] — 同為語者分離工具，voicetag 是高階封裝，DiariZen 是底層模型
- [[jb55-Transcribe]] — 結合 pyannote 系語者分離與轉錄的工具鏈
- [[OpenAI-Whisper]] — 語者分離常與 Whisper 轉錄串接使用

## 備註

- DiariZen 架構分散於多個程式庫（pyannote、wespeaker、VBx），直接理解有一定門檻
- 教學論文 [[diarizen-explained]] 提供完整的逐步說明，適合想深入理解或客製化的開發者
- RTTM 格式是語者分離評測的標準輸出，可直接接入 pyannote 評測工具

## 相關概念

- [[語者分離與辨識]] — DiariZen 是此概念的頂尖開源實作
