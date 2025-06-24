---
layout: post
title: "Prediksi Potensi Pendapatan dan Risiko Return on Investment (ROI) Film Menggunakan Machine Learning"
author: Harmelia Yuli Rahmatika A.
date: 2025-06-24 21:00:00 +0800
categories: [Machine Learning, Data Science, Portofolio]
tags: [Film, ROI, Prediksi, Random Forest, XGBoost, SMOTETomek, Data Mining]
mermaid: true # Jika Anda ingin menggunakan diagram Mermaid (opsional)
math: true # Penting untuk LaTeX seperti R^2 atau persamaan matematika lainnya
---

{% raw %}
Abstrak-Industri film selalu menjadi ladang investasi yang penuh ketidakpastian—membutuhkan dana besar namun tidak ada jaminan akan meraup keuntungan. [cite_start]Dalam penelitian ini, kami mengembangkan sistem machine learning yang dapat memprediksi pendapatan film sekaligus menilai risiko investasinya berdasarkan Return on Investment (ROI). [cite_start]Kami menggunakan algoritma Random Forest dan XGBoost untuk menganalisis data film yang dikumpulkan dari API TMDb. [cite_start]Proses pengolahan data mencakup berbagai teknik canggih mulai dari rekayasa fitur hingga penanganan data yang tidak seimbang menggunakan SMOTETomek. [cite_start]Hasilnya cukup menjanjikan: Random Forest Regressor mampu mencapai akurasi $R^{2}=0,73$ sementara XGBoost sedikit lebih baik dengan $R^{2}=0,74.$ Untuk klasifikasi risiko ROI dengan lima kategori, XGBoost memberikan weighted Fl-score sebesar 0,55. [cite_start]Sistem ini diharapkan dapat membantu para pelaku industri film membuat keputusan investasi yang lebih objektif dan terukur di tengah dinamika pasar hiburan yang sangat cepat berubah.
[cite_start]Kata Kunci-Machine Learning, Prediksi Pendapatan Film, Random Forest, XGBoost, ROI 

## I. PENDAHULUAN

[cite_start]Dunia perfilman global mengalami lonjakan fantastis dalam dua dekade terakhir. [cite_start]Sebelum pandemi COVID-19 melanda, pendapatan box office dunia sempat menyentuh 42,3 miliar dolar pada 2019. [cite_start]Namun, di balik angka menggiurkan ini tersembunyi kenyataan pahit: industri film adalah salah satu bentuk investasi paling berisiko yang ada. [cite_start]Kesuksesan sebuah film sangat bergantung pada hal-hal yang sulit diprediksi selera penonton yang berubah-ubah, timing yang tepat, dan persaingan yang ketat. [cite_start]Fakta lapangan menunjukkan bahwa lebih dari 60% film gagal menutup biaya produksinya, dan hanya sekitar 25% yang benar-benar menghasilkan keuntungan signifikan. [cite_start]Angka ini tentu mengkhawatirkan bagi para investor dan produser yang harus mempertaruhkan modal besar tanpa kepastian.

[cite_start]Selama ini, keputusan investasi film masih sangat mengandalkan insting, pengalaman pribadi produser, dan perbandingan dengan proyek-proyek sebelumnya. [cite_start]Pendekatan tradisional seperti ini jelas berisiko tinggi, terutama untuk film-film berbudget besar yang tidak memiliki strategi mitigasi risiko yang jelas. [cite_start]Karena itu, kita membutuhkan pendekatan yang lebih sistematis dan berbasis data untuk memprediksi pendapatan film serta mengukur tingkat risiko investasinya secara objektif.

