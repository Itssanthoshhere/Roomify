<div align="center">
  <br />
    <a href="" target="_blank">
      <img src="public/readme/readme-hero.webp" alt="Project Banner">
    </a>
  <br />

  <div>
<img src="https://img.shields.io/badge/-React-61DAFB?style=for-the-badge&logo=React&logoColor=black" />
<img src="https://img.shields.io/badge/-Typescript-3178C6?style=for-the-badge&logo=Typescript&logoColor=white" />
<img src="https://img.shields.io/badge/-Tailwind-06B6D4?style=for-the-badge&logo=Tailwind-CSS&logoColor=white" />
<img src="https://img.shields.io/badge/-Puter-A855F7?style=for-the-badge&logo=Puter&logoColor=white" /><br/>
<img src="https://img.shields.io/badge/-Claude-D97757?style=for-the-badge&logo=Anthropic&logoColor=white" />
<img src="https://img.shields.io/badge/-Gemini-4285F4?style=for-the-badge&logo=Google-Gemini&logoColor=white" />
<img src="https://img.shields.io/badge/-CodeRabbit-FF6600?style=for-the-badge&logo=CodeRabbit&logoColor=white" />

  </div>

  <h3 align="center">Roomify | AI-powered Architectural Visualization App</h3>

<p>🧠 AI Rendering &nbsp;|&nbsp; 🏗️ Architecture &nbsp;|&nbsp; ☁️ Serverless SaaS</p>

  <div align="center">
   <a href="https://puter.com/app/roomify-or-ai-architectural-visualization" target="_blank"> <img src="https://img.shields.io/badge/🌐%20Open%20on%20Puter-7C3AED?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Puter Demo"/> 
   </a> <a href="https://roomify-ai-architectural-visualization.vercel.app/" target="_blank"> <img src="https://img.shields.io/badge/🚀%20View%20on%20Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Vercel Demo"/> </a> </div>
