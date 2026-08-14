# CodeCompass: Implementation Blueprint (Days 2-10)

This blueprint serves as the single source of truth for the remainder of the 10-day capstone. Each day is designed so that a fresh AI conversation can pick up exactly where the last one left off.

---

## Day 2: Tech Stack Foundation & Architecture Scaffold

**🎯 Objective:** Initialize the frontend and backend repositories/folders, configure essential tooling, and establish basic communication between the two.
**📖 What I'll learn:** Setting up a monorepo structure, configuring FastAPI with CORS, and Vite React foundation.
**🛠 Features to build:** 
- A basic FastAPI backend returning a health check.
- A basic React (Vite) frontend with Tailwind CSS installed.
- API connectivity test (Frontend fetching from Backend).
**📝 Step-by-step implementation plan:**
1. Create a root `codecompass` folder. Inside, initialize `frontend` (Vite + React) and `backend` (Python virtual environment).
2. Backend: Install FastAPI, Uvicorn, and standard utilities. Create `main.py` with a `/health` endpoint and CORS middleware configured for `localhost:5173`.
3. Frontend: Install Tailwind CSS, configure `tailwind.config.js`. Create a simple UI in `App.jsx` with a "Backend Status" indicator.
4. Run both servers and verify the frontend can successfully ping the backend.
**📂 Files and folders to create or modify:**
- `backend/main.py`
- `backend/requirements.txt`
- `frontend/src/App.jsx`
- `frontend/tailwind.config.js` and `frontend/postcss.config.js`
**🔗 APIs, libraries, services:** FastAPI, Uvicorn, Vite, React, Tailwind CSS.
**🧪 Testing tasks:** Verify backend running on `8000`. Verify frontend running on `5173`. Ensure `/health` API call succeeds in browser network tab.
**🐞 Common issues and debugging tips:** CORS errors (ensure allow_origins includes `http://localhost:5173`). Port conflicts (kill existing uvicorn processes).
**✅ End-of-day checklist:**
- [ ] Backend repo set up.
- [ ] Frontend repo set up.
- [ ] Successful API call between them.
**📸 Expected project state and screenshots to capture:** A screenshot of the web page showing "Backend Status: Connected".
**➡️ Handoff notes for the next day:** We have a working frontend and backend. Tomorrow, we will implement the GitHub API ingestion service in the backend.

---

## Day 3: GitHub Repository Ingestion Service

**🎯 Objective:** Build the backend capability to accept a GitHub URL, validate it, and fetch the repository's file structure and content.
**📖 What I'll learn:** Working with the GitHub REST API, managing API rate limits, and parsing Git trees.
**🛠 Features to build:**
- API endpoint `POST /api/ingest` accepting a `repo_url`.
- Service to extract owner/repo, fetch the repository tree, and filter for target file extensions (`.py`, `.js`, `.ts`).
- Service to fetch raw file contents for the filtered files.
**📝 Step-by-step implementation plan:**
1. Generate a GitHub Personal Access Token (PAT).
2. Create `github_service.py` with functions to get the repository tree (recursive) and fetch raw file content.
3. Implement filtering to exclude `node_modules`, `.git`, lockfiles, and binaries. Enforce the ~200 file limit.
4. Update `main.py` to include the `POST /api/ingest` endpoint that uses this service and returns the file tree and contents as JSON.
**📂 Files and folders to create or modify:**
- `backend/services/github_service.py`
- `backend/main.py` (add endpoint)
- `backend/.env` (store GITHUB_TOKEN)
**🔗 APIs, libraries, services:** GitHub REST API (`PyGithub` or `requests`), `python-dotenv`.
**🧪 Testing tasks:** Use Postman or curl to hit `/api/ingest` with a small public repo (e.g., `<user>/<repo>`). Verify the returned JSON contains the correct file paths and raw text.
**🐞 Common issues and debugging tips:** GitHub rate limiting (ensure PAT is passed in headers). Recursive tree API truncating (handle large repos by rejecting them early).
**✅ End-of-day checklist:**
- [ ] GitHub token configured securely.
- [ ] Ingestion endpoint functional and tested.
- [ ] File limit and filtering logic works.
**📸 Expected project state and screenshots to capture:** JSON response from the ingest endpoint showing file paths and raw code.
**➡️ Handoff notes for the next day:** Ingestion works. Tomorrow we tackle chunking this code and generating vector embeddings.

