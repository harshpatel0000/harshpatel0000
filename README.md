# 🔮 Easy Predict — Walmart Sales Forecasting

> An end-to-end machine learning web app that forecasts Walmart store weekly sales using a Random Forest Regressor — with a full analytics dashboard built in Streamlit.

[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.6.1-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io)
[![Plotly](https://img.shields.io/badge/Plotly-Charts-3F4F75?logo=plotly&logoColor=white)](https://plotly.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📌 What It Does

Upload Walmart store sales data, explore it through an interactive dashboard, and generate a **12-week sales forecast** for any store and department — all without writing a single line of code.

Four ML models are trained and compared automatically. The best one (by R² score) is selected and used for predictions.

> ⚠️ **Note:** The trained model file (`best_model_.pkl`) is **not included** in this repo due to its large size (~1.1 GB). See [Getting Started](#-getting-started) to generate it locally.

---

## ✨ App Pages

| Page | What You Get |
|---|---|
| 📊 **Dashboard** | KPI metrics, store/department filter, monthly trend & holiday impact |
| 📈 **EDA** | Distributions, time trends, heatmaps, outlier detection |
| 🔮 **Prediction** | Interactive 12-week sales forecast with Plotly charts |
| ℹ️ **About** | Project summary and model info |

---

## 🤖 Model Comparison

Four regression models are trained and the best is auto-selected by R² score:

| Model | Notes |
|---|---|
| Linear Regression | Baseline |
| Decision Tree | `random_state=42` |
| ✅ **Random Forest** | `n_estimators=100`, `max_depth=20`, `n_jobs=-1` — **Best Model** |
| Gradient Boosting | `random_state=42` |

**Features used:** `Store`, `Dept`, `IsHoliday`, `Year`, `Month`, `Week`
**Target:** `Weekly_Sales`

---

## 📊 Dataset

Based on the [Walmart Store Sales Forecasting](https://www.kaggle.com/competitions/walmart-recruiting-store-sales-forecasting) dataset from Kaggle, cleaned and preprocessed.

| Column | Description |
|---|---|
| `Store` / `Store_Name` | Store identifier |
| `Dept` / `Dept_Name` | Department identifier |
| `Date` | Week of sales |
| `Weekly_Sales` | Target — weekly revenue |
| `IsHoliday` | Whether the week includes a public holiday |

---

## 📁 Project Structure

```
Easy-Predict/
│
├── app.py                            # Streamlit web application (4 pages)
├── EasyPredict_Part1 - Copy.ipynb    # Data exploration & EDA
├── EasyPredict_Part2 - Copy.ipynb    # Model training & evaluation → generates best_model_.pkl
├── walmart_sales_cleaned.csv         # Cleaned Walmart sales dataset
├── requirements.txt                  # Python dependencies
├── .gitignore                        # Excludes best_model_.pkl (too large for GitHub)
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/harshpatel0000/Easy-Predict.git
cd Easy-Predict
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

> ⚠️ Use **`scikit-learn==1.6.1`** exactly — the model was trained with this version. A different version may cause `InconsistentVersionWarning` or incorrect predictions.

### 3. Generate the Model

The app requires `best_model_.pkl` to run. Open and run all cells in:

```
EasyPredict_Part2 - Copy.ipynb
```

This notebook will:
- Load and preprocess `walmart_sales_cleaned.csv`
- Train all 4 models (Linear Regression, Decision Tree, Random Forest, Gradient Boosting)
- Auto-select the best model by R² score
- Save it as `best_model_.pkl` in the project folder

### 4. Run the App

```bash
streamlit run app.py
```

Open [http://localhost:8501](http://localhost:8501) in your browser.

---

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Web App | Streamlit |
| Visualization | Plotly, Matplotlib, Seaborn |
| Machine Learning | Scikit-learn |
| Data Processing | Pandas, NumPy |
| Language | Python 3.11 |

---

## 📦 Requirements

```
streamlit
pandas
numpy
matplotlib
seaborn
plotly
scikit-learn==1.6.1
```

Install all at once:

```bash
pip install -r requirements.txt
```

---

## 🗺️ Roadmap

- [ ] Add XGBoost / LightGBM to model comparison
- [ ] Include external features (fuel prices, CPI, temperature)
- [ ] Deploy on Streamlit Cloud
- [ ] Add store-level performance comparison view
- [ ] Export forecast results as CSV

---

## 👤 Author

**Harsh Patel**
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Harsh%20Patel-blue?logo=linkedin)](https://www.linkedin.com/in/harsh-patel-a7387537b/)
[![GitHub](https://img.shields.io/badge/GitHub-harshpatel0000-black?logo=github)](https://github.com/harshpatel0000)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
