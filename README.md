# Navigating SemEval: A Comparative Study of Feature Engineering in SVM and BERT for Relation Extraction

This repository contains the implementation and analysis of two distinct approaches to solving the relation classification problem on the SemEval-2010 Task 8 dataset. Specifically, we compare a traditional Support Vector Machine (SVM) model with manual feature engineering against a pre-trained transformer-based BERT model that relies on contextual embeddings.

---

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Approaches](#approaches)
  - [SVM-Based Model](#1-svm-based-model)
  - [BERT-Based Model](#2-bert-based-model)
- [Performance Summary](#performance-summary)

---

## Overview

Relation extraction is a key NLP task involving the identification of semantic relationships between pairs of entities in text. The SemEval-2010 Task 8 dataset provides labeled examples of entity pairs and their relations across nine distinct categories (and an 'Other' class).

This project explores two contrasting methodologies:
1. **SVM-based approach with manual feature engineering**
2. **BERT-based fine-tuned model leveraging deep contextual embeddings**

---

## Project Structure
```
project-repository/
│
├── Text Mining Approach 1 (SVM Technique).ipynb
├── Text Mining Approach 2 (BERT Technique).ipynb
├── paper.pdf
├── requirements.txt
└── README.md
```
---

## Approaches

### 1. SVM-Based Model

The first approach involves a traditional machine learning pipeline:

- **Preprocessing:**
  - Removal of XML tags.
  - Tokenization and normalization.
  - POS tagging and dependency parsing.

- **Feature Engineering:**
  - **Word Pair Features:** Specific lexical patterns between entity pairs.
  - **POS Tag Features:** Capturing syntactic patterns.
  - **Dependency Path Features:** Shortest dependency path between entities.
  - **Entity Context Features:** Words around entities.
  - **Distance Features:** Relative distance between entities.
  
- **Model:**
  - Multi-class **Support Vector Machine (SVM)** classifier.

---

### 2. BERT-Based Model

The second approach leverages the power of transformers:

- **Preprocessing:**
  - Special tokens `<e1>` and `<e2>` inserted to mark entities.
  - Tokenization compatible with BERT (WordPiece tokenizer).

- **Model:**
  - **Pre-trained BERT-base model**.
  - Fine-tuned using cross-entropy loss.
  - Last hidden state corresponding to `[CLS]` token used for classification.

---

## Performance Summary

| Approach          | F1-Score (Overall) | F1-Score (Excluding 'Other') |
|-------------------|-------------------|------------------------------|
| SVM-Based Model   | 76%               | 86%                          |
| BERT-Based Model  | 77%               | 87%                          |

**Note:** The BERT model exhibits marginally better overall performance, while the SVM model shows strong results due to carefully crafted feature sets.

---
