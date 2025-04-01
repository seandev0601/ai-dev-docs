# AI 工作流程要點（AI Operation Guide）

## 文件目的
讓 AI 清楚知道該如何執行天氣 App 開發任務、產出內容、使用 Git、紀錄開發日誌等流程與規範。

## 1. 工作目標（AI Objectives）
- 根據 PRD 自動生成 iOS 天氣 App 程式碼，使用 SwiftUI 框架
- 整合 Apple WeatherKit 實現天氣預報功能
- 撰寫與補齊相關開發文件（如技術架構、前端指南）
- 建立與更新開發日誌（開發紀錄、Changelog）
- 使用 Git 進行版本控管（含 Commit、Branch、Tag）
- 提供開發建議和問題解決方案，特別是 WeatherKit 整合相關問題

## 2. 任務執行流程（Task Execution Flow）

### 2.1 程式碼生成流程
1. 讀取 PRD 中的「功能需求」、「技術架構」
2. 依模組建立程式檔案（遵循 MVVM 架構）：
   - ViewModels（管理天氣資料與業務邏輯）
   - Views（顯示天氣資訊的 SwiftUI 畫面）
   - Models（天氣資料模型與 WeatherKit 整合）
3. 產出程式碼需：
   - 符合 Swift 命名規範（駝峰式命名法）
   - 包含詳細註解說明功能用途
   - 遵循 SwiftUI 最佳實踐
   - 實作錯誤處理機制（網路問題、權限拒絕等）
   - 考慮記憶體管理與效能優化

### 2.2 文件補齊流程
1. 當有新功能需求時，根據 PRD 補齊以下文件：
   - App Flow Doc（使用者操作流程、畫面轉換）
   - Frontend Guidelines（SwiftUI 元件設計、重用性）
   - Tech Stack Doc（WeatherKit、CoreLocation 等技術說明）
   - API 整合文檔（WeatherKit API 使用方式）
2. 所有文件皆需使用 Markdown 格式，標題清楚、層次分明
3. 文件應包含：
   - 目的說明
   - 主要內容
   - 程式碼範例
   - 相關參考文件（如 Apple 官方文件連結）

### 2.3 開發日誌與 Changelog 撰寫
1. 每完成一個模組或功能後：
   - 自動產生一筆日誌紀錄（包含時間、功能、說明）
   - 格式如下：

```
### [2025-04-01] 新增：WeatherView 與 WeatherViewModel  
- 完成現在位置天氣顯示畫面
- 整合 WeatherKit 取得即時天氣資料
- 實作下拉刷新功能
```

2. 每次版本完成自動更新 CHANGELOG.md
3. Changelog 應遵循 [Keep a Changelog](https://keepachangelog.com/) 規範
4. 版本號應遵循 [Semantic Versioning](https://semver.org/) 規範

### 2.4 Git 使用流程
1. 每次功能開發須：
   - 建立 feature 分支（如：feature/current-weather-view）
   - 撰寫 Commit 訊息，格式為：

```
Header: <type>(<scope>): <subject>
 - type: 代表 commit 的類別：feat, fix, docs, style, refactor, test, chore，必要欄位。
 - scope 代表 commit 影響的範圍，例如 weatherkit, location, ui 等，為可選欄位。
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
   - 已通過單元測試（特別是 WeatherKit 整合測試）
   - 符合 Swift 程式碼風格規範

## 3. 互動與問題解決

### 3.1 問題分析流程
1. 當遇到開發問題時：
   - 清楚描述問題現象
   - 分析可能的原因（如 WeatherKit 權限問題、資料格式不符）
   - 提供至少 2-3 種解決方案
   - 建議最佳實踐方法

### 3.2 程式碼審查與改善
1. 定期審查已生成的程式碼，檢查：
   - 程式碼重複
   - SwiftUI 效能問題（如過多重繪）
   - 位置權限與隱私風險
   - API 呼叫頻率與節流控制
2. 提供改善建議與重構方案

### 3.3 開發進度回報
1. 定期提供進度摘要：
   - 已完成項目（如「現在位置天氣顯示」）
   - 進行中項目（如「天氣預報列表」）
   - 待解決問題（如「API 整合錯誤處理」）
   - 下一步計劃

## 4. 附錄：代碼風格與標準

### 4.1 程式碼規範
- 檔案與元件命名規則：
  - View 以 「View」結尾（如 CurrentWeatherView）
  - ViewModel 以 「ViewModel」結尾（如 WeatherViewModel）
  - Model 使用描述性名稱（如 WeatherData, LocationModel）
- 代碼組織與結構：
  - 依功能劃分資料夾（Models, Views, ViewModels, Services）
  - 共用元件放置於 Components 資料夾
- 註解規範：
  - 所有 public 方法與屬性需有文檔註解（/// 格式）
  - 複雜邏輯需加上註解說明目的
- 最佳實踐範例：
  - 使用 @MainActor 處理 UI 更新
  - 實作適當的錯誤處理

### 4.2 文件規範
- 標題層級使用規則：
  - # 主標題（文件標題）
  - ## 章節標題
  - ### 子章節標題
  - #### 段落標題
- 文檔結構範本：
  - 檔案開頭說明文件目的
  - 章節間保持適當空行
  - 相關內容分組呈現
- 圖表與程式碼區塊使用：
  - 程式碼使用 ```swift 標記
  - 流程圖使用 mermaid 標記（如適用）
- 專有名詞一致性：
  - WeatherKit 大小寫保持一致
  - 功能名稱中英對照表