---

## Day 4: Code-Aware Chunking & Embeddings

**🎯 Objective:** Process the fetched code by chunking it intelligently (by functions/classes) and storing it in a vector database.
**📖 What I'll learn:** AST parsing (or LangChain code splitters), embedding models, Vector DB integrations.
**🛠 Features to build:**
- Code splitter service for Python and JS/TS.
- OpenAI Embeddings integration.
- Vector DB integration (Pinecone or Supabase).
**📝 Step-by-step implementation plan:**
1. Set up OpenAI and Vector DB API keys in `.env`.
2. Create `chunker.py` using LangChain's `RecursiveCharacterTextSplitter.from_language()` (or similar logic) to respect code boundaries. Include file metadata (path, language) in chunks.
3. Create `vector_db.py` to initialize the client, create an index (if needed), and upsert chunk embeddings.
4. Update the `/api/ingest` endpoint to pass the fetched code through the chunker and into the vector database.
**📂 Files and folders to create or modify:**
- `backend/services/chunker.py`
- `backend/services/vector_db.py`
- `backend/main.py`
**🔗 APIs, libraries, services:** `langchain-text-splitters`, `openai`, Vector DB client (e.g., `pinecone-client`).
**🧪 Testing tasks:** Ingest a small repo and verify in the Vector DB dashboard that vectors are created and metadata (file path) is attached.
**🐞 Common issues and debugging tips:** OpenAI rate limits or token limits (batch embeddings). Vector dimension mismatch (OpenAI `text-embedding-3-small` is 1536 dimensions).
**✅ End-of-day checklist:**
- [ ] Code properly chunked with metadata.
- [ ] Embeddings generated successfully.
- [ ] Vectors stored in DB.
**📸 Expected project state and screenshots to capture:** Screenshot of the Vector DB dashboard showing populated index.
**➡️ Handoff notes for the next day:** We have vectors stored. Tomorrow, we focus on an early public deployment to de-risk shipping.

---

## Day 5: Early Deployment Pipeline

**🎯 Objective:** Deploy the frontend and backend to live URLs to ensure the production environment mirrors local development.
**📖 What I'll learn:** Cloud hosting platforms (Render/Railway, Vercel), Environment variable management in production.
**🛠 Features to build:**
- Live backend API (e.g., on Render).
- Live frontend application (e.g., on Vercel).
- Configured production environment variables.
**📝 Step-by-step implementation plan:**
1. Push local repositories to GitHub.
2. Backend: Configure a `Procfile` or `render.yaml`. Deploy to Render/Railway. Add all `.env` variables (OpenAI, GitHub, VectorDB) to the hosting provider.
3. Frontend: Deploy to Vercel. Add the live Backend URL as an environment variable (e.g., `VITE_API_URL`).
4. Update frontend `App.jsx` to use `VITE_API_URL` instead of localhost for the health check.
**📂 Files and folders to create or modify:**
- `backend/Procfile` or equivalent config.
- `frontend/.env.production`
- Update CORS in `backend/main.py` to allow the Vercel URL.
**🔗 APIs, libraries, services:** Render/Railway, Vercel, GitHub Actions (optional).
**🧪 Testing tasks:** Visit the live Vercel URL. Ensure the health check succeeds. Hit the live backend `/health` URL directly.
**🐞 Common issues and debugging tips:** CORS failures in production (double-check trailing slashes in allowed origins). Missing env vars crashing the backend.
**✅ End-of-day checklist:**
- [ ] Backend deployed and accessible.
- [ ] Frontend deployed and accessible.
- [ ] Both communicating successfully.
**📸 Expected project state and screenshots to capture:** The live frontend showing a successful connection to the live backend.
**➡️ Handoff notes for the next day:** Deployed early! Tomorrow, we build the RAG retrieval logic and QA backend endpoints.

---

## Day 6: RAG Retrieval & Chat Backend

