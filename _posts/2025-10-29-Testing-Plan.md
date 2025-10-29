# 🧾 Software Testing Plan (IEEE 829 Format)

## 1. Review: Apa itu Testing Plan?

### Definisi
**Testing Plan** adalah dokumen formal yang menjelaskan strategi, ruang lingkup, pendekatan, dan jadwal kegiatan pengujian perangkat lunak.  
Dokumen ini menjadi acuan bagi tim QA untuk memastikan bahwa proses testing berjalan **terstruktur, konsisten, dan dapat ditelusuri**.

### Tujuan Testing Plan
- Menentukan **lingkup dan strategi pengujian**.  
- Menetapkan **tujuan pengujian dan kriteria keberhasilan**.  
- Menjelaskan **sumber daya, jadwal, dan tanggung jawab** tim QA.  
- Memberikan **pedoman pelaksanaan testing** yang jelas.  
- Meminimalkan risiko kesalahan atau pengujian yang tidak terarah.

---

## 2. IEEE 829 Test Plan Outline

Berikut struktur **IEEE 829 Test Plan** menurut standar:

1. Test Plan Identifier  
2. Introduction  
3. Test Items  
4. Features to be Tested  
5. Features Not to be Tested  
6. Approach  
7. Item Pass/Fail Criteria  
8. Suspension Criteria and Resumption Requirements  
9. Test Deliverables  
10. Testing Tasks  
11. Environmental Needs  
12. Responsibilities  
13. Staffing and Training Needs  
14. Schedule  
15. Risks and Contingencies  
16. Approvals  

---

## 3. Contoh Dokumen Testing Plan  
### Kasus: *Aplikasi Pengukuran BMI Sederhana*

---

### 1. Test Plan Identifier  
**TP-BMI-APP-001**  
Dokumen rencana pengujian untuk *Aplikasi Pengukuran BMI v1.0*

---

### 2. Introduction  
Dokumen ini menjelaskan rencana pengujian untuk aplikasi pengukuran BMI sederhana.  
Aplikasi ini menerima input berat badan (kg) dan tinggi badan (cm), menghitung nilai BMI, serta menampilkan kategori:  
- Underweight  
- Normal  
- Overweight  
- Obese  

Tujuan utama pengujian adalah untuk memastikan fungsi perhitungan dan tampilan hasil bekerja dengan benar sesuai spesifikasi.

---

### 3. Test Items  
Item yang akan diuji meliputi:
- Input berat badan (Field “Weight”)  
- Input tinggi badan (Field “Height”)  
- Tombol “Calculate”  
- Tampilan hasil BMI  
- Klasifikasi kategori BMI  

---

### 4. Features to be Tested  
- Validasi input numerik (angka positif, bukan teks)  
- Akurasi perhitungan BMI dengan rumus `BMI = weight / (height/100)^2`  
- Tampilan kategori sesuai nilai BMI  
- Respons sistem terhadap input kosong atau tidak valid  

---

### 5. Features Not to be Tested  
- Integrasi dengan perangkat eksternal (misalnya smart scale)  
- Penyimpanan data pengguna  
- Fitur multi-bahasa  

---

### 6. Approach  
Metode pengujian yang digunakan adalah **Black Box Testing** dengan pendekatan **Functional Testing**, yaitu:
- Menguji input dan output berdasarkan spesifikasi tanpa mengetahui kode sumber.  
- Fokus pada hasil perhitungan dan tampilan kategori.  

Jenis testing yang dilakukan:
- **Unit Testing** (fungsi perhitungan BMI)  
- **System Testing** (antarmuka pengguna dan validasi input)  
- **Usability Testing** (kemudahan penggunaan form input dan interpretasi hasil)

---

### 7. Item Pass/Fail Criteria  
- **Pass:** Jika hasil perhitungan BMI dan kategori sesuai spesifikasi.  
- **Fail:** Jika terjadi kesalahan perhitungan, input tidak tervalidasi, atau hasil tampilan salah.  

