---
title: "Who Said What, and Will It Be Remembered? Evaluating Persistent Speaker Attribution Across Meetings"
type: source
tags: [語者辨識, 語者分離, 會議記錄, 評測基準, 學術論文]
created: 2026-10-02
updated: 2026-10-02
sources: ["Who Said What, and Will It Be Remembered? Evaluating Persistent Speaker Attribution Across Meetings.md"]
---

# Who Said What, and Will It Be Remembered?（跨會議的持久性語者歸屬評測）

## 後設資料

- **來源**：arXiv 2609.39344
- **類型**：學術論文（語者分離 / 語者辨識評測）
- **發布**：2026

## 摘要

當語音轉錄被當作「長期記憶」使用時，不只要保留正確的字詞，還要讓同一個人在跨會議時保持穩定的身分。現有的會議轉錄評測指標要麼忽略語者，要麼在每份錄音中獨立重新標記匿名語者，因此無法衡量「同一個人在多場會議中是否維持單一身分」。本論文提出 **SI-cpWER（Speaker Identified cpWER）** 指標，在單一全域語者 ID 對應下為整個語料庫評分。作者在 CHiME-8 NOTSOFAR（129 場會議）與 CHiME-6 上，評測五個商業「先分離後辨識」級聯系統、兩個開源學術基線，以及自家端到端參考系統 **ThyVoice**。

## 主要重點

- **核心問題**：轉錄若要成為可查詢的持久記錄（例如回答「上週這個人決定了什麼」），同一人必須跨會議保有單一身分；否則事實會被連結到錯的人
- **錯誤的不對稱性**：漏字只是降低召回率，但**歸屬錯誤會把某個事實、偏好或承諾掛到錯的人身上**，傷害更大
- **新指標 SI-cpWER**：在整個語料庫用單一全域語者對應計算 cpWER，直接衡量「持久身分」
- **關鍵發現：要求持久身分會改變系統排名**——
  - [[ThyVoice]] 在三種條件下 SI-cpWER 都低於所有商業級聯，全盤平均最低（47.13 vs 次佳 54.75）
  - ElevenLabs 的「單場」cpWER 最低，但換成跨會議 SI-cpWER 就落後（CHiME-6 上 SI-cpWER 比單場 cpWER 高了約 30 個百分點）
- **評測的商業系統**：ElevenLabs、PyannoteAI、AssemblyAI、Deepgram、OpenAI（都共用 PyannoteAI 的聲紋辨識後端）
- **身分膨脹問題**：參考答案 12 位語者，但 PyannoteAI 竟解析出 75–101 個身分、OpenAI 71–124 個（過度分裂）；ThyVoice 維持在 14–21 個，接近真實
- **ThyVoice 的設計核心「閘控語者證據」**：先偵測/修復重疊語音，拒絕模糊證據，只用乾淨證據建立與更新聲紋
- **重疊語音是關鍵難點**：約 30% 評測語音有重疊；用分離+重新匹配策略效果最佳

## 介紹的新實體 / 概念

- [[ThyVoice]] — 本論文的端到端參考系統
- [[語者分離與辨識]] — 本論文的核心概念（含 SI-cpWER、diarization、聲紋）

## 與現有頁面的關聯

- [[ASR技術]] 中提過的「語者分離（Diarization）」在此有深度評測
- 與 [[gladia-speaker-reid]] 同主題（跨會議語者再辨識）
- 直接呼應畢業專題的「完整記憶 + 追蹤誰說了什麼」需求（見 [[2026-08-13-wiki-session]] 的專題構想）

## 個人看法

**這篇對畢業專題極度關鍵。** 你想做的「AI 專案管理系統」要能記住「誰承諾了什麼、誰回報了進度」，本質上就是本論文談的「持久性語者歸屬」問題。論文點出：單場表現好 ≠ 跨會議記憶可靠，而且**歸屬錯誤比漏字更危險**（會把承諾掛到錯的人）。商業大廠（OpenAI、Deepgram）在這個任務上表現並不好，代表這是尚有研究空間的題目。SI-cpWER 這個評測框架也可以借用來驗證你系統的「記憶正確性」。
