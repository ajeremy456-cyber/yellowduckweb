# 小鴨電腦工作室 & 小鴨代購

同一個 repo 放兩個網站，用 GitHub Pages 發布後會自動分成子路徑。

## 上傳步驟

```bash
git init
git add .
git commit -m "初始化網站"
git branch -M main
git remote add origin https://github.com/你的帳號/repo名稱.git
git push -u origin main
```

到 GitHub repo → Settings → Pages → Source 選 `main` / `root` → Save。

發布後網址：
- 首頁導覽：`https://你的帳號.github.io/repo名稱/`
- 電腦工作室：`https://你的帳號.github.io/repo名稱/computer-studio/`
- 小鴨代購：`https://你的帳號.github.io/repo名稱/duck-shopping/`

## 電腦工作室網站要改的地方

打開 `computer-studio/index.html`，搜尋以下文字並替換成真實資料：
- `0900-000-000（先預留，之後請自行修改）` → 真實電話
- `雲林縣○○鄉○○路000號（先預留，之後請自行修改）` → 真實地址
- `LINE QRcode<br>待替換圖片` 那一段的 `.qr-placeholder` → 換成你的 LINE QRcode 圖片（把圖片放進 `computer-studio/` 資料夾，改成 `<img src="line-qr.png">`）
- 服務項目與價格可直接在 `<div class="service-row">` 區塊內修改文字

## 小鴨代購後台設定（第一次使用）

1. 打開 `https://你的帳號.github.io/repo名稱/duck-shopping/admin.html`
2. 到 GitHub 申請 **Personal Access Token**：
   - 右上角頭像 → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token
   - Repository access 選你這個 repo
   - Permissions 裡的 **Contents** 設為 **Read and write**
   - 產生後複製 token（只會顯示一次，要存好）
3. 在 admin.html 點「⚙️ 連線設定」，填入：
   - GitHub 帳號 / 組織名稱
   - Repository 名稱
   - 分支名稱（通常是 `main`）
   - products.json 路徑：`duck-shopping/products.json`
   - 貼上剛剛的 token
   - 按「儲存設定」
4. 之後就可以直接在表單新增商品，按「新增到網站」會自動幫你 commit 更新 `products.json`

### 重要提醒

- **admin.html 這個網址不要公開分享**，因為任何拿到這個網址、又知道你 token 的人都能改商品資料。它不會出現在導覽選單或前台頁面上，但技術上只要知道網址還是打得開，所以自己保存好連結即可。
- 新增商品後，GitHub Pages 大約需要 30 秒到 1 分鐘重新部署，前台才會顯示。
- 商品圖片目前用「圖片網址」的方式帶入，建議先把圖片上傳到圖床（或之後请我教你怎麼把圖片一起放進 repo 裡）再貼網址。
