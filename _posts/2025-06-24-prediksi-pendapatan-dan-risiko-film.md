# Prediksi Potensi Pendapatan dan Risiko Return on Investment (ROI) Film Menggunakan Machine Learning

**Oleh:** Harmelia Yuli Rahmatika A. (dan Tim Peneliti)
**Email:** ahyr23h@student.unhas.ac.id

---

## Inti Proyek

Proyek ini mengembangkan sistem Machine Learning untuk memprediksi pendapatan film dan menilai risiko investasinya (Return on Investment/ROI) berdasarkan data pra-rilis. [cite_start]Kami menggunakan algoritma Random Forest dan XGBoost, serta teknik penanganan data tidak seimbang (SMOTETomek) untuk meningkatkan akurasi. 

---

## Latar Belakang Masalah (Mengapa Proyek Ini Penting?)

[cite_start]Industri film adalah ladang investasi yang sangat berisiko.  [cite_start]Meskipun ada potensi pendapatan besar (mencapai 42,3 miliar dolar pada 2019 sebelum pandemi), lebih dari 60% film gagal menutup biaya produksi, dan hanya sekitar 25% yang menghasilkan keuntungan signifikan.  [cite_start]Keputusan investasi seringkali masih mengandalkan insting dan pengalaman, bukan data objektif, terutama untuk film berbiaya besar. 

[cite_start]Hal ini menimbulkan kebutuhan mendesak akan pendekatan yang lebih sistematis dan berbasis data untuk memprediksi pendapatan dan mengukur risiko investasi film secara objektif. 

**Pertanyaan Penelitian Utama:**
* [cite_start]Seberapa akurat data produksi dapat memprediksi pendapatan film? 
* [cite_start]Bagaimana mengembangkan metode klasifikasi risiko investasi berdasarkan prediksi ROI? 

---

## Metode Singkat

[cite_start]Kami mengumpulkan data dari API TMDb (10.247 film internasional 2000-2023)  dan melakukan beberapa langkah kunci:

1.  [cite_start]**Pra-pemrosesan Data:** Membersihkan data, mengisi nilai hilang (misal, anggaran kosong diisi median per genre/tahun). 
2.  **Rekayasa Fitur:** Membuat fitur baru seperti:
    * [cite_start]`release_year`, `release_month`, dan `Seasonal_Score` dari tanggal rilis. 
    * [cite_start]Encoding genre menjadi vektor biner. 
    * [cite_start]Normalisasi `popularity`. 
    * [cite_start]Fitur biner `lang_en` (bahasa Inggris) dan `lang_others`. 
3.  [cite_start]**Perhitungan ROI:** Dihitung dari keuntungan bersih dibagi anggaran. 
4.  [cite_start]**Klasifikasi Risiko ROI:** ROI dikategorikan ke dalam 5 kelas: Kerugian Ekstrem, Kerugian Signifikan, Keuntungan Marjinal, Keuntungan Baik, dan Blockbuster. 
5.  [cite_start]**Penanganan Ketidakseimbangan Kelas:** Menggunakan SMOTETomek karena data ROI sangat tidak seimbang (misal, 42% Kerugian Ekstrem, hanya 5% Blockbuster). 

**Diagram Alur Kerja Sistem:**
<div style="text-align: center;">
    <img src="assets/images/workflow.png" alt="Diagram Alur Kerja Sistem Prediksi ROI Film" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Diagram ini menunjukkan tahapan lengkap dari pengumpulan data hingga evaluasi model. </p>
</div>

---

## Hasil Utama

### Performa Prediksi Pendapatan (Regresi)
* [cite_start]**Akurasi:** Random Forest Regressor mencapai $R^{2}=0,7250$ pada data pengujian, sementara XGBoost Regressor sedikit lebih baik dengan $R^{2}=0,7390$. 
* [cite_start]**Overfitting:** Ada sedikit *overfitting* karena performa pada data pelatihan jauh lebih tinggi ($R^{2} \approx 0,95-0,96$) dibandingkan data pengujian, menunjukkan model terlalu kompleks untuk generalisasi sempurna. 

