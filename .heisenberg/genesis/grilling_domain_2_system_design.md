# ⚗️ Grilling Domain 2: System Design (LOCKED & VERIFIED)
### Feynman Adaptive Engine (AI Tayyari Hub) — Stage 0 Baseline

> [!NOTE]
> All 20 questions in this domain have been answered and calibrated with the user. The architecture, database engine, task queues, streaming protocols, and Narrsistic Pluto evaluations are locked below.

---

## 1. Locked Decisions Summary

| Question | Architectural Dimension | User Decision / Specification | Status |
|---|---|---|---|
| **Q1** | **State Machine Authority** | **Agent-Driven State Loop:** Progression is driven by the LLM/Agent loop via tool-calling and context; backend provides persistence and tool execution. | `LOCKED` |
| **Q2** | **Database Engine** | **Dockerized PostgreSQL + Neon Cloud:** Local dev runs PostgreSQL in Docker; live production runs on Neon PostgreSQL. | `LOCKED` |
| **Q3** | **Transport Protocol** | **HTTP REST + SSE (Server-Sent Events):** Standard REST for mutations, SSE for real-time word-by-word streaming. | `LOCKED` |
| **Q4** | **Session Interruption** | **Persistent State Resumption:** State saved per topic/session; student cleanly resumes exactly where they left off. | `LOCKED` |
| **Q5** | **Template Packaging** | **Relational Database Tables:** Stored in PostgreSQL (`courses`, `course_templates`, `topics`, `syllabus_nodes`). | `LOCKED` |
| **Q6** | **Deployment Target** | **Cloud-Hosted Web SaaS:** Mobile-first responsive web application, fully functional on desktop browsers too. | `LOCKED` |
| **Q7** | **Async Background Tasks** | **Celery + Redis (Dockerized Linux):** Background task workers running in Linux containers for heavy jobs. | `LOCKED` |
| **Q8** | **Caching Layer** | **Hybrid Client/Server Cache:** Client-side caching for quiz artifacts + Redis backend caching. | `LOCKED` |
| **Q9** | **Question Bank** | **Hybrid Repository:** Verified past exam questions served from PostgreSQL/Qdrant; unseen questions generated on-the-fly. | `LOCKED` |
| **Q10** | **Swappable LLM Seam** | **Abstract Provider Interface:** `ILLMProvider` decoupling Gemini, OpenAI, and OpenRouter via `.env`. | `LOCKED` |
| **Q11** | **Concurrency Protection**| Idempotency keys on submissions; handled per Heisenberg devcycle. | `LOCKED` |
| **Q12** | **Topic Prerequisite DAG**| **Configurable Mastery Gating:** Admin-configurable threshold (default 85%); agent automatically boots new session on topic mastery. | `LOCKED` |
| **Q13** | **Essay Storage** | **Dual Storage (DB + Workspace):** Stored in PostgreSQL and cached in workspace directory for instant access. | `LOCKED` |
| **Q14** | **Config Management** | **`pydantic-settings` + `.env`:** Twelve-Factor App compliance, validated via Narrsistic Pluto analysis. | `LOCKED` |
| **Q15** | **API Surface Topology** | **RESTful `/api/v1/...`:** Standard modular route hierarchy. | `LOCKED` |
| **Q16** | **Database Migrations** | **Alembic (Python):** Schema migrations managed via Alembic. | `LOCKED` |
| **Q17** | **Telemetry & Tracing** | **OpenTelemetry GenAI Standards:** OTel-native tracing with Arize Phoenix / Langfuse. | `LOCKED` |
| **Q18** | **Boot Time SLA** | **$< 1.5\text{ seconds}$** cold-start initialization. | `LOCKED` |
| **Q19** | **Data Portability** | **1-Click Export:** Download study logs, quiz records, and mastery cards to PDF / Docs. | `LOCKED` |
| **Q20** | **Graceful Shutdown** | Atomic database transactions per question; state preserved across process restarts. | `LOCKED` |
