# CodeCompass: Product Requirements Document (PRD)

## 1. Product Overview
**CodeCompass** is an AI-powered developer tool designed to accelerate the onboarding process for software engineers navigating unfamiliar codebases. By simply pasting a public GitHub repository URL, developers get an instant, AI-generated onboarding brief, a visual file tree, and a proactive chat interface to ask natural-language questions grounded in the repository's actual source code.

## 2. Problem Statement
When developers join a new project, contribute to open-source, or review external libraries, they spend hours parsing undocumented code, tracing execution paths, and figuring out where to start. Existing AI tools often require cloning the repo locally, setting up heavy IDE extensions, or lack code-aware context (naive text chunking breaks functions in half, leading to poor answers).

## 3. Target Audience
- **Software Engineers (Mid/Senior):** Exploring open-source libraries or onboarding to new team projects.
- **Junior Developers:** Needing guidance to understand architecture and execution flow.
- **AI/ML Engineers:** Reviewing reference implementations of research papers.

## 4. The Solution
CodeCompass provides a zero-setup web interface where users can interact with a codebase instantly. It differentiates itself through **code-aware RAG**—chunking source code intelligently by function and class boundaries rather than arbitrary character counts, ensuring the LLM understands the complete context of a code block.

## 5. Scope & Features (v1.0)

### 5.1 Must-Have Features (In-Scope for Day 10)
1. **Repository Ingestion via URL:** Accept a public GitHub URL (Python/JS/TS, capped at ~200 files) and fetch the raw code.
2. **Code-Aware Chunking & Embedding:** Parse Python and JS/TS files, chunk them by functions/classes, embed using OpenAI, and store in a Vector DB.
3. **Auto-Generated Onboarding Brief:** Generate a high-level architecture overview, key modules list, and setup steps upon ingestion.
4. **Visual File Tree:** Display the repository's directory structure alongside the chat interface.
5. **Proactive Chat with Citations:** Natural language Q&A grounded in the codebase. Responses must cite the specific file (and ideally the line number, degrading to file-name gracefully if needed).
6. **Public Live Deployment:** Accessible via a live URL, deployed early (Day 4-5) to de-risk shipping.

### 5.2 Out of Scope (For Future Versions)
- Private repository support (OAuth).
- Code generation / writing commits.
- Support for repositories >200 files or unsupported languages (e.g., C++, Rust).
- IDE integrations (VS Code / JetBrains extensions).
- Multi-repo chat.

## 6. Technical Architecture
- **Frontend:** React (Vite), Tailwind CSS, Framer Motion (for polished UI).
- **Backend:** FastAPI (Python) - optimized for AI/DS track strengths.
- **AI / Data Pipeline:** 
  - LangChain / LlamaIndex for RAG orchestration.
  - OpenAI (GPT-4o or gpt-4o-mini for generation, `text-embedding-3-small` for embeddings).
  - Pinecone or Supabase for Vector Database.
  - GitHub REST API for code fetching.
- **Deployment:** Vercel (Frontend) and Render/Railway (Backend).

## 7. Success Criteria
- **Functional:** A user can paste a 100-file Python repo, wait < 60 seconds for ingestion, read the brief, and get an accurate answer about where a specific feature is implemented.
- **Technical:** Live deployment is stable. Code-aware chunking yields noticeably better answers than naive text splitting.
- **Deadline:** v1.0 is polished and deployed by the end of Day 10.
