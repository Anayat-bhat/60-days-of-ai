# CodeCompass Project Structure

```text
codecompass/
├── frontend/                  # React & Vite frontend
│   ├── public/                # Static assets
│   ├── src/
│   │   ├── components/        # React UI components (Chat, FileTree, etc.)
│   │   ├── utils/             # Helper functions (e.g., API clients)
│   │   ├── App.jsx            # Main React component
│   │   ├── main.jsx           # React entry point
│   │   └── index.css          # Tailwind CSS global styles
│   ├── package.json
│   ├── tailwind.config.js     # Tailwind v4 configuration
│   └── vite.config.js
│
├── backend/                   # FastAPI Python backend
│   ├── services/              # Core business logic
│   │   ├── github_service.py  # GitHub API ingestion
│   │   ├── chunker.py         # Code splitting logic
│   │   ├── vector_db.py       # Pinecone integration
│   │   ├── rag_service.py     # LLM and retrieval logic
│   │   └── brief_service.py   # Onboarding summary generation
│   ├── main.py                # FastAPI app & endpoints
│   ├── requirements.txt       # Python dependencies
│   └── .env                   # Environment variables (IGNORED IN GIT)
│
├── docs/                      # Architectural source of truth
│   ├── ARCHITECTURE.md
│   ├── SCHEMA.md
│   ├── API.md
│   ├── UI-WIREFRAMES.md
│   └── PROJECT-STRUCTURE.md
└── README.md
```
