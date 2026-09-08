# Micha Noel Donges

I build AI assistants that run on my own hardware — the kind you can unplug from the
internet and still get something out of. Both projects below exist because I wanted the
thing to exist, not because a course told me to build them.

**I am looking for an Ausbildung as Fachinformatiker — open to all four Fachrichtungen.**

---

## JARVIS — self-hosted personal AI assistant

[![tests](https://github.com/70cacao/Public-Jarvis-Project/actions/workflows/tests.yml/badge.svg)](https://github.com/70cacao/Public-Jarvis-Project/actions/workflows/tests.yml)

Node.js, runs locally on Windows. WhatsApp is the command surface, so there is no app to
install. It routes between a local model and a hosted one per message, sees the screen,
speaks and listens, and acts on its own initiative — but every automatic action can be
undone for 30 seconds after it happened.

The parts I am most pleased with are not the features:

- **A handler pipeline where the first handler to answer wins.** Adding a command does not
  mean touching the ones next to it.
- **Every automated action carries a reason.** The telemetry stream says *why* it fired,
  not just that it did — because an assistant that acts without explaining itself is one
  you stop trusting.
- **Nothing user-specific lives in the source.** Name, city, contacts, trusted senders and
  focus hours are all in `.env`. Clone it, fill in your own values, and it is your
  assistant rather than a copy of mine.

**→ [Public-Jarvis-Project](https://github.com/70cacao/Public-Jarvis-Project)** · JavaScript,
npm workspaces monorepo, SQLite, local + hosted LLMs

---

## Orynex — Windows desktop assistant

*In development. The [repository](https://github.com/70cacao/Orynex) carries the full
description; the source itself is not public.*

Rust and Tauri v2 underneath, React and TypeScript on top, talking straight to the Windows
APIs. No Python, no second runtime — one binary and an installer. It is the same idea as
JARVIS taken seriously: local-first, and you bring your own API key.

Where it stands: **816 tests green**, a written architecture, and a decision log that
records why things are the way they are.

Three decisions I would defend in an interview:

- **Every tool declares what it needs**, and the permission check happens before it runs
  rather than inside it — so a new tool cannot quietly grant itself something.
- **The app never runs as administrator.** The handful of actions that genuinely need
  admin rights go through a separate, small helper process, so the surface that is
  elevated stays small enough to read in one sitting.
- **Secrets are never in a config file or a log.** They live in the Windows Credential
  Manager, and the key never leaves the module that talks to the provider.

---

## How I work

Three habits, all of them learned by first getting it wrong:

**Architecture before code.** Both projects have written architecture and design
documents. When the code and the document disagree, the document wins and the code gets
changed — otherwise the document is decoration within a week.

**Measure instead of guessing.** A relevance threshold in Orynex looked reasonable and
let five out of five nonsense questions through. The fix was not a better number; it was
realising that no fixed number works there, and measuring on real data until a relative
threshold showed itself.

**A green test suite is not proof.** Tests catch what I already thought of. The bugs that
actually cost me time showed up when I ran the real thing and looked at the real data —
including a privacy switch that displayed the wrong state and did nothing when pressed,
sitting quietly behind hundreds of passing tests.

---

## Tech I have actually shipped with

Rust · TypeScript · JavaScript / Node.js · React · Tauri · SQLite · Windows APIs ·
local and hosted LLMs (Ollama, Groq)

## Contact

micha.noel.donges@gmail.com · micha@ceruleancircle.com
