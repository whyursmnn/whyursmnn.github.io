# 🧪 Pengantar Cypress

---

## 1. 📘 Definisi: Apa itu Cypress?

**Cypress** adalah framework *end-to-end testing* berbasis JavaScript yang digunakan untuk **mengotomatisasi pengujian aplikasi web langsung di browser nyata**.  
Berbeda dengan Selenium yang berinteraksi melalui *remote driver*, Cypress berjalan **langsung di dalam browser**, sehingga lebih cepat dan terintegrasi dengan baik dengan DOM, jaringan, dan API.

### ⚙️ Posisi Cypress dalam Pengujian
Cypress berada pada tahap **pengujian antarmuka (UI)** dan **pengujian integrasi front-end**, berfokus untuk:
- Menguji alur kerja pengguna (*user flow*)
- Memastikan elemen UI berfungsi sesuai ekspektasi
- Menguji integrasi API di sisi klien

---

## 2. 🌟 Keunggulan Cypress

Cypress memiliki beberapa fitur pembeda dibanding framework lain:

### 🚀 a. Arsitektur Modern
- Cypress berjalan **di dalam browser yang sama dengan aplikasi** yang diuji  
- Tidak menggunakan *WebDriver* eksternal seperti Selenium, sehingga pengujian berjalan lebih cepat dan stabil

### 👀 b. Test Runner Interaktif
- Menampilkan hasil pengujian **secara real-time**  
- Setiap langkah uji (klik, input, visit) ditampilkan di UI Test Runner

### ⏪ c. Time Travel Debugging
- Cypress menyimpan **screenshot otomatis di setiap langkah uji**, sehingga kamu dapat "melihat kembali" apa yang terjadi saat pengujian gagal

### 🧠 d. Built-in Waiting
- Cypress **secara otomatis menunggu** elemen muncul sebelum melanjutkan langkah berikutnya, mengurangi kebutuhan penggunaan `wait()` manual

---

## 3. ⚙️ Instalasi Cypress via NPM/Yarn

Sebelum mulai, pastikan kamu sudah menginstal **Node.js dan npm**.

### 🔧 Langkah Instalasi

1. **Inisialisasi proyek Node.js**
   ```bash
   mkdir cypress-demo
   cd cypress-demo
   npm init -y
   ```
2. **Instal Cypress**
   ```bash
   npm install cypress --save-dev
   ```
3. **Jalankan Cypress pertama kali**
   ```bash
   npx cypress open
   ```
   ✅ Cypress akan membuka GUI Test Runner dan otomatis membuat struktur folder:

```
cypress/
├── e2e/
│   └── example.cy.js
├── fixtures/
├── support/
cypress.config.js
```

---

## 4. 🧩 Struktur Tes: Anatomi File Tes

Cypress menggunakan gaya pengujian Mocha dan Chai, dengan struktur dasar sebagai berikut:

```javascript
describe('Nama Fitur yang Diuji', () => {
  it('Deskripsi langkah pengujian', () => {
    // kode pengujian di sini
  });
});
```

🧱 Penjelasan:
- `describe()` → Mengelompokkan serangkaian test case
- `it()` → Mendefinisikan satu test case
- `cy` → Objek global Cypress untuk berinteraksi dengan browser

---

## 5. 🧭 Perintah Dasar Cypress

| Perintah | Fungsi |
| --- | --- |
| `cy.visit('url')` | Membuka halaman web |
| `cy.get('selector')` | Mencari elemen DOM |
| `cy.type('text')` | Mengetik teks ke input |
| `cy.click()` | Mengklik elemen |
| `cy.contains('text')` | Mencari elemen berdasarkan teks |
| `cy.url()` | Mendapatkan URL aktif |
| `cy.should('contain', 'value')` | Verifikasi hasil |

### 🧪 Contoh
```javascript
cy.visit('https://example.com');
cy.get('#username').type('admin');
cy.get('#password').type('12345');
cy.get('#login-button').click();
```

---

## 6. 💻 Studi Kasus: Login Otomatis ke saucedemo.com

