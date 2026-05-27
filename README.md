# Debug 🐛 - 居家昆蟲辨識與社群防護網

「Debug」是一個結合**邊緣運算 (Edge Computing)** 與 **Serverless 架構**的行動端網頁應用程式 (Web App)。
專為解決居家蟲害問題設計，提供即時的相機影像辨識，並整合了社群論壇，讓使用者能快速獲取專家建議與實用除蟲經驗。

## ✨ 系統特色與亮點

* **純前端影像辨識 (Client-side CV)：** 捨棄傳統耗時的後端影像傳輸，採用 `jsfeat` 函式庫，直接在使用者的瀏覽器端進行特徵點運算與匹配。不僅大幅降低伺服器成本，更確保了使用者的隱私安全。
* **無伺服器後端 (Serverless Architecture)：** 整合 Supabase 作為 Backend-as-a-Service (BaaS)，快速實現安全的會員驗證 (Authentication) 與即時資料庫。
* **嚴謹的資料庫安全防護：** 前端僅存放低權限之匿名金鑰 (`anon_key`)，核心資安防線建構於資料庫層級，全面啟用 **RLS (Row Level Security)** 政策，嚴格控管資料的讀寫權限。
* **雙模式互動體驗：** 針對「怕蟲」的使用者族群，貼心設計了「真實模式 / 卡通模式」的即時切換功能，提升 UX 友善度。

## 🛠️ 技術堆疊 (Tech Stack)

* **前端介面：** HTML5, Vanilla JavaScript, Tailwind CSS
* **影像處理：** jsfeat (特徵點擷取、灰階轉換、相似度比對)
* **後端與資料庫：** Supabase (PostgreSQL, Auth, RLS)
* **部署：** GitHub Pages

## 🚀 快速啟動 (Quick Start)

### 1. 本地端運行
本專案為純前端架構，無需安裝 Node.js 模組。
1. 將專案 clone 至本地端。
2. 使用 VS Code 打開專案資料夾。
3. 啟動 **Live Server** 擴充功能，即可在瀏覽器預覽 `index.html`。

### 2. 環境變數與後端設定
* `config.js` 內存放 Supabase 連線資訊與基準圖路徑。本專案採 SPA 架構，前端僅放置具備 RLS 防護之 `anon_key` 以供展示與介接。
* **資料庫重建：** 若需部署至全新的 Supabase 專案，請將專案根目錄下的 `supabase_forum_posts_rls.sql` 匯入至 Supabase SQL Editor 執行，即可一鍵建立完整的資料表 (Tables)、關聯 (Relations)、觸發器 (Triggers) 以及 RLS 安全政策。

## 📁 專案結構

```text
├── index.html                  # 主應用程式 (相機辨識、結果展示、論壇)
├── register.html               # 獨立註冊頁面
├── config.js                   # 環境變數與全域設定檔
├── supabase_forum_posts_rls.sql # 資料庫結構與 RLS 權限建置腳本
└── Photo/                      # 昆蟲基準圖庫
