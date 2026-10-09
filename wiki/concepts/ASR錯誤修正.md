---
title: "ASR錯誤修正"
type: concept
tags: [ASR, 錯誤修正, LLM, 後處理]
created: 2026-10-02
updated: 2026-10-09
sources: ["ASR Error Correction using Large Language Models.md", "Better Pseudo-labeling with Multi-ASR Fusion and Error Correction by SpeechLLM.md", "HyPoradise.md", "Aligning Speech to Languages.md", "Generative Error Correction for Code-Switching ASR.md", "Semi-supervised CS-ASR with LLM Filter.md"]
---

# ASR錯誤修正（ASR Error Correction, EC）

**ASR 錯誤修正**是在語音辨識系統輸出後，透過後處理步驟自動偵測並修正辨識錯誤的技術，用以提升轉錄的可讀性與正確性。其最大價值在於：**不需存取底層 ASR 模型的程式碼或權重**，即可改善黑箱 ASR 系統（如商業 API）的表現。

## 詳細說明

傳統 ASR 錯誤修正從規則式系統起步，演進到端到端注意力模型，再到以大型語言模型（LLM）為基礎的方法。核心輸入形式有兩種：

- **1-best 假設**：只用 ASR 最可能的單一輸出
- **N-best 清單**：用 ASR 波束搜尋產生的前 N 個候選句，提供更豐富的上下文線索（效果更好）

### 兩種實作路線

| 路線 | 代表方法 | 特點 |
|------|---------|------|
| **微調（Fine-tuning）** | N-best T5、LoRA LLM | 針對特定 ASR 訓練，表現穩定但需訓練資料 |
| **零樣本（Zero-shot）** | ChatGPT / GPT-4 | 免訓練，GPT-4 可超越微調 T5，但對某些 ASR（如 Whisper）效果有限 |

### 解碼策略（控制生成範圍）

1. **無受限解碼（uncon）**：自由生成，GPT-4 等強模型表現最好
2. **N-best 受限解碼（constr）**：只能從候選清單選，貼近原始語音
3. **N-best 最近解碼（closest）**：生成後找 Levenshtein 距離最近的候選
4. **格狀受限解碼（lattice）**：擴大到合併路徑的格狀空間

### 進階：多模態與多模型融合

- **多 ASR 融合**：結合不同架構 ASR 的 N-best，LLM 作為集成工具，WER 可降 32–36%（見 [[multi-asr-fusion-speechllm]]）
- **SpeechLLM（語音大模型）**：同時納入文字假設與原始聲學證據，比純文字 LLM 更能消歧，可用於偽標籤生成

### 語碼轉換場景的特殊方法

- **語言對齊損失（LAL）**：在訓練期間對齊聲學特徵與偽語言標籤，幀級語言識別能力，搭配 LLM 修正可達 14.1% 相對改善（見 [[aligning-speech-to-languages]]）
- **生成式修正 + LoRA**：多 ASR N-best + LLM LoRA 微調，顯著降低混合錯誤率（MER）（見 [[generative-ec-cs-asr]]）
- **LLM-Filter 半監督**：LLM 精煉偽標籤，用於訓練資料選擇而非推論後處理（見 [[semi-supervised-cs-asr-llm]]）

### 基準資料集：HyPoradise

**HyPoradise（HP）**（NeurIPS 2023）是此領域最重要的開源 benchmark：
- 33 萬+ 組 N-best 假設與正確轉錄配對，橫跨多個語音領域
- 展示生成式修正可突破「N-best oracle 上限」——LLM 能修正 N-best 中根本不存在的 token
- 詳見 [[hyporadise]]

## 出現場合 / 使用者

- 商業黑箱 ASR 的後處理（無法微調底層時的首選改善手段）
- 半監督 ASR 訓練的偽標籤生成
- 低資源語言（如台語、客語）的語料自動標註
- 語碼轉換場景的混合錯誤率改善

## 相關概念

- [[ASR技術]] — 本概念是其「生成式 AI 增強 ASR」的具體化
- [[語者分離與辨識]] — 同為 ASR 的延伸技術環節
- [[語碼轉換ASR]] — 語碼轉換場景下的錯誤修正是本概念的重要子領域

## 備註

- Whisper 的 N-best 多樣性低（因內建反正規化 ITN，候選常只差格式不差內容），限制了 N-best 修正的效益
- 零樣本路線需注意「資料污染」：測試集可能已被 LLM 預訓練看過，導致評估偏高
- LoRA 使 LLM 修正語碼轉換 ASR 的成本大幅降低，是低資源語言的可行路線
