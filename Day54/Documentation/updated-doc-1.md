# API Specifications: CodeCompass (Day 4 Update)

This document details the active REST API endpoints implemented on the FastAPI backend for **CodeCompass**.

---

## 1. System Health Check
**Purpose:** Endpoint used by the React frontend and monitoring tools to check backend operational status.

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

## 2. Ingest GitHub Repository
**Purpose:** Fetches a public GitHub repository, extracts source code files, splits code into AST-aware chunks, generates vector embeddings, and stores vectors into ChromaDB.

- **URL:** `POST /api/ingest`
- **Headers:** `Content-Type: application/json`
- **Request Body:**
  ```json
  {
    "repo_url": "https://github.com/bottlepy/bottle"
  }
  ```

- **Validation Rules:**
  - `repo_url` must be a valid public GitHub URL or `owner/repo` string.
  - Excludes binary files, lockfiles (`package-lock.json`, `poetry.lock`), and ignored directories (`node_modules`, `.git`, `venv`, `dist`, `build`).
  - Limits file fetching to 150 supported source files per repository.
  - Supported extensions: `.py`, `.js`, `.ts`, `.jsx`, `.tsx`, `.html`, `.css`, `.json`, `.md`, `.go`, `.rs`, `.java`, `.c`, `.cpp`.

- **Response (200 OK):**
  ```json
  {
    "status": "success",
    "repo_url": "https://github.com/bottlepy/bottle",
    "owner": "bottlepy",
    "repo": "bottle",
    "file_count": 31,
    "chunk_count": 524,
    "files": [
      {
        "path": "bottle.py",
        "language": "python"
      },
      {
        "path": "test/test_router.py",
        "language": "python"
      }
    ],
    "vector_db": {
      "status": "success",
      "count": 524,
      "collection": "codecompass_chunks",
      "message": "Successfully indexed 524 chunks into vector database."
    }
  }
  ```

- **Error Responses:**
  - `400 Bad Request`: Invalid GitHub URL format or no supported source code files found.
  - `404 Not Found`: Repository does not exist or is private.
  - `500 Internal Server Error`: Parsing or vector store insertion failure.

---

## 3. Semantic Vector Search
**Purpose:** Queries indexed code chunks using semantic vector similarity.

- **URL:** `POST /api/search`
- **Headers:** `Content-Type: application/json`
- **Request Body:**
  ```json
  {
    "query": "routing logic for HTTP GET",
    "top_k": 5
  }
  ```

- **Response (200 OK):**
  ```json
  {
    "status": "success",
    "query": "routing logic for HTTP GET",
    "count": 5,
    "results": [
      {
        "content": "class Router(object):\n    def add(self, rule, method, target, name=None):...",
        "metadata": {
          "file_path": "bottle.py",
          "language": "python",
          "repo": "bottlepy/bottle",
          "chunk_index": 12,
          "total_chunks": 48
        },
        "score": 0.2451
      }
    ]
  }
  ```

---

## 4. Grounded Chat Stream (Scheduled for Day 6)
**Purpose:** Streamed RAG response generation using retrieved context.
- **URL:** `POST /api/chat`
