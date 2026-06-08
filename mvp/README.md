# 🌧️ Jakarta Flood Early Warning System – v3

## ⚠️ PENTING: Jalankan retrain dulu sebelum buka app

Model `.joblib` yang ada di folder `models/` ditraining di environment berbeda,
sehingga **tidak bisa langsung dipakai** — harus ditraining ulang di komputer lo dulu.
Tenang, ini cuma sekali dan prosesnya otomatis.

---

## Cara Pakai (urutan wajib)

### Step 1 — Install dependencies
```
pip install -r mvp/requirements_mvp.txt
```

### Step 2 — Retrain model (SEKALI SAJA)
```
cd Aol_softeng_v3
python sourcecode/retrain_combined.py
```
Script ini akan:
- Baca `dataset/jakarta_flood_combined.xlsx`
- Training 2 model (classifier + regressor)
- Simpan otomatis ke `models/flood_classifier.joblib` dan `models/flood_depth_regressor.joblib`

Estimasi waktu: **2–5 menit** tergantung spesifikasi komputer.

### Step 3 — Jalankan app
```
cd mvp
streamlit run app_streamlit.py
```

### Step 4 — Upload di browser
Di sidebar Streamlit, upload:
1. `models/flood_classifier.joblib`
2. `models/flood_depth_regressor.joblib`
3. `dataset/jakarta_flood_combined.xlsx`

Lalu pilih Wilayah & Kelurahan — selesai!

---

## Struktur Folder

```
Aol_softeng_v3/
├── dataset/
│   └── jakarta_flood_combined.xlsx   ← satu file semua area (~456k baris)
├── models/
│   ├── flood_classifier.joblib       ← di-generate oleh retrain_combined.py
│   └── flood_depth_regressor.joblib  ← di-generate oleh retrain_combined.py
├── mvp/
│   ├── app_streamlit.py
│   ├── requirements_mvp.txt
│   └── README.md
└── sourcecode/
    └── retrain_combined.py           ← ← jalankan ini dulu!
```

---

## Navigasi Area

| Wilayah | Kelurahan tersedia |
|---|---|
| DKI Jakarta | Semua Wilayah (general) |
| Jakarta Utara | Semua Wilayah, Kelapa Gading, Penjaringan, Pluit, Tanjung Priok, Pademangan |
| Jakarta Barat | Semua Wilayah, Kemanggisan, Grogol, Tambora, Cengkareng, Kalideres |
| Jakarta Selatan | Semua Wilayah, Kebayoran Baru, Mampang Prapatan, Tebet, Jagakarsa, Pesanggrahan |
| Jakarta Timur | Semua Wilayah, Jatinegara, Kramat Jati, Cakung, Duren Sawit, Matraman |
| Jakarta Pusat | Semua Wilayah, Menteng, Gambir, Senen, Kemayoran, Tanah Abang |
