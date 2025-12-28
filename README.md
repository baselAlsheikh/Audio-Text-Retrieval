# Option 2 – Robust Information Retrieval with ASR Errors using Phoneme 3-grams

## Overview
This project implements **Option 2** of the assignment:  
**searching over combined audio and text representations** in the presence of **Automatic Speech Recognition (ASR) errors**.

ASR systems often produce transcription errors (e.g., substitutions, misspellings, word splitting), which cause traditional exact-text search to fail.  
To address this problem, we use **phoneme-based indexing** and **cosine similarity**, inspired by classic Information Retrieval techniques for robustness to noise.

---

## Goal
The goal of this assignment is to demonstrate how **phoneme 3-grams** can be used to:
- Represent text documents derived from speech
- Remain robust to ASR-related errors
- Retrieve relevant documents using **cosine similarity**

---

## Data
The project uses **synthetic data** created for demonstration purposes:

- **2 clean text documents**
- **2 ASR-like documents** containing recognition errors
- **1 clean query** containing 3 words:

ASR errors are introduced **only in the documents**, not in the query, to simulate real-world search scenarios.

---

## Methodology

### 1. Phoneme Conversion
- Text is converted into **phoneme sequences** using the **CMU Pronouncing Dictionary (CMUdict)**.
- If a word is not found in the dictionary, a character-based fallback is used.

### 2. Phoneme 3-gram Extraction
- Each document is decomposed into overlapping **phoneme trigrams (3-grams)**.
- This allows partial matching even when words are misspelled or misrecognized.

### 3. Vectorization
- Documents and query are represented using **TF-IDF vectors** over phoneme 3-grams.

### 4. Similarity Measurement
- **Cosine similarity** is computed between the query vector and each document vector.
- Documents are ranked according to similarity score.

### 5. Visualization
- Similarity scores are displayed both as:
- A ranked table
- A bar plot visualization

---

## Results
- The most relevant clean document receives the **highest similarity score**.
- ASR documents with recognition errors still receive **high similarity**, thanks to phoneme overlap.
- The unrelated document receives a **very low score**.

This demonstrates that phoneme-based n-gram indexing is **robust to ASR noise**.

---

## Files
- `Option2_Phoneme_3Gram_ASR_Retrieval.ipynb` – Main implementation notebook
- `docs/` – Folder containing the generated text documents
- `README.md` – Project description (this file)
- `video.mp4` – Assignment presentation video (submitted separately)

---

## Requirements
- Python 3.x
- Libraries:
- numpy
- pandas
- scikit-learn
- matplotlib
- nltk

The CMU Pronouncing Dictionary (`cmudict`) is automatically downloaded via NLTK if not already installed.

---

## How to Run
1. Open the notebook:
2. Run all cells in order.
3. Observe the similarity scores and visualization.

---

## Conclusion
This project shows how **classic Information Retrieval techniques**, combined with **phoneme-level representations**, can effectively handle ASR transcription errors and enable robust search over speech-derived text.
