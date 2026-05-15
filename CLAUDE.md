# nucleolin.github.io — Personal Academic Website

## Project Overview

Yang Chen Lin (YC) 的個人學術網站，純靜態 HTML/CSS/JS，部署在 GitHub Pages。

- **網址**: https://nucleolin.github.io
- **Owner**: Yang Chen Lin (YC), Graduate Researcher, NTHU HMI Lab
- **Research areas**: HCI, Cognitive Neuroscience, Conversational AI, NeuroAI

---

## File Structure

```
nucleolin.github.io/
├── index.html          # redirect → about.html
├── about.html          # About / Bio / Education / Experience / Skills
├── research.html       # Research Vision / Projects / Directions
├── publications.html   # Publication list with filters
├── news.html           # News & Updates + Conferences & Talks (two-column)
├── blog.html           # Blog posts (Research notes / Dev log / Essay)
├── editor.html         # Visual content editor for about.html (local use only)
└── analytics-setup.md  # GA4 + Umami setup guide
```

---

## Design System

### Color Palette — Warm Slate

| Token | Dark | Light |
|---|---|---|
| `--bg` | `#1a1714` | `#f5f2ec` |
| `--bg2` | `#232018` | `#fdfbf7` |
| `--bg3` | `#2c2820` | `#ede9e0` |
| `--fg` | `#ede8e0` | `#1c1814` |
| `--fg2` | `#a89e90` | `#5a5048` |
| `--fg3` | `#665e52` | `#9a9088` |
| `--acc` | `#d4924a` | `#a0640a` |
| `--blue` | `#6aa4c8` | `#2a6a94` |
| `--violet` | `#9d8fe8` | `#5a4ab0` |

### Topic Tag Colors

| Tag | Dark BG | Dark FG |
|---|---|---|
| HCI & Design | `#1e2e1a` | `#6bc46a` |
| Neuroimaging | `#221840` | `#9d8fe8` |
| Conversational AI | `#122040` | `#6aa4c8` |
| NeuroAI | `#2e1e08` | `#d4924a` |

### Typography
- Font: `'Segoe UI', system-ui, sans-serif`
- Base size: 14px, line-height: 1.65

---

## Architecture

- **No build step** — 純靜態 HTML，直接 push 即上線
- **Theme persistence** — `localStorage('theme')` 跨頁同步 dark/light
- **Scroll anchors** — `scroll-margin-top: 72px` 補償 sticky topbar
- **Fade-in** — IntersectionObserver `.fi` → `.fi.vis`
- **Opportunities popup** — sidebar 左下角點擊展開，click-outside 關閉

---

## Common Tasks

### 新增一篇 Publication

在 `publications.html` 的 `#pub-list` 裡，找對應年份的 `.yg` 區塊，複製一個 `.pr` 並修改：

```html
<div class="pr" data-type="conf" data-topics="hci" data-role="first">
  <div class="pr-venue">CHI '27</div>
  <div class="pr-body">
    <div class="pr-title">論文標題</div>
    <div class="pr-authors"><strong>Yang Chen Lin</strong>, Co-author</div>
    <div class="pr-meta">
      <span class="tag tag-hci">HCI & Design</span>
      <span class="tbadge tb-conf">Conference</span>
      <span class="tb-first">★ First author</span>
    </div>
    <div class="pr-links">
      <a class="pl pl-pdf" href="URL">PDF</a>
      <a class="pl pl-doi" href="URL">DOI</a>
      <a class="pl pl-page" href="URL">Project page</a>
      <a class="pl pl-slides" href="URL">Slides</a>
    </div>
  </div>
</div>
```

**data-type 可選值**: `conf` / `lbw` / `workshop` / `journal`
**data-topics 可選值**: `hci` / `neuro` / `ai` / `neuroai`（空格分隔多個）
**data-role**: `first`（first author）或留空

### 新增一篇 Blog Post

在 `blog.html` 的 `#post-list` 最上方插入：

```html
<div class="post-item" data-cat="note">
  <div class="post-top">
    <span class="post-cat cat-note">Research note</span>
    <span class="post-date">Jan 2027</span>
  </div>
  <a class="post-title" href="#">文章標題</a>
  <div class="post-excerpt">一段摘要說明文章內容。</div>
  <div class="post-tags"><span class="tag tag-hci">HCI & Design</span></div>
</div>
```

**data-cat 可選值**: `note` / `dev` / `essay`

### 新增一筆 News

在 `news.html` 左欄 Updates 最上方插入：

```html
<div class="upd-item">
  <div class="upd-dot"></div>
  <div class="upd-body">
    <div class="upd-date">Jan 2027</div>
    <div class="upd-text"><strong>標題。</strong>說明文字。<span class="nb nb-paper">Paper</span></div>
  </div>
</div>
```

**nb 類型**: `nb-paper` / `nb-talk` / `nb-event`

### 新增一筆 Talk

在 `news.html` 右欄 Talks，找對應年份 `.yr-div` 後插入：

```html
<div class="talk-item">
  <div class="talk-head">
    <div class="talk-title">演講標題</div>
    <span class="talk-type tt-conf">Conference</span>
  </div>
  <div class="talk-venue">ACM CHI 2027</div>
  <div class="talk-loc">City, Country · Month Year</div>
  <div class="talk-role">Paper presentation · First author</div>
</div>
```

**talk-type 可選值**: `tt-conf` / `tt-talk` / `tt-poster`

### 新增一個 Project

在 `research.html` 的 `#proj-grid` 裡插入：

```html
<div class="pc" data-status="ongoing" data-tags="hci ongoing">
  <div class="pc-head">
    <div class="pc-title">專案名稱</div>
    <span class="pc-status status-ongoing">Ongoing</span>
  </div>
  <div class="pc-period">MM/YYYY – present · Lab Name</div>
  <div class="pc-desc">專案描述。</div>
  <div class="pc-footer">
    <div class="pc-tags"><span class="tag tag-hci">HCI & Design</span></div>
    <div class="pc-pubs"><a class="pub-chip" href="#">CHI '27</a></div>
  </div>
</div>
```

**data-status**: `ongoing` / `past`

---

## Pending Placeholders

以下內容仍是範例，需要替換成真實資料：

- [ ] `about.html` — 大學學歷、所有外部連結（Scholar / GitHub / Twitter / LinkedIn / CV）
- [ ] `about.html` — 照片（把 `YC` 文字替換成 `<img src="photo.jpg" alt="Yang Chen Lin">`）
- [ ] `about.html` — `mailto:your@email.com` → 真實 email（共 2 處）
- [ ] `research.html` — Projects 和 Directions 的真實描述
- [ ] `publications.html` — 所有 PDF / DOI / Project page / Slides 的真實 URL
- [ ] `news.html` — 確認 talks 的地點和日期
- [ ] `blog.html` — 刪除頂部 WIP 提示框，替換為真實文章
- [ ] 所有頁面 — `G-XXXXXXXXXX` → 真實 GA4 Measurement ID

---

## Deploy

```bash
# 修改內容後
git add .
git commit -m "描述這次改了什麼"
git push
# GitHub Pages 約 1–2 分鐘後自動更新
```

---

## Analytics

- **GA4**: 在 analytics.google.com 建立 property，取得 `G-XXXXXXXXXX` 後替換所有頁面的 gtag ID
- **Umami**（選用）: umami.is 註冊後取得 website ID，貼入各頁面 `</body>` 前被註解的 script tag
- 詳細說明見 `analytics-setup.md`
