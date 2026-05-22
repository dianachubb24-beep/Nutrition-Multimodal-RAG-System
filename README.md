# Nutrition RAG Pipeline

A multimodal Retrieval-Augmented Generation (RAG) system built to query a library of nutrition research papers and health articles using natural language. Designed for a nutrition counseling clinic use case.

**Group Project — ADTA/DAST 5770 | Spring 2026 | Group 2**

**Team Members:**
* Ramzy Idris
* Otto Prado
* Diana Chubb

---

## Table of Contents

- [Overview](#overview)
- [Knowledge Base](#knowledge-base)
- [Business & Technical Requirements](#business--technical-requirements)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Testing](#testing)
- [Project Files](#project-files)

---

## Overview

We are Intelligence Architects — an AI system development group contracted to create a multimodal generative AI Q&A search system for a nutrition counseling clinic. This system retrieves vetted, credible, and evidence-based information to help patients with nutritional guidance. The multimodal architecture integrates text embeddings, vector search, and language model reasoning to provide comprehensive, grounded responses. When a query falls outside the knowledge base scope, the system clearly communicates this limitation to the user.

---

## Knowledge Base

The knowledge base consists of 150 PDFs — 100 focused on nutrition and 50 covering general health topics. Documents were collected through personal research and web-crawling, then individually selected and curated for credibility and relevance to nutrition counseling.

---

## Business & Technical Requirements

The multimodal RAG system retrieves vetted, credible, and evidence-based information from the knowledge base to help patients with nutritional guidance. When a query falls outside the knowledge base scope, the system clearly communicates this limitation to the user.

**Key Performance Indicators (KPIs):**
* Usefulness and Relevance
* Retrieval Accuracy
* Clarity, Coherence, and Understanding
* Completeness and Depth
* Overall Satisfaction

---

## Architecture

The pipeline runs across two major components:

### Ingestion & Indexing Pipeline (Phases 1–6)

* **Phase 1:** PDF knowledge base uploaded to Google Cloud Storage (GCS)
* **Phase 2:** Documents ingested, parsed, and split into overlapping chunks via LangChain
* **Phase 3:** Empty Vertex AI Vector Search index created
* **Phase 4:** Matching Engine configured and vector database initialized in GCS
* **Phase 5:** LangChain instance integration initialized
* **Phase 6:** Chunks transformed into embeddings using Vertex AI `text-embedding-005`

### Retrieval & Response Loop (Phases 7–10)

* **Phase 7:** Gemini 2.5 Pro LLM object created
* **Phase 8:** LangChain RAG chain configured with prompt template
* **Phase 9:** End-to-end Q&A tested — natural language queries are embedded, matched against the vector store via Top-K similarity search, and fed to the LLM for a grounded response
* **Phase 10:** System undeployed and indexes/endpoints cleaned up

---

## Tech Stack

| Layer | Tool |
| :--- | :--- |
| Cloud Storage | Google Cloud Storage (GCS) |
| Document Loading | LangChain + GCSDirectoryLoader |
| Text Splitting | LangChain RecursiveCharacterTextSplitter |
| Embeddings | Vertex AI `text-embedding-005` (768 dimensions) |
| Vector Store | Vertex AI Vector Search (Matching Engine) |
| LLM | Gemini 2.5 Pro via Vertex AI |
| Orchestration | LangChain |
| Environment | Python, Google Colab / Jupyter |

---

## Testing

The system was validated using 10 natural language questions drawn from the nutrition knowledge base, each with a pre-verified expected answer. All 10 questions were answered correctly.

For detailed testing results and evaluation scores, refer to:
* [ADTA_5770_Testing_&_Evaluation.docx](ADTA_5770_Testing_&_Evaluation.docx)
* [ADTA_5770_responses_evaluation_scores.xlsx](ADTA_5770_responses_evaluation_scores.xlsx)

---

## Project Files

* **Generative AI Q&A-Search System_Group2.ipynb** — Main implementation notebook containing the complete multimodal RAG pipeline
* **ADTA_5770_Nutrition_RAG_System_Final_Report.docx** — Comprehensive final project report
* **ADTA_5770_Testing_&_Evaluation.docx** — Detailed testing and evaluation documentation
* **ADTA_5770_responses_evaluation_scores.xlsx** — Evaluation scores and metrics for all test queries

---

## Questions?

For more information, refer to the final project report or contact the team.
