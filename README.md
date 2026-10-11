# DPIB — Desain Pemodelan dan Informasi Bangunan
### Portal Profil Jurusan & Sistem Informasi Portofolio Siswa SMKN 1 Kawali

![PHP](https://img.shields.io/badge/PHP-8.0%2B-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-Modern_UI-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![SMKN 1 Kawali](https://img.shields.io/badge/School-SMKN_1_Kawali-005691?style=for-the-badge)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Active_Development-success?style=for-the-badge)

---

## 🏛️ Ringkasan Proyek

**DPIB Web Portal** adalah aplikasi web dinamis yang dirancang khusus untuk mempublikasikan profil, kompetensi keahlian, kurikulum industri, serta portofolio karya siswa jurusan **Desain Pemodelan dan Informasi Bangunan (DPIB)** di **SMK Negeri 1 Kawali**. 

Aplikasi ini menggabungkan antarmuka modern bernuansa *architectural minimalism* dengan backend fungsional berbasis **PHP Native** dan **MySQL**, dilengkapi sistem manajemen konten galeri (CRUD), pengelolaan akun bertingkat (*role-based access control*), serta portal wawasan teknologi konstruksi terkini seperti *Building Information Modeling* (BIM).

---

## ✨ Fitur-Fitur Utama

### 1. 🏢 Halaman Beranda Interaktif (`index.php`)
- **Hero Presentation**: Pengantar visi presisi desain arsitektural dengan tipografi modern dan call-to-action dinamis.
- **Profil Jurusan & Filosofi**: Pemaparan komprehensif visi, misi, dan orientasi lulusan berstandar dunia usaha/dunia industri (DUDI).
- **Software Suite Showcase**: Sorotan ekosistem perangkat lunak industri yang dikuasai siswa (AutoCAD, Revit, SketchUp, ArchiCAD).
- **Fasilitas Studio & Lab**: Galeri fasilitas studio gambar manual, laboratorium komputer CAD/BIM, dan instrumen ukur tanah (Total Station).

### 2. 🖼️ Galeri Portofolio & Manajemen Konten Dinamis (`galeri.php`)
- **Masonry Visual Grid**: Tampilan portofolio karya desain 2D, visualisasi 3D rendering, dan maket fisik dalam layout kisi responsif.
- **Filter Kategori Real-Time**: Navigasi karya terstruktur berdasarkan klasifikasi (misal: *3D Modeling*, *Desain Interior*, *Gambar Kerja*, *Maket*).
- **Admin In-Page CRUD**:
  - Administrator dapat menambah, memperbarui, dan menghapus postingan galeri langsung dari antarmuka halaman.
  - Pengelolaan taksonomi kategori karya (tambah, edit nama, dan hapus kategori) secara fleksibel.

### 3. 📰 Wawasan & Berita Konstruksi (`artikel.php`)
- **Sorotan Artikel Utama**: Ulasan mendalam topik mutakhir industri, seperti implementasi *BIM Level 3* pada mega-proyek infrastruktur.
- **Katalog Artikel Edukatif**: Seri panduan dasar modeling BIM, tren konstruksi ramah lingkungan (*sustainable green building*), dan laporan workshop pengukuran lahan.
- **Navigasi Baca Terstruktur**: Sidebar pencarian, filter kategori wawasan, dan daftar postingan terbaru.

### 4. 📬 Pusat Kontak & Layanan Informasi (`kontak.php`)
- **Formulir Pesan Interaktif**: Antarmuka bagi calon siswa, wali murid, dan mitra industri untuk mengirimkan pertanyaan atau kerja sama.
- **Informasi Kontak Terpadu**: Alamat resmi kampus SMKN 1 Kawali, hotline telepon, surel institusi, dan jam operasional dinas.

### 5. 🔐 Sistem Autentikasi & Kontrol Akses (`auth.php`, `login.php`, `daftar.php`, `logout.php`)
- **Pendaftaran Pengguna Mandiri**: Validasi format email institusi/pribadi, batas minimal 8 karakter kata sandi, dan konfirmasi kata sandi.
- **Session Guarding & XSS Protection**: Enkapsulasi session terpusat dan helper `escapeHtml()` menggunakan `htmlspecialchars` untuk mitigasi serangan XSS.
- **Navigasi Dinamis & Avatar Profil (`navbar.php`)**: Header cerdas yang mendeteksi status sesi login, menampilkan inisial pengguna terotentikasi, tautan cepat dashboard admin, serta akses keluar sistem (*logout*).

### 6. ⚙️ Manajemen Pengguna Admin (`admin-users.php`, `admin-user-edit.php`)
- **Tabel Pengguna Terdaftar**: Tinjauan lengkap seluruh akun terdaftar beserta perannya (*admin* atau *user*).
- **Editor Akun Terproteksi**: Hak akses eksklusif administrator untuk memperbarui nama, surel, kata sandi, dan status hak akses menggunakan *MySQL Prepared Statements*.

### 7. 👤 Pengaturan Akun Mandiri (`profil.php`)
- **Self-Service Profile**: Pengguna yang masuk dapat memperbarui nama tampilan pribadi atau mengganti kata sandi secara mandiri kapan saja.

---

## 🛠️ Arsitektur Teknologi & Dependensi

| Layer | Komponen / Library | Peran & Implementasi |
| :--- | :--- | :--- |
| **Backend Engine** | PHP 8.0+ Native | Server-side scripting, session management, dan routing logika bisnis |
| **Database** | MySQL / MariaDB | Penyimpanan relasional data pengguna dan taksonomi galeri (`db_dpib`) |
| **Database Driver** | MySQLi (Prepared Statements) | Kueri aman terparameterisasi untuk mencegah injeksi SQL |
| **Styling Framework** | Tailwind CSS (CDN Play) | Utilitas CSS modern dengan konfigurasi palet monokromatik arsitektur |
| **Iconography** | Google Material Symbols Outlined | Ikon antarmuka bersih dan konsisten |
| **Tipografi** | Google Fonts (Inter & JetBrains Mono) | Kombinasi sans-serif elegan dan font monospace teknis ala cetak biru (*blueprint*) |
| **Encoding** | `utf8mb4` | Standardisasi set karakter universal untuk keamanan data teks |

---

## 🗄️ Skema Database & Migrasi SQL

Proyek ini menggunakan database `db_dpib`. Jalankan kueri SQL berikut di phpMyAdmin atau MySQL CLI untuk menyiapkan struktur tabel lengkap beserta data awal:

```sql
-- 1. Pembuatan Database
CREATE DATABASE IF NOT EXISTS db_dpib 
  CHARACTER SET utf8mb4 
  COLLATE utf8mb4_unicode_ci;

USE db_dpib;

-- 2. Tabel Pengguna (users)
CREATE TABLE IF NOT EXISTS users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nama VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role ENUM('user', 'admin') NOT NULL DEFAULT 'user',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- 3. Tabel Galeri & Kategori (galeri)
CREATE TABLE IF NOT EXISTS galeri (
    id INT AUTO_INCREMENT PRIMARY KEY,
    type ENUM('category', 'post') NOT NULL,
    title VARCHAR(255) NOT NULL,
    image VARCHAR(2048) NULL,
    category_id INT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    INDEX idx_type (type),
    INDEX idx_category (category_id),
    CONSTRAINT fk_galeri_category 
      FOREIGN KEY (category_id) 
      REFERENCES galeri(id) 
      ON DELETE SET NULL 
      ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- 4. Data Benih Awal (Seeding)
-- User Default
INSERT INTO users (nama, email, password, role) VALUES
('Administrator DPIB', 'admin@dpib.sch.id', 'admin123', 'admin'),
('Siswa Contoh', 'siswa@dpib.sch.id', 'siswa123', 'user')
ON DUPLICATE KEY UPDATE id=id;

-- Kategori Galeri
INSERT INTO galeri (id, type, title) VALUES
(1, 'category', 'Desain 3D & BIM'),
(2, 'category', 'Gambar Kerja 2D'),
(3, 'category', 'Maket Arsitektur')
ON DUPLICATE KEY UPDATE title=VALUES(title);

-- Contoh Postingan Karya
INSERT INTO galeri (type, title, image, category_id) VALUES
('post', 'Desain Rumah Tinggal Tropis Modern', 'dpib1.jpg', 1),
('post', 'Perencanaan Denah dan Potongan Gedung', 'dpib 2.jpg', 2),
('post', 'Maket Kompleks Hunian Ramah Lingkungan', 'dpib 3.jpg', 3);
```

---

## 🚀 Panduan Instalasi & Menjalankan Proyek

### Prasyarat Sistem
- **Web Server & Database**: XAMPP, Laragon, atau LAMP/MAMP stack dengan PHP versi 8.0 atau yang lebih baru.
- **MySQL / MariaDB Service**: Berjalan di port default `3306`.
- **Git** (opsional untuk cloning).
- Peramban web modern (Google Chrome, Firefox, Microsoft Edge).

### Langkah 1: Unduh atau Klon Repositori
Tempatkan berkas proyek di folder publik web server Anda:

```bash
# Menggunakan Git
git clone https://github.com/hamdandzrpl/DPIB-projects.git

# Arahkan folder ke direktori web server:
# Pada XAMPP: C:/xampp/htdocs/DPIB-projects
# Pada Laragon: C:/laragon/www/DPIB-projects
```

### Langkah 2: Impor Database
1. Buka antarmuka phpMyAdmin di peramban (`http://localhost/phpmyadmin`).
2. Buat database baru bernama `db_dpib`.
3. Buka tab **SQL**, salin dan tempel kueri dari bagian [Skema Database](#-skema-database--migrasi-sql), lalu tekan tombol **Go / Kirim**.

### Langkah 3: Konfigurasi Koneksi (`koneksi.php`)
Periksa berkas `koneksi.php` pada *root* proyek dan sesuaikan kredensial server lokal Anda:

```php
<?php
// Koneksi database MySQL
$host = "localhost";
$user = "root";
$pass = "";
$db   = "db_dpib";

$conn = mysqli_connect($host, $user, $pass, $db);

if (!$conn) {
    die("Koneksi gagal: " . mysqli_connect_error());
}

mysqli_set_charset($conn, "utf8mb4");
```

### Langkah 4: Jalankan Aplikasi
Buka peramban favorit Anda dan akses URL berikut:
```text
http://localhost/DPIB-projects/index.php
```

> [!TIP]
> **Menjalankan via PHP Built-in Server**:
> Jika Anda tidak menggunakan XAMPP/Laragon, Anda dapat langsung menjalankan perintah berikut di terminal pada folder proyek:
> ```bash
> php -S localhost:8000
> ```
> Lalu buka `http://localhost:8000/index.php` pada browser.

### Akun Bawaan untuk Uji Coba

| Peran (*Role*) | Surel (*Email*) | Kata Sandi | Hak Akses |
| :--- | :--- | :--- | :--- |
| **Administrator** | `admin@dpib.sch.id` | `admin123` | Akses penuh: kelola posting & kategori galeri, manajemen seluruh akun pengguna |
| **Siswa / User** | `siswa@dpib.sch.id` | `siswa123` | Eksplorasi profil, artikel, galeri, serta pembaruan profil mandiri |

---

## 📁 Struktur Direktori Proyek

```text
DPIB-projects/
├── admin-user-edit.php   # Antarmuka & pemrosesan edit data serta peran akun oleh admin
├── admin-users.php       # Dashboard daftar seluruh akun pengguna terdaftar
├── artikel.php           # Portal artikel berita dan wawasan teknologi konstruksi
├── auth.php              # Helper inisiasi sesi PHP dan sanitasi keamanan (escapeHtml)
├── daftar.php            # Form dan pemrosesan pendaftaran akun pengguna baru
├── galeri.php            # Halaman galeri interaktif dengan filter dan panel CRUD karya
├── index.php             # Halaman beranda utama, profil jurusan, visi misi, & fasilitas
├── koneksi.php           # Konfigurasi koneksi database MySQLi terpusat
├── kontak.php            # Halaman informasi kontak, form saran, & lokasi sekolah
├── login.php             # Form dan logika otentikasi login pengguna
├── logout.php            # Penghancuran sesi login dan pengalihan ke halaman masuk
├── navbar.php            # Komponen navigasi universal dengan menu responsif & profil avatar
├── profil.php            # Fitur pembaruan nama pengguna dan kata sandi mandiri
├── README.md             # Dokumentasi teknis proyek
└── assets/               # Berkas gambar karya siswa, logo, dan aset visual (dpib1.jpg, dst.)
```

---

## 🔒 Catatan Keamanan & Praktik Terbaik

> [!IMPORTANT]
> Proyek ini dikembangkan dalam kerangka pembelajaran dan tugas kejuruan Rekayasa Perangkat Lunak (RPL). Untuk penerapan di lingkungan produksi (*live production server*), disarankan menerapkan peningkatan keamanan berikut:

- **Enkripsi Kata Sandi**: Ganti penyimpanan teks terbuka (*plaintext*) dengan fungsi standar industri `password_hash($password, PASSWORD_BCRYPT)` pada saat pendaftaran/edit akun, dan verifikasi menggunakan `password_verify()` saat proses masuk.
- **Proteksi CSRF**: Sematkan token acak (*Anti-CSRF Token*) pada setiap formulir POST untuk mencegah eksploitasi pengiriman data lintas situs.
- **Unggah Berkas Fisik yang Aman**: Tambahkan validasi tipe MIME biner, batasan ukuran berkas, dan penamaan hash acak ketika mengunggah foto karya siswa langsung ke penyimpanan server.
- **Pagination Galeri**: Tambahkan pembagian halaman (*pagination* atau *infinite scroll*) saat volume portofolio karya bertambah banyak.

---

## 🗺️ Peta Pengembangan (Roadmap)

- [x] Desain antarmuka responsif modern berbasis Tailwind CSS
- [x] Sistem autentikasi pengguna dengan session PHP
- [x] Manajemen galeri dan kategori karya dinamis (CRUD admin)
- [x] Kontrol akses multi-peran (*admin* dan *user*)
- [x] Modul mandiri pembaruan profil pengguna
- [ ] Implementasi hashing kata sandi (`password_hash` & `password_verify`)
- [ ] Fitur unggah langsung berkas gambar karya ke server (*file upload handler*)
- [ ] Integrasi artikel berbasis database dengan rich text editor (WYSIWYG)
- [ ] Fitur testimoni alumni dan mitra industri DUDI
- [ ] Optimasi SEO (*OpenGraph tags*, sitemap, dan meta schema)

---

## 👨‍💻 Kontributor & Pengembang

Proyek ini dibangun dan dikembangkan dengan dedikasi tinggi oleh:

- **Hamdan Dzakir** ([@hamdandzrpl](https://github.com/hamdandzrpl))  
  *Siswa Rekayasa Perangkat Lunak (RPL) — SMK Negeri 1 Kawali*  
  Portofolio / Situs: [tkj-smknn1kawali.vercel.app](https://tkj-smknn1kawali.vercel.app)

---

## 📄 Lisensi

Didistribusikan di bawah lisensi **MIT License**. Terbuka untuk digunakan, dimodifikasi, dan dikembangkan kembali untuk keperluan edukasi dan kemajuan dunia vokasi. Silakan merujuk pada berkas lisensi untuk detail selengkapnya.

---

<div align="center">
  <sub>Dibangun dengan bangga untuk memajukan talenta vokasi teknik & teknologi di SMKN 1 Kawali 🚀</sub>
</div>
