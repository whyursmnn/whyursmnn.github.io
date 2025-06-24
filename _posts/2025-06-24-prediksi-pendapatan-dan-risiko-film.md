# Prediksi Potensi Pendapatan dan Risiko Return on Investment (ROI) Film Menggunakan Machine Learning

**Oleh:** Harmelia Yuli Rahmatika A. (dan Tim Peneliti)
**Email:** ahyr23h@student.unhas.ac.id

---

## Inti Proyek

Proyek ini mengembangkan sistem Machine Learning untuk memprediksi pendapatan film dan menilai risiko investasinya (Return on Investment/ROI) berdasarkan data pra-rilis. Kami menggunakan algoritma Random Forest dan XGBoost, serta teknik penanganan data tidak seimbang (SMOTETomek) untuk meningkatkan akurasi. 

---

## Latar Belakang Masalah (Mengapa Proyek Ini Penting?)

Industri film adalah ladang investasi yang sangat berisiko. Meskipun ada potensi pendapatan besar (mencapai 42,3 miliar dolar pada 2019 sebelum pandemi), lebih dari 60% film gagal menutup biaya produksi, dan hanya sekitar 25% yang menghasilkan keuntungan signifikan. Keputusan investasi seringkali masih mengandalkan insting dan pengalaman, bukan data objektif, terutama untuk film berbiaya besar.

Hal ini menimbulkan kebutuhan mendesak akan pendekatan yang lebih sistematis dan berbasis data untuk memprediksi pendapatan dan mengukur risiko investasi film secara objektif.

**Pertanyaan Penelitian Utama:**
* Seberapa akurat data produksi dapat memprediksi pendapatan akhir sebuah film? 
* Bagaimana mengembangkan metode klasifikasi risiko investasi yang praktis berdasarkan prediksi ROI dan karakteristik produksi film? 

---

## Metode Singkat

Kami mengumpulkan data dari API TMDb (10.247 film internasional 2000-2023)  dan melakukan beberapa langkah kunci:

1.  **Pra-pemrosesan Data:** Membersihkan data, mengisi nilai hilang (misal, anggaran kosong diisi median per genre/tahun).
2.  **Rekayasa Fitur:** Membuat fitur baru seperti:
    * `release_year`, `release_month`, dan `Seasonal_Score` dari tanggal rilis.
    * Encoding genre menjadi vektor biner.
    * Normalisasi `popularity`.
    * Fitur biner `lang_en` (bahasa Inggris) dan `lang_others`.
3.  **Perhitungan ROI:** Dihitung dari keuntungan bersih dibagi anggaran.
4.  **Klasifikasi Risiko ROI:** ROI dikategorikan ke dalam 5 kelas: Kerugian Ekstrem ($ROI < -50$), Kerugian Signifikan ($-50 \le ROI < 0$), Keuntungan Marjinal ($0 \le ROI < 50$), Keuntungan Baik ($50 \le ROI < 200$), dan Blockbuster ($ROI > 200$).
5.  **Penanganan Ketidakseimbangan Kelas:** Menggunakan SMOTETomek karena data ROI sangat tidak seimbang (42% Kerugian Ekstrem, 23% Kerugian Signifikan, 18% Keuntungan Marjinal, 12% Keuntungan Baik, dan hanya 5% Blockbuster).

**Diagram Alur Kerja Sistem:**
![Diagram Alur Kerja Sistem Prediksi ROI Film](/assets/images/workflow.png)
*Diagram ini menunjukkan tahapan lengkap dari pengumpulan data hingga evaluasi model. *

---

## Hasil Utama

### Performa Prediksi Pendapatan (Regresi)

* **Akurasi:** Random Forest Regressor mencapai $R^{2}=0,7250$ pada data pengujian, sementara XGBoost Regressor sedikit lebih baik dengan $R^{2}=0,7390$.
* **Overfitting:** Ada sedikit *overfitting* karena performa pada data pelatihan jauh lebih tinggi ($R^{2} \approx 0,95-0,96$) dibandingkan data pengujian, menunjukkan model terlalu kompleks untuk generalisasi sempurna.

**Plot Aktual vs Prediksi XGBoost Regressor:**
![Plot Aktual vs Prediksi XGBoost Regressor](/assets/images/apr_xgb.png)
*Perbandingan Pendapatan Aktual dan Prediksi oleh XGBoost Regressor.*

**Feature Importance (Regresi):**

* Fitur `budget` (anggaran produksi) dan `popularity` adalah kontributor paling dominan dalam memprediksi pendapatan film untuk kedua model.
* `release_year`, `release_month`, dan `runtime` juga memiliki bobot yang signifikan.

![Feature Importance Random Forest Regressor](/assets/images/fi_rf.png)
*Top 15 Feature Importance - Random Forest Regressor.*
![Feature Importance XGBoost Regressor](/assets/images/fi_xgb.png)
*Top 15 Feature Importance - XGBoost Regressor.*

### Performa Klasifikasi Risiko ROI

* **Akurasi:** XGBoost Classifier mencapai *weighted F1-score* 0,55, sedikit lebih baik dari Random Forest Classifier (0,53).
* **Tantangan:** Kategori `Marginal Profit` dan `Significant Loss` masih menjadi tantangan utama dengan F1-score rendah, kemungkinan karena distribusi data yang sangat tidak seimbang dan tumpang tindih karakteristik.

**Confusion Matrix (Contoh XGBoost Classifier):**
![Confusion Matrix XGBoost Classifier](/assets/images/cf.png)
*Confusion Matrix (Normalized & Raw Counts) untuk XGBoost Classifier.*

**Feature Importance (Klasifikasi):**
* Mirip dengan regresi, `vote_count` dan `budget` masih sangat penting, diikuti oleh genre dan tahun rilis.

![Feature Importance Random Forest Classifier](/assets/images/fi_rfc.png)
*Top 10 Feature Importance - Random Forest Classifier.*
![Feature Importance XGBoost Classifier](/assets/images/fi_xgbc.png)
*Top 10 Feature Importance - XGBoost Classifier.*

---

## Kesimpulan dan Implikasi Praktis

Framework yang kami kembangkan mampu memprediksi pendapatan dan mengklasifikasikan risiko ROI film secara efektif. Ini dapat membantu produser dan investor membuat keputusan investasi yang lebih objektif berdasarkan data pra-produksi, mengoptimalkan portofolio proyek, dan merencanakan strategi distribusi yang lebih baik. Wawasan dari analisis fitur juga berguna untuk alokasi anggaran produksi yang lebih efektif.

Meskipun model memiliki akurasi yang baik, penelitian ini memiliki keterbatasan pada jenis data yang digunakan (numerik dan kategorikal, sebagian besar pasar Amerika Utara). Pengembangan selanjutnya bisa mencakup integrasi data multimodal (visual poster, teks ulasan media sosial), analisis kausal, dan perluasan cakupan data ke pasar global.

---

## Makalah Lengkap

Untuk informasi lebih detail, Anda dapat mengunduh makalah penelitian lengkap kami:
[Unduh Makalah (PDF)](/assets/docs/Paper_Data_Mining.pdf)
---

## Kontak

Untuk pertanyaan atau kolaborasi, silakan hubungi saya:
* **Email:** ahyr23h@student.unhas.ac.id

**Anggota Kelompok Lainnya:**
* Pangeran Juhrifar Jafar (jafarpj23h@student.unhas.ac.id)
* Wahyu Rusman (rusmanw23h@student.unhas.ac.id)
* Zahra Salsabila (salsabilaz23h@student.unhas.ac.id)