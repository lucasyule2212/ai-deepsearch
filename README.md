# 🧠 AI DeepSearch

> DeepSearch Chat implementation - a chat agent capable of performing deep web research to answer complex queries. Built with T3 Stack + Google Gemini.

## 📖 Overview

**AI DeepSearch** is a chat application that implements an autonomous agent loop that can search the web, analyze results, and perform multi-step reasoning to provide comprehensive, fact-checked answers.

## ✨ Key Features

- **🔍 Deep Research Agent:** detailed, multi-step research on complex topics using Serper.
- **💾 Persistent History:** Chat history is saved via PostgreSQL & Drizzle ORM.
- **⚡ Real-time Streaming:** Experience the thought process as the AI thinks and writes.
- **🔒 Authentication:** Secure user accounts via NextAuth (Discord integration).
- **🔌 Extensible:** Built on the Vercel AI SDK for easy model swapping and expansion.
- **📊 Observability:** Integrated with Langfuse for tracing and monitoring agent performance.

## 🛠️ Tech Stack

- **Framework:** [Next.js 15](https://nextjs.org/) (App Router)
- **Language:** TypeScript
- **Styling:** Tailwind CSS
- **AI/LLM:** [Google Gemini](https://ai.google.dev/) (via Vercel AI SDK)
- **Search:** [Serper](https://serper.dev/)
- **Database:** PostgreSQL (with [Drizzle ORM](https://orm.drizzle.team/))
- **Caching/Queue:** Redis
- **Auth:** [Auth.js](https://authjs.dev/) (NextAuth)
- **Observability:** [Langfuse](https://langfuse.com/)

## 🚀 Getting Started

Follow these steps to get your own instance running locally.

### Prerequisites

- Node.js 20+
- pnpm (`npm install -g pnpm`)
- Docker (optional, for running Postgres/Redis easily)

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/ai-deepsearch.git
cd ai-deepsearch
```

### 2. Install Dependencies

```bash
pnpm install
```

### 3. Environment Setup

Create a `.env` file based on the example:

```bash
cp .env.example .env
```

Fill in the required API keys in `.env`:

- `GOOGLE_GENERATIVE_AI_API_KEY`: Your Gemini API key.
- `SERPER_API_KEY`: Your Serper.dev API key for search.
- `AUTH_DISCORD_ID` & `AUTH_DISCORD_SECRET`: For Discord login (or configure another provider).
- `DATABASE_URL`: Postgres connection string.
- `REDIS_URL`: Redis connection string.

### 4. Start Infrastructure (DB & Redis)

If you have Docker installed, you can spin up the required services (assuming you have a docker-compose or just use the provided scripts/commands if available).
*Alternatively, ensure you have a local Postgres and Redis instance running and update `.env` accordingly.*

### 5. Database Migration

Push the schema to your database:

```bash
pnpm db:push
```

### 6. Run the Application

```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## 🧪 Running Evaluations

This project uses `evalite` for running evaluations against the AI model.

```bash
pnpm evals
```

## 📂 Project Structure

```
├── src/
│   ├── app/             # Next.js App Router pages
│   ├── components/      # React UI components
│   ├── server/          # Backend logic
│   │   ├── deep-research.ts  # Core research logic
│   │   ├── run-agent-loop.ts # Main agent execution loop
│   │   └── db/          # Database schema and queries
│   └── evals/           # Evaluation scripts
├── drizzle/             # Database migrations
└── public/              # Static assets
```