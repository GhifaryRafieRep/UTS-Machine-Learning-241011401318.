UTS Machine Learning

- Nama         : Ghifary Rafie Ananda
- NIM            : 241011401318
- Kelas         : Reg B
- random_state : 18 

Seluruh model dan metrik diimplementasikan sendiri dengan NumPy (library: numpy, pandas, matplotlib).
scikit-learn hanya dipakai pada soal bonus.

# Isi Repositori
- `README.MD` – Penjelsan
- `tugas_UTS.ipynb` – notebook jawaban
- `Ads_Data.csv`, `Email_Data.csv` – dataset

# Ringkasan Hasil
# Bagian A
– Linear Regression (`Ads_Data.csv`, 40 data, split 32 training / 8 testing)
- Persamaan: `y_hat = 29.3242 + 9.0051 * BiayaIklan`
- Setiap kenaikan biaya iklan 1 juta Rp, penjualan naik sekitar 9.01 juta Rp.

| Metrik | Training | Testing |
|---|---|---|
| MAE | 4.0424 | 6.3949 |
| MSE | 31.9135 | 54.5504 |
| RMSE | 5.6492 | 7.3858 |
| R² | 0.9556 | 0.8152 |

- Gradient descent (5000 iterasi): lr 0.001 terlalu lambat (belum konvergen), lr 0.02 pas (hasil sama dengan normal equation), lr 0.1 divergen (batas stabil teoritis lr < 0.0289).
- Prediksi: 4.5 juta → 69.85 juta; 7 juta → 92.36 juta; 12 juta → 137.39 juta (ekstrapolasi, kurang dapat dipercaya).

# Bagian B 
– Logistic Regression (`Email_Data.csv`, 60 data, split 45 training / 15 testing)
- Persamaan: `P(Spam) = sigmoid(-8.5571 + 0.7374 * JumlahLink + 0.7276 * KataPromo)`
- Evaluasi testing (threshold 0.5): accuracy 1.0, precision 1.0, recall 1.0, F1 1.0 (TN=11, FP=0, FN=0, TP=4). Akurasi training 0.8667.
- Threshold 0.3 dan 0.5 memberi hasil sama; threshold 0.7 menurunkan recall menjadi 0.5 (FN=2). Threshold pilihan: **0.5**.
- Prediksi email baru (threshold 0.5): E1 Bukan Spam (P=0.0017), E2 Bukan Spam (P=0.3764), E3 Spam (P=0.9953), E4 Spam (P=0.7152).

# Bonus – scikit-learn
- Linear Regression: hasil identik dengan implementasi sendiri.
- Logistic Regression: koefisien berbeda karena scikit-learn memakai regularisasi L2 (C=1.0) secara default dan solver yang konvergen penuh; hasil evaluasi testing tetap sama.
