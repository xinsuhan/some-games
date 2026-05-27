# Personal Website

This is Xin Suhan's personal website for sharing a learning journey, skills, academic highlights, project practice, and a small collection of browser games. It reflects my interests as a CS / AI undergraduate student (个人主页).

The site now also includes an AI Q&A Assistant that can answer questions about the website, projects, and learning content.

Website: https://xinsuhan.top

## Highlights
- Bilingual homepage
- Personal introduction and skills
- Academic highlights
- MCM/ICM achievement
- Personal projects
- Browser games collection
- AI Q&A Assistant powered by a Vercel Serverless Function

## Project Structure
- index.html homepage
- api/chat.js Vercel Serverless Function for AI chat
- assets/ images and paper PDF
- 2048/
- snake/
- minesweeper/
- hextris/
- dark-room/

## Games
- /2048
- /snake
- /minesweeper
- /hextris
- /dark-room

## Academic Highlights
- 2026 MCM/ICM Honorable Mention
- Calculus I Perfect Score, 100/100

MCM Paper PDF: Behind the Mirrorball: Vote Reconstruction

## Student Innovation Project
Project: 基于粒球表示学习的医学图像异常检测技术 / Medical Image Anomaly Detection with Granular-Ball Representation Learning

Type: 大学生创新训练计划 / Student Innovation Training Program

Tags: `Medical Image Analysis` `Anomaly Detection` `Granular-Ball Learning` `Computer Vision` `AI for Healthcare`

This student innovation project explores medical image anomaly detection based on granular-ball representation learning. It aims to improve efficiency, robustness, and interpretability in the detection, segmentation, and diagnosis pipeline by using adaptive granular-ball representation, graph construction, and neural network models.

本项目面向医学图像异常检测任务，探索基于粒球表示学习的高效、鲁棒、可解释的异常检测方法，尝试通过自适应粒球表示、图结构建模和神经网络模型提升检测、分割与辅助诊断流程的效率、鲁棒性与可解释性。

[View Redacted Proposal](assets/dachuang-proposal-redacted.pdf)

## AI Q&A Assistant
- The frontend chat box is located between the Projects & Games section and the Contact section.
- When a user submits a question, the frontend sends a request to `/api/chat`.
- `/api/chat` is implemented as a Vercel Serverless Function.
- The backend calls the DeepSeek API.
- The default model is `deepseek-v4-flash`.
- The API key is read from the `DEEPSEEK_API_KEY` environment variable and is never exposed to frontend JavaScript.

## Environment Variables
Create a local environment file with:

```env
DEEPSEEK_API_KEY=your_deepseek_api_key_here
```

## Local Development
1. Install the Vercel CLI:

```bash
npm i -g vercel
```

2. Create `.env.local`.
3. Add `DEEPSEEK_API_KEY`.
4. Start the local Vercel dev server:

```bash
vercel dev
```

5. Visit:

```text
http://localhost:3000
```

## Deployment
- Custom domain: xinsuhan.top
- Recommended deployment: Vercel.
- GitHub Pages can host static pages only. It cannot run backend endpoints such as `/api/chat`.
- To use the AI Q&A Assistant, deploy to Vercel or another platform that supports Serverless Functions or backend APIs.
- In Vercel, add `DEEPSEEK_API_KEY` under Project Settings -> Environment Variables.
- Redeploy the project after changing environment variables.

## Security Notes
- Never write a real API key into README files, frontend JavaScript, GitHub commits, or screenshots.
- Keep `.env.local` in `.gitignore`.
- The frontend should never call the DeepSeek API directly.
- All AI requests should go through the `/api/chat` backend proxy.

## License / Credits
- Some games are integrated from open-source projects.
- Original LICENSE, README, and author credits are preserved inside each subproject directory.
- This repository does not claim all games are my original work.
