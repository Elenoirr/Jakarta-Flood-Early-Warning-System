# Jakarta Flood Early Warning System (FEWS)

Aplikasi web berbasis Machine Learning untuk memprediksi probabilitas dan kedalaman banjir di kelurahan-kelurahan Jakarta, 6 jam sebelum kejadian.

---

## Struktur Proyek

```
├── dataset/
│   └── jakarta_flood_combined.xlsx   # lihat bagian Dataset di bawah
├── models/
│   ├── flood_classifier.joblib
│   └── flood_depth_regressor.joblib
├── mvp/
│   ├── app_streamlit.py
│   └── requirements_mvp.txt
└── sourcecode/
    └── retrain_combined.py
```

---

## Dataset

Dataset tidak disertakan dalam repository karena ukuran file melebihi batas GitHub.

Download dataset di sini: [jakarta_flood_combined.xlsx](https://drive.google.com/drive/folders/1Yf5vnpMFBRqUjqYrGGFD4EyAgui7dohR)

Setelah download, letakkan file di folder `dataset/`.

---

## Cara Menjalankan

**Prasyarat:** Python 3.10+

**1. Clone repository**

```bash
git clone https://github.com/Elenoirr/Jakarta-Flood-Early-Warning-System.git
cd Jakarta-Flood-Early-Warning-System
```

**2. Buat virtual environment**

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# Mac/Linux
source .venv/bin/activate
```

**3. Install dependencies**

```bash
pip install -r mvp/requirements_mvp.txt
```

**4. Jalankan aplikasi**

```bash
streamlit run mvp/app_streamlit.py
```

Aplikasi akan terbuka di browser pada `http://localhost:8501`.

---

## Cara Pakai Aplikasi

Setelah aplikasi terbuka, upload file berikut lewat sidebar:

- `flood_classifier.joblib` (dari folder `models/`)
- `flood_depth_regressor.joblib` (dari folder `models/`)
- `jakarta_flood_combined.xlsx` (dari folder `dataset/`)

Setelah upload, pilih kelurahan dari sidebar untuk melihat prediksi banjir 6 jam ke depan. Tersedia tiga tab: **Prediksi**, **Riwayat**, dan **Ranking**.

---

## Melatih Ulang Model

```bash
python sourcecode/retrain_combined.py
```

---

## Dependencies

```
streamlit >= 1.32.0
pandas >= 2.0.0
numpy >= 1.24.0
scikit-learn >= 1.3.0
joblib >= 1.3.0
openpyxl >= 3.1.0
```