**🎯 Objective:** Implement the logic to search the vector database and generate AI responses grounded in the retrieved code.
**📖 What I'll learn:** Semantic search, prompt engineering for code comprehension, LangChain QA chains.
**🛠 Features to build:**
- Retrieval service to find relevant code chunks for a user query.
- LLM generation service to construct a prompt with the retrieved context.
- `POST /api/chat` endpoint to handle user questions.
**📝 Step-by-step implementation plan:**
1. Create `rag_service.py` to handle querying the Vector DB based on the user's input (embedded).
2. Construct a system prompt instructing the LLM (GPT-4o/mini) to answer based ONLY on the provided context, and to cite file paths (metadata).
3. Create the `/api/chat` endpoint which takes `session_id`, `query`, and returns the AI's answer and sources.
**📂 Files and folders to create or modify:**
- `backend/services/rag_service.py`
- `backend/main.py` (add chat endpoint)
**🔗 APIs, libraries, services:** `langchain` (optional, can use raw OpenAI client), `openai`.
**🧪 Testing tasks:** Call `/api/chat` via Postman with a question like "Where is the authentication handled?". Check if the response includes file paths.
**🐞 Common issues and debugging tips:** Hallucinations (enforce strict prompt constraints). Poor retrieval (tweak top_k or chunk size).
**✅ End-of-day checklist:**
- [ ] Vector search works.
- [ ] LLM generates accurate, cited answers.
- [ ] Chat endpoint is functional.
**📸 Expected project state and screenshots to capture:** JSON response from `/api/chat` showing the answer and cited file metadata.
**➡️ Handoff notes for the next day:** Backend chat logic is ready. Tomorrow, we build the core Frontend UI.

---

## Day 7: Frontend Interface (Chat & File Tree)

**🎯 Objective:** Build the main user interface for CodeCompass, featuring the chat window and the repository file tree.
**📖 What I'll learn:** Complex React state management, building polished UI components, rendering recursive data structures.
**🛠 Features to build:**
- URL input bar for repo ingestion.
- Chat Interface (message list, input field, loading states).
- Visual File Tree panel (collapsible folders).
**📝 Step-by-step implementation plan:**
1. Scaffold layout: Left panel (File Tree), Right panel (Chat & Brief tabs).
2. Build `FileTree.jsx` using the tree metadata returned during the Day 3 ingestion endpoint. Use recursive components for folders.
3. Build `Chat.jsx` to map over a messages array (user vs assistant) and handle input submission, hitting `/api/chat`.
4. Style with Tailwind and Lucide icons for a premium feel.
**📂 Files and folders to create or modify:**
- `frontend/src/components/FileTree.jsx`
- `frontend/src/components/Chat.jsx`
- `frontend/src/components/Layout.jsx`
- `frontend/src/App.jsx`
**🔗 APIs, libraries, services:** `lucide-react`, `framer-motion` (for smooth transitions).
**🧪 Testing tasks:** Paste a URL, verify the file tree renders correctly. Ask a question, verify the message appears in the UI after the API responds.
**🐞 Common issues and debugging tips:** React state desync during slow API calls (use loading spinners). Tree rendering errors (ensure stable JSON structure).
**✅ End-of-day checklist:**
- [ ] File tree renders accurately.
- [ ] Chat UI handles messaging flow.
- [ ] Layout is responsive and polished.
**📸 Expected project state and screenshots to capture:** The full web UI with a populated file tree and a chat interaction.
**➡️ Handoff notes for the next day:** UI is looking great. Tomorrow, we add the auto-generated Onboarding Brief.

---

## Day 8: Auto-Generated Onboarding Brief

**🎯 Objective:** Implement the automated summary that welcomes the user after repo ingestion.
**📖 What I'll learn:** Prompting for summarization, managing parallel LLM tasks, structuring markdown in React.
**🛠 Features to build:**
- Backend service to generate a summary (Architecture, Key Files, Setup) using the repo structure and `README.md`.
- Frontend tab to display the Onboarding Brief (Markdown rendered).
**📝 Step-by-step implementation plan:**
1. Backend: Update `/api/ingest` (or a separate `/api/brief` endpoint) to send the repo structure and README to GPT-4o with a summarization prompt.
2. Frontend: Install a markdown renderer (e.g., `react-markdown`).
3. Frontend: Create the `OnboardingBrief.jsx` component.
4. Set the Brief to display automatically once ingestion completes, acting as the first message in the chat or in its own dedicated tab.
**📂 Files and folders to create or modify:**
- `backend/services/brief_service.py`
- `frontend/src/components/OnboardingBrief.jsx`
**🔗 APIs, libraries, services:** `react-markdown`, `remark-gfm`.
**🧪 Testing tasks:** Ingest a repo, verify the brief is generated in < 15 seconds. Ensure markdown renders correctly in the UI (headers, lists, code blocks).
**🐞 Common issues and debugging tips:** LLM timeouts during summarization (use a smaller model or only send key files). Markdown rendering issues with Tailwind (use `@tailwindcss/typography`).
**✅ End-of-day checklist:**
- [ ] Backend generates the brief.
- [ ] Frontend renders it cleanly.
**📸 Expected project state and screenshots to capture:** The UI showing the beautifully formatted Onboarding Brief tab.
**➡️ Handoff notes for the next day:** The core features are complete. Tomorrow we refine, connect edge cases, and add streaming if possible.

