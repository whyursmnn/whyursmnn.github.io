# 🧭 Pengantar Selenium WebDriver

## 📘 1. Apa itu Selenium dan Apa itu Selenium WebDriver?

### 🧩 Apa itu Selenium?
**Selenium** adalah framework *open-source* yang digunakan untuk **mengotomatisasi pengujian aplikasi web** (Web Automation Testing).  
Dengan Selenium, penguji dapat membuat skrip otomatis yang menjalankan browser layaknya pengguna sungguhan — seperti membuka halaman web, mengisi form, menekan tombol, dan memverifikasi hasil yang ditampilkan.

Selenium sendiri terdiri dari beberapa komponen utama:
1. **Selenium IDE** → alat perekam otomatis berbasis browser.  
2. **Selenium RC** → versi lama Selenium untuk remote control browser (sudah digantikan WebDriver).  
3. **Selenium WebDriver** → API utama untuk otomatisasi browser modern.  
4. **Selenium Grid** → digunakan untuk menjalankan pengujian paralel di beberapa browser dan platform.

### 🔧 Apa itu Selenium WebDriver?
**Selenium WebDriver** adalah komponen utama Selenium yang memungkinkan penguji **mengontrol browser secara langsung** melalui API tanpa perantara.  
Dengan WebDriver, kita dapat:
- Membuka dan menutup browser secara otomatis  
- Mencari dan berinteraksi dengan elemen HTML (input, tombol, teks, dll)  
- Melakukan validasi hasil atau navigasi halaman  
- Mengambil tangkapan layar hasil pengujian  

---

## 🌟 2. Kenapa Harus Menggunakan Selenium?

Berikut alasan kenapa Selenium menjadi alat favorit untuk pengujian berbasis web:

1. 💻 **Multi-Browser Support** – Mendukung Chrome, Firefox, Edge, Safari, dan Opera.  
2. 🧩 **Multi-Language Support** – Bisa digunakan dengan Python, Java, JavaScript, C#, Ruby, dan Kotlin.  
3. 🧠 **Mudah Dipelajari** – Sintaks sederhana dan dokumentasi lengkap.  
4. ⚡ **Cross-Platform** – Dapat dijalankan di Windows, Linux, maupun macOS.  
5. 🔁 **Integrasi CI/CD** – Mudah diintegrasikan dengan Jenkins, GitHub Actions, atau GitLab CI.  
6. 💰 **Gratis dan Open Source** – Tidak berbayar dan terus diperbarui oleh komunitas besar.

---

## ⚙️ 3. Instalasi Selenium dengan Bahasa Pemrograman Python

Langkah-langkah instalasi Selenium dan WebDriver (contoh menggunakan Google Chrome):