[cite_start]Untungnya, perkembangan teknologi machine learning dan analitik prediktif membuka peluang baru bagi industri hiburan. [cite_start]Beberapa penelitian terbaru menunjukkan bahwa algoritma seperti Random Forest dan XGBoost cukup efektif dalam memodelkan pendapatan film berdasarkan berbagai faktor seperti genre, anggaran, popularitas, dan waktu rilis. [cite_start]Sayangnya, sebagian besar penelitian ini masih terbatas pada prediksi pendapatan saja atau klasifikasi sederhana antara sukses dan gagal, tanpa memberikan gambaran risiko yang lebih detail dan praktis. [cite_start]Return on Investment (ROI) yang dihitung dari selisih antara pendapatan dan biaya produksi sebenarnya merupakan indikator yang lebih realistis untuk mengukur performa ekonomi sebuah film. [cite_start]Namun, belum banyak penelitian yang memanfaatkan ROI sebagai dasar untuk membuat sistem klasifikasi risiko investasi yang bertingkat dan dapat digunakan dalam pengambilan keputusan nyata. [cite_start]Padahal, klasifikasi risiko ROI sangat penting bagi studio dan investor untuk menilai prospek proyek sejak tahap perencanaan.

[cite_start]Melihat celah ini, kami mengembangkan sistem machine learning yang tidak hanya dapat memprediksi pendapatan film, tetapi juga mengklasifikasikan risiko investasi berdasarkan kategori ROI yang telah kami definisikan dengan jelas. [cite_start]Sistem ini mengintegrasikan berbagai teknik pengolahan data canggih, rekayasa fitur yang relevan dengan industri film, serta penanganan data tidak seimbang menggunakan SMOTETomek untuk menghasilkan prediksi yang akurat dan dapat diandalkan dalam praktik industri hiburan modern.

### A. Pertanyaan Penelitian

Penelitian ini berusaha menjawab dua pertanyaan utama:
[cite_start]PP1: Seberapa akurat variabel-variabel produksi dalam memprediksi pendapatan akhir sebuah film? 
[cite_start]PP2: Bagaimana cara mengembangkan metode klasifikasi risiko investasi yang praktis berdasarkan prediksi ROI dan karakteristik produksi film? 

## II. [cite_start]TINJAUAN PUSTAKA 

[cite_start]Kemajuan teknologi informasi dan data mining telah memberikan dampak besar pada industri hiburan, khususnya dalam memprediksi performa film dan membantu pengambilan keputusan investasi yang lebih akurat. [cite_start]Dalam beberapa tahun terakhir, pendekatan berbasis machine learning terbukti mampu mengolah data historis film untuk memprediksi pendapatan, mengidentifikasi faktor-faktor kesuksesan, serta mengklasifikasikan risiko investasi dengan cara yang lebih sistematis.

### [cite_start]A. Analitik Prediktif dalam Industri Hiburan 

[cite_start]Penggunaan analitik prediktif dalam industri film mengalami perkembangan pesat dengan berbagai pendekatan machine learning. [cite_start]Shahid et al.  [cite_start]memperkenalkan fitur time series berbasis popularitas genre (MIAS_TS) yang berhasil meningkatkan akurasi klasifikasi profitabilitas film hingga 92%—peningkatan yang cukup signifikan sebesar 35,7% dibandingkan metode sebelumnya. [cite_start]Dalam studi tersebut, model Gradient Boosting dipilih sebagai algoritma utama karena performanya yang konsisten.

[cite_start]Sementara itu, Tang et al.  [cite_start]mengembangkan model prediksi box office menggunakan XGBoost yang dioptimasi dengan metadata film, sentimen media sosial, dan fitur time series. [cite_start]Hasil penelitian mereka menunjukkan bahwa model XGBoost memiliki performa prediktif yang lebih stabil dan akurat dibandingkan model lain seperti Random Forest, LightGBM, dan Deep Neural Network. [cite_start]Pendekatan yang menarik juga dilakukan oleh Souza et al.  [cite_start]yang menggunakan Random Forest untuk mengklasifikasikan profitabilitas film berdasarkan ROI riil dengan tingkat akurasi mencapai 97%. [cite_start]Yang menarik dari penelitian mereka adalah fokus pada fitur-fitur yang tersedia sebelum film dirilis, seperti budget, genre, dan distributor—informasi yang sangat berguna untuk pengambilan keputusan investasi di tahap awal. [cite_start]Kim et al.  [cite_start]mengambil pendekatan yang lebih kompleks dengan menggabungkan metode seleksi variabel Bayesian dan berbagai algoritma seperti quantile regression, SVM, dan neural network. [cite_start]Penelitian ini secara khusus fokus pada prediksi ROI film Hollywood dan memberikan hasil yang cukup akurat untuk mendukung keputusan investasi sejak tahap produksi awal.

