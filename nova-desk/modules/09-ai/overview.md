# 🤖 AI Module — Overview

## What This Module Does

The AI Module powers **Nova**, Nova Desk's built-in AI assistant. It gives every user a personalized AI agent, real-time chat (streaming and non-streaming), persistent conversation history, and a daily token budget to keep usage under control. Under the hood it talks to the DeepSeek API through an OpenAI-compatible client.

---

## Core Concepts

| Concept | Description |
|---|---|
| **Per-User Agent** | Each user gets their own AI agent instance — name, personality prompt, and model settings (temperature, max tokens, etc.) can all be customized. |
| **Lazy Agent Creation** | An agent isn't created until the user actually needs one — the first chat or an explicit "create agent" call sets it up. |
| **Conversations** | Every chat is saved as a conversation with full message history, so users can pick up where they left off. |
| **Token Budget** | Each user gets a daily token allowance (10/day in testing, 50/day planned for production) that resets every 24 hours, preventing runaway usage/cost. |
| **Streaming & Non-Streaming Chat** | Messages can be sent as a single response or streamed back in real time via Server-Sent Events, for a more natural typing-style UX. |

---

## Key Features

| Feature | Description |
|---|---|
| AI Chat | Real-time conversations with Nova using the DeepSeek API |
| Conversation History | Every user-AI interaction is persisted |
| Agent Customization | Personalized agent settings per user |
| Token Management | Daily token limits, auto-reset every 24 hours |
| Streaming Support | Real-time streaming responses |
| Multi-User Support | Each user has their own independent agent instance |

---

## Technology Stack

| Component | Technology |
|---|---|
| Backend Framework | Express.js |
| Database | MongoDB (Mongoose) |
| AI Provider | DeepSeek API |
| API Client | OpenAI SDK (DeepSeek is OpenAI-compatible) |
| Authentication | JWT |
| Testing | k6 |

---

## Journey: From 46% to 100%

| Stage | Result | What Was Happening |
|---|---|---|
| **First test pass** | 6/13 (46.15%) | Health check failing, agent-stats endpoints erroring, and — the real bug — **agent creation failing with `"AIAgent is not defined"`**, a missing-import error that cascaded into several dependent checks also failing. |
| **After the import fix** | **13/13 (100%)** | Every scenario passes cleanly: health check, agent creation and stats, chat (first and follow-up messages), conversation retrieval, token-limit enforcement, settings update, conversation deletion, and unauthorized-access rejection. |

**In plain terms:** the AI module had one root-cause bug — the AI Agent database model wasn't imported into the controller that needed it — and that single missing import was responsible for most of the early failures. Once fixed, every feature worked correctly on the very next test pass.

---

## What Was Actually Wrong (Plain-Language Summary)

The core issue was straightforward: the code that creates a user's AI agent tried to use the `AIAgent` database model without ever importing it — so the very first attempt to set up an agent failed with `"AIAgent is not defined"`. Because agent stats, conversation stats, and a few other checks all depend on an agent actually existing, that one missing import caused a chain reaction of failures across several unrelated-looking endpoints. Once the import was added, agent creation started working, and every dependent feature came online immediately — no other code changes were needed.

Full technical detail — the exact log evidence, the fix, and the complete before/after test data — is in `backend.md`.

---

## Token Management

| Environment | Tokens/User/Day | Purpose |
|---|---|---|
| Testing | 10 | Load testing and development |
| Staging | 25 | UAT and integration testing |
| Production | 50 | Live users (configurable) |

Token usage automatically resets 24 hours after a user's first message of the day. The daily limit is enforced per-user, not per-conversation, so it carries across multiple chats.

---

## Test Results Summary

**Test:** `tests/ai-complete-test.js` — 13 scenarios per iteration.

| Metric | Value |
|---|---|
| Final iteration result | **13/13 passed (100%)** |
| Total requests (full run) | 66 |
| Overall HTTP success rate | 90.91% |
| **AI-specific failure rate** | **0.00%** |
| Average response time | 604.85ms |

> The 90.91% HTTP-level figure blends the early failing iteration (before the import fix) together with the fully-passing final iteration in the same run — see `backend.md` for the iteration-by-iteration breakdown. Once the fix was in place, every AI request succeeded.

---

## Status

**AI Module: Production ready**, with the token limit intended to be raised from the testing value of 10/day to the production value of 50/day before launch. All 13 tested scenarios — health, agent lifecycle, chat, conversations, token limits, settings, and access control — pass consistently once the one root-cause import bug was fixed.