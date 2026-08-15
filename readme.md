# Lithium-Ion Battery SOH Prediction

Portfolio-ready adaptation of a battery health prediction project using NASA lithium-ion cycling data.

This repository has been cleaned for presentation purposes. I removed non-essential media, generated artifacts, and promotional content while preserving the original project context and the required dataset attribution.

## Project Overview

This project predicts battery State of Health (SOH) from degradation patterns in lithium-ion battery cycling data. The workflow combines data loading, feature engineering, and machine learning models to estimate health decline over operational cycles.

The repository uses the NASA Prognostics Center battery dataset, which contains charge/discharge measurements and degradation histories for multiple Li-ion cells. The modeled objective is to estimate SOH from cycle-level battery behavior and capacity degradation trends.

## Key Features

- Exploratory analysis of NASA battery cycling data
- Feature extraction from charge/discharge cycle measurements
- SOH estimation using a supervised regression workflow
- Comparison of two model families:
  - XGBoost for structured tabular features
  - LSTM for sequence-based time-series modeling
- Model artifacts saved under `models/`
- Reusable utility functions for loading and plotting battery data

## Tech Stack

- Python 3.8+
- TensorFlow / Keras
- XGBoost
- Pandas, NumPy
- SciPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

## Setup

1. Clone the repository:

```bash
git clone <repository-url>
cd "Li-ion Battery SOH Prediction"
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Download the NASA battery dataset and place the `.mat` files in `data/NASA_batteries_1/`.

## Usage

This project is primarily executed through the Jupyter notebooks:

1. `notebooks/battery_data_analysis.ipynb`
   - loads the NASA data
   - reviews cycle behavior and degradation trends
   - prepares feature sets for modeling

2. `notebooks/battery_prediction.ipynb`
   - trains the XGBoost and LSTM models
   - evaluates SOH prediction performance
   - compares model behavior and error metrics

Run the notebooks with:

```bash
jupyter notebook notebooks/battery_data_analysis.ipynb
jupyter notebook notebooks/battery_prediction.ipynb
```

## Results

The project evaluates the ability of two modeling approaches to estimate battery SOH from deteriorating cycle data.

Key observations from the workflow:

- Battery capacity declines steadily as the number of charge/discharge cycles increases.
- The capacity fade pattern shows clear degradation behavior across the battery cells.
- XGBoost performs strongly on the engineered tabular feature set and was observed to outperform the LSTM baseline for SOH regression in this project evaluation.
- The LSTM model remains useful for sequence-based temporal modeling, but the tabular feature approach is more effective in this dataset setup.

The project demonstrates that time-series battery signals can be converted into meaningful health indicators and used for predictive maintenance-oriented diagnostics.

## Data Source and Attribution

This project uses the NASA battery degradation dataset from the NASA Prognostics Center of Excellence.


## Repository Layout

```text
.
├── data/
│   └── NASA_batteries_1/
│       ├── B0005.mat
│       ├── B0006.mat
│       ├── B0007.mat
│       ├── B0018.mat
│       └── README.txt
├── models/
│   ├── lstm_soh_model/
│   └── xgboost_soh_model.json
├── notebooks/
│   ├── battery_data_analysis.ipynb
│   └── battery_prediction.ipynb
├── utils/
│   ├── __init__.py
│   ├── data_loader.py
│   └── plotting.py

├── readme.md
├── requirements.txt
└── data/NASA_batteries_1/README.txt
```