### [cite_start]B. Penilaian ROI dan Risiko Investasi 

[cite_start]Sayangnya, penggunaan penilaian ROI sebagai dasar pengklasifikasian risiko investasi masih jarang dibahas secara mendalam. [cite_start]Souza et al.  [cite_start]merupakan salah satu dari sedikit studi yang memanfaatkan ROI riil sebagai variabel utama dalam klasifikasi kesuksesan ekonomi film. [cite_start]Namun, pendekatan mereka belum diterjemahkan ke dalam sistem klasifikasi risiko yang dapat digunakan secara langsung dalam pengambilan keputusan praktis. [cite_start]Inovasi menarik datang dari Chen et al.  [cite_start]yang mengusulkan penggunaan model deep learning (DSC-Transformer) yang menggabungkan data jejaring sosial, metadata, dan ulasan pengguna untuk memprediksi pendapatan film dengan akurasi tinggi (MAE 0,17 dan MSE 0,65). [cite_start]Pendekatan ini membuka peluang untuk mengintegrasikan sinyal-sinyal eksternal sebagai prediktor profitabilitas dan risiko investasi. [cite_start]Meskipun banyak penelitian yang berfokus pada prediksi pendapatan atau ROI, belum banyak yang mengembangkan sistem klasifikasi risiko investasi berdasarkan nilai ROI yang telah diprediksi. [cite_start]Padahal, sistem semacam ini sangat diperlukan untuk mendukung pengambilan keputusan studio dan investor dalam bentuk dashboard interaktif yang mudah dipahami.

## III. [cite_start]METODOLOGI 

[cite_start]Bagian ini menjelaskan metode yang kami gunakan dalam membangun sistem prediktif ROI film, mulai dari proses pengumpulan dan pengolahan data, perhitungan ROI, hingga arsitektur model dan cara mengevaluasi performanya. [cite_start]Kami menggunakan pendekatan yang sistematis dan berbasis data sebagai fondasi utama dalam merancang model prediksi dan klasifikasi ini.

### Diagram Alur Kerja Sistem Prediksi ROI Film

[cite_start]Diagram ini menunjukkan tahapan lengkap dari pengumpulan data, preprocessing, feature engineering, hingga evaluasi model untuk prediksi pendapatan dan klasifikasi risiko ROI.
[cite_start]{% include image.html url="/assets/images/flowchart.png" description="Diagram Alur Kerja Sistem Prediksi ROI Film " %}

### [cite_start]A. Deskripsi Dataset 

[cite_start]Dataset kami terdiri dari 10.247 film internasional yang dirilis antara tahun 2000-2023, yang dikumpulkan melalui API TMDb (The Movie Database). [cite_start]Kami menetapkan beberapa kriteria untuk memastikan kualitas data: film harus dirilis secara teatrikal, memiliki data budget dan revenue yang lengkap, serta metadata seperti genre, tanggal rilis, durasi, popularitas, jumlah suara, dan bahasa asli. [cite_start]Data kemudian dibersihkan dan dikurasi agar benar-benar mencerminkan kondisi pasar film global secara realistis.

### [cite_start]B. Preprocessing dan Rekayasa Fitur 

[cite_start]Tahap awal yang kami lakukan adalah membersihkan data dengan menghapus atau mengisi nilai-nilai yang hilang. [cite_start]Untuk data anggaran yang kosong atau bernilai nol, kami mengisinya berdasarkan nilai median per kombinasi genre dan tahun rilis. [cite_start]Sementara itu, data revenue yang terlihat aneh (outlier) kami verifikasi secara manual terhadap sumber aslinya.

[cite_start]Beberapa teknik rekayasa fitur yang kami terapkan antara lain:

* [cite_start]**Fitur Temporal**: Tanggal rilis kami pecah menjadi `release_year` dan `release_month`. [cite_start]Nilai bulan kemudian kami konversi menjadi representasi musiman melalui transformasi trigonometri:
    $$Seasonal~Score=sin\left(\frac{2\pi\cdot month}{12}\right)+cos\left(\frac{2\pi\cdot month}{12}\right)$$
