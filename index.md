---
title: "Wiki Index"
updated: 2026-06-25
---

# Wiki Index

> Master catalog of all wiki pages. Updated after every ingest, query filing, or lint pass.

## Stats（自動計算）

```dataview
TABLE length(rows) AS "頁面數"
FROM "wiki"
WHERE type != null
GROUP BY type
SORT length(rows) DESC
```

---

## Sources

```dataview
TABLE WITHOUT ID file.link AS "來源頁面", join(tags, ", ") AS "標籤", updated AS "更新日期"
FROM "wiki/sources"
SORT updated DESC
```

---

## Entities

```dataview
TABLE WITHOUT ID file.link AS "工具 / 實體", join(tags, ", ") AS "標籤", updated AS "更新日期"
FROM "wiki/entities"
WHERE file.name != ".gitkeep"
SORT file.name ASC
```

---

## Concepts

```dataview
TABLE WITHOUT ID file.link AS "概念", join(tags, ", ") AS "標籤", updated AS "更新日期"
FROM "wiki/concepts"
WHERE file.name != ".gitkeep"
SORT file.name ASC
```

---

## Analyses

```dataview
TABLE WITHOUT ID file.link AS "分析", updated AS "更新日期"
FROM "wiki/analyses"
WHERE file.name != ".gitkeep"
SORT updated DESC
```

---

## 🔍 最近更新的頁面

```dataview
TABLE WITHOUT ID file.link AS "頁面", type AS "類型", updated AS "更新日期"
FROM "wiki"
WHERE type != null
SORT updated DESC
LIMIT 10
```

---

## ⚠️ 可能的孤立頁面（無其他頁面連結至此）

```dataview
LIST
FROM "wiki"
WHERE file.name != ".gitkeep" AND type != null AND length(file.inlinks) = 0
SORT file.name ASC
```
