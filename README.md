
# 🛢️ Brent Oil Price Prediction Using RNN

> This project predicts **Brent oil prices** using historical time-series data and technical indicators with a **Recurrent Neural Network (RNN)** architecture. Multiple feature combinations are used to evaluate model performance across various input dimensions.

---

## 📌 Project Overview

The model is trained using Brent oil price historical data including open, close, high, low, and adjusted close prices, along with:

- Returns and Log Returns
- Technical Indicators: Moving Average (SMA), Exponential Moving Average (EMA), MACD, RSI
- Crude oil price (WTI) as an additional feature in some cases

The data is modeled using RNN architectures like LSTM, trained on different feature sets (kv1 to kv4).

---

## 🧾 Feature Combinations

- **kv1**: Open, Close, High, Low, Adj Close, Log Return
- **kv2**: Technical indicators + Log Return
- **kv3**: WTI price + Log Return
- **kv4**: Combination of kv2 and kv3 (Tech Indicators + WTI)

---

## 🧠 Model Architecture

```python
model = Sequential([
    LSTM(units=50, return_sequences=True, input_shape=(hops, features)),
    Dropout(0.2),
    LSTM(units=50),
    Dropout(0.2),
    Dense(1)
])
```

- Optimizer: Adam
- Loss: Mean Squared Error
- Epochs: 100
- Batch Size: 32
- Validation Split: 0.2

---

## 📊 Evaluation Results (kv1 & kv2)

| Metric     | kv1 Value    | kv2 Value    |
|------------|--------------|--------------|
| MAE        | 20.08        | 22.22        |
| MSE        | 865.35       | 1056.45      |
| RMSE       | 29.42        | 32.50        |
| R² Score   | 0.9784       | 0.9736       |

✅ The model shows **high accuracy and low error** for both kv1 and kv2 combinations, with kv1 slightly outperforming kv2.

---

## 📈 Visualization

Candlestick and line charts are generated to visualize actual vs predicted prices using:

- `plotly.graph_objects`
- `matplotlib.pyplot`

---

## 📁 Repository Structure

```
Brent_Oil_Price_Prediction/
├── data.xlsx        # Input dataset with Brent and WTI prices
├── main.ipynb       # Main notebook with full workflow
└── README.md        # You're here
```


---

## 🧾 Conclusion

These results provide insights into the performance of each feature combination in predicting the Brent oil price. It appears that **kv1** achieved the lowest MAE and RMSE, indicating better predictive performance compared to other combinations. However, further analysis and experimentation may be necessary to determine the most effective feature combination for accurate predictions.

### 🔹 kv1 (Basic stock data with log returns)
- Includes basic stock data: open, close, high, low, adj close, and log returns.
- Achieved the **lowest MAE and RMSE**, showing better performance.
- Log returns appear to provide strong signals on price movement.

### 🔹 kv2 (Stock data with technical indicators and log returns)
- Adds SMA_10, EMA_12, MACD, RSI to kv1 features.
- Slight increase in MAE and RMSE compared to kv1.
- Technical indicators might introduce redundancy or noise.

### 🔹 kv3 (Stock data with WTI and log returns)
- Combines basic stock data, WTI prices, and log returns.
- External factor (WTI) does not significantly improve accuracy.
- Higher MAE and RMSE indicate less predictive power than kv1.

### 🔹 kv4 (Technical indicators + WTI + log returns)
- Combines kv2 and kv3.
- Performance is **closer to kv1** than to kv2 or kv3.
- Suggests technical indicators and WTI provide marginal value in this context.

---

## 👤 Author

**Alexander Tiopan**  
📧 alexandertiopan1212@gmail.com  
🔗 GitHub: [alexandertiopan1212](https://github.com/alexandertiopan1212)
