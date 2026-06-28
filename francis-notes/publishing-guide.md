# 發布教學 ｜ 法蘭西斯的學習筆記

> 圖解版見同資料夾的 `deploy-guide.svg`（用瀏覽器打開即可）。

這個網站是純靜態 HTML，不需要後端、不需要寫程式。
下面分三段：**第一次上線**、**之後發新文章**、**常見問題**。

---

## 一、第一次上線（GitHub Pages，免費）

1. **解壓縮 ZIP**
   下載並解壓 `francis-notes.zip`，得到一個含 `index.html` 的資料夾。

2. **建立 GitHub 儲存庫**
   到 github.com 註冊或登入 → 右上 **＋ → New repository** → 取名（例如 `francis-notes`）→ 選 **Public** → **Create repository**。

3. **上傳檔案**
   在 repo 頁面 **Add file → Upload files**，把資料夾「**裡面**」的所有檔案一起拖進去 → **Commit changes**。

4. **開啟 GitHub Pages**
   **Settings → Pages** → Source 選 *Deploy from a branch* → Branch 選 **main**、資料夾 **/(root)** → **Save**。

5. **等 1–2 分鐘 → 取得網址**
   重新整理 Pages 頁，上方出現你的網址：
   `https://你的帳號.github.io/francis-notes/`

6. **完成**
   打開網址就是目錄首頁，點任一篇即可閱讀。這個連結傳給任何人都能看。

> ⚠️ **最容易出錯的一步**：要上傳的是資料夾「裡面的檔案」，讓 `index.html` 落在 repo 的最上層（根目錄）。
> 不要把整個 `francis-notes` 資料夾連名字一起丟進去，否則網址會多一層、打不開。

---

## 二、之後發新文章（每週 3 步）

1. 複製 `_template.html` → 改成**英文檔名**（例如 `2026-07-05-topic.html`）→ 填內容。
2. 開 `index.html`，複製一個 `<li>…</li>` 區塊 → 改連結、標題、日期。
3. 回 repo → **Add file → Upload files** 上傳這兩個檔 → **Commit**。網站約 1 分鐘後自動更新。

---

## 三、常見問題

- **打開是 404 或空白？**
  多半是 (a) 還沒等夠 1–2 分鐘，或 (b) `index.html` 不在根目錄。回去確認它在 repo 第一層。

- **中文檔名可以嗎？**
  能動，但網址會變亂碼。維持**英文檔名**最穩。

- **想改顏色？**
  每個 HTML 最上面 `:root{ --accent: ... }` 改一個色碼即可。知識解碼墨綠藍 `#216B78`、投資筆記靛藍 `#3A4D7A`、成長雜記琥珀金 `#B07A2E`。

- **想換網域（例如 yourname.com）？**
  之後在 Settings → Pages → Custom domain 綁定，再到網域商設定 DNS 即可（可日後再做）。

---

## 檔案清單

| 檔案 | 用途 |
|---|---|
| `index.html` | 目錄首頁（打開這個） |
| `sales-marketing-war.html` | 知識解碼：業務與行銷，為什麼總是開戰？ |
| `see-the-relationship.html` | 成長雜記：看清關係，再決定距離 |
| `memory.html` | 成長雜記：看見自己，享受當下（鬆開過去） |
| `see-yourself.html` | 成長雜記：看見自己，享受當下 |
| `_template.html` | 知識解碼系列空白模板 |
| `rss.xml` | 文章 RSS feed（Substack 匯入／訂閱用）|
| `deploy-guide.svg` | 上傳流程圖解 |
| `publishing-guide.md` | 本說明文件 |
| `CLAUDE.md` | 給 Claude Code 的專案說明（自動讀取）|
| `workflow-manual.md` | 完整使用手冊（Mac × 桌面版）|

---

## 四、並行 Substack（全文路線）

你的網站是「正本」，Substack 放全文 + 一行原載連結。已幫你做好三項：

1. **canonical 標籤**：每頁 `<head>` 已加 `<link rel="canonical">`，宣告自己網站是正本。
2. **`rss.xml`**：列出所有文章，供 Substack 一次性匯入、RSS 訂閱者、未來自動化使用。
3. **訂閱區塊**：`index.html` 底部已加「訂閱新文章」區，內含 Substack 表單位置。

### 上線前要改的兩個佔位字

- **`francpeng-ops`**（出現在每頁 canonical 與 `rss.xml`）→ 換成你的 GitHub 帳號。
  一次搞定：用編輯器把所有檔案裡的 `francpeng-ops` 全部取代掉即可。
- **`YOURPUB`**（在 `index.html` 訂閱區的 iframe）→ 換成你的 Substack 子網域（例如 `francis`）。

### 每次發文的並行流程

1. 用 Markdown 寫一份原稿。
2. 生成網站 HTML → 上 GitHub（先發，讓 Google 先收錄你的版本）。
3. 在 `index.html` 加一個 `<li>`、在 `rss.xml` 加一個 `<item>` → Commit。
4. 把同一份貼進 Substack（全文）→ 開頭或結尾加一行：
   「本文原載於 法蘭西斯的學習筆記」+ 你的文章網址。

> 註：Substack 無法設 canonical，所以那一行「原載連結」就是它的替代品；對個人小站，SEO 影響很小，不用擔心。
