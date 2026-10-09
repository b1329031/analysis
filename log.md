# Wiki Log

> Append-only record of all wiki activity.  
> Parse recent entries: `grep "^## \[" log.md | tail -10`

---

## [2026-06-24] init | Wiki created
Files touched: CLAUDE.md, index.md, log.md, directory structure
Notes: Initial scaffold created. No sources ingested yet.

## [2026-06-24] ingest | 2026 AI 會議紀錄工具實測｜8 款語音轉文字與摘要速度大比拚
Files touched: sources/ai-meeting-tools-benchmark-2026.md, entities/Meeting-Ink.md, entities/Vocol-ai.md, entities/Plaud.md, entities/Good-Tape.md, entities/Otter-ai.md, entities/雅婷逐字稿.md, entities/Vurbo-ai.md, entities/SeaMeet.md, concepts/AI會議記錄工作流.md, index.md
Notes: Meeting Ink官方評測，8款工具速度數據與訂閱價格，具立場偏向需保留審慎態度。

## [2026-06-24] query | AI會議記錄工具比較表
Files touched: wiki/synthesis/AI會議記錄工具比較表.md, index.md
Notes: 整合兩篇來源，建立速度/功能/定價比較表 + 決策樹，存入 wiki/synthesis/。

## [2026-06-24] ingest | 會議紀錄用AI怎麼做？｜104職場力
Files touched: sources/104-ai-meeting-tutorial.md, entities/CLOVA-Note.md, index.md
Notes: 2024年教學文，介紹CLOVA Note + ChatGPT分層工作流，與整合型工具形成互補視角。

## [2026-06-25] ingest | 2026年最推AI會議記錄神器（CyberLink/MyEdit）
Files touched: sources/cyberlink-myedit-meeting-2026.md, entities/MyEdit.md, entities/Notta.md, entities/tl;dv.md, index.md
Notes: CyberLink推廣文，主推MyEdit+ChatGPT三步驟工作流，Notta/tl;dv資訊可信度較高。

## [2026-06-25] ingest | AI會議記錄軟體Top5（Plaud官方）
Files touched: sources/plaud-ai-meeting-top5.md, entities/Smartshoki.md, entities/Rimo-Voice.md, entities/Plaud.md（更新）, index.md
Notes: Plaud官方自評文，補充Notta/Otter.ai資訊，新增NotePin硬體、免費方案、安全認證至Plaud頁面。

## [2026-06-25] ingest | ASR語音AI生態系｜myVoca（台灣大哥大）
Files touched: sources/twm-myvoca-asr.md, entities/myVoca.md, concepts/ASR技術.md, index.md
Notes: 台灣大哥大官方行銷文，介紹國台英客四語混合ASR模型myVoca，同步建立ASR技術概念頁。

## [2026-06-25] ingest | 不限時間！3個免費AI逐字稿工具（104職場力）
Files touched: sources/104-free-transcription-tools.md, entities/Easemate-AI.md, entities/inFin.md, entities/NotebookLM.md, concepts/AI會議記錄工作流.md（更新）, index.md
Notes: 補充免費工具選項，更新AI會議記錄工作流加入「免費分層工作流」模式三。

## [2026-06-25] ingest | ASR語音轉文字技術（LargitData）
Files touched: sources/largitdata-asr-technology.md, concepts/ASR技術.md（更新）, index.md
Notes: 技術深度文，涵蓋ASR四階段發展、2026串流辨識趨勢、生成式AI整合，補充ASR技術概念頁內容。

