# Vitor Plentz · @Pl3ntz

### AI Engineer — LLM systems in production · Python / FastAPI · evals, RAG, agents, cost & security

> **Open to remote AI / backend engineering roles** (LATAM / global, paid in USD) · GMT-3, overlap-friendly with US East / EU West · Santa Catarina, Brazil

I design, build and operate **LLM systems that real users depend on** — not demos. 2.5+ years shipping AI features to production: multi-tenant agent platforms, text-to-SQL, RAG pipelines, routing cascades that cut cost, and guardrails that block prompt injection before it reaches the model. I treat evals, observability and failure modes as first-class concerns, because that's what separates a production system from a prototype. Much of my production work runs under NDA — the public repos below are what I can show; sanitized case studies are available on request.

**Reach me:** [LinkedIn](https://www.linkedin.com/in/vitor-plentz)

---

## Selected work

### [quarterdeck](https://github.com/Pl3ntz/quarterdeck) · Python

> Agent orchestration for Claude Code: 28 specialist agents in 8 squads, and the guardrails that stop them from committing something wrong.

- **Routing eval 0.947 / 26/26** — measured, reproducible, honest about its limits; every number in the README links to how it's produced.
- **Hierarchy as an invariant** — agents never act on their own; an orchestrator dispatches and synthesizes, keeping a multi-agent system debuggable instead of emergent.
- **Zone assignment before parallel writes** — write-capable agents get explicit file ownership so no two touch the same file in one wave; read-only reviewers always parallelize.
- **Gates on commit** — review, eval, suite, test; each keys on a hash, so a stale check stops counting. 60 guardrail checks, no model calls.

`Python` · multi-agent systems · parallel orchestration · evals · routing

---

### [llmfoundry](https://github.com/Pl3ntz/llmfoundry) · Python

> The AI engineering kit for DeepSeek — turn opencode into a team: 12 specialist agents, 30 skills, living memory, quality gates. Built for **$2.01** in LLM spend.

The most direct statement of my AI engineering philosophy, as an open-source platform:

- **Orchestration** — 12 specialist agents (research, architecture, evals, security, database, reverse engineering) routed by task, not one model doing everything.
- **Living memory** — local embeddings + recall injection, so agents persist decisions and gotchas across sessions without a cloud dependency.
- **Quality gates as plugins** — delegation guard, anti-delirium, verify guard, voice guard, publish guard: the same fail-closed discipline I apply to production LLM apps.
- **30 skills** covering prompt engineering, evals, RAG pipelines, MCP development, observability and agent safety.

`Python` · agents · evals · memory · quality gates · DeepSeek

---

### [skeg](https://github.com/Pl3ntz/skeg) · TypeScript

> An open-source proxy that repairs broken tool calls from local LLMs (Ollama, LM Studio) before they crash your session.

A hard reliability problem, solved at the protocol layer:

- **JSON repair + validation + retry with feedback** — broken function calls from small local models get fixed in-flight instead of killing the agent loop.
- **Fallback chain** — when a call can't be repaired, the proxy degrades gracefully instead of failing hard.
- **Test-driven** — 59 tests pinning the repair behavior; works with Claude Code, OpenCode and Open WebUI.

`TypeScript` · LLM tool calling · JSON repair · reliability · local models

---

### [forja](https://github.com/Pl3ntz/forja) · TypeScript

> A CV-builder SaaS in production: live preview, LaTeX → PDF export, no local toolchain, no vendor lock-in.

- **Applied AI** — CV parsing, ATS scoring and translation via Groq / Llama 3.3 70B, with a 24h TTL cache on scores to cut redundant API calls.
- **End-to-end auth & security** — Better Auth, DB-backed sessions, rate limiting, httpOnly cookies, Zod validation, parameterized queries through Drizzle ORM.
- **LaTeX pipeline under concurrency control** — Tectonic (XeTeX) with a configurable `PDF_CONCURRENCY` cap; LaTeX-escaping closes off template injection.

`Hono` · `React` · `Vite` · `Better Auth` · `Drizzle ORM` · `PostgreSQL` · `Tectonic`

---

## Systems & low-level

The same production discipline applied to native code — proof of range beyond LLM.

### [orelhao](https://github.com/Pl3ntz/orelhao) · Swift / Objective-C++
A native macOS SIP softphone — *"the MicroSIP of the Mac."* PJSIP 2.17 engine bridged through Objective-C++ into SwiftUI; threading discipline over GCD + pjlib; UI driven by a frozen `SIPEngine` protocol with a fake engine for tests. README documents hard-won gotchas: port 5060 self-answering, INVITEs over 1300 bytes silently dropping to TCP (RFC 3261 §18.1.1), UDP undelivered under Docker Desktop.

### [OpenSharkMacOS](https://github.com/Pl3ntz/OpenSharkMacOS) · Swift
A macOS configurator for the Attack Shark R1 mouse, built on a **reverse-engineered HID protocol** documented from scratch (`docs/PROTOCOL.md`). Feature-report encoding locked down by golden-vector codec tests; no third-party software at runtime.

---

## Stack

**AI / LLM** — Python · FastAPI · Groq / Llama · agents (Claude Code) · RAG · evals · prompt-injection defense · cost optimization
**Backend** — Python · FastAPI · PostgreSQL · SQLite · outbox patterns · rate limiting
**Web** — TypeScript · Hono · React · Vite · Node · Drizzle ORM
**Systems** — Swift · Objective-C++ · IOKit · SwiftUI · HID / SIP protocols

---

**Open to remote AI / backend engineering roles, LATAM or global — paid in USD.**
The fastest way to reach me is [LinkedIn](https://www.linkedin.com/in/vitor-plentz)
