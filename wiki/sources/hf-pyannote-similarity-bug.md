---
title: "HF 論壇：相似度全部 1.000 的踩雷"
type: source
tags: [語者辨識, pyannote, debug, 論壇]
created: 2026-10-09
updated: 2026-10-09
sources: ["HF 論壇：相似度全部 1.000 的踩雷.md"]
---

# HF 論壇：相似度全部 1.000 的踩雷

## 後設資料

- **來源**：HuggingFace Discuss 論壇
- **URL**：https://discuss.huggingface.co/t/speaker-verification-all-speakers-getting-perfect-1-000-similarity-scores/140088
- **類型**：論壇問題紀錄（尚無官方解答）
- **發布**：不詳

## 摘要

使用 `pyannote/embedding`（版本 3.1.1）進行語者驗證時，所有語者的餘弦相似度分數均為 0.999+ 到 1.000，即使男女聲明顯不同也一樣。這是一個開放問題，尚無確定解答。實踐建議：接入正式流程前，先用已知不同聲音測試確認分布合理（同人 0.6–0.9，不同人 0.0–0.3）。

## 主要重點

- **問題**：pyannote/embedding 3.1.1 所有語者相似度均為 1.000
- **受影響條件**：embedding 形狀 `[1, 512]`，有做 L2 正規化
- **可能原因**（均未確認）：
  1. L2 正規化後嵌入空間分布異常，餘弦相似度（即點積）全趨近 1.0
  2. pyannote 版本不相容
  3. 音訊前處理錯誤（採樣率、聲道數）
  4. 模型權重未正確載入（HuggingFace token / 授權問題）
- **健康分布參考**：同人 0.6–0.9，不同人 0.0–0.3

## 介紹的新實體 / 概念

- [[語者分離與辨識]] — 語者驗證（Speaker Verification）是其核心子任務

## 與現有頁面的關聯

- [[語者分離與辨識]] — 記錄了實作 pyannote embedding 時的常見陷阱
- [[Voicetag]] — 基於 pyannote 的工具，同樣需注意此 embedding 問題
- [[jb55-Transcribe]] — 使用 pyannote 做語者分離，相似度門檻設定 0.55

## 個人看法

這種「看起來正常運行但結果全錯」的 silent failure 特別危險——沒有 error message，輸出也不是 None，只是數字不對。在語者辨識流程中加入「健全性測試（sanity check）」是必要的防護措施。L2 正規化後再做餘弦相似度在理論上應該有效，推測是版本問題或前處理問題較大。