---

### 8. Suspension Criteria and Resumption Requirements  
- **Suspension:** Pengujian dihentikan jika sistem crash atau nilai BMI yang dihasilkan tidak sesuai rumus dasar.  
- **Resumption:** Pengujian dilanjutkan setelah bug diperbaiki dan build terbaru disediakan.  

---

### 9. Test Deliverables  
- Test Plan (dokumen ini)  
- Test Case Document (dikosongkan sesuai arahan)  
- Test Execution Report  
- Bug Report  
- Final Test Summary Report  

---

### 10. Testing Tasks  
| No | Task | Deskripsi | PIC |
|----|------|------------|-----|
| 1 | Persiapan Lingkungan | Instalasi aplikasi BMI pada perangkat uji | QA Engineer |
| 2 | Pembuatan Test Case | Menulis skenario dan test case pengujian fungsi BMI | QA Engineer |
| 3 | Eksekusi Testing | Menjalankan test case dan mencatat hasil | QA Engineer |
| 4 | Pelaporan | Membuat laporan hasil pengujian dan bug list | QA Lead |

---

### 11. Environmental Needs  
- **Perangkat:** Laptop/Smartphone Android  
- **Sistem Operasi:** Windows 10 / Android 13  
- **Perangkat Lunak:** Python/Java Runtime (jika diperlukan)  
- **Alat Testing:** Manual testing menggunakan Excel dan Google Sheets  

---

### 12. Responsibilities  
| Peran | Tanggung Jawab |
|--------|----------------|
| QA Lead | Menyusun test plan, mengatur jadwal testing |
| QA Engineer | Membuat test case, melaksanakan testing |
| Developer | Memperbaiki bug berdasarkan laporan |
| Project Manager | Menyetujui dokumen dan hasil akhir testing |

---

### 13. Staffing and Training Needs  
- Tim QA memerlukan pemahaman dasar tentang:
  - Rumus BMI  
  - Prinsip validasi input  
  - Dasar *functional testing*  
- Pelatihan singkat terkait alat bantu pelaporan bug (misalnya Trello atau Jira).

---

### 14. Schedule  
| Aktivitas | Tanggal Mulai | Tanggal Selesai |
|------------|----------------|----------------|
| Penyusunan Test Plan | 1 Nov 2025 | 2 Nov 2025 |
| Pembuatan Test Case | 3 Nov 2025 | 4 Nov 2025 |
| Eksekusi Testing | 5 Nov 2025 | 6 Nov 2025 |
| Laporan Akhir | 7 Nov 2025 | 7 Nov 2025 |

---

### 15. Risks and Contingencies  
| Risiko | Dampak | Mitigasi |
|---------|----------|-----------|
| Keterlambatan build aplikasi | Menunda jadwal testing | Komunikasi intensif dengan developer |
| Bug mayor pada fungsi utama | Menghambat progress testing | Lakukan retesting setelah bug diperbaiki |
| Kurangnya dokumentasi spesifikasi | Pengujian tidak terarah | Konsultasi dengan tim pengembang |

---

### 16. Approvals  
| Nama | Jabatan | Tanggal | Tanda Tangan |
|-------|----------|----------|---------------|
| Andi Pratama | QA Lead | 2 Nov 2025 | _(digital signature)_ |
| Budi Santoso | Project Manager | 2 Nov 2025 | _(digital signature)_ |
| Siti Rahma | Developer | 2 Nov 2025 | _(digital signature)_ |

---

## 4. Catatan Tambahan
Bagian **Test Scenario** dan **Test Case** akan disiapkan oleh **kelompok 4** sesuai pembagian tugas, dan akan dimasukkan dalam dokumen lanjutan *Test Case Specification (IEEE 829 Section 4)*.

---

📘 **Referensi:**
- IEEE Standard 829-1998: *Software Test Documentation.*  
- Pressman, R. S. (2010). *Software Engineering: A Practitioner’s Approach.*  
- ISTQB Foundation Level Syllabus.

