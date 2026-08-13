---
name: ingest
description: 將 raw/ 目錄下的原始資料編譯到 wiki/ 中。處理完成後，將源文件自動移動到 raw/09-archive/ 歸檔。支援 `/ingest` (掃描 raw/ 下所有未歸檔文件) 或 `/ingest <path>` (處理指定文件)。當用戶提到「攝取」、「導入」、「收入」資料，或要求將文件加入知識庫時，也應該觸發此技能。絕對忽略 raw/09-archive/ 目錄。
user-invocable: true
---

# ingest 技能

## 核心工作流：Inbox & Archive

你正在維護一個 **LLM Wiki**（Obsidian 知識庫）。`raw/` 目錄是「待處理收件箱」，`wiki/` 是「編譯輸出層」。

**目錄結構約定：**
- `raw/01-articles/` — 網頁剪藏的 Markdown 文章
- `raw/02-papers/` — 論文和 PDF 文獻
- `raw/03-transcripts/` — 視頻轉錄文案
- `raw/09-archive/` — **已處理文件的歸檔目錄，禁止讀取**
- `wiki/sources/` — 資料摘要
- `wiki/entities/` — 實體（人物、公司、工具、產品）
- `wiki/concepts/` — 概念（框架、方法論、理論）

## 觸發邏輯

1. **用戶執行 `/ingest`**：掃描 `raw/` 所有子目錄（排除 `09-archive/`），找出待處理文件。
2. **用戶執行 `/ingest <path>`**：僅處理指定文件。
3. **隱式觸發**：用戶說「把這個資料攝入知識庫」、「導入這篇文章」時，自動執行 ingest。

## 編譯流水線

對每個待處理源文件，嚴格按以下步驟執行：

### 步驟 1：讀取源文件

- **如果是 `.md` 文件**：使用讀取工具完整讀取內容。
- **如果是 `.pdf` 文件**：使用讀取工具嘗試提取文字。如果無法提取或內容為空，改為記錄文件元信息（文件名、頁數）在 sources 頁面中。

### 步驟 2：提煉核心並翻譯

從源文件中提取：
- **核心主旨**：這段資料講什麼（1-2句話）
- **實體**：人物、公司、工具、產品等具體名詞
- **概念**：框架、方法論、理論等抽象名詞

如果是非中文內容，則翻譯成繁體中文。

### 步驟 3：建立來源摘要

在 `wiki/sources/` 建立 Markdown 文件：

```markdown
---
title: "摘要-文件slug"
type: source
tags: [來源, 原始文件]
sources: [raw/01-articles/xxx.md]
last_updated: YYYY-MM-DD
---

## 核心摘要
[3-5句話的核心總結]

## 關聯連接
- [[EntityName]] — 關聯實體
- [[ConceptName]] — 關聯概念
```

文件名使用 kebab-case：`摘要-{文件slug}.md`

### 步驟 4：知識網路化（實體/概念頁面）

對於步驟 2 提取的每個實體和概念：

**目標目錄：**
- 實體 → `wiki/entities/`
- 概念 → `wiki/concepts/`

**處理邏輯：**
1. 頁面不存在 → 按照 CLAUDE.md 的 Frontmatter 規範建立新頁面
2. 頁面已存在 → 讀取現有內容，**增量合併**新信息
3. **發現衝突** → **立即暫停**，向用戶報告衝突內容，詢問處理方式後再繼續

**頁面模板：**

```markdown
---
title: "頁面名稱"
type: entity | concept
tags: [標籤]
sources: [關聯的源文件]
last_updated: YYYY-MM-DD
---

## 定義
[對該實體/概念的定義]

## 關鍵信息
[從源文件中提取的詳細信息]

## 關聯連接
- [[摘要-source-slug]] — 來源
- [[RelatedEntity]] — 相關實體
```

### 步驟 5：更新全域注冊表

**更新 `wiki/index.md`：**
按照 CLAUDE.md 規定的格式，將新增頁面添加到對應分類下：
- Sources: `[[摘要-source-slug]] — 該資料的核心主旨`
- Entities: `[[EntityName]] — 該實體的身份定義`
- Concepts: `[[ConceptName]] — 該概念的核心定義`

**更新 `wiki/log.md`：**
追加操作日誌（Append-only）：
```markdown
## [YYYY-MM-DD] ingest | 操作簡述
- **變更**: 新增 [[PageName]]; 更新 [[index.md]]
- **衝突**: 無 (或: 衝突 [[ConflictingPage]], 已暫停等待決策)
```

### 步驟 6：歸檔源文件

在確認以下全部完成後，將源文件移動到 `raw/09-archive/` 目錄：
- sources 頁面已建立
- 實體/概念頁面已建立或更新
- index.md 已更新
- log.md 已更新

**絕對禁止修改源文件內部的文字。**

## 衝突處理流程

當發現新舊知識衝突時：

1. **暫停**：停止當前 ingest 流程
2. **報告**：向用戶說明衝突內容（哪個頁面、衝突點是什麼）
3. **詢問**：請用戶選擇處理方式：
   - A) 保留新舊兩者，標注為「知識衝突」
   - B) 用新知識覆蓋舊知識
   - C) 放棄本次 ingest
4. **繼續**：根據用戶選擇繼續或終止

## 注意事項

- 絕對不讀取 `raw/09-archive/` 下的任何文件
- 所有 wiki 頁面必須包含 `## 關聯連接` 區域，不能產生孤島頁面
- 使用繁體中文編寫所有內容
- 實體命名使用 TitleCase，概念和來源使用 kebab-case
