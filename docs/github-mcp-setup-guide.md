# Cursor IDE GitHub MCP 設置教學

## 目錄
1. [簡介](#簡介)
2. [環境準備](#環境準備)
3. [安裝步驟](#安裝步驟)
4. [與 Agent 互動使用 GitHub MCP](#與-agent-互動使用-github-mcp)
   - [使用技巧](#使用技巧)
   - [基本對話指令](#基本對話指令)
   - [實際對話範例](#實際對話範例)

## 簡介
本教學將指導您如何在 Cursor IDE 中設置 GitHub MCP（Mission Control Protocol）。通過 Composio 的 MCP，我們可以直接在 Cursor IDE 中使用 GitHub 的功能。

## 環境準備
在開始之前，請確保您已具備：
- Node.js 環境
- Cursor IDE 最新版本
- GitHub 帳號
- 命令行終端機（Terminal）

## 安裝步驟

### 1. 安裝 Composio MCP
在終端機中執行以下命令：
```bash
npx @composio/mcp@latest setup "https://mcp.composio.dev/github/mealy-millions-grass-1lDTiR" --client cursor
```

### 2. 設置過程說明
安裝命令會：
- 下載必要的 MCP 組件
- 配置 Cursor IDE 整合
- 設置 GitHub 認證
- 生成必要的配置文件


## 與 Agent 互動使用 GitHub MCP


### 使用技巧

1. **明確指定資訊**
   - 提供完整的倉庫名稱（包含用戶名或組織名）
   - 指定明確的 PR 或 Issue 編號
   - 說明具體的分支名稱

2. **補充說明**
   - Agent 會在需要更多信息時主動提問
   - 您可以分步驟提供信息
   - 可以隨時要求查看操作結果

3. **操作確認**
   - 重要操作前，Agent 會請求您確認
   - 您可以在執行前檢查操作參數
   - 可以要求 Agent 說明將要執行的具體步驟

### 基本對話指令

1. **查看倉庫相關**
   - "請列出我的 GitHub 倉庫"
   - "幫我搜尋關於 [關鍵字] 的倉庫"
   - "顯示 [倉庫名稱] 的詳細信息"
   - "查看 [倉庫名稱] 使用了哪些程式語言"

2. **Pull Request 相關**
   - "幫我建立一個 PR，從 [分支名稱] 合併到 main"
   - "查看 PR #[編號] 的狀態"
   - "列出 PR #[編號] 的所有提交記錄"
   - "顯示最近的 PR 列表"

3. **Issue 相關**
   - "在 [倉庫名稱] 建立一個新的 Issue"
   - "幫我在 Issue #[編號] 添加評論"
   - "查看 [倉庫名稱] 的所有開放 Issue"

### 實際對話範例

1. **倉庫操作範例**
   ```
   使用者：請列出我最近更新的 GitHub 倉庫
   Agent：好的，我會幫您查詢您的倉庫列表，並按更新時間排序...

   使用者：幫我查看 myproject 倉庫用了哪些程式語言
   Agent：我來幫您檢查 myproject 的語言統計信息...
   
   使用者：請幫我 fork composio/mcp 這個倉庫
   Agent：好的，我現在就幫您 fork 這個倉庫到您的帳號下...
   
   使用者：請幫我在 myproject 倉庫建立一個新的分支
   Agent：沒問題，請問您想要將新分支命名為什麼？
   ```

2. **PR 操作範例**
   ```
   使用者：請幫我建立一個 PR，要從 feature-login 分支合併到 main
   Agent：好的，我會幫您建立 Pull Request，請問您想要設定什麼標題？

   使用者：查看 PR #123 的狀態
   Agent：我來幫您檢查這個 PR 的詳細信息...
   
   使用者：請幫我審查 PR #456 的程式碼變更
   Agent：好的，我來幫您檢視這個 PR 的所有更改內容...
   
   使用者：請幫我在 PR #789 加上 "ready for review" 標籤
   Agent：好的，我這就幫您在 PR 上添加標籤...
   ```

3. **Issue 操作範例**
   ```
   使用者：請在 myproject 建立一個 Bug 回報的 Issue
   Agent：好的，我來幫您建立 Issue。請問您想要描述什麼問題？

   使用者：幫我在 Issue #456 添加一個進度更新的評論
   Agent：沒問題，請告訴我您想要添加什麼內容...
   
   使用者：請幫我將 Issue #789 指派給 @johndoe
   Agent：好的，我來幫您更改 Issue 的指派對象...
   
   使用者：請列出所有被標記為 "high priority" 的 Issue
   Agent：我來幫您篩選具有該標籤的 Issue...
   ```

4. **程式碼審查範例**
   ```
   使用者：請幫我查看最近一次提交的變更內容
   Agent：好的，我來幫您檢視最新的 commit 內容...
   
   使用者：請幫我比較 develop 和 main 分支的差異
   Agent：我來幫您分析這兩個分支之間的差異...
   
   使用者：在 PR #234 的第 15 行加上一個評論
   Agent：好的，請告訴我您想要在這行程式碼上添加什麼評論...
   ```

## 注意事項

1. **權限相關**
   - 某些操作可能需要特定的訪問權限
   - Agent 會提醒您是否需要額外授權
   - 可以隨時確認當前的權限狀態

2. **操作安全**
   - 重要操作會要求確認
   - 可以隨時取消正在進行的操作
   - 敏感信息不會被公開顯示

## 故障排除

### 常見問題

1. **連接失敗**
- 檢查網絡連接
- 確認 GitHub 認證是否有效
- 重新運行安裝命令

2. **認證錯誤**
- 清除瀏覽器快取
- 重新登入 GitHub
- 檢查權限設置

3. **命令無法執行**
- 確認 Node.js 版本是否最新
- 檢查 Cursor IDE 版本
- 重新安裝 MCP

### 解決方案

1. **重新安裝**
```bash
npx @composio/mcp@latest setup "https://mcp.composio.dev/github/mealy-millions-grass-1lDTiR" --client cursor --force
```

2. **清除設置**
- 刪除 MCP 配置文件
- 重新執行安裝步驟
- 重新授權 GitHub

## 參考資源
- [Cursor MCP 官方文檔](https://composio.notion.site/Cursor-MCP-Docs-1adf261a6dfe80b4ba5fe492bf41441c)
- [Composio MCP GitHub 實例](https://mcp.composio.dev/github/mealy-millions-grass-1lDTiR)
- [GitHub API 文檔](https://docs.github.com/en/rest)
- [Cursor IDE 文檔](https://cursor.sh/docs) 