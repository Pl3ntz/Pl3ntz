# Vitor Plentz · @Pl3ntz

### AI Engineer · AI Platform Engineer · Forward Deployed Engineer

> Open to remote AI / backend engineering roles, LATAM or global, paid in USD. GMT-3, with overlap-friendly hours for US East and EU West. Santa Catarina, Brazil.

I build and operate production AI systems end to end, from architecture and infrastructure through delivery and reliability. As founding and sole engineer at Aliança, I took a multi-tenant logistics platform from zero to paying clients; it now serves 445 users across 12 tenants on a roughly 60M-row PostgreSQL backbone.

My focus is reliable LLM systems: RAG and text-to-SQL agents, evaluation, AI safety, multi-tenant isolation, event-driven pipelines, and provider resilience. My primary stack is Python, FastAPI, PostgreSQL, Redis, React, and TypeScript.

My repositories are private, and much of the production work runs under NDA. The write-ups below describe systems I built and operate. Sanitized case studies, code walkthroughs and repo access are available on request.

**Reach me:** [LinkedIn](https://www.linkedin.com/in/vitor-plentz) · [Portfolio](https://vitorplentz.com.br)

## Agent harnesses

These are the engineering harnesses I use to make AI-assisted work bounded, observable and reproducible.

### Keystone · Codex-native

A zero-runtime-dependency harness for disciplined Codex work. Sol owns investigation and decisions; bounded executors perform repository and specialist work. It routes capabilities, uses isolated worktrees, enforces RED/GREEN gates and PR-only delivery, and maintains durable context and security boundaries with measurable token budgets.

`Python` · Codex · orchestration · worktrees · quality gates · security · token efficiency

### quarterdeck · Claude Code

Agent orchestration for Claude Code: 28 specialist agents in 8 squads, with traceable routing evals and guardrails that stop agents from committing something wrong. Write-capable agents have explicit file ownership; commits pass review, eval, suite and test gates.

`Python` · multi-agent systems · parallel orchestration · evals · routing

### llmfoundry · OpenCode

An AI engineering kit that turns OpenCode into a team: 12 specialist agents, 30 skills, local living memory and quality gates. It covers prompt engineering, evals, RAG pipelines, MCP development, observability and agent safety.

`Python` · agents · evals · memory · quality gates

## Production AI systems

### Aliança · Multi-tenant logistics / AI

As founding and sole engineer, I built and operate the platform end to end: 445 users across 12 tenants on a roughly 60M-row PostgreSQL backbone. Its AI and reliability layer includes a 3-tier NLU cascade, Whisper transcription, provider failover, spend budgets, rate limits, prompt-injection defense, structured-output validation, and a confidence boundary that prevents the model from overriding verified data. The platform uses a transactional outbox instrumented with 25 Prometheus metrics; I am also building a schema-RAG text-to-SQL agent with a sqlglot AST guard.

## LLM reliability tooling

### skeg · TypeScript

A proxy that repairs broken tool calls from local LLMs (Ollama, LM Studio) before they crash an agent loop. It performs JSON repair, validation and retry with feedback, with 59 tests pinning the repair behavior. Works with Claude Code, OpenCode and Open WebUI.

`TypeScript` · LLM tool calling · JSON repair · reliability · local models

## Products in production

### [AI Job Matcher](https://usematcher.com) · live in production

A browse-first remote tech job board that aggregates public sources into a deduplicated pool, with dynamic role, currency and engagement-scope filters and optional CV-fit ranking.

`FastAPI` · `SQLite` · `vanilla JavaScript` · job matching

### [Forja](https://forja.vitorplentz.com.br) · live in production

An AI-assisted CV builder with live preview, ATS analysis, PT/EN translation and LaTeX PDF export. CV parsing, ATS scoring and translation run on Groq / Llama 3.3 70B; the product also uses Better Auth, DB-backed sessions, rate limiting, Zod validation, Drizzle ORM and PostgreSQL.

`Hono` · `React` · `Vite` · `Better Auth` · `Drizzle ORM` · `PostgreSQL` · `Tectonic`

## Systems & low-level

### orelhao · Swift / Objective-C++

A native macOS SIP softphone using PJSIP bridged through Objective-C++ into SwiftUI, with a frozen engine protocol and a fake engine for tests.

### OpenSharkMacOS · Swift

A macOS configurator for the Attack Shark R1 mouse, built on a reverse-engineered HID protocol with golden-vector codec tests.

## Stack

- **AI / LLM** · Python · FastAPI · Groq / Llama · OpenAI · Anthropic · Whisper · RAG · schema retrieval · text-to-SQL · tool calling · MCP · evals · guardrails
- **Backend** · PostgreSQL · Redis · SQLAlchemy · Alembic · asyncpg · transactional outbox · RabbitMQ · rate limiting
- **Web** · TypeScript · Hono · React · Vite · Node · Drizzle ORM
- **Infrastructure** · Docker · Linux · Cloudflare Tunnel · Caddy · CI/CD · Prometheus · Graylog
- **Languages** · English (B2) · Portuguese (Native)

---

Open to remote AI and backend engineering roles, LATAM or global, paid in USD. [LinkedIn](https://www.linkedin.com/in/vitor-plentz) · [Portfolio](https://vitorplentz.com.br)
