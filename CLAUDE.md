# LLM Wiki — Schema & Workflow

這是維護此 Wiki 的主要設定檔。每次工作階段開始時請先閱讀此檔案。

## Directory Layout

```
/
├── raw/                  # 不可修改的原始資料 — 請勿更動
│   └── assets/           # 原始資料所引用的已下載圖片
├── wiki/
│   ├── entities/         # 人物、組織、地點、產品
│   ├── concepts/         # 觀念、主題、框架、術語
│   ├── sources/          # 每份原始資料對應一頁摘要
│   ├── analyses/         # 值得保存的查詢解答
│   └── synthesis/        # 跨來源整合分析（比較表、決策樹等）
├── index.md              # 所有 Wiki 頁面的總目錄
├── log.md                # 僅供附加的活動紀錄
└── CLAUDE.md             # 本檔案
```

## Page Conventions

### Frontmatter (YAML)
每個 Wiki 頁面都必須包含 frontmatter：

```yaml
---
title: "Page Title"
type: entity | concept | source | analysis | synthesis
tags: []
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []          # 此頁面所引用的原始資料檔案清單
---
```

### Cross-references
使用 `[[Page Title]]` Obsidian 風格的 wikilink 連結各 Wiki 頁面。  
使用 `[[../raw/filename]]` 引用原始資料。

### Page structure by type

**entity** — 人物、組織、地點、產品
- 一段式描述
- 關鍵屬性（角色、日期、所屬機構等）
- 與其他實體及概念的關聯
- 備註：矛盾之處或待解問題

**concept** — 觀念、框架、主題、術語
- 定義（1–2 句）
- 詳細說明
- 出現場合 / 使用者
- 相關概念
- 備註

**source** — 原始文件的摘要
- 後設資料：標題、作者、日期、URL/檔名、類型
- 摘要（3–5 句）
- 主要主張 / 重點（條列清單）
- 新介紹的實體或概念
- 與現有 Wiki 頁面的關聯
- 個人看法 / 引發的問題

**analysis** — 值得歸檔的查詢解答
- 原始問題
- 解答 / 綜合分析
- 附有引用 Wiki 頁面的佐證
- 可信度與注意事項
- 後續追蹤問題

## Workflows

### Ingest a new source

1. 從 `raw/` 讀取原始資料檔案
2. 若有幫助，與使用者討論重點摘要
3. 建立 `wiki/sources/<slug>.md`，包含完整摘要
4. 針對每個重要實體：建立或更新 `wiki/entities/<name>.md`
5. 針對每個重要概念：建立或更新 `wiki/concepts/<name>.md`
6. 更新 `index.md` — 新增新頁面、更新已變更頁面
7. 附加至 `log.md`：
   ```
   ## [YYYY-MM-DD] ingest | <Source Title>
   Files touched: sources/<slug>.md, entities/..., concepts/...
   Notes: <一行說明變更內容>
   ```

### Answer a query

1. 閱讀 `index.md` 以找出相關 Wiki 頁面
2. 閱讀相關頁面
3. 綜合解答並附上引用（使用 `[[Page]]` 連結）
4. 詢問使用者：「要將此解答歸檔為 Wiki 頁面嗎？」
5. 若是：建立 `wiki/analyses/<slug>.md`，並更新 `index.md` 與 `log.md`

### Lint the wiki

定期檢查：
- 沒有任何入站連結的頁面（孤立頁面）
- 不同頁面中互相矛盾的主張
- 已被提及但缺少專屬頁面的實體或概念
- 列於 `index.md` 但未反映在實體/概念頁面中的資料來源
- `index.md` 中缺漏或過時的條目

以檢查清單形式回報結果，並修正使用者同意的問題。

## Index format

`index.md` 的各節：
- 概覽統計（依類型分類的頁面數量）
- Sources
- Entities
- Concepts
- Analyses
- Synthesis

每筆條目格式：`- [[Page Title]] — 一行描述 *(N sources)*`

## Log format

`log.md` 中的條目以 `## [YYYY-MM-DD] <operation> | <title>` 為前綴，便於搜尋。  
操作類型：`ingest`、`query`、`lint`、`edit`

## Working principles

- 絕不修改 `raw/` 下的任何檔案 — 視其為不可變的事實來源
- 任何 Wiki 變更後，務必更新 `index.md` 與 `log.md`
- 當新資料與現有頁面矛盾時，應明確標註矛盾之處，而非直接覆寫
- 小幅補充時，優先更新現有頁面而非建立新頁面
- 保持頁面標題簡潔一致 — 它們將成為 wikilink 的目標
- 若某概念或實體反覆出現卻無專屬頁面，應為其建立頁面
