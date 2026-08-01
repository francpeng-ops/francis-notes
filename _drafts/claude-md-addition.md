# CLAUDE.md 追加段 — 「發佈週報」程序

以下整段貼到 CLAUDE.md 的「發新文章的標準流程」之後。

---

## 發佈週報(收到「發佈週報」指令時執行)

前提:`_drafts/weekly/` 下有一份 Francis 已審過的草稿。本程序把它正式上線。

1. 找到 `_drafts/weekly/` 中最新的 `2026-wNN.html`。若該檔的審稿清單註解仍有未勾項或主軸段仍有 `<!-- DRAFT -->` 註解,先向 Francis 確認是否照發,不要自行判斷。
2. 清稿:移除檔頂的審稿清單註解與所有 `<!-- DRAFT -->` 註解。
3. 檢查:GA 標籤、canonical(= `.../weekly/2026-wNN.html`)、角括號轉義、`.pager` 的 prev 指向上一期。
4. 搬檔:草稿移入 `weekly/2026-wNN.html`,刪除 `_drafts/weekly/` 內的原檔。
5. 上一期補 pager:在上一期的 `.pager` 加 next 指向本期(dir 文字「下一期 →」,pt 放本期主軸句)。
6. `weekly/index.html`:在 `<ul class="issues">` 最上面加本期 `<li>`(wk 期別日期、t 主軸句、d 一句話簡介)。
7. 主 `index.html` 入口卡三個欄位:`.wc-main` 的 href 改指本期、`.wc-d` 換成本期一句話、`.wc-meta` 換成本期期別日期。**不動卡片其他部分。**
8. `rss.xml`:第一個 item 上方新增 item。title = `市場週報 WNN｜<主軸句>`;link/guid = `https://francpeng-ops.github.io/francis-notes/weekly/2026-wNN.html`;description = 入口卡那句一句話;pubDate 用 RFC822、+0800。
9. 本地預覽:週報頁淺色/深色不破版、numstrip 手機兩欄正常、pager 前後期互通、入口卡與週報目錄頁更新正確。
10. `git diff` 給 Francis 過目,確認後 commit(訊息格式:`weekly: 2026-wNN <主軸句>`)並 push,提醒 Francis 按 Sync。

### 不要做
- 不要在發佈階段改寫主軸段或觀察清單的文字內容(那是 Francis 定稿過的);只做搬運、連結、清單與 rss 的機械性更新。
- 不要動 `weekly/` 既有各期的內文;上一期只允許加 pager next。
