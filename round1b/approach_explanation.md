# Round 1B – Approach Explanation

## 🧠 Objective
Build an intelligent document reader that extracts and ranks the most relevant sections from multiple PDFs for a given persona and task.

## 👤 Persona Modeling
The persona is parsed as a structured JSON. We perform keyword and intent extraction using TF-IDF and custom heuristics to understand key interests (e.g., "R&D", "revenue").

## 📄 Section Relevance Extraction
- Each PDF is first pre-processed using PyMuPDF to detect sections and subheadings.
- Sections are scored based on:
  - Semantic similarity to persona goals using sentence embeddings
  - Frequency of persona-relevant terms
  - Positional importance in document (e.g., executive summary, conclusions)

## 🔍 Sub-Section Summarization
- Relevant sections are further broken down to paragraph level.
- Summarization is done using extractive techniques like TextRank.

## ⚙️ Offline & Lightweight
- CPU only
- No external API calls
- Model size < 1GB using DistilBERT or SentenceTransformer (optional)

## 📦 Output
A JSON file with ranked sections and refined sub-sections.