## [2026-06-25] edit | 強化 Wiki 結構（Dataview + 統一欄位 + wikilink）
Files touched: 全部 18 個 entities/*.md（frontmatter），wiki/synthesis/AI會議記錄工具比較表.md，index.md
Notes: 為所有 entity 頁面新增 free_tier / chinese / taiwan_made / hardware 四個統一欄位；比較表改為 Dataview 動態查詢（支援篩選免費/中文/本土工具）；index.md 改為 Dataview 自動統計；補強各 entity 頁面之間的 wikilink 交叉連結。

## [2026-08-02] ingest | 5篇新文章（Tinrec部落格 × 3、leadingmrk、104職場力）
Files touched: sources/tinrec-5tools-guide.md, sources/tinrec-9tools-2026.md, sources/leadingmrk-8tools-comparison.md, sources/104-voicetext-5tools.md, sources/tinrec-taiwanese-asr.md, entities/Tinrec.md, entities/RecCloud.md, entities/Memo-AI.md, entities/Typeless.md, entities/AudioPen.md, entities/Wispr-Flow.md, entities/cSubtitle.md, entities/Litok.md, entities/Otter-ai.md（更新）, entities/雅婷逐字稿.md（更新）, wiki/synthesis/AI會議記錄工具比較表.md（更新）, index.md
Notes: 新增 8 款工具（Tinrec、RecCloud、Memo AI、Typeless、AudioPen、Wispr Flow、cSubtitle、Litok）；更新 Otter.ai（補充簡體中文支援與免費方案 300分/月）；更新雅婷逐字稿（補充一次性 300 分鐘免費試用）；比較表加入新工具、修正資料、更新決策樹與注意事項；引入「語音輸入法」與「語音筆記」新類別。

## [2026-10-02] ingest | 4篇學術論文（ASR錯誤修正 + 語者歸屬）
Files touched: sources/asr-error-correction-llm.md, sources/multi-asr-fusion-speechllm.md, sources/persistent-speaker-attribution.md, sources/gladia-speaker-reid.md, concepts/ASR錯誤修正.md, concepts/語者分離與辨識.md, entities/OpenAI-Whisper.md, entities/ThyVoice.md, concepts/ASR技術.md（更新）, index.md
Notes: 攝入 3 篇 arXiv 論文 + 1 篇 Gladia 部落格（內容未擷取，建存根）；新增概念「ASR錯誤修正」「語者分離與辨識」；新增實體 OpenAI Whisper、ThyVoice；ASR技術頁補上新概念與來源連結。論文主題（LLM 錯誤修正、持久性語者歸屬）與畢業專題高度相關。

## [2026-10-09] ingest | 13篇原始資料（語碼轉換ASR + 即時轉錄 + 語者分離工具）
Files touched: sources/aligning-speech-to-languages.md, sources/taiwanese-spoken-lm.md, sources/diarizen-explained.md, sources/generative-ec-cs-asr.md, sources/hf-pyannote-similarity-bug.md, sources/hyporadise.md, sources/semi-supervised-cs-asr-llm.md, sources/voicestreamai.md, sources/whisper-streaming.md, sources/jb55-transcribe.md, sources/voicetag-pkg.md, sources/nknu-whisper-taiwanese.md, sources/rocling2007-lid.md, entities/DiariZen.md, entities/Whisper-Streaming.md, entities/SimulStreaming.md, entities/VoiceStreamAI.md, entities/jb55-Transcribe.md, entities/Voicetag.md, entities/Whisper-Taiwanese.md, concepts/語碼轉換ASR.md（新增）, concepts/即時串流轉錄.md（新增）, concepts/ASR錯誤修正.md（更新）, concepts/語者分離與辨識.md（更新）, concepts/ASR技術.md（更新）, index.md
Notes: 攝入學術論文 7 篇（LAL/語碼轉換、HyPoradise、DiariZen、生成式EC-CS-ASR、半監督CS-ASR、台灣華語口語LM、ROCLING 2007）、工具文件 4 篇（VoiceStreamAI、Whisper-Streaming、jb55/transcribe、voicetag）、產品新聞 1 篇（南大Whisper-Taiwanese）、論壇踩雷 1 篇（pyannote相似度全1.000）；新增概念「語碼轉換ASR」「即時串流轉錄」；新增實體 7 個；更新概念頁 3 個；原始資料已歸檔至 raw/09-archive/。
