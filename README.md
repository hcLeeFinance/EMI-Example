# 量化投資互動式講義使用說明 (MCU Dept. of Finance — Quantitative Investment)

這是為銘傳大學財務金融學系「量化投資」課程打造的 **互動式單頁網頁講義**，主題為 **Portfolio Weight Determination**，支援 EMI 英文授課及中文同步字幕。

---

## 📂 檔案說明

| 檔案 | 說明 |
|---|---|
| `index.html` | 主講義（桌面投影版，所有功能皆在此單一檔案） |
| `index_pull.html` | 同一份講義的響應式/可捲動變體，適合手機或窄螢幕檢視 |
| `AGENT.md` | AI 協作說明（最新架構、函式與維護規範） |
| `STATUS.md` | 專案狀態與變更記錄 |
| `Portfolio_Weight_Determination_Bilingual_Subtitles.docx` | 全 12 張投影片中英文字幕講稿 |

開啟方式：直接雙擊 `index.html`，在 Chrome 或 Edge 中播放，無需安裝任何軟體。

### `index.html` 與 `index_pull.html` 的關係

兩個 HTML 檔案內容高度相同，皆包含 12 張投影片、Chart.js 效率前緣、KaTeX 公式、TTS、英文/中文字幕講稿、互動計算器與相同的 JavaScript 函式。差異集中在 CSS 版面：

- `index.html` 是主要桌面投影版：slide area 使用 `overflow:hidden`，投影片垂直置中，適合教室投影避免滑動。
- `index_pull.html` 是響應式變體：slide area 使用 `overflow-y:auto`，投影片可隨內容高度伸展，新增 `max-width:768px` 手機/窄螢幕 media query。
- `index_pull.html` 會在小螢幕隱藏英文副標、縮小字體、控制列可換行、兩欄卡片改單欄、右側講稿欄高度縮短。
- 若修改投影片內容、講稿、公式或計算邏輯，兩個 HTML 應同步更新；若只調整手機閱讀體驗，通常只影響 `index_pull.html`。

---

## 📊 投影片結構（12 張）

| Slide | 階段 | 標題 |
|:---:|---|---|
| 1 | — | How to Determine Portfolio Weights? |
| 2 | — | The Asset Allocation Problem |
| 3 | Step 1 of 10 | Define Asset Return & Risk |
| 4 | Step 2 of 10 | Measure Asset Correlation |
| 5 | Step 3 of 10 | Calculate Portfolio Return & Risk |
| 6 | Step 4 of 10 | The Sharpe Ratio — Measuring Risk-Adjusted Performance |
| 7 | Step 5 of 10 | Optimization Objectives & Constraints |
| 8 | Step 6 of 10 | Closed-Form Solution: MVP |
| 9 | Step 7 of 10 | Closed-Form Solution: Tangency |
| 10 | Step 8 of 10 | Compare Three Allocation Methods |
| 11 | Step 9 of 10 | Test the Weight Allocation (Interactive Calculator) |
| 12 | Step 10 of 10 | Visualize the Efficient Frontier (Dynamic Chart) |

---

## 🚀 核心功能

### 1. 🎙️ 雙語講稿側欄 (Script Sidebar)
- 簡報右側有內建講稿，每張投影片都有對應的英文口說稿與教學提示。
- 底部控制列左側的 **`📋 Hide Script`** 按鈕可隱藏側欄，進入全螢幕簡報模式。
- 再按一次 **`📋 Show Script`** 即可重新顯示。
- 字幕語言可透過下拉選單切換：**無字幕 / EN Script / 中文字幕**，與語音語言完全獨立。

### 2. 🔊 文字轉語音 (Text-to-Speech)
- 按下 **`🔊 Speak`** 按鈕，系統會朗讀當前投影片的講稿。
- **`🇺🇸 EN`** / **`🇨🇳 中文`** 按鈕切換朗讀語言（英文或中文）。
- **Voice 下拉選單** 可選擇不同的語音（英文語音與中文語音分組顯示）。
- 勾選 **`Auto`** 後，切換投影片時會自動開始朗讀。
- 語音偏好設定儲存於瀏覽器 `localStorage`，下次開啟仍保留。

