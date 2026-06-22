<div align="center">

# LLM Zoomcamp — Learning Journey

### A hands-on, end-to-end path through building production-grade LLM applications

Building, breaking, and rebuilding real Retrieval-Augmented Generation (RAG) and
agentic systems — one module at a time. This repository is my public engineering
log as I work through [DataTalksClub's LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp).

![Python](https://img.shields.io/badge/Python-3.12+-3776AB?logo=python&logoColor=white)
![LLM](https://img.shields.io/badge/LLM-RAG_&_Agents-8A2BE2?logo=openai&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-API-412991?logo=openai&logoColor=white)
![uv](https://img.shields.io/badge/uv-Package_Manager-DE5FE9)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-In_Progress-2EA44F)

> **Last updated:** Week 1 — Agentic RAG · June 2026

</div>

---

## Why this repo exists

This isn't a collection of copy-pasted tutorials. Each module is implemented
**from scratch first**, then hardened with clean architecture, persistence, and
real LLM APIs. The goal is to demonstrate applied engineering judgment — not
just that something runs, but *why* it's built a certain way.

For recruiters and hiring managers: this README is the map. Scroll to the
[**Roadmap**](#-roadmap) to see where I am, and to
[**What I'm learning**](#-what-im-learning) to see which production skills each
module demonstrates.

---

## 🗺 Roadmap

The camp spans seven modules. I update this table every week as I ship.

| # | Module | Focus | Status | Artifacts |
|:-:|----------------|---------------------------------------------|:------:|:---------:|
| 1 | **Agentic RAG** | Keyword search, prompt building, LLM calls, persistence, function calling, agentic loop | ✅ | [`01-agentic-rag`](./01-agentic-rag) |
| 2 | **Vector Search** | Embeddings, semantic search, ANN, hybrid retrieval | 🔜 Next | — |
| 3 | **Orchestration** | Workflows, chaining, state management | ⏳ Planned | — |
| 4 | **Evaluation** | Retrieval + answer quality, LLM-as-a-judge | ⏳ Planned | — |
| 5 | **Monitoring** | Tracing, drift, production observability | ⏳ Planned | — |
| 6 | **Best Practices** | Production hardening, cost & latency | ⏳ Planned | — |
| 7 | **Project Example** | Capstone — end-to-end system | ⏳ Planned | — |

<details>
<summary><b>Legend</b></summary>

- ✅ **Completed** — implemented, tested, and documented
- 🚧 **In Progress** — actively being built this week
- 🔜 **Next** — up next in the queue
- ⏳ **Planned** — on the roadmap

</details>

---

## ✅ Module 1 — Agentic RAG

Built a RAG assistant from the ground up and evolved it into an agentic system
that decides for itself when to search, call tools, and stop.

### What was built

- **Data ingestion** — fetched and indexed course FAQ data with `minsearch`,
  including de-duplication keys so records aren't re-imported.
  [`ingest.py`](./01-agentic-rag/src/agentic_rag/ingest.py)
- **RAG helper** — a clean, extensible `RAGBase` class separating search,
  context-building, prompt construction, and the LLM call. Subclassed
  (`LessonRAG`) to adapt to a different document schema without rewriting the
  pipeline. [`rag_helper.py`](./01-agentic-rag/src/agentic_rag/rag_helper.py)
- **Token visibility** — refactored the helper to surface `usage` data so prompt
  size can be measured and optimized, not just the answer.
- **Persistence** — moved from in-memory search to a `sqlitesearch`-backed index
  so the knowledge base survives restarts.
- **Function calling & agentic loop** — turned the linear RAG flow into an agent
  that iteratively calls tools until it reaches a stopping condition.
- **Framework exploration** — implemented the same patterns with `toyaiku` and
  compared approaches.

### Key concepts applied

`prompt engineering` · `retrieval-augmented generation` · `keyword search & boosting`
· `clean / extensible class design` · `LLM usage tracking` · `SQLite persistence`
· `function calling` · `agentic loop` · `tool use`

---

## 🧠 What I'm learning

Mapped to the skills the industry actually hires for:

| Skill area | Demonstrated in |
|------------|-----------------|
| Retrieval-Augmented Generation (RAG) | Module 1 |
| Prompt engineering & instruction design | Module 1 |
| Agentic systems & function calling | Module 1 |
| Clean, extensible architecture | Module 1 |
| Vector search & embeddings | Module 2 |
| Workflow orchestration | Module 3 |
| LLM evaluation (LLM-as-a-judge) | Module 4 |
| LLM observability & monitoring | Module 5 |
| Production best practices | Module 6 |

---

## 🛠 Tech stack

| Layer | Tools |
|-------|-------|
| Language | Python 3.12+ |
| Package manager | [`uv`](https://docs.astral.sh/uv/) |
| LLM provider | OpenAI API |
| Search / retrieval | `minsearch`, `sqlitesearch`, `sentence-transformers` |
| Notebooks | Jupyter |
| Persistence | SQLite (Postgres-ready via `psycopg`) |

---

## 📂 Repository structure

```
.
├── 01-agentic-rag/
│   ├── lessons/            # Module lesson notes (reference)
│   ├── notebooks/          # Exploratory & implementation notebooks
│   ├── homework/           # Module assignments
│   ├── src/agentic_rag/    # Reusable RAG package
│   │   ├── ingest.py       #   data loading + index building
│   │   └── rag_helper.py   #   RAG + agentic core
│   ├── pyproject.toml      # uv / hatch project config
│   └── uv.lock
├── 02-vector-search/       # 🔜 Next module
└── README.md
```

---

## 🚀 Run it locally

> Requires [uv](https://docs.astral.sh/uv/) and Python 3.12+.

```bash
# from any module directory, e.g. the first one
cd 01-agentic-rag
uv sync                     # install dependencies from uv.lock

# set your OpenAI key
cp .env.example .env        # then edit .env with your key

# open the notebooks to follow along
uv run jupyter lab
```

---

## 📈 Weekly update log

| Week | Module | Highlights |
|:----:|:-------|------------|
| 1 | Agentic RAG | RAG from scratch, SQLite persistence, function calling, agentic loop |

---

## 📫 Connect

Built and maintained by **Jhon Jairo Realpe**.

- 🔗 LinkedIn: https://www.linkedin.com/in/jhonjairorealpe/
- 🐙 GitHub: https://github.com/jhontd03
- ✉️ Email: jhonjarealpe@gmail.com

---

<div align="center">

<sub>Part of the [LLM Zoomcamp](https://github.com/DataTalksClub/llm-zoomcamp) by DataTalksClub.</sub>

</div>
