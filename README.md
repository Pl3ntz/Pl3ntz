# Vitor Plentz · @Pl3ntz

### Software Engineer — Python/FastAPI · TypeScript · AI systems

> **Open to remote engineering roles** (LATAM / global) · GMT-3, overlap-friendly with US East / EU West · Santa Catarina, Brazil

I build backend-heavy systems that ship to production: AI agent orchestration, full-stack SaaS, and native macOS. Depth in Python backend and LLM agent systems; breadth across the stack — from a LaTeX-rendering PDF pipeline down to a reverse-engineered HID protocol. The projects below are ordered by how directly they map to a hiring need, not by recency.

**Reach me:** [LinkedIn](https://www.linkedin.com/in/vitor-plentz)

---

## Selected work

### [quarterdeck](https://github.com/Pl3ntz/quarterdeck) · Python

> An orchestration framework for AI coding agents: 26 agents across 8 squads, executed in parallel waves.

The single-agent default serializes multi-step engineering work into one bottleneck. Quarterdeck decomposes a request into **waves** — within a wave, 3–5 specialized agents run in parallel (reconnaissance, validation); waves run sequentially only when there's a true data dependency. The design rests on a few deliberate constraints:

- **Hierarchy as an invariant** — agents never act on their own; an orchestrator dispatches and synthesizes. This keeps a multi-agent system debuggable instead of emergent.
- **Zone assignment before parallel writes** — write-capable agents get explicit file ownership so no two touch the same file in one wave. Read-only reviewers (quality gates) skip this and always parallelize.
- **Deterministic routing + standardized output** — requests route to squads by signal; every agent returns the same output contract, so synthesis doesn't depend on per-agent formatting.

`Python` · multi-agent systems · parallel orchestration · routing

---

### [forja](https://github.com/Pl3ntz/forja) · TypeScript

> A CV-builder SaaS with live preview and LaTeX → PDF export — no local toolchain, no vendor lock-in.

A full-stack product running in production. The engineering load sits in three places:

- **LaTeX PDF pipeline under concurrency control** — PDFs compile with Tectonic (XeTeX) from EJS → LaTeX templates; a `p-queue` with configurable `PDF_CONCURRENCY` caps server load, and LaTeX-character escaping closes off template injection.
- **End-to-end auth & security** — Better Auth with DB-backed sessions tracking IP and User-Agent, user/admin roles, per-route fixed-window rate limiting, httpOnly cookies, Zod validation on every endpoint, and parameterized queries through Drizzle ORM.
- **Applied AI** — CV parsing, ATS scoring, and translation via Groq / Llama 3.3 70B, with a 24h in-memory TTL cache on ATS scores to cut redundant API calls.

`Hono` · `React 19` · `Vite` · `Better Auth` · `Drizzle ORM` · `PostgreSQL` · `Tectonic`

---

### [local-mind](https://github.com/Pl3ntz/local-mind) · JavaScript

> Local-first persistent memory for AI coding agents — SQLite, zero cloud, zero API keys.

A clean-room rebuild: same goal as a cloud-based predecessor, opposite architecture — local SQLite instead of a cloud API.

- **Custom relevance scoring** — ranking by `BM25 * 0.7 + Recency * 0.3`, with recency decaying as `e^(-0.15t)` (≈4.6-day half-life). Severity tunes the decay: `CRITICAL` findings persist ~35 days, `INFO` decays in ~3.5.
- **Data engineering** — a 9-table SQLite schema with FTS5 full-text search and incremental transcript capture by byte-offset (only new bytes are read).
- **Test rigor** — 18 suites / 310 tests, Biome for lint/format, esbuild for builds.

`JavaScript` · `SQLite` · `FTS5` · information retrieval

---

## Native macOS — proof of low-level range

These ship the same product instincts down to the protocol and FFI layer.

### [orelhao](https://github.com/Pl3ntz/orelhao) · Swift / Objective-C++

> A native macOS SIP softphone — *"the MicroSIP of the Mac."* Engine: PJSIP 2.17.

Low-level systems work across a three-language boundary. Three decisions carried it:

- **A clean FFI boundary** — PJSUA2 (C++) is subclassed in Objective-C++ and exposed to Swift as a pure Obj-C delegate of immutable value objects, so C++ never leaks above the bridge.
- **Threading discipline over GCD + pjlib** — one serial dispatch queue owns every PJSIP call; since GCD doesn't pin threads, each block re-registers via `pj_thread_register` before touching pjlib — the fix for intermittent asserts that only reproduce under load.
- **Testable against a frozen protocol** — the whole UI runs against a `SIPEngine` protocol; a `FakeSIPEngine` (`ORELHAO_FAKE_ENGINE=1`) made the UI buildable and demoable before the real engine existed.

The README's *hard-won gotchas* go deeper: port 5060 self-answering, INVITEs over 1300 bytes silently dropping to TCP per RFC 3261 §18.1.1, UDP undelivered under Docker Desktop with `network_mode: host`.

`Swift` · `Objective-C++` · `SwiftUI` · `PJSIP` · SIP / RTP

---

### [OpenSharkMacOS](https://github.com/Pl3ntz/OpenSharkMacOS) · Swift

> A macOS configurator for the Attack Shark R1 mouse, built on a reverse-engineered HID protocol.

The vendor ships Windows-only software; the protocol was reversed and documented from scratch (`docs/PROTOCOL.md`).

- **HID reverse engineering** — a vendor HID interface (usage page 1 / usage `0x80`, 64-byte feature reports); button remaps write via feature report `0x08`, firmware ACKs on `0x03`. Talks to the device directly over IOKit — no third-party software at runtime.
- **Layered design + golden-vector tests** — `R1Kit` holds protocol + IOKit transport with no UI (`ReportBuilder`, `HidTransport`, `ScrollInverter`); CLI and SwiftUI app consume the kit; report encoding is locked down by golden-vector codec tests.
- **An OS-level workaround for a firmware gap** — the firmware has no native scroll-invert, so per-device inversion runs macOS-side through a `CGEventTap` login agent, leaving trackpad natural scrolling untouched.

`Swift` · `IOKit` · HID protocol · reverse engineering

---

## Also public

| Project | What it is |
|---|---|
| [tributometro](https://github.com/Pl3ntz/tributometro) · TypeScript | A Brazilian tax-transparency calculator. |
| [ascii-art](https://github.com/Pl3ntz/ascii-art) | A 3D Möbius strip rendered in ASCII with Phong shading. |
| [claude-dotfiles](https://github.com/Pl3ntz/claude-dotfiles) / [claude-code-config](https://github.com/Pl3ntz/claude-code-config) | Claude Code configuration. |

---

## Stack

**Backend & AI** — Python · FastAPI · LLM agents (Claude Code) · Groq / Llama
**Web** — TypeScript · Hono · React · Vite · Node · Drizzle ORM
**Systems** — Swift · Objective-C++ · IOKit · SwiftUI
**Data** — PostgreSQL · SQLite · FTS5

---

**Open to remote engineering roles, LATAM or global — backend-heavy or full-stack.**
The fastest way to reach me is [LinkedIn](https://www.linkedin.com/in/vitor-plentz)
