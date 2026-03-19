# 🛒 Market Basket Analysis — Apriori Algorithm

A Python implementation of the **Apriori algorithm** for association rule mining on a market basket dataset. Discovers frequent item sets and generates association rules to uncover purchasing patterns.

---

## 📋 Overview

This project applies the **Apriori algorithm** to transaction data to find hidden relationships between products. By mining association rules, retailers can better understand what items customers tend to buy together, enabling smarter product placement, promotions, and recommendations.

---

## 📁 Files

| File | Description |
|------|-------------|
| `apriori.ipynb` | Main Jupyter notebook with full pipeline |
| `Market_Basket_Optimisation.csv` | Transaction dataset (one row per transaction) |
| `Mall_Customers.csv` | Customer metadata (CustomerID, Genre, Age, Annual Income, Spending Score) |

---

## 🔗 Association Rules Discovered

The model surfaced **9 significant rules** ranked by descending lift:

| Left Hand Side | Right Hand Side | Support | Confidence | Lift |
|---|---|---|---|---|
| fromage blanc | honey | 0.0033 | 0.245 | **5.16** |
| light cream | chicken | 0.0045 | 0.291 | **4.84** |
| pasta | escalope | 0.0059 | 0.373 | **4.70** |
| pasta | shrimp | 0.0051 | 0.322 | **4.51** |
| whole wheat pasta | olive oil | 0.0080 | 0.271 | **4.12** |
| tomato sauce | ground beef | 0.0053 | 0.377 | **3.84** |
| mushroom cream sauce | escalope | 0.0057 | 0.301 | **3.79** |
| herb & pepper | ground beef | 0.0160 | 0.323 | **3.29** |
| light cream | olive oil | 0.0032 | 0.205 | **3.11** |

> **Lift > 1** indicates a positive association — customers buying the left-hand item are more likely to also buy the right-hand item than by chance.

---


## 🚀 Getting Started

### Prerequisites

```bash
pip install numpy pandas matplotlib seaborn apyori
```

### Run the Notebook

1. Clone this repository
2. Place `Market_Basket_Optimisation.csv` in the project directory
3. Open `apriori.ipynb` in Jupyter Notebook or Google Colab
4. Run all cells

---

## 🧠 How It Works

### 1. Data Preprocessing
Transaction data is loaded from CSV (no header) and converted into a list of lists — one inner list per transaction, with `NaN` values removed.

```python
transactions = []
for i in range(0, dataset.shape[0]):
    transaction = [str(dataset.values[i, j]) for j in range(0, dataset.shape[1])
                   if str(dataset.values[i, j]) != 'nan']
    transactions.append(transaction)
```

### 2. Training the Apriori Model

```python
from apyori import apriori

rules = apriori(
    transactions=transactions,
    min_support=0.003,
    min_confidence=0.2,
    min_lift=3,
    min_length=2,
    max_length=2
)
```

| Parameter | Value | Meaning |
|---|---|---|
| `min_support` | 0.003 | Item set appears in ≥ 0.3% of transactions |
| `min_confidence` | 0.2 | Rule is correct ≥ 20% of the time |
| `min_lift` | 3 | Association is ≥ 3× better than random |
| `min/max_length` | 2 | Only pairwise rules |

### 3. Results & Visualisation

Rules are parsed into a clean Pandas DataFrame and sorted by **lift** (highest first). A scatter plot visualises **Support vs. Confidence**, with point size and color encoding the **Lift** value.

---

## 📊 Visualisation

The scatter plot below shows all discovered rules. Larger, brighter points indicate stronger associations (higher lift).

> *Support vs. Confidence (coloured by Lift)*

---

## 📌 Key Concepts

- **Support**: How frequently the item set appears in the dataset
- **Confidence**: How often the rule is found to be correct
- **Lift**: How much more likely the rule is compared to random chance (lift > 1 = positive association)

---

## 🛠 Tech Stack

- Python 3
- [apyori](https://pypi.org/project/apyori/) — Apriori implementation
- Pandas, NumPy — Data manipulation
- Matplotlib, Seaborn — Visualisation
- Jupyter Notebook / Google Colab

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
