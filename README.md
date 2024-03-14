# Algorithmic-trading-of-BTC-USDT
**Problem Statement:** Algorithmic Trading Model Development for BTC/USDT Crypto Market.
-> Main task is crafting models that outperform benchmarks,balancing returns and risk management in the dynamic BTC/USDT market.
Algorithmic trading, enhanced by the integration of artificial intelligence, embodies a potent synergy, optimizing market strategies with the precision of computational analysis and adaptive learning for more informed and dynamic decision-making.

**Preprocessing**

**Feature Selection**
The ‘opening price’ feature from the BTC/USDT dataset is used in training and testing the machine learning model .
![image](https://github.com/Dadikusumakumari/Algorithmic-trading-of-BTC-USDT/assets/82317063/476c13eb-767e-457b-a1a1-20f990386b8a)

**Sequences Creation:** Considering the last 10 observations and forecasting a single future observation for each sequence.
![image](https://github.com/Dadikusumakumari/Algorithmic-trading-of-BTC-USDT/assets/82317063/4f311bae-e001-492c-9794-fc67670495f4)

**Train-Test Split:**
The split ratio is 80% for training and 20% for testing.
Training Data :Jan 2018 - Apr 2021
Testing Data : Apr 2021 - Jan 2022
![image](https://github.com/Dadikusumakumari/Algorithmic-trading-of-BTC-USDT/assets/82317063/e30212d3-7979-4d2e-9a57-cab22eca9db3)

**Gap Trading Strategy**
The strategy aims to identify observations with a significant gap between the price of one obs. and the next obs.'s price. It then takes trading positions based on whether the gap is positive or negative. Positive gaps may trigger a buying position, while negative gaps may trigger a selling position. This strategy requires the price of the next observation to take the decision.
![image](https://github.com/Dadikusumakumari/Algorithmic-trading-of-BTC-USDT/assets/82317063/e1884381-c672-4816-8879-d43647edb902)

**Regression Model**
Well-known and widely regarded as a powerful machine learning model.
Some Features:
Ensemble Learning
Decision Trees
Bootstrapping

**Trading Logic:**
We have some indicators that will help explain our strategy.:
1. Position:
position = 1: Represents a long trade, indicating that the algorithm has bought an asset or security.
position = 0: Denotes a neutral position, suggesting that there is no ongoing trade (neither buying nor
selling).
position = -1: Corresponds to a short trade, implying that the algorithm has sold an asset.
2. action (The action suggested by the Gap trading strategy):
action = 1: Indicates a signal to buy or initiate a long trade or close a short trade.
action = 0: Represents a hold signal, advising to maintain the current position without taking any new
actions.
action = -1: Signifies a signal to sell or initiate a short trade.

**Logic:**
Long Trade (position P= 1 or 0):
1.If P = 0 and the action is 1 (Buy), it initiates a long trade. The algorithm purchases the asset.
2.If P = 1 and the action is -1 (Sell), it ends the long trade and initializes a short trade immediately.
3.If the action is 0, it means to maintain the current position without any new buying or selling.
4.If the price movement reaches a level that surpasses the stop-loss, the algorithm ends the long trade
to minimize losses.

Short Trade (position = -1):
1.If the action is 1 (Buy), it closes the short sell position and simultaneously initiates a new long trade.
2.If the action is 0, it means to maintain the current position without any new buying or selling.
3.If the action is -1, the model maintains the current position of short sell without any new buying or
selling. As we use compounding, we don’t sell the stocks again.
4.If the price movement reaches a level that surpasses the stop-loss, the algorithm ends the short
trade and simultaneously initiates a new trade.

**Model’s Signals**
![image](https://github.com/Dadikusumakumari/Algorithmic-trading-of-BTC-USDT/assets/82317063/de973c6f-a4d2-4c55-bc8c-8d694fe2bd4e)

**Backtesting Parameters :**
1.ML model Parameters ( Random Forest))
2.gap-threshold-percentage = 0.85
3. stop-loss-percentage = 0.30
4.Look-Back Window = 10 Obs.

**Overall Results**
1. Gross Profit: 1484430.98
2. Net Profit: 483996.36
3. Gross Loss: -1000434.62
4. Max Drawdown: -35734.62
5. Buy and Hold Return of BTC: 484.00%
6. Sharpe Ratio: 1.2384
7. Sortino Ratio: 112.3862
8. Total Closed Trades: 268
9. Number of Winning Trades: 171
10. Number of Losing Trades: 97
11. Average Winning Trade (in USDT): 8680.88
12. Average Losing Trade (in USDT): -10313.76
13. Largest Winning Trade (in USDT): 54753.93
14. Largest Losing Trade (in USDT): -35734.68
15. Average Holding Duration per Trade: 29.97 hrs
16. Max Drawdown Percentage: 6.28%

**Random Forest Results**
**Train Set Metrics:**
R2 Score: 0.9998820645527133
Mean Squared Error: 14760.061048243917
Mean Absolute Error: 54.92394429652503
**Test Set Metrics:**
R2 Score: 0.9693747358366076
Mean Squared Error: 2456163.9950162075
Mean Absolute Error: 1038.8512681053812

**Results:**
Generated 448% return along with the max drawdown of 6.28%.