</div>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Quick Start](#-quick-start)
- [Environment Variables](#-environment-variables)
- [API Reference](#-api-reference)
- [Deployment](#-deployment)
- [Roadmap](#-roadmap)

---

## 🎯 Overview

**Roomify** is an AI-first architectural visualization platform that transforms 2D floor plans into **photorealistic 3D renders in seconds**.

It eliminates the slow and complex traditional workflow of manual 3D modeling by enabling:

```

Upload floor plan
↓
AI generates 3D render
↓
Compare before & after
↓
Save + export project

```

### 💡 Real-world use case

A designer uploads a rough floor plan and instantly generates a realistic preview to present ideas to clients — without needing tools like SketchUp or Blender.

---

## ✨ Features

| Feature                              | Status |
| ------------------------------------ | ------ |
| 2D → 3D AI Rendering                 | ✅     |
| Before/After Comparison Slider       | ✅     |
| Project History (Persistent Storage) | ✅     |
| Image Hosting with Public URLs       | ✅     |
| Export Rendered Images               | ✅     |
| Authentication (Puter)               | ✅     |
| Serverless Backend (Workers + KV)    | ✅     |
| Real-time Rendering Feedback UI      | ✅     |
| Share Projects                       | 🔜     |
| Public Community Feed                | 🔜     |

---

## ⚙️ Tech Stack

### Frontend

| Layer         | Tech                      |
| ------------- | ------------------------- |
| Framework     | React 19 + React Router 7 |
| Language      | TypeScript                |
| Styling       | Tailwind CSS 4            |
| UI Icons      | Lucide React              |
| Image Compare | react-compare-slider      |

### Backend (Serverless)

| Layer        | Tech                     |
| ------------ | ------------------------ |
| Platform     | Puter                    |
| Storage      | Puter KV (Key-Value DB)  |
| File Hosting | Puter File System        |
| Workers      | Puter Serverless Workers |

### AI

| Provider | Model                          |
| -------- | ------------------------------ |
| Gemini   | gemini-2.5-flash-image-preview |
| Claude   | Prompt engineering support     |

---

## 🏗️ Architecture

```

Frontend (React + Vite)
│
│ puter.js SDK
▼
┌──────────────────────────────┐
│ PUTER PLATFORM │
├──────────────────────────────┤
│ Auth → puter.auth │
│ Storage → puter.kv │
│ File Hosting → puter.fs │
│ AI Models → puter.ai │
│ Workers API → REST routes │
└──────────────┬───────────────┘
│
▼
AI Image Generation

```

---

## 🔄 Data Flow

```

Upload Image
↓
Convert to Base64
↓
Upload to Hosted Storage
↓
Save metadata in KV (project)
↓
Call AI (txt2img)
↓
Store rendered image
↓
Update project

```

---

## 📂 Project Structure

```

roomify/
├── app/
│ ├── routes/
│ │ ├── home.tsx
│ │ └── visualizer.$id.tsx
│ ├── root.tsx
│
├── components/
│ ├── Navbar.tsx
│ ├── Upload.tsx
│ └── ui/
│ └── Button.tsx
│
├── lib/
│ ├── ai.action.ts # AI rendering logic
│ ├── puter.action.ts # API wrapper
│ ├── puter.worker.js # backend routes
│ ├── puter.hosting.ts # file hosting logic
│ └── utils.ts # helpers
│
├── public/
├── .env.local
└── package.json

```

---

## 🚀 Quick Start

### Prerequisites

- Node.js (v18+)
- npm
- Puter account

---

### 1. Clone Repository

```bash
git clone https://github.com/Itssanthoshhere/Roomify
cd Roomify
```

---

### 2. Install Dependencies

```bash
npm install
```

---

### 3. Setup Environment Variables

Create `.env.local`

```env
VITE_PUTER_WORKER_URL=https://your-worker-url.puter.work
```

---

### 4. Run Development Server

```bash
npm run dev
```

Open:

```
http://localhost:3000
```

---

## 🔑 Environment Variables

| Variable              | Description                  |
| --------------------- | ---------------------------- |
| VITE_PUTER_WORKER_URL | URL of your Puter worker API |

---

## 📡 API Reference

### Save Project

```
POST /api/projects/save
```

### Get All Projects

```
GET /api/projects/list
```

### Get Project by ID

```
GET /api/projects/get?id=PROJECT_ID
```

---

## 📦 Deployment

### Web

```bash
npm run build
```

Deploy to:

- Vercel
- Netlify

---

### Puter Worker

- Deploy via Puter dashboard
- Attach KV + hosting permissions

---

### Live Demo

- [https://puter.com/app/roomify-or-ai-architectural-visualization](https://puter.com/app/roomify-or-ai-architectural-visualization)
- [https://roomify-ai-architectural-visualization.vercel.app/](https://roomify-ai-architectural-visualization.vercel.app/)

---

## 🗺️ Roadmap

- [ ] Project sharing (public/private toggle)
- [ ] Community feed
- [ ] Style presets (Modern, Minimal, Luxury)
- [ ] AI prompt customization
- [ ] Pagination for project history
- [ ] Async rendering queue
- [ ] Performance optimization (image compression)
- [ ] Mobile responsiveness improvements

---

## 🔐 Security

| Feature                      | Status              |
| ---------------------------- | ------------------- |
| Authentication               | ✅                  |
| User-based project isolation | ⚠️ Improve          |
| CORS handling                | ⚠️ Needs refinement |
| Input validation             | ⚠️ Basic            |
| Rate limiting                | ❌ Planned          |

---

## 🤝 Contributing

1. Fork repo
2. Create branch → `feature/your-feature`
3. Commit → `git commit -m "feat: add feature"`
4. Push → `git push`
5. Open PR

---

## 👤 Author

**Santhosh VS**

- GitHub: [https://github.com/Itssanthoshhere](https://github.com/Itssanthoshhere)
- LinkedIn: [https://www.linkedin.com/in/thesanthoshvs/](https://www.linkedin.com/in/thesanthoshvs/)

---

<div align="center">

**Built with ❤️ using React, TypeScript, and AI**

⭐ Star this repo if you found it useful!

</div>

---
