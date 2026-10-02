---
title: "ThyVoice"
type: entity
tags: [語者辨識, 語者分離, 端到端系統, 學術系統]
created: 2026-10-02
updated: 2026-10-02
sources: ["Who Said What, and Will It Be Remembered? Evaluating Persistent Speaker Attribution Across Meetings.md"]
free_tier: false
chinese: false
taiwan_made: false
hardware: false
---

# ThyVoice

ThyVoice 是論文 [[persistent-speaker-attribution]] 提出的端到端語者歸屬參考系統，核心設計理念為「**閘控語者證據（gated speaker evidence）**」：在建立聲紋前先偵測與修復重疊語音、拒絕模糊證據，只用可信的乾淨證據建立與更新身分。

## 關鍵屬性

- **性質**：學術研究的端到端參考系統（非商業產品）
- **設計理念**：先分離後辨識（diarization-before-separation）
- **管線組件**：
  - DiariZen md-v2 分離器（重疊感知的語者活動）
  - MossFormer2 來源分離（處理兩人重疊區）
  - WeSpeaker SimAM-ResNet100 語音嵌入器（聲紋）
  - Qwen3-ASR 辨識器

## 效能表現（SI-cpWER，越低越好）

| 條件 | ThyVoice | 次佳商業系統 |
|------|----------|-------------|
| Clean | 34.89 | ElevenLabs 36.13 |
| Noisy | 51.27 | ElevenLabs 53.89 |
| CHiME-6 | 55.24 | PyannoteAI 65.30 |
| **全盤平均** | **47.13** | ElevenLabs 54.75 |

- **三種條件下 SI-cpWER 都低於所有商業級聯系統**
- **身分數量接近真實**：參考 12 位語者，ThyVoice 解析出 14–21 個（商業系統如 PyannoteAI 高達 75–101 個，嚴重過度分裂）

## 與其他實體的關聯

- 辨識器基礎：Qwen3-ASR（非 [[OpenAI Whisper]]）
- 評測對手（商業級聯）：ElevenLabs、PyannoteAI、AssemblyAI、Deepgram、OpenAI
- 評測對手（開源基線）：SE-DiCoW、WhisperX
- 核心概念：[[語者分離與辨識]]

## 備註

- ThyVoice 的價值不只在「準」，更在「跨會議維持穩定身分」——這正是把轉錄當長期記憶的關鍵
- 其「閘控證據」思路（寧可捨棄模糊證據，也不污染身分）對畢業專題的「可靠記憶」設計有參考價值
