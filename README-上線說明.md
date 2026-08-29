# 世一未來分析 SHIYI FUTURE ANALYTICS — 官方網站

純靜態網站（HTML + CSS + JS，無需伺服器、無需資料庫、無建置流程）。
把整個資料夾丟到任何靜態主機就會動。

---

## 一、檔案結構

```
index.html              首頁
about.html              關於我們
services.html           服務總覽
services/
  big-data.html         網路大數據分析
  polling.html          民調統計分析
  election.html         視覺化選情預測
  ai-prediction.html    AI 數據預測
  brand.html            品牌與市場分析
  visualization.html    資料視覺化
cases.html              案例研究
insights.html           數據洞察
contact.html            聯絡我們
404.html                找不到頁面
.nojekyll               關閉 GitHub 的 Jekyll 處理（必要，勿刪）
sitemap.xml             給 Google 的網站地圖
robots.txt              爬蟲規則
assets/
  css/style.css         全站樣式（唯一一支）
  js/main.js            全站互動（唯一一支）
  img/                  Logo、favicon、社群分享圖
```

---

## 二、上線（GitHub Pages，免費）

這份網站已經設定成部署在 `https://shiyi-deploy.github.io`。

**1. 把 repo 改名**
`github.com/shiyi-deploy/shiyi-deploy` → **Settings** → 最上面 **Repository name** 改成：

```
shiyi-deploy.github.io
```

（一定要一字不差，GitHub 靠這個名稱判斷要把站台放在網域根目錄。）

**2. 上傳檔案**
回到 repo 首頁 → **Add file** → **Upload files** → 把解壓縮後資料夾**裡面**的東西全部拖進去
（拖進去後應該看到 `index.html`、`assets`、`services` 在最外層，不是包一層資料夾）
→ 下方 **Commit changes**

> 隱藏檔 `.nojekyll` 很重要，不要漏掉。它會關閉 GitHub 的 Jekyll 處理，否則有些檔案不會被正確發布。
> Mac 上按 `Cmd + Shift + .` 可以顯示隱藏檔，Windows 在檔案總管的「檢視」勾「隱藏的項目」。

**3. 開啟 Pages**
**Settings** → 左側 **Pages** → Source 選 **Deploy from a branch** → Branch 選 **`main`** 和 **`/ (root)`** → **Save**

等 1～3 分鐘，網站就會出現在：

```
https://shiyi-deploy.github.io/
```

---

## 二之一、改用 Cloudflare Pages（替代方案）

如果你之後想改用 Cloudflare：做法是 Workers & Pages → Create application → Get started → Drag and drop your files，專案名稱要填 `shiyi-deploy`，並且要先把網站裡的網址換掉（見第三節）。

---

## 二之二、配色說明

網站採**淺色主題**：冷調偏藍的米白底（`#F4F7FB`）、白色卡片、深藍墨字（`#041D48`，取自 Logo）。
品牌青分成兩支：`--cyan`（`#22C3F5`）只用在圖表填色，`--cyan-ink`（`#0A6E9E`）用在文字與連結，確保白底上的對比度符合 WCAG AA。
全站唯一的深色區塊是每頁下方的 CTA（深藍卡片），刻意做為視覺重點。

所有文字與底色的對比度都已實測，最低的一組也在 4.3:1 以上。

---

## 三、換成自己的網域

1. 買網域（`.com` 約 NT$400／年；Cloudflare Registrar、Gandi、GoDaddy 都可以）
2. repo → **Settings** → **Pages** → **Custom domain** 填入網域 → 到你的網域商設定 DNS（GitHub 會顯示要填的值）；設定完記得勾 **Enforce HTTPS**
3. **重要**：換網域後要更新網站內的網址設定
   - 全站搜尋 `https://shiyi-deploy.github.io`
   - 全部取代成你的新網址（例如 `https://shiyifuture.com`）
   - 會出現在每頁的 `<link rel="canonical">`、Open Graph 標籤、`sitemap.xml`、`robots.txt`
   - 若之後請我改，我這邊只要改一個變數就會全部重產

---

## 四、讓 Google 搜尋得到（最重要的一步）

網站上線 ≠ Google 找得到。以下三件事要做：

### 1. Google Search Console（必做）
1. 到 <https://search.google.com/search-console>
2. 選 **網址前置字元**，輸入完整網址（含 `https://`）
3. 驗證方式選 **HTML 標記**，複製它給的那行 `<meta name="google-site-verification" ...>`
4. 貼到 `index.html` 的 `<head>` 裡面（任何一行都可以，放在 `<title>` 下面最好），重新部署
5. 回 Search Console 按驗證
6. 左側 **Sitemap** → 輸入 `sitemap.xml` → 提交
7. 左側 **網址審查** → 貼上首頁網址 → **要求建立索引**（每頁都可以做一次，會快很多）

通常 **3～14 天**會被收錄。搜尋「世一未來分析」時，因為沒有人跟你搶這個關鍵字，收錄後很快就會排在第一。

### 2. Google 商家檔案（有實體地址才做）
<https://business.google.com> 申請，需要明信片或電話驗證。
通過後，搜尋公司名時右側會出現資訊卡（地址、電話、營業時間、評論），這對品牌搜尋的效果最大。

### 3. 外部連結（加速收錄）
Google 是靠連結發現新網站的。把網址放到：
- Facebook／Instagram 粉專的「網站」欄位
- LinkedIn 公司頁
- Email 簽名檔
- 任何你有帳號的產業目錄

有 2～3 個外部連結，收錄速度會明顯變快。

---

## 五、常見修改位置

| 想改什麼 | 改哪裡 |
|---|---|
| Email、公司名 | 全站搜尋 `shiyifuture@gmail.com` 取代 |
| 主色（圖形用的品牌青） | `assets/css/style.css` 最上方 `--cyan` |
| 主色（文字／連結用，較深） | 同上 `--cyan-ink` |
| 底色（頁面／卡片） | 同上 `--bg`、`--bg-2`、`--surface`、`--surface-2` |
| 標題與按鈕的深藍 | 同上 `--navy`、`--navy-2` |
| 服務項目文字 | 各 `services/*.html` |
| 案例內容 | `cases.html` |
| 文章列表 | `insights.html` |
| 社群分享圖 | `assets/img/og-image.png`（1200×630） |

---

## 六、內容規範（已內建，請勿移除）

網站上所有數字、圖表、地圖、案例都是**示意資料**，且已在畫面上明確標示：

- 儀表板：`DEMO DATA｜示意資料`
- 選情地圖：`Illustrative Data｜示意資料`
- 案例：`CASE STUDY DEMO`，且「主要發現」欄位皆標示為「示意展示」
- 全站未出現任何真實客戶名稱、合作企業、民調數據或選舉預測結果
- 全站未使用「全球領先」「最準確」「100% 準確」等無法證明的宣稱

之後若要換成真實案例，請務必連同「示意資料」標記一起更新，避免示意數字被誤讀為研究結果。

---

## 七、聯絡表單說明

目前是靜態表單：使用者按「送出需求」會開啟他自己電腦的郵件程式，內容已自動填好，寄到 `shiyifuture@gmail.com`。

想改成「直接進信箱、不開郵件程式」，可以接免費服務（不需要後端）：
- [Formspree](https://formspree.io)（免費每月 50 封）
- [Web3Forms](https://web3forms.com)（免費無上限）
- Cloudflare Pages Functions（自己寫，免費）

需要的話跟我說，我幫你接。