### 🔍 Tujuan
Melakukan pengujian login berhasil dan login gagal pada situs demo [https://www.saucedemo.com](https://www.saucedemo.com).

### 📁 Lokasi File
Buat file baru di:

```bash
cypress/e2e/saucedemo_login.cy.js
```

### 🧠 Kode Uji
```javascript
describe('Testing Login Page SauceDemo', () => {
  
  // Dilakukan sebelum setiap test case
  beforeEach(() => {
    cy.visit('https://www.saucedemo.com/');
  });

  it('✅ Login Berhasil dengan Kredensial Valid', () => {
    cy.get('#user-name').type('standard_user');
    cy.get('#password').type('secret_sauce');
    cy.get('#login-button').click();

    // Verifikasi berhasil login
    cy.url().should('include', '/inventory.html');
  });

  it('❌ Login Gagal dengan Password Salah', () => {
    cy.get('#user-name').type('standard_user');
    cy.get('#password').type('wrong_password');
    cy.get('#login-button').click();

    // Verifikasi pesan error
    cy.get('.error-message-container')
      .should('contain', 'Username and password do not match any user');
  });
});
```

### 🧾 Cara Menjalankan Tes:
```bash
npx cypress open
```
Lalu pilih file `saucedemo_login.cy.js` untuk menjalankannya.

---

## 7. 🧾 Test Scenario dan Test Case

### 📋 Test Scenario
| ID | Deskripsi | Tujuan |
| --- | --- | --- |
| TS-001 | Verifikasi login berhasil dengan kredensial valid | Pastikan login sukses ke halaman utama |
| TS-002 | Verifikasi login gagal dengan password salah | Pastikan sistem menampilkan pesan error |
| TS-003 | Verifikasi form login kosong | Pastikan validasi input muncul |

### 🧪 Test Case Detail

#### ✅ Test Case 1: Login Berhasil
| Atribut | Nilai |
| --- | --- |
| ID | TC-001 |
| Deskripsi | Login menggunakan username dan password valid |
| Langkah Uji | 1. Buka https://www.saucedemo.com/ <br> 2. Isi username `standard_user` <br> 3. Isi password `secret_sauce` <br> 4. Klik tombol Login |
| Hasil Diharapkan | Berhasil masuk ke halaman `inventory.html` |
| Status | ✅ Passed |

#### ❌ Test Case 2: Login Gagal
| Atribut | Nilai |
| --- | --- |
| ID | TC-002 |
| Deskripsi | Login dengan password salah |
| Langkah Uji | 1. Isi username `standard_user` <br> 2. Isi password `wrong_pass` <br> 3. Klik tombol Login |
| Hasil Diharapkan | Tampil pesan error `Epic sadface: Username and password do not match any user in this service` |
| Status | ✅ Passed |

---

## 8. 🧩 Contoh Tambahan: Pengujian Produk & Logout

```javascript
describe('Fitur Produk & Logout', () => {
  beforeEach(() => {
    cy.visit('https://www.saucedemo.com/');
    cy.get('#user-name').type('standard_user');
    cy.get('#password').type('secret_sauce');
    cy.get('#login-button').click();
  });

  it('🛒 Menambahkan Produk ke Keranjang', () => {
    cy.get('.btn_inventory').first().click();
    cy.get('.shopping_cart_link').click();
    cy.get('.inventory_item_name').should('be.visible');
  });

  it('🚪 Logout dari Aplikasi', () => {
    cy.get('#react-burger-menu-btn').click();
    cy.get('#logout_sidebar_link').click();
    cy.url().should('eq', 'https://www.saucedemo.com/');
  });
});
```

---

## 9. 💡 Kesimpulan

Cypress adalah framework modern untuk *end-to-end testing* berbasis JavaScript yang:
- Menyediakan test runner interaktif
- Menjalankan pengujian cepat dan stabil
- Memiliki fitur *time travel debugging*
- Dapat meniru perilaku pengguna sebenarnya di browser

Dengan Cypress, tim pengembang dapat memastikan fungsi utama aplikasi web bekerja sesuai ekspektasi dengan efisiensi tinggi.

---

## 10. 🔗 Sumber Referensi
- [Cypress Official Website](https://www.cypress.io/)
- [Cypress Documentation](https://docs.cypress.io/)
- [SauceDemo Test Site](https://www.saucedemo.com/)

---