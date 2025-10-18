# 🧠 RAG-ChatBot Based Information Retrieval System
> A from-scratch Retrieval-Augmented Generation (RAG) pipeline to chat with large PDFs locally — privacy-first, fast, and fully customizable.

<p align="left">
  <a href="https://img.shields.io/badge/Python-3.10+-blue.svg"><img src="https://img.shields.io/badge/Python-3.10+-blue.svg" /></a>
  <a href="https://img.shields.io/badge/LLM-Local-green"><img src="https://img.shields.io/badge/LLM-Local-green" /></a>
  <a href="https://img.shields.io/badge/License-MIT-lightgrey"><img src="https://img.shields.io/badge/License-MIT-lightgrey" /></a>
</p>

---

## 📌 Overview
This project implements a **local RAG pipeline** that lets you upload a PDF, ask questions, and get **grounded, citation-backed answers** from a **local LLM**.  
Unlike using frameworks (LangChain/LlamaIndex), this repo **builds each piece from scratch** so you can understand and tune:
- chunking strategies (fixed / semantic / structural)
- embeddings & vector search
- retrieval → augmentation → generation

**Why local?** Privacy 🔒, speed ⚡, and zero per-query cost 💸.

---

## ✨ Features
- 📄 **PDF ingestion** (any textbook/doc)
- 🧱 **Chunking**: fixed, semantic, structural
- 🧮 **Embeddings** via open-source models
- 🔎 **Vector search** (cosine similarity)
- 💬 **Chat UI** (Streamlit/Flask)
- 📚 **Citations**: source text + page refs
- 🧪 **Fully transparent codepath** (no magic)

---

## 🧭 Architecture

**RAG Flow**
1) **Ingest & Chunk** → 2) **Embed** → 3) **Index** → 4) **Retrieve** → 5) **Augment Prompt** → 6) **Generate + Cite**

---

## 🧰 Tech Stack
- Python, PyTorch / Transformers
- FAISS or Chroma for vector search
- Streamlit or Flask for UI
- Any local LLM (e.g., Mistral/Llama-family via GGUF/Transformers)

---

## 🚀 Quickstart

> **Prereqs:** Python 3.10+, GPU (optional but recommended)

```bash
# 1) Clone
git clone https://github.com/<your-username>/RAG-ChatBot--Based-Information-Retrieval-System.git
cd RAG-ChatBot--Based-Information-Retrieval-System

# 2) Create venv (optional but recommended)
python -m venv .venv && source .venv/bin/activate   # (Windows: .venv\Scripts\activate)

# 3) Install deps
pip install -r requirements.txt

# 4) Put your PDF(s)
mkdir -p data && cp /path/to/your.pdf data/

# 5) Run (choose your entrypoint)
# Streamlit UI:
streamlit run app.py
# OR Flask:
# python app.py
# OR Notebook:
# jupyter lab  # then open main.ipynb



🧠 What I Learned (Course Outcomes)

Create/run a local RAG pipeline from scratch

Implement chunking (fixed/semantic/structural)

Build vector search & retrieval scoring

Construct prompts with retrieved context

Integrate local LLM inference end-to-end
