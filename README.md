# Search-Engine-Project
This project builds a search engine over job postings and employment-related discussions to compare classical keyword-based retrieval with modern semantic search. Using a large text corpus, we construct BM25 and BERT-based FAISS indexes and evaluate indexing behavior, query performance, and ranking quality.

```markdown
# Job & Employment Search Engine (Course Project)

This repository contains the code and data pipeline for a course project focused on building and comparing **classical keyword-based retrieval** and **modern semantic retrieval** methods over a large corpus of job postings and employment-related discussions.

The primary goal is to study differences in indexing behavior, query performance, and ranking quality between:
- **Keyword-based search** using an inverted index (PyLucene / BM25)
- **Semantic search** using dense embeddings (BERT) and FAISS

This README reflects the **initial, simplified version** of the project. The pipeline and features will be extended over time.

---

## Project Overview

We collect and process data from multiple sources:
- **Job postings** (structured text)
- **Employment-related Reddit discussions** (posts + comments)

The data pipeline follows a clear separation of concerns:
1. Data collection (crawling)
2. Cleaning and normalization
3. Deduplication
4. Canonical document storage
5. Index construction (keyword + semantic)

Both retrieval systems operate on the **same cleaned corpus** to ensure a fair comparison.

---

## Repository Structure (Current)

```

project/
│── data/
│   ├── raw/            # Raw, unmodified crawled data
│   ├── processed/      # Cleaned and deduplicated documents
│   └── indexes/        # Lucene and FAISS indexes
│
│── src/
│   ├── crawl/          # Data collection scripts
│   ├── preprocess/    # Cleaning and deduplication
│   ├── index/          # Index construction
│   └── utils/          # Shared helpers
│
│── main.py             # Pipeline entry point
│── requirements.txt
│── README.md

```

---

## Data Pipeline (Simple Version)

```

Raw Data
↓
Cleaning & Normalization
↓
Deduplication
↓
Canonical Document Store (JSONL)
↓
Indexing
├── Keyword Index (PyLucene)
└── Semantic Index (BERT + FAISS)

````

The processed dataset is stored as a **JSONL file** and serves as the single source of truth for all indexing and evaluation steps.

---

## Document Format

All documents (job postings and Reddit content) are normalized into a shared schema:

```json
{
  "doc_id": "...",
  "source": "reddit | job",
  "title": "...",
  "text": "...",
  "metadata": { ... }
}
````

This allows both retrieval systems to index heterogeneous data consistently.

---

## How to Run (Initial Pipeline)

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Run the pipeline:

```bash
python main.py
```

At this stage, the pipeline:

* Collects raw data (if enabled)
* Cleans and deduplicates documents
* Writes a processed document file
* Builds keyword and semantic indexes

---

## Current Status

* ✅ Basic data pipeline implemented
* ✅ Cleaning and deduplication
* ✅ Canonical document format
* ⏳ Indexing improvements (chunking, tuning)
* ⏳ Query evaluation and metrics
* ⏳ Incremental indexing and scaling

---

## Notes

* Raw data is **never overwritten**
* The pipeline is designed to be **re-runnable and deterministic**
* This README will be expanded as the project evolves

---

## Course Context

This project is developed as part of a **Search Engine course assignment** and emphasizes:

* Information retrieval fundamentals
* Fair experimental comparison
* Clean, reproducible data pipelines

```

---

If you want, I can next:
- Tighten this to **<1 page** if your professor prefers brevity
- Add a **pipeline diagram (ASCII or figure-ready)**
- Rewrite it once the project reaches “final submission” polish
- Align it explicitly with **grading rubric language**

Just tell me.
```
