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
## ☁️ Deployment & Infrastructure

This project currently runs on **Google Cloud** with embeddings powered by **OpenAI** and models/resources from **Hugging Face**.  
**Supabase** is used for auth, storage, and optionally vector DB. The frontend is being built with **Lovable** (shipping soon).

### Stack at a Glance
- **Compute:** Google Cloud (Compute Engine / Cloud Run)
- **Vector DB:** Supabase pgvector (or FAISS/Chroma locally)
- **Auth/DB/Storage:** Supabase
- **Embeddings:** OpenAI Embeddings API
- **LLMs / Models:** Hugging Face (Transformers / GGUF as applicable)
- **Frontend:** Lovable (in progress; production link coming soon)

---

## 🔑 Services & Keys

Create a `.env` file at the project root:

```ini
# Core
ENV=production
PORT=5000

# OpenAI (used for embeddings)
OPENAI_API_KEY=sk-...

# Hugging Face (optional for gated models or rate limits)
HUGGINGFACEHUB_API_TOKEN=hf_...

# Supabase
SUPABASE_URL=https://<your-project>.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOi...
SUPABASE_SERVICE_ROLE_KEY= # keep server-side only; never expose to frontend

# Vector store choice: faiss | chroma | supabase
VECTOR_STORE=supabase

# Model & device
EMBED_MODEL=text-embedding-3-large           # or text-embedding-3-small
GEN_MODEL_ID=TheBloke/Mistral-7B-Instruct-GGUF  # or HF Transformers model id
DEVICE=cuda                                   # or cpu

# CORS / Frontend
CLIENT_URL=https://<your-lovable-app>.com


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



## 🧠 What I Learned (Course Outcomes)

- ✅ **Create and run a local RAG pipeline from scratch**  
  Learned how to design and execute an end-to-end Retrieval-Augmented Generation system entirely on local hardware.

- ✅ **Implement chunking (Fixed / Semantic / Structural)**  
  Explored multiple text-splitting methods to optimize document embedding and retrieval efficiency.

- ✅ **Build vector search & retrieval scoring**  
  Understood similarity search concepts using cosine distance and integrated FAISS/Chroma for high-speed retrieval.

- ✅ **Construct prompts with retrieved context**  
  Designed dynamic prompt templates that merge retrieved chunks into the model input for accurate, contextual responses.

- ✅ **Integrate local LLM inference end-to-end**  
  Combined embedding, retrieval, and generation modules into a unified local pipeline powered by open-source LLMs.

