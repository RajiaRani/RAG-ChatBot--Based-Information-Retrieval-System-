# 🧠 RAG-ChatBot Based Information Retrieval System
> A from-scratch Retrieval-Augmented Generation (RAG) pipeline to chat with large PDFs — privacy-first, fast, and fully customizable.

<p align="left">
  <a href="https://img.shields.io/badge/Python-3.10+-blue.svg"><img src="https://img.shields.io/badge/Python-3.10+-blue.svg" /></a>
  <a href="https://img.shields.io/badge/LLM-Local-green"><img src="https://img.shields.io/badge/LLM-Local-green" /></a>
  <a href="https://img.shields.io/badge/License-MIT-lightgrey"><img src="https://img.shields.io/badge/License-MIT-lightgrey" /></a>
</p>

---

## 📌 Overview
This project implements a **RAG pipeline** that lets you upload a PDF, ask questions, and get **grounded, citation-backed answers** from a **local or cloud-based LLM**.  

Unlike frameworks such as **LangChain** or **LlamaIndex**, this repo **builds each piece from scratch**, helping you understand:
- Chunking strategies (Fixed / Semantic / Structural)
- Embeddings & Vector Search
- Retrieval → Augmentation → Generation workflow  

**Why local or hybrid cloud?**  
Privacy 🔒 | Speed ⚡ | Zero recurring cost 💸

---

## ✨ Features
- 📄 **PDF ingestion** (any document or textbook)
- 🧱 **Chunking:** Fixed, Semantic, Structural
- 🧮 **Embeddings:** via OpenAI or local models
- 🔎 **Vector Search:** Cosine similarity (FAISS / Chroma / Supabase)
- 💬 **Chat Interface:** Streamlit / Flask
- 📚 **Citations:** Source text + page numbers
- 🧪 **Transparent Architecture:** Every step is visible and customizable

---

## 🧭 Architecture

The RAG pipeline follows a modular design connecting document ingestion, embedding, retrieval, and generation:

<p align="center">
  <img src="./assets/rag_architecture.png" alt="RAG Architecture Diagram" width="85%" />
</p>

**Workflow Steps:**
1️⃣ Document ingestion → text chunking  
2️⃣ Embedding creation (OpenAI / Hugging Face)  
3️⃣ Vector storage in Supabase / FAISS  
4️⃣ Retrieval based on semantic similarity  
5️⃣ Context-augmented prompt construction  
6️⃣ Response generation via LLM  
7️⃣ Citation + source display in UI

---

## ☁️ Deployment & Infrastructure

This project runs on **Google Cloud**, with embeddings powered by **OpenAI**, models from **Hugging Face**, and backend storage via **Supabase**.  
Frontend is being developed on **Lovable**, and the **production link** will be added soon.

### 🧩 Stack at a Glance
| Layer | Service / Tool |
|-------|----------------|
| Compute | Google Cloud (Compute Engine / Cloud Run) |
| Database | Supabase (pgvector) |
| Embeddings | OpenAI API |
| LLM | Hugging Face Transformers / GGUF |
| UI | Lovable (in progress) |
| Vector Store | Supabase / FAISS / Chroma |

---

## 🔑 Environment Setup

Create a `.env` file in your root directory:

```ini
# Core
ENV=production
PORT=5000

# OpenAI (for embeddings)
OPENAI_API_KEY=sk-...

# Hugging Face (optional)
HUGGINGFACEHUB_API_TOKEN=hf_...

# Supabase
SUPABASE_URL=https://<your-project>.supabase.co
SUPABASE_ANON_KEY=eyJhbGciOi...
SUPABASE_SERVICE_ROLE_KEY= # keep this private

# Vector store choice: faiss | chroma | supabase
VECTOR_STORE=supabase

# Model & device
EMBED_MODEL=text-embedding-3-large
GEN_MODEL_ID=TheBloke/Mistral-7B-Instruct-GGUF
DEVICE=cuda  # or cpu

# CORS / Frontend
CLIENT_URL=https://<your-lovable-app>.com
