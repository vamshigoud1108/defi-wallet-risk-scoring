# DeFi Wallet Risk Scoring

This project analyzes on-chain transaction data for Ethereum wallets to assign a **risk score between 0–1000**. The goal is to understand wallet behavior and evaluate risk levels using historical transaction data from the Ethereum blockchain.

## 🚀 Problem Statement

Given a list of Ethereum wallet addresses, the task is to:
1. **Fetch transaction history** for each wallet (using Covalent API).
2. **Engineer features** from the transaction data that indicate wallet activity, value movement, and gas usage.
3. **Assign a risk score** to each wallet based on its behavior using a rule-based scoring model.

## 📁 Dataset

- A CSV file containing wallet addresses.
- On-chain transaction data fetched using the **Covalent API** for each wallet.

## 🔧 Methodology

### 1. Data Collection
- Used CovalentHQ's API to fetch transaction data (`transactions_v2` endpoint) for each wallet address.

### 2. Feature Engineering
For each wallet, we computed:
- Number of transactions
- Total value sent and received
- Total gas spent
- Average transaction value
- Number of active days
- Duration between first and last transaction

### 3. Scoring Logic
- All features were normalized using **MinMax Scaling**.
- A **rule-based weighted score** was calculated using:


## ✅ Output

Final CSV file: `wallet_credit_scores.csv`
| wallet          | credit_score |
|------------------|--------------|
| 0xabc...123      | 735.21       |

- Top wallets are printed in the notebook based on highest credit scores.

## 🧠 Tools Used

- Python
- Pandas
- Requests
- Scikit-learn (MinMaxScaler)

## 📘 Notebook

- `DeFi_Wallet_Risk_Scoring.ipynb`

## 📌 Notes

- The current implementation uses Covalent API instead of Compound V2/V3-specific APIs.
- This scoring logic can be extended to include protocol-specific actions (e.g., borrow, repay, liquidation) for more precise DeFi risk analysis.
