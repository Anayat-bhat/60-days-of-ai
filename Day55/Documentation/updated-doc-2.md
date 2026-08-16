# REST API Specifications & Vector Store Schemas (Day 5 Update)

This document details the active REST API endpoints, vector database schemas, and payload structures for **CodeCompass**.

---

## 1. Active REST API Endpoints

### A. Health Check Endpoint
- **URL:** `GET /health`
- **Headers:** `Accept: application/json`
- **Response (200 OK):**
  ```json
  {
    "status": "ok",
    "message": "CodeCompass API is operational"
  }
  ```

---

### B. Ingest GitHub Repository Endpoint
- **URL:** `POST /api/ingest`
- **Headers:** `Content-Type: application/json`
- **Request Payload:**
  ```json
  {
    "repo_url": "https://github.com/fastapi/fastapi"
  }
  ```
- **Response (200 OK):**
  ```json
  {
    "status": "success",
    "repo_url": "https://github.com/fastapi/fastapi",
    "owner": "fastapi",
    "repo": "fastapi",
    "file_count": 45,
    "chunk_count": 120,
    "files": [
      { "path": "fastapi/applications.py", "language": "python" },
      { "path": "fastapi/routing.py", "language": "python" }
    ],
    "vector_db": {
      "status": "success",
      "count": 120,
      "collection": "codecompass_chunks",
      "message": "Successfully indexed 120 chunks into vector database."
    }
  }
  ```

---

### C. Semantic Vector Search Endpoint
- **URL:** `POST /api/search`
- **Headers:** `Content-Type: application/json`
- **Request Payload:**
  ```json
  {
    "query": "Where is CORS middleware configured?",
    "top_k": 5
  }
  ```
- **Response (200 OK):**
  ```json
  {
    "status": "success",
    "query": "Where is CORS middleware configured?",
    "count": 5,
    "results": [
      {
        "content": "app.add_middleware(CORSMiddleware, allow_origins=['*'])",
        "metadata": {
          "file_path": "backend/main.py",
          "language": "python",
          "repo": "owner/repo",
          "chunk_index": 0,
          "total_chunks": 3,
          "char_length": 145
        },
        "score": 0.1852
      }
    ]
  }
  ```

---

## 2. Vector Store & Payload Schema

### Database Collection Settings
- **Vector DB:** Persistent ChromaDB (`backend/chroma_db`)
- **Collection Name:** `codecompass_chunks`
- **Embedding Model:** Local ONNX `all-MiniLM-L6-v2` (384 dimensions, zero API cost)
- **Distance Metric:** Cosine similarity

### Chunk Payload Schema
```json
{
  "id": "fastapi_fastapi_fastapi_applications_py_0",
  "document": "class FastAPI(Starlette):\n    def __init__(self, ...): ...",
  "metadata": {
    "file_path": "fastapi/applications.py",
    "language": "python",
    "repo": "fastapi/fastapi",
    "chunk_index": 0,
    "total_chunks": 12,
    "char_length": 950
  }
}
```
