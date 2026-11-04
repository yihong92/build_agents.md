# 專案名稱：AI 工具與 Prompt 筆記庫 (AI Knowledge Base)

## 1. 專案目的 (Project Purpose)
本專案為一個模組化、響應式的個人知識庫網站，用於整理與展示各種 AI 工具使用技巧、Prompt 範例與開發筆記。
透過這份規範，讓 AI 能在完全不需要重新解釋視覺與結構的前提下，快速擴充新的主題頁面與維護內容。

## 2. 技術棧與規範 (Tech Stack)
- **HTML5**: 採用語意化標籤 (`header`, `nav`, `main`, `section`, `article`, `footer`)。
- **CSS 框架**: 統一採用 Tailwind CSS CDN（請勿使用 npm 打包或任何複雜建構工具）。
  - CDN 引入語法：`<script src="https://cdn.tailwindcss.com"></script>`
- **圖示庫**: Font Awesome 6.x CDN。
- **部署環境**: GitHub Pages 根目錄 (Root) 部署，確保所有路徑均採用相對路徑 (`./` 或 `pages/`)。

## 3. 專案檔案結構 (Project Structure)
```text
/
├── index.html              # 網站首頁（所有主題卡片與目錄列表）
├── CLAUDE.md               # AI 開發與擴充規範文件 (本檔案)
└── pages/                  # 內容子頁面資料夾
    └── prompt-basics.html  # 範例子頁面 1
```

## 4. 網頁視覺與 UI 風格 (Visual & UI Style Guide)
- **配色計畫 (Color Palette)**：
  - 主背景色：`bg-slate-50`
  - 卡片背景：`bg-white`
  - 主要文字：`text-slate-800`
  - 次要文字：`text-slate-500`
  - 品牌主題色 (Accent)：`text-indigo-600` / `bg-indigo-600`
  - 程式碼 / Prompt 區塊：`bg-slate-900` 搭配 `text-slate-100`
- **卡片樣式與動畫**：
  - 卡片需帶有圓角與陰影，懸停時有上浮動畫：`rounded-xl shadow-sm hover:shadow-md hover:-translate-y-1 transition-all duration-200`
- **響應式佈局**：
  - 手機端 1 欄位 (`grid-cols-1`)，平板 2 欄位 (`md:grid-cols-2`)，桌面 3 欄位 (`lg:grid-cols-3`)。

## 5. 新增內容與頁面標準規範 (Rules for Content Expansion)

### A. 首頁卡片規範 (`index.html`)
每當新增一個子頁面時，必須在 `index.html` 的卡片網格區域新增一張卡片，結構必須完全符合以下模板：

```html
<a href="pages/YOUR-FILE-NAME.html" class="block bg-white p-6 rounded-xl shadow-sm border border-slate-100 hover:shadow-md hover:-translate-y-1 transition-all duration-200">
  <div class="flex items-center justify-between mb-3">
    <span class="px-2.5 py-1 text-xs font-medium text-indigo-600 bg-indigo-50 rounded-full">分類名稱</span>
    <span class="text-xs text-slate-400">YYYY-MM-DD</span>
  </div>
  <h3 class="text-lg font-bold text-slate-800 mb-2">單元主題標題</h3>
  <p class="text-slate-500 text-sm line-clamp-2">簡短描述這個單元的核心內容（不超過 60 字）。</p>
</a>
```

### B. 子頁面結構規範 (`pages/*.html`)
所有在 `pages/` 目錄下的頁面，必須包含以下基本結構：
1. **頂部導覽列**：必須包含「回到首頁」按鈕（連結指回 `../index.html`）。
2. **主題 Hero 區塊**：包含分類標籤、大標題與摘要簡介。
3. **主內容區**：
   - 內文標題統一採用 `text-2xl font-bold text-slate-800 mt-8 mb-4`。
   - Prompt 或範例程式碼統一包覆在 `<pre><code class="font-mono text-sm">` 中。
4. **頁尾 Footer**：統一包含版權與回到頁頂連結。

## 6. AI 協助開發與維護指令 (AI Agent Rules)
當使用者要求「新增一個頁面」或「擴充內容」時，AI Agent 必須遵循以下規則：
1. **零編譯原則**：只生成純 HTML/CSS/JS 檔案，嚴禁引入 Node.js、Vite、React 或打包工具。
2. **命名規範**：`pages/` 下的 HTML 檔案一律使用全小寫加連字號 (kebab-case)，例如 `prompt-engineering-101.html`。
3. **同步雙向更新**：在 `pages/` 新增頁面檔後，必須同時更新 `index.html`，自動將新的卡片組件嵌入首頁網格中。
4. **相對路徑正確性**：
   - 首頁（`index.html`）連結至子頁面：`pages/filename.html`
   - 子頁面（`pages/*.html`）連結至首頁：`../index.html`
