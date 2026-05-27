# Personal Website / 个人主页

This is Xin Suhan's personal website for sharing a learning journey, skills, academic highlights, project practice, and a small collection of browser games. It reflects my interests as a CS / AI undergraduate student (个人主页).

本项目是个人主页站点，核心目标是：简单、稳定、可长期维护。

Website: https://xinsuhan.top

## 项目简介 / Overview
- Static HTML/CSS/JS homepage (no frameworks, no build step).
- AI Chat and OCR are provided by Serverless APIs (`/api/chat`, `/api/vision-ocr`).
- Multiple games (2048, Snake, Minesweeper, Hextris, A Dark Room).
- Academic assets: PDFs, certificates, images.
- Bilingual content (EN/ZH).

## 目录结构 / Structure
```
.
├─ index.html            # Homepage entry
├─ css/site.css          # Homepage styles
├─ js/site.js            # Homepage logic (i18n, AI, OCR)
├─ api/                  # Serverless APIs (Vercel)
│  ├─ chat.js
│  └─ vision-ocr.js
├─ assets/               # PDFs, certificates, images
├─ 2048/                 # 2048 game entry
├─ snake/                # Snake game
├─ minesweeper/          # Minesweeper game
├─ hextris/              # Hextris game
├─ dark-room/            # A Dark Room game
├─ games/                # Compatibility placeholder (future migration)
├─ js/                   # Legacy 2048 assets + site.js
├─ style/                # Legacy 2048 styles
└─ meta/                 # Legacy 2048 icons
```

Note: `js/`, `style/`, `meta/` are still legacy assets for 2048 until the gradual migration finishes.

## 本地预览 / Local Preview
### Static preview (no AI/OCR)
- Option A: open `index.html` directly in a browser.
- Option B (recommended): run a simple static server if available.

```bash
python -m http.server 8000
```

Visit:
```
http://localhost:8000
```

### Full preview (AI/OCR enabled)
Use Vercel Dev to run Serverless APIs locally:

```bash
npm i -g vercel
vercel dev
```

Visit:
```
http://localhost:3000
```

## 部署 / Deployment
### GitHub Pages + 自定义域名
1. Settings -> Pages -> Deploy from branch (`main`), folder `/`.
2. Ensure the `CNAME` file contains your domain (e.g. `www.xinsuhan.top`).
3. DNS:
	 - `www` -> CNAME to `<username>.github.io`
	 - Apex domain: use provider ALIAS/ANAME or A records per GitHub Pages docs.

GitHub Pages is static only, so `/api/*` will not work there.

### Vercel (AI/OCR APIs)
1. Import this repo to Vercel.
2. Framework preset: Other (no build step).
3. Add environment variables (see below).
4. Deploy.

API endpoints:
- `/api/chat` (AI chat)
- `/api/vision-ocr` (OCR)

### 混合部署（静态 + API）
- Static site on GitHub Pages / OSS / CDN.
- API on Vercel.
- Set `API_BASE` to the Vercel domain (see next section).

## API_BASE 使用说明
Default behavior: if `API_BASE` is empty, the frontend calls `/api/*` on the same origin (best for full Vercel deployment).

To call a separate API host, set one of the following:

Option A (HTML attribute):
```html
<html data-api-base="https://your-api.vercel.app">
```

Option B (global variable):
```html
<script>
	window.API_BASE = "https://your-api.vercel.app";
</script>
<script defer src="./js/site.js"></script>
```

## 环境变量 / Environment Variables
Create `.env.local` (for Vercel dev) or set in Vercel Project Settings:

```env
DEEPSEEK_API_KEY=your_deepseek_api_key_here
DASHSCOPE_API_KEY=your_dashscope_api_key_here
```

- `DEEPSEEK_API_KEY`: required for AI chat.
- `DASHSCOPE_API_KEY`: required for OCR.

## 常见问题 / FAQ
### PDF/图片/游戏 404
- Confirm the file exists under `assets/` or the game folder.
- Check case sensitivity on Linux hosts (GitHub Pages is case-sensitive).
- Ensure links are relative (`./assets/...`, `./2048/`) when using project subpaths.
- If using CDN/OSS, verify upload paths and clear cache.

## Security Notes
- Never commit real API keys.
- Keep `.env.local` out of git (already ignored).
- The frontend should never call the AI provider directly.

## License / Credits
- Some games are integrated from open-source projects.
- Original LICENSE, README, and author credits are preserved inside each subproject directory.
- This repository does not claim all games are my original work.
