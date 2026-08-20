# DEVLOG — blog

隨手開發紀錄。心得萃取後才進 Obsidian 的 `學習紀錄/`，這裡放過程。

## 2026-08-19 — 第一個首頁

做了什麼：
- 建 `~/Projects/blog`，寫出首頁 `index.html` + `css/style.css`
- 純 HTML / CSS，零框架、零 JavaScript。深色主題
- 區塊：頁首（sticky 導覽）→ hero →「最新文章」卡片 ×1 →「關於」→ 頁尾
- 所有顏色集中在 `style.css` 開頭的 `:root` 色票，改一次全站生效
- 手機版靠一個 `@media (max-width: 600px)` 縮字級

驗證方式：
- `python3 -m http.server 4173` 起本機伺服器，Chrome 無頭模式截圖
- 桌機 1280px 正常；截圖見 `screenshots/2026-08-19-首頁.png`
- **踩到的坑**：截圖 390px 手機寬度時右側被切掉，一度以為 CSS 壞了。
  實際是 Chrome 無頭模式視窗最小寬度約 500px，390 只是把 500 的畫面裁掉。
  改用 500px 截圖就正常 → 以後量測手機版不要相信無頭模式的 390px
- Chrome 擴充功能擋 `file://` 與 `localhost`，所以走無頭 CLI 截圖

下一步：
- 把首頁那張卡片連到真正的文章頁 `posts/2026-08-19-第一天.md`（或 .html）

## 2026-08-19（第二段）— 風格定調與改版

先用 grilling 技能把設計決策問到底（14 條），結論寫進 `CLAUDE.md`。重點：
讀者第一順位是自己（不為陌生初學者補解釋）、一週至少一篇、站名「參拾 aChi」、
標語刪掉等自己的句子、上線走 GitHub Pages（`hugo0963.github.io/blog`）。

改了什麼：
- 配色從深色改成**米白為主**，加一組 `@media (prefers-color-scheme: dark)`，
  系統深色模式時自動變深色。**純 CSS，沒有 JavaScript**
- 內容寬度 720 → 680，字級 17 → 18，行距 1.8 → 1.9（閱讀優先）
- 站名與頁尾改成「參拾 aChi」，`aChi` 用 `<em>` 標成強調色
- 新增 `_template.html` 新文章範本、`posts/` 資料夾、`CLAUDE.md` 專案規則

驗證方式與踩到的坑：
- Chrome 無頭模式的 `--force-prefers-color-scheme=dark` **無效**，截出來還是淺色。
  改用「複製一份到暫存目錄、把深色色票附加成 `:root`」的方式強制渲染才截到深色版
- 順手用左上角像素值確認深淺真的不同（`(250,249,247)` vs `(14,17,22)`），
  比肉眼看截圖可靠
- 文章頁第一版的標籤跟第一段黏在一起 → 補 `.post .tags { margin-bottom: 32px; }`

截圖：`screenshots/2026-08-19-首頁-淺色.png`、`-深色.png`、`-文章範本.png`

下一步：上線（第二階段）——裝 gh、登入、git init、推上 GitHub、開啟 Pages。
