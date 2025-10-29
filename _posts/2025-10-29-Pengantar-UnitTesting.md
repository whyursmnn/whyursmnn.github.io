# 🧪 Pengantar Unit Testing

## 📘 Definisi: Apa itu Unit Testing
**Unit Testing** adalah proses pengujian terhadap komponen terkecil dari perangkat lunak — biasanya fungsi, metode, atau kelas — untuk memastikan bahwa bagian tersebut berfungsi sebagaimana mestinya secara terisolasi dari bagian lainnya.  
Tujuan utama dari unit testing adalah untuk **mendeteksi bug lebih awal**, sebelum perangkat lunak digabungkan ke tahap pengujian yang lebih besar (seperti integration atau system testing).

---

## 🌟 Keunggulan Unit Testing
Mengapa Unit Testing penting?

1. ✅ **Deteksi dini bug** — kesalahan dapat ditemukan sebelum tahap integrasi.
2. 🧩 **Kode lebih modular** — memaksa pengembang menulis fungsi kecil yang bisa diuji.
3. 🔁 **Mendukung refactoring** — memastikan perubahan kode tidak merusak fungsionalitas lama.
4. 🚀 **Meningkatkan kepercayaan diri dalam deployment** — karena setiap unit telah terverifikasi.
5. 📊 **Dokumentasi otomatis** — setiap tes menjelaskan bagaimana fungsi seharusnya berperilaku.

---

## 🧰 Framework & Tools Populer
Berikut beberapa framework unit testing yang sering digunakan berdasarkan bahasa pemrograman:

| Bahasa Pemrograman | Framework Populer | Website |
|--------------------|-------------------|----------|
| **Python** | Pytest | [docs.pytest.org](https://docs.pytest.org/en/stable/) |
| **Java** | JUnit | [junit.org](https://junit.org/) |
| **JavaScript/TypeScript** | Jest | [jestjs.io](https://jestjs.io/) |

Framework ini menyediakan struktur dan *assertion tools* untuk mempermudah pengujian otomatis.

---

## 🧩 Struktur Tes: Pola Arrange – Act – Assert (AAA)
Pendekatan **AAA (Arrange, Act, Assert)** adalah pola umum dalam menulis unit test:

1. **Arrange** — siapkan data, objek, atau kondisi awal untuk pengujian.  
2. **Act** — jalankan fungsi atau metode yang ingin diuji.  
3. **Assert** — verifikasi hasil aktual dengan hasil yang diharapkan.

Contoh alur:
```plaintext
Arrange → Membuat input berat = 70 kg, tinggi = 170 cm  
Act → Memanggil fungsi hitung_bmi(70, 170)  
Assert → Memastikan hasilnya = 24.22 (kategori: Normal)