### 🧩 Langkah 1 – Pastikan Python dan pip sudah terpasang
Cek versi Python dan pip di terminal atau command prompt:
```bash
python --version
pip --version
Jika belum terpasang, unduh dan install dari https://www.python.org/downloads/.

🧩 Langkah 2 – Instal Selenium Library
Jalankan perintah berikut di terminal:

bash
Copy code
pip install selenium
Perintah ini akan mengunduh dan memasang library Selenium ke lingkungan Python kamu.

🧩 Langkah 3 – Unduh WebDriver (contoh: ChromeDriver)
Cek versi Chrome kamu:
Buka Chrome → chrome://settings/help

Unduh ChromeDriver yang sesuai versi di:
🔗 https://chromedriver.chromium.org/downloads

Ekstrak file dan letakkan di folder proyek atau path sistem (contoh: C:\chromedriver\chromedriver.exe).

🧩 Langkah 4 – Uji Instalasi
Buat file bernama test_selenium.py dan isi dengan kode berikut:

python
Copy code
from selenium import webdriver

# Membuka browser Chrome
driver = webdriver.Chrome()

# Membuka halaman Google
driver.get("https://www.google.com")

# Menutup browser
driver.quit()
Jalankan di terminal:

bash
Copy code
python test_selenium.py
✅ Hasil: Browser Chrome akan terbuka secara otomatis dan memuat halaman Google.

🌐 4. Open Browser dengan Selenium
Contoh membuka browser dan mengatur ukuran jendela:

python
Copy code
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://www.python.org")
driver.maximize_window()  # Membesarkan jendela browser
print("Judul Halaman:", driver.title)
driver.quit()
🧾 Output:

vbnet
Copy code
Judul Halaman: Welcome to Python.org
🧩 5. Cara Berinteraksi dengan Elemen-elemen pada Halaman HTML
Selenium dapat mencari elemen di halaman web menggunakan berbagai locator strategy.

Metode Locator yang Umum Digunakan
Locator	Contoh	Deskripsi
By.ID	driver.find_element(By.ID, "user-name")	Berdasarkan atribut id
By.NAME	driver.find_element(By.NAME, "password")	Berdasarkan atribut name
By.XPATH	driver.find_element(By.XPATH, "//button[@id='login-button']")	Berdasarkan struktur XPath
By.CSS_SELECTOR	driver.find_element(By.CSS_SELECTOR, ".btn_login")	Berdasarkan class CSS
By.LINK_TEXT	driver.find_element(By.LINK_TEXT, "Login")	Berdasarkan teks hyperlink

Contoh Operasi Umum
python
Copy code
from selenium.webdriver.common.by import By

# Menulis teks ke input
driver.find_element(By.ID, "username").send_keys("standard_user")

# Klik tombol
driver.find_element(By.ID, "login-button").click()

# Mengambil teks dari elemen
message = driver.find_element(By.CLASS_NAME, "error-message-container").text
print("Pesan Error:", message)
💻 6. Contoh Interaksi (Live Coding) dengan Selenium WebDriver
Berikut contoh sederhana login otomatis pada situs https://www.saucedemo.com:

python
Copy code
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# Inisialisasi WebDriver
driver = webdriver.Chrome()
driver.maximize_window()

# Buka situs
driver.get("https://www.saucedemo.com/")

# Isi form login
driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")

# Klik tombol login
driver.find_element(By.ID, "login-button").click()

# Tunggu sejenak
time.sleep(2)

# Verifikasi login berhasil
assert "inventory" in driver.current_url
print("✅ Login Berhasil!")

# Tutup browser
driver.quit()
🧾 Output di Terminal:

pgsql
Copy code
✅ Login Berhasil!
🧪 7. Test Case dan Test Scenario
📋 Test Scenario
ID	Deskripsi	Tujuan
TS-001	Verifikasi login berhasil dengan kredensial valid	Memastikan pengguna dapat login
TS-002	Verifikasi login gagal dengan password salah	Memastikan sistem menampilkan pesan error
TS-003	Verifikasi penambahan produk ke keranjang	Memastikan fungsi “Add to Cart” berjalan

🧾 Test Case
Test Case 1: Login Berhasil
Atribut	Nilai
ID	TC-001
Deskripsi	Login menggunakan username dan password valid
Langkah Uji	1. Buka situs https://www.saucedemo.com
2. Masukkan username: standard_user
3. Masukkan password: secret_sauce
4. Klik tombol login
Hasil Diharapkan	Berhasil masuk ke halaman inventory.html
Status	✅ Passed

Test Case 2: Login Gagal
Atribut	Nilai
ID	TC-002
Deskripsi	Login dengan password salah
Langkah Uji	1. Buka situs https://www.saucedemo.com
2. Masukkan username: standard_user
3. Masukkan password: wrong_pass
4. Klik tombol login
Hasil Diharapkan	Tampil pesan error “Epic sadface: Username and password do not match any user in this service”
Status	✅ Passed

Test Case 3: Tambah Produk ke Keranjang
Atribut	Nilai
ID	TC-003
Deskripsi	Menambahkan produk ke keranjang setelah login
Langkah Uji	1. Login ke sistem
2. Klik “Add to cart” pada produk pertama
3. Klik ikon keranjang
Hasil Diharapkan	Produk tampil di halaman keranjang
Status	✅ Passed

💡 8. Contoh Implementasi Testing Lengkap
python
Copy code
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()
driver.maximize_window()
driver.get("https://www.saucedemo.com/")

# Login
driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")
driver.find_element(By.ID, "login-button").click()
time.sleep(1)

# Tambah produk ke keranjang
driver.find_element(By.CLASS_NAME, "btn_inventory").click()
driver.find_element(By.CLASS_NAME, "shopping_cart_link").click()
time.sleep(1)

# Verifikasi produk ditambahkan
assert "inventory-item" in driver.page_source
print("✅ Produk berhasil ditambahkan ke keranjang")

# Logout
driver.find_element(By.ID, "react-burger-menu-btn").click()
time.sleep(1)
driver.find_element(By.ID, "logout_sidebar_link").click()
time.sleep(1)
print("✅ Logout berhasil")

driver.quit()
🧾 Output di Terminal:

Copy code
✅ Produk berhasil ditambahkan ke keranjang
✅ Logout berhasil
🧠 9. Kesimpulan
Selenium WebDriver adalah alat otomatisasi yang sangat kuat untuk melakukan pengujian antarmuka web secara efisien.
Dengan Selenium, penguji dapat:

Membuka browser dan menjalankan interaksi secara otomatis.

Melakukan pengujian regresi dan fungsional dengan cepat.

Mengurangi kesalahan manusia dalam pengujian manual.

Mengintegrasikan pengujian dengan pipeline DevOps modern.

📚 10. Sumber Referensi
Selenium Python Tutorial (with Example) | BrowserStack

WebDriver | Selenium

