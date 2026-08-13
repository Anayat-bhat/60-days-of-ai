# Day 50 — Defend Your Experience (Premium UX with Home Landing Page)

## What Defend Your Experience Is

**Defend Your Experience** is a commercial-grade, premium, offline-first adaptive interview application designed to make interview defense feel like a high-end product rather than a basic AI chatbot.

Instead of providing generic interview advice, the application extracts every explicit claim from a candidate's uploaded resume, portfolio, or startup proposal and acts as an **intelligent skeptic** that continuously challenges them with adaptive, personalized follow-up questions tailored specifically to their own experience.

---

## Purpose & Core UX Philosophy

Traditional interview preparation tools focus on resume formatting or boilerplate question lists. However, real technical interviewers, VC investors, and senior leaders probe deeply into specific assertions:
- *"You claimed a 45% latency reduction — what was the exact baseline metric and benchmark setup?"*
- *"You listed PyTorch and Fast-API — did you write the core inference pipeline yourself or use a high-level wrapper?"*
- *"You said you led a team — how did you resolve conflicts when members disagreed on technical direction?"*

**Defend Your Experience** addresses these challenges with a **Product-Grade Premium UX**:
- **🏠 Dedicated Home Landing Page:** High-impact hero section with gradient headings, quick call-to-action buttons (`Start New Defense Session`, `Try Sample AI Profile`, `Watch Interactive Tour`), feature showcase grid, and 4-step workflow banner.
- **Clear Onboarding:** Guided 3-step interactive tour explaining the claim-defense lifecycle.
- **Workflow Progress Stepper:** Top breadcrumb bar tracking active progress from *Setup & Upload* to *Claim Extraction*, *Interrogation*, and *Final Assessment*.
- **Question-by-Question Navigation:** Question progress bar (`Claim X of Y (Pct%)`), claim navigation controls (`Prev Claim`, `Next Claim`, `Skip`), and active claim display cards.
- **Live Response Performance Analyzer:** Real-time feedback bar analyzing input word count, metric presence (`📊 Metric Detected`), STAR framework keywords, and strong impact verbs.
- **Confidence & Performance Indicators:** 5-axis SVG Radar Chart, SVG stroke-dashoffset readiness gauge dial (0–100%), and color-coded claim vulnerability risk badges (`HIGH`, `MEDIUM`, `LOW`, `DEFENDED`).
- **Final Defense Diagnostic Report:** Executive summary, defended vs. vulnerable claim matrices, anticipated attack vectors, and story reframing recommendations.
- **Session History & Persistence:** LocalStorage session manager allowing users to save, load, rename, and export past interview rounds.
- **Multi-Format Exports:** Export reports as **Printable PDF**, **Markdown Summary**, or **JSON Session Data**.
- **Graceful Offline & API Error Handling:** Direct Anthropic Messages API client paired with an intelligent local simulation engine that guarantees 100% functionality without API keys or during network errors.

---

## Navigation & Page Views

1. **🏠 Home:** Hero landing page with quick action triggers, feature cards, and visual workflow overview.
2. **📝 Setup & Claims:** Document upload, goal selection, persona picker, and NLP claim extraction.
3. **🎯 Adaptive Interview:** Interactive chat interface with AI skeptic persona, MCQ response strategy pills, live STAR tracker, and progress bar.
4. **📊 Analytics:** 5-Axis SVG Radar Chart and claim vulnerability matrix table.
5. **📜 Defense Report:** Comprehensive diagnostic report with attack vector analysis and printable PDF export.
6. **💾 Saved Sessions:** LocalStorage session manager to review, load, or export historical interview rounds.

---

## Technical Stack & Architecture

- **Frontend Core:** Single-file HTML5, CSS3 with CSS variables and backdrop glassmorphism, Vanilla ES6+ JavaScript.
- **AI Engine:** Direct Anthropic Messages API client (`claude-3-haiku-20240307` / `claude-3-5-sonnet-20241022`) + Local Intelligent Simulation Fallback Engine.
- **Data Persistence & Graphics:** Custom inline SVG Radar Chart generator, SVG stroke-dashoffset animated dial, and browser `LocalStorage` session management.

---

## Verification & Usage

1. Open `defend_your_experience.html` in any modern web browser.
2. Explore the **🏠 Home Page** hero section and feature cards.
3. Click **🚀 Start New Defense Session** or select one of the built-in sample profiles (🎓 AI Student, 💻 Full-Stack Lead, 🚀 Startup Founder).
4. Click **Extract Claims** to review assertions and risk levels.
5. Click **Launch Skeptic Interrogation** to start question-by-question defense.
6. Respond via open text or MCQ pills while tracking the live Response Strength Analyzer and STAR framework metrics.
7. Inspect your 5-axis Radar Chart in **Analytics** and print your diagnostic report in **Defense Report**.