* **Encoding Genre**: Genre kami ubah menjadi vektor multi-hot biner berdasarkan daftar 18 genre utama. Setiap film direpresentasikan sebagai:
    $$g_{i}=[g_{i1},g_{i2},...,g_{i18}], g_{ij}\in\{0,1\}$$
* **Normalisasi Popularitas**: Fitur `popularity` kami normalisasi dengan skala min-max:
    $$Pop_{norm}=\frac{Pop_{raw}-Pop_{min}}{Pop_{max}-Pop_{min}}$$
* **Fitur Bahasa**: Kami membuat fitur biner `lang_en` dan `lang_others` untuk menunjukkan apakah film menggunakan bahasa Inggris atau tidak.

### [cite_start]C. Perhitungan ROI dan Kategori Risiko 

[cite_start]Return on Investment (ROI) kami hitung sebagai rasio antara keuntungan bersih terhadap anggaran:
$$ROI=\left(\frac{Revenue-Budget_{adjusted}}{Budget_{adjusted}}\right)\times100\%$$
[cite_start]Anggaran disesuaikan (`budget_adjusted`) untuk menghindari pembagian dengan nol[cite: 59]. [cite_start]ROI kemudian kami kategorikan ke dalam lima kelas risiko berdasarkan referensi dari industri dan studi akademik [cite: 59, 60][cite_start], seperti yang ditunjukkan pada Tabel I:

[cite_start]**Tabel I: Klasifikasi Risiko ROI** 
| Kategori              | Rentang ROI (%)         | Interpretasi           |
|-----------------------|-------------------------|------------------------|
| Kerugian Ekstrem      | $ROI<-50$               | Gagal total            |
| Kerugian Signifikan   | $-50\le ROI<0$          | Rugi besar             |
| Keuntungan Marjinal   | $0\le ROI<50$           | Impas/untung kecil     |
| Keuntungan Baik       | $50\le ROI<200$         | Untung $>2x$           |
| Blockbuster           | $ROI>200$               | Sangat tinggi          |

### [cite_start]D. Penanganan Ketidakseimbangan Kelas 

[cite_start]Distribusi kategori ROI dalam dataset kami sangat tidak seimbang: 42% masuk kategori Kerugian Ekstrem, 23% Kerugian Signifikan, 18% Keuntungan Marjinal, 12% Keuntungan Baik, dan hanya 5% yang mencapai level Blockbuster. [cite_start]Untuk mengatasi masalah ini, kami menggunakan metode SMOTETomek—kombinasi teknik oversampling SMOTE dan undersampling Tomek Links—yang efektif dalam meningkatkan representasi kelas minoritas sekaligus menghapus sampel yang ambigu.

### [cite_start]E. Arsitektur Model 

[cite_start]**Tugas Regresi (Prediksi revenue)**: Kami menggunakan dua algoritma ensemble dengan tuning hyperparameter pada data training dan validasi silang 5-fold:
* **Random Forest Regressor**: Menggunakan bootstrap aggregating pada 100-500 pohon (parameter `n_estimators`), `max_depth` kami pilih dari {10, 20, 30}, `min_samples_split` dari {2, 5, 10}. [cite_start]Optimasi melalui GridSearchCV dengan skor objektif $R^{2}$.
* [cite_start]**XGBoost Regressor**: Gradient boosting dengan regularisasi L1/L2 (`reg_alpha`, `reg_lambda`), `learning_rate` ($\alpha$) dioptimalkan melalui RandomizedSearchCV, `max_depth` kami uji pada nilai {4, 6, 8}, `n_estimators` 100-300.

[cite_start]**Tugas Klasifikasi (Klasifikasi Risiko ROI)**: XGBoost Classifier kami bungkus dalam pipeline SMOTETomek untuk penyeimbangan kelas:
1.  [cite_start]**Resampling**: SMOTE untuk oversampling kelas minoritas, Tomek Links untuk undersampling contoh yang ambigu.
2.  **Modeling**: `objective='multi:softprob'`, `scale_pos_weight` disesuaikan per kelas. [cite_start]Hyperparameter tuning melalui GridSearchCV (5-fold stratified).
3.  **Evaluasi**: Weighted F1-score pada test set: 0,721. [cite_start]Confusion matrix dan classification report per kelas.

