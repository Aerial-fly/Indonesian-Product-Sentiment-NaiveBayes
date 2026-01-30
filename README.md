# 🇮🇩 Product Review Sentiment Analysis (Indonesian)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Sastrawi](https://img.shields.io/badge/Stemmer-Sastrawi-green)
![Accuracy](https://img.shields.io/badge/Accuracy-93.82%25-brightgreen)

This project is a Machine Learning implementation to classify e-commerce product review sentiment (Positive/Negative).

This system is specifically designed to address the linguistic challenges of Indonesian, such as the use of non-standard words (slang), affixes, and negation contexts, which are often mispredicted by conventional models.

## 🌟 Key Features

This project has advantages over standard classification because it applies in-depth preprocessing techniques:

1. Negation Handling:

A smart algorithm that detects negation words ('tidak', 'tidak', 'gak').
* Combines negation words with the adjective after them (e.g., "tidak rusak" &rarr; `tidak_rusak`).
* Results: The model is able to distinguish "rusak" (Negative) from "tidak rusak" (Positive).

2. Context Bias Correction (Data Balancing):
* Addresses bias in ambiguous words such as **"Nyesel"**.
* In the original dataset, the word "nyesel" often has a positive connotation (*"Nyesel hanya membeli satu"*).
* Targeted Data Augmentation (Oversampling) was performed to teach the model that the word "sesal/nyesel" without negation is a negative sentiment.

3. Advanced Preprocessing:
* Slang Normalization: Converts "gk", "bgt", and "brg" into standard language.
* Stemming (Literary): Converts affixed words to their base words.
* TF-IDF Bigram: Uses the ngram_range=(1,2) feature to capture two-word patterns.

## 📊 Model Evaluation Results

The model was trained using the Multinomial Naive Bayes algorithm with an 80:20 data split.

| Metric | Score |
| :--- | :--- |
| Accuracy | 93.82% |
| Precision (Positive) | 99% |
| Recall (Positive) | 87% |

*Accuracy Calculation: (258 correct predictions / 275 total test data).*

### Confusion Matrix Insight:
The model demonstrates very stable performance with minimal prediction errors (False Positive/False Negative) thanks to the *Negation Handling* feature.

## 🛠️ Technologies Used

* **Python**: Main programming language.
* **Pandas**: Tabular data manipulation.
* **Sastrawi**: Indonesian-specific stemming library.
* **Scikit-Learn**: Implementation of Naive Bayes, TF-IDF, and metric evaluation.
* **Matplotlib/Seaborn**: Data visualization.

## 🚀 How to Run (Installation)

1. **Clone Repository:**
```bash
git clone [https://github.com/your-username/repo-name.git](https://github.com/your-username/repo-name.git)
```

2. **Install Library:**
Make sure the following libraries are installed:
```bash
pip install pandas scikit-learn Sastrawi matplotlib seaborn
```

3. **Run Notebook:**
Open the `.ipynb` file in Jupyter Notebook or Google Colab, then run each cell sequentially.

## 📝 Quick Demo

Here's an example of how the system handles ambiguous sentences:

| User Input | Preprocessing | Model Prediction |
| :--- | :--- | :--- |
| "The item arrived safely **undamaged**" | `... safe not_damaged` | ✅ **Positive** |
| "The item was damaged **really regretful**" | `... damaged really regretful` | ❌ **Negative** |
| "**No regrets** buying here" | `... no_regrets_buying ...` | ✅ **Positive** |

---
**Created by [Your Name/Your Group]**
