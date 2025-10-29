# 🔗 Pengantar API Testing

---

## 📘 1. Definisi: Apa itu API Testing
**API Testing (Application Programming Interface Testing)** adalah proses pengujian yang berfokus pada **lapisan logika bisnis dan komunikasi antar komponen** dalam sebuah sistem, bukan pada tampilan antarmuka (UI).  
API Testing memastikan bahwa endpoint yang disediakan oleh sistem **berfungsi sesuai spesifikasi**, mengembalikan **data yang benar**, dan **menangani error dengan baik**.

Contohnya:  
Ketika aplikasi BMI mobile meminta data dari server (`/api/hitung_bmi`), pengujian API memastikan endpoint tersebut menghitung BMI dengan benar dan mengembalikan hasil sesuai format JSON yang diharapkan.

---

## 🌟 Keunggulan: Kenapa Pengujian API Itu Penting
Mengapa API Testing menjadi krusial dalam pengembangan modern?

1. ⚙️ **Menguji logika inti tanpa UI** — mempercepat proses pengujian karena tidak perlu menjalankan front-end.  
2. 🔍 **Validasi integrasi antar sistem** — memastikan komunikasi antar aplikasi (misal: mobile app ↔️ server) berjalan lancar.  
3. 🚀 **Lebih cepat dan stabil dibanding UI testing** — tidak tergantung perubahan tampilan visual.  
4. 🧩 **Deteksi bug lebih awal** — memeriksa error di level logika sebelum pengguna mengalaminya.  
5. 🔐 **Meningkatkan keamanan** — memastikan endpoint tidak bocor atau menerima input berbahaya (injection, invalid data, dll).

---

## 🧰 Tools Populer untuk API Testing
Beberapa tool yang sering digunakan oleh Software Quality Assurance (SQA) engineer:

| Tool | Deskripsi Singkat | Website |
|------|--------------------|----------|
| **Postman** | Tool paling populer untuk mengirim request HTTP (GET, POST, PUT, DELETE) dan memverifikasi respons. | [postman.com](https://www.postman.com/) |
| **SoapUI** | Alat open-source untuk menguji SOAP dan REST API dengan skenario kompleks. | [soapui.org](https://www.soapui.org/) |

> 💡 **Postman** biasanya digunakan untuk RESTful API, sedangkan **SoapUI** cocok untuk API berbasis SOAP/XML.

---

## 🧩 Konsep Dasar: Anatomi Request & Response API
Sebelum melakukan testing, penting memahami **struktur dasar komunikasi HTTP**:

### 📨 Request API
Sebuah request biasanya terdiri dari:
- **URL / Endpoint:** Alamat API, contoh:  
  `https://api.example.com/users`
- **HTTP Method:** Jenis operasi, seperti:  
  - `GET` – Mengambil data  
  - `POST` – Mengirim data baru  
  - `PUT` – Memperbarui data  
  - `DELETE` – Menghapus data
- **Headers:** Informasi tambahan seperti format (`Content-Type: application/json`), token, dll.
- **Body (optional):** Data yang dikirim dalam format JSON atau XML.

### 📬 Response API
Response biasanya mengandung:
- **Status Code:**  
  - `200 OK` → Berhasil  
  - `201 Created` → Data berhasil dibuat  
  - `400 Bad Request` → Input tidak valid  
  - `401 Unauthorized` → Tidak punya izin  
  - `500 Internal Server Error` → Error di server
- **Body:** Data hasil respons dalam format JSON atau XML.
- **Headers:** Metadata respons seperti waktu, tipe konten, dll.

---

## 🧪 Operasi Dasar di Postman
Langkah-langkah umum untuk menguji API menggunakan **Postman**:

1. **Buka Postman**, buat tab baru.
2. Pilih metode (GET, POST, PUT, DELETE).
3. Masukkan URL endpoint API.
4. Jika perlu, tambahkan:
   - Header (`Content-Type: application/json`)
   - Body (format JSON) jika metode POST/PUT.
5. Klik **Send**.
6. Periksa hasil di tab **Response**.

---

## 💻 Studi Kasus: Contoh Live API Testing

### 📍 API Publik: [JSONPlaceholder](https://jsonplaceholder.typicode.com/)
API dummy untuk latihan request-response.

---

### 🧠 Contoh 1: **GET Request**
**Tujuan:** Mengambil daftar pengguna dari endpoint `/users`

**Langkah di Postman:**
- Method: `GET`
- URL: `https://jsonplaceholder.typicode.com/users`
- Klik **Send**

**Contoh Response:**
```json
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz"
  },
  {
    "id": 2,
    "name": "Ervin Howell",
    "username": "Antonette",
    "email": "Shanna@melissa.tv"
  }
]
```