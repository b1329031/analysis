---
title: "AI會議記錄工具比較表"
type: analysis
tags: [AI, 會議記錄, 工具比較, 整合分析]
created: 2026-06-24
updated: 2026-06-25
sources: ["2026 AI 會議紀錄工具實測｜8 款語音轉文字與摘要速度大比拚.md", "會議紀錄用AI怎麼做？會議逐字稿如何整理？｜104職場力.md", "2026年最推AI會議記錄神器，省時省力的開會必備工具！.md", "AI 會議記錄軟體推薦：5 大 App 實測評比，自動轉文字讓你開會超輕鬆！.md", "不限時間！3個免費AI逐字稿工具，好用推薦！AI語音筆記生成會議記錄、簡報、心智圖｜104職場力.md"]
---

# AI會議記錄工具比較表

> 整合所有已收錄的 AI 會議記錄工具，支援動態篩選。

---

## 所有工具總覽（動態）

```dataview
TABLE WITHOUT ID
  file.link AS "工具",
  chinese AS "中文支援",
  free_tier AS "有免費方案",
  taiwan_made AS "台灣本土",
  hardware AS "需要硬體",
  join(tags, ", ") AS "標籤"
FROM "wiki/entities"
WHERE file.name != ".gitkeep"
SORT taiwan_made DESC, free_tier DESC, file.name ASC
```

---

## 只看有免費方案的工具

```dataview
TABLE WITHOUT ID
  file.link AS "工具",
  chinese AS "中文支援",
  taiwan_made AS "台灣本土",
  join(tags, ", ") AS "標籤"
FROM "wiki/entities"
WHERE free_tier = true AND file.name != ".gitkeep"
SORT taiwan_made DESC, file.name ASC
```

---

## 只看支援中文的工具

```dataview
TABLE WITHOUT ID
  file.link AS "工具",
  free_tier AS "有免費方案",
  taiwan_made AS "台灣本土",
  hardware AS "需要硬體"
FROM "wiki/entities"
WHERE chinese = true AND file.name != ".gitkeep"
SORT taiwan_made DESC, free_tier DESC, file.name ASC
```

---

## 台灣本土工具

```dataview
TABLE WITHOUT ID
  file.link AS "工具",
  free_tier AS "有免費方案",
  chinese AS "中文支援",
  join(tags, ", ") AS "標籤"
FROM "wiki/entities"
WHERE taiwan_made = true AND file.name != ".gitkeep"
SORT file.name ASC
```

---

## 速度實測比較（靜態，2026年測試，26分鐘英文音檔）

> 速度數據來源：[[ai-meeting-tools-benchmark-2026]]（Meeting Ink 官方，具立場偏向）

| 工具              | 上傳                | 轉文字         | 摘要          | 即時字幕 | 語者分段 |
| --------------- | ----------------- | ----------- | ----------- | ---- | ---- |
| [[Meeting Ink]] | 55秒               | 1分58秒       | **26秒** ★最快 | ✔    | ✔    |
| [[SeaMeet]]     | 1分02秒             | 合計 3分46秒    | ←           | ✔    | ✔    |
| [[Vocol.ai]]    | 1分53秒             | 3分29秒       | 1分23秒       | ✘    | ✔    |
| [[Otter.ai]]    | 1分11秒             | 3分35秒       | 2分38秒       | ✔    | ✔    |
| [[Vurbo.ai]]    | 合計 **12分51秒** ★最慢 | ←           | **18秒** ★最快 | ✔    | ✘    |
| [[Plaud]]       | **26秒** ★         | **49秒** ★最快 | 1分03秒       | ✘    | ✘    |
| [[雅婷逐字稿]]       | **17秒** ★最快       | 4分34秒       | 50秒（不穩）     | ✘    | ✔    |
| [[Good Tape]]   | 1分41秒             | 1小時以上       | 不支援         | ✘    | ✘    |

---

## 定價比較（靜態）

| 工具 | 免費方案 | 入門付費 | 計費方式 |
|------|----------|----------|----------|
| [[Meeting Ink]] | 無 | NT$279/月（20小時）| 訂閱 |
| [[SeaMeet]] | 無 | US$9.99/月（20小時）| 訂閱 |
| [[Vocol.ai]] | 無 | US$11/月（5小時）| 訂閱 or 流量包 |
| [[Otter.ai]] | 無 | US$16.99/月（20小時）| 訂閱 |
| [[Vurbo.ai]] | 無 | NT$2,000/月（不限）| 訂閱 |
| [[Plaud]] | 300分鐘/月 | NT$3,300/年（20小時）| 硬體+訂閱 |
| [[Good Tape]] | 無（等待超長）| €15/月（20小時）| 訂閱 |
| [[雅婷逐字稿]] | 無 | NT$156（1小時）| 時數包 |
| [[CLOVA Note]] | 600分鐘/月 | 無付費版 | 完全免費 |
| [[MyEdit]] | 每日點數 | 未揭露 | 點數制 |
| [[Notta]] | 120分鐘/月 | $8.17/月 | 訂閱 |
| [[tl;dv]] | 無限線上錄製 | US$18/月 | 訂閱 |
| [[Easemate AI]] | 無限 | 無 | 完全免費 |
| [[inFin]] | 無限 | 無 | 完全免費 |
| [[NotebookLM]] | 無限 | 無 | 完全免費 |

---

## 選工具決策樹

```
需要台語/客語？
  └─ 是 → [[Meeting Ink]] 或 [[雅婷逐字稿]]

預算為零？
  └─ 是，需要即時轉錄 → [[Easemate AI]]
  └─ 是，需要摘要整理 → [[inFin]] 或 [[CLOVA Note]] + ChatGPT
  └─ 是，需要心智圖/簡報 → [[NotebookLM]]

主要用線上會議（Meet/Teams/Zoom）？
  └─ Teams / Google Meet → [[SeaMeet]]
  └─ 英文國際會議 → [[Otter.ai]]
  └─ 三平台、多語言 → [[Notta]] 或 [[tl;dv]]

行動錄音（外出/訪談）？
  └─ 是 → [[Plaud]]（硬體錄音筆）

需要即時翻譯？
  └─ 是 → [[Vurbo.ai]]（但總流程較慢）

高頻使用、重視效率？
  └─ → [[Meeting Ink]]（速度+功能最均衡）

低頻、按量計費？
  └─ → [[雅婷逐字稿]] 或 [[Vocol.ai]]（V-point）

日文會議？
  └─ 企業 → [[Smartshoki]]
  └─ 個人 → [[Rimo Voice]]
```

---

## 注意事項

- 速度數據測試條件為免費版 + 26分鐘英文音檔，付費版或中文音檔結果可能不同
- [[Meeting Ink]] 評測來自其官方部落格，具有立場偏向
- [[Plaud]] Top5 排行由 Plaud 官方撰寫，自評第一，立場偏向
- [[CyberLink]] 文章主推 [[MyEdit]]，具商業立場
- AI 摘要可能虛構內容，重要會議記錄需人工驗證
