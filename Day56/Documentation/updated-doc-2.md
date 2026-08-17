# Day 56 Documentation: RAG REST API & Schema Specifications

This document details the payload schemas and API specifications introduced on Day 56 for **CodeCompass**.

---

## 📡 Endpoints Summary

| Endpoint | Method | Purpose | Status |
| :--- | :--- | :--- | :--- |
| `/health` | `GET` | Server health & CORS check | ✅ Operational |
| `/api/ingest` | `POST` | Ingest GitHub repo, chunk AST, index ChromaDB | ✅ Operational |
| `/api/search` | `POST` | Perform raw vector similarity search | ✅ Operational |
| `/api/chat` | `POST` | Perform RAG QA with file citations | ✅ Operational (Day 56) |

---

## 📄 `POST /api/chat` Endpoint Specification

### Request Body (`ChatRequest`)
```json
{
  "query": "Where is CORS middleware configured?",
  "top_k": 5,
  "repo_url": "https://github.com/fastapi/fastapi"
}
```

### Response Payload (200 OK)
```json
{
  "status": "success",
  "query": "Where is CORS middleware configured?",
  "answer": "Based on semantic code search in the ingested repository, CORS middleware is configured in `backend/main.py` using `app.add_middleware(CORSMiddleware, allow_origins=['*'])`.",
  "sources": [
    {
      "file_path": "backend/main.py",
      "language": "python",
      "chunk_index": 0,
      "snippet": "app.add_middleware(CORSMiddleware, allow_origins=['*'], allow_credentials=True...)"
    }
  ],
  "chunks_retrieved": 5
}
```

---

## 🌐 Cloud Deployment Setup

- **Backend (Render):** Deploy using `backend/render.yaml` or connect repository to Render Web Service pointing to root directory `backend`.
  - Build Command: `pip install -r requirements.txt`
  - Start Command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
- **Frontend (Vercel):** Import repository in Vercel, set root directory to `frontend`.
  - Environment Variable: `VITE_BACKEND_URL=https://<your-render-backend-url>`