> **注意**：Microsoft 語音（如 David、Zira）為 Windows 系統語音，需事先安裝對應語言包。  
> 若缺少中文語音，請至 **Windows 設定 → 時間與語言 → 語音 → 管理語音** 安裝。

### 3. 🧮 互動計算器（Slide 11）
- 拖曳 **Weight in Stock A** 滑桿（0%–100%），即時顯示投資組合的 Return、Risk 與 Sharpe Ratio。
- 展示要點：相關係數 ρ = 0.20 時，組合風險低於各個資產的簡單加權平均，視覺化說明分散投資的威力。

### 4. 📈 動態效率前緣圖（Slide 12）
- 繪製完整的 Markowitz 效率前緣曲線，標示 MVP（最小變異數組合）與 Tangency Portfolio（最大夏普比率）。
- 拖曳 **Correlation (ρ)** 滑桿（−1.0 至 +1.0），曲線即時動態彎曲。
- 展示要點：ρ → −1 時曲線極度向左，ρ → +1 時曲線退化為直線（無分散效果）。

### 5. 📐 數學公式渲染
- 所有公式（MVP、Tangency、Sharpe Ratio、Variance）以 KaTeX 精確渲染，清晰呈現推導過程。
- Slide 6 的 Sharpe Ratio 公式卡片已改為較精簡版面，讓下方「How to Interpret」與「Numerical Example」兩個框框上移、投影時更緊湊。

### 6. 📝 雙語字幕 Word 檔
- `Portfolio_Weight_Determination_Bilingual_Subtitles.docx` 收錄每張投影片的英文與中文字幕講稿，內容來源為 `index.html` 內的 `speakerNotes` 與 `speakerNotesZH`。
- 已讀取 DOCX 內容：文件標題為 `Portfolio Weight Determination`，副標為 `Bilingual Subtitle Scripts / 中英文字幕講稿`，共 12 張投影片，每張依序列出 `English Script` 與 `中文字幕`。最後同步更新：2026-06-29 session 4（Slide 4 相關係數 ρ=0 英中說明文字同步）。

---

## ⏱️ 課堂時間分配建議（約 45–50 分鐘）

| Slide | 建議時間 | 教學重點 |
|:---:|:---:|---|
| 1 | 1 min | 開場，說明本堂課目標 |
| 2 | 3 min | 引出問題：$10,000 如何分配 A 與 B？詢問學生直覺 |
| 3 | 4 min | 介紹報酬率與波動率（σ），帶入數值 r_A=12%, σ_A=20% |
| 4 | 4 min | 解釋相關係數 ρ，用手勢示範 +1 與 −1 的直覺意義 |
| 5 | 4 min | 推導組合報酬與風險公式，代入 50/50 權重計算 |
| 6 | 4 min | 介紹 Sharpe Ratio，帶入數值比較 A、B 與組合 |
| 7 | 4 min | 說明 MVP 與 Tangency Portfolio 的最佳化目標與限制式 |
| 8 | 4 min | 帶出 MVP 封閉解公式，代入數值得出最佳權重 |
| 9 | 4 min | 帶出 Tangency Portfolio 封閉解，比較兩種最佳化結果 |
| 10 | 4 min | 三種方法（50/50、MVP、Tangency）並排比較夏普比率 |
| 11 | 5 min | **互動**：讓學生喊出權重，即時拖曳滑桿驗證 |
| 12 | 5 min | **視覺高潮**：拖曳相關係數滑桿，展示曲線動態變化 |

---

## ⌨️ 快捷鍵

| 按鍵 | 功能 |
|---|---|
| `→` / `空白鍵` / `Enter` | 下一張投影片 |
| `←` | 上一張投影片 |
| `F11` | 瀏覽器全螢幕模式（建議課堂使用） |

---

## 🔧 常見問題

**Q：語音選單顯示「Loading voices...」一直不消失？**  
A：重新整理頁面（F5），或換用 Chrome/Edge 瀏覽器。

**Q：想重設語音偏好？**  
A：開啟瀏覽器 DevTools（F12）→ Application → Local Storage → 刪除 `selectedVoiceEN`、`selectedVoiceZH`、`speakLang`、`subtitleMode`。

**Q：公式沒有正確顯示？**  
A：確認網路連線正常（KaTeX 從 CDN 載入），或換用 Chrome/Edge。
