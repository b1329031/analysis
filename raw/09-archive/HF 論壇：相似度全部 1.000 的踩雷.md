---
title: "HF 論壇：相似度全部 1.000 的踩雷"
source: "https://discuss.huggingface.co/t/speaker-verification-all-speakers-getting-perfect-1-000-similarity-scores/140088"
author:
published:
created: 2026-10-09
description: "使用 pyannote/embedding 3.1.1 時所有語者餘弦相似度都跑出 1.000 的問題與討論"
tags:
  - "clippings"
  - "diarization"
  - "speaker-recognition"
  - "debug"
---

## 問題描述

使用 `pyannote/embedding`（版本 3.1.1）進行語者驗證時，**所有語者的相似度分數都是 0.999+ 到 1.000**，即使是明顯不同的聲音（如男聲 vs 女聲）也一樣。

原文關鍵描述：
> "Every speaker gets similarity scores of 0.999+ to 1.000...Even clearly different voices (male/female) get perfect matches"

## 技術細節

- 使用的模型：`pyannote/embedding`（v3.1.1）
- reference 和 test embedding 的形狀：`[1, 512]`
- 後處理有做 L2 正規化（`F.normalize()`）
- 測試音訊為高品質 FLAC 檔

## 可能原因（待確認）

這是一個**尚未解決的開放問題**，論壇尚無明確解答。可能的方向：

1. **L2 正規化後再做餘弦相似度**：如果 embedding 已經 L2 正規化，那餘弦相似度本質上就是點積，結果可能因 embedding 空間的分布問題而全部趨近 1.0
2. **版本不相容**：pyannote 不同版本之間的 embedding 提取方式可能有差異
3. **音訊前處理問題**：採樣率、聲道數是否正確轉換
4. **模型權重未正確載入**：確認 HuggingFace token 與模型授權

## 踩雷重點

使用 pyannote embedding 做語者驗證前，務必先用已知的不同聲音測試，確認相似度分布合理（同人 0.6-0.9，不同人 0.0-0.3），再接入正式流程。
