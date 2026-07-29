# 🔍 RAG-FactCheck

An NLP-based fact-checking system that combines **Retrieval-Augmented Generation (RAG)** with transformer models to verify claims against evidence — built and evaluated on the **FEVER** dataset.

---

## 📌 Overview

RAG-FactCheck takes a claim as input, retrieves relevant supporting/refuting evidence from a knowledge base, and classifies the claim as **SUPPORTED**, **REFUTED**, or **NOT ENOUGH INFO** — mimicking how human fact-checkers cross-reference sources before making a verdict.

The system achieved a **peak validation accuracy of 84.70%** on the FEVER dataset.

---

## 🧠 How It Works

1. **Claim Input** — A user-provided claim is passed into the pipeline
2. **Dense Retrieval** — Relevant evidence passages are retrieved using **SentenceTransformers** embeddings indexed with **FAISS**
3. **Evidence Re-ranking** — Retrieved passages are filtered/ranked for relevance
4. **Claim Verification** — **BERT** is used to classify the claim against retrieved evidence
5. **Generation (RAG)** — **T5** is used to generate human-readable justifications/summaries for the verdict

---

## 🛠️ Tech Stack

| Component            | Tool/Library                  |
|-----------------------|--------------------------------|
| Claim Verification    | BERT                          |
| Text Generation        | T5                             |
| Dense Retrieval        | SentenceTransformers            |
| Vector Search          | FAISS                          |
| Dataset                | FEVER (Fact Extraction and VERification) |
| Language               | Python                         |

---

## 📊 Results

| Metric                  | Score   |
|--------------------------|---------|
| Peak Validation Accuracy | 84.70%  |

*(Additional metrics such as F1-score and precision/recall are documented in the full project report.)*

---

## 📂 Project Structure

```
rag-factcheck/
├── data/                   # FEVER dataset (train/val/test splits)
├── retrieval/              # SentenceTransformers + FAISS indexing & retrieval logic
├── verification/           # BERT-based claim classification
├── generation/             # T5-based justification generation
├── notebooks/              # Experiment notebooks
├── report/                 # Full LaTeX project report
└── README.md
```

---

## ⚡ Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/<your-username>/rag-factcheck.git
cd rag-factcheck
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the FEVER dataset
Instructions for downloading and preprocessing FEVER are in `data/README.md`.

### 4. Build the FAISS index
```bash
python retrieval/build_index.py
```

### 5. Run fact-checking on a sample claim
```bash
python main.py --claim "The Eiffel Tower is located in Berlin."
```


## 🎯 Future Improvements

- [ ] Expand retrieval corpus beyond FEVER's Wikipedia-based evidence
- [ ] Experiment with larger/more recent LLMs for generation
- [ ] Add a web-based UI for interactive fact-checking
- [ ] Improve evidence re-ranking with cross-encoder models

---

## 📜 License

Academic project, developed for educational and research purposes.
