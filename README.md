<div align="center">
  <img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:101820,35:245953,70:35a67b,100:f2c14e&height=190&section=header&text=Orito&fontSize=68&fontColor=ffffff&animation=twinkling&fontAlignY=36&desc=A%20Linux%20helper%20that%20thinks%20in%20steps.&descAlignY=58&descSize=17" alt="Orito animated header" />

  <a href="https://readme-typing-svg.demolab.com"><img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=18&pause=1100&color=F2C14E&center=true&vCenter=true&width=720&lines=Plan+the+task;Check+the+commands;Explain+what+happens" alt="Typing tagline" /></a>

  <p>
    <img src="https://img.shields.io/badge/Node.js-20%2B-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js 20+" />
    <img src="https://img.shields.io/badge/TypeScript-Fastify-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript and Fastify" />
    <img src="https://img.shields.io/badge/AI-Multi--agent-7B61FF?style=for-the-badge" alt="Multi-agent" />
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-F2C14E?style=for-the-badge" alt="MIT License" /></a>
  </p>
</div>

## 🐧 What it does

Orito is a backend for a Linux assistant. It classifies a request, gathers context, plans work, validates command safety, and returns a response through a Fastify API. This repository contains the backend; it does not include a finished desktop client.

## 🔁 Request path

```mermaid
flowchart LR
  A[Client] --> B[Fastify API]
  B --> C[Orchestrator]
  C --> D[Research and planner agents]
  D --> E[Command validator]
  E --> F[Tool registry]
  F --> G[Response and audit record]
  C --> H[LLM providers and retrieval]
```

## 🧩 Building blocks

- Specialist agents cover planning, research, validation, synthesis, and system context.
- Registered tools include web search, package lookup, man-page retrieval, calculations, and command-safety checks.
- OpenRouter and Gemini are configured as model providers; SearXNG/Tavily and Pinecone/Qdrant settings are present for search and retrieval integrations.
- Firebase authentication, JWT sessions, MongoDB persistence, WebSocket streaming, and audit logging are implemented in the backend.

Commands are proposed and validated by the application. Review any command before running it on a real machine; an assistant is not a substitute for an operator's judgment.

## 🧰 Stack

| Area | Tools |
|---|---|
| Runtime/API | Node.js 20+, TypeScript, Fastify |
| Auth | Firebase Admin, JWT |
| Data | MongoDB/Mongoose |
| Models | OpenRouter SDK, Google Gemini |
| Search/retrieval | SearXNG/Tavily, Pinecone or Qdrant configuration |
| Realtime/logging | WebSockets, Pino |

## 🚀 Run the backend

```bash
git clone https://github.com/ChristopherJoshy/Orito.git
cd orito/backend
npm ci
cp .env.example .env
npm run dev
```

On Windows PowerShell, copy the example with `Copy-Item .env.example .env`. Fill in only the providers you intend to use. MongoDB is required for persistence; the optional integrations need their own services and credentials.

Useful scripts:

```bash
npm run build
npm test
```

## 🗂️ Layout

```text
backend/src/agents/   orchestration and specialist agents
backend/src/tools/    registered tool implementations
backend/src/routes/   HTTP and WebSocket endpoints
backend/src/models/   persisted domain models
```

## 📄 License

MIT. See [`LICENSE`](LICENSE).

## ⚠️ Notes

The repository is backend-only. Provider credentials, Firebase service-account files, and production infrastructure are not included.