# 國中複習網站

數學・物理・化學 三科複習教材，適合手機閱讀。

---

## 如何放到 GitHub Pages（免費網站）

### 第一步：建立 GitHub 帳號
1. 前往 [github.com](https://github.com)
2. 點「Sign up」，用電子信箱註冊
3. 記下你的「用戶名稱」（username）

### 第二步：建立新的 Repository（倉庫）
1. 登入後，點右上角的「+」→「New repository」
2. Repository name 輸入：`study`（或任何名字）
3. 選「Public」（公開）
4. 點「Create repository」

### 第三步：上傳檔案
1. 在新建的 repository 頁面，點「uploading an existing file」
2. 把這個資料夾裡的所有檔案**拖進去**（注意要保留資料夾結構）：
   ```
   index.html
   css/
     main.css
   chemistry/
     index.html
     ch5.html
   math/
     index.html
   physics/
     index.html
   ```
3. 拉到下方，點「Commit changes」

### 第四步：開啟 GitHub Pages
1. 在 repository 頁面，點「Settings」（設定）
2. 左側選單找「Pages」
3. 在「Source」選「Deploy from a branch」
4. Branch 選「main」，資料夾選「/ (root)」
5. 點「Save」

### 第五步：等待部署（約1～2分鐘）
- 網站網址會是：`https://你的用戶名.github.io/study/`
- 例如：`https://apple123.github.io/study/`

---

## 之後怎麼新增內容

每次要新增章節：
1. 把新的 HTML 檔案放到對應資料夾（chemistry、math、physics）
2. 在對應的 `index.html` 中加上那個章節的連結
3. 重新上傳到 GitHub，網站自動更新

---

## 資料夾結構

```
index.html              ← 首頁（選科目）
css/
  main.css              ← 共用樣式
chemistry/
  index.html            ← 化學主頁（選章節）
  ch5.html              ← 第五章：元素及化合物 ✅
math/
  index.html            ← 數學主頁（待新增）
physics/
  index.html            ← 物理主頁（待新增）
```
