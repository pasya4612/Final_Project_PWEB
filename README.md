<h1 align="center">LAPORAN PROYEK PENGEMBANGAN WEB: STUDYSYNC</h1>

<p align="center">
  <img src="https://via.placeholder.com/300x150?text=STUDYSYNC+LOGO" width="300" alt="Logo StudySync">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-Final+Project-brightgreen" alt="Status">
  <img src="https://img.shields.io/badge/Technology-Web+Application-blue" alt="Technology">
</p>

## JUDUL PROYEK:
**Rancang Bangun Aplikasi Manajemen Tugas dan Kolaborasi Belajar "StudySync" Berbasis Web**

<br>

## TIM PENGEMBANG:
**[Nama Pengembang 1]** [5025xxxxxx] [Backend & Logika Sistem]<br>
**[Nama Pengembang 2]** [5025xxxxxx] [Frontend & User Interface]

---

## 💻 BAB 1: PENDAHULUAN

### 1.1 Latar Belakang
StudySync dikembangkan sebagai solusi terpadu untuk pelajar dan mahasiswa dalam mengelola beban tugas yang dinamis. Aplikasi ini mengatasi kelemahan *to-do list* konvensional dengan mengintegrasikan fitur **manajemen tugas cerdas** yang otomatis mengklasifikasikan tugas berdasarkan tenggat waktu (*due date*), serta **modul kolaborasi sosial** untuk memfasilitasi diskusi dan komunikasi pribadi.

### 1.2 Tujuan Proyek
1.  Mengimplementasikan sistem **Task Management** (CRUD) yang dilengkapi dengan penandaan status otomatis (**Today, Upcoming, Overdue**).
2.  Menyediakan *dashboard* yang menampilkan metrik kinerja pengguna (*Total Tasks* dan *Completed Tasks*).
3.  Mengembangkan modul **Study Group** dan fitur komunikasi **Private Chat** (1-on-1) untuk mendukung kolaborasi akademik.
4.  Memastikan fleksibilitas akses melalui Login standar dan **Login dengan Google Account**.

---

## 🛠️ BAB 2: ANALISIS DAN PERANCANGAN SISTEM

### 2.1 Fitur Utama (*Functional Requirements*)

| Modul | Fitur | Deskripsi Fungsionalitas |
| :--- | :--- | :--- |
| **Autentikasi** | Register & Login | Mendukung pendaftaran akun baru, login standar, dan **Login via Google Account**. |
| **Profil** | Pengaturan Profil | Mengubah Nama, Email, dan Kata Sandi. |
| **Task Management**| Add & Edit Task | Tambah tugas (Konteks, Deskripsi, DL, Kategori). Fitur Edit memungkinkan perubahan detail dan pengembalian status dari **Completed ke Pending**. |
| **Pelacakan Waktu**| Klasifikasi Otomatis | Sistem mengkategorikan tugas ke: **Today List** (DL hari ini), **Upcoming This Week** (DL 2-7 hari ke depan), dan **Overdue** (DL terlewat). |
| **Dashboard** | Metrik Kinerja | Menghitung dan menampilkan **Total Tugas** yang ditambahkan dan **Tugas Selesai** (*Completed*). |
| **Study Group** | Group Management | Membuat, Mengedit, dan Menghapus grup diskusi untuk tugas atau materi. |
| **Friend & Chat** | Komunikasi Sosial | **Add Friend** (dari grup), mengelola permintaan (**Accept/Reject/Remove**), dan **Private Chat** 1-on-1. |

### 2.2 Arsitektur Sistem

StudySync dibangun di atas arsitektur *Client-Server* yang memisahkan database, logika aplikasi (*backend*), dan antarmuka pengguna (*frontend*). Logika utama terletak pada pemrosesan tanggal tugas dan manajemen relasi sosial (grup dan pertemanan).

#### Diagram Konteks (DFD Level 0)
Diagram ini menunjukkan interaksi StudySync dengan Pengguna sebagai entitas eksternal.



#### Logika Alir Data Tugas (DFD Level 1: Task Management)
Proses utama dalam aplikasi adalah pemrosesan data tugas untuk klasifikasi otomatis.



**Logika Kunci:** Data `Due Date` tugas diproses secara berkala (Proses Kategorisasi Otomatis) untuk menentukan kategori penempatan (Today, Upcoming, Overdue) sebelum ditampilkan di Dashboard.

---

## 📘 BAB 3: PANDUAN PENGGUNA (USER GUIDE)

Berikut adalah langkah-langkah dasar untuk memulai dan memanfaatkan fitur StudySync:

### 1. Memulai Akun

1.  **Login Cepat:** Pilih **"Login dengan Google Account"** di halaman awal untuk langsung masuk.
2.  **Edit Profil:** Akses menu **"Profile"** untuk mengganti Nama, Email, atau Kata Sandi Anda.

### 2. Mengelola Tugas

| Langkah | Aksi | Hasil |
| :--- | :--- | :--- |
| **Tambah Tugas** | Klik **"+ Add Task"**. Isi Konteks, Deskripsi, DL, dan Kategori. | Tugas Anda masuk ke kategori **Today**, **Upcoming**, atau **Overdue** secara otomatis. |
| **Lihat Progres** | Kunjungi **Dashboard**. | Lihat total tugas yang pernah dibuat dan berapa banyak yang sudah diselesaikan (*Completed*). |
| **Tandai Selesai**| Klik ikon centang (**Mark Complete**) di samping tugas. | Status tugas berubah. Anda dapat **mengedit** tugas untuk mengubah status kembali ke *Pending* jika salah input. |

### 3. Kolaborasi dan Komunikasi

| Langkah | Aksi | Hasil |
| :--- | :--- | :--- |
| **Buat Grup** | Buka **"Study Group"** $\rightarrow$ **"+ Buat Grup Baru"**. | Anda dapat memulai diskusi topik tertentu dengan teman. |
| **Tambah Teman** | Di dalam Study Group, klik anggota $\rightarrow$ **"Add Friend"**. | Permintaan pertemanan terkirim. Anda juga bisa **Edit** atau **Delete** grup yang Anda buat. |
| **Kelola Teman** | Buka **"Friend List"**. | **Accept** atau **Reject** permintaan pertemanan. Anda bisa **Remove** teman yang sudah ada. |
| **Private Chat** | Pilih nama teman dari **"Friend List"**. | Memulai sesi *chatting* 1-on-1 (mirip WA/Line) langsung di dalam StudySync. |

---

## 🚀 BAB 5: PENUTUP

### 5.1 Kesimpulan
StudySync merupakan *platform* yang berhasil mengintegrasikan manajemen tugas yang efisien dengan alat komunikasi dan kolaborasi yang fleksibel. Fitur utamanya (klasifikasi otomatis dan Study Group) memenuhi kebutuhan pelajar untuk mengelola tenggat waktu dan berinteraksi secara efektif. StudySync siap menjadi asisten digital yang andal dalam lingkungan akademik.

---
<center>
Copyright © 2025 StudySync.
</center>
