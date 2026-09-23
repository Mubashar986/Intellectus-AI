# ⚗️ Master Cold-Start Genesis Summary
### Feynman Adaptive Engine (AI Tayyari Hub)
**Date:** 2026-09-23 | **Protocol:** Heisenberg OS Stage 0 Greenfield Genesis

---

## 1. What We Have Done So Far

1. **Environmental Verification & Guard Boot:**
   - Ran `scripts/heisenberg_guard.py validate --workspace .` (`VALID: true`, mode: `guarded`).
   - Inspected repository baseline: Greenfield project, zero legacy code, Git on `main`.
2. **Visual & Master Prompt Deconstruction:**
   - Thoroughly deconstructed the 4 uploaded blueprints in `Image/`:
     - `3rdImage.jpeg`: Landing Dashboard & Course Template Grid.
     - `3rd.jpeg`: Mobile-first responsive conversational workspace & widget stream.
     - `2ndImage.jpeg`: The 30–40 past paper resource dilemma & RAG vs context trade-off.
     - `WhatsApp Image`: Single-template prompt execution & bottom progress modal.
   - Fully analyzed the **LAT Master Execution Prompt** (the 10-stage Feynman learning cycle).
3. **The 100-Question Grilling Battery:**
   - Structured 100 targeted questions across 5 core engineering domains (20 questions each).
   - Saved and tracked across dedicated artifacts under `.heisenberg/genesis/`.
4. **Live Web Research & Narrsistic Pluto Architectural Evaluations:**
   - **Qdrant Past-Paper Ingestion:** Structure-aware atomic MCQ chunking + Anthropic Contextual Retrieval prepending + payload separation.
   - **Configuration:** `pydantic-settings` + `.env` Twelve-Factor App compliance (type safety, fail-fast boot, `SecretStr` masking).
   - **Telemetry:** OpenTelemetry GenAI Semantic Conventions with Arize Phoenix (single Docker container) for zero-lock-in tracing.

---

## 2. What Has Been Proposed & What is 100% CLEAR / LOCKED

### 🤖 A. AI Integrations & Agents (Domain 1 — LOCKED)
- **Agent Topology:** Single Socratic Agent with tool-calling for MVP (quiz creation, evaluation, repair) to avoid early multi-agent overhead.
- **Resource Ingestion:** **Qdrant Vector Database** storing atomic MCQs with payload separation (answers/traps kept in metadata) and Anthropic contextual prepending.
- **Model Orchestration:** **100% Model-Agnostic** via **OpenRouter** (free tier models for testing); all credentials decoupled in `.env`.
- **Streaming Output Format:** Streaming custom delimiters / XML tags (e.g., `<quiz-batch>...</quiz-batch>`) parsed on the fly.
- **Request Router Guardrail:** Dedicated ingress router for domain classification $\to$ LAT tools vs. side chat vs. blocked query.
- **Deduplication Engine:** 3-layer pipeline (SimHash fast-filter $\to$ `all-MiniLM-L6-v2` semantic check at $0.85$ $\to$ prompt exclusion).
- **Dynamic Difficulty:** 8-step calibration pipeline for Levels 1–6.
- **Hallucination Defense:** Verified past exam questions stored with ground-truth answers in DB; LLM reserved for dynamic unseen questions.

### ⚙️ B. System Design & Infrastructure (Domain 2 — LOCKED)
- **State Machine Authority:** Agent/LLM-driven conversation loop using tools; backend provides persistence, validation, and tool execution.
- **Database Engine:** **PostgreSQL** running in Docker locally, connecting to **Neon PostgreSQL** in production.
- **Schema Migrations:** Managed via **Alembic (Python)**.
- **Transport Protocol:** **HTTP REST + SSE (Server-Sent Events)** for word-by-word streaming.
- **Asynchronous Task Queue:** **Celery + Redis** in Docker for heavy PDF parsing and essay grading jobs.
- **Configuration Management:** **`pydantic-settings`** reading from `.env` (validated via Narrsistic Pluto).
- **Telemetry & Tracing:** **OpenTelemetry GenAI Standards** reporting to **Arize Phoenix** (single Docker container).
- **Session Resumption:** State saved per topic/session; cleanly resumes where student left off.

### 👤 C. User Perspectives & Psychology (Domain 3 — LOCKED)
- **Pedagogical Persona:** Empathetic mentor, low-anxiety, encouraging, managed via system prompt.
- **Active Learning Rule:** Brief explanations ($<100$ words) followed immediately by mandatory prediction challenges.
- **Topic Flow:** When a topic is mastered, the agent starts a fresh session carrying cumulative progress forward.
- **Language Medium:** Core English with native Urdu vocabulary aids for complex terms.
- **Topic Navigation:** Students can jump topics, but the coach probes them with a diagnostic challenge before granting access.
- **Student Input Modes:** Multi-modal (type directly, paste text, or upload images of handwritten work).
- **Study Pacing:** Natural student-directed sessions (like ChatGPT), private solo journey, quick practice revisit mode.

---

## 3. What is OPEN & PENDING USER REVIEW

The following two domains are authored and waiting for your direct feedback:

### 🔌 Domain 4: Frontend Integration (`grilling_domain_4_frontend_integration.md`)
*Key Open Decisions:*
- Frontend framework: **Vite + React 19 SPA + TypeScript** vs. **Next.js 14 App Router**.
- Client state management: **Zustand** vs. Jotai vs. Redux Toolkit.
- Mobile keyboard management: `100dvh` + `window.visualViewport` auto-scroll pinning.
- Progressive Web App (PWA) installability.
- Voice input integration via browser Web Speech API.

### 🎨 Domain 5: UI/UX Perspectives (`grilling_domain_5_ui_ux_perspectives.md`)
*Key Open Decisions:*
- Aesthetic Archetype: **Swiss Minimalist** vs. **Ethereal Double-Bezel Hardware Cards** vs. **Gapless Bento**.
- Double-Bezel card architecture (nested outer/inner cards for progress and quizzes).
- Quiz option layout (full-width stacked pills with $\ge 48\text{px}$ touch targets).
- Answer reveal micro-animation (green checkmark ripple vs. red shake + trap expansion).
- Progress Header tap modal (expandable bottom-sheet syllabus tree with colored badges).
- Typography & high-contrast sunlight readability.

---

## 4. Repository Artifact Directory (Heisenberg Compliance)

All artifacts are persisted in the repository under `.heisenberg/genesis/`:
- `.heisenberg/genesis/genesis_intake.md`
- `.heisenberg/genesis/grilling_domain_1_ai_integrations.md` (LOCKED)
- `.heisenberg/genesis/grilling_domain_2_system_design.md` (LOCKED)
- `.heisenberg/genesis/grilling_domain_3_user_perspectives.md` (LOCKED)
- `.heisenberg/genesis/grilling_domain_4_frontend_integration.md` (PENDING REVIEW)
- `.heisenberg/genesis/grilling_domain_5_ui_ux_perspectives.md` (PENDING REVIEW)
- `.heisenberg/genesis/MASTER_GENESIS_SUMMARY.md`
