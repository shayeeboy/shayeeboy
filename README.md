# My AI Portfolio

Production-grade AI systems built end-to-end — data pipelines, RAG, autonomous agents, and live web apps — shipped free-tier and verified in production. Each project below is public, deployed, and links to a working demo.

📍 Toronto-area builder · 🛠️ Node.js · PostgreSQL / Neon · pgvector · MCP · LLM orchestration · 🤖 built with Claude Code

---

## Executive Summary

| Project | What it does | Goal |
| --- | --- | --- |
| **[Enterprise RAG Assistant](https://github.com/shayeeboy/Enterprise-RAG-Assistant)** | A retrieval-augmented Q&A assistant over a piano-pedagogy knowledge base, from ingestion to a live cited-answer chat app. | Prove out a **complete, honest RAG stack** — hybrid retrieval, reranking, guardrails, LLM-as-judge evaluation, and built-in observability — running entirely on free/local infrastructure. |
| **[Financial Intelligence Strategy Agent](https://github.com/shayeeboy/Financial-Intelligence-Strategy-Agent)** | An autonomous BI agent that turns live Canadian demographic and economic data into retail-banking strategy briefs. | Show how an **agent grounded in authoritative public data** (Statistics Canada, Bank of Canada, CMHC) can produce decision-ready analysis with explicit provenance and guardrails. |
| **[AI-Native Team Diagnostic](https://github.com/shayeeboy/ai-native-diagnostic)** | A self-scoring assessment that measures how "AI-native" a team is, with a shared team view. | Deliver a **lightweight, sharable diagnostic** as a full-stack web app — from a static single-file tool to a persisted, multi-user team dashboard. |

---

## 🎹 Enterprise RAG Assistant

An AI-native, fully-cited question-answering assistant built over a piano-learning knowledge base (*Fundamentals of Piano Practice* and *Hanon: The Virtuoso Pianist*). It demonstrates a complete RAG lifecycle — not just a demo, but ingestion, retrieval, evaluation, and observability — all on free or local infrastructure with **no paid APIs**.

- **Live app:** [shayeeboy.github.io/Enterprise-RAG-Assistant](https://shayeeboy.github.io/Enterprise-RAG-Assistant/?api=https://rag-assistant-694391756200.us-central1.run.app)
- **Pipeline:** parse → chunk → embed → index, then rewrite → hybrid search (pgvector cosine + Postgres full-text, fused with RRF) → cross-encoder rerank → prompt → LLM → guardrails.
- **Stack:** Node.js · Neon Postgres + pgvector · local `mxbai-embed-large` embeddings (Transformers.js) · Groq-hosted `llama-3.3-70b` · Google Cloud Run backend · GitHub Pages frontend.
- **Trustworthiness:** citation grounding with clickable deep-links to the exact source PDF page, out-of-scope refusal, an answerability gate, and an NLI-based faithfulness filter.
- **Evaluation & observability:** an LLM-as-judge harness measuring faithfulness, correctness, and semantic Hit@5; per-request latency / token / cost tracing persisted to a searchable DB; CI-gated regression floors.

## 🏦 Financial Intelligence Strategy Agent

An autonomous business-intelligence agent that produces Canadian demographic → retail-banking strategy briefs. It pulls live public data, composes an analysis with explicit confidence levels, and can generate briefs on demand from the browser.

- **Live brief generator:** [shayeeboy.github.io/Financial-Intelligence-Strategy-Agent](https://shayeeboy.github.io/Financial-Intelligence-Strategy-Agent/)
- **Data sources (all public, no API key):** Statistics Canada WDS (debt-to-income, CPI, rents & vacancy), Bank of Canada Valet API (policy, prime & mortgage rates), CMHC housing data (via StatCan tables).
- **Architecture:** Node.js MCP server over stdio with live data adapters; a fully client-side web generator covering 13 census metro areas × demographics × banking products (42 combinations per city).
- **Guardrails:** no rate forecasts, no legal/FINTRAC advice, and thin data series explicitly flagged as low-confidence.
- **Engineering:** 17 offline acceptance tests + live integration smoke tests, CI, architecture/workflow diagrams, and a documented email-delivery path — all at **$0/mo**.

## 📊 AI-Native Team Diagnostic

A self-scoring assessment tool that helps a team gauge how "AI-native" it is, evolving across three versions from a static tool to a persisted, multi-user team dashboard.

- **Live app:** [shayeeboy.github.io/ai-native-diagnostic](https://shayeeboy.github.io/ai-native-diagnostic/)
- **v1** — static, single-file assessment · **v2** — adds local auto-save · **v3** — shared persistence via an API plus an aggregated team view.
- **Stack:** static HTML/JS frontends on GitHub Pages · Node.js/Express API on Render · Neon Postgres.
- **Full-stack:** REST API (`/api/sessions`), CORS-locked origins, health checks, and a database migration flow — verified working end-to-end.

---

<sub>All three projects are public, deployed, and were built with <a href="https://claude.com/claude-code">Claude Code</a>. Explore the repositories on <a href="https://github.com/shayeeboy">my profile</a>.</sub>
