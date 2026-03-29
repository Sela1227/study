# 國中複習

數學・物理・化學 三科複習教材，適合手機閱讀。
GitHub Pages 靜態網站。

---

## 版本歷程

### V1.1 — 2026.03.29
**全站北歐美學設計重製**
- 配色：暖米色底（#F4F2ED）、自然材質色系（板岩藍 · 森林綠 · 暖棕土）
- 字型：輕量化層次（300–500 weight），大量留白
- 版型：極簡卡片、細線邊框、無裝飾
- 各科頁面加入統一頂部導覽列

**新增內容**
- 化學科：第一次段考 30 題完整解析（觀念 · 平衡方程式 · 質量守恆 · 莫耳計算）
- 化學科章節狀態顯示更新

**版本控制系統建立**
- 建立版本命名規則：V[主版本].[次版本]
- 新增此 Changelog

---

### V1.0 — 2026.03 初始版本
- 網站架構建立（首頁 → 科目 → 章節）
- 化學第五章完整教材（10 堂課）
  - 萬物分類 · 元素 · 原子構造 · 元素命名
  - 化合物 · 化學鍵結 · 金屬 vs 非金屬
  - 週期表 · 重要元素 · 挑戰測驗
- 數學・物理佔位頁面

---

## 如何上傳到 GitHub Pages

### 第一次設定
1. 前往 [github.com](https://github.com) 建立帳號
2. 點右上角「+」→「New repository」，名稱輸入 `study`，選 Public
3. 點「uploading an existing file」，把 zip 解壓縮後，**把所有檔案和資料夾拖進去**
4. 點「Commit changes」
5. 進 Settings → Pages → Source 選「Deploy from a branch」→ Branch 選 `main`，資料夾 `/ (root)` → Save
6. 約 1 分鐘後，網址為 `https://你的用戶名.github.io/study/`

### 之後更新
1. 在 GitHub 上開啟對應的檔案，點鉛筆圖示直接編輯，或
2. 直接上傳新的 HTML 檔案（會覆蓋舊的）

---

## 檔案結構

```
index.html                      ← 首頁（選科目）
css/
  main.css                      ← 共用樣式（Nordic Design System）
chemistry/
  index.html                    ← 化學主頁（章節 + 段考列表）
  ch5.html                      ← 第五章：元素及化合物 ✅
  exam1.html                    ← 第一次段考詳解 ✅
math/
  index.html                    ← 數學主頁（待新增）
physics/
  index.html                    ← 物理主頁（待新增）
README.md                       ← 這個檔案
```

---

## 版本命名規則

`V[主版本].[次版本]`

- **主版本**：大幅架構改動或設計重製時遞增（V1 → V2）
- **次版本**：新增內容或小調整時遞增（V1.1 → V1.2）

每次更新請同步修改：
1. 本 README 的版本歷程
2. 各頁面 footer 的版本號