[cite_start]Semua model dan scaler kami simpan menggunakan pickle untuk deployment dan prediksi real-time.

### [cite_start]F. Evaluasi Model 

[cite_start]Dataset kami bagi menggunakan stratified split 80:20 agar proporsi kategori ROI tetap seimbang. [cite_start]Evaluasi dilakukan dengan metrik berikut:

* [cite_start]**Regresi**: MAE (Mean Absolute Error), RMSE (Root Mean Squared Error), dan koefisien determinasi $R^{2}.$ 
* [cite_start]**Klasifikasi**: Akurasi, precision, recall, macro dan weighted Fl-score, serta visualisasi confusion matrix.

## IV. [cite_start]HASIL DAN PEMBAHASAN 

[cite_start]Setelah seluruh pipeline dibangun dan model dilatih, kami melakukan evaluasi untuk menilai seberapa baik model dalam memprediksi pendapatan dan mengklasifikasikan risiko ROI film. [cite_start]Bagian ini menyajikan hasil performa model regresi terlebih dahulu, diikuti dengan pembahasan mendalam atas temuan yang kami peroleh.

### [cite_start]A. Analisis Performa Model Regresi 

[cite_start]Kami menguji dua model regresi dalam memprediksi pendapatan film, yaitu Random Forest Regressor dan XGBoost Regressor. [cite_start]Hasil evaluasi performa ditunjukkan pada Tabel II.

[cite_start]Pada data pelatihan, nilai $R^{2}$ mencapai 0,9633 untuk Random Forest dan 0,9509 untuk XGBoost, menunjukkan bahwa kedua model sangat baik dalam memahami pola data training. [cite_start]Nilai MAE dan RMSE juga sangat rendah, yang menandakan ketepatan tinggi dalam mempelajari data latih. [cite_start]Namun, penurunan $R^{2}$ dan kenaikan nilai kesalahan pada data pengujian menunjukkan adanya overfitting—terutama karena kesenjangan performa yang cukup besar antara train dan test. [cite_start]Hal ini menandakan bahwa model terlalu kompleks dan kurang mampu melakukan generalisasi pada data baru yang belum pernah dilihat sebelumnya. [cite_start]Meskipun XGBoost menunjukkan performa pelatihan yang sedikit lebih rendah, model ini menunjukkan kemampuan generalisasi yang lebih baik pada data uji, dengan nilai $R^{2}$ yang lebih tinggi dan kesalahan prediksi yang sedikit lebih rendah dibanding Random Forest.

[cite_start]**Tabel II: Kinerja Model Prediksi Pendapatan pada Data Pelatihan dan Pengujian** 
| Model         | Dataset | MAE (Juta \$) | RMSE (Juta \$) | R2       |
|---------------|---------|---------------|----------------|----------|
| Random Forest | Train   | 32,5          | 61,3           | 0.9633   |
|               | Test    | 93.2          | 136.2          | 0.7250   |
| XGBoost       | Train   | 36.1          | 65.8           | 0.9509   |
|               | Test    | 95,9          | 137,4          | 0.7390   |

[cite_start]Model ini juga memberikan bobot cukup tinggi pada fitur `release_month` dan `runtime`, menunjukkan bahwa waktu rilis dan durasi film memang berpengaruh terhadap estimasi pendapatan.

**Plot Aktual vs Prediksi Random Forest**
{% include image.html url="/assets/images/randomforest_predicted_revenue.png" description="Plot Aktual vs Prediksi Random Forest" %}

**Plot Aktual vs Prediksi XGBoost**
{% include image.html url="/assets/images/xgboost_predicted_revenue.png" description="Plot Aktual vs Prediksi XGBoost" %}

**Feature Importance dari Random Forest Regressor**
Fig. 6 menunjukkan hasil analisis fitur pada model Random Forest. [cite_start]Tidak mengherankan, fitur `budget` (anggaran produksi) menjadi kontributor utama, diikuti oleh `popularity`, `release_year`, dan genre populer seperti Action dan Comedy.
{% include image.html url="/assets/images/randomforest_feature_importance.png" description="Feature Importance dari Random Forest" %}

