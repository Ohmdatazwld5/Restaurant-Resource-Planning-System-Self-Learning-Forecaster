# 🍽️ Restaurant Resource Planning System — Self-Learning Forecaster

## 🚀 Overview

This project builds an **end-to-end AI system** that helps restaurants optimize operations by predicting:

* 📊 **Customer demand (hourly covers)**
* 👨‍🍳 **Staff planning (role & station-wise)**
* 🥦 **Inventory ordering (shelf-life aware)**

Unlike traditional forecasting systems, this model **continuously improves using real-world feedback from managers**.

---

## 🎯 Problem

Restaurants face two major inefficiencies:

| Issue            | Impact                         |
| ---------------- | ------------------------------ |
| Over-resourcing  | Wasted food, higher labor cost |
| Under-resourcing | Poor service, lost revenue     |

👉 The challenge: Build a system that **learns from its mistakes** and improves over time.

---

## 🧠 Solution

This system combines:

* Machine Learning (XGBoost)
* Time-series feature engineering
* Feedback-driven retraining loop
* Real-time interactive UI (Gradio)

---

## 🔁 Core Innovation: Self-Learning Feedback Loop

Managers can input actual values:

> Predicted: 682
> Actual: 500

System automatically:

* Computes correction ratio
* Stores contextual feedback (weather, event, promo)
* Retrains model with higher weight on recent feedback
* Applies calibration for future predictions

---

## 📈 Model Convergence (Real Output)

### ✅ Initial Error → High

* Predicted: **682**
* Actual: **500**
* Error: **36.4%**

### ✅ After Learning (Few Iterations)

| Round | Predicted | Actual | Error %    |
| ----- | --------- | ------ | ---------- |
| 1     | 682       | 500    | 36.4%      |
| 2     | 391       | 500    | 21.8%      |
| 3     | 559       | 500    | 11.8%      |
| 4     | 497       | 500    | 0.6%       |
| 5     | 502       | 500    | **0.4%** ✅ |

👉 The system **converged rapidly** to near-perfect prediction.

---

## 📊 Final Performance Snapshot

* 📉 **Final Error:** ~0.4% – 1.8%
* 📉 **Global MAE:** ~3.3 covers
* 🔁 **Stable Calibration Factor:** ~0.98–1.01
* 📊 **Consistent Predictions across feedback rounds**

👉 This proves the system is **self-correcting and stable**

---

## ⚙️ System Components

### 1. Demand Forecasting

* Model: **XGBoost Regressor**
* Features:

  * Weather, Events, Promotions
  * Lag features (1h, 24h, 168h)
  * Rolling averages
  * Cyclical time encoding

---

### 2. Staff Planning Model

* Predicts:

  * Staff per role (Chef, FOH, Delivery)
  * Staff per station
* Uses separate models per role-station pair

---

### 3. Inventory Optimization

* Predicts ingredient order quantities
* Considers:

  * Shelf life
  * Supplier lead time
  * Demand
* Outputs:

  * Order quantity
  * Stockout risk
  * Priority level (HIGH / MED / LOW)

---

### 4. Feedback Learning Engine

* Accepts corrections within safe range:

  ```
  0.5 ≤ actual / predicted ≤ 2.0
  ```
* Uses:

  * Weighted retraining
  * Recent feedback prioritization
  * Context-aware calibration

---

## 🖥️ Interactive UI (Gradio)

### Inputs:

* Restaurant
* Weather
* Event type
* Promotion
* Actual covers (for retraining)

### Outputs:

* 📊 Demand forecast (hourly + total)
* 👨‍🍳 Staff plan (role & station)
* 🥦 Inventory recommendations
* 📈 Convergence graph (learning over time)

---

## 📁 Project Structure

```
.
├── Restaurant_Resource_Planning.ipynb   # Main notebook (complete system)
├── data/
│   ├── restaurants.csv
│   ├── hourly_demand.csv
│   ├── staffing_plan.csv
│   ├── inventory_plan.csv
│   └── manager_corrections.csv
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup

```bash
git clone https://github.com/your-username/restaurant-resource-planning-ml.git
cd restaurant-resource-planning-ml

pip install -r requirements.txt
jupyter notebook
```

Open:

```
Restaurant_Resource_Planning.ipynb
```

---

## 🧪 Evaluation Metrics

* MAE (Mean Absolute Error)
* RMSE (Root Mean Squared Error)
* Live Convergence Tracking

---

## 💡 Key Strengths

✅ Self-learning system (not static ML)
✅ Real-time feedback integration
✅ Multi-output prediction (Demand + Staff + Inventory)
✅ Business-impact focused (cost + revenue optimization)

---

## 🚀 Future Improvements

* Deep Learning (LSTM / Transformers)
* Real-time POS integration
* Multi-location scaling
* Reinforcement learning for staffing optimization

---

## 👨‍💻 Author

**Ohmprakaash Raja**

---

## ⭐ Final Note

This is not just a forecasting model —
it is a **closed-loop intelligent decision system** that improves with real-world usage.

👉 That’s what makes it production-grade.
