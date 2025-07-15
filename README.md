# DeFi Credit Score Analysis

This project analyzes Ethereum wallet transaction data to generate a decentralized credit score based on user behavior in DeFi protocols.

## 📁 Dataset

- `user-wallet-transactions.json`  
  Contains on-chain activity for multiple wallets, such as deposits, borrows, repayments, and liquidations.

## 📊 Objective

To compute a meaningful credit score for each wallet, reflecting responsible behavior such as:
- Regular repayments
- Limited borrowing
- Avoiding liquidations
- Diversified actions

## 📌 Methodology

1. **Data Preprocessing**  
   - Extract amounts in USD
   - Identify action types: deposit, borrow, repay, liquidationcall

2. **Feature Engineering**  
   - Total deposited, borrowed, repaid
   - Liquidation count
   - Action diversity score

3. **Scoring Formula**  
   ```
   raw_score = deposits + repays + 500×diversity - 0.5×borrows - 200×liquidations
   ```

4. **Normalization**  
   - Min-Max scaled to 0–1000 for interpretability

5. **Visualization**  
   - Histogram showing the credit score distribution across wallets

## 📂 Output

- `credit_scores.csv` — Final scores per wallet
- `figs/score_hist.png` — Score distribution chart

## 📦 Requirements

See `requirements.txt`

## 🛠️ How to Run

```bash
pip install -r requirements.txt
jupyter notebook
```

Then open and run `DeFi_Credit_Score_Analysis.ipynb`.
````

---

### ✅ 2  requirements

```
pandas
numpy
scikit-learn
matplotlib
seaborn
```

---

### ✅ 3. `DeFi_Credit_Score_Analysis.ipynb` – Analysis Outline

Below is a description of what's included in the notebook, section by section. You don’t need to copy this into GitHub, just make sure the notebook reflects this:

#### 🔹 Phase 1: Introduction

* Project context and goal

#### 🔹 Phase 2: Load & Explore Dataset

* Load JSON file
* Convert to DataFrame
* Inspect structure, sample records

#### 🔹 Phase 3: Feature Engineering

* Extract `amountUSD`
* Group by wallet
* Calculate deposit, borrow, repay, liquidation count, diversity

#### 🔹 Phase 4: Scoring

* Apply formula:

  ```
  score = deposits + repays + 500×diversity - 0.5×borrows - 200×liquidations
  ```
* Normalize with MinMaxScaler

#### 🔹 Phase 5: Visualization

* Histogram of credit scores


#### 🔹 Phase 6: Export Results

```python
final_scores.to_csv("credit_scores.csv", index=False)
