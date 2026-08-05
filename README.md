# Vitor Plentz · @Pl3ntz

### AI Engineer · LLM systems in production · Python / FastAPI · evals, RAG, agents

> Open to remote AI / backend engineering roles, LATAM or global, paid in USD. GMT-3, with overlap-friendly hours for US East and EU West. Santa Catarina, Brazil.

I design, build and operate LLM systems that real users depend on. Not demos. For over two years I have been shipping AI features to production: multi-tenant agent platforms, text-to-SQL, RAG pipelines, routing cascades that cut cost, and guardrails that block prompt injection before it reaches the model. Evals, observability and failure modes are first-class concerns here. That is what separates a production system from a prototype.

Much of my production work runs under NDA. The public repos below are what I can show. Sanitized case studies are available on request.

**Reach me:** [LinkedIn](https://www.linkedin.com/in/vitor-plentz)

---

## Selected work

### [quarterdeck](https://github.com/Pl3ntz/quarterdeck) · Python

> Agent orchestration for Claude Code. 28 specialist agents in 8 squads, with guardrails that stop them from committing something wrong.

The routing eval sits at 0.947 across 26 runs. Measured, reproducible, and honest about its own limits. Every number in the README links to how it is produced.

- Agents never act on their own. An orchestrator dispatches and synthesizes. That keeps a multi-agent system debuggable instead of emergent.
- Write-capable agents get explicit file ownership so no two touch the same file in one wave. Read-only reviewers always parallelize.
- Commits pass review, eval, suite and test. Each gate keys on a hash, so a stale check stops counting. 60 guardrail checks, zero model calls.

`Python` · multi-agent systems · parallel orchestration · evals · routing

---

### [llmfoundry](https://github.com/Pl3ntz/llmfoundry) · Python

> The AI engineering kit for DeepSeek. It turns opencode into a team: 12 specialist agents, 30 skills, living memory, quality gates. Built for $2.01 in total LLM spend.

This is the kit I use to ship AI features. Published so others can run the same stack.

- 12 specialist agents (research, architecture, evals, security, database, reverse engineering) routed by task. One model doing everything is not the pattern here.
- Living memory with local embeddings and recall injection. Agents persist decisions and gotchas across sessions without a cloud dependency.
- Quality gates shipped as plugins: delegation guard, anti-delirium, verify guard, voice guard, publish guard. The same fail-closed discipline I apply to production LLM apps.
- 30 skills covering prompt engineering, evals, RAG pipelines, MCP development, observability and agent safety.

`Python` · agents · evals · memory · quality gates · DeepSeek

---

### [skeg](https://github.com/Pl3ntz/skeg) · TypeScript

> An open-source proxy that repairs broken tool calls from local LLMs (Ollama, LM Studio) before they crash your session.

A hard reliability problem, solved at the protocol layer.

- Broken function calls from small local models get repaired in-flight instead of killing the agent loop. JSON repair, validation, and retry with feedback.
- When a call cannot be repaired, the proxy degrades gracefully. It does not fail hard.
- 59 tests pin the repair behavior. Works with Claude Code, OpenCode and Open WebUI.

`TypeScript` · LLM tool calling · JSON repair · reliability · local models

---

### [forja](https://github.com/Pl3ntz/forja) · TypeScript

> A CV-builder SaaS in production. Live preview, LaTeX to PDF export, no local toolchain, no vendor lock-in.

- CV parsing, ATS scoring and translation run on Groq / Llama 3.3 70B, with a 24h TTL cache on scores so redundant API calls never happen.
- Better Auth, DB-backed sessions, rate limiting, httpOnly cookies, Zod validation, parameterized queries through Drizzle ORM.
- The LaTeX pipeline compiles with Tectonic (XeTeX) under a configurable `PDF_CONCURRENCY` cap. LaTeX-escaping closes off template injection.

`Hono` · `React` · `Vite` · `Better Auth` · `Drizzle ORM` · `PostgreSQL` · `Tectonic`

---

## Systems & low-level

The same production discipline, applied to native code. Proof of range beyond LLM.

### [orelhao](https://github.com/Pl3ntz/orelhao) · Swift / Objective-C++
A native macOS SIP softphone. The MicroSIP of the Mac. PJSIP 2.17 engine bridged through Objective-C++ into SwiftUI, threading discipline over GCD and pjlib, and a UI driven by a frozen `SIPEngine` protocol with a fake engine for tests. The README documents the hard-won gotchas: port 5060 self-answering, INVITEs over 1300 bytes silently dropping to TCP (RFC 3261 §18.1.1), UDP undelivered under Docker Desktop.

### [OpenSharkMacOS](https://github.com/Pl3ntz/OpenSharkMacOS) · Swift
A macOS configurator for the Attack Shark R1 mouse, built on a reverse-engineered HID protocol documented from scratch in `docs/PROTOCOL.md`. Feature-report encoding is locked down by golden-vector codec tests. No third-party software at runtime.

---

## Stack

**AI / LLM** · Python · FastAPI · Groq / Llama · agents (Claude Code) · RAG · evals · prompt-injection defense · cost optimization
**Backend** · Python · FastAPI · PostgreSQL · SQLite · outbox patterns · rate limiting
**Web** · TypeScript · Hono · React · Vite · Node · Drizzle ORM
**Systems** · Swift · Objective-C++ · IOKit · SwiftUI · HID / SIP protocols

---

Open to remote AI and backend engineering roles, LATAM or global, paid in USD. The fastest way to reach me is [LinkedIn](https://www.linkedin.com/in/vitor-plentz).
