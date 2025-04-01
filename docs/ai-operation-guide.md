# AI 工作流程要點（AI Operation Guide）

## 文件目的
讓 AI 清楚知道該如何執行任務、產出內容、使用 Git、紀錄開發日誌等流程與規範。

## 1. 工作目標（AI Objectives）
- 根據 PRD 自動生成程式碼
- 撰寫與補齊相關開發文件（如技術架構、前端指南）
- 建立與更新開發日誌（開發紀錄、Changelog）
- 使用 Git 進行版本控管（含 Commit、Branch、Tag）
- 提供開發建議和問題解決方案

## 2. 任務執行流程（Task Execution Flow）

### 2.1 程式碼生成流程
1. 讀取 PRD 中的「功能需求」、「技術架構」
2. 依模組建立程式檔案（ViewModel, View, Model）
3. 產出程式碼需：
   - 命名規則一致
   - 包含註解
   - 遵循 Lint 規範
   - 實作錯誤處理機制
   - 考慮記憶體管理

### 2.2 文件補齊流程
1. 當有新功能需求時，根據 PRD 補齊以下文件：
   - App Flow Doc
   - Frontend/Backend Guidelines
   - Tech Stack Doc
   - API 文檔（如適用）
2. 所有文件皆需使用 Markdown 格式，標題清楚、層次分明
3. 文件應包含：
   - 目的說明
   - 主要內容
   - 範例說明
   - 相關參考

### 2.3 開發日誌與 Changelog 撰寫
1. 每完成一個模組或功能後：
   - 自動產生一筆日誌紀錄（包含時間、功能、說明）
   - 格式如下：

```
### [2025-04-01] 新增：LoginView 與 ViewModel  
- 完成使用者登入畫面
- 串接假資料來源並顯示錯誤提示
- 實作表單驗證邏輯
```

2. 每次版本完成自動更新 CHANGELOG.md
3. Changelog 應遵循 [Keep a Changelog](https://keepachangelog.com/) 規範
4. 版本號應遵循 [Semantic Versioning](https://semver.org/) 規範

### 2.4 Git 使用流程
1. 每次功能開發須：
   - 建立 feature 分支（如：feature/login-view）
   - 撰寫 Commit 訊息，格式為：

```
Header: <type>(<scope>): <subject>
 - type: 代表 commit 的類別：feat, fix, docs, style, refactor, test, chore，必要欄位。
 - scope 代表 commit 影響的範圍，例如資料庫、控制層、模板層等等，視專案不同而不同，為可選欄位。
 - subject 代表此 commit 的簡短描述，不要超過 50 個字元，結尾不要加句號，為必要欄位。

Body: 72-character wrapped. This should answer:
 * Body 部份是對本次 Commit 的詳細描述，可以分成多行，每一行不要超過 72 個字元。
 * 說明程式碼變動的項目與原因，還有與先前行為的對比。

Footer: 
 - 填寫任務編號（如果有的話）.
 - BREAKING CHANGE（可忽略），記錄不兼容的變動，
   以 BREAKING CHANGE: 開頭，後面是對變動的描述、以及變動原因和遷移方法。
```

2. 每完成一個階段：
   - 合併至 develop 分支
   - 打上版本 Tag（如：v1.0.0）
3. 合併前應確認：
   - 程式碼無編譯錯誤
   - 已通過單元測試
   - 符合程式碼風格規範

## 3. 互動與問題解決

### 3.1 問題分析流程
1. 當遇到開發問題時：
   - 清楚描述問題現象
   - 分析可能的原因
   - 提供至少 2-3 種解決方案
   - 建議最佳實踐方法

### 3.2 程式碼審查與改善
1. 定期審查已生成的程式碼，檢查：
   - 程式碼重複
   - 潛在效能問題
   - 安全性風險
   - 可維護性問題
2. 提供改善建議與重構方案

### 3.3 開發進度回報
1. 定期提供進度摘要：
   - 已完成項目
   - 進行中項目
   - 待解決問題
   - 下一步計劃

## 4. 附錄：代碼風格與標準

### 4.1 程式碼規範
- 檔案與元件命名規則
- 代碼組織與結構
- 註解規範
- 最佳實踐範例

### 4.2 文件規範
- 標題層級使用規則
- 文檔結構範本
- 圖表與程式碼區塊使用
- 專有名詞一致性