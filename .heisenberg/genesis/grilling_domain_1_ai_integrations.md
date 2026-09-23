# ⚗️ Grilling Domain 1: AI Integrations & Agents (LOCKED & VERIFIED)
### Feynman Adaptive Engine (AI Tayyari Hub) — Stage 0 Baseline

> [!NOTE]
> All 20 questions in this domain have been answered and calibrated with the user. Key architectural contracts, diagrams, and research findings are locked below.

---

## 1. Locked Decisions Summary

| Question | Architectural Parameter | User Decision / Specification | Status |
|---|---|---|---|
| **Q1** | **Agent Topology** | **Single Agent with Tool Calling (MVP):** One session orchestrating tasks using specialized tools (quiz creation, evaluation, etc.). | `LOCKED` |
| **Q2** | **Resource Strategy** | **Qdrant Vector Database:** Pre-extract past questions into Qdrant + generate new ones. Deep RAG design analyzed via web research. | `LOCKED` |
| **Q3** | **Output Contract** | **Option B (Streaming Custom Delimiters):** LLM streams markdown with XML tags (e.g., `<quiz-batch>...</quiz-batch>`) parsed by frontend. | `LOCKED` |
| **Q4** | **Model Selection** | **Model-Agnostic via OpenRouter:** Free OpenRouter models for testing; all model configurations decoupled in `.env`. | `LOCKED` |
| **Q5** | **Quota Defense** | **Graceful UI Card:** Display clean rate-limit warning card to the student. | `LOCKED` |
| **Q6** | **Prompt Caching** | **Enabled:** Cache LAT Master Execution Prompt and syllabus definitions. | `LOCKED` |
| **Q7** | **Temperature** | **Adaptive Temperature:** Handled programmatically per tool/task (low for quizzes, adaptive for explanations). | `LOCKED` |
| **Q8** | **Hallucination Defense**| **Hybrid Ground Truth:** Past-paper questions saved with answers in DB; LLM used only for unseen/random questions. | `LOCKED` |
| **Q9** | **Guardrails** | **Request Router:** Domain classification, injection detection, safety routing (see diagram below). | `LOCKED` |
| **Q10** | **Error Taxonomy** | Integrated with user flow; distinguishes Concept Error, Careless, Guess, etc. | `LOCKED` |
| **Q11** | **Difficulty Engine** | **8-Step Calibration Pipeline** (Levels 1–6) from explicit rules to candidate validation (see below). | `LOCKED` |
| **Q12** | **Deduplication** | **3-Layer Pipeline:** Lexical Fast-Filter $\to$ Semantic Embedding (0.85 threshold) $\to$ Prompt Exclusion. | `LOCKED` |
| **Q13** | **Persona** | Dynamic adaptation per subject. | `LOCKED` |
| **Q14** | **Essay Grading** | **Standard/Normal Evaluation:** Clean, straightforward feedback without excessive bureaucracy. | `LOCKED` |
| **Q15** | **Confusion Detection**| **Persistent Engagement:** Continue quiz with student until answered; do not advance until resolved. | `LOCKED` |
| **Q16** | **Multimodal / Vision** | **Vision Support Enabled:** User can send image responses (scanned diagrams, handwritten work). | `LOCKED` |
| **Q17** | **Chunking Technique** | **Semantic / Contextual Chunking:** (Voyage / Anthropic Contextual Retrieval methodology). | `LOCKED` |
| **Q18** | **Retrieval Spacing** | **Memory-Driven Retrieval:** AI surfaces previous topics based on session memory. | `LOCKED` |
| **Q19** | **Latency Ceiling** | **$< 3\text{ seconds}$** for interactive turns and batch deliveries. | `LOCKED` |
| **Q20** | **Knowledge Tracing** | **Context-Driven Tracing:** Managed within LLM context using remaining topic lists and conversation history. | `LOCKED` |

---

## 2. Architectural Diagrams & Pipelines (User Provided)

### A. The Request Router (Guardrail Architecture)
```text
Student Message
       │
       ▼
┌──────────────────────────┐
│ Request Router           │
│                          │
│ • Domain classification  │
│ • Injection detection    │
│ • Safety classification  │
└────────────┬─────────────┘
             │
       ┌─────┼──────┐
       │     │      │
       ▼     ▼      ▼
     LAT   Side    Block
           Chat
       │     │
       ▼     ▼
   Main LLM  Temporary LLM
       │
       │
       ▼
  LAT tools/data
```

### B. The 8-Step Dynamic Difficulty Pipeline (Levels 1–6)
```text
1. Define Levels 1–6 with explicit rules
        ↓
2. Give the LLM 2–3 good examples per level
        ↓
3. Tell the LLM the target level + difficulty attributes
        ↓
4. Generate 3–5 candidate questions
        ↓
5. Run a separate validator
        ↓
6. Pick the question that best matches the target level
        ↓
7. Record the student's result
        ↓
8. Later, use real student data to calibrate difficulty
```

### C. The 3-Layer Unseen Question Deduplication Pipeline
1. **Layer 1 (Lexical Fast-Filter):** Normalize text (lowercase, remove punctuation), compute SimHash, reject if Hamming distance $\le 3$. Cost: $0 tokens.
2. **Layer 2 (Semantic Embedding Check):** Embed candidate question with `all-MiniLM-L6-v2` (local CPU), compute cosine similarity against seen questions. Reject if similarity $> 0.85$.
3. **Layer 3 (Prompt-Based Exclusion):** Inject summarized stems of seen questions into prompt with negative instructions.
