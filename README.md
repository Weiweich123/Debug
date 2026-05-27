# Final Prototype

這是一個以純前端 HTML / JavaScript 製作的昆蟲辨識與社群留言原型，搭配 Supabase 作為登入、發文、投票與資料儲存後端。

## 專案內容

- `index.html`：主頁，包含相機辨識、辨識結果與論壇區塊。
- `register.html`：註冊頁。
- `config.js`：Supabase 與辨識基準圖設定。
- `Photo/`：昆蟲基準圖片資料夾。
- `supabase_forum_posts_rls.sql`：Supabase 資料表、RLS、投票表與 trigger 設定腳本。

## 功能

- 相機即時辨識昆蟲卡片。
- 支援多張基準圖與多裁切比對。
- 顯示對應解法與討論區留言。
- Supabase 登入、註冊、發文與投票。
- 匿名可閱讀留言，登入後才可發文與投票。

## 執行方式

1. 先確認 `config.js` 裡的 Supabase URL、API Key 與圖片路徑正確。
2. 將 `supabase_forum_posts_rls.sql` 貼到 Supabase SQL Editor 執行一次，建立或更新資料表與權限。
3. 用瀏覽器開啟 `index.html`，或用 VS Code Live Server 預覽。
4. 點擊相機按鈕開始辨識，登入後可發文與投票。

## SQL 檔案要不要上傳

建議要上傳。

- 它是這個專案的資料庫設定與 migration 檔，能讓別人重建 Supabase 的表結構、RLS、投票功能與 trigger。
- 如果你未來要重新部署、交作業、或讓別人檢查專案，這份 SQL 很重要。
- 只有在你想把 repo 當成純前端展示，而且確定不需要別人重建資料庫時，才可以不強制包含。

## 應該一起上傳的檔案

- `index.html`
- `register.html`
- `config.js`
- `supabase_forum_posts_rls.sql`
- `Photo/` 內的圖片

## 上傳到 GitHub 的建議

- `config.js` 目前只有 Supabase URL 與 anon key，通常可以上傳。
- 如果未來改成更敏感的金鑰，請改成不要提交到 GitHub。
- `Photo/` 的基準圖片也應一起上傳，否則辨識功能無法重現。

## VS Code 內建上傳到既有儲存庫

可以，不用先打指令。

1. 左側打開 Source Control。
2. 如果還沒初始化 Git，先按 `Initialize Repository`。
3. 把想上傳的檔案加入 stage。
4. 在上方輸入 commit 訊息，按 Commit。
5. 點右下角或 Source Control 的 `Publish Branch` / `Sync Changes`。
6. 如果已經有 GitHub remote，VS Code 會直接推到既有儲存庫；如果沒有，會引導你連線。

## 需要注意

- 上傳前先確認不要把不想公開的檔案加入 stage。
- 如果某些檔案只想保留在本機，可以再補 `.gitignore`。