---

## Day 9: End-to-End Refinement & Streaming Responses

**🎯 Objective:** Tie all systems together seamlessly, handle edge cases, and upgrade the chat to stream responses word-by-word for better UX.
**📖 What I'll learn:** Server-Sent Events (SSE) / Streaming with FastAPI and React, error boundary handling.
**🛠 Features to build:**
- Chat response streaming.
- Graceful error handling (invalid URLs, repos too large, rate limits).
- Clear loading states for ingestion.
**📝 Step-by-step implementation plan:**
1. Backend: Refactor `/api/chat` to use FastAPI's `StreamingResponse` and LangChain's async streaming callbacks (or raw OpenAI streaming).
2. Frontend: Refactor chat fetching to use the Streams API (`reader.read()`) to append text to the active message state.
3. Add toast notifications (e.g., `react-hot-toast`) for error handling.
4. Verify citations are visibly formatted (e.g., as badges or inline links).
**📂 Files and folders to create or modify:**
- `backend/main.py` (update chat endpoint)
- `frontend/src/components/Chat.jsx` (stream reader)
**🔗 APIs, libraries, services:** `react-hot-toast`.
**🧪 Testing tasks:** Ask a complex question and watch the text stream in. Test breaking the app (bad URL, huge repo) and ensure friendly errors appear.
**🐞 Common issues and debugging tips:** Streaming chunks combining incorrectly in React state (use functional state updates). SSE connection timeouts on hosting providers.
**✅ End-of-day checklist:**
- [ ] Streaming works smoothly.
- [ ] Error states handled gracefully.
- [ ] Citations are distinct and readable.
**📸 Expected project state and screenshots to capture:** A GIF or screenshot of the chat streaming a response with citations.
**➡️ Handoff notes for the next day:** The app is robust and feels premium. Tomorrow is Day 10: Final polish, push to prod, and pitch prep.

---

## Day 10: Final Polish, Testing & Pitch Prep

**🎯 Objective:** Ensure the v1.0 deployment is flawless, finalize the UI aesthetics, and prepare the project for presentation.
**📖 What I'll learn:** Final QA methodologies, preparing a technical showcase.
**🛠 Features to build:**
- Final UI tweaks (colors, padding, empty states).
- Comprehensive end-to-end testing of the live deployment.
**📝 Step-by-step implementation plan:**
1. Push all code to the production branch. Verify Vercel and Render deployments succeed.
2. Conduct manual QA: Test 3 different repos (a small python script, a mid-sized JS framework, a repo with no README).
3. Update the GitHub `README.md` for CodeCompass with a great description, screenshot, and the live link.
4. Record a 1-2 minute demo video/GIF for the pitch deck and README.
**📂 Files and folders to create or modify:**
- `README.md` (Project root)
- UI components (for minor polish)
**🔗 APIs, libraries, services:** None.
**🧪 Testing tasks:** Cross-browser testing (Chrome, Safari). Mobile responsiveness check (at least basic readability).
**🐞 Common issues and debugging tips:** Last-minute CSS bugs. Production env vars missing after a refactor.
**✅ End-of-day checklist:**
- [ ] Live app is stable and fast.
- [ ] Code is pushed and clean.
- [ ] Pitch deck is ready (generated on Day 1).
- [ ] Demo recorded.
**📸 Expected project state and screenshots to capture:** The final, polished v1.0 application deployed live.
**➡️ Handoff notes for the next day:** CONGRATULATIONS! You have successfully shipped CodeCompass v1.0 in 10 days!
