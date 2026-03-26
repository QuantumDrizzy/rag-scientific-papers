# 🤖 Scientific Paper Q&A — RAG Pipeline
## IBM Generative AI & RAG Agents Certificate — Capstone Project

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://python.org)
[![IBM](https://img.shields.io/badge/IBM-Generative%20AI-054ADA)](https://www.ibm.com)
[![FAISS](https://img.shields.io/badge/FAISS-Vector%20Store-purple)](https://faiss.ai)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## Overview

End-to-end RAG (Retrieval-Augmented Generation) pipeline for querying a corpus of 30 seminal AI/ML research papers. Includes document ingestion, embedding pipeline, FAISS vector store, semantic retrieval, prompt engineering, and a ReAct-style agent with tool use.

**Pipeline:** Ingest → Chunk → Embed → Index → Retrieve → Generate → Evaluate

---

## Dataset

**Source:** arXiv.org — Seminal AI/ML Papers  
**URL:** https://arxiv.org

| Stat | Value |
|------|-------|
| Papers | 30 |
| Categories | cs.AI, cs.CL, cs.LG, cs.CV, cs.DB, quant-ph |
| Year range | 2017–2024 |
| Chunks indexed | 30 |

---

## Structure

```
rag-scientific-papers/
├── rag_pipeline.ipynb       # Main RAG notebook
├── arxiv_papers.csv         # Paper corpus
├── README.md
├── requirements.txt
└── figures/
    ├── fig1_embedding_space.png
    └── fig2_evaluation.png
```

---

## Key Results

| Metric | Value |
|--------|-------|
| Precision@3 | 0.73 |
| Recall@3 | 0.80 |
| MRR | 0.71 |
| Vector store | FAISS IndexFlatIP |
| Embedding dim | 128 |

---

## Components

- **Chunking:** Sliding window (200 words, 50 overlap)
- **Embeddings:** TF-IDF + SVD (production: sentence-transformers)
- **Vector Store:** FAISS IndexFlatIP (cosine similarity)
- **Retrieval:** Top-k with diversity filter (max 2 chunks/doc)
- **Prompt Engineering:** System + context + query template
- **Agent:** ReAct loop with search, filter, count tools

## Production Upgrade Path
```
TF-IDF → sentence-transformers/all-MiniLM-L6-v2
Simulated LLM → Anthropic Claude API
FAISS local → Pinecone / ChromaDB
Manual tools → LangChain / LlamaIndex agents
```

---

## Setup

```bash
pip install pandas numpy matplotlib seaborn scikit-learn faiss-cpu scipy jupyter
jupyter notebook rag_pipeline.ipynb
```

---
*Part of the IBM Generative AI & RAG Agents Professional Certificate portfolio*
