# 阿蔓明道國中復習專班 — 設計規格書

**版本：V1.3　最後更新：2026.03.29**

這份文件完整描述網站的設計語言，讓任何新頁面的設計都能與現有頁面一致，不需要重新摸索。

---

## 一、設計哲學

這個網站採用**北歐極簡美學（Nordic Minimalism）**，核心原則只有三條：

1. **暖而不冷** — 所有色調帶暖色調，沒有純冷灰，背景是羊皮紙暖米色而非白色
2. **留白即設計** — 間距慷慨，卡片之間的空白和卡片本身同等重要
3. **克制的層次** — 字重只用 300/400/500，顏色只在必要時才出現

**不做的事：**
- 不用漸層（gradient）
- 不用 box-shadow
- 不用粗邊框（border > 1px）
- 不用大圓角（border-radius > 8px，導覽列元素 ≤ 4px）
- 不用彩色大面積背景
- 不用 emoji 做 icon（content pages 例外）
- 不加動畫（除非功能需要）
- 不用超過 500 的字重（除非是互動元素的 label）

---

## 二、色彩系統

### 基礎色（所有頁面）

```css
--bg:       #F4F2ED;   /* 頁面背景：暖羊皮紙 */
--surface:  #FFFFFF;   /* 卡片白 */
--surface2: #F9F8F5;   /* 微暖白，用於 hover 或嵌套區域 */

--border:       #E3DFDA;   /* 常用邊框 */
--border-mid:   #CCCAB5;   /* 較深邊框，分隔線、箭頭 */
--border-dark:  #B0ADA4;   /* 最深邊框，少用 */

--text-1: #1A1916;   /* 主文字：近黑色 */
--text-2: #65635E;   /* 次要文字 */
--text-3: #A5A29C;   /* 說明文字、placeholder */
```

### 三個科目的 accent 色（自然材質靈感）

```css
--math:        #2B4C7E;   --math-light:  #EAF0F8;   /* 深海板岩藍 */
--phys:        #3A5C42;   --phys-light:  #EBF2EC;   /* 森林綠 */
--chem:        #7A4E36;   --chem-light:  #F5EDE8;   /* 暖棕土/赤陶 */
```

### 狀態色

```css
--done:    #3A5C42;   --done-bg:  #EBF2EC;   /* 完成：森林綠 */
--wip:     #78600A;   --wip-bg:   #F5EDDA;   /* 進行中：麥穗黃 */
--todo:    #A5A29C;   --todo-bg:  #EEECEA;   /* 待辦：灰 */
```

### 化學第五章內頁——六色系統（section 區分）

ch5.html 內部各 section 有自己的 accent，全部使用同一套暖色調系統：

| Section | 用途 | 文字色 | 背景色 | 邊框色 |
|---|---|---|---|---|
| 觀念判斷 | `--concept-c` | `#7A6018` | `#F5EDD8` | `#C9A84C` |
| 平衡方程式 | `--balance-c` | `#3A5C42` | `#EBF2EC` | `#7AB888` |
| 質量守恆 | `--mass-c` | `#7A4E36` | `#F5EDE8` | `#C47F64` |
| 莫耳計算 | `--mole-c` | `#2B4C7E` | `#EAF0F8` | `#6A9AC4` |
| 手寫題 | `--written-c` | `#5A3E6E` | `#EEE8F4` | `#9A7EC0` |

### 化學第六章——覆蓋色系（同上五個 accent + 第六個）

ch6.html 的六個 section 對應的 CSS 變數覆蓋值：

```css
--c1: #2B4C7E;  --c1l: #EAF0F8;   /* 6-1 原子說：板岩藍 */
--c2: #3A5C42;  --c2l: #EBF2EC;   /* 6-2 分子：森林綠 */
--c3: #78600A;  --c3l: #F5EDD8;   /* 6-3 粒子觀點：麥穗黃 */
--c4: #5A3E6E;  --c4l: #EEE8F4;   /* 6-4 化學式：煙燻紫 */
--c5: #7A4E36;  --c5l: #F5EDE8;   /* 6-5 原子量莫耳：赤陶土 */
--c6: #2C5F6E;  --c6l: #E8F3F5;   /* 章末複習：北歐藍綠 */
```