**Plot Aktual vs Prediksi XGBoost Regressor:**
<div style="text-align: center;">
    <img src="assets/images/apr_xgb.png" alt="Plot Aktual vs Prediksi XGBoost Regressor" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Perbandingan Pendapatan Aktual dan Prediksi oleh XGBoost Regressor.</p>
</div>

**Feature Importance (Regresi):**
* [cite_start]Fitur `budget` (anggaran produksi) dan `popularity` adalah kontributor paling dominan dalam memprediksi pendapatan film untuk kedua model. 
* [cite_start]`release_year`, `release_month`, dan `runtime` juga memiliki bobot yang signifikan. 

<div style="text-align: center;">
    <img src="assets/images/fi_rf.png" alt="Feature Importance Random Forest Regressor" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Top 15 Feature Importance - Random Forest Regressor.</p>
</div>
<div style="text-align: center;">
    <img src="assets/images/fi_xgb.png" alt="Feature Importance XGBoost Regressor" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Top 15 Feature Importance - XGBoost Regressor.</p>
</div>

### Performa Klasifikasi Risiko ROI

* [cite_start]**Akurasi:** XGBoost Classifier mencapai *weighted F1-score* 0,55, sedikit lebih baik dari Random Forest Classifier (0,53). 
* [cite_start]**Tantangan:** Kategori `Marginal Profit` dan `Significant Loss` masih menjadi tantangan utama dengan F1-score rendah, kemungkinan karena distribusi data yang sangat tidak seimbang dan tumpang tindih karakteristik. 

**Confusion Matrix (Contoh XGBoost Classifier):**
<div style="text-align: center;">
    <img src="assets/images/cf.png" alt="Confusion Matrix XGBoost Classifier" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Confusion Matrix untuk XGBoost Classifier.</p>
</div>

**Feature Importance (Klasifikasi):**
* Mirip dengan regresi, `vote_count` dan `budget` masih sangat penting, diikuti oleh genre dan tahun rilis.

<div style="text-align: center;">
    <img src="assets/images/fi_rfc.png" alt="Feature Importance Random Forest Classifier" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Top 10 Feature Importance - Random Forest Classifier.</p>
</div>
<div style="text-align: center;">
    <img src="assets/images/fi_xgbc.png" alt="Feature Importance XGBoost Classifier" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.08);">
    <p style="font-style: italic; font-size: 0.9em; color: #666; margin-top: 10px;">Top 10 Feature Importance - XGBoost Classifier.</p>
</div>

---

## Kesimpulan dan Implikasi Praktis

[cite_start]Framework yang kami kembangkan mampu memprediksi pendapatan dan mengklasifikasikan risiko ROI film secara efektif.  [cite_start]Ini dapat membantu produser dan investor membuat keputusan investasi yang lebih objektif berdasarkan data pra-produksi, mengoptimalkan portofolio proyek, dan merencanakan strategi distribusi yang lebih baik.  [cite_start]Wawasan dari analisis fitur juga berguna untuk alokasi anggaran produksi yang lebih efektif. 

[cite_start]Meskipun model memiliki akurasi yang baik, penelitian ini memiliki keterbatasan pada jenis data yang digunakan (numerik dan kategorikal, sebagian besar pasar Amerika Utara).  [cite_start]Pengembangan selanjutnya bisa mencakup integrasi data multimodal (visual poster, teks ulasan media sosial), analisis kausal, dan perluasan cakupan data ke pasar global. 

---

## Makalah Lengkap

Untuk informasi lebih detail, Anda dapat mengunduh makalah penelitian lengkap kami:
[Unduh Makalah (PDF)](assets/docs/Paper_Data_MiningFIX2 (1).pdf)

---

## Kontak

Untuk pertanyaan atau kolaborasi, silakan hubungi saya:
* **Email:** ahyr23h@student.unhas.ac.id
* **LinkedIn:** [Tambahkan tautan LinkedIn Anda di sini]
* **GitHub:** [Tambahkan tautan Profil GitHub Anda di sini]

**Anggota Kelompok Lainnya:**
* Pangeran Juhrifar Jafar (jafarpj23h@student.unhas.ac.id)
* Wahyu Rusman (rusmanw23h@student.unhas.ac.id)
* Zahra Salsabila (salsabilaz23h@student.unhas.ac.id)