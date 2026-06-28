# 使用手冊（Mac × Claude Code 桌面版）

完整流程：哪些在「對話介面（這裡）」做，哪些交給「Claude Code 桌面版 App」。
重點：用桌面版，你幾乎不用碰終端機——大部分事情用「點」和「跟它講話」就能完成。

---

## 全貌：兩個工具、各司其職

| | 對話介面（claude.ai） | Claude Code 桌面版 App |
|---|---|---|
| 角色 | **想 + 寫 + 設計 + 討論** | **改檔 + 更新 rss + commit + push** |
| 介面 | 聊天 | 圖形介面（Code 分頁，可看檔案差異／預覽） |
| 檔案在哪 | 雲端沙箱（用 zip 下載） | 你 Mac 上的專案資料夾 |
| 適合 | 構思系列、寫文章、調版型、聊策略 | 多檔修改、版本控制、發佈 |

**接力**：在這裡把內容與設計想清楚、做出來 → 落地與每週維運交給 Claude Code。

---

## 階段一：在對話介面（構思與創作）

你現在已經在做的事：想系列定位與標題、寫改文章、調版型配色、討論 Substack 策略。
產出：HTML 檔、模板、`rss.xml`、`index.html`、整包 `francis-notes.zip`。

---

## 階段二：一次性設定（Mac 桌面版，從無到有上 GitHub）

> 只有「人」能做的：註冊帳號、安裝、第一次登入授權。其餘都能交給 Claude Code。

**1. 註冊 GitHub 帳號**（github.com，瀏覽器）。

**2. 安裝 Claude Code 桌面版**
到 **claude.com/download** 下載 Mac 版 → 拖進「應用程式」→ 開啟 → 用你的 Anthropic 帳號**登入**（需 Pro／Max 等付費帳號）→ 點上方 **Code** 分頁。

**3. 解壓資料夾到 Mac**
把 `francis-notes.zip` 解壓到你找得到的位置（例如「文件」）。

**4. 在 App 裡開這個專案**
Code 分頁 → 點 **＋ New session**（或 Cmd+N）→ 選 `francis-notes` 資料夾。

**5. 讓 Claude Code 幫你把雜事做完**——在對話框直接打字交代，例如：
> 「這個專案要上 GitHub。請幫我：
> 「這個專案要上 GitHub。請幫我：
> （1）初始化 git，用名字 **Francis Peng**、email **francpeng@gmail.com** 設定身分；
> （2）把 git 預設分支設成 main；
> （3）建立一個叫 francis-notes 的**公開** repo（我的帳號是 francpeng-ops）並 push 上去。」

（GitHub 帳號 `francpeng-ops` 我已幫你套進所有檔案，canonical 與 rss.xml 都是正式網址，這步不用再改。只剩 Substack 的 `YOURPUB` 等你確定子網域後替換。）

過程中可能會遇到兩個「要你點一下」的地方，都很單純：
- **Git 沒裝**：它會停下來請你安裝。Mac 會跳出一個安裝視窗（Command Line Tools），按「安裝」等它跑完，再回 App 跟它說「裝好了，繼續」。（裝 Git 不需要 GitHub 帳號。）
- **要連 GitHub**：建立 repo 時它會請你在瀏覽器授權登入 GitHub（或安裝 `gh` 工具，它會提示你）。點一次完成即可。

**6. 開啟 GitHub Pages（在網站點一次）**
到 repo → **Settings → Pages** → Branch 選 **main**、資料夾 **/(root)** → Save。
等 1–2 分鐘 → 網址 `https://francpeng-ops.github.io/francis-notes/`。

> 你實際「自己動手」的，只有：註冊 GitHub、按一下 Git 安裝視窗、瀏覽器授權一次、Pages 點一次。其餘交給 Claude Code。

---

## 階段三：每週固定發（在 App 裡講一句話）

打開 Claude Code → Code 分頁 → 開 `francis-notes` 的 session → 在對話框打字，例如：

