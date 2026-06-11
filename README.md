# Graph-Based Anti-Money Laundering Detection and Explainable Risk Scoring

## Overview

Anti-Money Laundering (AML) is one of the most critical challenges in modern banking systems. Traditional transaction-level fraud detection models often fail to capture complex relationships between accounts involved in suspicious financial activities.

This project implements a graph-based AML detection pipeline that models banking transactions as a network of interconnected accounts. By combining graph analytics, community detection, anomaly detection, machine learning, and explainable AI, the system identifies high-risk accounts and provides interpretable risk assessments.

---

## Problem Statement

Financial institutions process millions of transactions daily. Detecting suspicious activity is difficult because money laundering often occurs through networks of accounts rather than isolated transactions.

This project aims to:

* Model transactions as a directed graph
* Identify suspicious account communities
* Detect anomalous account behavior
* Generate account-level risk scores
* Explain model predictions using SHAP

---

## Dataset

Dataset Used:

**IBM Transactions for Anti-Money Laundering (AML)**

Dataset contains:

* Transaction timestamp
* Sender bank and account
* Receiver bank and account
* Transaction amount
* Currency information
* Payment format
* Laundering label

For experimentation, a subset of approximately 1 million transactions was used.

---

## System Architecture

Transactions
↓
Graph Construction
↓
Community Detection (Louvain)
↓
Graph Feature Engineering
↓
Behavioral Feature Engineering
↓
Isolation Forest Anomaly Detection
↓
XGBoost Risk Scoring
↓
SHAP Explainability

---

## Methodology

### 1. Graph Construction

Each account is represented as a node.

Each transaction is represented as a directed edge between accounts.

The resulting transaction network captures the flow of money across the banking ecosystem.

---

### 2. Community Detection

The Louvain algorithm is applied to identify densely connected account clusters.

Generated features:

* Community ID
* Community Size

These features help detect coordinated laundering behavior.

---

### 3. Graph Feature Engineering

For each account, the following network metrics are calculated:

* In Degree
* Out Degree
* Total Degree
* PageRank
* Community Size

These features capture account connectivity and influence within the transaction network.

---

### 4. Behavioral Feature Engineering

Transaction-based features include:

* Total Amount Sent
* Average Amount Sent
* Maximum Amount Sent
* Transaction Count
* Total Amount Received
* Average Amount Received
* Maximum Amount Received

---

### 5. Anomaly Detection

Isolation Forest is used to identify accounts exhibiting unusual behavior patterns.

Generated outputs:

* Anomaly Score
* Anomaly Flag

---

### 6. Risk Scoring

An XGBoost classifier is trained using graph features, behavioral features, and anomaly scores.

Output:

* Account Risk Probability

---

### 7. Explainable AI

SHAP (SHapley Additive exPlanations) is used to explain model predictions and identify the key drivers behind high-risk accounts.

---

## Technologies Used

* Python
* Pandas
* NumPy
* NetworkX
* Python-Louvain
* Scikit-Learn
* XGBoost
* SHAP
* Matplotlib
* Seaborn

---

## Results

Dataset Scale:

* ~202,000 Accounts
* ~201,000 Transaction Edges

Model Performance:

* ROC-AUC: 0.778
* Recall on Suspicious Accounts: 35%

The model successfully combines graph structure and transaction behavior to identify suspicious accounts while maintaining explainability.

---

## Key Learnings

* Graph analytics provides valuable context beyond transaction-level analysis.
* Community structures can reveal coordinated laundering patterns.
* Anomaly detection is useful but insufficient on its own.
* Combining graph features with machine learning improves detection capability.
* Explainable AI is essential in financial risk systems.

---

## Future Improvements

* Graph Neural Networks (GCN / GraphSAGE)
* Node2Vec Graph Embeddings
* Temporal Transaction Analysis
* Real-Time Risk Scoring
* Streamlit Dashboard
* Multi-Hop Suspicious Path Detection

---

## Author

Ayush Ojha
NIT Rourkela
B.Tech Computer Science and Engineering

Project Focus:
Graph Analytics • Machine Learning • Financial Risk Intelligence • Explainable AI
