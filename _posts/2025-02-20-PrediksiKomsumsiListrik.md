---
title: "Prediksi Konsumsi Listrik Ruangan"
date: 2025-02-20
categories: [Machine Learning, Kaggle]
tags: [Regresi Linear, Prediksi Konsumsi Listrik, Kaggle, Sistem Informasi]
---

# Prediksi Konsumsi Listrik Ruangan  

## 📌 Latar Belakang
Saya telah menyelesaikan kompetisi Sisfo UH Introduction of Kaggle Competition, sebuah ajang yang dirancang untuk memperkenalkan Machine Learning Competition di Kaggle kepada mahasiswa Sistem Informasi Universitas Hasanuddin. Kompetisi ini berfokus pada Prediksi Konsumsi Listrik Ruangan, dengan tujuan membangun model yang dapat memperkirakan konsumsi listrik berdasarkan durasi penggunaan perangkat listrik dalam ruangan tersebut.

Melalui kompetisi ini, saya mempelajari:  
✅ Cara bekerja dengan dataset dalam format **kompetisi Kaggle**  
✅ Teknik dasar **Machine Learning**, khususnya **Regresi Linear**  
✅ Cara mengunggah prediksi dan memahami **leaderboard Kaggle**  

## 📂 Dataset  
Dataset kompetisi ini terdiri dari tiga file utama:  
- **Training.csv** – Data pelatihan model, berisi waktu penggunaan listrik (`menit`) dan konsumsi listrik (`watt`).  
- **Testing.csv** – Data pengujian model, hanya berisi waktu (`menit`), tanpa konsumsi listrik.  
- **Sample_submission.csv** – Format yang harus digunakan untuk mengunggah hasil prediksi ke Kaggle.  


## Kode yang digunakan
```python
import pandas as
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score

# Membaca data
df_train = pd.read_csv('Training.csv')
df_test = pd.read_csv('Testing.csv')

# Persiapan data training
X_train = df_train[['menit']]
y_train = df_train['watt']

# Membagi data menjadi training dan testing
X_train, X_test, y_train, y_test = train_test_split(X_train, y_train, test_size=0.2, random_state=42)

# Membuat dan melatih model regresi linear
model = LinearRegression()
model.fit(X_train, y_train)

# Memprediksi data testing
df_test = df_test.rename(columns={'waktu': 'menit'})
df_test['watt'] = model.predict(df_test[['menit']])

# Hasil prediksi
df_test.drop('menit', axis=1, inplace=True)
df_test.head()


# Load hasil prediksi
df = pd.read_csv('hasil_prediksi.csv')

# Plot data
plt.figure(figsize=(8,5))
plt.plot(df['id'], df['watt'], marker='o', linestyle='-', color='r', label="Prediksi Konsumsi Listrik")
plt.xlabel("Id")
plt.ylabel("Konsumsi Listrik (Watt)")
plt.title("Prediksi Konsumsi Listrik berdasarkan Waktu")
plt.legend()
plt.grid()

# Simpan sebagai gambar
plt.savefig("hasil_prediksi.png")
plt.show()

```



## 📊 Hasil dan Kesimpulan
![Hasil Prediksi Konsumsi Listrik](assets/dokumentasi/hasil_prediksi.png)
Model Regresi Linear yang dibangun dapat memperkirakan konsumsi listrik berdasarkan waktu penggunaan perangkat listrik. Hasil prediksi dapat digunakan untuk pengambilan keputusan terkait efisiensi energi di ruangan tersebut.

Melalui proyek ini, saya telah memahami sedikit dasar-dasar Machine Learning, Regresi Linear, dan cara bekerja dengan dataset kompetisi Kaggle. 🚀
