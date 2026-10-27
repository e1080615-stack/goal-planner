# 目標理財規劃器

用 PV（現值）、FV（終值）、PMT（定期投入）與期數，依理財目標做試算與建議的純靜態網站。無建置步驟、無外部依賴。

> 試算結果依假設報酬率推算，僅供規劃參考，非投資建議。

## 功能
- 每月該存多少（PMT）、未來會有多少（FV）、多久能達標（N）、需要多少本金（PV）
- 通膨調整、敏感度分析、資產成長圖、深色模式、手機版面

## 檔案結構（index.html 在最外層）
```
finance-planner/
├── index.html   # 整個網站
├── _headers     # Cloudflare 安全標頭（可刪）
├── .gitignore
└── README.md
```

## 部署到 Cloudflare Pages
**直接上傳（最簡單）**
Workers & Pages → Create → Pages → Upload assets → 把整個資料夾（或 zip）拖進去 → Deploy。

**GitHub 連動**
1. 把這個資料夾的內容上傳到 GitHub repo（index.html 要在 repo 最外層）
2. Cloudflare → Pages → Connect to Git → 選 repo
3. Build command 留空，Build output directory 留空（或填 `/`）→ Deploy

**指令部署**
```bash
npx wrangler pages deploy . --project-name=finance-planner
```

## 本機預覽
直接用瀏覽器開啟 `index.html`。
