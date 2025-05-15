# Association Rule Mining on Persian Text Data

This project applies **Association Rule Mining (ARM)** to Persian textual data to discover meaningful patterns of word co-occurrence within documents. By treating each document as a set of stemmed words, the project extracts association rules that reflect linguistic and topical relationships.

---

## Project Overview

- **Text Preprocessing:** Uses *Parsivar* for normalization, tokenization, and stemming of Persian sentences.
- **Transaction Creation:** Converts each sentence into a set of unique stemmed tokens to form transactions for ARM.
- **Frequent Itemset Mining:** Employs the Apriori algorithm via *mlxtend* to find frequent word combinations.
- **Rule Generation:** Extracts association rules with varying minimum support and confidence thresholds.
- **Parameter Tuning:** Analyzes different `min_support` and `min_confidence` values to select thresholds that yield meaningful and statistically significant rules.
- **Evaluation:** Uses a confusion matrix and classification report to assess the predictive power of extracted rules on unseen test data.
- **Visualization:** Displays the relationship between support, confidence, and the number of generated rules.

---

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/mohammad-majoony/data-mining-ARM.git
   cd data-mining-ARM

2. Install required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

1. Prepare your dataset:

   * `input.txt`: Contains Persian sentences (one per line) for training ARM.
   * `test.txt`: Contains Persian sentences for evaluating the extracted rules.

2. Run the notebook or script to:

   * Preprocess text data.
   * Generate frequent itemsets and association rules.
   * Tune and select appropriate support and confidence thresholds.
   * Evaluate rules on test data using confusion matrix metrics.

---

## Selecting Support and Confidence

Through experimentation, the following values produced robust rules balancing quantity and quality:

* **Minimum Support:** 0.5 (patterns appear in at least 50% of documents)
* **Minimum Confidence:** 0.6 (consequents appear in at least 60% of transactions containing antecedents)

Lower thresholds resulted in many low-confidence or noisy rules, while higher thresholds missed valuable patterns.

---

## Evaluation: Confusion Matrix and Classification Report

The performance of rules is evaluated by comparing the presence of antecedents and consequents in test sentences:

|                               | Predicted Consequent Present | Predicted Consequent Absent |
| ----------------------------- | ---------------------------- | --------------------------- |
| **Actual Consequent Present** | True Positive (TP)           | False Negative (FN)         |
| **Actual Consequent Absent**  | False Positive (FP)          | True Negative (TN)          |

Key metrics derived from this matrix include:

* **Accuracy**
* **Precision**
* **Recall**
* **F1-Score**

These metrics help verify the reliability and usefulness of the generated association rules.

---

## Example Rules

| Antecedent     | Consequent       | Support | Confidence | Lift |
| -------------- | ---------------- | ------- | ---------- | ---- |
| {تهران}        | {امتحانات}       | 0.7     | 0.70       | 1.00 |
| {برای, دانشجو} | {دانشگاه, تهران} | 0.5     | 1.00       | 1.00 |

---