---

## 三、字型系統

### 字型堆疊

```css
font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", "Segoe UI",
             "Hiragino Sans", "Noto Sans TC", sans-serif;
```

### 字型層次表

| 用途 | 大小 | 字重 | 其他 |
|---|---|---|---|
| 頁面大標題（首頁 hero） | 32px | 300 | letter-spacing: -.02em |
| 科目頁標題 | 28px | 300 | letter-spacing: -.015em |
| 內頁 section 標題 | 22px | 300 | — |
| 卡片主標題 | 18px | 400 | letter-spacing: -.01em |
| 項目標題（.item-title） | 14px | 500 | — |
| 正文 | 14–15px | 400 | line-height: 1.65–1.75 |
| 說明文字（.item-sub） | 12–13px | 400 | color: text-3 |
| 標籤/狀態/版本（.section-head-label） | 10–11px | 500–600 | uppercase, letter-spacing: .12em |
| footer | 11px | 400 | color: text-3 |

**規則：**
- 600/700 weight **只出現在**互動元件的標籤（如 quiz 答案 label）
- 主要文字大小：移動端 14px，不低於 13px
- 中英文混排時，英文 label（如 "Chemistry"、版本號）用小字配大中文標題，製造層次感

---

## 四、間距與形狀

```css
--r:   4px;   /* 標準圓角，用於卡片、項目、按鈕 */
--r-s: 2px;   /* 小圓角，用於徽章、tag */
```

**間距原則：**

| 位置 | 值 |
|---|---|
| 頁面容器最大寬度 | 560px（main.css）/ 640px（content pages）|
| 頁面左右 padding | 20px |
| 頁面底部 padding | 56px（避免底部導覽遮擋） |
| 卡片 padding | 16–20px |
| Section 間距 | 32px margin-top |
| 連接列表（card-stack）卡片間隔 | 1px（border 重疊效果） |
| 元件間距（gap） | 8–10px |
| Hero 區域上方 padding | 52px |

---

## 五、元件清單

### 5.1 頂部導覽列（Topbar）

```css
height: 52px;
position: sticky; top: 0; z-index: 100;
background: rgba(244,242,237,.94);
backdrop-filter: blur(12px);
border-bottom: 1px solid var(--border);
```

結構：`← 上一層` + `/` 分隔 + 當前頁標題

返回按鈕：13px，color: text-2，min-height: 44px（可觸控）

---

### 5.2 Hero 區（首頁）

```
上方小標（英文 or 說明）— 11px，uppercase，text-3
主標題 — 32px，weight 300
副標題 — 14px，text-2
```

---

### 5.3 區段標題（Section Divider）

```html
<div class="section-head">
  <span class="section-head-label">章節教材</span>
  <div class="section-head-line"></div>
</div>
```

標籤：10px，weight 600，uppercase，letter-spacing .14em，color: text-3
橫線：1px solid border，flex: 1

---

### 5.4 科目卡片（Subject Card）

首頁用，帶左側 10px 彩色圓點。

```
padding: 20px 18px
border: 1px solid border
border-radius: 4px
hover: border-color → border-mid
active: background → surface2
```

---

### 5.5 項目列表（Card Stack）

科目頁章節/段考列表。外包 `.card-stack-wrap`（border + overflow:hidden），裡面 `.item` 用 border-top: 1px 分隔，第一個不顯示 border-top。

```
.item: padding 16px, min-height 64px
.item-num: 12px, text-3, width 22px
.item-title: 14px, weight 500
.item-sub: 12px, text-3
.item-arrow: 16px, border-mid
```

**Disabled 狀態：** opacity .5，pointer-events: none

---

### 5.6 狀態徽章（Status）

```html
<span class="status s-done">
  <span class="status-dot"></span>完成
</span>
```

```
font-size: 11px; font-weight: 500; letter-spacing: .02em;
dot: 5px 圓形
```

三種狀態：`.s-done`（森林綠）、`.s-wip`（麥穗黃）、`.s-todo`（灰）

---

### 5.7 統計方格（Stats Grid）

科目頁頂部，3欄，卡片間 1px gap（用 background: border 做）。

```
.stat-n: 22px, weight 300
.stat-l: 11px, text-3, letter-spacing .04em
```

