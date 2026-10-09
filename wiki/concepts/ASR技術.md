---
title: "ASR技術"
type: concept
tags: [ASR, 語音辨識, 深度學習, 技術概念]
created: 2026-06-25
updated: 2026-10-09
sources: ["人工智慧時代來臨！ASR語音轉文字技術創新與實際應用.md", "ASR語音AI生態系｜最新ASR模型myVoca誕生!更快更準更省｜台灣大哥大企業服務.md", "Building a Taiwanese Mandarin Spoken Language Model.md", "南大 Whisper-Taiwanese Tv0.5.md"]
---

# ASR技術

**ASR（Automatic Speech Recognition，自動語音辨識）** 是一種將人類語音轉換為文字的技術，是語音 AI 系統的核心感知模組。

## 技術發展四階段

| 時期 | 方法 | 特點 |
|------|------|------|
| 1950s | 模式匹配 | 比對聲音與已知語音模式，準確率低 |
| 1970s–1990s | 統計模型（HMM） | 捕捉語音時間序列特徵，但面臨變異性挑戰 |
| 2000s– | 深度學習（端到端模型） | 直接從語音生成文字，大幅提升準確率 |
| 現在 | 多模態融合 | 結合視覺、語言模型，成為 AI Agent 感知前端 |

## 技術原理

深度學習驅動的 ASR 主要流程：
1. **數據收集與預處理**：去除雜音、音頻標準化
2. **特徵提取**：轉換為頻譜特徵（MFCC、MEL）
3. **建立深度學習模型**：RNN、LSTM、GRU 或 Transformer
4. **模型訓練**：反向傳播 + 梯度下降最佳化
5. **語言模型輔助解碼**：引入上下文資訊提升準確性
6. **部署與應用**

## 2026 年最新發展

### 串流辨識與超低延遲

詳細技術方案見 [[即時串流轉錄]]。

- **GPT-4o Realtime API**（OpenAI）：端對端延遲最低 **200 毫秒**
- **Bloomberg 串流 Whisper**：CPU 條件下低於 **500 毫秒**，準確率接近離線模型
- **Deepgram Nova-3**：低延遲、高噪音準確率，主流企業即時轉錄選擇
- **Canary Qwen 2.5B**：Hugging Face Open ASR 排行榜第一，WER **5.63%**
- **[[Whisper-Streaming]]**：Local Agreement Policy，~3.3 秒延遲，開源可自建

### 語音 AI Agent

ASR 不再只是「轉文字工具」，而是語音 AI Agent 的**感知前端**：
- 結合多模態 RAG 在企業資料中定位答案並語音輸出
- 預計 2026 年底企業整合率從 **5% 升至 40%**
- 情緒辨識可使客服問題升級率降低約 **25%**
- 台大李宏毅實驗室的台灣華語口語 LM 代表下一代全雙工語音對話（見 [[taiwanese-spoken-lm]]）

### 成本大幅下降

- GPT-4o 等主流模型推理成本較一年前下降超過 **90%**

## 生成式 AI 增強 ASR 的四種方式

1. **後處理校正**：用 LLM 修正轉錄錯誤，錯誤率可降低約 11%（深化見 [[ASR錯誤修正]]）
2. **上下文補全**：填補省略、代詞，提升可讀性
3. **多語言翻譯**：語音直接翻譯為目標語言
4. **自動摘要與結構化輸出**：自動生成會議要點、決策事項、待辦任務

## 應用場景

- 智慧助手（Siri、Google Assistant、Alexa）
- 語音轉文字服務（[[雅婷逐字稿]]、[[CLOVA Note]]、[[Good Tape]]）
- 客服中心 IVR 自動應答
- 醫療記錄（Nuance Dragon Medical One）
- 語言學習（Duolingo、Rosetta Stone）
- 企業會議記錄（[[Meeting Ink]]、[[Otter.ai]]、[[myVoca]]）

## 優勢與挑戰

**優勢**：提升效率、擴大可用性（輔助障礙用戶）、支援多語言溝通

**挑戰**：
- 噪音/方言/口音環境下準確率仍有限
- 語碼轉換（多語混合）場景是核心難題（見 [[語碼轉換ASR]]）
- 上下文與語意理解仍不完整
- 語音資料的隱私與安全疑慮

## 台灣本土案例

- [[myVoca]]：台灣大哥大 × 長問科技，支援國台英客四語混合辨識，正確率最高 97%
- [[Whisper-Taiwanese]]：南大李建興教授研究團隊，基於 whisper-large-v3-turbo 微調的開源台語 ASR 模型

## 相關概念

- [[AI會議記錄工作流]]（ASR 的主要應用場景之一）
- [[ASR錯誤修正]]（用 LLM 後處理修正 ASR 錯誤，屬「生成式 AI 增強 ASR」的深化）
- [[語者分離與辨識]]（ASR 的延伸技術環節：標記「誰說了什麼」）
- [[語碼轉換ASR]]（多語混合語音的 ASR 挑戰）
- [[即時串流轉錄]]（ASR 在即時場景的應用形式）

## 相關來源

- [[largitdata-asr-technology]]
- [[twm-myvoca-asr]]
- [[asr-error-correction-llm]]（LLM 錯誤修正）
- [[multi-asr-fusion-speechllm]]（多 ASR 融合與 SpeechLLM）
- [[persistent-speaker-attribution]]（跨會議語者歸屬評測）
- [[taiwanese-spoken-lm]]（台灣華語口語 LM）
- [[nknu-whisper-taiwanese]]（南大台語 ASR 模型）
