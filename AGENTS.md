# AGENTS.md - 自由上下載作品集 (OpenPortfolio) 專案規範

本文件旨在讓 AI 助手（如 Claude, ChatGPT, Cursor）理解本專案的架構、設計風格與內容擴充規範。當需要新增頁面、擴充作品資料或修改功能時，請嚴格遵守以下規則。

---

## 1. 專案目的與核心理念
- **專案定位**：輕量級、免後端的個人數位作品展示與分享庫。
- **核心功能**：
  1. 訪客可瀏覽作品、依分類/關鍵字篩選。
  2. 提供「下載作品」功能，可獲取作品原始檔或附件。
  3. 提供「線上上傳」互動介面，支援瀏覽器端即時載入展示與下載。
  4. 靜態部署於 GitHub Pages，無需任何 Node.js 建置流程。

---

## 2. 技術棧與設計系統 (Design System)
- **核心技術**：HTML5 + Tailwind CSS (CDN 載入) + Vanilla JavaScript + Lucide Icons。
- **色彩風格**：
  - 背景：極簡淺灰/純白 (`bg-slate-50` / `bg-white`)
  - 主色調：靛藍至紫羅蘭 (`text-indigo-600`, `bg-indigo-600`, `hover:bg-indigo-700`)
  - 文字層次：深灰標題 (`text-slate-900`)、次要內文 (`text-slate-600`)、輔助小字 (`text-slate-400`)
- **排版原則**：
  - 響應式卡片網格：手機 1 欄、平板 2 欄、桌面 3 欄 (`grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`)。
  - 卡片視覺：圓角 `rounded-2xl`、柔和陰影 `shadow-sm hover:shadow-md`、平滑過渡 `transition-all duration-200`。

---

## 3. 作品資料模型 (Project Schema)
預設作品存放於 `data/projects.json`，每筆作品資料必須具備以下欄位：

```json
{
  "id": "project-001",
  "title": "作品名稱",
  "category": "UI設計 | 程式專案 | 簡報文件 | 多媒體",
  "description": "100 字以內的作品重點介紹與使用技術。",
  "tags": ["標籤1", "標籤2"],
  "date": "2026-11",
  "coverUrl": "封面圖片網址或 base64",
  "downloadUrl": "可下載檔案之連結或資料 (支援 Data URL 或檔案路徑)",
  "downloadFilename": "my-work.zip"
}