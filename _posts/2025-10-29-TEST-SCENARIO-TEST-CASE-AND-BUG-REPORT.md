# 🧩 TEST SCENARIO, TEST CASE, AND BUG REPORT

## 1. Pengantar

### Apa itu Test Scenario?
**Test Scenario** adalah deskripsi tingkat tinggi yang menggambarkan *apa yang akan diuji* dalam suatu aplikasi.  
Skenario ini membantu memastikan bahwa semua alur dan fungsi penting sistem telah ter-cover dalam pengujian.

> Contoh: “Memverifikasi hasil perhitungan BMI berdasarkan input berat dan tinggi badan.”

### Apa itu Test Case?
**Test Case** adalah dokumen yang menjabarkan langkah-langkah detail, data uji, dan hasil yang diharapkan untuk memverifikasi fungsionalitas tertentu dari aplikasi.  
Test Case berasal dari Test Scenario dan menjadi acuan teknis bagi QA saat melakukan eksekusi pengujian.

> Contoh: “Memasukkan berat badan 60 kg dan tinggi badan 170 cm, kemudian memverifikasi hasil BMI yang dihitung.”

---

## 2. Template Sederhana

### 🧾 Template Test Scenario

| No | Test Scenario ID | Deskripsi Skenario | Prioritas | Status |
|----|-------------------|--------------------|------------|--------|
| 1 | TS-BMI-01 | Memverifikasi perhitungan BMI berdasarkan input berat dan tinggi | High | Open |
| 2 | TS-BMI-02 | Memverifikasi validasi input ketika field kosong | Medium | Open |

---

### 🧾 Template Test Case

| No | Test Case ID | Test Scenario ID | Deskripsi Test Case | Langkah Uji | Data Uji | Hasil yang Diharapkan | Hasil Aktual | Status |
|----|----------------|-------------------|----------------------|--------------|-----------|------------------------|----------------|----------|
| 1 | TC-BMI-001 | TS-BMI-01 | Menghitung BMI dengan input valid | 1. Buka aplikasi BMI<br>2. Masukkan berat 60 kg<br>3. Masukkan tinggi 170 cm<br>4. Tekan tombol “Hitung” | Berat: 60<br>Tinggi: 170 | BMI = 20.76<br>Kategori: Normal | Sesuai | Pass |
| 2 | TC-BMI-002 | TS-BMI-02 | Menguji respon jika field berat kosong | 1. Buka aplikasi<br>2. Biarkan kolom berat kosong<br>3. Isi tinggi 170 cm<br>4. Klik “Hitung” | Berat: kosong<br>Tinggi: 170 | Muncul pesan error “Masukkan berat badan dengan benar” | Tidak muncul pesan error | Fail |
| 3 | TC-BMI-003 | TS-BMI-01 | Menghitung BMI dengan data ekstrem (berat tinggi, tinggi pendek) | 1. Masukkan berat 120 kg<br>2. Masukkan tinggi 150 cm<br>3. Tekan “Hitung” | Berat: 120<br>Tinggi: 150 | BMI = 53.33<br>Kategori: Obese | Sesuai | Pass |
| 4 | TC-BMI-004 | TS-BMI-02 | Memasukkan data teks pada field berat | 1. Isi berat dengan “enampuluh”<br>2. Isi tinggi 170 cm<br>3. Klik “Hitung” | Berat: “enampuluh” | Muncul pesan error input tidak valid | Tidak ada pesan error | Fail |

---

## 3. Test Scenario & Test Case untuk Aplikasi BMI

### 📱 Deskripsi Singkat Aplikasi
Aplikasi **Pengukuran BMI** menghitung indeks massa tubuh berdasarkan input:
- **Berat badan (kg)**
- **Tinggi badan (cm)**  
Aplikasi menampilkan hasil BMI dan klasifikasi:
- `<18.5` → Underweight  
- `18.5–24.9` → Normal  
- `25–29.9` → Overweight  
- `≥30` → Obese  

---

### 📋 Test Scenario List

| No | Test Scenario ID | Deskripsi | Prioritas |
|----|-------------------|------------|------------|
| 1 | TS-BMI-01 | Menghitung BMI dengan input valid | High |
| 2 | TS-BMI-02 | Validasi input kosong | Medium |
| 3 | TS-BMI-03 | Validasi input non-numerik | Medium |
| 4 | TS-BMI-04 | Verifikasi kategori BMI | High |
| 5 | TS-BMI-05 | Pengujian UI tombol “Hitung” dan tampilan hasil | Low |

---

### 🧮 Test Case Detail

