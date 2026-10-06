# Singlish Hate Speech Detection

Detecting hate speech in code-mixed Romanized Sinhala (Singlish) social media text using transformer-based models.

Course: IT41043 — Intelligent Systems 
Institution: Horizon Campus, Faculty of IT  
Academic Year: 2026

---

## 📌 Project Overview

This project investigates whether transformer-based models (SinBERT, XLM-RoBERTa) can outperform traditional machine learning classifiers (Naïve Bayes, SVM, Logistic Regression, Random Forest) in detecting hate speech in Singlish text.

Research Gap: Existing Sinhala hate speech detection systems operate only on formal Sinhala Unicode text and fail to generalise to the dominant informal register used on Sri Lankan social media: code-mixed Romanized Sinhala (Singlish).

---

## 📊 Dataset

| Property | Value |
|----------|-------|
| Source | YouTube comments (YouTube Data API v3) |
| Raw comments collected | 3,578 |
| Final annotated corpus | 2,500 |
| Hate (label 1) | 1,305 (52.2%) |
| Not Hate (label 0) | 1,195 (47.8%) |
| Annotation | Manual, by two annotators |
| File | `singlish_comments_2500_labeled.xlsx` |

---

## 🏗️ System Architecture

```
[Data Collection] → [Preprocessing] → [Feature Extraction]
    → [Model Inference] → [Output Interpretation]

Data Collection     : YouTube Data API v3 → 3,578 raw comments
Preprocessing       : Cleaning & filtering → 2,500 comments
Feature Extraction  : TF-IDF (baseline) OR Transformer tokenizer (proposed)
Model Inference     : NB / SVM / LR / RF  OR  SinBERT / XLM-RoBERTa
Output              : Hate (1) / Not Hate (0)
```

---

## 🧪 Models Evaluated

### Baseline (TF-IDF + Traditional ML)
- Multinomial Naïve Bayes
- Linear SVM
- Logistic Regression
- Random Forest

### Proposed (Transformers)
- SinBERT-small (`NLPC-UOM/SinBERT-small`)
- XLM-RoBERTa-base (`xlm-roberta-base`)

---

## 📈 Preliminary Results

### Baseline (5-fold CV F1)

| Model | Accuracy | F1-Score | CV F1 (mean ± std) |
|-------|----------|----------|---------------------|
| Naive Bayes | 0.8120 | 0.8115 | 0.8462 ± 0.0085 |
| Logistic Regression | 0.8120 | 0.8113 | 0.8403 ± 0.0152 |
| SVM | 0.8040 | 0.8040 | 0.8324 ± 0.0081 |
| Random Forest | 0.7900 | 0.7894 | 0.8134 ± 0.0095 |

### SinBERT-small (3 epochs)

| Epoch | Train Loss | Val Loss | Accuracy | F1 |
|-------|------------|----------|----------|-----|
| 1 | 0.6963 | 0.6979 | 0.5840 | 0.4853 |
| 2 | 0.5897 | 0.6049 | 0.6560 | 0.6211 |
| 3 | 0.5292 | 0.5397 | 0.7380 | 0.7357 |

Note: SinBERT-small underperformed the baseline. Analysis and failure discussion are provided in the Milestone 2 report. XLM-RoBERTa experiments are ongoing.

---

## 🚀 Reproduction Instructions

### 1. Clone the repository
```bash
git clone https:///github.com/Devindihansini/singlish-hate-speech-detection.git
cd singlish-hate-speech-detection
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
Open `singlish_hate_speech_detection.ipynb` in Google Colab or Jupyter, upload `singlish_comments_2500_labeled.xlsx`, and run all cells.

### 4. Hardware requirements
- GPU recommended for transformer fine-tuning (Google Colab T4 is sufficient)
- Training time: ~90 seconds per epoch for SinBERT-small on T4 GPU

---

## 📁 Repository Structure

```
singlish-hate-speech-detection/
├── README.md
├── requirements.txt
├── .gitignore
├── singlish_hate_speech_detection.ipynb    # Main notebook (Colab)
├── preprocessing.py                        # Data cleaning scripts
├── baseline_results.csv                    # Saved baseline outputs
└── singlish_comments_2500_labeled.xlsx    # Annotated dataset
```


---

## 🔒 Ethical Statement

All data were collected from publicly available YouTube comments. No personally identifiable information was retained. `@mentions` were replaced with `@user`. The dataset contains offensive language and is intended strictly for academic research on hate speech detection.

---

P. G. A. H. Devindi 
ITBIN-2211-0124 
Faculty of Information Technology, Horizon Campus