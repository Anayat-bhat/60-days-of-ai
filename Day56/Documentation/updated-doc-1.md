# Day 56 Documentation: RAG Retrieval & Chat Backend Architecture

This document details the Day 6 (Day 56 of 60-Day Challenge) technical architecture updates for **CodeCompass**.

---

## 🧭 Overview

On Day 56 (Capstone Day 6), we implemented the **RAG Retrieval & Intelligence Chat Service** and integrated it into a full **React Frontend MVP**.

---

## 🏗️ Technical Architecture Updates

### 1. RAG Service Layer (`backend/services/rag_service.py`)
- **Vector Retrieval:** Queries ChromaDB collection `codecompass_chunks` via cosine similarity search (`query_vector_db`).
- **Context Assembly:** Formats top matching code chunks with file paths, languages, and chunk index headers.
- **LLM Grounding:** Prompts the model to answer strictly using provided code snippets and cite exact file paths.
- **Multi-Model Support:** Supports **Google Gemini API** (`GEMINI_API_KEY`), **OpenAI API** (`OPENAI_API_KEY`), or a **Zero-Cost Local Fallback Synthesizer** if no external API key is configured.
- **Citation Extraction:** Returns structured array of source cards:
  ```json
  [
    {
      "file_path": "fastapi/applications.py",
      "language": "python",
      "chunk_index": 0,
      "snippet": "class FastAPI(Starlette)..."
    }
  ]
  ```

### 2. FastAPI Endpoint (`backend/main.py`)
- `POST /api/chat`: Accepts `ChatRequest` schema (`query`, `top_k`, `repo_url`) and returns `{ "status": "success", "answer": "...", "sources": [...] }`.
- Configured CORS middleware allowing cross-origin requests from local dev (`localhost:5173`) and production Vercel domains.

---

## 🎨 Interactive Frontend Architecture

### 1. Collapsible File Tree (`FileTree.jsx`)
- Recursively converts flat file arrays (`[{ path, language }]`) into a directory tree object.
- Features folder expansion/collapse, search filter input, and file extension badges.

### 2. RAG Intelligence Chat (`Chat.jsx`)
- Renders user and assistant message bubbles.
- Provides quick prompt suggestions for onboarding ("Explain architecture", "Where are endpoints defined?").
- Displays expandable **Retrieved Code Citations** cards with copy-to-clipboard code snippets.

### 3. Challenge Footer (`App.jsx`)
- Renders the mandatory footer visible across local and deployed environments:
  > `"Built with Claude as part of the AB Talks 60-Day Claude AI Challenge."`
