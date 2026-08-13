---
title: "AI會議記錄工作流"
type: concept
tags: [AI, 會議記錄, 工作流, 語音轉文字]
created: 2026-06-24
updated: 2026-06-24
sources: ["2026 AI 會議紀錄工具實測｜8 款語音轉文字與摘要速度大比拚.md", "會議紀錄用AI怎麼做？會議逐字稿如何整理？｜AI語音轉逐字稿教學｜104職場力.md", "2026年最推AI會議記錄神器，省時省力的開會必備工具！.md", "不限時間！3個免費AI逐字稿工具，好用推薦！AI語音筆記生成會議記錄、簡報、心智圖｜104職場力.md"]
---
[[0813]]
# AI會議記錄工作流

利用 AI 工具自動化會議語音轉文字、摘要生成與整理的工作流程。

## 兩種主流模式

### 模式一：整合型工具（一站式）

單一工具包辦錄音/上傳 → 語音轉文字 → AI 摘要生成，整合在同一平台。

代表工具：[[Meeting Ink]]、[[Otter.ai]]、[[SeaMeet]]、[[Vocol.ai]]

優點：流程順暢、不需切換工具  
缺點：依賴特定平台，轉錄和摘要品質綁在一起

### 模式二：分層工作流（轉錄 + LLM）

Step 1：純轉錄工具生成逐字稿（[[CLOVA Note]]）  
Step 2：將逐字稿貼入通用 LLM（ChatGPT、Copilot、Gemini）整理

優點：靈活，可自訂 LLM prompt；轉錄工具可替換  
缺點：需手動銜接兩個工具，逐字稿可能凌亂需要清理

## 技術環節與影響因素

AI 會議記錄工具速度由五大環節決定：

| 環節 | 技術基礎 |
|------|----------|
| 音檔上傳 | 雲端儲存、伺服器佇列 |
| 語音轉文字（STT） | Transformer / Whisper 模型 |
| AI 摘要生成 | LLM（GPT-5、Gemini 2.5 Pro、Claude Opus 4 等） |
| 語者分離（Diarization） | 聲紋辨識 |
| 即時字幕/翻譯 | ASR + 神經機器翻譯（NMT） |

## 選工具的四個評估維度

1. **速度效率**：能否在時限內完成？
2. **功能整合**：是否有需要的功能（即時字幕、語者分段、翻譯）？
3. **場景契合度**：適合語言、設備習慣、會議形式？
4. **價格與實際用量**：評估每月實際使用時數再比較單價

## 工具速度比較（2026年實測，26分鐘英文音檔）

參見 [[ai-meeting-tools-benchmark-2026]]

摘要最快：[[Vurbo.ai]]（18秒）但總流程最慢  
轉文字最快：[[Plaud]]（49秒）但只支援手機  
最均衡：[[Meeting Ink]]

## 注意

AI 生成的會議摘要有虛構風險，需人工驗證重要內容。

## 模式三：免費分層工作流

使用完全免費的工具完成轉錄 + 摘要，無需付費：

- [[Easemate AI]]：網頁即時轉錄（免安裝），支援 AI 聊天提問
- [[inFin]]：App 免費免註冊，一鍵生成摘要/會議記錄/待辦事項
- [[NotebookLM]]：Google 免費助理，可將音訊轉為心智圖或簡報影片

**適合對象**：預算有限、頻率不高、不需要語者分段的個人用戶

## 常見工具與平台的選擇建議

| 需求 | 推薦工具 |
|------|---------|
| 台灣在地化 + 台語支援 | [[Meeting Ink]]、[[myVoca]]（企業 API）|
| 完全免費、不限時間 | [[Easemate AI]]、[[inFin]]、[[NotebookLM]] |
| 多語言（英文為主） | [[Otter.ai]]、[[Notta]] |
| 硬體錄音筆 | [[Plaud]]（NotePin / Plaud Note）|
| 分層工作流（轉錄 + ChatGPT）| [[CLOVA Note]]、[[MyEdit]] + ChatGPT |
| 日文會議 | [[Smartshoki]]、[[Rimo Voice]] |

## 相關工具

- [[Meeting Ink]] · [[CLOVA Note]] · [[Vocol.ai]] · [[Plaud]] · [[Good Tape]] · [[Otter.ai]] · [[雅婷逐字稿]] · [[Vurbo.ai]] · [[SeaMeet]]
- [[MyEdit]] · [[Notta]] · [[tl;dv]] · [[Easemate AI]] · [[inFin]] · [[NotebookLM]]
- [[Smartshoki]] · [[Rimo Voice]]（日文市場）