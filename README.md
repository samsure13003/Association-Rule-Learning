# Association-Rule-Learning
# 🛒 Market Basket Analysis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![Models](https://img.shields.io/badge/Models-2-blueviolet?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

Association rule mining on retail transaction data using the **Apriori** and **ECLAT** algorithms to discover frequently co-purchased product combinations.

---

## 📂 Project Structure

```
├── apriori.ipynb                    # Apriori algorithm implementation
├── eclat.ipynb                      # ECLAT algorithm implementation
└── Market_Basket_Optimisation.csv   # Transaction dataset (7,500 transactions)
```

---

## 📊 Dataset

**`Market_Basket_Optimisation.csv`**

- **7,501 transactions** from a retail store (one week of data)
- Each row represents a customer's basket — up to **20 items** per transaction
- No header row; items are stored as comma-separated values across columns
- Missing values (`NaN`) indicate that a transaction had fewer than 20 items

**Sample rows:**

| Item 1 | Item 2 | Item 3 | ... |
|--------|--------|--------|-----|
| shrimp | almonds | avocado | ... |
| burgers | meatballs | eggs | ... |
| chutney | | | ... |

---

## 🔍 Algorithms

### Apriori (`apriori.ipynb`)

Generates association rules with **Support**, **Confidence**, and **Lift** metrics.

| Parameter | Value |
|-----------|-------|
| `min_support` | 0.003 |
| `min_confidence` | 0.2 |
| `min_lift` | 3 |
| `min_length` | 2 |
| `max_length` | 2 |

**Output:** A ranked DataFrame of product-pair rules sorted by descending Lift, plus a scatter plot of Support vs. Confidence (coloured by Lift).

---

### ECLAT (`eclat.ipynb`)

Mines frequent itemsets using a depth-first, set-intersection approach — focusing on **Support** only.

| Parameter | Value |
|-----------|-------|
| `min_support` | 0.003 |
| `min_lift` | 3 |
| `min_length` | 2 |
| `max_length` | 2 |

**Output:** A ranked DataFrame of product pairs by descending Support, plus a horizontal bar chart of the top 10 associations.

---

## ⚙️ Installation

```bash
pip install apyori pandas numpy matplotlib seaborn
```

---

## 🚀 Usage

1. Clone this repository and place `Market_Basket_Optimisation.csv` in the project root.
2. Open either notebook in Jupyter:

```bash
jupyter notebook apriori.ipynb
# or
jupyter notebook eclat.ipynb
```

3. Run all cells. Results are displayed as sorted DataFrames and visualisation plots.

---

## 📈 Sample Results

Both notebooks output the **top 10 product-pair associations**. Example (Apriori):

| Left Hand Side | Right Hand Side | Support | Confidence | Lift |
|----------------|-----------------|---------|------------|------|
| light cream | chicken | 0.0045 | 0.29 | 4.84 |
| pasta | escalope | 0.0059 | 0.37 | 4.70 |
| ... | ... | ... | ... | ... |

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `apyori` | Apriori / ECLAT rule mining |
| `pandas` | Data loading and DataFrame output |
| `numpy` | Numerical utilities |
| `matplotlib` | Base plotting |
| `seaborn` | Statistical visualisations |

---

## 📖 Key Concepts

- **Support** — Fraction of transactions containing the itemset
- **Confidence** — Probability of buying item B given item A was bought
- **Lift** — How much more likely the pair is bought together vs. independently (lift > 1 = positive association)

---

## 📄 License

This project is for educational purposes.