> 「把這段內容變成**知識解碼**系列的一篇，標題《XXX》，slug 用 `xxx`。
> 照 CLAUDE.md 的流程：建檔、設 canonical、更新 index 和 rss.xml，
> 做好後讓我看一下差異，沒問題就 commit、push。」

Claude Code 會：
1. 複製 `_template.html` → 產生 HTML、填內容、設 canonical；
2. 更新 `index.html`（加 `<li>`）與 `rss.xml`（加 `<item>`）；
3. 在 App 裡用**差異檢視（diff）**把改動列給你看 → 你確認 → 它 `commit` 並 `push`。

> App 裡還有「預覽」窗格，可以直接看網頁長相，不用切去瀏覽器。

最後你做一件手動的事：把同一篇**全文**貼到 Substack，加一行「本文原載於 法蘭西斯的學習筆記」+ 文章網址。

---

## 你的三個問題，直接回答

- **能用 Claude Code 從無到有上 GitHub 嗎？** 能。建 repo、commit、push 都能交給它；Pages 在 GitHub 網站點一次最穩。
- **要先註冊 GitHub 嗎？** 要，帳號一定得你本人先註冊（它不能替你建帳號）。
- **「安裝 Git／設定身分」也要用終端機嗎？** 用桌面版**不用**。Git 若沒裝，App 會提示你、Mac 跳安裝視窗點一下即可；設定身分（名字／email）你直接「叫 Claude Code 幫你設」就好。

---

## 小提醒
- `CLAUDE.md` 在資料夾根目錄，Claude Code 一開專案就自動讀，知道你的系列、配色與發文流程。
- 桌面版 App 目前不支援 Linux（Mac／Windows 才有），你用 Mac 沒問題。
- 想換設計、加深色模式、加「上一篇／下一篇」這類有創意的調整，回這裡跟我做好，再讓 Claude Code 落地。

---

## 我們的協作流程（最低摩擦版）

分工：**想／寫／改** 在對話介面（claude.ai）做；**落地／發布／維護** 交給 Claude Code。
交付以「**單檔 + 一段 prompt**」為主，不再每次丟整包 zip。

### 三種交付方式

**1. 新文章 → 單檔 + prompt（預設）**
我給你「**那一篇的 `.html`**」（已排好版、設好 canonical）＋一段給 Claude Code 的 prompt。
你把該檔放進專案資料夾、把 prompt 貼進 Claude Code，它完成其餘所有事。

標準 prompt 範本（我每次會幫你填好）：
> 我在專案資料夾放了新檔 `xxx.html`（◯◯系列）。請照 `CLAUDE.md`：
> 1. 確認 canonical 指向 `https://francpeng-ops.github.io/francis-notes/xxx.html`；
> 2. 在 `index.html` 的「◯◯」區最上面，加一個指向它的 `<li>`（標題《…》、簡介「…」、日期 2026.◯◯.◯◯）；
> 3. 在 `rss.xml` 第一個 `<item>` 上面，加一個對應 `<item>`；
> 4. commit（訊息 `post: xxx`）然後 push。

**2. 小修改 → 只給文字指示（最輕）**
連檔案都不用。我給你「找這段 → 換成這段、在哪個檔」，你貼給 Claude Code。
> 在 `see-the-relationship.html`，把「（舊句）」整段換成「（新句）」，然後 commit（`edit: 微調`）並 push。

**3. 第一次上線 → 整包 zip（只此一次）**
專案還沒在你 Mac 上時，用整包 zip 建立本機資料夾、推上 GitHub。之後改用 1 或 2，不再用 zip。

### 「第一次上線」prompt（可直接複製給 Claude Code）
> 這個專案要上 GitHub。請幫我：
> 1. 初始化 git，用名字 Francis Peng、email francpeng@gmail.com 設定身分，預設分支設成 main；
> 2. 建立一個叫 francis-notes 的公開 repo（我的帳號是 francpeng-ops）並 push。
> （檔案裡的 USERNAME 已套好，只剩 Substack 的 YOURPUB 之後再換。）

完成後到 GitHub → Settings → Pages → main、/(root) → Save，等 1–2 分鐘即上線。
