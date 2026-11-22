# Jakarta Flood Early Warning System (FEWS)

A Machine Learning web application built with **Streamlit** and **scikit-learn (`HistGradientBoosting`)** to predict flood probability and estimated inundation depth across Jakarta sub-districts (*kelurahan*) **6 hours ahead**.

---

## Project Structure

```text
├── dataset/
│   └── jakarta_flood_combined.xlsx   # See Dataset section below
├── models/
│   ├── flood_classifier.joblib
│   └── flood_depth_regressor.joblib
├── mvp/
│   ├── app_streamlit.py
│   ├── requirements_mvp.txt
│   └── README.md
└── sourcecode/
    └── retrain_combined.py
```

---

## Dataset

The dataset is excluded from this repository due to GitHub's file size limits (~456k hourly records across Jakarta districts and sub-districts).

Download the dataset here: [jakarta_flood_combined.xlsx](https://drive.google.com/drive/folders/1Yf5vnpMFBRqUjqYrGGFD4EyAgui7dohR)

After downloading, place the file inside the `dataset/` directory.

---

## Getting Started

**Prerequisites:** Python 3.10+

**1. Clone the repository**

```bash
git clone https://github.com/Elenoirr/Jakarta-Flood-Early-Warning-System.git
cd Jakarta-Flood-Early-Warning-System
```

**2. Create and activate a virtual environment**

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

**3. Install dependencies**

```bash
pip install -r mvp/requirements_mvp.txt
```

**4. Launch the Streamlit application**

```bash
streamlit run mvp/app_streamlit.py
```

The web interface will open automatically at `http://localhost:8501`.

---

## How to Use

Once the dashboard opens in your browser, upload the following three artifacts via the left sidebar:

1. `flood_classifier.joblib` (from `models/`)
2. `flood_depth_regressor.joblib` (from `models/`)
3. `jakarta_flood_combined.xlsx` (from `dataset/`)

Select a Jakarta municipality (*Wilayah*) and sub-district (*Kelurahan*) from the sidebar to inspect **6-hour ahead flood predictions**. The dashboard provides three interactive views:
* **6-Hour Forecast:** Single-timestamp inspection, sensor telemetry breakdown, batch predictions, and CSV export.
* **Historical Floods:** Monthly and yearly flood frequency and severity analysis based on historical ground-truth records.
* **Risk Ranking:** Sub-district flood risk leaderboard ranked by historical inundation frequency and depth.

---

## Retraining the Models

If you run on a different `scikit-learn` version or want to retrain from scratch on updated telemetry:

```bash
python sourcecode/retrain_combined.py
```

---

## Dependencies

```text
streamlit>=1.32.0
pandas>=2.0.0
numpy>=1.24.0
scikit-learn>=1.3.0
joblib>=1.3.0
openpyxl>=3.1.0
```