| No | Test Case ID | Scenario | Langkah Pengujian | Data Uji | Hasil yang Diharapkan | Status |
|----|----------------|-----------|--------------------|-----------|------------------------|----------|
| 1 | TC-BMI-001 | TS-BMI-01 | Isi berat: 60<br>Isi tinggi: 170<br>Klik “Hitung” | Berat=60, Tinggi=170 | BMI=20.76, kategori Normal | Pass |
| 2 | TC-BMI-002 | TS-BMI-02 | Biarkan kolom berat kosong, isi tinggi: 170, klik “Hitung” | Berat=kosong, Tinggi=170 | Pesan error muncul “Masukkan berat badan dengan benar” | Fail |
| 3 | TC-BMI-003 | TS-BMI-03 | Isi berat dengan huruf “abc”, tinggi: 170 | Berat=abc, Tinggi=170 | Pesan error input tidak valid | Fail |
| 4 | TC-BMI-004 | TS-BMI-04 | Isi berat: 45, tinggi: 165 | Berat=45, Tinggi=165 | BMI=16.5 → kategori Underweight | Pass |
| 5 | TC-BMI-005 | TS-BMI-05 | Tekan tombol “Hitung” tanpa mengisi data apapun | Kosong semua | Tombol tidak aktif / muncul pesan error | Pass |

---

## 4. Bug Report

### 📖 Definisi
**Bug Report** adalah dokumen yang berisi detail tentang kesalahan (defect) yang ditemukan selama pengujian.  
Laporan bug digunakan oleh developer untuk **mereproduksi, memahami, dan memperbaiki** masalah yang terjadi pada sistem.

### Tujuan Bug Report
- Memberikan **informasi lengkap dan jelas** tentang bug.  
- Membantu **developer menemukan akar masalah**.  
- Memastikan **bug dapat diverifikasi setelah diperbaiki** (retesting).

---

### 🧾 Template Sederhana Bug Report

| Field | Deskripsi |
|--------|------------|
| **Bug ID** | Nomor unik bug |
| **Title** | Judul singkat bug |
| **Module** | Modul atau fitur terkait |
| **Severity** | Tingkat keparahan (Low/Medium/High/Critical) |
| **Priority** | Tingkat urgensi perbaikan |
| **Environment** | OS, browser, versi aplikasi |
| **Steps to Reproduce** | Langkah-langkah untuk menimbulkan bug |
| **Expected Result** | Hasil yang seharusnya terjadi |
| **Actual Result** | Hasil aktual yang muncul |
| **Status** | Open / Fixed / Closed |
| **Assigned To** | Developer yang menangani |
| **Attachment** | Screenshot atau log error (opsional) |

---

### 🐞 Contoh Bug Report  
**Kasus:** Field input berat tidak menampilkan pesan error saat dikosongkan.

| Field | Isi |
|--------|-----|
| **Bug ID** | BUG-BMI-002 |
| **Title** | Tidak muncul pesan error ketika field berat kosong |
| **Module** | Input Validasi Berat Badan |
| **Severity** | Medium |
| **Priority** | High |
| **Environment** | Android 13, BMI App v1.0 |
| **Steps to Reproduce** | 1. Buka aplikasi BMI<br>2. Biarkan kolom berat kosong<br>3. Isi tinggi badan 170 cm<br>4. Klik tombol “Hitung” |
| **Expected Result** | Muncul pesan error: “Masukkan berat badan dengan benar.” |
| **Actual Result** | Tidak muncul pesan apapun, aplikasi tetap menghitung BMI dengan hasil `NaN` |
| **Status** | Open |
| **Assigned To** | Developer - Siti Rahma |
| **Attachment** | Screenshot_bug_bmi_empty_weight.png |

---

## 5. Kesimpulan

- **Test Scenario** memberikan gambaran umum apa yang diuji.  
- **Test Case** memberikan rincian langkah dan hasil yang diharapkan.  
- **Bug Report** menjadi dokumen penting untuk komunikasi antara QA dan developer.  

Dengan kombinasi ketiganya, proses *Software Quality Assurance (SQA)* dapat berjalan sistematis dan efisien.

---

📚 **Sumber Referensi:**
- Belajar SQA Dasar #4: *Membuat Test Case (Part 1)*  
- Belajar SQA Dasar #5: *Membuat Test Case (Part 2)*  
- Belajar SQA Dasar #6: *Membuat Bug Report*  
- IEEE Standard 829 – *Software Test Documentation*  
- Pressman, R. S. (2010). *Software Engineering: A Practitioner’s Approach.*
