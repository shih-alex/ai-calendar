# AI 行事曆（GitHub Pages 網頁版 / iPhone PWA）

結合行事曆、待辦事項與 **Google Gemini API** 的純前端智慧排程網頁應用，專為 **GitHub Pages** 部署與 **iPhone Safari「加入主畫面」** 設計。

---

## 功能亮點

- **純瀏覽器直連 Gemini API**：免伺服器、免註冊，API Key 與所有行程、待辦資料只存在你的裝置瀏覽器（`localStorage`）裡。
- **多模態智慧排程**：
  - 直接打字（例如「下週三下午三點牙醫回診」、「這週五前要繳電費提醒我」）。
  - 支援**拖曳檔案、剪貼簿直接貼上截圖（Ctrl+V）、手機相簿選圖、相機拍照**，格式涵蓋 **圖片、PDF、Word (`.docx`)、Excel (`.xlsx`)、PowerPoint (`.pptx`)、TXT / CSV / ICS**，支援多檔混合一次解析。
  - **精準分類**：有明確時間 → 行事曆行程；無明確時段或只有截止日 → 待辦事項。
  - **重複排程與自然語言修改／取消**：支援每天／每週特定星期／每月固定日重複規則，以及打「把明天會議改到後天三點」或「取消週五聚餐」自動比對修改與刪除。
- **人機確認與時間衝突警告**：解析後跳出預覽確認卡片，標示時間衝突警告並可就地微調，或於設定開啟「單筆高信心純文字自動加入（附 6 秒復原）」。
- **一鍵匯出 `.ics` 加入 iPhone 原生行事曆**：支援匯出單一或全部行程（含重複規則與系統鬧鐘提醒），iPhone Safari 點開直接加入 Apple 行事曆。
- **JSON 完整備份與還原**：隨時下載與還原資料，不怕清除瀏覽器快取。

---

## GitHub Pages 上線步驟

本專案已同時內建兩種 GitHub Pages 部署方式（輸出目錄 `docs/` 與自動化工作流 `.github/workflows/deploy-pages.yml`）：

1. 在 GitHub 建立新 Repository（例如 `ai-calendar`）。
2. 將本專案推送至 GitHub：
   ```powershell
   git push -u origin main
   ```
3. 進入 GitHub Repository 的 **Settings → Pages**：
   - 方式 A（最快）：**Source** 選 **Deploy from a branch** → Branch 選 **`main`**、資料夾選 **`/docs`** → Save。
   - 方式 B：**Source** 選 **GitHub Actions**，之後每次 push 皆會自動執行測試並重新建置部署。
4. 完成後打開你的專屬網址：`https://shih-alex.github.io/ai-calendar/`

---

## 在 iPhone 當成原生 App 使用

1. 用 iPhone 的 **Safari** 開啟上述 GitHub Pages 網址。
2. 點選畫面底部的 **「分享」** 圖示（方框向上箭頭）。
3. 選擇 **「加入主畫面」** → **「新增」**。
4. 進入 **「設定」** 分頁，貼上你在 [Google AI Studio](https://aistudio.google.com/apikey) 取得的 Gemini API Key 並測試連線即可開始使用！

---

## 本機開發與驗證指令

```powershell
# 安裝依賴
npm.cmd install

# 啟動開發預覽
npm.cmd run dev

# 型別檢查、單元測試與打包產出至 docs/
npm.cmd run typecheck
npm.cmd test
npm.cmd run build
```
