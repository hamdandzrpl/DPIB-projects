# DPIB — Desain Pemodelan dan Informasi Bangunan

<div align="center">

![Header](https://capsule-render.vercel.app/api?type=waving&color=0:1a1a1a,100:515f74&height=200&section=header&text=DPIB&fontSize=80&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Website%20Jurusan%20Desain%20Pemodelan%20dan%20Informasi%20Bangunan&descAlignY=58&descSize=16)

<p>
  <img src="https://img.shields.io/badge/PHP-8.x-777BB4?style=for-the-badge&logo=php&logoColor=white" />
  <img src="https://img.shields.io/badge/MySQL-MariaDB-4479A1?style=for-the-badge&logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind-CDN-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" />
  <img src="https://img.shields.io/badge/Lisensi-MIT-000000?style=for-the-badge" />
</p>

</div>

---

## 📌 Apa ini?

Website profil dan portal internal untuk jurusan **DPIB (Desain Pemodelan dan Informasi Bangunan)**. Isinya halaman profil jurusan, artikel, galeri karya siswa, halaman kontak, plus sistem login sederhana supaya admin bisa kelola akun dan konten galeri.

Dibikin pakai PHP native + MySQL, tanpa framework. Frontend pakai Tailwind lewat CDN biar ringan dan gampang diutak-atik.

---

## 🎯 Fitur

**Untuk pengunjung umum**
- Halaman profil jurusan (visi, misi, fasilitas, software yang dipelajari)
- Daftar artikel seputar BIM, konstruksi, dan kegiatan jurusan
- Galeri karya dengan filter kategori
- Form kontak dan peta lokasi

**Untuk user yang login**
- Ubah nama tampilan
- Ganti password

**Untuk admin**
- Kelola seluruh akun pengguna (tambah, edit, hapus, ganti role)
- Tambah, edit, hapus kategori galeri
- Tambah, edit, hapus karya di galeri

---

## 🧩 Struktur File

```
dpib/
├── koneksi.php              # Koneksi ke database db_dpib
├── auth.php                 # Session + helper escapeHtml()
├── navbar.php               # Header dan navigasi bersama
├── index.php                # Halaman utama / profil jurusan
├── artikel.php              # Daftar artikel
├── galeri.php               # Galeri karya + panel admin
├── kontak.php               # Halaman kontak
├── login.php                # Form masuk
├── daftar.php               # Form registrasi user baru
├── logout.php               # Keluar dari session
├── profil.php               # Pengaturan akun (nama/password)
├── admin-users.php          # Daftar seluruh akun (khusus admin)
├── admin-user-edit.php      # Edit satu akun (khusus admin)
└── auth.css                 # Style halaman auth & admin
```

---

## ⚙️ Cara Jalanin

**1. Clone repo**

```bash
git clone https://github.com/username/dpib.git
cd dpib
```

**2. Siapkan database**

Bikin database bernama `db_dpib`, lalu import struktur tabel `users` dan `galeri`:

```sql
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nama VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL,
  role ENUM('user','admin') DEFAULT 'user'
);

CREATE TABLE galeri (
  id INT AUTO_INCREMENT PRIMARY KEY,
  type ENUM('category','post') NOT NULL,
  title VARCHAR(180) NOT NULL,
  image VARCHAR(2048) DEFAULT NULL,
  category_id INT DEFAULT NULL
);
```

**3. Sesuaikan koneksi**

Buka `koneksi.php` dan sesuaikan kalau perlu:

```php
$conn = mysqli_connect("localhost", "root", "", "db_dpib");
```

**4. Jalankan**

Taruh folder di `htdocs` (XAMPP) atau `www` (Laragon), lalu buka:

```
http://localhost/dpib/
```

**5. Bikin akun admin pertama**

Daftar lewat `daftar.php` seperti biasa, terus ubah role-nya di database:

```sql
UPDATE users SET role = 'admin' WHERE email = 'email-kamu@example.com';
```

---

## 🛠️ Yang Dipakai

| Bagian | Teknologi |
|---|---|
| Backend | PHP 8 native, MySQLi (prepared statement) |
| Frontend | Tailwind CSS (CDN), Material Symbols, Inter + JetBrains Mono |
| Auth | PHP Session, `session_regenerate_id()` |
| Gambar | URL eksternal atau nama file lokal |

---

## 🔐 Catatan Keamanan

Ini proyek pembelajaran, jadi ada beberapa hal yang **belum production-ready**:

- Password disimpan sebagai teks biasa, belum di-hash pakai `password_hash()`
- Verifikasi password di login masih perbandingan string langsung
- Halaman admin menampilkan password user apa adanya
- Belum ada proteksi CSRF di form

Kalau mau dipakai beneran, tiga hal pertama itu wajib dibenerin dulu.

---

## 🗺️ Rencana ke Depan

- [ ] Hash password pakai `password_hash()` + `password_verify()`
- [ ] Upload gambar langsung dari form (bukan cuma URL/nama file)
- [ ] Halaman artikel diambil dari database, bukan statis
- [ ] Panel admin buat kelola artikel
- [ ] Sitemap dan meta SEO dasar

---

## 🤝 Kontribusi

Pull request selalu dibuka. Kalau nemu bug atau punya ide fitur, buka issue dulu biar bisa dibahas bareng.

```bash
git checkout -b fitur/nama-fitur
git commit -m "tambah fitur X"
git push origin fitur/nama-fitur
```

---

## 📄 Lisensi

MIT — bebas dipakai, dimodifikasi, dan dibagikan.

<div align="center">

![Footer](https://capsule-render.vercel.app/api?type=waving&color=0:515f74,100:1a1a1a&height=100&section=footer)

</div>
