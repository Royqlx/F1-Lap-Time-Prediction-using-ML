# 🏎️ Formula 1 Lap Time Prediction using Machine Learning

## 📌 Project Overview

This project builds a **machine learning model to predict Formula 1 lap times** using race timing and telemetry data.

The dataset is accessed using the **FastF1 Python library**, which provides official race timing data including lap times, tyre information, driver positions, and race conditions.

The objective is to understand **how different race factors influence lap performance** and to develop a predictive model capable of estimating lap times under varying conditions.

---

# 📊 Dataset

The dataset is retrieved using the **FastF1 API**.

It contains official timing data from **Formula 1 race sessions**, including:

| Feature | Description |
|------|------|
| Driver | Driver identifier |
| LapNumber | Lap number in race |
| Stint | Tyre stint number |
| Compound | Tyre compound used |
| TyreLife | Laps completed on current tyre |
| TrackStatus | Track condition (green/yellow flag) |
| Position | Driver race position |
| LapTime | Total lap time |

Data is sourced from race sessions of the **Formula 1 season**.

---

# ⚙️ Feature Engineering

Several additional features were created to improve prediction accuracy.

### Fuel Load Estimate
Cars start races with heavy fuel loads which gradually decrease.

```
FuelLoadEstimate = 110 − (LapNumber × FuelBurnRate)
```

### Track Evolution
Tracks become faster as more rubber is deposited during the race.

```
TrackEvolution = LapNumber / MaxLapNumber
```

### Tyre Degradation
Tyre performance decreases as tyre life increases.

```
TyreDeg = TyreLife^1.3
```

### Traffic Indicator
Drivers following another car experience aerodynamic disturbance.

```
Traffic = Position > 1
```

---

# 🤖 Machine Learning Model

The project uses a **Random Forest Regressor** for lap time prediction.

Reasons for choosing Random Forest:

- Handles non-linear relationships
- Robust to noisy real-world data
- Performs well on tabular datasets

### Model Pipeline

1. Data Collection (FastF1 API)
2. Data Cleaning
3. Feature Engineering
4. Encoding Categorical Variables
5. Train/Test Split
6. Model Training
7. Model Evaluation

---

# 📈 Model Performance

Model evaluation metrics:

| Metric | Value |
|------|------|
| Mean Absolute Error (MAE) | ~2 seconds |
| R² Score | ~0.93 |

This indicates that the model explains **over 90% of lap time variability**.

---

# 📊 Example Visualization

The model performance can be visualised using a **Predicted vs Actual Lap Time plot**.

This helps illustrate how closely the model predictions match the real lap times.

---

# 🧠 Key Insights

Some insights derived from the analysis:

- **Fuel load significantly impacts early lap times**
- **Tyre degradation causes lap times to increase gradually**
- **Traffic conditions introduce lap time variability**
- **Track evolution improves lap times over a race session**

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- FastF1

---

# 📂 Project Structure

```
f1-lap-time-prediction
│
├── notebooks
│   └── lap_time_prediction.ipynb
│
├── cache
│
├── README.md
│
└── requirements.txt
```

---

# 🚀 Future Improvements

Possible extensions to improve the model:

- Train using **multiple seasons of data**
- Incorporate **weather conditions**
- Use **telemetry data (speed, throttle, braking)**
- Implement **XGBoost or LightGBM models**
- Build a **Streamlit dashboard for lap time prediction**

---

# 📚 References

- FastF1 Documentation
- Official Formula 1 Timing Data

---

# 👨‍💻 Author

**Royston Rex Fernandez**  
Data Scientist | Data Engineer

---

⭐ If you found this project interesting, consider starring the repository!
