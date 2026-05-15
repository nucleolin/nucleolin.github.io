# Analytics Setup Guide — yangchenlin.github.io

## Option A: Google Analytics 4 (GA4)

### 優點
- 免費、功能最完整
- 頁面瀏覽、停留時間、裝置、地理、來源 referrer 全有
- 後台有地圖視圖可以看訪客來自哪個國家

### 設定步驟

1. 前往 https://analytics.google.com
2. 點 Admin（左下齒輪）→ Create → Property
3. 填寫：
   - Property name: `Yang Chen Lin Website`
   - Reporting time zone: `Taiwan`
   - Currency: 任意
4. 選 **Web** platform → 填入 `yangchenlin.github.io`
5. 拿到你的 **Measurement ID**，格式：`G-XXXXXXXXXX`

### 加入所有 HTML 頁面

在每個 HTML 的 `<head>` 內，把 `G-XXXXXXXXXX` 換成你的真實 ID：

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

需要加到這 4 個檔案：
- `about.html`
- `research.html` ✅ (已加入)
- `publications.html`
- `news.html` ✅ (已加入)

### GA4 後台重要報表

| 報表位置 | 可以看到 |
|---|---|
| Reports → Realtime | 目前線上幾人、在哪頁 |
| Reports → Engagement → Pages | 每頁瀏覽數、平均停留時間 |
| Reports → User → Demographics | 來源國家、城市 |
| Reports → Tech → Tech details | 裝置類型、瀏覽器、OS |
| Reports → Acquisition | 流量來源（Google / Twitter / Direct） |

---

## Option B: Umami (推薦併用)

### 優點
- 介面極簡、漂亮
- 不需要 cookie banner（GDPR compliant）
- 可以把統計數字公開顯示在你的網站上（學術個人網站很加分）
- 免費方案：https://umami.is（cloud）或自架

### 設定步驟

1. 前往 https://umami.is → Sign Up（免費）
2. Add Website → 填入 `yangchenlin.github.io`
3. 拿到追蹤碼，長這樣：

```html
<script defer src="https://cloud.umami.is/script.js"
  data-website-id="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"></script>
```

4. 貼到所有頁面的 `</body>` 前

### 公開統計頁面

在 Umami 後台 Settings → Websites → Share URL，
可以生成一個公開連結，直接嵌入你的網站 footer 或 About 頁。

---

## 建議

同時跑 GA4 + Umami：
- GA4 用來深入分析（哪篇 paper 被看最多次、從哪裡來的流量）
- Umami 用來展示給訪客看（"This site has X visitors from Y countries"）

---

## GitHub Pages 部署提醒

推送到 GitHub 後，GA 需要約 **24–48 小時**才會開始有穩定數據。
Realtime 報表是即時的，可以用來驗證追蹤碼是否正確安裝。

驗證方式：
1. 打開 GA4 → Reports → Realtime
2. 用手機或另一台電腦開你的網站
3. Realtime 頁面應該顯示 "1 user in last 30 minutes"
