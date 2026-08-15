# Vector Database & AST Code Chunking Schema (Day 4 Update)

This document specifies the vector database architecture, embedding configuration, and code-aware chunking schema used in **CodeCompass**.

---

## 1. Vector Database Architecture

CodeCompass utilizes **ChromaDB** as its persistent local vector database engine, configured to store vectors on disk under `backend/chroma_db`.

### Database Settings
- **Client Type:** Persistent Chroma Client (`chromadb.PersistentClient`)
- **Collection Name:** `codecompass_chunks`
- **Embedding Model:** `text-embedding-3-small` (OpenAI, 1536 dimensions)
- **Fallback Embedding Model:** ONNX `all-MiniLM-L6-v2` (384 dimensions, local offline fallback)
- **Distance Metric:** Cosine Distance (`cosine`)

---

## 2. AST Code-Aware Chunking Strategy

Instead of naive fixed-character splitting that breaks mid-sentence or mid-variable, CodeCompass uses Abstract Syntax Tree (AST) language splitters from `langchain-text-splitters` (`RecursiveCharacterTextSplitter.from_language()`).

### Language Mapping Table

| File Extension | Language Enum | Separators / Boundaries Preserved |
|---|---|---|
| `.py` | `Language.PYTHON` | `def`, `class`, block indentation |
| `.js`, `.jsx` | `Language.JS` | `function`, `class`, `const`, `export` |
| `.ts`, `.tsx` | `Language.TS` | `interface`, `type`, `function`, `class` |
| `.html` | `Language.HTML` | `<div>`, `<script>`, `<style>`, tags |
| `.css` | `Language.HTML` | Rule blocks, media queries |
| `.go` | `Language.GO` | `func`, `struct`, `package` |
| `.rs` | `Language.RUST` | `fn`, `struct`, `impl`, `mod` |
| `.java` | `Language.JAVA` | `class`, `interface`, `public static void` |
| `.c`, `.cpp`, `.h` | `Language.CPP` | `class`, functions, includes |
| `.md` | `Language.MARKDOWN` | Headings (`#`, `##`), code blocks (```` ``` ````) |

### Default Chunk Parameters
- **Target Chunk Size:** 1,000 characters
- **Chunk Overlap:** 150 characters

---

## 3. Record & Metadata Schema

Each vector stored in the Chroma DB collection represents a single code chunk.

```json
{
  "id": "bottlepy_bottle_bottle_py_12",
  "document": "class Router(object):\n    def add(self, rule, method, target, name=None):\n        ...",
  "metadata": {
    "file_path": "bottle.py",
    "language": "python",
    "repo": "bottlepy/bottle",
    "chunk_index": 12,
    "total_chunks": 48,
    "char_length": 842
  }
}
```

### Metadata Fields

1. `file_path` (*String*): Relative file path inside the repository (e.g. `src/utils/helpers.py`).
2. `language` (*String*): Normalized language identifier (e.g. `python`, `ts`).
3. `repo` (*String*): Owner and repository identifier (e.g. `bottlepy/bottle`).
4. `chunk_index` (*Integer*): 0-indexed position of chunk within the file.
5. `total_chunks` (*Integer*): Total count of chunks generated from this file.
6. `char_length` (*Integer*): Exact character count of the chunk text.

---

## 4. Query Retrieval Pipeline

When a query is submitted to `POST /api/search`:
1. The text query is converted into an embedding vector via `text-embedding-3-small`.
2. ChromaDB evaluates Cosine similarity against all vectors in `codecompass_chunks`.
3. The top `k` chunks with smallest cosine distance are returned alongside complete source metadata for LLM citation.