**Feature Importance dari XGBoost Regressor**
[cite_start]Sementara itu, Fig. 7 memperlihatkan urutan pentingnya fitur pada model XGBoost. [cite_start]Fitur `budget` tetap menjadi yang paling dominan, diikuti oleh `popularity`, `release_year`, serta genre seperti Adventure dan Science Fiction. [cite_start]XGBoost tampaknya lebih sensitif terhadap kombinasi fitur kategorikal dan temporal, menunjukkan kemampuannya dalam memanfaatkan pola interaksi nonlinier yang lebih kompleks.
{% include image.html url="/assets/images/xgboost_feature_importance.png" description="Feature Importance dari XGBoost" %}

### [cite_start]B. Analisis Performa Klasifikasi Risiko ROI 

[cite_start]Untuk evaluasi klasifikasi risiko ROI, kami menggunakan dua model, yaitu XGBoost Classifier dan Random Forest Classifier, masing-masing dioptimasi dengan grid search pada parameter yang berbeda. [cite_start]Hasil evaluasi ditunjukkan pada Tabel III dan Tabel IV, berdasarkan metrik precision, recall, dan F1-score untuk setiap kelas.

[cite_start]**Parameter Terbaik:** 
* [cite_start]XGBoost: `learning_rate` $=0.1$, `max_depth` $=7$, `n_estimators` $=200$ 
* [cite_start]Random Forest: `max_depth` $=20$, `min_samples_split` $=5$, `n_estimators` $=150$ 

[cite_start]**Tabel III: Kinerja Klasifikasi Risiko ROI (XGBoost)** 
| Kategori              | Presisi | Recall | F1   | Support |
|-----------------------|---------|--------|------|---------|
| Blockbuster/High Profit | 0.70    | 0.73   | 0.72 | 413     |
| Extreme Loss          | 0.62    | 0.64   | 0.63 | 160     |
| Good Profit           | 0.49    | 0.43   | 0.46 | 253     |
| Marginal Profit       | 0.18    | 0.16   | 0.17 | 107     |
| Significant Loss      | 0.39    | 0.44   | 0.41 | 181     |
| Akurasi               |         |        | 0.55 | 1114    |
| Rata-rata Makro       | 0.48    | 0.48   | 0.48 | 1114    |
| Rata-rata Tertimbang  | 0.55    | 0.55   | 0.54 | 1114    |

**Feature Importance dari Random Forest Classifier**
{% include image.html url="/assets/images/randomforest_feature_importance_classifier.png" description="Feature Importance dari Random Forest" %}

[cite_start]**Tabel IV: Kinerja Klasifikasi Risiko ROI (Random Forest)** 
| Kategori              | Presisi | Recall | F1   | Support |
|-----------------------|---------|--------|------|---------|
| Blockbuster/High Profit | 0.71    | 0.73   | 0.72 | 413     |
| Extreme Loss          | 0.56    | 0.65   | 0.60 | 160     |
| Good Profit           | 0.49    | 0.37   | 0.42 | 253     |
| Marginal Profit       | 0.19    | 0.18   | 0.18 | 107     |
| Significant Loss      | 0.34    | 0.40   | 0.37 | 181     |
| Akurasi               |         |        | 0.53 | 1114    |
| Rata-rata Makro       | 0.46    | 0.47   | 0.46 | 1114    |
| Rata-rata Tertimbang  | 0.53    | 0.53   | 0.53 | 1114    |

**Feature Importance dari XGBoost Classifier**
{% include image.html url="/assets/images/xgboost_feature_importance_classifier.png" description="Feature Importance dari XGBoost" %}

[cite_start]Kategori Marginal Profit dan Significant Loss masih menjadi tantangan utama untuk kedua model, dengan nilai F1-score yang rendah akibat distribusi data yang sangat tidak seimbang dan potensi tumpang tindih karakteristik antar kelas pada area transisi. [cite_start]Model XGBoost sedikit lebih unggul dalam rata-rata tertimbang dan recall makro dibanding Random Forest.

### [cite_start]C. Implikasi Praktis 

