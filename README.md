<div align="center">

# 📚 Smart Document Knowledge Assistant

**Ask your notes anything. Every answer shows the exact passage it came from.**

A polished, single-file front end for a Retrieval-Augmented Generation (RAG) study assistant, built for first-year students and researchers who are tired of `Ctrl+F`.

![HTML5](https://img.shields.io/badge/HTML5-single_file-E34F26?logo=html5&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-CDN-06B6D4?logo=tailwindcss&logoColor=white)
![JavaScript](https://img.shields.io/badge/Vanilla_JS-no_build-F7DF1E?logo=javascript&logoColor=black)
![Status](https://img.shields.io/badge/RAG_engine-simulated-10B981)

[**Live demo**](#-live-demo) · [**Features**](#-features) · [**How it works**](#-how-the-simulation-works) · [**Roadmap**](#-roadmap)

<!-- Add a screenshot or GIF of the dashboard here -->
<!-- ![Dashboard preview](docs/preview.png) -->

</div>

---

## 🎯 The problem

Students deal with piles of unstructured files: lecture PDFs, lab manuals, research articles and text notes. Keyword search can't follow a concept across synonyms or across pages, so finding one answer means opening five documents.

## 💡 The idea

Upload your documents, ask a question in plain language, and get an answer **grounded strictly in your files**. The assistant retrieves the 3 to 5 most relevant chunks, answers from them, and shows each source next to the answer so you can verify it.

---

## ✨ Features

### Knowledge base (left panel)
- **Drag-and-drop upload** for `.pdf` and `.txt`, with an animated hover state
- **File manager** with type badges, size, token count, live indexing progress, and delete
- **RAG metrics:** animated chunk counter, embedding model (`text-embedding-3`), and search threshold (Top 5)
- **One-click sample files** so the demo works without any uploads

### Chat and verification (right panel)
- **Streaming answers** with a visible pipeline: *Searching vector index → Extracting top N chunks → Generating response*
- **Inline citations** such as `[Source 1]` in every answer
- **Source cards** showing file name, page, a **match-score bar** (e.g. `94% match`), and the retrieved text with your query terms highlighted
- **Citation hover:** hover a badge and its source card opens and lights up
- **Prompt chips:** *Summarize page 4*, *Extract key formulas*, *Compare lab manual vs lecture*
- **Honest fallback:** if nothing relevant is found, it says so instead of guessing

### Design
- Deep slate canvas `#0F172A`, indigo accent `#6366F1`, emerald status `#10B981`
- Glassmorphism panels with sub-pixel `white/10` borders and backdrop blur
- Glowing gradient focus ring on the input, press and hover feedback on every button
- Custom inline SVG icons (no icon font, no broken images)
- **Plus Jakarta Sans** for UI text and **JetBrains Mono** for technical snippets
- Responsive layout (two columns on desktop, stacked on mobile), visible keyboard focus, and `prefers-reduced-motion` support

---

## 🚀 Quick start

No install, no build step.

```bash
git clone https://github.com/<your-username>/smart-document-assistant.git
cd smart-document-assistant
open knowledge-assistant.html     # or just double-click the file
```

You need an internet connection the first time, because Tailwind and the Google Fonts load from a CDN.

### Try it in 30 seconds
1. A sample lecture file is already indexed. Click a sample button to add the lab manual or the calculus notes.
2. Click **Extract key formulas**, or type *"What is the energy of a particle in a box?"*
3. Hover `[Source 1]` in the answer to see the exact passage it came from.
4. Drop in your own `.txt` file and ask about it.

---

## 🧠 How the simulation works

This front end runs entirely in the browser. It imitates a real RAG pipeline so the experience can be designed and demoed without a server or API key.

| Step | In the demo | In a real backend |
|---|---|---|
| **Ingest** | `.txt` files are read and split into ~380-character chunks | Parse PDFs and text, then split into overlapping chunks |
| **Embed** | Not used | `text-embedding-3` vectors stored in a vector index |
| **Retrieve** | Word-overlap scoring over chunk text, file name and page; top 4 kept | Cosine similarity search for the top 3 to 5 chunks |
| **Generate** | Answer composed from the retrieved passages and streamed word by word | Chunks and question sent to an LLM API with a grounding prompt |
| **Cite** | Source cards with score, page, and highlighted text | Same, using real similarity scores and page metadata |

> **Note:** Uploaded `.pdf` files are indexed by size only in this demo. Real PDF text extraction belongs in the backend.

---

## 🗂 Project structure

```
.
├── knowledge-assistant.html   # the whole app: markup, styles, and logic
└── README.md
```

---

## 🛣 Roadmap

- [ ] Connect to a Python backend (Streamlit or FastAPI) for real PDF parsing
- [ ] Real embeddings and a vector store (FAISS or Chroma)
- [ ] LLM API integration with a "answer only from the context" prompt
- [ ] Multi-turn memory for follow-up questions
- [ ] Click a source card to jump to the page in a PDF viewer
- [ ] Export a chat as study notes

---

## 🧰 Built with

HTML5 · Tailwind CSS (CDN) · Vanilla JavaScript · Google Fonts (Plus Jakarta Sans, JetBrains Mono) · Hand-written SVG icons

---

## 📄 License

Released under the [MIT License](LICENSE). Replace this section if your club or institution requires a different one.

<div align="center">

Made for students who would rather understand their notes than search them.

</div>
