# CLAUDE.md — 法蘭西斯的學習筆記

給 Claude Code 的專案說明。動手前請先讀這份。

## 這是什麼
個人文章網站「**法蘭西斯的學習筆記**」。純靜態 HTML、**無建置步驟、無框架、無後端**，部署在 **GitHub Pages**。內容是繁體中文個人文章，分三個系列。

## 技術原則（請遵守）
- 每篇文章是一個獨立 `.html`，CSS 內嵌在各檔的 `<style>`。**不要**引入框架、打包工具或 build step；保持「打開即是成品」。
- 字型用 Google Fonts：Noto Serif TC（標題）、Noto Sans TC（內文）。
- 部署：GitHub Pages，**main 分支、/(root)**。
- 任何放進 HTML 或 SVG `<text>` 的角括號（例如 `<li>`）**務必轉義**成 `&lt;li&gt;`，否則破版。

## 檔案結構
| 檔案 | 用途 |
|---|---|
| `index.html` | 目錄首頁（三個系列 + 訂閱區） |
| `_template.html` | 知識解碼系列空白模板（寫新文章從這複製） |
| `sales-marketing-war.html` | 知識解碼：業務與行銷，為什麼總是開戰？ |
| `see-the-relationship.html` | 成長雜記：看清關係，再決定距離 |
| `memory.html` | 成長雜記：看見自己，享受當下（鬆開過去） |
| `see-yourself.html` | 成長雜記：看見自己，享受當下 |
| `rss.xml` | RSS feed（含「新文章樣板」註解區塊） |
| `deploy-guide.svg` / `publishing-guide.md` | 上傳教學 |

## 三個系列與視覺識別
- **知識解碼（knowledge）**：把專業講清楚、案例/框架解析。主色墨綠藍 `--accent:#216B78`。有「三句話看懂」`.tldr` 摘要框與 `.framework` 表格。
- **投資筆記（invest）**：投資／理財的報告、案例與框架解析，專業但白話。主色靛藍 `#3A4D7A`（首頁系列 class 為 `.i`）。文章版型沿用知識解碼模板，把 `--accent` 改成 `#3A4D7A` 即可。
- **成長雜記（growth）**：向內的體悟、第一人稱散文。主色琥珀金 `#B07A2E`。有 `.lead .opening` 開場句。
- 共用：紙感底色 `#F5F0E7`、襯線標題、`.hl` 重點底線、`.pull` 金句、`.closing` 結尾光暈、頂部與底部 `← 回目錄`。
- 風格：少用 emoji、克制排版、句子精煉。

## 佔位字
- GitHub 帳號 **已套用為 `francpeng-ops`**（canonical 與 `rss.xml` 皆已是正式網址，base URL：`https://francpeng-ops.github.io/francis-notes`）。
- `YOURPUB` → Substack 子網域（仍在 `index.html` 訂閱區 iframe，待確定後替換）。
- 新文章模板 `_template.html` 的 canonical 仍是 `CHANGE-ME.html`，每篇要改成該篇英文檔名。

## 發新文章的標準流程
1. 複製 `_template.html` → 英文檔名（建議 `slug.html` 或 `yyyy-mm-dd-slug.html`）。
2. 填內容：kicker、`<h1>`、sub、各 `<section>`。零件：`<h2> <h3> <p>`、`<span class="hl">`、`<span class="strong">`、`<blockquote class="pull">`、表格 `.framework`、`.closing`。
3. 設該頁 `<link rel="canonical">` = `https://francpeng-ops.github.io/francis-notes/<檔名>`。
4. `index.html`：在對應系列 `<ul class="posts">` **最上面**複製一個 `<li>`，改 href、`.t` 標題、`.d` 簡介、`.meta` 日期（新到舊排序）。
5. `rss.xml`：在第一個 `<item>` 上面新增一個 `<item>`（檔內已有註解樣板），改 title / link / guid / description / pubDate（RFC822，+0800）。
6. 若是**成長雜記**：在新文章底部加 `.pager`（prev = 前一篇），並更新前一篇的「下一篇」指向新文章。知識解碼目前單篇，暫不需 pager。
7. 本地確認不破版（見下），再 commit + push。

## 不要做
- 不要改既有文章的 `<h1>` 標題或作者原文用字（那是已發布內容）。
- 不要把中文當檔名（網址會變亂碼）。一律英文。
- 不要動 `<style>` 內的共用版型，除非使用者明確要求改設計。

## 深色模式（重要）
- 每頁都內建深色配色：`<style>` 結尾有 `color-scheme: light dark;` 和一段 `@media (prefers-color-scheme: dark){ … }`。母版 `_template.html` 也含這套，新文章直接沿用即可。
- 規則：用 CSS 變數（`--paper / --ink / --ink-soft / --accent …`）的元素會自動跟著深色走；**凡是寫死 `rgba()` 或 hex 的顏色**（如 `.hl` 底色、`thead`、`.tldr`、`.closing` 光暈、`.foot a` 行內色），都要在那段 `@media` 裡補一條深色覆蓋，否則深色下會看不清。
- 新文章若加了新元件（圖表、卡片等），記得同步在深色 `@media` 內補上它的深色樣式。
- 驗收：把系統/瀏覽器切到深色模式，逐頁確認「暖色深底 + 米白字 + 系列色夠亮、不刺眼」；再切回淺色確認米色版正常。

## 指令速查
```bash
# 本地預覽
python3 -m http.server 8000   # 然後開 http://localhost:8000

# 發佈
git add -A && git commit -m "post: <標題>" && git push
```
GitHub Pages 第一次設定：Settings → Pages → Branch main、/(root)（或用 `gh` API）。

## 並行 Substack（全文路線）
網站是 canonical 正本；Substack 放**全文** + 一行「本文原載於 法蘭西斯的學習筆記」+ 連結。每發一篇都要同步更新 `rss.xml`。
