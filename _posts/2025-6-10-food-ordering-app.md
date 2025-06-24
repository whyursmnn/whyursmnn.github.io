# Aplikasi Pemesanan Makanan & Minuman (Android)

**Oleh:** Wahyu Rusman
**Email:** wahyurusman31@gmail.com

---

## Inti Proyek

Proyek ini adalah simulasi sederhana aplikasi pemesanan makanan dan minuman berbasis Android. Berfokus pada pengembangan antarmuka pengguna yang modern dan fungsionalitas inti yang biasa ditemukan pada aplikasi sejenis. Aplikasi ini dirancang untuk menunjukkan kemampuan dalam membangun aplikasi mobile yang lengkap, mulai dari autentikasi pengguna hingga integrasi API eksternal dan pengelolaan data.

---

## Latar Belakang Masalah (Tujuan & Relevansi Proyek)

Dalam era digital saat ini, aplikasi pemesanan makanan dan minuman telah menjadi bagian integral dari kehidupan sehari-hari, menawarkan kenyamanan dan efisiensi. Proyek ini bertujuan untuk mensimulasikan pengalaman pengguna dalam aplikasi semacam itu, sekaligus mengeksplorasi implementasi teknis dari fitur-fitur penting. Ini adalah kesempatan untuk mendemonstrasikan pemahaman tentang pengembangan Android, integrasi API, pengelolaan data lokal, dan desain UI/UX, yang relevan dalam mengembangkan solusi digital di industri kuliner dan layanan.

---

## Fitur Utama

Aplikasi ini dirancang untuk memberikan pengalaman pemesanan yang mulus dengan fitur-fitur berikut:

* **Autentikasi Pengguna:** Memungkinkan pendaftaran akun dan login sederhana.
* **Penjelajahan Menu:** Pengguna dapat menjelajahi daftar menu makanan dan minuman.
* **Pencarian & Filter Menu:** Kemampuan mencari menu berdasarkan kata kunci dan memfilter menu berdasarkan kategori.
* **Manajemen Keranjang Belanja:** Menambahkan item ke keranjang dan mengatur kuantitas.
* **Ringkasan Pesanan & Simulasi Checkout:** Pengguna dapat melihat ringkasan pesanan dan mensimulasikan proses checkout.
* **Pencatatan Pesanan ke Google Sheets:** Mengirim data pesanan ke Google Sheets.
* **Pengaturan Tema:** Mengubah tema aplikasi antara mode terang dan gelap.
* **Dukungan Offline:** Mengakses data offline jika koneksi internet terputus.

---

## Implementasi Teknis Singkat

Aplikasi ini dibangun menggunakan **Android Studio** dengan bahasa pemrograman **Java**.

* **Arsitektur:** Menggunakan `Activity` sebagai host utama dan `Fragment` untuk bagian-bagian UI yang berbeda, diatur menggunakan **Navigation Component**.
* **Pengambilan Data:** Data menu diambil dari **Spoonacular API** menggunakan library **Retrofit** dan **Gson**. Paginasi (infinite scrolling) diimplementasikan untuk memuat data secara bertahap.
* **Autentikasi:** Sistem login dan pendaftaran sederhana menggunakan **SharedPreferences** untuk menyimpan kredensial akun secara lokal.
* **Keranjang Belanja:** Data keranjang dikelola oleh kelas `CartManager` (singleton) dan disimpan secara persisten menggunakan **SharedPreferences**.
* **Integrasi Google Sheets:** Data pesanan dikirim ke Google Sheets melalui API Web yang dibangun dengan **Google Apps Script**.
* **Tema:** Aplikasi mendukung tema terang dan gelap, preferensi disimpan di **SharedPreferences** dan diterapkan saat `Activity` diluncurkan.
* **Penanganan Offline:** Aplikasi dapat menampilkan data yang di-cache dari **SharedPreferences** sebagai *fallback* jika tidak ada koneksi internet atau panggilan API gagal.

---

## Cara Penggunaan (Panduan Singkat)

1.  **Luncurkan Aplikasi:** Aplikasi akan dimulai dengan *splash screen*.
2.  **Login/Daftar:** Jika ini pertama kali, Anda akan diarahkan ke halaman daftar. Buat akun baru, lalu login.
3.  **Jelajahi Menu:** Di halaman utama, Anda dapat melihat daftar menu. Gunakan kategori di bagian atas atau bilah pencarian untuk menemukan item spesifik.
4.  **Tambah ke Keranjang:** Klik item menu untuk melihat detailnya, lalu tambahkan ke keranjang dengan kuantitas yang diinginkan.
5.  **Ringkasan Pesanan & Checkout:** Pergi ke tab "Keranjang", lalu klik "Lanjutkan Pembayaran" untuk melihat ringkasan pesanan. Klik "PESAN SEKARANG" untuk mensimulasikan pembayaran dan mencatat pesanan Anda ke Google Sheets.
6.  **Pengaturan Tema:** Di tab "Settings", Anda dapat beralih antara tema terang dan gelap.
7.  **Logout:** Tombol "Logout" juga tersedia di tab "Settings".


### Screenshot Aplikasi
![Tampilan Utama Aplikasi](/assets/images/docs_app.jpeg)
*Tampilan utama aplikasi pemesanan makanan.*

---

## Persyaratan & Konfigurasi

Untuk menjalankan atau mengembangkan aplikasi ini, Anda memerlukan:

* **Android Studio** dan **JDK**.
* **API Key Spoonacular:** Diperlukan untuk mengambil data menu. Pastikan Anda memasukkan API Key Anda di `HomeFragment.java`.
* **Google Sheet & Google Apps Script:** Diperlukan untuk fitur pencatatan pesanan. Anda harus mendeploy Google Apps Script sebagai aplikasi web dan memasukkan URL yang benar di `OrderSummaryFragment.java`.

---

## Kontak

Untuk pertanyaan atau kolaborasi, silakan hubungi saya:
* **Email:** wahyurusman31@gmail.com
* **LinkedIn:** (www.linkedin.com/in/wahyu-rusman-91b722280)
* **GitHub:** (https://github.com/whyursmnn/Food-End-Drink-Projek-Akhir-Mobile)