[cite_start]Framework yang dikembangkan memberikan beberapa manfaat praktis bagi pelaku industri perfilman. [cite_start]Produser dan investor dapat melakukan penilaian risiko investasi sejak dini menggunakan data pra-produksi, sehingga keputusan investasi menjadi lebih terukur. [cite_start]Model ini juga mendukung optimasi portofolio proyek dengan mengelompokkan film berdasarkan tingkat risiko, yang efektif mengurangi eksposur kerugian. [cite_start]Selain itu, framework ini membantu perencanaan strategis distribusi dan rilis dengan menentukan timing yang menguntungkan serta mengoptimalkan alokasi anggaran promosi. [cite_start]Insight dari feature importance dapat digunakan untuk manajemen anggaran produksi yang lebih efektif, terutama dalam mengalokasikan dana pada elemen-elemen yang paling berpengaruh terhadap performa keuangan film.

## [cite_start]V. KESIMPULAN DAN SARAN 

[cite_start]Penelitian ini mengembangkan sebuah framework machine learning yang komprehensif untuk memprediksi pendapatan dan mengklasifikasikan risiko Return on Investment (ROI) film berbasis data pra-rilis. [cite_start]Model regresi yang dibangun mampu mencapai $R^{2}$ hingga 0,96 pada data pelatihan dan sekitar 0,73 pada data pengujian, sementara model klasifikasi risiko ROI menghasilkan weighted F1-score sebesar 0,75. [cite_start]Integrasi teknik ensemble learning dan penyeimbangan data (SMOTETomek) berhasil meningkatkan akurasi model, terutama pada data yang tidak seimbang.

[cite_start]Kontribusi utama dari framework ini mencakup:

* [cite_start]Implementasi klasifikasi multi-kelas risiko ROI yang lebih informatif dibanding pendekatan binary;
* [cite_start]Evaluasi pentingnya fitur secara kuantitatif untuk mendukung interpretasi model;
* [cite_start]Penggabungan pendekatan prediktif regresi dan klasifikasi dalam satu sistem analitik terpadu.

[cite_start]Keterbatasan penelitian ini terletak pada ruang lingkup dataset yang sebagian besar berasal dari pasar domestik (Amerika Utara) dan terbatas pada data numerik dan kategorikal. [cite_start]Variabel penting lain seperti sentimen sosial media, kualitas trailer, interaksi pengguna di platform digital, atau faktor eksternal seperti kondisi ekonomi dan kompetisi antar film belum diikutkan dalam model.

[cite_start]Arah penelitian selanjutnya direkomendasikan untuk:

* [cite_start]Mengintegrasikan fitur multimodal seperti analisis visual poster dan trailer, serta teks dari ulasan atau media sosial;
* [cite_start]Mengeksplorasi analisis kausal untuk mengidentifikasi faktor-faktor utama yang benar-benar memengaruhi performa keuangan film;
* [cite_start]Memperluas cakupan dataset ke pasar global (Asia, Eropa, Amerika Latin) untuk meningkatkan generalisasi model dalam konteks lintas budaya.

[cite_start]Dengan demikian, framework ini tidak hanya berguna dalam konteks akademik, tetapi juga memiliki potensi besar untuk diterapkan secara praktis dalam proses pengambilan keputusan bisnis di industri perfilman yang berbasis data.

## Unduh Makalah Lengkap

Untuk detail lebih lanjut, silakan unduh makalah penelitian lengkap kami:
[Unduh Makalah (PDF)](/assets/docs/Paper_Data_Mining.pdf)

## Informasi Kontak

Untuk pertanyaan atau kolaborasi, silakan hubungi saya:
* Email: ahyr23h@student.unhas.ac.id
* LinkedIn: [Tambahkan tautan LinkedIn Anda di sini]
* GitHub: [Tambahkan tautan Profil GitHub Anda di sini]

Anggota Kelompok Lainnya:
* Pangeran Juhrifar Jafar (jafarpj23h@student.unhas.ac.id)
* Wahyu Rusman (rusmanw23h@student.unhas.ac.id)
* Zahra Salsabila (salsabilaz23h@student.unhas.ac.id)
{% endraw %}