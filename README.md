# 📚 Sistem Informasi E-Library Digital (SPA)

Proyek ini dibangun untuk memenuhi tugas **UAS Pemrograman Web 2** dengan menerapkan arsitektur terpisah (*Decoupled Architecture*). Aplikasi memisahkan secara total sisi Frontend (Client) dan Backend (RESTful API Server).

---

## 👨‍💻 Identitas Mahasiswa
* **Nama:** Muhamad Ricky Nugraha
* **NIM:** 312410186
* **Kelas:** I241B
* **Program Studi:** Teknik Informatika
* **Universitas:** Universitas Pelita Bangsa

---

## 📝 Deskripsi Proyek & Studi Kasus
Proyek ini mengangkat studi kasus **Sistem Informasi E-Library Digital** (Perpustakaan Digital). 

Aplikasi ini menggunakan **Arsitektur Terpisah (*Decoupled Architecture*)**. Sisi **Backend** berfungsi sebagai *RESTful API Server* berbasis **CodeIgniter 4** yang bertugas mengamankan database, menangani bypass CORS, serta mengelola autentikasi berbasis token (*Token-Based Authentication*). Sisi **Frontend** dirancang sebagai *Single Page Application* (SPA) murni berbasis **Vue.js 3** bertenaga **TailwindCSS** untuk visualisasi antarmuka dan manipulasi data secara *asynchronous* melalui **Axios** tanpa memerlukan proses *build compile* Node.js.

---

## 🗄️ Skema Relasi Tabel Database
Database bernama `library` mengimplementasikan relasi data master buku serta tabel petugas (`users`). Kolom `token` pada tabel `users` digunakan sebagai kunci validasi session keamanan API.

Skema Relasi Database <img width="1920" height="1080" alt="Screenshot (315)" src="https://github.com/user-attachments/assets/d58a8121-e67e-42f0-b1ae-f345d4e7ece6" />


---

## 🔒 Pengujian Proteksi Keamanan API (Error 401)
Setiap *request* manipulasi data master pada rute `/api/buku` dilindungi secara ketat oleh `AuthFilter` backend. Jika ditembak menggunakan **Postman** tanpa menyertakan HTTP Header `Authorization: Bearer <token>`, server otomatis menolak akses dan membalas dengan status **401 Unauthorized**.

Uji Coba Postman Gagal - Error 401 <img width="1920" height="1080" alt="Screenshot (289)" src="https://github.com/user-attachments/assets/6f534844-3c3e-4006-9660-49638f3a1ac0" />


---

## 🎨 Dokumentasi Antarmuka Aplikasi (UI TailwindCSS)

### A. Halaman Form Login Petugas
Antarmuka form autentikasi petugas e-library sebelum diberikan token akses.
Halaman Login <img width="1920" height="1080" alt="Screenshot (317)" src="https://github.com/user-attachments/assets/e204146d-a3f6-4b9b-86c7-d12e771469aa" />


### B. Halaman Dashboard Admin
Tampilan panel utama setelah berhasil menembus verifikasi login akun.
Halaman Dashboard Admin <img width="1920" height="1080" alt="Screenshot (316)" src="https://github.com/user-attachments/assets/fe0fb775-26a5-40ff-ad62-a8acd826111b" />


### C. Tampilan Form Modal Tambah/Edit Data Buku
Komponen dialog pop-up interaktif Vue.js untuk melakukan *input* data buku baru atau mengubah data lama.
Form Modal Tambah/Edit <img width="1920" height="1080" alt="Screenshot (318)" src="https://github.com/user-attachments/assets/1da9ce88-4ead-4ddb-a2f7-53098f3a9a2b" />


### D. Visualisasi Data pada Tabel bertenaga TailwindCSS
Tampilan penyajian data master buku yang terstruktur rapi menggunakan tabel responsif utility-first TailwindCSS.
Visualisasi Tabel Buku <img width="1920" height="1080" alt="Screenshot (319)" src="https://github.com/user-attachments/assets/638878b4-24c8-4027-81d5-4f029cce9a6c" />


---

## 🔧 Petunjuk Instalasi Komputer Lokal (Localhost)

### 1. Menjalankan Proyek Backend (CodeIgniter 4)
1. Aktifkan modul **Apache** dan **MySQL** pada XAMPP Control Panel Anda.
2. Pindahkan folder proyek `UAS_Web2_312410186_ricky` ke dalam direktori `C:/xampp/htdocs/`.
3. Buka phpMyAdmin (`http://127.0.0.1/phpmyadmin/`), buat database baru bernama **`library`**, lalu import struktur file database SQL Anda ke dalamnya.
4. Buka folder `backend-api/` menggunakan VS Code, sesuaikan konfigurasi database pada file `.env`, dan pastikan mode environment diubah ke development:
   ```ini
   database.default.hostname = localhost
   database.default.database = library
   database.default.username = root
   database.default.password = 
   CI_ENVIRONMENT = development
