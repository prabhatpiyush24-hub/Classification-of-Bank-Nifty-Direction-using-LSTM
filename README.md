# Classification-of-Bank-Nifty-Direction-using-LSTM
📌 Project Overview

This project focuses on applying deep learning (LSTM – Long Short-Term Memory networks) to a real-world financial analytics problem:
👉 Classifying the next-day directional movement of the Bank Nifty index (Up/Down).

Instead of attempting unrealistic price forecasting, the project is framed as a binary classification problem, which is widely adopted in quantitative finance research and trading system design.

The complete pipeline includes:

Financial data acquisition

Feature engineering based on market theory

Sequence modeling using LSTM

Out-of-sample evaluation

Probabilistic interpretation of market direction

🎯 Objective

To build an LSTM-based classification model that learns from historical financial market behavior and outputs the probability of upward movement in Bank Nifty for the next trading day.

📊 Data Description

Source: Yahoo Finance (via yfinance API)
Time period: January 2012 – December 2024
Frequency: Daily
Total observations: ~2,800 trading days

Instruments used:
Ticker	Role
^NSEBANK	Target index (Bank Nifty)
^NSEI	Domestic market trend
^INDIAVIX	Market volatility / fear index
^GSPC	Global market sentiment

This multi-index setup allows the model to learn from domestic trends, volatility conditions, and global cues.

🛠 Feature Engineering

Raw prices were transformed into financial indicators to extract meaningful structure:

1. Returns & Momentum

Daily returns of Bank Nifty, NIFTY 50, S&P 500, India VIX

5-day S&P 500 returns

2. Trend Indicators

10-day and 20-day moving averages

Price gaps from moving averages

3. Volatility Measures

10-day rolling volatility of Bank Nifty

India VIX level and change

Total engineered features: 10

These features capture momentum, trend strength, volatility regimes, and global influence.

🧠 Target Variable

The target is defined as:

1 (Up) → Bank Nifty closes higher on the next trading day

0 (Down/Flat) → Bank Nifty closes lower or remains flat

This formulation converts the task into a supervised binary classification problem.

🤖 Model Architecture – LSTM

The project uses a Long Short-Term Memory (LSTM) neural network, a specialized form of Recurrent Neural Network designed for time-series and sequential data.

Input Structure:

Each prediction uses:

👉 20 trading days × 10 features

Model design:

LSTM layer (64 units)

Dropout layer (20%)

Dense layer (32 units)

Output sigmoid neuron → probability of upward movement

Training parameters:

Epochs: 15

Batch size: 32

Train-test split: 80% / 20% (time-based)

📈 Model Evaluation

The model was evaluated on out-of-sample test data using:

Accuracy score

Confusion matrix

Classification report

Probability-based prediction analysis

Learning curves (loss & accuracy)

Key findings:

Test accuracy ≈ 48–55% across runs

Better performance in identifying upward movements

Difficulty in predicting sudden downside movements

Probabilities clustered near 0.50, reflecting market efficiency

Interpretation:

The results confirm that:

Short-term markets are weakly predictable but not random

Financial time series contain limited, unstable patterns

Deep learning models are more suitable as decision-support systems rather than direct prediction engines

📉 Visual Analysis

The notebook includes visualizations of:

Bank Nifty long-term price movement (2012–2024)

Training vs validation loss

Accuracy curves

Confusion matrix

Sample predictions with probabilities

These are used to interpret market structure, model learning behavior, and generalization quality.

📂 Repository Structure
├── FA Project Final.ipynb     # Complete project notebook
├── BankNifty_LSTM_FA_Final.pptx   # Final academic presentation
├── README.md                  # Project documentation

▶️ How to Run the Project
1. Install dependencies
pip install pandas numpy yfinance matplotlib scikit-learn tensorflow

2. Open Jupyter Notebook
jupyter notebook

3. Run

Open FA Project Final.ipynb and run all cells sequentially.

🧾 Key Concepts Covered

Financial time series modeling

Feature engineering for markets

Volatility and regime behavior

LSTM and sequential learning

Binary classification

Overfitting and generalization

Probabilistic decision frameworks

🏁 Conclusion

This project demonstrates the practical application of deep learning in financial analytics, while also highlighting the limitations imposed by market efficiency, noise, and regime instability.

It establishes a scalable framework that can be extended using:

News sentiment analysis

Options and derivatives data
Author

Piyush Prabhat

Intraday price signals

Advanced deep learning architectures (Bi-LSTM, Transformers)