---

### 5.8 Footer

```html
<div class="page-footer">
  <span class="footer-left">科目 · 阿蔓明道國中復習專班</span>
  <span class="footer-right">V1.x</span>
</div>
```

兩端對齊，11px，text-3，border-top: 1px solid border，margin-top: 56px

---

### 5.9 內頁（ch5/exam1）通用元件

以下元件在 ch5.html 和 exam1.html 中定義，新的 content page 建議複用：

**Callout/Highlight Box**
```
border-left: 3px solid [accent]; border-radius: 4px; padding: 12–14px;
使用 accent 的淡色背景（light variant）
```

**化學方程式框**
```css
background: var(--bg); border: 1px solid var(--border);
border-radius: 4px; font-family: Georgia, serif;
font-size: 14px; text-align: center; padding: 12px 16px;
```

**步驟列表（Steps）**
圓形編號（22×22px，使用 accent 背景），旁邊是 13px 說明文字

**總結區（Summary）**
```css
background: #EBF2EC; border: 1px solid #7AB888;
border-radius: 6px; padding: 1rem 1.25rem;
```
帶 ✓ 前綴的列表項

**Quiz 題卡**
```css
background: #FFFFFF; border: 1px solid var(--border);
border-radius: 4px; padding: 14px 16px;
```
收合時顯示：題號徽章 + 題目標題 + 答案徽章 + ▾ 箭頭
展開後：body 區域帶 border-top

---

## 六、頁面結構類型

目前網站有三種頁面類型：

### 類型 A：導覽頁（index.html、chemistry/index.html 等）
使用 `main.css`，結構：頂部 topbar → hero/header → section divider → card stack → footer

### 類型 B：教材頁（ch5.html、ch6.html）
自帶完整 CSS，結構：sticky 頂部導覽（含返回按鈕）→ 橫向分頁標籤 → 課程內容 → 底部上下課按鈕

### 類型 C：考題詳解頁（exam1.html）
自帶完整 CSS，結構：sticky 返回導覽 → sticky 題型標籤列 → 手風琴題卡

---

## 七、互動行為規則

- **可點擊區域最小高度：44px**（可觸控標準）
- **Hover**：border-color 加深或 background → surface2，不加陰影
- **Active/Press**：background → #EDEBE5（比 surface2 更深一點）
- **Focus**：border-color → accent（不用 outline）
- **Disabled**：opacity .5，pointer-events: none

---

## 八、新增頁面 Checklist

新增任何頁面前確認：

- [ ] `<meta name="theme-color" content="#F4F2ED">` 已加入
- [ ] `<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">` 已加入
- [ ] title 格式：`頁面名稱 — 阿蔓明道國中復習專班`
- [ ] 頂部有 topbar（← 返回 / 當前頁）
- [ ] 頁面容器最大寬 560–640px，左右 padding 20px
- [ ] footer 包含頁面名稱（左）和版本號（右）
- [ ] 版本號與其他頁面一致
- [ ] 無漸層、無 box-shadow、無大圓角
- [ ] 文字不小於 13px
- [ ] 返回按鈕 min-height: 44px

---

## 九、版本命名規則

格式：`V[主版本].[次版本]`

- **主版本遞增**：大幅設計重製或架構重組
- **次版本遞增**：新增章節、修改教材、功能小調整

每次版本更新必須同步：
1. README.md 的版本歷程
2. 所有頁面 footer 的版本號（目前是 V1.3）
3. 如是重要更新，更新 `css/main.css` 檔頭的版本備注

---

## 十、檔案結構

```
index.html              ← 首頁（類型 A）
css/main.css            ← 共用樣式（類型 A 頁面使用）
chemistry/
  index.html            ← 化學主頁（類型 A）
  ch5.html              ← 第五章（類型 B，自帶 CSS）
  ch6.html              ← 第六章（類型 B，自帶 CSS）
  exam1.html            ← 第一次段考詳解（類型 C，自帶 CSS）
math/
  index.html            ← 數學主頁（類型 A，待新增內容）
physics/
  index.html            ← 物理主頁（類型 A，待新增內容）
README.md               ← 版本歷程 + GitHub Pages 設定說明
DESIGN.md               ← 這個文件
```
