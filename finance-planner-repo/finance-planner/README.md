# 目標理財規劃器

用 PV（現值）、FV（終值）、PMT（定期投入）與期數，依理財目標做試算與建議的純靜態網站。無建置步驟、無外部依賴。

## 功能
- **每月該存多少（PMT）**：依目標、本金、年限、報酬率、通膨回推每月投入，並附敏感度分析
- **未來會有多少（FV）**：依每月投入推算終值與今日購買力
- **多久能達標（N）**：算出需要幾年幾個月
- **需要多少本金（PV）**：退休提領試算與年提領率
- 資產成長圖、期初／期末投入切換、深色模式、手機版面

> 試算結果依假設報酬率推算，僅供規劃參考，非投資建議。

## 專案結構
```
finance-planner/
├── public/            # 部署內容（Cloudflare Pages 輸出目錄）
│   ├── index.html     # 整個網站
│   └── _headers       # Cloudflare 安全標頭
├── wrangler.toml      # Cloudflare Pages 設定
├── package.json       # dev / deploy 指令
├── .github/workflows/deploy.yml   # 選用：GitHub Actions 部署
└── README.md
```

## 一、上傳到 GitHub
1. 在 GitHub 建立新的空 repository（例如 `finance-planner`，不要勾選加入 README）
2. 在本資料夾執行：
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<你的帳號>/finance-planner.git
git push -u origin main
```

## 二、部署到 Cloudflare Pages

### 方法 A：Git 連動（推薦，之後 push 就自動更新）
1. Cloudflare 後台 → Workers & Pages → Create → Pages → Connect to Git
2. 授權並選擇 `finance-planner` repo
3. 設定：
   - Production branch：`main`
   - Framework preset：`None`
   - Build command：**留空**
   - Build output directory：`public`
4. Save and Deploy，完成後得到 `https://finance-planner.pages.dev`

### 方法 B：Wrangler 指令（手動部署）
```bash
npx wrangler login
npm run deploy
```
第一次執行時若專案不存在，Wrangler 會詢問是否建立。

### 方法 C：GitHub Actions 自動部署
見 `.github/workflows/deploy.yml` 內的說明（需設定 API Token 與 Account ID）。
若已使用方法 A，請勿同時啟用，以免重複部署。

## 本機預覽
```bash
npm run dev
```
或直接用瀏覽器開啟 `public/index.html`。

## 自訂網域
Cloudflare 後台 → 該 Pages 專案 → Custom domains → Set up a custom domain。
