# 路線圖

## Phase 1：環境建置與 ASR 實測
- [x] 建立 Python 開發環境（~/asr-env）
- [x] Breeze-ASR-26 vs Taiwan-Tongues-ASR-CE 實測
- [ ] 整合 WhisperX（Whisper + forced alignment + pyannote）
- [ ] 多語 ASR 合併：Whisper + Breeze 輸出整合成正確句子（華語／英語／台語）⭐ 主要 AI 亮點
- [ ] 實測更新的 ASR 模型（親自測，不看網路宣稱）
- [ ] （選做）客語四腔測試，資料來源 speech.hakka.gov.tw
- [ ] FastAPI 基本 API 架構

## Phase 2：語者歸屬（老師最重視）
- [ ] 會前選擇講者人數
- [ ] 跨會議持久化聲紋資料庫（不用每場重新註冊）
- [ ] 未知講者標記「新人一／二」，命名後自動合併
- [ ] （選做）聲紋註冊對應真名
- [ ] 語者歸屬準確率評估，目標 99%+

## Phase 3：即時轉錄（雙軌）
- [ ] 即時軌：WebSocket + VAD + 小模型
- [ ] 即時轉錄網頁顯示
- [ ] 會後軌：batch 精準處理
- [ ] （延後）會中英文翻譯，待翻譯模型測試後再決定

## Phase 4：LLM 萃取與跨會議 Task 追蹤 ⭐ 核心差異化
- [ ] 實作 LLMProvider 抽象層（可切 Ollama / API）
- [ ] 決策萃取 prompt（獨立）
- [ ] 待辦萃取 prompt（獨立，不可與決策合併）
- [ ] SQLite Task schema：task_id 由 DB 產生、owner 來自 diarization
- [ ] 跨會議 Task 狀態追蹤（完成度、負責人、時間）
- [ ] 下次會議自動帶出上次待辦回顧
- [ ] 會議類型 YAML 設定檔

## Phase 5：Meeting RAG 與整合
- [ ] 會議議程附件、歷史紀錄納入 RAG
- [ ] Google Calendar webhook 整合（demo 用，非即時）
- [ ] PII 遮罩（Presidio）
- [ ] （選做）知識圖譜

## Phase 6：前端
- [ ] 近零互動 UI 設計稿（語音／語意驅動）
- [ ] 會議中簡潔動態畫面
- [ ] 會後紀錄與 Task 追蹤頁面（React/Vue）
- [ ] 串接後端 API、基本錯誤處理

## Phase 7：使用者測試與優化
- [ ] 招募測試對象（至少 3 人）
- [ ] Usability test
- [ ] 依回饋修正 UX
- [ ] 效能調校

## Phase 8：簡報與報告
- [ ] 系統說明文件
- [ ] 競品比較（Notta／NotebookLM／GPT／Claude 跨會議追蹤實測）
- [ ] 畢業專題簡報
- [ ] Demo 影片
- [ ] 書面報告
